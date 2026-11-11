# Exp 6 – React Lab Exercise: Form Validation

## NAME : V.S.SREE VIVEKA
## REG NO : 2305001031

## Aim
To create a React form with validation for required fields, email, and password, and display appropriate error messages.

## Objectives
- To create a form using React.
- To manage form data using `useState()`.
- To validate required fields.
- To validate an email address.
- To validate password length.
- To display error messages dynamically.

## Program

### Step 1 – Create React Project

```bash
npm create vite@latest form-validation
cd form-validation
npm install
npm run dev
```

Select React as the framework and JavaScript as the variant.

### Step 2 – App.jsx

```jsx
import { useState } from "react";
import "./App.css";

function App() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    password: ""
  });

  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  const validate = () => {
    let newErrors = {};

    // Required field validation
    if (formData.name.trim() === "") {
      newErrors.name = "Name is required";
    }

    // Email validation
    if (formData.email.trim() === "") {
      newErrors.email = "Email is required";
    } else if (!formData.email.includes("@")) {
      newErrors.email = "Enter a valid email";
    }

    // Password validation
    if (formData.password === "") {
      newErrors.password = "Password is required";
    } else if (formData.password.length < 6) {
      newErrors.password =
        "Password must contain at least 6 characters";
    }

    return newErrors;
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    const validationErrors = validate();
    setErrors(validationErrors);

    if (Object.keys(validationErrors).length === 0) {
      alert("Form submitted successfully!");
    }
  };

  return (
    <div className="container">
      <h1>Registration Form</h1>

      <form onSubmit={handleSubmit} noValidate>
        <label>Name:</label>
        <input
          type="text"
          name="name"
          value={formData.name}
          onChange={handleChange}
          placeholder="Enter your name"
        />
        {errors.name && <p>{errors.name}</p>}

        <label>Email:</label>
        <input
          type="text"
          name="email"
          value={formData.email}
          onChange={handleChange}
          placeholder="Enter your email"
        />
        {errors.email && <p>{errors.email}</p>}

        <label>Password:</label>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleChange}
          placeholder="Enter your password"
        />
        {errors.password && <p>{errors.password}</p>}

        <button type="submit">Register</button>
      </form>
    </div>
  );
}

export default App;
```

### Step 3 – App.css

```css
.container {
  width: 350px;
  margin: 30px auto;
  padding: 20px;
  border: 1px solid gray;
  border-radius: 10px;
}

h1 {
  text-align: center;
  color: blue;
}

label {
  display: block;
  margin-top: 15px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
}

p {
  color: red;
  margin: 5px 0;
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  cursor: pointer;
}
```

## Output

### 1. Invalid Form – Error Messages
<img width="1078" height="530" alt="WhatsApp Image 2026-11-11 at 9 05 26 AM" src="https://github.com/user-attachments/assets/24834056-a67f-4718-a70d-47a03c6b0b81" />

### 2. Correct Form – Valid Input Details
<img width="1068" height="522" alt="WhatsApp Image 2026-11-11 at 9 06 06 AM" src="https://github.com/user-attachments/assets/7bb6e966-5969-41f0-874d-4804f02efaea" />

### 3. Successful Form Submission – Alert Pop-up
<img width="1077" height="526" alt="WhatsApp Image 2026-11-11 at 9 06 18 AM" src="https://github.com/user-attachments/assets/4078a24d-c340-4cac-95eb-7d63ec025449" />

## Result

Thus, a React Registration Form was successfully created with form validation using the `useState()` Hook. Required fields, email format, and password length were validated, and appropriate error messages were displayed dynamically. The form was successfully submitted when all the entered details were valid.

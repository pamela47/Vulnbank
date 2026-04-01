# VulnBank Web Application Security Assessment  
**Consultant:** Pamela Batchato  
**Date:** 28.03.2026  

This repository contains a redacted version of a web application security assessment performed on the fictional **VulnBank** platform.  
The goal of this project is to demonstrate practical experience in:

- Web application penetration testing  
- API security analysis  
- Authentication and session testing  
- Access control validation  
- Vulnerability reporting and remediation  

All sensitive client information has been removed.  
This project is intended for portfolio and educational purposes.

---

## 🔍 Assessment Overview

The assessment followed a structured methodology aligned with OWASP Web Security Testing Guide (WSTG).  
Testing focused on:

- Authentication & session management  
- API request/response flows  
- Access control enforcement  
- Input validation  
- Token handling  
- Error handling & server responses  

The engagement simulated real-world attack scenarios in a controlled environment.

---

## 🧭 Methodology

The following phases were performed:

1. **Reconnaissance** – Understanding application structure and workflows  
2. **Enumeration** – Mapping endpoints, parameters, and API behaviour  
3. **Vulnerability Testing** – Targeted testing for OWASP Top 10 issues  
4. **Exploitation** – Controlled validation of identified weaknesses  
5. **Reporting** – Documentation of findings and remediation guidance  

Detailed methodology notes are available in `/01-Overview/`.

---

## ⚠️ Key Findings

### 1. Insecure JWT Handling (High)
The application stored sensitive authorization data (e.g., `is_admin`) inside a client-controlled JWT cookie.  
This allowed potential privilege escalation if the token was modified.

### 2. Insecure Direct Object Reference – IDOR (High)
The endpoint `/transactions/{account_number}` lacked ownership validation, allowing access to other users' financial data.

### 3. Weak Authentication Enforcement (Medium)
Requests missing authentication headers or cookies were still accepted, indicating inconsistent session validation.

### 4. SQL Injection in Authentication (Critical)
Unsanitised input in the login form allowed SQL injection, enabling full authentication bypass.

Full write-ups for each vulnerability are available in `/02-Findings/`.

---

## 🛠 Tools & Techniques Used

- Burp Suite  
- Postman  
- JWT.io  
- SQLMap (for validation only)  
- Manual payload crafting  
- OWASP Testing Guide  
- HTTP request manipulation  
- API enumeration  

---

## 🛡 Remediation Summary

- Enforce server-side validation for all authentication mechanisms  
- Implement strict access control checks  
- Use parameterised SQL queries  
- Avoid storing authorization data in client-side tokens  
- Validate object ownership before returning sensitive data  
- Standardise authentication (header or cookie, not both)  

Detailed remediation guidance is available in `/04-Remediation/`.

---

## 📁 Repository Structure

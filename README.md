# Customer Intake & Contract Automation with n8n

An end-to-end automation workflow built with **n8n** that receives customer requests, validates the data, prevents duplicate submissions, stores customer information, generates a personalized contract, and prepares a Gmail draft with the contract attached.

## Overview

This workflow automates a simple customer intake process.

When a new customer request is submitted:

1. The request is received through a Webhook.
2. Customer data is normalized.
3. The email address is validated.
4. Google Sheets is checked for duplicate email addresses.
5. New customer requests are stored in Google Sheets.
6. A copy of a Google Docs contract template is created.
7. Customer information is inserted into the contract.
8. The contract is downloaded as a document.
9. A Gmail draft is automatically created.
10. The generated contract is attached to the email draft.

The email is **not automatically sent**, allowing manual review before sending.

---

## Workflow

```text
Customer Request
      ↓
Webhook
      ↓
Normalize Customer Data
      ↓
Validate Email
   ┌─────────────┐
   │             │
Invalid        Valid
   │             │
Error        Check Google Sheets
Response          ↓
             Duplicate?
             ┌──────────────┐
             │              │
            Yes             No
             │              │
      Duplicate Response   Save Customer
                            ↓
                     Create Contract Copy
                            ↓
                     Fill Contract Template
                            ↓
                     Download Contract
                            ↓
                     Create Gmail Draft
                            ↓
                     Success Response

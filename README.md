# Channel Middleware

Shared Express operations for Jamuna Bank PLC channel APIs. These are the core-facing helpers a channel should call instead of inventing its own cheque, customer, and account posting.

This repository is a sanitized public sample. It does not include the live route table or any core host.

## What I owned

I built a set of posting and enquiry operations the channels share: customer create, deposit account, standing instruction, stop cheque, cheque deposit and correction, clearing, NEFT and RTGS debit, and customer or account enquiry. The same validation and error shape wraps each one.

## Operations the channels share

- Enquire customer, branch, and linked accounts
- Create customer and create deposit account
- Account prefetch, including prefetch by customer and by routing number
- Standing instruction and stop cheque
- Cheque deposit, correction, dishonour, and payment by transfer
- Clearing session maintenance
- NEFT and RTGS debit and standing order
- Amend a posting restriction
- Duplicate statement print

## Technologies

- Node.js and Express
- One module per core operation, not one file that posts everything
- Request id and a single error JSON
- Credentials and core URLs from the environment

## Why this exists

Each of those operations is a place a channel used to copy a request body and a host. When the core contract moved, every copy broke. One middleware owns the body. Channels own the screen.

Portfolio: https://rafiimam.github.io/rafi_portfolio/

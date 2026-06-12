---
title: "Email Server"
date: 2012-03-28
forum: Server Platforms
---

### Post by paulwilson5x on 2012-03-28
Hi, I have a Ubuntu server and desktop working and networked in Oracle virtual box. Im making a website and have made a contact form, when I fill in the contact form details and try to send the form by email, I get the response " An error occurred sending mail: SMTP server project-server is unknown. The server may be incorrectly configured. Please verify that your SMTP server settings are correct and try again." New to all this so any good tutorials or advice would be great, thanks.

---

### Post by nsnidanko on 2012-03-29
Firstly, how is your mail sent? Using script's mail() function (or w.e its called there) or you sending it directly via localhost smtp? Also what is project-server? What does it resolve to?

---

### Post by paulwilson5x on 2012-03-29
project-server is just the name of my server, i tried to write a php script to send the email from a tutorial but also got the same error message

---

### Post by mikaelcrocker on 2012-03-29
Are you trying to setup your own SMTP server, or do you care if you go through gmail or sendgrid?

---

### Post by d4m1r on 2012-03-29
Do you have an email server running on the server? Using sendmail or other email server package?

---


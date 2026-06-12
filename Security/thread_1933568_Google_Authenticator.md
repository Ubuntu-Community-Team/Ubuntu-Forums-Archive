---
title: "Google Authenticator"
date: 2012-02-29
forum: Security
---

### Post by mnorgate on 2012-02-29
I have just set up the Google Authenticator on my server and have the following line in /etc/pam.d/sshd

auth required pam_google_authenticator.so

Is there any way to only use this if the user is not on the local network?

---

### Post by cariboo on 2012-03-01
A bump for the move.

---


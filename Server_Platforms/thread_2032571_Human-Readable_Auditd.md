---
title: "Human-Readable Auditd?"
date: 2012-07-24
forum: Server Platforms
---

### Post by TehSteppo on 2012-07-24
Good morning!

Our marketing department has requested that we construct a daily human-readable e-mail report of all altered files on our webservers. Auditd is the only file change auditing system that I'm familiar with, but this doesn't fit the bill as the output is a little... verbose.

Does anyone know of a proper human-readable file auditing solution that is akin to - or works with - auditd?

Thanks in advance!

---

### Post by TehSteppo on 2012-08-08
My one and only bump. Any ideas, anyone?

---

### Post by Cheesemill on 2012-08-08
You could always write an awk script that would take the auditd logs and parse them into a nice human readable format.

It doesn't have to be awk. Perl or python would work as well but this is exactly the sort of situation awk was designed for.
Just use whichever you are most comfortable with.

---


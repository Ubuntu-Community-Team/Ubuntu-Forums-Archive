---
title: "Password reset fails/passwd module not found"
date: 2009-03-23
forum: Security
---

### Post by goshawkjim on 2009-03-23
When I went to log into my system today (OpenGEU, based on Ubuntu 8.10 running on a Dell e1505) I received a notice that I needed to reset my password. I followed the prompts, and entered by current password; but instead of a prompt to enter a new password, I got an error message: change of authentication token has failed.

I've tried to work around this by using a variety of ways of getting to a root prompt and using passwd <username>, but each time I get an error:

passwd: module not found

Any hints on what I should try next?

---

### Post by goshawkjim on 2009-03-24
OK, I found a workaround. I booted using a live cd and edited /etc/shadow to extend the password expiration date. But I'd like to determine why the password reset function isn't working so I can avoid this in the future.

Thanks.

---


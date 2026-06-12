---
title: "pure-ftpd login help"
date: 2007-03-23
forum: Server Platforms
---

### Post by pouncer11 on 2007-03-23
when i telnet to my ubuntus server in the pureftpd it asks for a login

ive tried to login and cant figure it out

user ??? pass ????
is that the setup for logging in?

 help please

---

### Post by invalid on 2007-03-23
Are you trying to login to an ftp server, or a telnet server?
Either way, it should be your username and password (the one you use to log into your system with).

---

### Post by gepatino on 2007-03-23
if you have annonymous enabled, login as that user, otherwise you'll need to login with a user defined in the server.

---

### Post by pouncer11 on 2007-03-23
i telnetted to the server, port 21

then it asks for theftp login like if you were in a browser but it tells me password is required
how do i enter thepassword, the command is pass but it doesnt seem to recognize it

can someone copypasta the form for logging in?

---

### Post by invalid on 2007-03-23
I am a bit confused with what you are trying to describe.

If you are trying to say that nothing shows up when typing in your password, this is normal. The password does not show characters or a mask for security reasons. It is, however, being typed in. Just hit return after you type it, and it should connect.

---

### Post by invalid on 2007-03-23
After re-reading this post, I think I understand what you are trying to ask now.
You are using telnet to login to an ftp server, and don't understand the sequence of commands?

After connecting type
```
user <username>
pass <password>
```

---

### Post by pouncer11 on 2007-03-23
no i know all that
i figured it out
it was a bad install of the ftpd
i just reinstalled and it all worked out fine
ive done this stuff before just couldnt figure out why it wouldnt let me enter a password, the password prompt wouldnt even come up was the problem

---


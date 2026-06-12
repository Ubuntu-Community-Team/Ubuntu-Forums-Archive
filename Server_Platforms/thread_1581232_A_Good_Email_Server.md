---
title: "A Good Email Server"
date: 2010-09-24
forum: Server Platforms
---

### Post by ScriptingPenguin on 2010-09-24
Hello All,

I am just looking for everyone's input on what a good email server package would be. I've looked at several, Courier, DBmail, Cyrius, and so on.

But I am looking for something that supports encryption, either GPG or other means. 
And most importantly, something that will send email encrypted, (think stegnography).

I just want to set up a secure email server, and if a man-in-the-middle attack captured an email in transit, it would be encrypted.

Thanks

---

### Post by Bachstelze on 2010-09-24
GPG encryption has nothing to do with the mail server. You need to do that in your client.

---

### Post by ScriptingPenguin on 2010-09-24
Ahh, thanks for that bit of info.

But is there anything available i can download from a repository for my email server needs?

---

### Post by btindie on 2010-09-24
Any MTA should do what you want to but some are easier to configure than others. My preference would be either Postfix or Exim.
 
If you want to secure the connection between the MUA (client) and MTA (server) then configure it to accept SMTPS/TLS connections, this will secure the transfer between the two.
 
To be able to then transfer the email from your MTA to the destinations MX server securely depends on the server they use. I think by default if Postfix detects that the remote MTA supports TLS it will issue the STARTTLS command and transfer the email securely over a TLS connection, but this all depends on the ability of the far end to accept a TLS connection.
 
If all you wanted to do was encrypt email in transit then the above would solve your problem.
 
To then be able to receive email you then need to run an email server such as Dovecot. You can then use POPS or IMAPS to retrieve the email securely.

---

### Post by Bachstelze on 2010-09-24
The Ubuntu Server Guide has a section about email stuff:

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

---

### Post by lisati on 2010-09-24
Moved to "Server Platforms"

I'd go with the Postfix or Exim suggestions.

---


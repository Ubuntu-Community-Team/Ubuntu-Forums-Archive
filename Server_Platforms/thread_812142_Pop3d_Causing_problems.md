---
title: "Pop3d Causing problems"
date: 2008-05-29
forum: Server Platforms
---

### Post by Ignite_nz on 2008-05-29
Greetings,

I've followed the "perfect server" guide on HowToForge for setting up and Ubuntu 8.04 server, and I've also got ISPConfig installed now too.

([http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)).

Now, I'm kind of used to Apache, Bind, Proftpd etc etc, but when it comes to mail, I'm still learning, as I've only ever used Exchange 2007 for this kind of stuff.

My problem is, I can't login to pop3 with Windows Mail from a desktop within my network. I want to get internal stuff working before I start bothering with external. I created a mail account in ISPConfig, (I'll substitute the name for my own security reasons) let's say for namesake, the username is "foo.com_froggy", and the users email is [email]froggy@foo.com[/email].

That's fine, ISPConfig accepts that. However, when I go to login with Windows Mail, I get this:
> 
Account: '192.168.1.2', Server: '192.168.1.2', Protocol: POP3, Server Response: '-ERR chdir Maildir failed', Port: 110, Secure(SSL): No, Server Error: 0x800CCC90, Error Number: 0x800CCC92

Now, I checked /var/log/mail.log, and saw the following error messages:

> May 30 08:57:25 server1 pop3d: chdir Maildir: No such file or directory
May 30 08:57:35 server1 pop3d: Connection, ip=[::ffff:192.168.1.103]


Now I know it's not a "User does not exist" error, becuase if I login with the username as [email]froggy@foo.com[/email], I'll see this in the log:

> May 30 08:57:35 server1 pop3d: LOGIN FAILED, user=froggy@foo.com, ip=[::ffff:192.168.1.103]
May 30 08:57:40 server1 pop3d: Disconnected, ip=[::ffff:192.168.1.103]

Any ideas? As I'm at a loss over here.:confused:

---

### Post by Ignite_nz on 2008-06-02
Anybody? This is driving me nuts.

---

### Post by quelx on 2008-06-02
Admittedly, I did not read the link you used to setup your server, but you mail server is complaining about not finding a folder, **Maildir**.  Was there a step in those instructions to use **maildirmake** for the users or is it using something like vpop, inotherwords is the user **froggy** a system user in addition to a mail user?

---

### Post by Ignite_nz on 2008-06-04
Thanks. I found an option in ISPCONFIG, one checkbox that says "Maildir create". This solved my problem :)

---


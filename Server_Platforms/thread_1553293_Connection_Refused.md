---
title: "Connection Refused"
date: 2010-08-14
forum: Server Platforms
---

### Post by Vegan on 2010-08-14
I am using TeraTerm for Windows and I am getting a connection refused message from the program.

Do I need to add anything to 10.04?

---

### Post by Bachstelze on 2010-08-14
TeraTerm seems to be a telnet client/terminal emulator. Any reason you have to use it? You probably should be using a SSH client like Putty.

---

### Post by Vegan on 2010-08-14
It supports SSH

---

### Post by Bachstelze on 2010-08-14
> **Vegan said:**
> It supports SSL

Given that the website says "Last updated: Aug 9 1999", it probably uses an old and insecure version of whatever protocol it uses.  If you really want to use it, what port does it try to connect on?

---

### Post by CharlesA on 2010-08-14
> **Bachstelze said:**
> Gice that the website says "LAst updated: Aug 9 1999", it probably uses an old and insecure version of whatever protocol it uses.  If you really want to use it, what port does it try to connect on?
There's a newer version out. [http://ttssh2.sourceforge.jp/](http://ttssh2.sourceforge.jp/)

I'd still stick to putty tbh.

---

### Post by eric_1982 on 2010-08-14
Have you successfully ssh into your Ubuntu server from any other device?

I am not positive if open-ssh is installed or not by default. You could try **sudo apt-get install openssh-server** in the command line of the Ubuntu server and see if that fixes your issue.

---

### Post by Vegan on 2010-08-14
> **eric_1982 said:**
> Have you successfully ssh into your Ubuntu server from any other device?

I am not positive if open-ssh is installed or not by default. You could try **sudo apt-get install openssh-server** in the command line of the Ubuntu server and see if that fixes your issue.

Thanks, that package was what I needed to install.

---


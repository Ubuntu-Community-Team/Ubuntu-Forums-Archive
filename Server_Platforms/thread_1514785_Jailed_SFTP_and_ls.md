---
title: "Jailed SFTP and ls"
date: 2010-06-21
forum: Server Platforms
---

### Post by bward on 2010-06-21
I have setup a jailed sftp server.  Users can log in fine, but when the ls command is run the connection drops.  This happens while using the cli, or a program like Filezilla.  This only happens to the jailed users.  If a non jailed user logs in they can run the ls command without any issues.  Any suggestions on how to fix this or why it is happening?

---

### Post by FunkyFungi on 2010-06-21
Hi bward. I am new to the forums but you're issue sounds interesting. Why are you running the ls command? Do  you not get a directory listing when the user connects?

---

### Post by bward on 2010-06-28
The user does not get a directory listing.  Even a GUI like filezilla runs ls in the background to get a directory listing.  So it seems that the issue is with the ls command.

---


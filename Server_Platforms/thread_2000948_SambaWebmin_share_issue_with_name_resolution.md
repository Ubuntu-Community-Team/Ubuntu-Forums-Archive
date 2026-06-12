---
title: "Samba/Webmin share issue with name resolution"
date: 2012-06-10
forum: Server Platforms
---

### Post by flycast on 2012-06-10
I have installed Ubuntu 12.04 with Samba and Webmin. I set up a simple share with permissions 775. Add a user to the share. Sync my Linux users and groups with Samba.

I can see the server by name "\\server\test" from windows. I cannot access the share by name. I get a message immediately that says that I do not have permission. When I use "\\192.168.10.10\test" instead I get the prompt to log in and I can log in just fine.

The share is working, name resolution in samba is not. Network name resolution seems to be working ... when I ping the server by name in a dos prompt it pings just fine.

What is the issue here? How can I get Samba using names correctly? IP address only isn't very useful.

---

### Post by flycast on 2012-06-11
Hmmm...I changed the server name in Windows networking options and it seems to have solved the issue. I had named the computer "server" when I installed Ubuntu and names Samba "server". That apparently causes the issue.

---

### Post by flycast on 2012-06-11
Is this a bug or intended behavior?
Does this make sense to anybody else?

---

### Post by CharlesA on 2012-06-11
I haven't used webmin, so I don't know what the deal is, but have you tried running smbtree on the Samba box?

---


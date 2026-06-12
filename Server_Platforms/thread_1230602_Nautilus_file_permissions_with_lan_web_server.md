---
title: "Nautilus file permissions with lan web server?"
date: 2009-08-03
forum: Server Platforms
---

### Post by mag1 on 2009-08-03
I've just followed the official ubuntu server guide to setup a lamp server with openssh, i connected by terminal ok and after some searching found out i can access files on the server using nautilus, trouble is im having file permission problems and i have no idea what to do, i've used ubuntu for a few years but am new to the server version and doing things remotely over lan like this, what should i do to get it working?

Also are there any good guides that explain all the settings and stuff a newbie should know with setup and running of a ubuntu server other than the official guide? thanks. :P

---

### Post by cdenley on 2009-08-03
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mag1 on 2009-08-04
I don't understand what that's telling me to do, ubuntu's official help isn't always great which was why i came here in the first place, simply linking me to the permissions page doesn't help much for someone new to ubuntu servers and doing things remotely, i just want to fix this problem with a guide or post if someone is nice enough to thanks.

---

### Post by wojox on 2009-08-04
You need to log in via a terminal and you can do what you want that way.

---

### Post by cdenley on 2009-08-04
> **mag1 said:**
> I don't understand what that's telling me to do, ubuntu's official help isn't always great which was why i came here in the first place, simply linking me to the permissions page doesn't help much for someone new to ubuntu servers and doing things remotely, i just want to fix this problem with a guide or post if someone is nice enough to thanks.

You need to understand file permissions if you're going to administer a server, and I can't do a better job of explaining it than the page I linked to. It sounds like there is no "problem", but you are just trying to modify files which you don't have permission to modify. You can give yourself permission, as explained in the page I linked to, but depending on the file, that might not be a good idea. Some files you should simply edit as root. However, it generally is not safe to give access to root remotely, so you won't be able to have a remote nautilus session as root. As wojox said, you would need a terminal session so you can edit files with "sudo nano filename". I can't give you a specific solution to your problem unless you give me specific details about your problem.

---


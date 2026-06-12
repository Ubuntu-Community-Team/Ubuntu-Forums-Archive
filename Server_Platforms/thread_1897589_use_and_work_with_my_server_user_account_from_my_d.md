---
title: "use and work with my server user account from my desktop"
date: 2011-12-19
forum: Server Platforms
---

### Post by herbert tamayo on 2011-12-19
Hi, I'm new in admin servers, i have this question:

I heard that it is unsecure work directly to my server, you know, sit in front of it and do configuration, also i'm far of the server, in the server I've created my user account, so, my question is:

what is the software/command to access from my pc desktop and log into my server using my server user account and do things like: update databases, update php code, admin dns, mta, etc, what is the way?

second questions: in linux is also used the term "remote desktop"?

I want to say it that I'm using ubuntu server 11.04, I'm not looking for graphical mode, I want to do it all from the console, so, If you have suggestions would be welcome.

regards

---

### Post by CharlesA on 2011-12-19
I don't believe it is really "insecure" to work from the physical console, but you can use SSH to admin from your workstation instead of going to the server room.

Keep in that that ssh provides shell access and secure it with that in mind.

As for remote desktop, it depends on what you refer to as "remote desktop."

It sounds like you are looking for openssh-server.

---

### Post by Lars Noodén on 2011-12-19
As Charles suggests, install openssh-server on your server and then connect with ssh from your desktop.  It's a really nice way to work.  One tip about that.  That is if your server is facing the open Internet, you might want to consider using [keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) for authentication and turning off password authentication.

---


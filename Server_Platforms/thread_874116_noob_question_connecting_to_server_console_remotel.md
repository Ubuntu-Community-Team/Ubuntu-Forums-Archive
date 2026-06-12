---
title: "noob question: connecting to server console remotely"
date: 2008-07-29
forum: Server Platforms
---

### Post by ehull82 on 2008-07-29
Hi everyone,
I have a very noob question.

How do I connect to the console of my computer running Ubuntu Server from a remote computer?

I've setup a LAMP server on a spare machine of mine and I'd like to be able to connect to it using my Ubuntu Desktop machine.  I've connected to a linux server from a windows box in the past using PuTTY but I can't seem to figure out all the steps needed to do the same for these two machines.

Do I need to enable anything on the server to allow remote connections? Do I need to install software on my Desktop to connect with?

Any help is welcome.

Eric

---

### Post by trigsenior on 2008-07-29
hi,
Im not an expert in servers but i recommend you use ssh to connect to your machines. As it is secure and can also be used with putty. 

Here is a link howto set it up 

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

PS: not sure if ubuntu has ssh already installed if not a simple sudo apt-get install ssh would fix it.

---

### Post by ehull82 on 2008-07-29
That helped! Thank you!

---


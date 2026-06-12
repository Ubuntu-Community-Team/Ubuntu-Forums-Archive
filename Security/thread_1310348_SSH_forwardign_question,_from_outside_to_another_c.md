---
title: "SSH forwardign question, from outside to another computer on the network"
date: 2009-11-01
forum: Security
---

### Post by kartal on 2009-11-01
Hi

I am connecting to my computer regularly from outside via SSH. Everything works great. The only thing I cannot figure out is how to connect to another computer and maybe mount some folders from the second computer on the network via the same SSH session.

I have 2 computers
1-192.168.2.110 (Ubuntu, the main computer that has the SSH running)
2-192.168.2.120 (Windows, the one that I also want to be able to access from outside)

I do not want to run another SSH on the second one since it is my workstation. I also do not want to open multiple ports on my router for multiple ssh forwarding schemes. I want to be able to connect to No(1) and the have the ability to mount some drives-folders from No(2) 

Within my network these 2 computers can communicate well. I can share folders open files between eachother. There are no user name, rights problems.


Any suggestions ?

thanks

---

### Post by woodside100 on 2009-11-01
My favorite post on the subject:

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

I should clarify after rereading your post.  Anything you Mount on the remote machine should be accessible in the same way you currently access locally stored resources.

---

### Post by treymul on 2009-11-02
Have a look at this site:  [http://linuxgazette.net/115/chirico.html]("http://linuxgazette.net/115/chirico.html")

I use this set up with my computers.  You can log into both of them with only one port open on your router.

---

### Post by kartal on 2009-11-02
Hi

Thank you so much for useful information. I will try these solutions today.


cheers

---

### Post by woodside100 on 2009-11-02
> **treymul said:**
> Have a look at this site:  [http://linuxgazette.net/115/chirico.html](http://linuxgazette.net/115/chirico.html)

I use this set up with my computers.  You can log into both of them with only one port open on your router.

 You can also use ssh tunnels within Putty on Windows to same end.

---

### Post by __p1n__ on 2009-11-02
Although I am not an admin my personal favorite tool for remote windows management is a meterpreter shell.

---


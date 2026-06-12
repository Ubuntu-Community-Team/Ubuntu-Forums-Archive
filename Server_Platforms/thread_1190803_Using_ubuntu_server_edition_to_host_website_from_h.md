---
title: "Using ubuntu server edition to host website from home.."
date: 2009-06-18
forum: Server Platforms
---

### Post by heeman453 on 2009-06-18
Hi everyone, I am still a novice in ubuntu and trying to set up a website and host it from home using ubuntu server..I have followed a step by step tutorial to install from this link [http://www.youtube.com/watch?v=lBiNOqims7o](http://www.youtube.com/watch?v=lBiNOqims7o) and I have installed putty on the windows platform.When I run putty from windows I got successful but once I tried to run psftp, I got stuck it seems to ask me to log in to server but I can't.Can anyone help here?Thanks in advance.> 

---

### Post by ghen on 2009-06-18
What happens when you try to log in under psftp, does it say invalid password or something? It should be the same user name and password that you use for the normal putty ssh connection, IE: a user on the ubuntu box.

I just tested it on my server where the only connection package installed is openssh-server so it should work without flaws on a default setup.

Is this computer on the same subnet as yourself? If not, its possible that port 21 is blocked along the way somewhere. (I assume that psftp is using ftp of course, I don't know the program)

---

### Post by heeman453 on 2009-06-18
When I run putty it's fine and once I minimize and try to run psftp then I get this message : no host name specified ; use "open host.name" to connect . 
Any help wold be appreciated..

---

### Post by ghen on 2009-06-18
Oh ok, so you have to run the open command with the hostname or IP address of your server.

So when you get that prompt type:

open 192.168.1.100 

or whatever your server's IP address is.

Then it will ask

login as: 

where you can type in your normal user name

---

### Post by heeman453 on 2009-06-18
But that mean I will not be able to run psftp within putty?Have a look at the link I mentioned before then you will understand what I mean.. Thank you for helping me.

---

### Post by v3xtra on 2009-06-18
It's port 22...the SSH port.  Not the default FP port, of 21.  That may help you.

---

### Post by heeman453 on 2009-06-18
Thank you for helping me,the solution was quite straight forward thanks to this thread..The step by step tutorial did not mention that..but thanks to this forum and Ghen my server is up and running.The problem I had is I followed this turorial and I got a straight connection to ubuntu server using putty but when it comes to use psftp then I got stuck..Few searches on google said something like name.host etc which confused me.But instead I wrote what Ghen gave me and bingo.!!!I know many of you will come accross this problem and I would strongly suggest this goes on and ubuntu is great.Hail to ubuntu..Hip Hip Pip!!Hurray!!That would make all of you linux lovers smile now!!!

---


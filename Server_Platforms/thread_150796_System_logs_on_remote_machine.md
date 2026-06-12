---
title: "System logs on remote machine"
date: 2006-03-26
forum: Server Platforms
---

### Post by RicJD on 2006-03-26
Hey guys

I'm setting up a server and want to easily monitor the logs from my own desktop machine.  Basically i would like to have them loaded up on my desktop using something like 'root-tail'.  So I have two questions:

1: Is root-tail ok to use on ubuntu? i know some of these kind of programs don't like nautilus and so forth? or is there better programs out there to monitor logs?

2: Will I be able to use 'root-tail' or any other recomended program to read from the server easily?  I know syslog could store the log of my server on my desktop, but i would prefer to keep them on my server for when i ssh into my server remotly (as I don't let ssh access to my desktop at all for paranoid security reasons).  I was thinking of setting up a shamba/nfs which is mounted on my desktop at boot up, but was wondering if this could pose security concerns for the server?

Thanks in advance

Rick

---

### Post by claes on 2006-03-27
The easiest way would be to ssh to your server with:

ssh -X username@servername

And from there you run your graphical log monitor tool. Then the X display would be tunneled through ssh to your workstation. No need to share anything out on the network. 

This is not the only solution to your problem. But it's the way I would do it. 

Claes

---

### Post by RicJD on 2006-03-27
So would I be able to use root-tail ok with ubuntu and gnome?  also i should then be able to tunnel root-tail through ssh?

---

### Post by claes on 2006-03-27
Well all X programs would work through the tunnel. The problem is that root-tail output the text to the root window. And nautilus draws over that. So you wont see anything if you run nautilus. :-(

Claes

---

### Post by RicJD on 2006-03-27
thanks claes, i thought that would be the case.  Would there be anything out there which would work with well with nautilus and i can easily monitor the logs? I never reallt had the need before to monitor logs like this before.

---


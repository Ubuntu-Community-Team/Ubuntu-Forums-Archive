---
title: "X versus VNC (over SSH)"
date: 2007-11-14
forum: Server Platforms
---

### Post by kooseefoo on 2007-11-14
Hey!

I'm running a LAMP (among other things) server on Ubuntu Server Edition 7.10 (Gutsy).

I'm thinking about sending some sort of graphical environment through SSH. Although it isn't necessary, it seems like something that would be kind of fun to do.

So, the two possibilities I've stumbled upon are doing a direct X through SSH or sending VNC through SSH. They both seem fairly simple to do...

What are the advantages and disadvantages of each? If I wanted to have a full gnome or kde session (or xfce, I suppose), which would work better?

Thanks,
Chris

---

### Post by HermanAB on 2007-11-14
People coming from the Windows world like to have a complete desktop.  They typically prefer VNC for a few months, till they get tired of the slowness or finally realize that they already have a desktop so it is redundant to have another one.

More seasoned users simply use ssh with X forwarding enabled and directly run whatever program they want on the remote system, without bothering with a second desktop.  Something like this:
$ ssh -X joesixpack@server sudo gedit /etc/fstab
password

and up pops gedit with fstab on the remote machine.

Even more seasoned users will have certificates set up so that they don't even have to enter a password...

It kinda depends on whether you want to play, or whether you want to get the job done...

Cheers,

Herman

---

### Post by kooseefoo on 2007-11-14
Thanks!

This server has been running for a bit over a year without any graphical interface at all, and I've been using ubuntu on my desktop for a couple years now. I guess that means that I'm not migrating from Windows anymore... thanks for the tip on forwarding X through SSH.

---

### Post by HermanAB on 2007-11-15
Simply install the graphical programs you need and run them remotely over ssh.  For server admin, you only need a handful, like firefox, gedit and nautilus and well, I can't really think of anything else that would be useful.  Running a whole gawddam desktop just to launch gedit is kinda silly, so I just use ssh.

---

### Post by kooseefoo on 2007-11-15
Here's an interesting quirk:

I have everything I want working - I can run gedit or... well, whatever, through the terminal. However, firefox ends up freaking out...

First off, this is a double-pass SSH (I'm SSHing into a server, and from there into a workstation within a protected network). When I launch firefox, it wants to go through my university's network login page, and I get stuck in an infinite loop. How does that work?

Thanks,
Chris

---


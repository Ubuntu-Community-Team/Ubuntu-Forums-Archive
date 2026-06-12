---
title: "Windows Server 2003 or Ubuntu Server"
date: 2010-06-10
forum: Server Platforms
---

### Post by Roly25 on 2010-06-10
Hi,
 I'm running Ubuntu 10.04 Desktop Edition on my Advent Netbook and was wondering if I should connect it to a Server running Windows Server 2003 or is it better to connect it to a server running Ubuntu Server Edition.  I've run a home network using Windows XP Professional and Windows Server 2003 in the past and as I've now moved over to Linux I don't know what the best Server OS to use would be?

Roland

---

### Post by clrg on 2010-06-10
Actually, it doesn't really matter whether you are getting your services from an Ubuntu Server or a M$ Windoze Server. If you happen to already have either of those running, just stick to it. Server migrations are nasty.

But now you ask, use an Ubuntu Server. Stable, secure, really fast, free, runs on most architectures, open source, need I say more?

---

### Post by Roly25 on 2010-06-10
> **clrg said:**
> Actually, it doesn't really matter whether you are getting your services from an Ubuntu Server or a M$ Windoze Server. If you happen to already have either of those running, just stick to it. Server migrations are nasty.

But now you ask, use an Ubuntu Server. Stable, secure, really fast, free, runs on most architectures, open source, need I say more?

I'm not currently running a Server OS as I've now got to move my Server over to a Notebook as I've not got as much space as when I was running a Windows network using Windows Server (not as much space in my bedroom as there was when I was living at my mums) to have a Tower Server I've run Windows Server on a Laptop before so know that for my needs a Notebook or Laptop will make an adequate Server.

Is ubuntu Server easy to configure and manage? 

Are there any Microsoft Exchange Server quality group-ware Servers that are free, as I would like to keep my Network to free software only?

Roland

---

### Post by clrg on 2010-06-10
What do you need groupware for? And you can't compare a Windoze Server to an Ubuntu Server, since those are very different operating systems. 

If you how to use a system using nothing but a shell, then you'll be fine. If you're stuck as soon as there is no GUI application to accomplish a task, you'll not get happy with an Ubuntu Server (unless you are willing to do a lot of RTFM :> ).

I'm curious. What do you need Exchange-like software for in a private household?

---

### Post by kevin11951 on 2010-06-10
> **Roly25 said:**
> I'm not currently running a Server OS as I've now got to move my Server over to a Notebook as I've not got as much space as when I was running a Windows network using Windows Server (not as much space in my bedroom as there was when I was living at my mums) to have a Tower Server I've run Windows Server on a Laptop before so know that for my needs a Notebook or Laptop will make an adequate Server.

Is ubuntu Server easy to configure and manage? 

**Are there any Microsoft Exchange Server quality group-ware Servers that are free, as I would like to keep my Network to free software only?**

Roland

As to that question, Zimbra is the best IMO, but it requires 2GB of RAM sitting idle!  Citadel/UX, is uglier, but supports a lot of the same features, and can run on anything.

Citadel is also in the repos, just install the package "citadel-suite", and answer the questions that apply.

---

### Post by Roly25 on 2010-06-10
> **kevin11951 said:**
> As to that question, Zimbra is the best IMO, but it requires 2GB of RAM sitting idle!  Citadel/UX, is uglier, but supports a lot of the same features, and can run on anything.

Citadel is also in the repos, just install the package "citadel-suite", and answer the questions that apply.

Thanks for the info.

A little off topic for this forum but can the Desktop Edition of 10.04 be used as a Server or can I only use the Server Edition of 10.04?

Roland

---

### Post by Lucky. on 2010-06-10
> A little off topic for this forum but can the Desktop Edition of 10.04 be used as a Server or can I only use the Server Edition of 10.04?

That's a great question.  Desktop can be used like a server, and server can be used like a desktop.  The major difference is that Desktop edition has a GUI (and hence takes up more system resources).  If you install the right packages, you can basically "convert" Server edition into Desktop edition.

If you're looking for an easier transition and you have the hardware to support it, there's no harm in trying out Desktop edition as as server.  However most of the server software & tutorials are are command line-based anyway, so over time you'll probably be heading towards the straight server edition.

---

### Post by arrrghhh on 2010-06-10
Yea, the main difference is the server edition has no GUI as Lucky. pointed out.  So less overhead from lack of a GUI.  You can easily install the exact same server-based applications on a desktop install - you can even have them run at boot (IE without a user logging in) if you wish, just as you would have a server setup.  I did this for a while before I got tired of my gf rebooting my 'server' to play games on the Windows side.  Build a new box, GUI-less on very meager hardware... I love it!

---

### Post by Roly25 on 2010-06-10
> **clrg said:**
> What do you need groupware for? And you can't compare a Windoze Server to an Ubuntu Server, since those are very different operating systems. 

If you how to use a system using nothing but a shell, then you'll be fine. If you're stuck as soon as there is no GUI application to accomplish a task, you'll not get happy with an Ubuntu Server (unless you are willing to do a lot of RTFM :> ).

**I'm curious. What do you need Exchange-like software for in a private household?**

I like playing around with things and learning how they work, then if I ever find myself needing to set up a Groupware system I know how to do it without having to learn how to do it.

Roland

---

### Post by Roly25 on 2010-06-10
> **Lucky. said:**
> That's a great question.  Desktop can be used like a server, and server can be used like a desktop.  The major difference is that Desktop edition has a GUI (and hence takes up more system resources).  If you install the right packages, you can basically "convert" Server edition into Desktop edition.

If you're looking for an easier transition and you have the hardware to support it, there's no harm in trying out Desktop edition as as server.  However most of the server software & tutorials are are command line-based anyway, so over time you'll probably be heading towards the straight server edition.

I've played with the Server features in SUSE Linux before and found that to run on an Ancient Packard bell Desktop with no problems other than getting Samba to run as a Windows Domain Controller.  So My 1.60GHZ AMD Turion 60 x2 with 1GB of RAM and 160GB HDD should run Desktop Edition as a Server with no problem.

Roland

---


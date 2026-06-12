---
title: "reinstall ubuntu without physical access?"
date: 2012-04-28
forum: Server Platforms
---

### Post by P3t3r on 2012-04-28
Is it possible to install Ubuntu from Ubuntu? I'm currently running a 10.04 LTS server on my VPS, and I'd like to switch to 12.04. And since upgrading often results in problems, I'd prefer to just install a new 12.04.

However, all the manuals I can find start with "create and insert install cd/usb". Which is quite cynical as you know just as well as me that people don't have physical access to their servers in datacenters -- and since it's a VPS things are even more complicated.

So I had hoped that there would be a script that would just download 12.04 to a folder /install, add a proper entry to grub to launch that installer (with VNC/SSH support of course) and do a fresh install from there? (or make a new partition instead of /install if that's better)

---

### Post by SeijiSensei on 2012-04-28
No, you'd need to be physically present unless you have some kind of KVM switch that supports TCP/IP connections. One possibility that some VM providers offer is the ability to connect to the host machine and operate on your machine from there.  I did that once with a [Linode]("http://www.linode.com/") on which I had accidentally deleted the OpenSSL libraries and then could no longer use SSH.  But I don't think I'd take that route for a complete system installation.

I just upgraded a server from 11.04 to 12.04 over SSH without a hitch.  You have to take it one step at a time, though, by running "sudo do-release-upgrade" and upgrading through each intermediate release.  In my case I first upgraded to 11.10 then 12.04.  I'm not sure how that would work for 10.04 since 10.10 has now reached end-of-life.

If you log into the server as an ordinary user over SSH you should see a message about upgrading to the next available release.

That said, if I were you I'd just rent a new VPS with 12.04 already installed, then migrate the services you need to that machine.  Once you're sure it's working the way you want, you can terminate your contract for your current machine.  That's a lot more reliable than upgrading.

---

### Post by CharlesA on 2012-04-28
You can upgrade directly from 10.04 to 12.04 can't you?

---

### Post by jonnyboysmithy on 2012-04-28
[http://omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go/](http://omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go/)
A review on the upgrade proccess from 10.04LTS to 12.04LTS.

---

### Post by Jonathan L on 2012-04-28
Hi p3t3r

> **SeijiSensei said:**
> I'd just rent a new VPS with 12.04 already installed, then migrate the services

Seiji's advice is excellent.  It's so much easier to check that the new one works how you want, and you're focussed on your data not lots of programs.  Especially as 12.04 is so new.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-04-28
> **Jonathan L said:**
> Hi p3t3r



Seiji's advice is excellent.  It's so much easier to check that the new one works how you want, and you're focussed on your data not lots of programs.  Especially as 12.04 is so new.

Kind regards,
Jonathan.
+1. I would recommend Linode if you want to get a VPS.

---

### Post by d4m1r on 2012-04-29
> **Jonathan L said:**
> Hi p3t3r



Seiji's advice is excellent.  It's so much easier to check that the new one works how you want, and you're focussed on your data not lots of programs.  Especially as 12.04 is so new.

Kind regards,
Jonathan.


That's a lot of work...is it a OpenVZ VPS or? I would FTP the files you need to your PC, reformat the VPS with 12.04 (if you can do autoreloads from SolusVM) and then just transfer all your files back....Using my method though, you have to reinstall your applications though.

---

### Post by SeijiSensei on 2012-04-29
That won't really work for a production server if downtime is unacceptable, though.  You could easily be offline for a couple of hours, and more if things go wrong along the way.

---


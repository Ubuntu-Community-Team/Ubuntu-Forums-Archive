---
title: "Lotus Domino 8.5 on Ubuntu"
date: 2009-06-12
forum: Server Platforms
---

### Post by Trialces on 2009-06-12
Hello,
I cant't find appropriate version of Lotus Domino for Ubuntu. There are versions for Windows or even linux but not for x86 or 64bit platform. No problem to find Lotus Sametime or Lotus Notes that run on Ubuntu. I know some of You have intalled Domino on Ubuntu. Please help.

---

### Post by rod40cool on 2009-07-15
> **Trialces said:**
> Hello,
I cant't find appropriate version of Lotus Domino for Ubuntu. There are versions for Windows or even linux but not for x86 or 64bit platform. No problem to find Lotus Sametime or Lotus Notes that run on Ubuntu. I know some of You have intalled Domino on Ubuntu. Please help.

Hi Trialces,

I have just installed Domino 8.5 Linux server version x86 on a Ubuntu 9.04 32 bit server running in Sun VirtualBox. The version you need is the [32 bit Linux version]("http://www-01.ibm.com/support/docview.wss?rs=463&uid=swg27013072") Domino for Linux is only supported by IBM on SUSE and Redhat but it works perfectly on Ubuntu server. There's a few tricks to getting in installed, like downloading about 6 library packages, and temporarily installing a desktop (I used Fluxbox and Xorg packages) to run the Java based server setup or Java console, but if you have a server just for Domino you can run it from command line once you've setup the server. I'm happy because I have a Domino 8.5 server (albeit the 90day trial version) running in a 256MB VirtualBox image on my laptop ;) so now I can study for my Domino Admin exam.

Rod

---


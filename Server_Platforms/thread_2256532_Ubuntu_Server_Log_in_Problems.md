---
title: "Ubuntu Server Log in Problems"
date: 2014-12-13
forum: Server Platforms
---

### Post by daniel228 on 2014-12-13
I've installed Ubuntu Server 14.04.1 and I'm struggling to Log in via the Log in screen. Its taking my name but their is nothing appearing when I enter my password. I've set up a File server using the LTS 14.04.1.

I will say I'm completely new to Ubuntu and Ubuntu server. I have no experience, and even logging in is proving to be difficult so god knows how I'll get on with the acutall learning of the server OS it self.

It seemed pretty easy to install but when asked for "password" Its not even showing up " * " as hashed out.

Any help please.

---

### Post by steeldriver on 2014-12-13
Hello and welcome to the forums

What you are describing sounds normal - the password characters are not echoed to the screen (not even as " * ") - just type the password then hit the "Enter" key

---

### Post by daniel228 on 2014-12-13
Does Ubuntu 14.04.1 LTS Server come with a GUI? Or is it all text based. Will I have to learn the full set of commands I'm being presented with? I have no experience with this?

---

### Post by steeldriver on 2014-12-13
The Server ISO comes with no GUI - that's really the point of it. If you are more comfortable with a GUI, you can either re-install using a Desktop ISO or install one of the GUI packages on top of the server (either a full-featured Desktop, or a minimal GUI such as LXDE or xfce4 without the additional "desktop" packages).

---

### Post by daniel228 on 2014-12-13
No problem I've been reading up on the GUI I can install over the top as a light weight or use the command text interface. When I installed the Ubuntu Server this Ver. it was 14.04.1 and I did not do any updates to the system. I think I have the bare minimum on the system. Can you tell me how to update the Server threw the text based interface and will also I have to familiarize my self with the Command based Text interface.

---

### Post by TheFu on 2014-12-14
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a link to a book that will help you learn the shell.

There are 10,000 different ways to learn this stuff but none are easy for someone without any UNIX-like OS experience.

If you want the bare minimum, [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) explains the commands to get started, but it is not enough to secure a server.

---


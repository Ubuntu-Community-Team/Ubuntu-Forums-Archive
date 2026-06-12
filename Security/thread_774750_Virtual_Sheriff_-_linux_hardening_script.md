---
title: "Virtual Sheriff - linux hardening script"
date: 2008-04-29
forum: Security
---

### Post by takedown on 2008-04-29
Hello. I write a interactive script like bastille in pure shell.
This script check you settings and installed software,after that it finds possible insecure settings and suggest a solution.
Why i write it? Well, im too lazy do a security realted settings after fresh install again and again. And bastille have a poor functionality.
For easiest maintain i make a modular structure, so if you what add some module this can be very easy without fully understand my code. Just write a module file, include it to main distribution specific file and use you functions.
You can also simply do a rollback and automatic apply you changes (similar to bastille).
Use it on you own risk, because some settings is critical so you can break something. If you dont undestand what sheriff talking just skip question and if you want ask me.
All settings based on default installation of Ubuntu 8.04 Server.
Tested on Ubuntu 7.10 and 8.04 , but almost all should work on any other ubuntu-based and debian-based(more specific, later may be i make a debian module).
[Launchpad link]("https://launchpad.net/virtualsheriff")
In archive you will find install and uninstall scripts which help you with installation procedure. Maybe later i pack all to .deb.
Also if you want add you distribution module to script send to me a complete security guide to you distribution(good example is: [Debian Security Guide]("http://www.debian.org/doc/manuals/securing-debian-howto/")) or just write them from scratch and send it to me.
Send to me feedback.

---


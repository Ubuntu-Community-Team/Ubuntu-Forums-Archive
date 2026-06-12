---
title: "File sharing server setup + Desktop useable"
date: 2009-05-27
forum: Server Platforms
---

### Post by Dominating on 2009-05-27
OK heya all :), well I'm really noob but hey found a old pc and been playing around with ubuntu again at the moment i have ubuntu 9.04 installed on this old PC basically i just want to setup a file sharing server but being able to use the comp for searching the web playing music and videos, I'm thinking for a desktop manager XFCE/Openbox i need something that is quick and easy and low resources because the comps specs are fairly low something like 756 ram and 2ghz single core processor, also i am trying to find a guide to setup a simple file sharing server that i can access from macs and windows :)

---

### Post by Jekshadow on 2009-05-28
Just install the File Server package and (if you want to access it remotely), setup your router to forward ports 21 (FTP) and 22 (Secure FTP) to the target computer.

---

### Post by cariboo on 2009-05-28
There is nothing wrong with your computer specs, that is more then adequate for what you need. You can setup X forwarding, by installing openssh-server to remotely access gui programs on the server, or you just planning to run a desktop computer as a file server?

---


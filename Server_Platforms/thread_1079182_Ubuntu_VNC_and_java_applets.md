---
title: "Ubuntu VNC and java applets"
date: 2009-02-24
forum: Server Platforms
---

### Post by danielw84 on 2009-02-24
Hi All,

I have an Ubuntu server for connecting to the office when I am not in the office. After connecting with a VPN to the office I make a connection to this server with VNC to work on it from outside the office. (remote desktop)

We have a CRM that's have been written in java. This is accessible with  a webbrowser. (in my case firefox)

I have the problem that in java applets my numpad doesn't work. It's only in the CRM (and other java applets, which I have search on the internet like old math java applets to test) So for example I can use my numpad in OpenOffice when I am connected via VNC tot the server. 

When I directly login to the server I don't have this problem. So it's a combination of VNC and JAVA that aren't working together.

Some technical information of the server:
I use Ubuntu 8.10 (intrepid) with GNOME (2.24.1).
I installed VNC using this manual: [https://help.ubuntu.com/community/UbuntuLTSP/GDMVNCInetdssh](https://help.ubuntu.com/community/UbuntuLTSP/GDMVNCInetdssh) 

Does somebody has this same problem, or maybe better, a solution?

Thanks,
Daniël

---

### Post by deeler on 2009-10-07
I have the exact same problem.

We use a debian linux server with 25 VNC connections connected to thinclients (Axel Platine Terminal or regular VNC viewer in Linux)

I've tried different vncserver in combination with different clients.
Nothing worked...

When doing some tests we found an even stranger issue:
We created a very simple java jar file that echoes text and what happens:
The first time we run this program over VNC and we type "1 2 3 4 5 ..." no text is echoed. We close the program, run it again and then you can type the keys previously entered !!! So each time a key doesn't work, type the key and the next time the program is started the key will work!
How strange is that?

has anyone got a clue :confused: we're quite desperate.
A workaround is to set a .Xmodmap file for each user, but this screws up the keyboard layout for other non-java applications. 

please help

---


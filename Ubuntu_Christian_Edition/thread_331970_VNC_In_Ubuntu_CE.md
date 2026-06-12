---
title: "VNC In Ubuntu CE"
date: 2007-01-05
forum: Ubuntu Christian Edition
---

### Post by runkidrun on 2007-01-05
I would really like to install a VNC program so I can help my friends...Right now I really don't have a preference of which VNC program anyone suggests....I just cannot find any VNC programs in the "ADD/REMOVE" pane or even any .deb packages on the internet. I know people have got it running before...but how?

---

### Post by meng on 2007-01-05
Sounds like you need to read a tutorial on how to install software in general:
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

That said (please do read it, that way you won't waste your time as you've already done)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

wiki.ubuntu.com is a great place to find stuff.

---

### Post by runkidrun on 2007-01-05
O.K. Your site says that I can install .rpm's which I thought only worked on other distros. That's good. So I found a VNC program called tightvnc. I found three rpm packages. One says "RedHat 7.x" and the other just says "source rpm" what should I choose?

---

### Post by runkidrun on 2007-01-05
Oh, wait...I just read the other link....So I don't have to install any packages? It's there already in the base system?

---

### Post by meng on 2007-01-05
Installing rpm is a last resort, I would not recommend it. Installing from the official Ubuntu repositories should always be the first option. Enable extra repositories (multiverse/universe) here's a guide to that:
[https://wiki.ubuntu.com/Repositories/Ubuntu](https://wiki.ubuntu.com/Repositories/Ubuntu)

If you really want a tightvnc client, you could try:
sudo aptitude install xtightvncviewer

Note that although you may be using UbuntuCE, your question is not specific to the Christian edition, and in future you should consider posting your questions to a wider audience.

---

### Post by runkidrun on 2007-01-05
I don't want to set up a server..just use a viewer...but am I correct in thinking that I could just use the terminal server client for that purpose as suggested in that link you gave me?

---

### Post by meng on 2007-01-05
> **meng said:**
> If you really want a tightvnc client, you could try:
sudo aptitude install xtightvncviewer
This looks like a viewer. Have your friends got a VNC server set up on their computers?

---

### Post by stalker145 on 2007-01-05
> **runkidrun said:**
> I don't want to set up a server..just use a viewer...but am I correct in thinking that I could just use the terminal server client for that purpose as suggested in that link you gave me?

If you do not want to set up a server and are connecting to another computer that already has VNC or some other similar software running, all you need to do is type into the terminal ```
vncviewer xxx.xxx.xxx.xxx
```where the x is the IP address of the machine you are trying to connect to. 

On the other hand, if you wish to set up a server on Ubuntu, it's as easy as going to Preferences->Login (I believe), choosing remote login, and setting the applicable boxes on that screen. I'm not at my Ubuntu box now (I'm on Windows at work](*,) ) so I may be mistaken, but it's there.

---

### Post by runkidrun on 2007-01-05
Thanks for all your help. I will be testing out the terminal method shortly...

---

### Post by qalimas on 2007-01-05
Applications > Internet > Terminal Server Client

It is a VNC Viewer if I am not mistaken.

---


---
title: "SMTP from XP Host to VirtualBox Ubuntu Guest?"
date: 2008-09-11
forum: Virtualisation
---

### Post by ddmorin on 2008-09-11
Because I have no SMTP server available for my day to day sandbox development, I thought I'd make use of a VM as a place where I could connect on port 25 and dump mail, without having to simulate it some ugly way.

I've been through the necessary installs, done the VBoxManage thing to "setextradata" for GuestPort=25 and HostPort=25.  However, whenever I attempt to telnet localhost 25 from my Windows box, it looks like a connection is made, but then immediately upon any keystroke, it exits out.  Have I missed a step?  the Ubuntu install registers no connection at all (not sure if I'm looking in the right place, but neither /var/log/mail nor /var/log/syslog show anything).

I know that it's at least attempting to connect because before I did the VBoxManage steps, attempting to telnet just stopped with a "Connection refused", as I would expect. Now it seems like something is listening, but then denying the connection.  Is there something I have to do at the Ubuntu level (using sendmail, by the way), to allow the connection to come in?

As far as I know I'm using the latest version of VB (just downloaded it yesterday), and Ubuntu 8.04 desktop edition on which I installed sendmail.  Locally on the ubuntu box I can telnet localhost 25 and it works.

Thanks!!

---

### Post by pp. on 2008-09-12
> **ddmorin said:**
> whenever I attempt to telnet localhost 25 from my Windows box, it looks like a connection is made, but then immediately upon any keystroke, it exits out.

"telnet localhost" attempts to open a session to itself, i.e. the Windows box. Presumably you want to establish a session with your (virtual) ubuntu box. In that case you have use the IP address of your ubuntu box.

---

### Post by ddmorin on 2008-09-13
> **pp. said:**
> "telnet localhost" attempts to open a session to itself, i.e. the Windows box. Presumably you want to establish a session with your (virtual) ubuntu box. In that case you have use the IP address of your ubuntu box.

True, but in this case I'm trying to set up port forwarding to the virtual box (that's what the "VBoxManage ... HostPort/GuestPort" stuff does).  So when I telnet localhost 25, the vbox driver is supposed to spot this and forward the request to the guest VM.  At least that's how I thought it was supposed to work.  If nothing was listening on 25 I'd just get a connection refused.

---


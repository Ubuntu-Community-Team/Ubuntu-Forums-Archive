---
title: "How do you remotely connect to your computer/server?"
date: 2011-12-09
forum: The Cafe
---

### Post by sandyd on 2011-12-09
On my main server, which runs ESXi, that would be the vSphere client.

Otherwise, KVM over IP

---

### Post by collisionystm on 2011-12-09
> **sandyd said:**
> On my main server, which runs ESXi, that would be the vSphere client.

Otherwise, KVM over IP

Vmware, same as you.

Others, Internally, through the terminal

externally, across a VPN.

---

### Post by lisati on 2011-12-09
It depends on what I'm doing and where I am at the time. From within my internal network I have been known to use SSH, which I have chosen not to make publicly accessible.

If you want to access my server, I don't mind visits to my website (hint: see sig.) but be aware that bad behaviour will be noticed, so behave yourself!

---

### Post by Old_Grey_Wolf on 2011-12-09
The poll needs to allow multiple choice answers.

I may use ssh, cssh, RDP/VNC, VPN, the ESXi vSphere client, on board administrator consoles for blade servers, among many other options.

It depends on the hardware, hypervisor, operating system being used, and what I am trying to accomplish.

---

### Post by Bachstelze on 2011-12-09
Netcat.

---

### Post by collisionystm on 2011-12-09
> **lisati said:**
> It depends on what I'm doing and where I am at the time. From within my internal network I have been known to use SSH, which I have chosen not to make publicly accessible.

If you want to access my server, I don't mind visits to my website (hint: see sig.) but be aware that bad behaviour will be noticed, so behave yourself!



Hmm... what do you have....

21/tcp    closed ftp
25/tcp    open   smtp
80/tcp    open   http
110/tcp   open   pop3
143/tcp   open   imap
10000/tcp open   snet-sensor-mgmt

AND you have your webmin opened up to the world? As soon as I saw 10000 I knew lol.

---

### Post by lisati on 2011-12-09
> **collisionystm said:**
> Hmm... what do you have....

21/tcp    closed ftp
25/tcp    open   smtp
80/tcp    open   http
110/tcp   open   pop3
143/tcp   open   imap
10000/tcp open   snet-sensor-mgmt

AND you have your webmin opened up to the world? As soon as I saw 10000 I knew lol.

Ah yes, I better get in the habit of closing that off when I don't need to access it from outside my network.

(Yes, I have noticed some rascals trying to get in through POP3 and occasionally SASL, this is detected and blocked easily.)

---


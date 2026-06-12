---
title: "SSH Brute Force Attack?"
date: 2011-02-02
forum: Security
---

### Post by PerfectReign on 2011-02-02
This may be the opposite of what normally is asked but...

I  recently installed a solar system on my house. It comes with a [device ]("http://www.enphaseenergy.com/products/products/envoy.cfm")that  takes the readings from my solar panels and passes them out to the  internet. 

[IMG]http://www.perfectreign.com/stuff/2011/20110201_solar_production.png[/IMG]

(I know that is from Win 7, but I'm at work.)

The device runs a micro linux system with an Apache  server so one can do administration. I ran nmap against it and found out  it runs Debian.

   [FONT=Courier New][SIZE=2][COLOR=Blue]21:20 Pacific Standard  Time Scanning 192.168.0.100 [1 port] 
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]... [/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]PORT STATE SERVICE VERSION 
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]22/tcp open ssh OpenSSH 3.8.1p1 Debian 8.sarge.4 
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]80/tcp open http? 
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]...  
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]MAC  Address: 00:1D:C0:04:15:00 (Enphase Energy) 
[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][COLOR=Blue]OS details: Linux 2.6.9 -2.6.31 Enphase Envoy -Products -Enph[/COLOR][/SIZE][/FONT]
  



When trying to ssh into the device, I run across a  roadblock. I'm unable to login.

[FONT=Courier New][COLOR=blue]login as: kai
kai@192.168.0.102's password:
Linux proxy 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010  i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com]("https://help.ubuntu.com/")

Last login: Wed Feb  2 09:28:47 2011 from m3e2736d0.tmodns.net
kai@proxy:~$ ssh root@192.168.0.100
root@192.168.0.100's password:
Permission denied, please try again.
root@192.168.0.100's password:
Permission denied, please try again.
root@192.168.0.100's password:
Permission denied (publickey,password,keyboard-interactive).


[/COLOR][/FONT]

So, given I have "console" access, what can I do? I assume there's a  brute force type of attack (for lack of a better term) but what  program?  I'm somewhat familiar with programs written in Wintendo that  can do such things, but not in Ubuntu.

Ideas?

---

### Post by anomie on 2011-02-02
I don't follow what a "brute force attack" has to do with this thread. 

Do you have access to any of the logs through the web interface? It may be that 1) root's password entry is locked; or 2) root is implicitly or explicitly prevented from logging in over ssh; or 3) something similar.

-------

edit: Ahhhh, got it now. You want help brute forcing the device. Can't help with that one.

---

### Post by cariboo on 2011-02-02
Can you ssh in as a normal user? Root login may be turned off, as it should be.

---

### Post by matt_symes on 2011-02-02
Hi

Assuming it does not void any warranty, have you talked to the technical support of the manufacturer ?

Kind regards

---

### Post by HermanAB on 2011-02-03
BTW, SSH brute force attacks started about 10 years ago and they are pretty stupid.  Change the SSH port from 22 to something else and the problem will go away.

---

### Post by CharlesA on 2011-02-03
If SSH is not exposed then you don't have to worry about bruteforce attacks.

If you are trying to get root access, then I suppose you should talk to the tech support people and see if it's even possible.

The only thing I could find regarding that device and SSH was on someone's blog:
[http://www.friday.com/bbum/2010/03/23/enphase-energys-envoy/](http://www.friday.com/bbum/2010/03/23/enphase-energys-envoy/)

---

### Post by spynappels on 2011-02-03
I expect that this link is used by the company to do remote diagnostics etc and is probably protected by keys and has password login disabled. That's what I would do if I was installing these anyway.

---


---
title: "Trying to get VNC thru firewall?"
date: 2010-07-20
forum: Security
---

### Post by iamgeniusrnti on 2010-07-20
OK, I'm doing something terribly wrong here and it's got to be something I'm overlooking... help?

I have Ubuntu running on an old PE server.  It is running Virtualbox with an instance of Ubuntu inside.  The instance is there to run my honeypot.

The server box IP is192.168.1.10.  The Virtualbox is bridged with it's own IP of 192.168.1.200.  The honeypot daemon is listening to 192.168.1.201 with arpd.

I set up the UFW with DENY. And then enabled only the ports leading to the honeypot scripts which are abound to IP .201.  I then forwarded the ports necessary to run VNC to .200.

Here is the UFW status:
buntu@ubuntu-desktop:/var/lib$ sudo ufw status
Status: active
To                         Action      From
--                         ------      ----
192.168.1.201 21/tcp       ALLOW       21/tcp
192.168.1.201 4444/tcp     ALLOW       4444/tcp
192.168.1.201 5544/tcp     ALLOW       5544/tcp
192.168.1.201 9996/tcp     ALLOW       9996/tcp
192.168.1.201 8967/tcp     ALLOW       8967/tcp
192.168.1.201 9898/tcp     ALLOW       9898/tcp
192.168.1.201 20168/tcp    ALLOW       20168/tcp
192.168.1.201 110/tcp      ALLOW       110/tcp
192.168.1.200 5900/tcp     ALLOW       5900/tcp
192.168.1.200 5901/tcp     ALLOW       5901/tcp
192.168.1.200 5902/tcp     ALLOW       5902/tcp
192.168.1.200 5903/tcp     ALLOW       5903/tcp
192.168.1.200 5904/tcp     ALLOW       5904/tcp
192.168.1.200 5905/tcp     ALLOW       5905/tcp
192.168.1.200 5906/tcp     ALLOW       5906/tcp
192.168.1.200 5907/tcp     ALLOW       5907/tcp
192.168.1.200 5908/tcp     ALLOW       5908/tcp
192.168.1.200 5909/tcp     ALLOW       5909/tcp
192.168.1.200 5910/tcp     ALLOW       5910/tcp

All the forwards to 201, work flawlessly.  But I can't get VNC to punch thru unless I turn off the firewall...


I can VNC view into 192.168.1.10 and thru virtualbox, I can control 192.168.1.200.  I can also VNC view into 192.168.1.200, the virtual appliance, BUT only when the UFW is DISABLED.  When I reenable it, I get this:

MAC=08:00:27:e1:7b:85:00:24:2b:e4:4a:06:08:00 SRC=192.168.1.111 DST=192.168.1.200 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=37322 DF PROTO=TCP SPT=54283 DPT=5900 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 20 23:45:49 ubuntu-desktop kernel: [171642.809092] [UFW BLOCK] IN=eth1 OUT= MAC=08:00:27:e1:7b:85:00:24:2b:e4:4a:06:08:00 SRC=192.168.1.111 DST=192.168.1.200 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=46276 DF PROTO=TCP SPT=54284 DPT=5900 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 20 23:45:54 ubuntu-desktop kernel: [171648.012074] [UFW BLOCK] IN=eth1 OUT= MAC=08:00:27:e1:7b:85:00:24:2b:e4:4a:06:08:00 SRC=192.168.1.111 DST=192.168.1.200 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=11469 DF PROTO=TCP SPT=35651 DPT=5901 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 20 23:46:19 ubuntu-desktop kernel: [171672.334886] [UFW BLOCK] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:d9:0a:6b:46:08:00 SRC=192.168.1.108 DST=192.168.1.255 LEN=177 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2190 DPT=2190 LEN=157

Where am I going wrong??

---

### Post by movieman on 2010-07-20
Your configuration only allows connections from port 5901 to port 5901, doesn't it? The remote VNC client will be using some random port, so the odds of it being 5901 are small.

---

### Post by iamgeniusrnti on 2010-07-22
> **movieman said:**
> Your configuration only allows connections from port 5901 to port 5901, doesn't it? The remote VNC client will be using some random port, so the odds of it being 5901 are small.
 
OK... if I do a vncviewer <host ip>::5900, that should direct it at that port, should it not?
 
Besides, with all the advances *nix has made, I refuse to believe that the Ubuntu firewall won't allow VNC... I mean, if it's truly necessary, I could install an ssh server in the virtual (kind of risky considering it's already a honeypot, drop a key and run a  bash script that would shoot a "sudo ufw disable; sleep 5; exit; sleep 5; vncviewer"... but that seems a little clunky.
 
Suggestions?

---

### Post by spynappels on 2010-07-23
Is there a specific reason you want VNC access? I would guess that for a honeypot, the logs are the most important thing, and you can get them using SSH just as easily.

You could also tunnel over a SSH connection.

VNC is unsecure, and the number of people who have had problems through VNC vulnerabilities is unreal.

---

### Post by yeleek on 2010-07-23
> **iamgeniusrnti said:**
> OK... if I do a vncviewer <host ip>::5900, that should direct it at that port, should it not?
 
Besides, with all the advances *nix has made, I refuse to believe that the Ubuntu firewall won't allow VNC... I mean, if it's truly necessary, I could install an ssh server in the virtual (kind of risky considering it's already a honeypot, drop a key and run a  bash script that would shoot a "sudo ufw disable; sleep 5; exit; sleep 5; vncviewer"... but that seems a little clunky.
 
Suggestions?

Yeah don't use VNC.  Why create honeypots, and then leave VNC open on the virtual server?  Makes no sense...  as VNC would be one of the first things I'd personally look at on a pentest.

However if you insist on it.  Look at this - would seem you are missing ranges.
[http://www.cyberciti.biz/faq/linux-iptables-open-vncserver-port-6000-5800-5900/](http://www.cyberciti.biz/faq/linux-iptables-open-vncserver-port-6000-5800-5900/)

---

### Post by iamgeniusrnti on 2010-07-24
> **yeleek said:**
> Yeah don't use VNC.  Why create honeypots, and then leave VNC open on the virtual server?  Makes no sense...  as VNC would be one of the first things I'd personally look at on a pentest.

However if you insist on it.  Look at this - would seem you are missing ranges.
[http://www.cyberciti.biz/faq/linux-iptables-open-vncserver-port-6000-5800-5900/](http://www.cyberciti.biz/faq/linux-iptables-open-vncserver-port-6000-5800-5900/)

That is what I was looking for., thanks!

I have it sitting behind a smoothwall.  All ports blocked except a high port number with ssh running on different machine (plus the ports honeypot is listening on).  Once piped in, I can go to my other computers with another ssh session or vnc..  The only way in on ssh is with a passworded key as it will not do user name/pass.

Funny thing... I woke up this morning and decided I was getting bored with the honeypot.  It gets a lot of hits but no biters LOL!

---

### Post by OpSecShellshock on 2010-07-24
> **iamgeniusrnti said:**
> That is what I was looking for., thanks!

I have it sitting behind a smoothwall.  All ports blocked except a high port number with ssh running on different machine (plus the ports honeypot is listening on).  Once piped in, I can go to my other computers with another ssh session or vnc..  The only way in on ssh is with a passworded key as it will not do user name/pass.

Funny thing... I woke up this morning and decided I was getting bored with the honeypot.  It gets a lot of hits but no biters LOL!

That's a potential drawback of honeypots: unless they're effectively impersonating another kind of system, it becomes pretty obvious that's what they are. Mostly, they'll be attracting automated attacks, of course, in which case you want it to look like (or be) a web server. You could impersonate a regular home or office desktop system, but most of the attacks against those are initially kicked off by user activity (and are made for Windows). Either way, though, you'll want another firewall between it and the real network. It sort of defines the difference between honeypot and *wide open attack vector*.

---

### Post by iamgeniusrnti on 2010-07-24
> **OpSecShellshock said:**
> That's a potential drawback of honeypots: unless they're effectively impersonating another kind of system, it becomes pretty obvious that's what they are. Mostly, they'll be attracting automated attacks, of course, in which case you want it to look like (or be) a web server. You could impersonate a regular home or office desktop system, but most of the attacks against those are initially kicked off by user activity (and are made for Windows). Either way, though, you'll want another firewall between it and the real network. It sort of defines the difference between honeypot and *wide open attack vector*.

Yea... I know.  But on the rare occasion that it does attract someone, it fills me with glea.  Just this morning after I posted this, I went and checked the log.  Apparently last night, someone wound up in an arm wresting match with the pop emulator (110).  They were tied up for about 20 mins manually sending user names and passwords.  Then the dude typed, I think you are an a$$hole... HAHAHAHAHAHA!

---

### Post by OpSecShellshock on 2010-07-24
> **iamgeniusrnti said:**
> Yea... I know.  But on the rare occasion that it does attract someone, it fills me with glea.  Just this morning after I posted this, I went and checked the log.  Apparently last night, someone wound up in an arm wresting match with the pop emulator (110).  They were tied up for about 20 mins manually sending user names and passwords.  Then the dude typed, I think you are an a$$hole... HAHAHAHAHAHA!

Ah yes, the simple pleasures of open mic night at the hacker café.

---


---
title: "Error: Can't open display"
date: 2007-08-03
forum: Sun Sparc Users
---

### Post by Lord_Vader on 2007-08-03
I installed 6.06 LTS on an Ultra10 and installed the ubuntu-desktop. Eveything seems fine except I can't tunnel x windows to it. I get the Error: Can't open display. I had no problems with Solaris. I even made sure that I exported my DISPLAY correctly. 

Could it be a conflict between the open ssh and ssh.com (installed on the remote system).

TIA,
Vader

---

### Post by Lord_Vader on 2007-08-13
I seemed to have stumped everyone.... :confused:

---

### Post by psychicist on 2007-08-14
Usually it's only necessary to connect using "ssh -X" and the display is automatically redirected. I can't really try on my SPARC server because it's running Splack (Slackware for SPARC) and I'm recompiling Slackware 12.0 for it at the moment.

Maybe I will try to install Ubuntu SPARC on a spare drive after recovering from a failed Kubuntu update experience two days ago on a laptop, so I removed it and installed Slackware 12.0, which works flawlessly. I prefer Debian/Ubuntu to all other Linux distributions but nothing comes close to the stability and speed of Slackware.

---

### Post by netztier on 2007-08-14
> **Lord_Vader said:**
> I even made sure that I exported my DISPLAY correctly. 


Well, what does **echo $DISPLAY** actually return? 

If you connected to the box with ssh -X, that should already be taken care of, so you don't have to fiddle around with the environment variable, justlike psychicist said.

best regards

Marc

---

### Post by Synchro on 2007-09-08
> **netztier said:**
> Well, what does **echo $DISPLAY** actually return? 

If you connected to the box with ssh -X, that should already be taken care of, so you don't have to fiddle around with the environment variable, justlike psychicist

By default, DISPLAY is empty when I connect. I have X11 forwarding allowed in sshd_config, and I specify -X on connecting. Even if I set DISPLAY manually after connecting, it still fails to open (but at least it doesn't say that DISPLAY is not set). I have the same problem happening from several clients (Linux and OS X) to about 12 servers. I just tried it from a brand-new clean install of an Ubuntu client and a Debian server with the same results. Everything else works just fine over SSH, just not X.

I'm a bit mystified by the .Xauthority file - given that there is only one file for my local account, I guess it's common to all X sessions I might open? My .Xauthority contains:

G4.local0MIT-MAGIC-COOKIE-1d ~v t_x

Which doesn't look like it contains any hash-like value to me.

 Is there any problem displaying X apps from several servers at once?

I'm not seeing any errors on connecting at all.

Does it make any difference that all hosts are headless?

What else can I try?

---

### Post by psychicist on 2007-09-09
Do you have this line in you "/etc/ssh/sshd_config" and have you
removed the comment character (#) so it shows up this way:

X11Forwarding yes

Then you just have to restart your ssh daemon, probably with
"/etc/init.d/sshd restart".

I have just tried on my computers (x86, MIPS and SPARC) and it
works fine with Konqueror and Kcontrol. But I am running Slackware
12.0 on them and not (K)Ubuntu so YMMV.

---

### Post by Synchro on 2007-09-09
> **psychicist said:**
> Do you have this line in you "/etc/ssh/sshd_config" and have you
removed the comment character (#) so it shows up this way:

X11Forwarding yes

Then you just have to restart your ssh daemon, probably with
"/etc/init.d/sshd restart"..

Unfortunately I've checked all that already. I'm fairly sure it's enabled on Ubuntu by default anyway.

---

### Post by psychicist on 2007-09-09
Have you tried "ssh -X -A" instead of just "ssh -X"? That seemed to help when I still ran Red Hat/Fedora.

---

### Post by graboskyc on 2007-09-11
Simple things first... Is the machine you are exporting to allowing input from this machine? If you changed hostnames or something between when you had Solaris and Linux, this would make sense.

On the machine you are exporting display to try typing "xhost +" to allow any host to export display to it temporarily then "ssh -X " where X is caps.

---


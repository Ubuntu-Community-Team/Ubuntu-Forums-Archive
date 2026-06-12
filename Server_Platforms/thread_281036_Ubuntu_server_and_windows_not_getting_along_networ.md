---
title: "Ubuntu server and windows not getting along network-wise."
date: 2006-10-20
forum: Server Platforms
---

### Post by curgoth on 2006-10-20
(I posted this earlier in the week on the networking forum, but had no luck there)

I'm running Ubuntu server 6.06 LTS, and having weird issues with the windows machines having thier connections to the Ubuntu server periodically.

I have four machines in the back room.

Velvet, the old linux server (debian).
Phoenix, the new linux server (Ubuntu server 6.06 LTS).
Gir, my windows desktop.
Shiny, a windows laptop.

Gir and Shiny can talk to each other with no trouble. Velvet and Phoenix can talk to each other with no trouble. Phoenix can connect to Gir with no trouble. But when Gir or Shiny connect to Phoenix, they are fine for a little while, but if we do anything intensive like playing mp3s off of samba shares on Phoenix, or tranferring large files, Phoenix cuts them off after 5-10 minutes.

Completely.

Not just samba shares - all TCP/IP connections (ssh, etc.) are cut off, and Phoenix won't talk to those boxes for a minute or so after they get cut off. No idea why. I tried upgrading to a new gigabit switch (phoenix and gir have gigabit cards), and I don't think it's network cabling, since the window -> velvet connections and the velvet <-> phoenix connections are solid (stay connected for weeks, etc.)

I've checked the process monitor on Gir, and I'm not seeing a huge spike in CPU usage or network usage before the cut offs. I played around with Samba settings to make sure Phoenix, not one of the windows machines, is the master browser for the workgroup. I checked Phoenix for weird iptables entries, and there were no rules set up, which is what I had expected.

I'm running out of ideas, here. Anyone have any idea what could be causing this?

---

### Post by Woei on 2006-10-21
> **curgoth said:**
> (I posted this earlier in the week on the networking forum, but had no luck there)

I'm running Ubuntu server 6.06 LTS, and having weird issues with the windows machines having thier connections to the Ubuntu server periodically.

I have four machines in the back room.

Velvet, the old linux server (debian).
Phoenix, the new linux server (Ubuntu server 6.06 LTS).
Gir, my windows desktop.
Shiny, a windows laptop.

Gir and Shiny can talk to each other with no trouble. Velvet and Phoenix can talk to each other with no trouble. Phoenix can connect to Gir with no trouble. But when Gir or Shiny connect to Phoenix, they are fine for a little while, but if we do anything intensive like playing mp3s off of samba shares on Phoenix, or tranferring large files, Phoenix cuts them off after 5-10 minutes.

Completely.

Not just samba shares - all TCP/IP connections (ssh, etc.) are cut off, and Phoenix won't talk to those boxes for a minute or so after they get cut off. No idea why. I tried upgrading to a new gigabit switch (phoenix and gir have gigabit cards), and I don't think it's network cabling, since the window -> velvet connections and the velvet <-> phoenix connections are solid (stay connected for weeks, etc.)

I've checked the process monitor on Gir, and I'm not seeing a huge spike in CPU usage or network usage before the cut offs. I played around with Samba settings to make sure Phoenix, not one of the windows machines, is the master browser for the workgroup. I checked Phoenix for weird iptables entries, and there were no rules set up, which is what I had expected.

I'm running out of ideas, here. Anyone have any idea what could be causing this?

Lets approach this one step at a time. As it stands, we don't know whether it's a Samba problem, DNS, iptables, driver problem, network problem or something entirely different even.

Connect Shiny to Phoenix (preferably over a crossed-cable if you have one) and use sftp/scp to transfer a few gigs each way. If that works, we know the hardware and basic network configuration is fine so we have to look at Samba. It would be instrumental in solving this problem if you could list each machine's /sbin/ifconfig -a's, iptables -L -v -n's, /etc/hosts and /etc/resolv.conf's output. Any relevant error messages in Samba's logs (/var/log/samba) or from the kernel (dmesg) would be helpful too.

If you can isolate the problem, the relevant output of tcpdump and strace (on the smbd process) would simplify things greatly.

---


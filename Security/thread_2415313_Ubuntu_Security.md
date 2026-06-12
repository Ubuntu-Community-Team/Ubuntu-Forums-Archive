---
title: "Ubuntu Security"
date: 2019-03-24
forum: Security
---

### Post by weirdygeekpsych on 2019-03-24
I tried nmap on my ubuntu system, and it says XXX(<1000) number of closed ports and 2 open ports?

And I disabled root i.e. I use it when I need by typing SU.

Also I use ubuntu firewall

Is my ubuntu secure enough?

How can I be sure that closed ports are securing my system? 

is XXX(<1000) number of closed ports normal number? 

And activating SE Linux is harm? because once it conflicted with my display manager and started running in low graphics mode.

---

### Post by TheFu on 2019-03-24
Review the sticky threads about Ubuntu Security here: [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by dakkmaddy on 2019-03-24
> **jegan2 said:**
> I tried nmap on my ubuntu system, and it says XXX(<1000) number of closed ports and 2 open ports?

And I disabled root i.e. I use it when I need by typing SU.

Also I use ubuntu firewall

Is my ubuntu secure enough?

How can I be sure that closed ports are securing my system? 

is XXX(<1000) number of closed ports normal number? 

And activating SE Linux is harm? because once it conflicted with my display manager and started running in low graphics mode.

Your post lacks context. Are you running any servers or just using as a desktop. Enabling samba or SSH is hosting a server and that could be an opening for an attacker.

---

### Post by weirdygeekpsych on 2019-03-25
Desktop

---

### Post by dakkmaddy on 2019-03-25
The only exposed ports you (should have) are Samba (445) and maybe SSH. If you close them down, then you should be in great shape (just be careful what you download and execute). If you are hosting a web server, you should be on Ubuntu Server. You can scan all port with nmap using the -p- switch.

---

### Post by TheFu on 2019-03-25
But for most people fairly new to Ubuntu, just doing the "Basic Security" [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) things is enough provided high-risk activities are avoided.

Keep asking questions, but also keep reading to learn more.  There's always more to know, for everyone. I guess I know about 10% after all these years.

How much security anyone needs is up to them, what they do on the computer, their network, and what the likely attack vectors could be based on your job, your country, etc.  If you work as an NSA/GCHQ administrator, you are being attacked at your home too.  But if you are a grip for a movie company, then the chances someone is attacking you as a target is almost non-existent.

Ubuntu comes with the root account inaccessible, so turning it off shouldn't be necessary. If it was on, then someone modified the installer. I would be suspicious.

All Linux systems have the firewall built into the kernel.  Enabling it doesn't do anything by default. It must be configured, set to startup at reboot AND enabled.  "Ubuntu Firewall" is vague. Care to name the program?  ufw, gufw, iptables, firehol, or one of the other interfaces into the kernel firewall?

Closed ports are just 1 method for security, especially for a desktop. Most desktop attacks happen from user choices in the browser or email program. This assumes there is a separate hardware router doing some firewall and port blocking too. If that isn't the situation, risks increase for the desktop.  nmap is an amazing tool. To get the most out of such a complex tool, take a look at the manpage which shows all the different options.

There is no "normal number" of closed/open ports.  Zero is better than 1. 1 is better than 2. If you run 2 services and those use network ports, then it is likely that at least 2 ports will be open, maybe more.  But you can limit the remote clients which have access to those ports through service configuration settings and/or firewall(s).  For example, the samba server allows controlling which IPs can access it and will deny all others, but we have to add that to the configuration.  

The same applies to ssh. The sshd_config file supports limiting where ssh client connections originate.  If you want to allow internet ssh connections, it is best not to allow everyone, every where, access.  Best to block everyone by default, except those places you will be AND want an ssh client to connect from. That isn't always possible.  There are tools to block failed ssh client connections too - denyhosts, fail2ban, and whatever firewall interface you are using, but each need to be configured.

SELinux was designed for use on RHEL-based distros, so while it can be enabled on Ubuntu, it isn't a normal situation to have it running.  Ubuntu has some other tools, IMHO, they aren't as comprehensive, but when used well, they do a job. Apparmor is one. [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor) There are also other techniques to secure specific processes by using Linux Containers [https://help.ubuntu.com/lts/serverguide/lxd.html.en](https://help.ubuntu.com/lts/serverguide/lxd.html.en) or cgroups [https://manpages.ubuntu.com/manpages/cosmic/man7/cgroups.7.html](https://manpages.ubuntu.com/manpages/cosmic/man7/cgroups.7.html) and namespaces to limit isolate processes to specific parts of the OS, hardware, networking, etc.  [https://www.linuxjournal.com/content/everything-you-need-know-about-linux-containers-part-i-linux-control-groups-and-process](https://www.linuxjournal.com/content/everything-you-need-know-about-linux-containers-part-i-linux-control-groups-and-process)

There are friendlier tools for a quick need - firejail, mbox, nsjail, ... and probably a few others.

But most desktops don't need these levels today for average, normal, people.

---

### Post by weirdygeekpsych on 2019-04-02
Thanks for your detailed explanation, gained some insights to proceed further

---


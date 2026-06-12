---
title: "I need an anti-virus program that cleans viruses"
date: 2009-06-21
forum: Security
---

### Post by medic2000 on 2009-06-21
I need to clean my the viruses on my windows partition from Linux. I have installed the clamav and AVG Linux version but they only scan and found viruses.But there is no cleaning option. 

So i need that option.Which antivirus could provide it?

---

### Post by Chemical Imbalance on 2009-06-21
[http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html)

Avast is my favorite free one.  Works great scanning from within linux.

Make sure you get the free registration key (follow instructions on their site). [http://avast.com/eng/home-registration.php](http://avast.com/eng/home-registration.php)

It detects and removes.

---

### Post by medic2000 on 2009-06-21
Thank you very much. At the moment i am dowloading it

---

### Post by medic2000 on 2009-06-21
I downloaded but after copying the key it gives an error:

Cannot allocate memory!

I have 2 gb ram how can this be?

---

### Post by balloooza on 2009-06-21
can you start it from the terminal (or did you) and post the output

---

### Post by medic2000 on 2009-06-21
Same error from the console and nothing more

---

### Post by cariboo on 2009-06-21
Check the man page for clamav, as it does give you the option to move the infected files to another directory. There is also a log file in /var/log that will give you the location of the infected files. I don't have it installed, or I would give you an example.

---

### Post by Sir Jasper on 2009-06-21
Hi,

I assume you downloaded the Debian version of Avast to your desktop and then double clicked? 

Avast scans significantly faster than ClamWin and has a better reputation than ClamWin, so it may be worth persevering to keep a choice of on demand scans

Avast free home edition for Windows provides very good active protection once you have cleaned your viruses. If you cannot clear your viruses try the a-squared forum for exceptional help in fixing problems via windows.

My regards

---

### Post by lovinglinux on 2009-06-21
[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by credobyte on 2009-06-22
> **lovinglinux said:**
> [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

Includes firewall ?

---

### Post by lovinglinux on 2009-06-22
> **credobyte said:**
> Includes firewall ?

No and it doesn't do real-time protection either. Most Linux anti-virus doesn't do that without additional installation and configuration. 

Ubuntu comes with a firewall installed and running by default, but it allows all traffic.

To create firewall rules you need to know the iptables (firewall) commands or install a firewall manager. Ubuntu also comes with a firewall manager (UFW) installed by default. If you want a graphical interface to control it, install [gufw](apt:gufw) [apt-get]. Then access it from "System >> Administration >> Firewall Configuration". You don't have to run it all the time, because the real firewall (iptables) runs in the background, so after creating the rules you can close the Firewall Configuration tool.

Keep in mind that Linux is not Windows. It is much more secure by default. 

I recommend reading [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial

---

### Post by credobyte on 2009-06-22
> **lovinglinux said:**
> No and it doesn't do real-time protection either. Most Linux anti-virus doesn't do that without additional installation and configuration. 

Ubuntu comes with a firewall installed and running by default, but it allows all traffic.

To create firewall rules you need to know the iptables (firewall) commands or install a firewall manager. Ubuntu also comes with a firewall manager (UFW) installed by default. If you want a graphical interface to control it, install [gufw]("apt:gufw") [apt-get]. Then access it from "System >> Administration >> Firewall Configuration". You don't have to run it all the time, because the real firewall (iptables) runs in the background, so after creating the rules you can close the Firewall Configuration tool.

Keep in mind that Linux is not Windows. It is much more secure by default. 

I recommend reading [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421") tutorial

I know that I don't really need an antivirus or any additional software to protect myself ( _in most cases_ ). I was just curious as I've never heard about BitDefender on Linux ( only AVG, Avast and Clam ) ;) The one and only thing I'm really interested in is real-time firewall ( auto-rule assignment for ports/IP's not in the list of *allowed* addresses ).

---

### Post by lovinglinux on 2009-06-22
> **credobyte said:**
> I was just curious as I've never heard about BitDefender on Linux ( only AVG, Avast and Clam ) ;) 

In my opinion, BitDefender for Linux is better than all those you mentioned, at least in terms of functions, easy updates, graphical interface and speed. I don't know about detection efficiency, because I'm virus free for years :) I use to run AVG and Comodo Firewall on Windows.

> **credobyte said:**
> The one and only thing I'm really interested in is real-time firewall ( auto-rule assignment for ports/IP's not in the list of *allowed* addresses ).

I think you should create a new thread for this, but I doubt you will find a firewall with alerts like ZoneAlarm or Comodo Firewall.

---

### Post by Wiebelhaus on 2009-06-22
[The best of the best # ]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html")

---

### Post by credobyte on 2009-06-22
> **lovinglinux said:**
> In my opinion, BitDefender for Linux is better than all those you mentioned, at least in terms of functions, easy updates, graphical interface and speed. I don't know about detection efficiency, because I'm virus free for years :) I use to run AVG and Comodo Firewall on Windows.

I think you should create a new thread for this, but I doubt you will find a firewall with alerts like ZoneAlarm or Comodo Firewall.

Thanks, will check them out a bit later on today. Haven't used ZoneAlarm for years ( never on Linux ) :)

---

### Post by lovinglinux on 2009-06-22
> **credobyte said:**
> Thanks, will check them out a bit later on today. Haven't used ZoneAlarm for years ( never on Linux ) :)

You can't run ZoneAlarm on Linux, I was just making a comparison, because it is a popular Windows firewall with those type of real-time alerts. ZoneAlarm sucks anyway. Comodo firewall is way much better and Windows 7 comes with a pretty decent firewall.

---

### Post by credobyte on 2009-06-22
> **lovinglinux said:**
> You can't run ZoneAlarm on Linux, I was just making a comparison, because it is a popular Windows firewall with those type of real-time alerts. ZoneAlarm sucks anyway. Comodo firewall is way much better and Windows 7 comes with a pretty decent firewall.

Damn ! Ok, anyway, thanks for your help - looks like I need to spend a few hours on reading ( available AV's, firewalls interfaces, etc. ) :)

---

### Post by bodhi.zazen on 2009-06-22
What is it you want to run a firewall for exactly ?

---

### Post by Wiebelhaus on 2009-06-22
> **credobyte said:**
> Damn ! Ok, anyway, thanks for your help - looks like I need to spend a few hours on reading ( available AV's, firewalls interfaces, etc. ) :)

Just use bit-defender for anti_malware , it's all you'll need.

---

### Post by blackxored on 2009-06-22
ClamAV, Avast, Panda. Pay for Kaspersky.

---

### Post by Chemical Imbalance on 2009-06-22
I didn't know Bitdefender had a free GUI linux client.

Nice.

Scanning my windows partition with it now.  :)

Bitdefender is a great scanner, better than Avast in my opinion.

Will definitely start recommending it for people scanning their NTFS drives within Linux.

Here's a direct link so that you don't have to register your email address to download:  [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)

---

### Post by Wiebelhaus on 2009-06-22
> **Chemical Imbalance said:**
> I didn't know Bitdefender had a free GUI linux client.

Nice.

Scanning my windows partition with it now.  :)

Bitdefender is a great scanner, better than Avast in my opinion.

Will definitely start recommending it for people scanning their NTFS drives within Linux.

Here's a direct link so that you don't have to register your email address to download:  [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)

I've been using it enterprise , work station and server level and it's absolutely fantastic , the best IMHO.

---

### Post by medic2000 on 2009-06-24
Yes now i have used the BitDefender 64 bit GUI anti-virus scanner. It suggest it too.

Note: i want to mark this thread with solved but there is not an option in Thread Tools.

---


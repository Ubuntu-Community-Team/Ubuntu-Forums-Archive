---
title: "Dansguardian troubles"
date: 2007-06-19
forum: Ubuntu Christian Edition
---

### Post by honda on 2007-06-19
I'm completely unable to get dansguardian to work with feisty. I had it running using the ubuntu ce filtering script on dapper and edgy, but this time no... I've read all threads in this forum and everything else, and I'm starting to get frustrated. Actually I don't think I even have a question. Or maybe if someone could confirm that they have dansguardian running on a plain feisty install by using the ubuntu ce script, then I would at least know it is possible. Seems as firehol is not working in feisty, but then I should have dansguardian working by stopping firehol and connecting to port 8080, right? The only way to connect to internet now is by connecting to port 3128, with that first  iptables rule disabled in firehol.conf (which is there to prevent just that)

---

### Post by tak1150 on 2007-06-20
DG was running fine on plain U-CE 3.2 (7.04)... until today!

Ok, I installed VMWare server in the last couple of days. So the virtual network may be interfering somehow...?

I do agree that DG did better back in Edgy.

Maybe filtering everything (as opposed to just web browsing traffic) is a bad idea? B/c I think back in edgy (or CE v.2.x), the filtering had to be set to port 8080 only for DG to work.

Somebody help us!

---

### Post by tak1150 on 2007-06-20
Actually now I that I look back, I had a fresh Ubuntu CE 3.2 install not too long ago, then I didn't touch DG GUI until today...

So my problem is probably the same as these posts;

[http://ubuntuforums.org/showthread.php?t=408272&page=2]("http://ubuntuforums.org/showthread.php?t=408272&page=2")
especially post #55-57

But re-installing the DG is not acceptable b/c then I would not have the settings I need.

I need/want;
[LIST=1]
[*]certain file extensions allowed
[*]certain MIMEs allowed
[*]strict image/web filtering
[/LIST]

To accomplish this, I have to go to the DG-GUI...

...help!

---

### Post by mhancoc7 on 2007-06-20
> **honda said:**
> I'm completely unable to get dansguardian to work with feisty. I had it running using the ubuntu ce filtering script on dapper and edgy, but this time no... I've read all threads in this forum and everything else, and I'm starting to get frustrated. Actually I don't think I even have a question. Or maybe if someone could confirm that they have dansguardian running on a plain feisty install by using the ubuntu ce script, then I would at least know it is possible. Seems as firehol is not working in feisty, but then I should have dansguardian working by stopping firehol and connecting to port 8080, right? The only way to connect to internet now is by connecting to port 3128, with that first  iptables rule disabled in firehol.conf (which is there to prevent just that)

OK, I have been watching these Dansguardian threads closely.

I have been unable to figure out why some users have had so much difficulty with Dansguardian in Feisty. I have just completed testing the Dansguardian Install script on a fresh installation of Feisty. It worked flawlessly. I then tested the Dansguardian GUI. I ran through several possible ways to configure and re-configure the settings. I tested locking and unlocking Firefox proxy settings. I also tested enabling and disabling the filtering. It worked great. The only issue that I did find is that occasionally I had to refresh Firefox several times after making a change for the site to load. Once it loaded though the internet worked great with filtering or without depending on the settings. 

So, I am still not sure why users are having trouble. It may have something to do with another program that may be installed on their system. Maybe if we could isolate what the users who are having trouble have in common then maybe we can find what is causing the issue. 

Thanks, Jereme

---

### Post by honda on 2007-06-20
Thanks for the answer. I don't have a completely plain 'out of the box' setup, I have a wireless connection using WEP encryption with a self-compiled driver (rtl-wifi), network-manager set to manual configuration, and static ip-address. Other than that I have not messed with the network settings... :-)

My current setup is an update-manager-upgraded Edgy. The first upgrade attempt failed, it complained about dansguardian... So I removed dansguardian and tried upgrade again. This time it worked and everything seemed normal. Then I run the ubuntu  CE dansguardian script, which sort of worked (I remember there was some trouble, but not exactly what).

 Then I disabled firefox locking with the gui and set the firefoxes of the grown up's in the family to point to port 3128, and disabled the iptables rule that prevents that. Then I HAD a sort-of-working setup. Sometimes internet through dansguardian didn't work but most often it did. Then a couple of weeks later when installing something else, apt-get complained about dansguardian package being broken. Trying to fix that I ended up trying to reinstall the whole dansG+tinyproxy+clamav+firehol and since then I haven't managed to return to the previous almost working state. 

I guess my next step will be to try a completely manual installation of DG+tinyproxy.

---

### Post by tak1150 on 2007-06-20
In the hope that these clues lead to a solution;

Here's the list of softwares that I have that I think may be related to the issue:
-not in any particular order
[LIST=1]
[*]Cisco VPN
[*]VMware server (sets up vmnet1 & 8)
[*]Swiftfox
[*]SciFinder Scholar (connects to the SciFinder research article database)
[*]Atheros wireless driver
[*]Wengophone
[*]Skype
[*]SSH
[*]Samba
[*]BackupPC (rsync + ssh)
[/LIST]

Also I use this laptop both at work (eth0, ethernet to LAN) and at home (ath0).
Thanks for looking into this!

Tak

---

### Post by tak1150 on 2007-06-20
Just to make sure, I reinstalled the DG + DG-GUI using the DG install script (not convert_me script) for U-CE 3.2

... and it works! Even after I change things in DG-GUI (as long as I restart the computer).

So I guess some of those programs I installed did something with either the proxy or firewall and I just had to reinstall DG after those programs are in place. Halleluja!

Tak

---

### Post by mhancoc7 on 2007-06-20
> **tak1150 said:**
> Just to make sure, I reinstalled the DG + DG-GUI using the DG install script (not convert_me script) for U-CE 3.2

... and it works! Even after I change things in DG-GUI (as long as I restart the computer).

So I guess some of those programs I installed did something with either the proxy or firewall and I just had to reinstall DG after those programs are in place. Halleluja!

Tak

Great to hear!

It is hard since I set it all up to work on a fresh installation of Ubuntu. There are so many things that can conflict once a user adds or removes programs. Specifically programs that affect the network settings.

I am glad to hear that you got it going. I am not sure why you have to restart after making changes. I know that I have to refresh my browser several times after making changes. It is usually faster to just restart the system though. :)

Let me know how things go.

Thanks, Jereme

---

### Post by honda on 2007-06-21
Now I have a working dansguardian also, I started by removing dansguardian, dansguardian-gui, all clamav packages, tinyproxy, firehol. Then I installed dansguardian and tinyproxy, but left out firehol. Edited dansguardian.conf, restarted and it worked! The browsers'  proxy setting had to be manually set to localhost, 8080, of course. I suspect firehol is the one messing my system up. The gui was nice, though... but I'm so deep into this by now so I guess I can manage without.

---


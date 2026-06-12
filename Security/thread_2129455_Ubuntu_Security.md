---
title: "Ubuntu Security"
date: 2013-03-26
forum: Security
---

### Post by lumaja on 2013-03-26
Ubuntu 12.04 LTS
 

 I need help about security, asking different appications but need this answers please bear with me.
 

 I have ClamTK, Firefox with Adblock Plus 2.2.3 and NoScript 2.6.5.8.
 I seen on the web not so good reports about this applications.  
   
 I read that ClamTK is only need if working with windows in Ubuntu – Is this correct? (I don’t)
 Is the above with Ubuntu only, protects on a web or not?
 I found articles about AppArmor is this better than ClamTk, should I rather replace to  
 AppArmor? (Using Ubuntu for banking).
 Found another application Host-based intrusion Detection Systems (HIDS) again ask if this is
 any good and should I use with my OS.  
 Please advise me which is the best for peace of mind.
 Thank you

---

### Post by haqking on 2013-03-26
> **lumaja said:**
> Ubuntu 12.04 LTS
 

 I need help about security, asking different appications but need this answers please bear with me.
 

 I have ClamTK, Firefox with Adblock Plus 2.2.3 and NoScript 2.6.5.8.
 I seen on the web not so good reports about this applications.  
   
 I read that ClamTK is only need if working with windows in Ubuntu &#8211; Is this correct? (I don&#8217;t)
 Is the above with Ubuntu only, protects on a web or not?
 I found articles about AppArmor is this better than ClamTk, should I rather replace to  
 AppArmor? (Using Ubuntu for banking).
 Found another application Host-based intrusion Detection Systems (HIDS) again ask if this is
 any good and should I use with my OS.  
 Please advise me which is the best for peace of mind.
 Thank you

Security is a process not a product.

Start reading here [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Apparmor and ClamTK are different products that do different things, it is covered in the link above.

Learn early on that "Linux is not more secure" than other OS, as most people will tell you that it is(the followers that is). Also the "linux is more secure" statement is nonsensical and non comparable.

There are steps you need to take with all OS to increase security, but nothing in a connected world is 100% secure.

Have a good read.

Peace

---

### Post by tubbygweilo on 2013-03-26
lumaja, can you give me some idea as to what types of threats concern you as 12.04LTS & Firefox with Adblock Plus 2.2.3 and NoScript 2.6.5.8 work together and are considered good bits of kit that work right out of the box? 

Your security should be in many layers starting with physical security and good strong passwords and pass phrases.

Your should consider applying all security updates as they become available.

When browsing or answering emails or banking via the net be aware of Social Engineering ploys that try to harvest your financial or personal data, these can be mitigated by Firefox with Adblock Plus and NoScript.

It is only now that I would move on to other means of hardening your kit with some of the tools you have mentioned but as I lack knowledge in those departments I'll leave that advice to others.

All the best with your research.

---

### Post by The Cog on 2013-03-26
Moved to Security Discussions

---

### Post by WhaleVPS on 2013-03-26
Its really not that Linux is more secure then Windows or MAC, its the fact that we aren't as targetted as much as the other user bases.

---

### Post by maglinu on 2013-03-26
As a relative newcomer to ubuntu, the extra things that I do from a security standpoint are:

Firefox and Chromium browser Apparmor profiles are set to to enforce.
I use the bitdefender trafficlight browser plug-in to give bit of additional phishing/fraud protection to what is built into Firefox/Chromium.
I use OpenDNS for much the same reason.
UFW is set to default deny inbound and outbound, with essential outbound ports allowed only as advised in the security wiki (I don't know if this outbound restriction really adds much value though).
I don't have java or flash installed (having read they are the main sources of cross-platform malware)
I use a different user account for sensitive web transactions, and_ only_ for those transactions. In this account I only use FF. In my main user account for general stuff I use only Chromium.
Given my long Windows background, I can't really feel fully relaxed without doing a bit of scanning (though those more knowledgeable will probably say it's pointless), so I do run an AV (and Chkrootkit).

I don't claim that this is a particularly good or well-researched model, but it may give you some ideas to look into.

---

### Post by UltimateCat on 2013-05-05
I have been trying to get BitDefender working for 2-3 days now and no matter what I try it will not scan.
Yet the application launches and is up --

You may not want to choose Bit Defender-
**If I get it working I'll be back:-**

ClamAV, F-Secyre and F-prot are other antivirus applications you could consider as well.
Synaptic should have ClamAV unless of course you prefer the version you are already working with-

Best regards

---

### Post by UltimateCat on 2013-05-06
Found the :
> BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

File online and ran it with chmod =x...(etc.)

Turned on my system today and BitDefender is up and running and scanning.
Took me 3 days of installing it and un-installing it and finally it is working!;)

[http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/](http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/)

And followed these instructions:
```

[h=3][BitDefender Antivirus Installation & Configuration on OpenSuSe Linux]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html")[/h]     Posted by Nikesh Jauhari    
  
   BitDefender Antivirus Scanner for Unices is a versatile on-demand scanner built for Linux and FreeBSD systems. It provides [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]antivirus [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]and [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]antispyware[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") scanning for both [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]UNIX[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#")-based and Windows-based partitions.
 
BitDefender Antivirus Scanner for Unices is highly customizable and  capable of script and extension-based integration with various  applications such as file managers and mail clients.

BitDefender Antivirus Scanner for Unices may be used free of charge at  home or on your personal computer. In case you want to use BitDefender  Antivirus for Unices for business purposes, a registration key must be  purchased through the BitDefender Online Store or from BitDefender  certified partners.
**Features and Benefits**
    * On-demand antivirus and antispyware protection
    * [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]Script[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") and extension-based integration with various applications and services:
           o Mail clients (e.g. *Pine, Evolution*) and Mail Server services
          o Scheduling services (e.g. *Cron*) ensuring scan and update automation
    * Classic [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]command[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") line scanner complete with a graphical [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]user [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]interface[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") for better integration with desktop environments.
     * Automatic addition of the scanner's GUI to the system menu.
    * Three popular file manager plugins (*the GPL-ed sources*) included in the GUI package: Konqueror (*KDE*), Nautilus (*GNOME*) and Thunar (*Xfce*).
    * Action setting based on scan result type.

**Installation:** 
Download BitDefender Antivirus from [here]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") (*provide  valid e-mail address and you will get the download link through mail*)
 PS : You can get your personal license from [here]("http://www.bitdefender.com/site/Products/ScannerLicense/").

Make the file executable:
[COLOR=blue]# chmod +x BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run[/COLOR]

Run the BitDefender Antivirus installer:
[COLOR=blue]# ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run[/COLOR]

[CENTER][[IMG]http://3.bp.blogspot.com/_VN8zHqq8Ns8/StCOX3r9hJI/AAAAAAAADDc/XhlT60JYzyA/s320/BitDefender_License.png[/IMG]]("http://3.bp.blogspot.com/_VN8zHqq8Ns8/StCOX3r9hJI/AAAAAAAADDc/XhlT60JYzyA/s1600-h/BitDefender_License.png")
 [/CENTER]

 You’ll be prompted with the end user licence agreement. At the end of the license type “*accept*” (*without quotes*). This will begin the installation of BitDefender antivirus on your machine.

**Running Bitdefender:**
After you have successfully installed the anti-virus go to *Applications->System->More Programs->BitDefender Scanner* and start the application.

[CENTER][[IMG]http://1.bp.blogspot.com/_VN8zHqq8Ns8/StCP5YEJJ0I/AAAAAAAADDk/qxopvm800ZA/s320/BitDefender.png[/IMG]]("http://1.bp.blogspot.com/_VN8zHqq8Ns8/StCP5YEJJ0I/AAAAAAAADDk/qxopvm800ZA/s1600-h/BitDefender.png")
 [/CENTER]

Enter the free key that you requested and received in your email to get the free 1 year license.     [1]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") 


```

Hope this is a help to someone.

---

### Post by QDR06VV9 on 2013-05-06
> **UltimateCat said:**
> Found the :

File online and ran it with chmod =x...(etc.)

Turned on my system today and BitDefender is up and running and scanning.
Took me 3 days of installing it and un-installing it and finally it is working!;)

[http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/](http://unices.bitdefender.com/2011/11/01/bitdefender-antivirus-scanner-for-unices/)

And followed these instructions:
```

[h=3][BitDefender Antivirus Installation & Configuration on OpenSuSe Linux]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html")[/h]     Posted by Nikesh Jauhari    
  
   BitDefender Antivirus Scanner for Unices is a versatile on-demand scanner built for Linux and FreeBSD systems. It provides [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]antivirus [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]and [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]antispyware[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") scanning for both [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]UNIX[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#")-based and Windows-based partitions.
 
BitDefender Antivirus Scanner for Unices is highly customizable and  capable of script and extension-based integration with various  applications such as file managers and mail clients.

BitDefender Antivirus Scanner for Unices may be used free of charge at  home or on your personal computer. In case you want to use BitDefender  Antivirus for Unices for business purposes, a registration key must be  purchased through the BitDefender Online Store or from BitDefender  certified partners.
**Features and Benefits**
    * On-demand antivirus and antispyware protection
    * [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]Script[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") and extension-based integration with various applications and services:
           o Mail clients (e.g. *Pine, Evolution*) and Mail Server services
          o Scheduling services (e.g. *Cron*) ensuring scan and update automation
    * Classic [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]command[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") line scanner complete with a graphical [[COLOR=blue][COLOR=blue!important][FONT=inherit!important][COLOR=blue!important][FONT=inherit!important]user [/FONT][/COLOR][COLOR=blue!important][FONT=inherit!important]interface[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") for better integration with desktop environments.
     * Automatic addition of the scanner's GUI to the system menu.
    * Three popular file manager plugins (*the GPL-ed sources*) included in the GUI package: Konqueror (*KDE*), Nautilus (*GNOME*) and Thunar (*Xfce*).
    * Action setting based on scan result type.

**Installation:** 
Download BitDefender Antivirus from [here]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") (*provide  valid e-mail address and you will get the download link through mail*)
 PS : You can get your personal license from [here]("http://www.bitdefender.com/site/Products/ScannerLicense/").

Make the file executable:
[COLOR=blue]# chmod +x BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run[/COLOR]

Run the BitDefender Antivirus installer:
[COLOR=blue]# ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.rpm.run[/COLOR]

[CENTER][[IMG]http://3.bp.blogspot.com/_VN8zHqq8Ns8/StCOX3r9hJI/AAAAAAAADDc/XhlT60JYzyA/s320/BitDefender_License.png[/IMG]]("http://3.bp.blogspot.com/_VN8zHqq8Ns8/StCOX3r9hJI/AAAAAAAADDc/XhlT60JYzyA/s1600-h/BitDefender_License.png")
 [/CENTER]

 You’ll be prompted with the end user licence agreement. At the end of the license type “*accept*” (*without quotes*). This will begin the installation of BitDefender antivirus on your machine.

**Running Bitdefender:**
After you have successfully installed the anti-virus go to *Applications->System->More Programs->BitDefender Scanner* and start the application.

[CENTER][[IMG]http://1.bp.blogspot.com/_VN8zHqq8Ns8/StCP5YEJJ0I/AAAAAAAADDk/qxopvm800ZA/s320/BitDefender.png[/IMG]]("http://1.bp.blogspot.com/_VN8zHqq8Ns8/StCP5YEJJ0I/AAAAAAAADDk/qxopvm800ZA/s1600-h/BitDefender.png")
 [/CENTER]

Enter the free key that you requested and received in your email to get the free 1 year license.     [1]("http://linuxpoison.blogspot.com/2009/10/bitdefender-antivirus-installation.html#") 


```

Hope this is a help to someone.

I Also had problems but went about install method diferently.
Dont know outcome will be the same for everybody but heres how I did it.

Code: wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc)
sudo apt-key add bd.key.asc


[Add in Software Sources]
deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

sudo apt-get update
sudo apt-get install bitdefender-scanner-gui

From Here:<https://sites.google.com/site/nikhildotnet/tutorials/linux/ubuntu-repository-ppa>

It is a bit buggy on first startup though..
Hope this helps..:)

---

### Post by lovebluesky2009 on 2013-05-06
eset is also very good, but it's not free. antivir and avast are also used by some people

---

### Post by HermanAB on 2013-05-08
The default Ubuntu security setup is good enough for home users.  The only thing you need to ensure is that you use passwords that are relatively long >=12 characters.

Other than that, relax and enjoy your Ubuntu system.

---

### Post by roten on 2013-05-09
Have a look at this page[URL="https://wiki.ubuntu.com/BasicSecurity"]
 
https://wiki.ubuntu.com/BasicSecurity[/URL]

it contains the basics you need.

---


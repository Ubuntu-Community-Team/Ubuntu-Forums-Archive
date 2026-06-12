---
title: "ubuntu as print server"
date: 2012-05-15
forum: Server Platforms
---

### Post by mosaic2s on 2012-05-15
I have installed 12.04 LTS 32bit on a system. This system has 2 printers. epson 1390 and hp designjet 111. Both are recognised by ubuntu and test page printed fine.
Now I have enabled these 2 printers and shared them as well. However unable to install them for printing through xp.

How to configure ports on xp for printing through linux server?

---

### Post by LHammonds on 2012-05-15
I believe you need to have CUPS installed in order to get Windows machines to print to printers attached to a Linux server.

I tried setting up a print server by manually installing all of the components but failed miserably due to my noob-level Linux skills.

However, I was able to setup a [Zentyal print server]("http://www.zentyal.org/") quite easily and it worked great.

LHammonds

---

### Post by mosaic2s on 2012-05-15
Saw Zentyal website.

The idea is to learn new skills as we go along, hence trying my head on my own just now.

---

### Post by Morbius1 on 2012-05-15
There's a problem with the samba - cups connection in 12.04 so it depends on how you are trying to connect to the printer from WinXP.

There's a bug report detailing this issue: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

Ubuntu went to a new version of samba which may or not be the cause of this problem but the best thing to do is circumvent samba entirely and connect to cups directly.

** Using the "Add printer" mechanism in XP choose "Connect  to a printer on the Internet ..." , then add in the "URL" box the actual address like this for example:
```
[http://192.168.0.100:631/printers/HPPrinter](http://192.168.0.100:631/printers/HPPrinter)

```If you're lucky you could also use the host name instead of the ip address.

---

### Post by mosaic2s on 2012-05-15
Yes, i am finding too many errors in 12.04. CITADEL does not work. Vbox is too slow and 64 bit does not change mouse button!

Going back to 10.04 LTS. Will try your lead and revert.

Thanks.

---

### Post by mosaic2s on 2012-05-16
Installed 64 bit 10.04 LTS and updated it last night.
Have managed to remotely administer the CUPS. thanks for the tip as above.

Have taken test print from xp while using ubuntu as a print server.
Then tried the same on win7. The installation is done but print is not happening.

Will chk epson tonight.

---

### Post by mosaic2s on 2012-05-26
for now using vbox to act as print server. will set up linux as print server after some time.

---

### Post by romgapuz on 2012-06-14
> **Morbius1 said:**
> There's a problem with the samba - cups connection in 12.04 so it depends on how you are trying to connect to the printer from WinXP.

There's a bug report detailing this issue: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

Ubuntu went to a new version of samba which may or not be the cause of this problem but the best thing to do is circumvent samba entirely and connect to cups directly.

** Using the "Add printer" mechanism in XP choose "Connect  to a printer on the Internet ..." , then add in the "URL" box the actual address like this for example:
```
[http://192.168.0.100:631/printers/HPPrinter](http://192.168.0.100:631/printers/HPPrinter)

```If you're lucky you could also use the host name instead of the ip address.

Been configuring CUPS for days, read so many articles on how to do it but none worked. Only to find out it's a bug.

This works for me, thanks a lot!

---


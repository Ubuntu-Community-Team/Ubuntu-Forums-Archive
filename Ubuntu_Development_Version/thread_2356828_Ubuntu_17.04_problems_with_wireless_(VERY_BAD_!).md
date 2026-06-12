---
title: "Ubuntu 17.04: problems with wireless (VERY BAD !)"
date: 2017-03-27
forum: Ubuntu Development Version
---

### Post by moma on 2017-03-27
Hello,
I have periodically serious problems with WIFI in Ubuntu 17.04.
The network icon shows "connected" to the router and internet, but browsers and other attempts to get data report DNS error / or not connected.
This happens in Ubuntu 17.04 ONLY and this bug affects all flavours of Ubuntu, Ubuntu GNOME etc.
Same laptop with Ubuntu 16.10 works flawlessly.

The connection works fine after I reboot (power off/on) the router box. 
Then the bug may return (or may not return) after I turn on my laptop next time.

This laptop is Toshiba Stellite P50 C.
The laptop has Intel Corporation Wireless 3165 (rev 81).

$ lspci -nnk | grep -iA2 net; uname -r; ls /lib/firmware/ | grep 'iwlwifi-7265d'

0d:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
	Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]
	Kernel driver in use: iwlwifi
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Toshiba America Info Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1179:f840]
	Kernel driver in use: r8169
	Kernel modules: r8169
4.11.0-041100rc4-generic

Ref: [https://wiki.debian.org/iwlwifi](https://wiki.debian.org/iwlwifi)

Restarting the network.manager does not help.
$ sudo service network-manager restart
Network manager connects (and sees) to the router, but cannot access internet.
 
**One possible solution (EDIT: It does not work!!) :**
I have upgraded to Linux-kernel version 4.11-rc4 (the very latest and hottest)

I have installed UKUU kernel-updater and run:
$ ukuu --list
$ sudo ukuu --install v4.11-rc4

Then reboot with the new 4.11 kernel.

Now the WIFI seems to work after each and every boot.  
However, I need to make more tests to see if this holds water.

$ uname -a
Linux Ubuntu1704  kernel 4.11.0-041100rc4-generic #201703261831 SMP Sun Mar 26 22:33:11 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04  Ubuntu GNOME
Codename:	zesty  

EDIT: A related bug-report.
[https://ubuntuforums.org/showthread.php?t=2354066](https://ubuntuforums.org/showthread.php?t=2354066)


The actual error message in the Chromium browser:
```
Server DNS address could not be found.
Try:
Checking the proxy, firewall, and DNS configuration
DNS_PROBE_FINISHED_BAD_CONFIG
ReloadHIDE DETAILS
Check your DNS settings
Contact your network administrator if you're not sure what this means.
```


Thanks.

---

### Post by mc4man on 2017-03-27
See basically same here, after install there is internet access for one session, then gone.
Was going to Automatic (DCHP) addresses only & using google nameservers to 'solve' here but just tested latest kernel & that also resolves.
Clearly Ubuntu needs to do something before release...

longstanding bug - 
[https://bugs.launchpad.net/linux/+bug/1654918](https://bugs.launchpad.net/linux/+bug/1654918)

---

### Post by moma on 2017-03-28
Re-hi,
I do not think the new kernel (v4.11) repairs this bug.
I am still having the same wifi-problem occasionally.  Kernel 4.11 fixes this bug partially, but not 100%. 


I have to re-start the router-box (internet modem) to get internet.

Let us hope they fix it before final release of 17.04.

---

### Post by mc4man on 2017-03-28
> **moma said:**
> Re-hi,
I do not think the new kernel (v4.11) repairs this bug.
I am still having the same wifi-problem occasionally.

I have to re-start the router-box (internet modem) to get internet.

Let us hope they fix it before final release of 17.04.

For me so far the best solution is to change nameservers, it has worked very well with exception of occasional glitch if going to/coming out of  suspend.
Due to apparent myriad of network issues in recent times I doubt what's affecting _Me_ will be fixed unless inadvertently so..

---

### Post by moma on 2017-03-28
Ok, I added the following lines to /etc/NetworkManager/conf.d/99-mac-addr.conf 
I have absolutely NO idea if these lines fixed my issue, but I still have internet (after couple of normal re-logins or reboots). 
Let us see if this is consistent over time. Now all is good. 

$ sudo gedit /etc/NetworkManager/conf.d/99-mac-addr.conf

[device.mac-addr]
wifi.scan-rand-mac-address=0

[connection.mac-addr]
wifi.cloned-mac-address=preserve
#ethernet.cloned-mac-address=preserve

EDIT: Still struggling with wifi on 17.04.

---

### Post by rrnbtter on 2017-03-29
Greetings,
Regarding this issue on my laptop. If I disable WIFI with my F7 key and then re-enable with my F7 key the matter is resolved. I don't know the desktop version of this since I don't use a desktop.

---

### Post by rrnbtter on 2017-03-30
Greetings,
This problem is mitigated considerably with the 4.11 RC4 kernel. At this point I can't say that it is corrected entirely. Still testing!

Linux rrnbtter-110-15ISK 4.11.0-041100rc4-generic #201703261831 SMP Sun Mar 26 22:42:30 UTC 2017 i686 i686 i686 GNU/Linux

---

### Post by moma on 2017-04-07
A temporary solution.
Set the addresses of DNS servers manually.
Here are my DNS addresses for servers in Portugal (Portugal / EU). 
[ATTACH=CONFIG]274459[/ATTACH]
[ATTACH=CONFIG]274460[/ATTACH]

Google for your internet provider + DNS Server.

8.8.8.8  and 8.8.4.4 are Google's (Google.com) DNS servers.

I have Ubuntu GNOME 3.24.

---

### Post by quyen2 on 2017-04-12
I am in Malaysia and used your advice. It worked! Thanks moma.

---

### Post by BigCityCat on 2017-04-13
I tried using the google servers and while it did work. There were a lot of disconnections. After googling my ISP DNS settings and using those numbers instead of google DNS. This works much better. I only get disconnected about once an hour using this method. I also installed Kernel 4.11.

---

### Post by ptn107 on 2017-04-13
I got my wireless working finally on 17.04 by going into network connections and setting ivp6 to ignore for my network.

[ The image won't upload so here: [http://pasteboard.co/oW62xUiK.png]("http://pasteboard.co/oW62xUiK.png") ]

It's working on kernel 4.10.0-19.21

---

### Post by srdrhl146 on 2017-04-16
I'm from India, the google's DNS Trick worked.

---

### Post by tajreed on 2017-04-16
Does upgrading to the 4.11 rc kernel fix this problem?

---

### Post by rrnbtter on 2017-04-16
Greetings,

> **tajreed said:**
> Does upgrading to the 4.11 rc kernel fix this problem?

The 4.11 AMD64 RC7 kernel is playing fair right now on my fresh 17.04 install. I put a new install of Gnome Ubuntu 64 on my wife's Toshiba 10" Laptop and she is having no problems with the 4.10-19 kernel on that Intel Atom system. So worth a try.

---

### Post by rrnbtter on 2017-04-17
Greetings,
This is odd. Closed my cover last night. Opened it this morning and now WIFI with RC7 is trash, even after a reboot. Had to revert back to RC6 and it back to working but not very good.

---

### Post by rrnbtter on 2017-04-17
Greetings,
There are new dns libs in the updates. Seems to work fine with default 4.10 kernel. Haven't tried it with RC kernel yet.

---


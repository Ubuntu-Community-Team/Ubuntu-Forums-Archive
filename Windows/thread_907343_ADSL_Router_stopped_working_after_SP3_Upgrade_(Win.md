---
title: "ADSL Router stopped working after SP3 Upgrade (Windows XP)"
date: 2008-09-01
forum: Windows
---

### Post by diwas on 2008-09-01
I have TP-Link TD-8817 ADSL Router which is working fine in Ubuntu but stopped working in XP after SP3 upgrade (which is provided as update by microsoft).

I dont know what to do...is there any solution?

---

### Post by Joeb454 on 2008-09-01
Moved to Windows Discussions.

Posting any errors you receive may help :)

---

### Post by diwas on 2008-09-01
Thank you.

The error is when i turn on the router in XP, a little icon containin two monitors and a movin kind of pointed light blinks and the message is "Acquiring network connection(or address...i forgot sorry)"
And ADSL light on the router does not turn on constantly (aka it blinks).

Since the router is in bridge mode...when i try to connect thru Start>Connect To>ADSL(which contains password and all). It says "Remote Computer ddnt respond". While in Ubuntu everything is smooth.

I dont quite use XP, its for my dad and both the OS are in the same box...wid same hardware and all.

So I think there's smthg wrong wid the driver XP has...or doesnt have.
I checked out the site of the router if it has any driver or patch to correct this problem...but it only has USB driver of the router, whereas i use ethernet card to connect in both system.

ON TOP OF THAT the SP3 wont uninstall. It says something like "File not found".

---

### Post by mellowd on 2008-09-01
I don't think it's anything with the router itself.

First, switch your router off for 2 minutes and power it back up. What happens?

After a few minutes click start - run and type cmd then press enter.

Type ipconfig /all (paste your results here)

Now type ipconfig /release

now type ipconfig /renew

and for good measure, type ipconfig /flushdns

now wait 2 minutes and type ipconfig /all again.

Paste here what you get

---

### Post by fiddledd on 2008-09-01
It's not what you described, but have a read [here](http://support.microsoft.com/kb/955084). It might help.

---

### Post by diwas on 2008-09-01
Thank you guys for your enormous help. I will do ASAP.

In the meanwhile (im sorry if this is not the appropriate place to say this...) I have a problem in ubuntu as well. Please check this thread out.
[http://ubuntuforums.org/showthread.php?t=889948](http://ubuntuforums.org/showthread.php?t=889948)

Thank you.

---

### Post by diwas on 2008-09-01
> 
First, switch your router off for 2 minutes and power it back up. What happens?


1. Acquiring Network Address in taskbar...beside the system clock appears.
2. Constantly says Network Cable is Unplugged.
3. The process repeats.(1 and 2)


> 
After a few minutes click start - run and type cmd then press enter.

Type ipconfig /all (paste your results here)

```

Windows IP Configuration
	Host Name.............................:home
	Primary Dns Suffix....................:
	Node Type..............................:Unknown
	IP Routing Enabled...................: No
	WINS Proxy Enabled.................: No
Ethernet adapter ADSL:
	Media State............................: Media disconnected
	Description..............................: RTL8139D PCI Fast Ethernet Adapter
	Physical Address.......................:00-18-46-01-4E-E3

```

> 
Now type ipconfig /release

now type ipconfig /renew

and for good measure, type ipconfig /flushdns

now wait 2 minutes and type ipconfig /all again.

Paste here what you get


With ipconfig /release the following stuff comes out: 
```

IP Address for adapter ADSL has already been released.
```

With ipconfig /renew it takes a long time and the error is: 
```

Windows IP configuration
An error occurred while renewing interface ADSL: unable to contact your DHCP server. Request has timed out.
(In the meantime the place where the "Network cable is unplugged" message is shown...another message "This connection has limited or no connectivity..." Is shown)
```
With ipconfig /flushdns:
```

Windows IP Configuration
Successfully flushed the DNS Resolver Cache.

```

With ipconfig /all:
```

Windows IP Configuration
	Host Name.............................:home
	Primary Dns Suffix....................:
	Node Type..............................:Unknown
	IP Routing Enabled...................: No
	WINS Proxy Enabled.................: No
Ethernet adapter ADSL:
	Connection-specific DNS Suffix....:
	Description..............................: RTL8139D PCI Fast Ethernet Adapter
	Physical Address.......................:00-18-46-01-4E-E3
	Dhcp Enabled...........................: Yes
	Autoconfiguration Enabled..........: Yes
	Autoconfiguration IP Address......: 169.254.214.12
	Subnet Mask...........................: 255.255.0.0
	Default Gateway......................: 169.254.214.12

```

---

### Post by mellowd on 2008-09-01
Ah, you are definately not getting an IP address from the routers dhcp. 

If you get a 169.x.x.x it means windows has assigned its own address (but it assigns no gateway, so you can't get out to the internet)

The link that fiddled provied shows you how to assign a static address. You may need to do that at least until a firmware upgrade is released. It isn't difficult at all and should work fine.

---

### Post by diwas on 2008-09-01
Yes, it worked (the link from microsoft). But I have another problem too. In ubuntu when i hit 192.168.1.1, my router's page is easily opened. But here in XP, it wont. So i cannot upgrade my firmware.

But honestly, im scared to upgrade to a new firmware...hehe. What if its wrong...the whole thing (regarding the router) will go down...is there anyway i cud alter the changes of my router's firmware if i accidently installed a wrong firmware?

---

### Post by mellowd on 2008-09-01
There is always a risk with upgrading firmware. Depending on the model you might be able to load an older firmware if it goes wrong. Some routers you'll brick if you do it wrong. 

If you're really uncomfortable doing it, get a friend who knows what they doing to do it.


You should be able to update from ubuntu as well. It depends on your model is updated. Usually all you need to do is browse your your router, click the upload button and browse on your local disk for the upgrade file (your could be different though)

---

### Post by diwas on 2008-09-01
> Yes, it worked (the link from microsoft). But I have another problem too. In ubuntu when i hit 192.168.1.1, my router's page is easily opened. But here in XP, it wont. So i cannot upgrade my firmware.

But honestly, im scared to upgrade to a new firmware...hehe. What if its wrong...the whole thing (regarding the router) will go down...is there anyway i cud alter the changes of my router's firmware if i accidently installed a wrong firmware?

(Sorry for posting twice...)

---

### Post by diwas on 2008-09-01
Yes, there's a place in router's place where i can upgrade the firmware. I have carefully downloaded the firmware by goin through every detail. I wil try to do it myself.

I will inform u if anything goes wrong.


BTW any solution to this page? 
[http://ubuntuforums.org/showthread.php?t=889948](http://ubuntuforums.org/showthread.php?t=889948)

---


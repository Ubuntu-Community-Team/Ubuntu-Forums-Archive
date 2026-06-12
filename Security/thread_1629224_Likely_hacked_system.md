---
title: "Likely hacked system?"
date: 2010-11-23
forum: Security
---

### Post by joegumbo on 2010-11-23
Hello,

I am running Ubuntu 10.04.1 LTS 32-bit dual-booting with Windows 7 64-bit on my desktop pc.  I mostly use Linux, not Windows.  I am running Lubuntu/LXDE.  The sytem is fully updated.

A few days ago, I started having problems logging into my [www.softhome.net](www.softhome.net) account.  I would get strange error messages such as "Password invalid (0x008 )" and "This signup form is no longer valid. Please use the one on
> >> [www.SoftHome.net](www.SoftHome.net) instead."

Naturally, I thought it was a problem with the softhome site.  So I contacted them.

They claim that it most likely that my opc is infected with something.  I did not think this was likely, so I booted into Windows 7 and tried there.  Again, the same strange error messages in Windows.

I recontacted softhome.  Again, they advised me that I was probably hacked.

So, I tried using a Mepis LiveCD.  I could now logon to the softhome site with no problems.

Apparently, something has invaded both my Lubuntu and Windows 7 partitions.

I have kept Lubuntu fully updated.  I am using Firestarter fw, as well as a router and an AlphaShield hw fw.  'denyhosts' is installed and configured.  'chkrootkit' indicates no problems.  'rkhunter' shows no rootkits, either.

---

### Post by brian_p on 2010-11-23
> **joegumbo said:**
> 

I recontacted softhome.  Again, they advised me that I was probably hacked.
It resonates - so you are inclined to go along with it. Neither of you know - so the problem remains.

> Apparently, something has invaded both my Lubuntu and Windows 7 partitions.

It's only apparent. In reality it hasn't.

> I have kept Lubuntu fully updated.  I am using Firestarter fw, as well as a router and an AlphaShield hw fw.  'denyhosts' is installed and configured.  'chkrootkit' indicates no problems.  'rkhunter' shows no rootkits, either.

One of these is the cause of your problem. I'd start by deleting all your firewall rules.

---

### Post by joegumbo on 2010-11-23
Hi Brian,

I'll investigate my fw's, as you suggested.

But I don't see why I cannot login at softhome from both Linux and Windows on the same machine. But, I can login if I use a LiveCD on the same machine.

It would seem that both Windows and Ubuntu have the same problem.

Thanks,
-Joe

---

### Post by FuturePilot on 2010-11-23
Try clearing your browser's cache. Or try creating a new browser profile.

---

### Post by mr-woof on 2010-11-23
I agree with future pilot, clear your browsers cache/cookies etc

---

### Post by dtfinch on 2010-11-23
I don't use their service, but if you use an anonymizing proxy on both windows and linux, and login with "restrict access" checked, I imagine it'll kick you out for accessing the site from multiple ip addresses.

If you were really hacked somehow, which I doubt, I imagine it'd be at the the dns server rather than your computer, but only if you manually specified one in both linux and windows, different from the dns server suggested by dhcp (which the livecd would use), and someone managed to poison the dns cache. Then you could be sent to a password logging proxy.

---

### Post by joegumbo on 2010-11-24
Thank you all so much for your help :)

I tried clearing out the browser's cache, removing cookies, and creating a new profile.  I still cannot login at softhome.net.

I use Comcast.  I did nothing to change from their DNS service.

I also scanned Windows with the Norton Suite that Comcast provides. It gave me a clean bill of health.

I was able to login at softhome just fine until a few days ago from Ubuntu.

However, there has been some anomalous behavior in both Ubuntu and Windows...

About a week ago, when I tried to login to Lubuntu, my system froze at the splash screen.  I had to force a hard shutdown and then reboot. This happened twice.

Yesterday, when I tried updating my antivirus in Windows, Norton complained that my subscription had expired. I had to try several times to update my definitions.  It eventually allowed me to.

Norton also warned me that my AV was turned off.

I received warnings from Windows that my firewall was turned off.  I went into Control Panel and was able to turn it back on.

When I tried to connect to the net from Internet Explorer, I received a message that the I.E. was not able to access the net.  I then tried with 64-bit I.E. and was able to.  Then, I was able to access the net from I.E.  Of course, I was not able to login at softhome.net.

Thanks! :)
-Joe

---

### Post by brian_p on 2010-11-24
> **joegumbo said:**
> 

I tried clearing out the browser's cache, removing cookies, and creating a new profile.  I still cannot login at softhome.net.

Being able to log in using a Mepis LiveCD is curious. I'm going to suggest you try a different browser. Lynx should do it if there is no JavaScript involved. Otherwise a graphical one, say Chromium.

---

### Post by joegumbo on 2010-11-24
From Ubuntu, I just tried Seamonkey, Epiphany, Opera, and "links www.softhome.net".   I cannot login at softhome.  I keep getting the same error message.

Thanks anyhow :)

Edit:  I also tried Chromium.  Same error message.

---

### Post by cwa on 2010-11-25
from my experience in dealing with malware (I am not a security expert, just have done research and had my far share of trying to clean computers)

I would recommend scanning your windows side with more than one malware finder. Malwarebytes for example, or something else. From my understanding and knowledge, one program can detect something and another one can not. Also, rootkits can hook into the system in a way to avoid being detected. I would also run hijackthis from trendmicro, it might be able to see if any rouge browser helper objects or malware start up entries. 

System internals process explorer can be used to look at all of the files that a process has open, it can be used to detect if a malware has hooked it self to IE or explorer or something else. 

Also, on the linux side, a malware can modify ls (for example) to list everything but itself. 

paranoia comments aside, this can also be done to rule out virus infection. I find it odd that both windows and linux cannot access the site, but a live cd can.

---

### Post by joegumbo on 2010-11-25
I think I may have a lead...

I tried using 'clamscan' on my home directory.  This is the error message I got:

[COLOR="Blue"]joegumbo@joegumbo-desktop:~$ sudo clamscan -r -i /home/joegumbo/*
[sudo] password for joegumbo: 
Bytecode run timed out, timeout flag set

libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code

Bytecode run timed out, timeout flag set
libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code

Bytecode run timed out, timeout flag set
libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code

Bytecode run timed out, timeout flag set
libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code

Bytecode run timed out, timeout flag set
libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code[/COLOR]


I checked on the version of Java I have installed:

[COLOR="Blue"]joegumbo@joegumbo-desktop:~$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)
[/COLOR]


The only thing I can think of that both Windows and Ubuntu have in common is Java.  The Mepis LiveCd would have an older version of Java.

---

### Post by joegumbo on 2010-11-26
I've tracked down a bit more...

The error message I'm getting...

[COLOR="Blue"]0x0008[/COLOR]

is listed as meaning

[COLOR="Blue"]Authentication type is unsupported.[/COLOR]

at [http://www.eldos.com/documentation/sbb/documentation/ref_cl_idsshclientserveriohandler9_evt_onerror.html?sphrase_id=79867](http://www.eldos.com/documentation/sbb/documentation/ref_cl_idsshclientserveriohandler9_evt_onerror.html?sphrase_id=79867)

I strongly suspect a Java problem.

I'm going to try to throw the ball back to the softhome folks.  If they give me anything useful, I'll report back here.

---

### Post by cwa on 2010-11-26
If you suspect Java, then have you tried reverting back to an earlier version and seeing if you can connect?

cwa

---

### Post by stoneage on 2010-11-26
Interesting.......


I have the same error from clamscan. I just experienced an unexplained restart and ran some checks, just in case.

For clamscan -ir and for clamscan -i  I get the error you quote, but clamscan -r seems to run ok. It did quote the error, but it is also still scanning.

I also find clamscan -irl FILE successfully writes to a file.

No infected files found so far :D



EDIT - Ack, spoke too soon:-

Bytecode run timed out, timeout flag set
libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code

---

### Post by joegumbo on 2010-11-27
I did look for an earlier version, but I could not find one listed in Synaptic.  The have  IcedTea6 and Sun's Java6.   

I did a complete uninstall of all Java and rebooted.  I then installed Sun's JDK and browser plugin through Synaptic.  But, I still get the same error message when trying to login at Softhome.

I tested to see which version of Java isa installed, and these are my results:
[COLOR="Blue"]joegumbo@joegumbo-desktop:~$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)[/COLOR]

It looks like I still have icedtea on here too, even though Synaptic tells me that it is uninstalled.

When I go to
[COLOR="Blue"]http://www.java.com/en/download/help/testvm.xml[/COLOR]

I get this output from their Java applet:
[COLOR="Blue"]Vendor: Sun Microsystems Inc. 
Version: Java 6 Update 22 
Operating System: Linux 2.6.32-26-generic-pae Architecture: i386 [/COLOR]

'clamav' was working perfectly for me until recently.  I used only "[COLOR="Blue"]clamscan -r -i /path/directory/*[/COLOR]".  These JIT complaints are recent here, too.

---

### Post by joegumbo on 2010-11-27
I have now set my router to use OpenDNS rather than Comcast.  I am still getting the same error messages at Softhome.

---

### Post by joegumbo on 2010-11-27
Well, I can no longer login from my LiveCD, either.

This has got to be a softhome problem.

Thank you everyone for your help :)

Tomorrow, I'm going to try from a completely different pc at a different address.

---

### Post by Wobblybob on 2010-11-27
> **joegumbo said:**
> 

[COLOR="Blue"]joegumbo@joegumbo-desktop:~$ sudo clamscan -r -i /home/joegumbo/*
[sudo] password for joegumbo: 
Bytecode run timed out, timeout flag set

libclamav JIT: *** JITed code intercepted runtime error!
LibClamAV Warning: Bytecode failed to run: Unknown error code



I'm getting this error today running the same command, I've only just added Clam and this is the first run and get the same message on 2 PC's running Ubuntu so i think you may have 2 different problems. I installed the clamtk front end and when I run that I don't get the error! I've even downloaded the latest version from the clam website with the same result.

---

### Post by joegumbo on 2010-11-28
There probably are two different issues here.  

It is interesting that clamav works OK with the clamtk frontend.  I wonder if there would be error messages when starting it from the cli.

---

### Post by dtfinch on 2010-11-29
You might want to check if your IP address is on any blocklists, in case softhome uses one of them to try and detect bot logins. [http://www.dnsbl.info/](http://www.dnsbl.info/)

---

### Post by joegumbo on 2010-11-29
Hi dtfinch,

An awesome site.

Thank you ! :)

But nope, I'm not listed.

Thanks again,
-Joe

---


---
title: "Need help troubleshooting linux PC for Ethernet remote desktop connection to win7 pc"
date: 2022-12-05
forum: Ubuntu/Debian BASED
---

### Post by DVD-R on 2022-12-05
Hello All,
I am trying to troubleshoot a problem with my Linux laptop making remote connection to a win7 laptop
Here are my steps so far.

I have 3 laptops
1) Laptop_A (win7)
2) Laptop_B (win7)
3) Laptop_C (Ubuntu 16 linux lite)

I want to access Laptop_B via a remote desktop using the Ubuntu 16 laptop

As a test - I can connect to Laptop_B with remote desktop - using laptop_A

In Laptop_B - before I connect the CAT5 cable - I watch the network monitor which shows no Ethernet connection.
I plug the CAT5 cable into both win7 laptops and then I can see the Ethernet connection being established.
Then - with laptop_A I can remote desktop into laptop_B

Next I unplug the CAT5 cable and plug it into my Ubuntu 16 laptop.
I do not see any Ethernet connection showing in Laptop_B

I'm not familiar enough with Linux network commands to determine whether or not the Ethernet port on the Ubuntu laptop is working.

Can anyone help?

Sincere thanks!

---

### Post by DVD-R on 2022-12-05
One thing I tried in the Ubuntu 16 PC is this:

sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 06
       serial: f0:de:f1:2f:6e:0f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz

So I think this means my Ethernet adapter is probably working.

---

### Post by ajgreeny on 2022-12-05
I can't answer the questions you ask but I hope you are aware that all the operating systems you have listed are out of support so you should not really be using them at all.

If they are connected to the web you are at a great risk of being attacked which is a risk to yourself and anyone else connected to the same network, be it local area or wide area, ie, the internet.

So please do use fully supported OSs.

---

### Post by grahammechanical on 2022-12-05
Linux Lite is based upon Ubuntu but it is not Ubuntu. Anyway Ubuntu 16.04 Long Term Support version reached end of life April 30th 2021. How long is your version of Linux Lite supported?

Have you checked in System Settings that Ethernet is enabled? Is Ethernet enabled in the motherboard's BIOS/UEFI settings utility? Do you have a modem with an Ethernet port. You can test laptop C ethernet adapter by trying to access the ISP using the Wired (Ethernet) connection.

You can try running

```
lshw
```

and see what is reported under the Network headings. Look for something like this:

> 
       *-network
             description: Ethernet interface
             product: Ethernet Connection (10) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 00
             serial: 80:fa:5b:9d:b0:5c
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.13.0-48-generic firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:130 memory:b1400000-b141ffff

Notice that my ethernet adapter has a driver installed.

Regards

---

### Post by coffeecat on 2022-12-05
Linux Lite is not Ubuntu nor is it an official flavour of Ubuntu. * Thread moved to **Ubuntu/Debian Based** sub-forum.*

Wikipedia tells me that the version of Linux Lite based on Ubuntu 16.04 also went end of life in April last year. Please heed what others have already said about not using an obsolete and unsupported version of an operating system.

---

### Post by DVD-R on 2022-12-05
Here is the official language:
Linux Lite is a beginner-friendly Linux distribution based on Ubuntu LTS and featuring the Xfce desktop.
In this  case it is Ubuntu 16.04 LTS - which is the last version of Ubuntu officially supporting 32bit hardware.
I would otherwise be forced to a different OS which I already know I would dislike.

---

### Post by DVD-R on 2022-12-05
Thank you grahammechanical!

In the example you provided - which line describes the driver?
Sincere thanks!

And excellent idea about plugging the PC into the ISP router!!
I will do that asap!!

---

### Post by DVD-R on 2022-12-05
I want to thank you again grahammechanical
I am currently connected by CAT5 to the IPS router
So that eliminates hardware as the issue.
I'll have to do some more digging on Linux Network commands I can use to trouble-shoot the issue.

---

### Post by guiverc on 2022-12-05
> **DVD-R said:**
> Here is the official language:
Linux Lite is a beginner-friendly Linux distribution based on Ubuntu LTS and featuring the Xfce desktop.
In this  case it is Ubuntu 16.04 LTS - which is the last version of Ubuntu officially supporting 32bit hardware.
I would otherwise be forced to a different OS which I already know I would dislike.

The last Ubuntu release that had full *i386* or 32-bit support was Ubuntu 19.04 (*with extremely limited ISO or installation media produced though**, but if used security updates were provided for the full disco cycle*), and not 16.04.

**Ubuntu still supports 32-bit hardware (*armhf*) up to Ubuntu 22.04 LTS**, it was just 32-bit *i386* or x86 that stopped at Ubuntu 19.04.

The last *i386* ISO was released in 2021-August though I recall QA-testing *i386* in  [2020-August]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") which included *i386* ISOs, [as I recall doing QA using pentium 4, pentium M]("http://iso.qa.ubuntu.com/qatracker/milestones/415/builds") and other boxes that were 32-bit x86 (ie. *i386*) only.  (*FYI:  the last i386 in August-2021 was [18.04.6]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") but I can't recall doing any QA for that release**; flavor support had already ended* *but a [quick look shows i386 included]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/")*)

[B]Ubuntu still support *i386* or 32-bit x86 using Ubuntu 18.04 LTS.

[Ubuntu 16.04 ESM support still exists, but that does not include *i386*]("https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm")[/B], and many packages that were supported during the standard support (ie. till 2021-April) via *deb* package are **now only supported via *snap* package**.  You'd not want to be using 16.04 if using *i386* in my opinion.

---

### Post by QIII on 2022-12-05
> **DVD-R said:**
> I would otherwise be forced to a different OS which I already know I would dislike.

Unfortunately, that may be what you will have to do

 A couple of community members at large, a Forums Staff Member and a Forum Admin have told you and now a second Forum Admin is telling you that running an old, unsupported release of an OS (particularly 32 bit, for which updated software is fading fast) is a bad idea.  Please take the weight of that to heart.

Windows 7 is also unsupported and dangerous.

You are putting yourself and all other netizens in jeopardy.  Old, unsupported and non-updated OSes and software are the primary vectors for nefarious activity on the web.

---

### Post by guiverc on 2022-12-05
> **DVD-R said:**
> 
I would otherwise be forced to a different OS which I already know I would dislike.

I didn't address this part of your quote, only noticing that fact now that QIII has answered.

Just FYI:   but I'm still an *i386* user (*part of why I was heavily involved in the QA or Quality Assurance testing of i386*) and still have at least one 18.04 *i386* system running on an old IBM Thinkpad t43, using it often to provide example posts of `ubuntu-support-status` in various Lubuntu & other posts.

I'm also involved in QA testing of Debian, and have many Debian *i386* installs.  When the *existing *18.04 install on my thinkpad t43 reaches EOSS (*end of standard support; April 2023*) I expect to switch it to Debian just like my other ibm thinkpad t43p, r50p, dell latitude d610 & other *i386* devices already use.  As 18.04 is still supported (*it was originally a Lubuntu 18.04 LTS install; but with Lubuntu 18.04 LTS I now consider it a Ubuntu 18.04 install*) I've not felt the need yet to switch **given how I use the box**.

You'll be much better using a *supported* OS than any *End of Life* OS if the machine is used online. I agree completely with QIII.

---

### Post by QIII on 2022-12-05
I believe that Bodhi Linux still makes 32-bit releases.  

Just to be clear:  The issue with 32-bit systems is that the 32-bit world is fading, just as 8 and 16-bit did.  The Elves are sailing to the West from the Grey Havens.  That is not the same as concern about unsupported releases of operating systems and software.

A supported release of a 32-bit operating system, such as Bodhi or 18.04 (Really.  Heh.  Didn't even think about it.) does not carry the risk of unsupported, dangerous software.

---

### Post by HermanAB on 2022-12-06
You need an IP address and a default route.  Windows runs something like Bonjour when there is no router with DHCP.  So either use a home router to automate the addressing or set it manually with the ip command.

---

### Post by DVD-R on 2022-12-06
Thank you.
Would I be putting anyone here on this forum in jeopardy by continuing to ask questions?
Sincere thanks

---

### Post by DVD-R on 2022-12-06
Ok thank you!
Per your recommendation - I am downloading Bodhi legacy release - which is listed as a 32bit OS.
I will install that OS and continue using it whether I dislike it or not.

In such case - am I clear to continue using this forum to ask questions?
Thanks

---

### Post by DVD-R on 2022-12-06
It looks like Linux mint 19.2 is also available in 32bit and is also an XFCE desktop.
Is everyone here ok with me using that OS for now?

---

### Post by DVD-R on 2022-12-06
Thank you HermanAB!
If I turn off wifi - and connect the Cat5 to my ISP router - within a minute that connection will be detected and the PC will be connected to the ISP router with internet access.
So that confirms the Ethernet port is functional and can be activated.

With the Cat5 connected to the windows PC instead of the ISP router - I tried the following:  sudo ip addr add 192.168.42.44/24 dev enp0s25
enp0s25 - within the software - functions as an alias for eth0

This command disconnected the wifi and a popup displayed indicating Ethernet connection.
However the cable is not plugged into the ISP router - but rather into the windows PC.
The windows connection monitor did not show any activity
And trying to PING the Linux machine was unsuccessful.

I also tried the commands:
sudo ip link set enp0s25 down
sudo ip link set enp0s25 up

And this did not make any change
Windows still does not see the Ethernet adapter in the Linux PC

---

### Post by guiverc on 2022-12-07
> **DVD-R said:**
> It looks like Linux mint 19.2 is also available in 32bit and is also an XFCE desktop.
Is everyone here ok with me using that OS for now?


Linux Mint 19 is based on Ubuntu 18.04 LTS, so has the same date as Ubuntu 18.04 LTS (*which has i386 support too*), ie. April 2023 (that's EOSS for 18.04, but EOL for Linux Mint 19)

I would ensure you're using a supported kernel (*security differs with Linux Mint, with more onus on you doing the checks with differing standards to Ubuntu*), and I had a look but they don't have a *manifest* so I can do a few quick checks myself. A look at [https://www.linuxmint.com/rel_tina_xfce_whatsnew.php](https://www.linuxmint.com/rel_tina_xfce_whatsnew.php) shows the 4.15 kernel (*Ubuntu still patch that*), plus also 4.18 & 5.0 which are *unpatched for security fixes* as those are from Ubuntu releases 18.10 & 19.04 thus long EOL. If you're using you box offline though, it won't matter.

---

### Post by DVD-R on 2022-12-07
Wonderful!
The Linux box here is running online - but not the windows machine.
I only use the windows machine very infrequently and never allow it online.
Eventually I'll figure out how to remote desktop into it!  :-]

I'll probably have mint 19.2 up and running tomorrow.
And then I can come back - and hopefully there will be some expertise here to help me troubleshoot the remote desktop problem.
Sincere thanks!

---

### Post by QIII on 2022-12-07
> **DVD-R said:**
> In such case - am I clear to continue using this forum to ask questions?

Of course!  There are forums specifically for Ubuntu-based distros, other distros and even Windows.

I see you may have installed Mint.  In that case, we have a MINT sub-forum.

---

### Post by DVD-R on 2022-12-07
Thank you QIII
Perhaps with Mint 19.2 installed - it would be more appropriate for me to ask questions in the Mint forum?

---


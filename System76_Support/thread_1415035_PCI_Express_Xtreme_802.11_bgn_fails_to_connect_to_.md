---
title: "PCI Express Xtreme 802.11 bgn fails to connect to wireless internet"
date: 2010-02-24
forum: System76 Support
---

### Post by savantelite on 2010-02-24
New Wild Beast to be used with Bluecherry Xubuntu DVR. 

The wireless has connected but has struggled since Xubuntu 9.04 update. It didn't work that great before. 

I have a Wireless n router and card but the default xubuntu drivers don't feel like they are optimised for the card. 

So how do I make wireless PCI Xtreme 803.11 BGN card to work better under Xubuntu 9.04?

---

### Post by thomasaaron on 2010-02-24
We don't test it with xubunutu, but i image it uses the same drivers for the card (probably the ath5k module).

Did you try it in Ubuntu to see if it had the same problem there?

---

### Post by curtishall on 2010-02-24
> **thomasaaron said:**
> We don't test it with xubunutu, but i image it uses the same drivers for the card (probably the ath5k module).

Did you try it in Ubuntu to see if it had the same problem there?

Technically speaking if System76 supports Jaunty then you can install their Jaunty based version and then email our support for the repository link and you can install the Bluecherry DVR software, that way you still have a 'supported' system from System76.

Thanks

--
Curtis Hall
Bluecherry
[www.bluecherrydvr.com](www.bluecherrydvr.com)

---

### Post by savantelite on 2010-02-24
Thank you both for your quick replys back. 

What option should I take next for installing Jaunty. I am struggling with Xubuntu quirks. But if I download the newest iso of Ubuntu Jaunty will I need to install any specific repositories for my wireless card? Or will Ubuntu auto-find them?

Is there a specific system76 iso of ubuntu for Jaunty?

I am looking for your opinion on the easest long-term solution.

---

### Post by thomasaaron on 2010-02-24
I'm not sure that Jaunty or Karmic is the issue... your Leopard should run both fine.

The problem is that we do no testing with the Ubuntu derivative Xubuntu, which uses a different wireless management program (as opposed to Network Manager, which manages the wireless under Ubuntu).

If you haven't already, you may want to try installing wicd...

sudo apt-get install wicd

...as I think most xubuntu users run wicd.

Is there a particular reason you are running Xubuntu on your system? Is it necessary for Bluecherry? If not, there isn't really a need to run such a minimalist OS on such a powerful comptuer... unless you just want to.

---

### Post by savantelite on 2010-02-24
BlueCherryDVR comes with an iso of xubuntu tweaked to run survelence system. Pop the CD and you get an up and running DVR usually.

---

### Post by curtishall on 2010-02-24
> **thomasaaron said:**
> I'm not sure that Jaunty or Karmic is the issue... your Leopard should run both fine.

The problem is that we do no testing with the Ubuntu derivative Xubuntu, which uses a different wireless management program (as opposed to Network Manager, which manages the wireless under Ubuntu).


Xubuntu uses NetworkManager, wicd is not installed by default

---

### Post by thomasaaron on 2010-02-25
I see. Then the problem is probably either the wireless card or the router (or the combination of the two). So, let's approach it from that angle. Thanks for the help, curtishall.

savantelite, you said...

> The wireless has connected but has struggled since Xubuntu 9.04 update. It didn't work that great before. 

Can you please provide a little more detail on what's going on? Is it dropping connections? Is it slow?

---

### Post by savantelite on 2010-02-25
After I installed Ubuntu Jaunty 64 bit I was able to connect to the wireless and update my system. After the update though my wireless stopped working.

After retyping my password and keyring I tried rebooting with the same failed attempts. It was only when I manually deleted my network(right-click edit connections in "network manager" and then retyping my password did it start working again?

---

### Post by savantelite on 2010-03-01
After down grade to Ubuntu 9.04 Jaunty wireless connects but is very sluggish. 

It will also disconnect randomly. I physically must go to the computer and click network manager and the wireless point to make it connect again.

---

### Post by savantelite on 2010-03-02
I downgraded to Jaunty for some software that required it. Since the downgrade my wireless has been very flaky. I am running a new Wild Beast. 

Why does my wireless keep disconnecting?

---

### Post by thomasaaron on 2010-03-02
OK, thanks for clarifying. The next time it drops the network connection, please *make note of the time* and then go directly to System > Admin > System76 Driver and click the Support tab and the Create button. This will create an archive called logs.tar in your home directory. Please attach that archive to this thread, and I'll have a look.

Also:

1. How old is your Access point? And what brand is it?
2. Do you have it set to "N" only, or "Combination"?
3. Have you tested with a different access point?

---

### Post by thomasaaron on 2010-03-02
Let's work on it in just one thread...
[http://ubuntuforums.org/showthread.php?t=1415035&page=2](http://ubuntuforums.org/showthread.php?t=1415035&page=2)

---

### Post by savantelite on 2010-03-02
The system76 driver could be my issue. I haven't installed it. I just have a stock version of Jaunty. 

How do I Install system 76 driver?

Also 

1. How old is your Access point? And what brand is it?   "Netgear WNR2000"
2. Do you have it set to "N" only, or "Combination"?   combo
3. Have you tested with a different access point?   No

---

### Post by thomasaaron on 2010-03-02
The System76 Driver has nothing to do with your wireless, but it his here...

[http://planet76.com/repositories](http://planet76.com/repositories)
(second link from the bottom)

Download it. Double-click and follow prompts to install it. Then go to System > Admin > System76 Driver > Restore tab > Restore button to run it.

Try setting your access point to n-only.

---

### Post by savantelite on 2010-03-03
After the system76 drivers were installed I was still having issues with the wireless. So I finally checked my keyrings and I had four of them in the GNome2 folder. I deleted them and have no issues for the last hour.

---

### Post by savantelite on 2010-03-06
can no longer connect:(

Router status is fine. I am able to log on with my System76 Lemur. Wild Beast sees the network but doesn't connect. 

Network manager icon slows to a crawl and sometime just stops. After restart and resetting key and passphrase I am still not able to connect:(

Is this an issue difference between 9.04 and 9.10? Is it an issue between 32 bit and 64bit?

I am lost. Please help.

---

### Post by savantelite on 2010-03-06
It must be a bug with 9.04 32 bit Ubuntu wireless driver. I tried a liveUSB of Lucid Lynx Alpha 3 64 bit and it connects without a problem. I suspect that it will connect fine with Ubuntu 9.10 64bit also. The machine orginally came with 9.10 64 bit.

---

### Post by thomasaaron on 2010-03-08
We've never tested that machine with 9.04, but try running...

sudo apt-get install linux-backports-modules-jaunty

...and then rebooting.

---


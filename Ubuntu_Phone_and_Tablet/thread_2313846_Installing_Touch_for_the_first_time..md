---
title: "Installing Touch for the first time."
date: 2016-02-16
forum: Ubuntu Phone and Tablet
---

### Post by warren3 on 2016-02-16
Hi.

I'm a big Ubuntu fan and use it as my main OS now :)

So I picked up a cheap 2nd hand Nexus 4 in order to try Ubuntu Touch but I just have a quick question about installation.  My Ubuntu desktop is 15.10.

On the installation instructions for Ubuntu Touch it says:

[I]'Note that there is a no-longer updated version of the phablet-tools package in trusty/universe. Please use the PPA instead.'
[/I]
But it doesn't state how to get that PPA.  After googling I found a askubuntu page stating:

*'You need to install the phablet PPA in order to get phablet-tools:*
[I]$ sudo add-apt-repository ppa:phablet-team/tools
$ sudo apt-get update
[/I]*And then install as you expect:*
[I]$ apt-get install phablet-tools'

[/I]So do I need to install this PPA on 15.10?

Cheers.

---

### Post by nikkkko on 2016-02-16
Is your Nexus rooted? If so, try installing MultiRom.  You can then easily, (from the MultiRom gui), download and install Touch alongside whatever other Rom you choose. Useful, as you will probably want to switch back to Android pretty quickly...

---

### Post by warren3 on 2016-02-18
I am through with Google and Apple and Microsoft.  Tax dodging scum the lot of them.

I am fully committed to Ubuntu phone warts and all!

---

### Post by nikkkko on 2016-02-18
Agreed, which is why I went CardDAV/CalDAV in the first place, so that my contacts and calendar could be Google free.  However, I cannot find a way to sync Ubuntu Touch with my CardDAV/CalDAV service, (I use Fruux), otherwise I would be using my Nexus 4 with Ubuntu.

So which is better?  An Ubuntu phone using a Google account to sync calendar and contacts or an Android phone using CardDAV/CalDAV to sync calendar and contacts?  I made my choice and installed the AOSP ROM, (Android Open Source Project), for my operating system and can happily sync my data with Fruux.  The day Ubuntu Touch supports this open standard for syncing, I will switch but as it's been almost 2 years now, I'm not holding out much hope.

---

### Post by grahammechanical on 2016-02-19
What tutorial are you following? This wiki page lists the Nexus 4 as a supported device

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/)

And these are the installation instructions

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

The information on AskUbuntu might be out of date. ubuntu-device-flash should be in the 15.10 universe repository. I know it is there in 16.04. And according to this Launchpad page the ubuntu-sdk-team PPA is available for both for both 15.10 & 16.04

[https://launchpad.net/~ubuntu-sdk-team/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-sdk-team/+archive/ubuntu/ppa)

click "Technical details about this PPA" and open the drop down menu of the "Choose your Ubuntu version" panel. You will see that both xenial (16.04) and wily (15.10) are both listed. So, I suggest following the instructions on the Developer.Ubuntu.com web site.

Regards.

---

### Post by warren3 on 2016-02-20
Can I flash Ubuntu touch on a Nexus 4 running stock lollipop?

---

### Post by nikkkko on 2016-02-24
I have no problems installing Ubuntu, I was talking about syncing contacts using the open standard, CardDAV. If you know of a CardDAV client for Ubuntu which works, please let me know.

---

### Post by grahammechanical on 2016-02-24
> **warren3 said:**
> Can I flash Ubuntu touch on a Nexus 4 running stock lollipop?

Watch this video & you will see Unity 8 convergence running on a Nexus 4. 

[http://www.omgubuntu.co.uk/2016/02/ubuntu-tablet-convergence-xda-video](http://www.omgubuntu.co.uk/2016/02/ubuntu-tablet-convergence-xda-video)

---


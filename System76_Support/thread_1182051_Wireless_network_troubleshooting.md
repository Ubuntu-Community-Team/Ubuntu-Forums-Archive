---
title: "Wireless network troubleshooting"
date: 2009-06-08
forum: System76 Support
---

### Post by pseudotheist on 2009-06-08
Are there any tools available to assist in troubleshooting wireless network connections?  My computer doesn't seem to always agree with  my home wireless network.  Sometimes it connects just fine but usually it boots, looks around for a while, and asks me to confirm network settings.  It'll look some more and ask again.  Then eventually it'll ask for settings for all the other network it sees, then give up.  Sometimes I can tell it to try to connect to the home network again, other times it's removed from the list.  It's successfully connected at many different stages of this process, but with no predictability.

It does seem that whatever step is represented by the upper light in the icon turning green is the problem, but I have no idea what that's supposed to represent.  It's also likely that it may be a problem with my home router, as in the limited situations I've had occasion to use the laptop on another network it comes up fine (but it could also be the WEP).  Anyway, are there any available tools or commands to provide more visibility into this process, so I can at least figure out who to blame for this problem?

FWIW I have a Darter Ultra, running Jackalope.  It's an upgrade from Ibex, but I was having the problem before as well.

---

### Post by thomasaaron on 2009-06-08
Yes. Immediately after the next failure to connect, go right-click on the network manager icon and disable wireless networking.

Then go to System > Admin > System76 Driver > Support > Create, and attach the logs.tar archive it creates in your home directory to this thread.

I'm having you disable wireless networking so it doesn't repeatedly try to re-connect. That will help me isolate the instance in question.

---

### Post by pseudotheist on 2009-06-18
Yeah, I don't have the System 76 Driver under my System>Administration tab.  How do I re-install that?

---

### Post by thomasaaron on 2009-06-19
To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by pseudotheist on 2009-06-24
Logs attached.

---

### Post by thomasaaron on 2009-06-25
> Jun 24 15:41:20 ubuntu NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (CBR78) 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  Marking connection 'Auto CBR78' invalid. 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  Activation (wlan0) failed. 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jun 24 15:41:20 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 

Tell me more about your router. It looks like Network manager is sometimes unable to determine what info it needs to provide to the router. If this is intermittent, I'm thinking your router is getting flaky.

---

### Post by pseudotheist on 2009-06-26
It's a FIOS provided wireless gateway currently set up with 128 bit WEP.  I haven't poked around much in it, but believe I could, if you want to look at specific settings.

---

### Post by thomasaaron on 2009-06-26
Well, seeing as how it is intermittent (if I'm understanding correctly), I'm voting for either a) a flaky wireless card, or b) a flaky access point. 

Do you get the same results from your Darter with other access points?

---

### Post by pseudotheist on 2009-06-26
Haven't had enough experience with other access points to be conclusive.  But I'm going to a convference this week, which should help me gather more data.

---

### Post by akwala on 2009-06-29
This post moved to its own thread...
[http://ubuntuforums.org/showthread.php?t=1199910](http://ubuntuforums.org/showthread.php?t=1199910)

---

### Post by thomasaaron on 2009-06-29
akwala, you're kinda hijacking an unrelated thread.;) 

Nevertheless, do you (or have you ever) had Windows installed or dual-booted on that machine?

---

### Post by akwala on 2009-06-29
> **thomasaaron said:**
> akwala, you're kinda hijacking an unrelated thread.;) 
Apologies. Moved to new thread: [http://ubuntuforums.org/showthread.php?t=1199910](http://ubuntuforums.org/showthread.php?t=1199910)

> Nevertheless, do you (or have you ever) had Windows installed or dual-booted on that machine?
No. I've added more info in the new thread.

---

### Post by pseudotheist on 2009-06-29
SO, the wireless works just fine at the convention and the hotel, but neither of them have WEP.  Do the logs rule that out as a problem?

---

### Post by thomasaaron on 2009-06-30
You shouldn't have any trouble with WEP. So, again, it sounds like you probably just have a flaky AP. Try resetting it (if you haven't already). Sometimes that fixes these types of problems.

---

### Post by pseudotheist on 2009-06-30
Oh, I reset it regularly...

---


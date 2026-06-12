---
title: "Darter Upgrade to Feisty-Success!"
date: 2007-05-02
forum: System76 Support
---

### Post by jml on 2007-05-02
There have been several posts describing problems upgrading a Darter from Edgy to Feisty.  As my title suggests, I was able  to successfully, (if not quickly,) do the upgrade.  I needed information from several different sites, so I thought that putting it all together here may be helpful to others.

1.  If you have Automatix2 installed, uninstall it, and comment out all references to the Automatix repositories in your sources list.  This is recommended by the Automatix Web site.  You do not have to uninstall any of the apps, or codecs installed by Automatix, however.

2.  Update Edgy by going into System--->Administration--->Update Manager, (do not click on the update to 7.04 button yet!)  Run and install updates.

2.a   (this may not hapen to you)  If notified by Ubuntu update manager of a System 76 driver update, install it and then reboot.

3.  Update System 76 driver (yes do it again,)r by going into System--->Administration--->System 76 Driver.  After installation, reboot the system.  This will restore the upgrade button to the Update Manager.

4.  Upgrade to 7.01 by going to System--->Administration--->Update Manager and click on the button labled Upgrade to 7.04 (or something to that effect.)  Be sure you want to do this because once you start there is no option to cancel it.  On a 5 mbps internet connection it took about one hour and 25 minutes to download the upgrade and another 35 minutes to install.

5.  If necessary, put a CD into the optical drive if your system freezes intermittantly, (this will only be needed for a short time.)

6.  Add System 76 repositories to the sources list by going to System--->Administration--->Software Sources.  Click on the "Third-Party Software" tab and check "http://planet76.com/repositories/ ./"  Then click close.

7.  Download System 76 Driver again,  System--->Administration--->System 76 Driver.  When complete, reboot again.

8.  Pray, not absolutely necessary, but it made my upgrade experience more serine.   ;) 

9.  Remove the cd from drive and you should be good to go.

After following these steps, all functions worked.  My third party/restricted/proprietary apps all worked.  I still had full functionality (playing DVD's, MP3's, Accelerated 3D graphics ect.)  At several points during the install my Darter froze up hard.  I did a forced shut down several times by holding down the power button for about 15 seconds.  After about a 30 second pause I restarted the system and was able to continue without any ill effects.  I hope that this will help others.  There may be other ways to do this successfully with fewer steps, but this did work for me.  I do not know if this would apply to any other system 76 computers, however, since both the Darter and the Gazelle Value had the same problems with the upgrade initially, this might work for that computer as well.  Carl, Thomas, any comments?

Joe

---

### Post by thomasaaron on 2007-05-03
The hard freez-ups concern me.
We've had a few other complaints about it.

I'm going to pass it on to the programmer.

Glad everything came together, though.


If anybody else has problems with the driver, can you send the details to support(at)system76.com so I can start figuring out the fix...

Best,
Tom

---

### Post by jml on 2007-05-03
Thanks for responding, Tom.  Do you need any more information from me about the upgrade?

Joe

---

### Post by thomasaaron on 2007-05-03
I don't think so, yet.
I forwarded this post to the programmer, so he may get back with you...

Best,
Tom

---


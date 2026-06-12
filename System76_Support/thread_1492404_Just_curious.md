---
title: "Just curious"
date: 2010-05-24
forum: System76 Support
---

### Post by MG37221 on 2010-05-24
I hope I'm not wasting space but Update Manager included new System76 drivers.  Anybody know what these do?  Reboot to enable or reload drivers to activate?

Thanks in advance,
MG

---

### Post by MG37221 on 2010-05-24
Don't know what was in the newer drivers but a reboot (due to a brief power outage) was successful (in doing what I've no idea).

Therefore, thanks anyway.

---

### Post by robtg on 2010-05-24
I was wondering the same thing, so I clicked on the Install Drivers tab and then the Install button and rebooted.  Not sure if it was necessary but no ill effects (Panp5).

Rob

---

### Post by thomasaaron on 2010-05-25
The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager.

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Downloads folder.

Once it has downloaded, double-click the icon in your Downloads folder and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by robtg on 2010-05-25
Tom:  Thanks.  Not to beat this to death though...if the system76 driver itself is updated via Update Manager, is there any need to invoke the Install Drivers function after the update?  Apologies up-front if I'm being dense about this.


Rob

---

### Post by thomasaaron on 2010-05-26
No, not a problem. Good questions.

It's good policy to always keep your System76 Driver updated to the newest version. And when a new version comes down the pike, you should run it.

If there are no fixes in it for your machine, nothing will change. If there are fixes, you will benefit from them. 

In other words, running the driver will not hurt your system or add anything to it you don't need.

Does that help?

---

### Post by MG37221 on 2010-05-26
> **thomasaaron said:**
> No, not a problem. Good questions.

It's good policy to always keep your System76 Driver updated to the newest version. And when a new version comes down the pike, you should run it.

If there are no fixes in it for your machine, nothing will change. If there are fixes, you will benefit from them. 

In other words, running the driver will not hurt your system or add anything to it you don't need.

Does that help?

Sort of.  Do you actually "run" the driver or just reboot for it to take effect?

---

### Post by isantop on 2010-05-26
You will need to "run" it (Open it, click on the "Install Drivers" tab, then click install).

After this, you may need a reboot. (Everyone should anyway, just to be sure.)

---

### Post by re1d on 2010-05-28
> **MG37221 said:**
> Sort of.  Do you actually "run" the driver or just reboot for it to take effect?

Good question! Because I got the update last night and (dullard that I am) didn't run it, just downloaded all the updates and rebooted. So I haven't actually benefited from the driver update until I run it. I'll do that tonight.

Thanks for the good question and for clearing up the procedure for me.

It pays to haunt the forum!

---

### Post by riseringseeker on 2010-05-29
> **thomasaaron said:**
> No, not a problem. Good questions.

It's good policy to always keep your System76 Driver updated to the newest version. And when a new version comes down the pike, you should run it.

If there are no fixes in it for your machine, nothing will change. If there are fixes, you will benefit from them. 

In other words, running the driver will not hurt your system or add anything to it you don't need.

Does that help?

Just thought I would add that if someone is running a Meerkat Ion, you will not be **able** to install the System76 driver, nor is it needed, everything works without it on that system.

Thanks, Tom for the quick reply on that while updating a friends Meerkat yesterday.  Maybe you can mention to the keeper of the knowledge pages to make that tidbit of info easy (easier?) to find.

---

### Post by re1d on 2010-05-29
Small point - it hasn't been a problem, but makes me curious about something else involved in updating System76 drivers: Why does it take so long? It took me about half an hour the first time, and when I did it last night, about the same. Nothing seems to be happening with the drive or the network, except the status bar goes back and forth busily. And after a looong time it says it's done. Neither time did I see it finish, so there may have been a burst of activity at the end. Is it waiting for input over the Internet or something? :confused:

I couldn't see any differences afterward (was hoping for the driver update that would cure my splash screen!) so I guess there was nothing in it for my Pangolin this time. Or nothing earth-shaking, anyway! But it seemed to go OK.

---

### Post by robtg on 2010-05-30
Thanks Tom.  That clears it up.

Rob

---


---
title: "HP ProBook 4535s"
date: 2013-09-27
forum: Ubuntu, Linux and OS Chat
---

### Post by jim_smith2 on 2013-09-27
First of all, I've been on board for several years with various distros, including but not limited to Ubuntu.  

My wife has had nothing but trouble with her Win7 HP Probook 4535s.  Running slow, lockups, various ailments.

I took it for a day while she was at work and backed up everything she might conceivably need. I HOPE!

Took a fresh cd with 12.04.2 iso and tried an install. It hung at the Ubuntu with dots splash screen.

Took a fresh cd with 12.04.3 iso with the same results.

Looked around my office and found my original 12.04.1 iso and tried that.  It installed, but on reboot gave the purple screen of death with a mouse pointer in the middle of the screen.

Hmmmm  researched for several hours and discovered that a lot of folks had the same problem, with assorted "solutions" and workarounds.

Thought for a little while, and remembered that 10.04 was an excellent, laptop friendly version.

Could not find my old CD or iso, so downloaded one from the archives.  Thanks to whomever keeps the old versions around for the older and finicky hardware.

Installed 10.04 without a hiccup.  even put the cairo-dock on board for her...

Then I got to thinking... It is offering to upgrade all the way from 10.04 to 12.04.3  ... I wonder...

So I bit the bullet and hit the upgrade link.  It progressed nicely and about 1.5 hours later,
presto, changeo, I had 12.04.3 up and running like a top.

Not only that, but 10.04 for some unknown reason, defaulted my wireless to the off position, and pushing the button had zero effect. It worked fine with a cat 5 cable hooked up, but refused to do wireless no matter how I pounded the wireless button with the amber rather than white light on.  The amber means wireless off, white means wireless on.

After the reboot after the upgrade to 12.04.3, the white lite was on.  Hurray!   Now my sweet wife can get back on her laptop after work.

Anyone have any thoughts about the path I had to take to get this distro working on the HP Probook 4535s?  I'm just glad I was persistent!

Best Regards,
Jim

---

### Post by stalkingwolf on 2013-09-27
I just updated the os on a friends compaq nc8000.  I put mint 13 on it to replace the zorin 5.1.  installed with no problem. In fact she got a bonus, now the internal wireless works flawlessly.

I use Mint 13 on all my systems and on those i maintain.

---

### Post by tgalati4 on 2013-09-27
Without the log files, it's difficult to know what happened.  Perhaps the wireless driver tried to load with the 12.04.x installs and failed and/or locked up. With 10.04, you got a clean install with wired connectivity.  It's also possible that you got all of the updates for 12.04.3 through wired connection and that may have fixed some things.  After rebooting, the new updates (including any wireless module updates) would be running, so now your wireless works as expected.  

Installation has always been a hassle and your research on that model HP laptop confirmed such hassles.

You have more persistance than most for such an installation.

Let us see how your wife likes it.  I would like to see her reaction.

---

### Post by cariboo on 2013-09-27
You probably could have completed the install the first time, if you had used the nomodeset boot option when booting from the CD.

---


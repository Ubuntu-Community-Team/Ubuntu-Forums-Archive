---
title: "2 day on-line UDS 5-6 March 2013"
date: 2013-02-28
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-02-28
A new idea. Have a 2 day UDS on-line every three months. [http://uds.ubuntu.com/](http://uds.ubuntu.com/) A preliminary to going rolling release, was my first thought. And I have seen this [http://www.omgubuntu.co.uk/2013/02/ubuntu-to-discuss-rolling-release-move-at-next-weeks-uds](http://www.omgubuntu.co.uk/2013/02/ubuntu-to-discuss-rolling-release-move-at-next-weeks-uds) which links to this 
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-February/036537.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-February/036537.html)

> 
In the meantime, with Ubuntu Touch, the Phone, the Tablet, and convergence of these device experiences with the Desktop, we are in the process of inventing what is essentially a next generation Ubuntu. There will be lots of new code written and code integrated from new sources to accomplish this. The 13.04 Desktop would not have any of this new code, and therefore will be "old" before it is even released.> 
More clearly, I think we should: * Stop making interim releases. * Keep doing daily quality and keep improving our daily quality. * Take a monthly snapshot of the development release, which we support only until the next snapshot[COLOR=#222222][FONT=Verdana]This should be an interesting discussion for the people of Ubuntu+1 to follow. 

I found the blue print for the discussion. [https://blueprints.launchpad.net/ubuntu/+spec/release-r-monthly-snapshots](https://blueprints.launchpad.net/ubuntu/+spec/release-r-monthly-snapshots)
[/FONT][/COLOR][FONT=Verdana]As regards the changes to the forum - I just have to say it. Oh, such a lot of orange. Where are my sunglasses? [/FONT]:)  [COLOR=#222222][FONT=Verdana]Regards.[/FONT][/COLOR]

---

### Post by ventrical on 2013-02-28
Thanks Graham.

btw .. i just left my message about the *orange* here:

[http://ubuntuforums.org/showthread.php?t=2120972&p=12534836#post12534836](http://ubuntuforums.org/showthread.php?t=2120972&p=12534836#post12534836)

realy.. ouch!

---

### Post by philinux on 2013-02-28
Also a rolling release proposal from VP.

[http://www.iloveubuntu.net/canonicals-vice-president-engineering-rick-spencer-officially-proposes-adoption-rolling-release](http://www.iloveubuntu.net/canonicals-vice-president-engineering-rick-spencer-officially-proposes-adoption-rolling-release)

---

### Post by ventrical on 2013-02-28
"Ubuntu will continue to maintain its stability, security and  reliability, including in the rolling release model, due to the daily  efforts on creating **daily quality** (as a clear example,  one can immediately observe the solid state of Raring Ringtail, release  that, although a development version, is fast, stable and reliable)."

This is absolutely beyond the pale.  Where does the VP get his information from? I knew this would happen and I believe it is largely due to cadence testing.

 The Intel video drivers are in tatters (as are the ATi drivers on hybrid systems) and ccsm is in again , and out again , and in again like a yo-yo. Most  all of the iso-s and dailys have this incessant flickering while booting all across the video graphics brands.Gnome System monitor has been butchered (among how many other bugs reported here) and he calls  this "stable and reliable" ? I would think it would be better be coined a rude awakening and future shock and ironically Ubuntu's stability will eventually suffer.

  If this then be the case then the days of us beta testers will be numbered or greatly diminished as will be older and legacy/hybrid systems.

regards,
ventrical

edit: actually it was working rather stable a week or so ago. So I eat crow today.

---

### Post by grahammechanical on 2013-02-28
I have found in a general sense that since 12.04 the development branch has been stable enough to use daily. But as we know it is not without problems. And I expect there will be more problems when they sneak in all that new code that they are talking about. Someone has to test that code in the real world.

Some months ago I made some suggestions to Nick. One of which was that they should stick to an ISO image that has been tested as working and not make a new one available for download until that new image has been tested by Community Volunteer testers. If this monthly snapshot was the only ISO image available for download and it was tested by Community Volunteer testers before it is put up for download, then I would go along with that and be more willing then I am at present to test the image.

I also suggested that upstream code should not be uploaded to the updates channel until it was tested by Community Volunteer testers, perhaps through a testing branch of Ubuntu that was available to those in a testing program. I see upstream code as having a big risk to breaking a rolling release Ubuntu. Once upstream code breaks Ubuntu, then bang goes stability as happened during Quantal with the kernel, Xserver and Nvidia drivers all breaking stuff at the same time. If the rolling release Ubuntu is that testing Ubuntu, then they will need testers to use it daily and to test out bug fixes.

Another point that comes in my mind with all this is that it might suit Ubuntu devs to go rolling release but what about those devs who work on the Ubuntu flavours. They may need even greater help testing those flavours. I think the term rolling release is a distraction. Testing release/branch is better, in my opinion.

Regards.

---


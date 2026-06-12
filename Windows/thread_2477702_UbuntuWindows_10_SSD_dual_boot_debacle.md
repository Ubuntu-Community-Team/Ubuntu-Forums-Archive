---
title: "Ubuntu/Windows 10 SSD dual boot debacle"
date: 2022-08-03
forum: Windows
---

### Post by skoles on 2022-08-03
It has been 2 years ago since I had this crazy idea about dual booting both Windows 10 and Ubuntu. I started with windows 10 and added Ubuntu to my DELL Inspiron 3670 with a 250GB SSD.

Its been working quite well until Windows 10 developed an eating disorder. Im sure many will tell me this was a bad idea and could forsee this coming. Windows chewed through the remaining 30 GB just sitting there. I have done everything possible to shed apps and space. Moved ALL documents over to my secondary 2 TB HD drive. Windows had 150GB on the SSD. 26GB for system and reserved and 118GB for applications and features. I have 3.5 GB left for Windows. I shut off the WIFI when booted in Windows until I figure what to do otherwise it will continue to gorge itself with more updates.

the Ubuntu partition has plenty of space left.

I am considering options at this point:

...Give Windows more space and Ubuntu less ? This doesnt sound like a wise idea at this point. Windows will probably just chew through the rest of it in short order.

....Is it possible to install a bigger SSD with minimal issues ? I suppose this is wishful thnking. I really like the fast SSD ! Works nicely.

Adding additional SATA drives ? Not overly familiar with this approach. Any advice would be oool.

Forgot about Windows altogether ? I really still rely on it with some software

I am on Ubuntu 20.04.04 at the moment. I have certain ham radio apps that need updating but requires an Ubuntu upgrade with one software package but BREAKS another due to the Unbuntu upgrade. Im kind of stuck in the unsupported software desert too here. At some point this will work itself out I guess. Hoy !

Thoughts ? Any advice would be helpful

I am holding off on the adult beverages for now ;-)

....

---

### Post by TheFu on 2022-08-04
Can't throw ideas out for most of the stuff you mention, but ....

I use lxd containers when different software packages need very different OSes/software stacks.  This keeps those dependencies self-contained.  I didn't always do that.  At 1 point, I had nextcloud and wallabag in the same virtual machine because they were both php/mysql webapps.  As you can guess, over time those 2 projects software stacks diverged.  About 18 months ago, I created an lxd container for wallabag and migrated my data over.  I'd planned to move the nextcloud webapp into a new LXD container, but never got around to it.  

Today, I'm using a similar idea for my backups.  When 20.04 was released, the backup software moved from python2 ---> python3 which broke the network serialization. They are incompatible, but most of my systems are still running 18.04 server (python2) and need backups for that.  Initially, I ported the python2 version of the backup software to 20.04 and that has been working, but my port isn't ideal.  The better answer is to use a linux container for the backup server with the OS release I need.  These Ubuntu releases for containers are less than 1G, so while not exactly "lite", they aren't totally bloated like a VM or physical Ubuntu install (8G-40G).

As for dual booting. I stopped doing that over a decade ago.  I put Windows into a VM and boot that VM for an hour or so about once every 2 weeks to do the 2 things I still need Windows to accomplish.  Since 2008, I've been on a concerted effort to remove all my Windows dependencies, without resorting to cloudy internet apps.  Last fall, the main reason for having Windows booted daily was replaced with a Linux tool. In some ways it is better than the Windows tool (commercial), but in a few ways it is less great. I sleep much better however knowing that some MSFT patch won't screw up my Linux systems.

Since we are each a little different, our needs will be different.  Make a list of software that you still need Windows to run.  Then every 6 months do an exhaustive search for replacements.  When a possible replacement for my 3rd-to-last software package became available, I contacted the developer through github and clearly asked for a new feature to support one of my workflows with the tool that was missing.  About a month later, in the next release, it was there.  It wasn't great, but it worked.  For other reasons, that software broke and I couldn't use it a few months later - he switched to snap packages and didn't get all the dependencies included.  The solution was that I needed to be running a newer version of Kubuntu, which wasn't gonna happen.  About 8 months later, 4 other tools that did the same sort of stuff became available. I tried them all, but found the one I've been using the last 18 months now. It has been improved in meaningful ways over this time, while remaining true to the base goals which I loved.  

I hope something similar happens with your software needs.

You ask:
> ....Is it possible to install a bigger SSD with minimal issues ? I suppose this is wishful thnking. I really like the fast SSD ! Works nicely.
The only valid answer is, "it depends."  Sometimes things like that just work and it seems like a foolish waste of time to have been worried at all.  Other times, there are driver issues or firmware problems with the newer SSD.  I don't know any certain way to know before trying it
OTOH, if you don't have backups that can be restored, this is the perfect time to create those AND test them restoring into the newer, larger, SSD.  If that doesn't work, then you need a better backup solution.  My backup and restore solution doesn't care about the underlying storage. Restores start with a minimal Ubuntu xx.yy install, then I start restoring from the backups.  I can swap storage completely. I can change the file system completely. I can switch from BIOS boot to UEFI boot.  I can add or remove LUKS encryption.  All this is a restore-time choice.  Also, my restores can be into completely different hardware. I've gone from a Core i7 to a Ryzen 5 CPU.   BTW, that migration was for a VM server and from a spinning HDD into an SSD.'

It is possible?  Yes, but your situation is different from everyone else's and results cannot be guaranteed.

---

### Post by skoles on 2022-08-05
So I see someone or something thinks I misspelled Windows but my misspelling was certainly intentional. Seems more appropriate at times.  Frogs Hair ? In any event.

> **TheFu said:**
> Can't throw ideas out for most of the stuff you mention, but ....

I use lxd containers when different software packages need very different OSes/software stacks.  This keeps those dependencies self-contained.  I didn't always do that.  At 1 point, I had nextcloud and wallabag in the same virtual machine because they were both php/mysql webapps.  As you can guess, over time those 2 projects software stacks diverged.  About 18 months ago, I created an lxd container for wallabag and migrated my data over.  I'd planned to move the nextcloud webapp into a new LXD container, but never got around to it.  

>>>>>>>>>>>>Interesting concept. I will delve into this further when I need to review next steps for my next Ubuntu upgrade.

Today, I'm using a similar idea for my backups.  When 20.04 was released, the backup software moved from python2 ---> python3 which broke the network serialization. They are incompatible, but most of my systems are still running 18.04 server (python2) and need backups for that.  Initially, I ported the python2 version of the backup software to 20.04 and that has been working, but my port isn't ideal.  The better answer is to use a linux container for the backup server with the OS release I need.  These Ubuntu releases for containers are less than 1G, so while not exactly "lite", they aren't totally bloated like a VM or physical Ubuntu install (8G-40G).

As for dual booting. I stopped doing that over a decade ago.  I put Windows into a VM and boot that VM for an hour or so about once every 2 weeks to do the 2 things I still need Windows to accomplish.  Since 2008, I've been on a concerted effort to remove all my Windows dependencies, without resorting to cloudy internet apps.  Last fall, the main reason for having Windows booted daily was replaced with a Linux tool. In some ways it is better than the Windows tool (commercial), but in a few ways it is less great. I sleep much better however knowing that some MSFT patch won't screw up my Linux systems.

Since we are each a little different, our needs will be different.  Make a list of software that you still need Windows to run.  Then every 6 months do an exhaustive search for replacements.  When a possible replacement for my 3rd-to-last software package became available, I contacted the developer through github and clearly asked for a new feature to support one of my workflows with the tool that was missing.  About a month later, in the next release, it was there.  It wasn't great, but it worked.  For other reasons, that software broke and I couldn't use it a few months later - he switched to snap packages and didn't get all the dependencies included.  The solution was that I needed to be running a newer version of Kubuntu, which wasn't gonna happen.  About 8 months later, 4 other tools that did the same sort of stuff became available. I tried them all, but found the one I've been using the last 18 months now. It has been improved in meaningful ways over this time, while remaining true to the base goals which I loved.  

I hope something similar happens with your software needs.

You ask:

The only valid answer is, "it depends."  Sometimes things like that just work and it seems like a foolish waste of time to have been worried at all.  Other times, there are driver issues or firmware problems with the newer SSD.  I don't know any certain way to know before trying it
OTOH, if you don't have backups that can be restored, this is the perfect time to create those AND test them restoring into the newer, larger, SSD.  If that doesn't work, then you need a better backup solution.  My backup and restore solution doesn't care about the underlying storage. Restores start with a minimal Ubuntu xx.yy install, then I start restoring from the backups.  I can swap storage completely. I can change the file system completely. I can switch from BIOS boot to UEFI boot.  I can add or remove LUKS encryption.  All this is a restore-time choice.  Also, my restores can be into completely different hardware. I've gone from a Core i7 to a Ryzen 5 CPU.   BTW, that migration was for a VM server and from a spinning HDD into an SSD.'

It is possible?  Yes, but your situation is different from everyone else's and results cannot be guaranteed.

>>>>>>It appears this "fix" will not occur overnight so I will continue to research the topic of upgrading the SSD.

Overall, I think you remind me of one important item that I need to address first and foremost. Backups ! I have lost a few drives over the years and was able to recover important stuff. I thinks its time to invest in a stable backup drive bank of some sort. 

Thank you for your thoughts :-)

---

### Post by QIII on 2022-08-05
@skoles

What is important about the spelling of Windows is that we do not appreciate "clever" misspellings like that.

Please see the links in my signature, taking particular note under the heading of "Trolling, Attacks and Flaming" of the text

> Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.

The only opinion about propriety of such misspellings that matters is that of the Forums Staff, which exercises editorial control of the content here.

---

### Post by skoles on 2022-08-06
Thoroughly understood and noted for all future posts !

> **QIII said:**
> @skoles

What is important about the spelling of Windows is that we do not appreciate "clever" misspellings like that.

Please see the links in my signature, taking particular note under the heading of "Trolling, Attacks and Flaming" of the text



The only opinion about propriety of such misspellings that matters is that of the Forums Staff, which exercises editorial control of the content here.

---


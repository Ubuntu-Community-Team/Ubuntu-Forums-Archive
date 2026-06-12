---
title: "[SOLVED] [IDEA] Option on Desktop CD for Ubiquity sans live session"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
An easily visible option (as one of the boot options, along with *Start or install Ubuntu*, *Start Ubuntu in safe graphics mode*, and *Check CD for defects*) to install Ubuntu without using a live session.

**Rationale:**
It happens all too many times--a new user comes to the forums asking why the Desktop CD freezes when she's trying to install Ubuntu. The other users ask how much RAM she has, and it's 256 MB or 128 MB. It's quite obvious that with that much RAM the live session cannot be running at the same time as Ubiquity *and* have both run without freezing.

So this new user gets the bad news that she just spent two and a half hours downloading the wrong CD. She really wants the Alternate CD, which isn't even available off the main Ubuntu download page any more. That's a lot more downloading.

If only she could go straight to the pretty installer without having a live Ubuntu running in the background, that'd save her the trouble of digging around the Ubuntu website, finding the Alternate CD, waiting for it to download, reburning another CD, figuring out what boot option she wants (you'd be surprised to see how many people do an OEM install or a server install), and then being surprised to see a text-based graphical installer.

**Scope and Use Cases:**
Uh, see above scenario. Basically, it's for users with enough RAM to run Ubuntu, enough RAM to install Ubuntu, but not enough RAM to install Ubuntu and run a live session in the background simultaneously.

**Implementation Plan:**
Another boot option: *Install Ubuntu directly*

It goes straight to Ubiquity and will be a lot like Fedora's Anaconda or Mandriva's installer (not sure if it has a name).

**Disclaimer**:
The option to use Ubiquity without the live session may already exist as some crazy workaround, but if that's the case, it should still be made into an easily-selectable option, not something that requires a Google search and a really long HowTo.

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-sans-live-session](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-sans-live-session)

---

### Post by =0verlord= on 2007-04-15
Man, I love this idea.  This is also great for when the user already *knows* they want to install ubuntu and don't want to spend the time booting it up from CD.

---

### Post by .t. on 2007-04-15
In these cases, Ubiquity would not function. The alternate CD, which provides for this use case, installs packages rather than copy over the currently running system, which Ubiquity does. We don't particularly want to reinvent the Debian Installer, which is present on the alternate CD, but without doing so there is simply not enough space on the CD for packages and a Live CD environment; as the two environments are completely different, for more than the simple use of packages vs a live session. Some daily desktop CD images don't even fit into the 700MiB of a CD as it is, and expanding to more than one CD or a DVD isn't really an option.

Update: ```
toby@leopard:~/src/ubiquity/d-i$ ls
build-manifest  lists                manifest      update-changelog
check-manifest  Makefile             README        update-control
get-sources     make-keyboard-names  sources.list
```Not that much d-i is actually used in  Ubiquity.

---

### Post by 23meg on 2007-04-15
Ubiquity depends on X and GTK (among other things) to run, and it would be a huge effort to strip it from its dependency on those; it would be the near equivalent of writing a whole new frontend to [d-i]("http://www.debian.org/devel/debian-installer/"). A more feasible solution may be to set up a barebones X environment with the bare essentials Ubiquity needs, but I'm not sure that would be guaranteed to save enough RAM to get Ubiquity running. I'll investigate this further.

---

### Post by =0verlord= on 2007-04-15
> **.t. said:**
> In these cases, Ubiquity would not function. The alternate CD, which provides for this use case, installs packages rather than copy over the currently running system, which Ubiquity does. We don't particularly want to reinvent the Debian Installer, which is present on the alternate CD, but without doing so there is simply not enough space on the CD for packages and a Live CD environment; as the two environments are completely different, for more than the simple use of packages vs a live session. Some daily desktop CD images don't even fit into the 700MiB of a CD as it is, and expanding to more than one CD or a DVD isn't really an option.

Ah, I was totally unaware of the alt CD and it took me a couple minutes of clicking around to actually find the page with it.  Let me change my support to making the release page a little easier to find.  Thanks for the info!

---

### Post by PriceChild on 2007-04-15
We're asking a few people on the feasibility of a "barebones" X session with only ubiquity loaded.

I like the idea a lot, I also think something needs to be done about the lack of a link to the alternate cd on [www.ubuntu.com](www.ubuntu.com)

---

### Post by =0verlord= on 2007-04-15
> **PriceChild said:**
> We're asking a few people on the feasibility of a "barebones" X session with only ubiquity loaded.

I like the idea a lot, I also think something needs to be done about the lack of a link to the alternate cd on [www.ubuntu.com](www.ubuntu.com)


I'd be happy with a link on the download page instead of download->mirror page->release page.

---

### Post by PriceChild on 2007-04-15
Yeah I just meant that I cannot see any link for the alternate cd on [www.ubuntu.com](www.ubuntu.com), subpages or not.

---

### Post by =0verlord= on 2007-04-15
Ah, yeah, completely in agreement - whose area would a change like this fall under?

---

### Post by .t. on 2007-04-15
The ubuntu-website product on Launchpad.

---

### Post by PriceChild on 2007-04-15
link to file a bug: [https://bugs.launchpad.net/ubuntu-website/+filebug](https://bugs.launchpad.net/ubuntu-website/+filebug)

To get this fixed please take the time to file a bug about this problem. :) Ask if you have any questions about it but it should be self explanatory.

---

### Post by =0verlord= on 2007-04-15
Looks like there are already several there, I linked a confirmed one here - [https://bugs.launchpad.net/ubuntu-website/+bug/94895](https://bugs.launchpad.net/ubuntu-website/+bug/94895)

---

### Post by justynbutler on 2007-04-15
+1 my support for making the alternative CD easy to find on the website. I had a (competent computer/Linux/Internet user) friend totally unable to locate it, which embarassed me somewhat because I'd been saying how easy Ubuntu was to install and use.

Of course if it is somehow possible to have the text-based Debain installer from the alt CD, or the features of it as aysiu suggests, on the main Ubuntu CD instead then that gets +100 from me.

Justyn

---

### Post by =0verlord= on 2007-04-15
I would support having the non-ubiquity installer on the live cd boot, but I doubt this will happen.

---

### Post by PriceChild on 2007-04-15
> **=0verlord= said:**
> I would support having the non-ubiquity installer on the live cd boot, but I doubt this will happen.This will not happen as both methods install in different ways and there is no-where near enough space for both. What we have been wondering about is the standard ubiquity in a stripped down X session.

---

### Post by reacocard on 2007-04-30
This is a great idea! Also for those who want the text-mode on the cd too, well, why not? Just create an ncurses frontend to Ubiquity and you'd be set. Doing that might actually be easier (better?) than trying to create a separate xsession for Ubiquity. You could even have it automatically drop to the text-mode installer if X won't start nicely.

---

### Post by r3m0t on 2007-05-01
> **reacocard said:**
> This is a great idea! Also for those who want the text-mode on the cd too, well, why not? Just create an ncurses frontend to Ubiquity and you'd be set. Doing that might actually be easier (better?) than trying to create a separate xsession for Ubiquity. You could even have it automatically drop to the text-mode installer if X won't start nicely.
Because the whole point of the text installer on the Alternative CD is that it has some more capabilities compared to Ubiquity. Seems to me that putting a text frontend to the "desktop" CD would be no use - if X doesn't work on that computer, why would they want to install the desktop version of Ubuntu?

Not to mention confusing people with a text frontend to Ubiquity *and* a text frontend to debian-installer, which would be subtly different. :-)

---

### Post by 23meg on 2007-05-01
aysiu, we're taking the liberty to integrate this idea [along with some others]("https://wiki.ubuntu.com/ForumAmbassadors/GutsyCommunityIdeas") into a big composite Ubiquity enhancements spec to be discussed at UDS. If you have an objection, please let me know.

---

### Post by gmatht on 2007-05-04
Here is some data on how much memory is used by different processes during an install of Ubuntu 7.04 from LiveCD:

```
PID USER      PR  NI  VIRT  SHR  RES S %CPU %MEM    TIME+  COMMAND
 7886 root      16   0 52280  11m  28m S  0.0 10.7   0:24.10 ubiquity
 7561 ubuntu    15   0 78840  13m  17m S  0.7  6.6   0:04.09 nautilus
 7816 ubuntu    15   0 59444  11m  17m S  5.5  6.5   0:07.67 gnome-terminal
 7559 ubuntu    15   0 42888  12m  16m S  2.3  6.3   0:07.83 gnome-panel
15895 root      18   0 19628 3076  15m R  6.5  5.9   2:18.95 install.py
 6898 root      16   0 31108 6664  14m R  9.5  5.6   2:21.12 Xorg
15892 root      18   0 17812 1892  14m S  0.0  5.6   0:02.69 debconf-communi
 7634 ubuntu    15   0 35324  10m  12m S  0.0  4.9   0:02.79 nm-applet
 7583 ubuntu    21   0 35584 9276  11m S  0.0  4.5   0:01.17 update-notifier
 7658 ubuntu    19   0 36448 9012  11m S  0.0  4.4   0:00.58 mixer_applet2
 7032 ubuntu    19   0 30428 8596  11m S  0.0  4.2   0:12.03 x-session-manag
 7557 ubuntu    15   0 16960 7280 9864 S  1.6  3.7   0:07.81 metacity
```

I believe that the kernel needs less than 10MB of ram. RES indicates the amount of memory actually resident, which should be a good measure of how much memory is needed without slowing down too much. Metacity might be nice, but I don't think that that Ubiquity strictly needs a window manager.

For the kernel, ubiquity, Xorg we would then need 10MB+28MB+14MB or 52MB of ram. Even with Metacity this comes to only 62MB of ram. Memory will be needed for other bits and pieces, but it may be possible to do an install  with as little as 64MB of Ram. For machines with less than 64MB of ram even Xubuntu really isn't suitable.

---

### Post by gmatht on 2007-05-04
The following links are also relevant to using Ubiquity on low memory machines:
[LIST]
[*] [Using Video Ram for swap (linuxnews.pl)]("http://hedera.linuxnews.pl/_news/2002/09/03/_long/1445.html").
[*] [Compressed Memory (wiki.ubuntu.com)]("https://wiki.ubuntu.com/CompressedMemory").
[*] [Using a spare USB drive for swap, which now makes sense, even for extended use (dansdata.com)]("http://dansdata.com/flashswap.htm").
[/LIST]

---

### Post by 23meg on 2007-05-04
This idea was incorporated into [the ubiquity-forumideas]("https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-forumideas") blueprint, which is still being worked on. Please consult the forum ambassadors team before making changes.

---

### Post by madman91 on 2007-05-04
Excellent idea!!!
I remember the problems I had trying to install Edgy because my video card driver wouldn't work.


+1

---

### Post by TwistedLincoln on 2007-05-05
> **gmatht said:**
> 
For the kernel, ubiquity, Xorg we would then need 10MB+28MB+14MB or 52MB of ram. Even with Metacity this comes to only 62MB of ram. Memory will be needed for other bits and pieces, but it may be possible to do an install  with as little as 64MB of Ram. For machines with less than 64MB of ram even Xubuntu really isn't suitable.

Well the problem with a situation like that is that your installed system would consist of almost nothing.  Remember that Ubiquity just copies the current live environment to the target system.  So if you strip down the running live cd, you also cripple the install.

Seems to me it would just be easier to have the Live CD check for the amount of Ram on the system and if it is under 256mb, give an error message stating that you need at least 256mb to use this CD...  Then provide instructions on where the user can get the alternate CD instead.

It would be nice to have all options on one CD, but if that's not possible, we should at least make it easy for people to figure out why things won't work.  When I first tried to install Edgy using the Desktop CD on a system with 128mb, I figured it would just take much longer to load up, but it would eventually work.  I assumed this because I had done an install on the same machine with the alternate cd before, an the installed system works fine.  So surely the LiveCD would be the same, right?  Wrong.  As we all know, this doesn't work.  But the new user with no patience who doesn't want to do any research isn't going to know this, so they'll just assume Ubuntu is slow and bloated.  

Having the LiveCD check for available RAM *before* loading X would be a great way to make sure new users don't give up on Ubuntu too easily.

---

### Post by Cows on 2007-06-04
Well yes this is a very good idea and I thought about why they haven't added this feature so it will completely be a 1 cd installer. The Desktop CD got everything and the other cd's are just step downs. Now if you open the isolinux.cfg you will see boot parameters. Why don't you just copy the alternative specific and server specific parameters and organize it respectebly in the isolinux.cfg of the Desktop CD before burning? That way you can boot up gui, boot up alternative and boot up a server install.

---

### Post by brim4brim on 2007-06-05
Its fine having two versions of Ubuntu CD to download depending on the type of installer needed but it needs to be clear which one to choose.

It should be explained how to choose and how to find out how much ram a user has in Windows so they know if they have the requirements to run the graphical installer or not.

---

### Post by ronacc on 2007-06-05
> **brim4brim said:**
> Its fine having two versions of Ubuntu CD to download depending on the type of installer needed but it needs to be clear which one to choose.

It should be explained how to choose and how to find out how much ram a user has in Windows so they know if they have the requirements to run the graphical installer or not.

I just went to  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  and checked a couple of the notrh american mirrors ( I'm in th US ) and had no trouble FINDING the alternate install CD , as you note though the explaination as to who needs to use it could better.

Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
creating pre-configured OEM systems; 
setting up automated deployments; 
upgrading from older installations without network access; 
LVM and/or RAID partitioning; 
installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

In the event that you encounter a bug using the alternate installer, please file a bug on the debian-installer package. 

There are two images available, each for a different type of computer:

should read 

Alternate install CD   USE THIS ONE IF YOU HAVE 256 MB RAM OR LESS   or   ( caps intended)

blah blah blah

and mabye an explaination on how to find how much ram you have , remember we are dealing with people who are used to having their hands held.

---

### Post by Cows on 2007-06-05
Yes it can be more clearer. But what do you think about my idea posted above? Do you think it can be possible?

---

### Post by reacocard on 2007-06-05
> **Cows said:**
> Yes it can be more clearer. But what do you think about my idea posted above? Do you think it can be possible?

Not in the way you mention. The graphical and text install disks store the data differently (because of the 'live' functionality), but there's no reason you couldn't add a text installer to the livecd that uses the graphical installer's backend.

---

### Post by Cows on 2007-06-07
That would be good then. Does the alternative cd bring the GUI backend but disabled? Maybe I can enable it on a Alternative CD, but if it doesn't work I can try to enable it on the Desktop CD.

---

### Post by Cows on 2007-06-12
Well nobody responded. I'm going to download the Desktop CD and add some parameters to see if I can get a text mode install going with the Ubuntu.

---

### Post by tormod on 2007-09-27
> Disclaimer:
The option to use Ubiquity without the live session may already exist as some crazy workaround, but if that's the case, it should still be made into an easily-selectable option, not something that requires a Google search and a really long HowTo.

Here's the crazy workaround, with the long HowTo:

[LIST=1]
[*] Boot the Desktop up as usual
[*] Log out from the slow, graphical session
[*] At the gdm menu, choose Failsafe Terminal
[*] Log in as "ubuntu" with empty password
[*] Type "ubiquity" in the terminal window
[*] Enjoy Ubiquity on your low-ram computer :)
[/LIST]

It works great with Feisty and Gutsy on my 240MB laptop. I think it should be very doable to integrate this in the Desktop CD. If we put the option in at the boot prompt, we can even avoid steps 1-5 above. Just make a hook in the gdm session file. Adds a kB to the CD.

PS. Why is this spec draft not on the wiki?

---

### Post by tormod on 2007-09-27
Did I say 1 kB? It's more like 150 bytes, uncompressed :) I have attached the patch for /etc/gdm/Xsession

To change the boot menu, isolinux.cfg also needs a one-line patch, which adds the "lowraminstall" boot option.

---

### Post by Lord Illidan on 2007-09-27
Don't shout at me if this is stupid, but can Anaconda be used in place of Ubiquity for this installation option?

---

### Post by tormod on 2007-10-05
Just to follow up on this, it has now been implemented in Gutsy with the "only-ubiquity" boot option. There will be no menu item for Gutsy, but maybe for Hardy...

ubiquity (1.6.2) gutsy; urgency=low

 [ Evan Dandrea ]
 * Add 'only-ubiquity' option to kernel cmdline to run ubiquity in a
   minimal session.  Thanks Tormod Volden (LP: #148341).

---

### Post by Cows on 2008-03-26
Well then mission accomplished :).

---

### Post by reacocard on 2008-03-26
There is indeed a boot option for ubiquity-only on the hardy cd menu.

---

### Post by aysiu on 2008-03-26
Since this has been solved, I'm going to close the thread. Great job, Ubuntu devs!

---


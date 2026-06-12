---
title: "My disastrous experience with Ubuntu 14.04 LTS Trusty Thar."
date: 2015-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by deragon on 2015-05-10
Greetings,

I want to share disastrous experience with Ubuntu 14.04 LTS Trusty Thar.  You can read about it on my blog at:  [http://www.deragon.info/ubuntu14.04.html](http://www.deragon.info/ubuntu14.04.html) 

I wish to start a healthy discussion about the situation, in the hope that it will stir some constructive feedback.  Do not hesitate to correct me if any information is wrong or if you have more details, workarounds and solutions about the issues I experience.

Best regards,
Hans Deragon

---

### Post by Frogs Hair on 2015-05-10
Moved to ***Ubuntu, Linux and OS Chat ***

---

### Post by QIII on 2015-05-10
Here are some really great ideas for constructive criticism:

Get a launchpad account and take part:  [https://launchpad.net/](https://launchpad.net/)

Report and light fires under bugs, like this:  [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

Share with the Forum volunteers who test development versions:  [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

Spend some time on the Forums and work toward becoming an Ubuntu Member:  [https://wiki.ubuntu.com/Forums/Membership](https://wiki.ubuntu.com/Forums/Membership)

Get on this mailing list:  [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss)  (There are more lists [here]("https://lists.ubuntu.com/").)

This entire Forum is full of criticism: some constructive, some not so much.  If you want to start a healthy dialogue, you may have arrived too late.  There are many already in progress.  They cover the gamut of things you have pointed out in your blog.  Unfortunately, Canonical employees -- in particular the developers -- are rarely here.  The Forums are certainly a good place to discuss among ourselves as users.  But for any criticism here to be constructive, the message needs to be delivered to the right destination at the right time.  Criticism after a release is not as effective as taking part in testing.  Taking part in the community is likely to be the most effective form of constructive criticism.

Please remember that Canonical is a very small company.  They have precious little time and resources.  They aren't Microsoft with tens of thousands of employees and seemingly limitless resources.  But they do have us.  We see the bugs.  We report the bugs.  We get the developers' attention via Launchpad.

Better to help than hurl barbs from the sidelines.

---

### Post by Mike_Walsh on 2015-05-11
I hate to say it, but from the sound of things, **you** want a free version of Windows.

Ubuntu (or, come to that, any other Linux distro) is **not** that. You have to understand, they all have one thing in common. They are free **alternatives** to Windows (or Macs, if they take your fancy). And, as QIII has just pointed out, most of the outfits developing Linux distros do not have the resources available to MicroSoft.

I suspect they treat their employees a wee bit better, though.....


Regards,

Mike.

---

### Post by ian-weisser on 2015-05-11
The [Ubuntu QA Team]("https://wiki.ubuntu.com/QATeam") would certainly welcome the OP to join as a Tester or a Bug Triager.
Really. Not joking.

The OP clearly has skills, years of Ubuntu experience, and interest. Make some lemonade out that bad experience!

---

### Post by user1397 on 2015-05-13
Geez, glancing through your blog post it seems that you got particularly unlucky.  Perhaps your hardware is just extremely not ubuntu 14.04 friendly?

I can relate to seeing some bugs here and there, and that bug report window appearing probably more often than I would care, but nothing major.  Overall I found 14.04 to be extremely stable on my laptop.  I'm currently using kubuntu 15.04 which uses the extremely new plasma 5 and I've seen even less bugs than on unity (so far), which is crazy to say the least.

---

### Post by Geoffrey_Arndt on 2015-05-13
When using 14.04,  I do occasionally get the annoying "apport" crash bug notice . . . doesn't seem to affect things negatively though it takes a couple tries to dismiss the window (and bug reporter crashes upon send attempt).

But, that's the ONLY issue that I've noticed, unlike the OP, network works flawlessly, nautilus works perfectly, apps run just fine (no crashes to speak of).    I don't especially care for VLC as it is a giant memory hog lately, but there are a lot of media alternatives.

It makes a big difference also, if you obtain your PC with Ubuntu, _in the same way you obtain a Windows PC_ . . . . you buy it with the OS pre-installed, and unless you're a gamer, choosing an all Intel system (wireless, graphics) prevents most problems.

Just my two-cents (been running Linux desktop since may of 2003.) and don't miss the major ANNOYING in your face crapware and updates from 1/2 dozen or more vendors all wanting to update OS or devices.

---

### Post by user1397 on 2015-05-13
indeed, if i have to compare my overall linux experience with my windows experience, i'll take linux any day.  neither is perfect, but linux is FAR less annoying

---

### Post by deragon on 2015-05-13
Greetings gentlemen,

OP here.  We share the same goal, hoping for Linux to take a good share of the desktop and consumer market.

Some of you report that the problem might be the hardware.  Lenovo (W510 laptop) is pretty much Linux friendly and many of the bugs I report are not related to hardware.  Sure, I have a NVIDIA card with the proprietary drivers (because I want performance; kids are gamers), and an Intel card with the open source drivers would probably eliminate some of the bugs, but Bluetooth and MTP broken, read-only USB, double login, network manager failing after resume and all the others are, AFAIK, not hardware related.

I do suspect that many graphic problems are related to NVIDIA's proprietary drivers.  However, maybe the drivers have been corrected since, but Canonical fails to upgrade them in the repository.  I will see if I can upgrade it use the xorg-edgers ppa.

And yes, I am reporting bugs and help out, all within my limits.  But as my blog states, I cannot recommend Ubuntu at this point as a general purpose computer where one can simply connect a phone, speaker or car via Bluetooth, download pictures using MTP, and simply having a stable system.  It does work if you use it on a desktop, never suspend, never use Bluetooth or MTP, never play AAA games, etc...

Canonical's aim is to make it consumer friendly, but my experience shows that they have still a long way to go.  Yes, I know, Canonical is small.  I state in my blog that they have to make revenues and the desktop is not their priority at the moment.

What I am doing is reporting my struggle like thousands went through.  The majority decided enough is enough, and moved to another platform.  I know at least four persons who used to run Ubuntu/Linux that moved to Mac.  I used to have colleagues running Linux, but now I am alone.  I read about this a lot on the web.  It is important to report what many experienced to understand why they left Linux.  While many say that Ubuntu is buggy and unstable, they fail to go into details.  I report all the bugs I suffer and try to link them to actual bug reports, in details.

My most pressing issues are the frequent desktop crashes after resume (started only a few weeks ago), double login and networking failure, which all prevent my family to login and use the laptop.  The odd things is all these pressings issues never occurred in 12.04.  There has been some regression since.

The good news is that regarding the networking issue, I found the following today:  [http://askubuntu.com/questions/452826/wireless-networking-not-working-after-resume-in-ubuntu-14-04](http://askubuntu.com/questions/452826/wireless-networking-not-working-after-resume-in-ubuntu-14-04)  The user provides a solution.  Nothing that a consumer could do, but at least I can.

Final thoughts:  if the Bluetooth and MTP stack are broken, how does the Ubuntu phone work?  If they have working Bluetooth and MTP stacks, why aren't they ported to the desktop?  Can the Bluetooth and MTP stacks from Android be ported or are there licensing issues?

Best regards,
Hans Deragon

---

### Post by ian-weisser on 2015-05-13
> **deragon said:**
> if the Bluetooth and MTP stack are broken, how does the Ubuntu phone work?

Well, on my 15.04 desktop, bluetooth and MTP *aren't* broken. For me they work well and reliably (two reported bugs notwithstanding), better and more reliably than 14.10.

My experience is that when a developer or tester discovers a bug, they don't ignore it.
Perhaps no developer or tester experienced the bug(s) that affect you.

---

### Post by user1397 on 2015-05-14
That's what I'm not understanding about the OP's concerns, are his problems completely isolated to one particular piece of hardware (his pc)?  Or has he had the same experience across multiple devices? and across multiple versions of ubuntu?

There are definitely thousands if not millions of ubuntu users out there completely satisfied with their ubuntu experience and most ubuntu people report their systems as overall stable.  The thing I don't think you understand OP is that this is an exception, not the rule.

---

### Post by deragon on 2015-05-19
Greetings,

You are numerous that have pointed out that most of my problems are probably caused by unsupported hardware.

While that might be for some bugs, I doubt that the majority are hardware related.  Desktop icons not showing, [Network Manager not waking up after a resume]("http://www.deragon.info/pages/bug-networkmanager-notworkingafterresumefromsleep.html"), [sound card not detected anymore]("http://www.deragon.info/pages/sound-card-not-detected-anymore.html"), ["Device not managed" showing up over 50 times]("http://www.deragon.info/pages/bug-nm-applet-repeat-error.html"), [black borders around Windows]("http://www.deragon.info/pages/bug-compiz-blackborders.html")?

While my Lenovo W510 laptop was not pre-installed with Ubuntu, [ it was certified for 12.04]("http://www.ubuntu.com/certification/hardware/201101-6974"). Granted, certification was not done for 14.04, but I doubt there was that much regression on the hardware side.  The only hardware side regression I can think of is the brightness control.  It used to work on the same laptop with 12.04.  Anyhow, I would be happy if you guys can prove me wrong and demonstrate that most of my bugs are hardware related.

[Bluetooth]("http://www.deragon.info/pages/bug-bluetooth-transferbroken.html") is one mystery for me.  Many of you report that it works greats.  Maybe I have faulty hardware.  I have a hard time to figure out how to debug this.

If you have suggestions on how to solve some problems I have, do not hesitate to make your suggestions; I am willing to try different solutions.

Best regards and many thanks for your replies.
Hans Deragon

---

### Post by germanix on 2015-06-04
Sorry to hear about your problems. I have Ubuntu 14.04 with the Unity desktop installed on both my Lenovo Thinkpad X230, as well as my Thinkpad 11e. I have not had even one issue on either of these machines. Everything just works. Actualy Lenovo is known for being Linux friendly, so I find it quite surprising that you have these problems. Maybe there are some issues with some of the hardware components in your machine or maybe your copy of 14.04 did not download correctly (MD5Sum)? Wish I could be more helpfull, sorry about that, hope you do find the solution though.

---

### Post by deragon on 2015-06-06
Thank you for responding Germanix.  Yes, Lenovo is generally user friendly.  My Lenovo W510 was after all, certified for 12.04.

On my [blog]("http://www.deragon.info/ubuntu14.04.html"), for many of the bugs I have, I point to the relevant ticket manager (launchpad, bugzilla, etc...).  On many of the bugs reports there is more than one user suffering from it.  In most cases, they are reproducible.

If there was a md5sum error, it would be for one package.  I got so many problems across so many sub systems that it cannot be caused by this.  Beside, most problems are shared by others, so we cannot have all md5sum errors.  Same reasoning goes for hardware problems.

I suspect that those using Ubuntu 14.04 who have no issues are not using their computers like me.  If you do not make use of Bluetooth file transfer, you do not suffer from the problem.  If you do not need powerful graphics and use Intel instead, you save yourselves some hassle.  You have a desktop instead of a laptop?  Not using Wifi saves you the troubles of network connectivity and suspending.

I have a colleague that swore that Ubuntu 14.04 was rock solid, until I made him read my blog.  All the bugs I was suffering where not part of his working flow as he was running it in a VM.  I was using it as a power user, using the desktop environment to the max with a laptop that requires power saving, Wifi, smartphone connectivity, etc...  He mostly started up terminals.  Not the same usage and not the same 'stress' on the system.

My blog is to point out that there are some serious bugs that prevents Ubuntu to be taken seriously by consumers.  Hopefully, since Ubuntu phones are in the hands of consumers, quality assurance must have been bumped higher for these devices.  When the merging will arrive between Ubuntu desktop and Ubuntu touch, the QA will, hopefully, follow.

But until then, I cannot recommend Ubuntu.  In my household, I might have to go back to Windows soon to at least have a stable platform that just works, after 12 years of being a Linux exclusive household.  Breaks my heart, but at the end, I need something that just works.

---

### Post by Copper Bezel on 2015-06-06
Honestly, I'm not sure how commonly Bluetooth file transfer really is used, even for phones. Obviously, Bluetooth peripherals work swimmingly in Ubuntu - I'd be lost without a Bluetooth headset or earpiece. I've never had any real issues with MTP, but I don't use it extensively, either - phones and tablets are computers, not peripherals, and I've never felt the need to physically plug in a device that's already on the network short of, say, cases I'm installing a ROM.

I have encountered the WiFi problem on suspend and resume on a previous machine. The fix was to add lines to the sleep and power scripts to simply remove and re-add the Atheros driver involved. 

And I've always stuck to Intel graphics, because the cards are simply supported. With anyone else, to the chipset manufacturer, you're a second-class consumer for using Linux and the driver is a second-class citizen in the system for being proprietary, so you're screwed twice over. I don't want to deal with that mess.

You're exactly right that not everyone's use case is the same, and I do think that is part of your problem here. If you need Windows for this machine and your use case, there's no need for any hand-wringing - just use the OS that works for you. More commonly it's enduser software that's the issue - gaming and a lot of professional areas, particularly graphics and visual artwork, are hamstrung on Linux for the fact that AAA shops or Adobe and so on don't support Linux. If you're deeply into one of those use cases, using Linux would be silly.

The set of bugs or missing features you encountered doesn't really say anything about Ubuntu as an OS; Android, for instance, is much more reliable and predictable than Windows; does that mean that Windows isn't ready for prime time?

---

### Post by Klaster on 2015-06-09
Hey germanix,
how is the wifi on your x230 with 14.04? I'm still running 12.04 but I think about upgrading, partially since my wifi is reaaally slow or not connecting to networks at all. Heard that was a common problem with the iwlwifi driver but I couldn't resolve the problem so far. Have you had bad xp with this in earlier versions?

---


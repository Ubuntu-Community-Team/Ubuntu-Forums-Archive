---
title: "Sorry, have to can Ubuntu - back to Windows"
date: 2009-11-17
forum: Testimonials &amp; Experiences
---

### Post by Jethro_uk on 2009-11-17
Been happily using Ubuntu for nearly 2 years now. Was inspired after deciding NO to Vista. Managed to set up my main home machine to dual-boot XP and Ubuntu. My wife uses Windows, and I soldier on with Ubuntu.

Have upgraded twice. 7.04->8.10, which caused 2 weeks worth of grief, but managed in the end,

Then 8.10-9.04. And there it has to stop. Why ? Because I cannot get the mouse to work properly. And a fresh 9.04 install on a spare machine shows the same problem. I have found many many many posts from other people (most here), but no simple answer. I have run all updates ... nada.


here's the most exact trail for this bug. I too am using a wireless mouse, so there's a hint there, but no fix ...


[https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905]("https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905")

In the end, the machine is practically useless. Once the mouse plays up I have to restart X. I could live without the soundcard. With lo-res graphics even. But I simply can't live without the mouse. In my two years, I have discovered the joys of a dual-boot machine, as booting into XP verifies there is no hardware issue ... it's definitely a drivers thing.

So until a stable fixed version comes out, I'm having to stop using Ubuntu. I've gone as far as my techie skills can take me. It is so frustrating, as I really really wanted it to work.

Sad day ...

p.s. my file/download server has remained rock stable with 8.10, and since it's not a client machine there's no push to upgrade. So there will still be a linux box in the house.

---

### Post by emigrant on 2009-11-17
after reading a lots of threads i have come to a conclusion:
not to upgrade from the distro.

---

### Post by madverb on 2009-11-17
Does this occur with every mouse you attach to it? Pretty weird if it does. I'd say you are doing something very wrong.
What is the mouse?

---

### Post by Jethro_uk on 2009-11-17
> **madverb said:**
> Does this occur with every mouse you attach to it? Pretty weird if it does. I'd say you are doing something very wrong.
What is the mouse?

I guess this isn't the place for a technical discussion ... however I so want this fixed.

My setup is a wireless mouse & keyboard (labtec). These work 100% under XP, so we can eliminate that. I tried a USB corded mouse, and had the same results. If you read the thread I referenced, you'll see suggestions about Compiz, Xorg, which I have followed to no avail (as have other posters). As luck had it my main machine was a 9.04 upgrade, but my sons (he loves Compiz, desk cubes and the like !) is a completely fresh install. (We both have wireless mice). So it's not an upgrade thing.

The worst thing is it seems semi-intermittent. Sometimes I can go an hour without it happening. Other times it cuts in straightaway.

It seems to be totally application independent, as it's happened when Firefix runs. Or nautilus. Or the system log viewer ....

As I said, I'm very sad ....

---

### Post by Jethro_uk on 2009-11-17
> **emigrant said:**
> after reading a lots of threads i have come to a conclusion:
not to upgrade from the distro.

But the completely fresh install does it too, so in this instance, you can't blame the upgrade ....

---

### Post by megamania on 2009-11-17
Did you try disabling desktop-effects (compiz)?

---

### Post by Jethro_uk on 2009-11-17
> **megamania said:**
> Did you try disabling desktop-effects (compiz)?

Yes. No joy.

---

### Post by Jazzy_Jeff on 2009-11-17
That is really weird. I have used a wireless mouse and a usb mouse without any problems. I only use Logitech though. I hope someone can find what ever the issue is and fix it. It sounds like a USB driver issue. That is if the wireless mouse plugs into your USB port like mine does.

---

### Post by Jethro_uk on 2009-11-17
> **Jazzy_Jeff said:**
> That is really weird. I have used a wireless mouse and a usb mouse without any problems. I only use Logitech though. I hope someone can find what ever the issue is and fix it. It sounds like a USB driver issue. That is if the wireless mouse plugs into your USB port like mine does.

it does. It's clearly a subtle one ... I'm not a Linux developer, but i have discovered that 8.10->9.04 mouse handling went from the X server to HAL, which might explain it.

I'll happily post whatever logfiles people would need to see. I do want it to work, honest.

---

### Post by Jazzy_Jeff on 2009-11-17
Did your mouse come with a PS/2 adapter? If so have you tried using that to see if it works?

---

### Post by Jethro_uk on 2009-11-17
> **Jazzy_Jeff said:**
> Did your mouse come with a PS/2 adapter? If so have you tried using that to see if it works?

No, just a USB adapter. I'd have to borrow/buy a PS2 mouse ...

---

### Post by Jazzy_Jeff on 2009-11-17
I was just wondering. Some USB mice come with the PS/2 adapter.

---

### Post by megamania on 2009-11-17
Honestly, I'd never switch operating systems (either Linux to Windows or the other way round) just because of a non-working mouse - I'd just change mouse.

I think I'd find the hassle of reinstalling everything unbearable, and I couldn't stand being forced to use an operating system I like less just because that way the mouse works.

Of course, that's just *my personal* behaviour in similar situations and I'm not judging or underestimating your frustration.

By the way, your problem is one of those which are likely to be fixed with a new kernel release.

---

### Post by running_rabbit07 on 2009-11-17
You say you are using Jaunty? Try Karmic. Or, as someone said earlier, go back to Hardy or Intrepid.

---

### Post by cmay on 2009-11-17
try set the usb mouse into a other port. the ports next to he networks would be the two ports most likely to work i think. it is on my machine constructed so that the two single usb ports always works fine whereas the next four wont always work for usb devices. fr some reason.

---

### Post by solwic on 2009-11-17
Why not just let the OP leave?  He/she wants to go back to Windows, then let us all wish him/her the best of luck and move on.  

JMO....

---

### Post by running_rabbit07 on 2009-11-17
> **Jethro_uk said:**
> But the completely fresh install does it too, so in this instance, you can't blame the upgrade ....

I am wondering if you tried the LiveCD with your machine before upgrading. I would really consider trying Karmic or going back to Intrepid.

---

### Post by Jethro_uk on 2009-11-17
> **cmay said:**
> try set the usb mouse into a other port. the ports next to he networks would be the two ports most likely to work i think. it is on my machine constructed so that the two single usb ports always works fine whereas the next four wont always work for usb devices. fr some reason.

This was one of the first things I did - same result. Again, XP works fine with the machine exactly as it is. It is undoubtably *something* to do with software.

---

### Post by Jethro_uk on 2009-11-17
> **running_rabbit07 said:**
> I am wondering if you tried the LiveCD with your machine before upgrading. I would really consider trying Karmic or going back to Intrepid.

I did (it's the CD I burned and used to install on the other machine). It *seemed* to work fine. But as I (and others in the thread I referenced) have discovered, it's an intermittent fault ... so it may not have reared it's head in the 10 minutes I messed around for a look & feel ...

---

### Post by Jethro_uk on 2009-11-17
> **solwic said:**
> Why not just let the OP leave?  He/she wants to go back to Windows, then let us all wish him/her the best of luck and move on.  

JMO....

I don't *want* to go back to windows. I like Ubuntu, and really want to use it. However at the moment I can't. And I am stuck as to getting a fix.

---

### Post by Jethro_uk on 2009-11-17
> **megamania said:**
> Honestly, I'd never switch operating systems (either Linux to Windows or the other way round) just because of a non-working mouse - I'd just change mouse.

I think I'd find the hassle of reinstalling everything unbearable, and I couldn't stand being forced to use an operating system I like less just because that way the mouse works.

Of course, that's just *my personal* behaviour in similar situations and I'm not judging or underestimating your frustration.

By the way, your problem is one of those which are likely to be fixed with a new kernel release.

The affected machine is the "house" PC. Which means other people have to use it (hence the XP partition), and for various reasons, they are totally happy with a wireless mouse this shape. True I *could* buy another mouse, and swap it over every time I boot into Ubuntu.

Don't forget I have a dual-boot machine. It's no more hassle for me to use windows than it is Ubuntu. At the end of the day, 95% of my time is spent surfing, downloading, emailing, and burning movies. All of which are just as easy from Windows ....

---

### Post by megamania on 2009-11-17
> **solwic said:**
> Why not just let the OP leave?  He/she wants to go back to Windows, then let us all wish him/her the best of luck and move on.  

All of us probably assumed that since he posted in a public forum, he was looking for feedback and suggestions.

---

### Post by Jethro_uk on 2009-11-17
> **megamania said:**
> All of us probably assumed that since he posted in a public forum, he was looking for feedback and suggestions.

I've already posted in the appropriate forums, and had no joy ... this post was meant to be a marker for other people, to help them make their minds up, and to leave a line in the sand for future generations ;)

---

### Post by solwic on 2009-11-17
> **megamania said:**
> All of us probably assumed that since he posted in a public forum, he was looking for feedback and suggestions.

In the Testimonials and Experiences forum?  Seriously?

But hey, it's a (mostly) free forum, so help away.  :)

@OP:  Good luck, whatever you decide.  :)

---

### Post by Jethro_uk on 2009-11-17
> **running_rabbit07 said:**
> You say you are using Jaunty? Try Karmic. Or, as someone said earlier, go back to Hardy or Intrepid.

Can you roll back an upgrade ? Going to KK is not really an option ... I upgraded to 8.10 the week it came out last year and had loads of issues with nVidia drivers and audio drivers.

That's why I waited 6 months before 9.04 ... give it a chance to settle down.

---

### Post by Jethro_uk on 2009-11-17
> **running_rabbit07 said:**
> I am wondering if you tried the LiveCD with your machine before upgrading. I would really consider trying Karmic or going back to Intrepid.

MAybe I'll try and boot the LiveCD, and see if that works OK over a few hours. If it does, I'll have a look at the FDI file it generates and try and use that to update the mouse settings in HAL ....

---

### Post by HappyFeet on 2009-11-17
> **megamania said:**
> Honestly, I'd never switch operating systems (either Linux to Windows or the other way round) just because of a non-working mouse - I'd just change mouse.


Let's weigh the options. New mouse vs. windows. New mouse wins every time.

---

### Post by HappyFeet on 2009-11-17
> **Jethro_uk said:**
> True I *could* buy another mouse, and swap it over every time I boot into Ubuntu.



No need to swap. You can have 2 mice plugged in at the same time.

---

### Post by dBuster on 2009-11-17
> **Jethro_uk said:**
> MAybe I'll try and boot the LiveCD, and see if that works OK over a few hours. If it does, I'll have a look at the FDI file it generates and try and use that to update the mouse settings in HAL ....

I was going to recommend that.  I for one dislike anything windows so I am purely a Linux user.  I too with a new laptop had issues but was able to work around the issues through deep searches of this forum as well as help from others.  Working with the livecd along with an alternate install disc I was able to get Jaunty working without any issues.  The normal install disc gave me a headache and once I switched to the alternate it was a piece of cake.  Could there be some underlying issue with how the mouse moves on screen due to a video driver?  have you examined all your hardware items in searches to see if there are any quirks about say the video card drivers, the motherboard on board drivers and so forth?

To me I can not justify putting my hard earned money into someone elses pocket for an OS that is known for being buggy and virus prone only to cause me to shell out more for some other application to try and secure the OS which in my opinion should be secure before going public...

---

### Post by running_rabbit07 on 2009-11-17
> **Jethro_uk said:**
> Can you roll back an upgrade ? Going to KK is not really an option ... I upgraded to 8.10 the week it came out last year and had loads of issues with nVidia drivers and audio drivers.

That's why I waited 6 months before 9.04 ... give it a chance to settle down.

That is completely understandable. Though I am testing Lucid, I have Jaunty on my production machine and my daughter's system.

---

### Post by Juan Largo on 2009-11-17
@Jethro_uk

Instead of switching back to Windows, have you considered switching to another Linux distro?  Although Ubuntu is a fine distro, it is not the easiest one to install or to maintain IMO.

If you are not adverse to trying KDE, I would strongly recommend trying SimplyMEPIS, which is also a Debian-based distro.  MEPIS is currently at version 8.0 using KDE 3.5, but the developer (Warren Woodford) will be rolling out a newer version using KDE 4.3 in the near future.

Here's the link to the MEPIS web site:  [https://www.mepis.org/](https://www.mepis.org/)

MEPIS is *not* "cutting edge," but if you want a distro that is very stable and easy to maintain, has excellent hardware recognition, and is easy to install, MEPIS fits the bill.  MEPIS is *not* a rolling release; Warren ties his new releases to Debian's cycle, so you can expect a new version to come out every 12-18 months or so.  Warren generally maintains support for the latest two versions, which could span up to three years.

There are Community Repositories that are actively maintained by the MEPIS community, and these have more recent and up-to-date packages than the standard repositories.  The MEPIS forums are the friendliest ones I've found anywhere, and you can get help almost intantly from people who are very patient and knowledgeable.  Check it out here:

[http://mepislovers.org/forums/index.php](http://mepislovers.org/forums/index.php)

---

### Post by Eagles18 on 2009-11-17
> **emigrant said:**
> after reading a lots of threads i have come to a conclusion:
not to upgrade from the distro.
I upgraded from the distro and am having no problems.

---

### Post by Tamlynmac on 2009-11-18
> solwic
In the Testimonials and Experiences forum?  Seriously?
 But hey, it's a (mostly) free forum, so help away.  :)

We have help sections in these forum? Really? :)

Humor aside, I do hope the OP finds a solution to their problem or installs an OS that best meets their needs.

---

### Post by Dullstar on 2009-11-18
Then go back to 8.10 if it worked, or try a different distribution, such as Debian or Arch.

---

### Post by Zoot7 on 2009-11-18
@OP

You're a lot better off you stick with the LTS's if you want stability. Hardy (while getting a little long in the tooth) is pretty darn stable right about now.

Anyway, it's up to you, if Windows is the tool for the job that best suits you then use Windows! :)

---

### Post by GodLikeCreature on 2009-11-18
Even if a fresh install would not fix the problem, it would have saved you all that grief you mention, which is a big part of your frustration, I believe.

I would recommend to go back to the distro/version that worked for you, then give Karmic a try again within 2-3 months.

I think these strange issues will go away eventually.

---

### Post by solwic on 2009-11-18
> **tamlynmac said:**
> we have help sections in these forum? Really? :)

humor aside, i do hope the op finds a solution to their problem or installs an os that best meets their needs.

+1.

---

### Post by Jethro_uk on 2009-11-19
Never thought of the video card. I was using an nVidia with the proprietary driver - have switched to open source driver for now.

One last clue ... when the mouse locks up ... the "alt-tab" key combination also stops working. I only realised this today, when I used it when the machine was behaving itself, and it works. It think that is the worst frustration of this issue - not being able to use the keyboard to switch windows and save work ....

not sure what the other machines graphics card is ... it's onboard, but I'll check tomorrow ....

---

### Post by dBuster on 2009-11-19
With the nVidia driver, have you checked to see the compatibility with Karmic for the version you were using?  

I know with my Jaunty, the initial driver version I tried did not work correctly for me and I had to hunt down the current working driver and put it on a flash drive then load it from a low graphics boot.  Once I did that all cleared up for me.

Good luck and keep us posted if drivers for the nVidia was an issue.

---

### Post by dE_logics on 2009-11-20
How much can the opensource developers help you if the company making the hardware is Microsoft only?

It's their fault...they did not make a "next next finish" installer.

You can't blame the OS for this!

---

### Post by Jethro_uk on 2009-11-20
reverting video driver didn't work.

However a small clue appears to be that this behaviour appears connected to list boxes (NOT drop downs). when the mouse goes into one of them, it won't come out.

---

### Post by Jethro_uk on 2009-11-25
Hi guys,

thanks for all your support, suggestions and help. Looks like this bug is a longstanding one, and is buried in the XServer ...

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

I'm particularly interested in the fact that I can get it to happen from a LiveCD, as well as the fact that clearly not everyone using 9.10 is experiencing it. To me this suggests a specific Xserver configuration is causing it. So it *could* have a hardware component to it.

I'm hoping by the repeated and cross-posting that I can get a googlewhack going so that future victims of this bug can find these posts and connect the mouse problem to an Xserver problem, and provide enough information to developers to crack this bug.

By the way, I did upgrade to 9.10, which I like very much ... in my opinion 9.04->9.10 has been the biggest style change I've seen. I especially like the software centre.

---

### Post by Jethro_uk on 2009-12-02
After a while playing with this problem, I have got it down to be an annoyance, rather than a showstopper.

Not being a Linux guru, my opinions are of limited value, but I firmly believe this is an X-Server/XOrg problem. I've seen it happen under GNOME and KDE, and with all combinations of window managers, and decorators.

There appears to be a connection with ALT-TAB ... as soon as the mouse focus issue happens, you lose ALT-TAB.

Anyway, I have discovered that if I activate ALT-TAB as soon as I login, it seems to "protect" my system, and I don't seem to lose mouse focus.

I have also discovered, that CTL-ALT-D (show desktop) seems to recover mouse focus ... once all windows are minimised to the taskbar, then ALT-TAB seems to work again, and mouse focus is restored. Hopefully this workaround will prove useful to people, and can remove the need to logout/login again, or to restart the machine with the loss of data that implies.

---

### Post by Jethro_uk on 2009-12-23
Having lived with this problem for a few weeks now, I believe I can have a stab at suggesting what is going on, and the intermittent nature of the bug.

I *think* that when GDM starts (after I login), some process somewhere starts up, and creates a window. I have read various reports that it's possible to create a window which does not appear in the panel area. This window then steals focus. Because it's hidden, you can't switch to it to close it. From that point on, you're stiffed.

I've read a lot about the modified behaviour of the update manager/notifier, and I would like to propose this as the app which is killing mouse focus.

I'm researching ways to kill it so it never starts ...

---

### Post by legendb on 2009-12-23
After wandering away from linux after university I decided to try diving back in with ubuntu as I'd heard how great it was and I have been getting very frustrated with this mouse problem. I have 2 usb mice and a keyboard and I have seen similar behaviour. The log files don't seem to show anything strange at the moment of impact.

Both Mice hang and x server won't restart with ctrl+alt+bkspace (it will restart if mouse hasn't hung), keyboard works fine for a while but may also hang after the mouse. Keyboard also sometimes goes a bit weird of it's own accord and send a repeated key stroke hence I get ouput like MMMMMMMMMMMMM etc.

Anyway, I tried installing both 64 and 32 bit versions this didn't help. I tried installing SUSE but the mouse and keyboard didn't even make it past the partitioner on the installer.

So, after doing much searching and reading I might have it running ok, I just hope I haven't spoke to soon.

Anyway, I went to the bios and I had on chip USB support enabled and keyboard/drive enabled as well as mouse enabled. Leaving USB support enabled but switching off the other 2 usb features seems to resolved the situation. The only downside is I have to use a ps2 keyboard now as I dual boot and need to use a keyboard for selecting os boot in grub and also altering the bios.

---

### Post by J V on 2009-12-23
> **Jethro_uk said:**
> I'm researching ways to kill it so it never starts ...
If this turns out to be the problem, I'd like to offer the answer :)

Open your configuration editor (command gconf-editor) and navigate to apps > update-notifier and uncheck auto-launch, this not only fixes the mouse problem, but stops that annoying window from popping up... Without disabling updates... Don't know how it would affect alt+tab though, so it may go nowhere...

GJ for staying at it for so long, this would be quite near the end of *my* rope anyway... :)

---

### Post by Jethro_uk on 2009-12-23
> **J V said:**
> If this turns out to be the problem, I'd like to offer the answer :)

Open your configuration editor (command gconf-editor) and navigate to apps > update-notifier and uncheck auto-launch, this not only fixes the mouse problem, but stops that annoying window from popping up... Without disabling updates... Don't know how it would affect alt+tab though, so it may go nowhere...

GJ for staying at it for so long, this would be quite near the end of *my* rope anyway... :)

GJ ?

Anyway thanks for that. Change made, and testing underway. What made me suspect  this is the reports that GDM restart seems to cure the problem ... update notifier doesn't run the 2nd time.

---

### Post by J V on 2009-12-23
Right, well good luck with that! Fixing that stupid update window is one of the first things I do on a new install...

GJ = good job :)

Hope it works [-o<

Edit: if it does, be sure to say so on the main post so people looking for testimonials get the right idea :D

---

### Post by Dullstar on 2009-12-23
> **Jethro_uk said:**
> GJ ?

Anyway thanks for that. Change made, and testing underway. What made me suspect  this is the reports that GDM restart seems to cure the problem ... update notifier doesn't run the 2nd time.

If that doesn't help, I think logitech mice seem to work with Linux.  If you want to use Ubuntu instead of Windows, then a new mouse would be a small price to pay (and btw, you can have multiple mice plugged in at once -there is a prank that one can pull by having two plugged in at once...  anyways, I have two plugged into my own computer all the time)

---

### Post by twifirphoda on 2009-12-23
Somehow, the expletives don't seem to add to the thread - it'd probably be easier to get to the useful information without them...

---

### Post by juancarlospaco on 2009-12-23
Always try the development version if other options dont work...

---

### Post by Jethro_uk on 2010-01-19
Well loads of other folks have noticed the bug ... it's clearly a *very* deep rooted issue.

I logged into my upstairs machine (it's running 9.10, but I NX into it from Windows) and ... guess what ... a new bug ... now ctrl+left click doesn't work in nautilus.

I keep asking myself, how the hell did this release get near a door ?

Best tip I can offer is to install Webmin (which has seriously impressed me) and then administer the machine using a windows box ... luckily I just use it for 24/7 torrenting, and Vuze has a web-based GUI, so adding torrents etc is easy.

---


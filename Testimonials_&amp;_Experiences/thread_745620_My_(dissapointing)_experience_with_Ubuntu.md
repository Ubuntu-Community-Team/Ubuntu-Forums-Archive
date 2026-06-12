---
title: "My (dissapointing) experience with Ubuntu"
date: 2008-04-04
forum: Testimonials &amp; Experiences
---

### Post by belaj on 2008-04-04
Hello!

I recently upgraded my PC and upon installing Windows, I discovered that I could not activate it because I went over my activation limit. So I said screw it, I'm installing Ubuntu. I'm gonna try (again) to use Linux as my main OS. The difference here is that I had the intention to switch over for good and ditch Windows completely.

However...well just read on to see what were the major issues I encountered.


**- Multiple monitors support**

It just sucks. nVidia TwinView is a poor hack compared to its Windows version. I have a LCD (1280x1024), CRT (1024x768) and a TV. I set up TwinView using the LCD and CRT, TV was a separate X window. On the CRT, I lose the bottom 256 pixels unless I specify a panning domain (bleh). Gnome doesn't see the two logical screens and stretches the panels and the login screen across the two monitors.

I tried Xinerama and it's MUCH better. I actually get three screens and I can move the windows between monitors. But then Compiz doesn't work... And Gnome lacks features to take advantage of this configuration (like a Send To Next Screen keyboard shortcut, which KDE apparently has). Some apps remember their position (on which screen), some open on whichever screen the cursor is on. Some apps like OpenOffice show their splash screen on the second screen and the app window on the first screen :confused:

Also, rendering seems inconsistent. For example, the Mines game takes a full 3-4 seconds to render the playing field. OpenOffice is slightly unresponsive. Although I didn't investigate this issue, so the cause could be anything.

And yes, I know TwinView is not the fault of the community/developers, but it's still a big issue for me.


**- Hibernation**

Oh boy. When I was still going to the university, I used Ubuntu (Dapper/Feisty? I don't remember) on my laptop and I quickly learned that I shouldn't bother with hibernation. Now, with Gutsy, things have (somewhat) improved. Most of the time, I can hibernate my desktop and resume without problems. Sometimes, I resume apparently without any problems, but I get an error message saying "...failed to hibernate" :confused: Other times, I get no error message, but my mouse doesn't work. And just today, I resumed fine, but none of my displays initialized (black screens everywhere). Ctrl+Alt+Del, Alt+R worked and I could reboot. Guess I shouldn't bother (again)...


**- Evolution**

Importing my emails from Outlook Express took some work but it was painless. I had to import my contacts by hand though, I don't know if Outlook's export or Evolution's import screwed up. I added some appointments in the calendar, set the alarms and...nothing. For several days. Then I guess the planets got in the right alignment because the alarms started working.

Yesterday, I got two emails from HR people asking for my diplomas (I'm looking for a job). So I scan them (on a Windows PC as JPEGs), use "convert" (I don't remember from which package) to get PDFs, attach them in my emails and click send. Today, both persons replied saying they couldn't open the files. Hmm. I try the PDFs on the Windows PC with Acrobat and they work fine. I attach them again and send an email to my web-based account. What do I get? 1.dat and 2.dat, both unreadable of course.

That was the last straw. Needless to say, this was something important and may have hurt my chances at getting a job :mad:


**- Conclusion**

Total timespan : I don't know, 2-3 weeks, on and off. In the end, I'd rather go through the hassle of calling Microsoft to be able to reactivate Windows than continue fighting Ubuntu. I'm really disappointed with my experience. I knew I would have to make many sacrifices (gaming for one), but this is just too much. I always considered Linux to be "by programmers for programmers" and this continues to be true (for me at least). I still use Ubuntu at my part time job for Web development, but as a general purpose OS for my desktop, it just fails.

---

### Post by KhaaL on 2008-04-04
Have you tried hardy for setting up multiple monitors? Because I agree with you that the support for that is (was) sucky, but with hardy a tool is included to set up multiple monitors easily.

And regarding hibernation... I use it on my eeepc with no problems, but thats because the ACPI modules are avaible for it :)

Give hardy a spin and see if it works better with multiple monitor support for you, because those issues you've mentioned are honestly not beyond hope.


Good luck, and hope to see you again? ;)

---

### Post by Leetbumble on 2008-04-04
I feel your pain I really do. I have had problems in the past with other linux distros and hated the thought of going back to windows but at times had no choice. 

As far as the multiple monitors issue... screw all other tools. Nvidia has a tool which you download from their website with the driver for your card. you run it and it mods ur xorg.conf file. I have a 19inch non-widescreen and a 20inch widescreen and all i had to do was download these two items, run the app with the system being in text mod and when it restarted BOOM! dual monitors and I actually have wine for games and compzi-fusion running at full speed all the cool tricks and tweaks. 

For email... gmail is all i can say on that.

For hibernation... well im a geek and i try to never leave the keys, but in reality i dont have a need to hibernate i guess in the end just shut off the monitor or try "x-lock" if ur worried about security.

Goodluck either way.

---

### Post by hurtstotalktoyou on 2008-04-04
> **belaj said:**
> Hello!

I recently upgraded my PC and upon installing Windows, I discovered that I could not activate it because I went over my activation limit. So I said screw it, I'm installing Ubuntu. I'm gonna try (again) to use Linux as my main OS. The difference here is that I had the intention to switch over for good and ditch Windows completely.

I don't think I could ever do that.  I don't think most Windows "power users" (and it sounds to me like that's what you are) can ever switch over completely--not in the current state of the Linux software spread, anyway.

> However...well just read on to see what were the major issues I encountered.

**- Multiple monitors support**

It just sucks. nVidia TwinView is a poor hack compared to its Windows version. I have a LCD (1280x1024), CRT (1024x768) and a TV. I set up TwinView using the LCD and CRT, TV was a separate X window. On the CRT, I lose the bottom 256 pixels unless I specify a panning domain (bleh). Gnome doesn't see the two logical screens and stretches the panels and the login screen across the two monitors.

I tried Xinerama and it's MUCH better. I actually get three screens and I can move the windows between monitors. But then Compiz doesn't work... And Gnome lacks features to take advantage of this configuration (like a Send To Next Screen keyboard shortcut, which KDE apparently has). Some apps remember their position (on which screen), some open on whichever screen the cursor is on. Some apps like OpenOffice show their splash screen on the second screen and the app window on the first screen :confused:

Also, rendering seems inconsistent. For example, the Mines game takes a full 3-4 seconds to render the playing field. OpenOffice is slightly unresponsive. Although I didn't investigate this issue, so the cause could be anything.

And yes, I know TwinView is not the fault of the community/developers, but it's still a big issue for me.

In my experience TwinView is buggier on Windows than Ubuntu.  Then again, I run two different graphics cards (6200TC on WinXP, and FX5200 on Ubuntu).  Also, I only TwinView a single CRT and a TV, not three displays.  However, I feel your pain.  Sometimes certain features work much easier on Windows than Ubuntu.  However, even though it's a hassle, I can't imagine you not getting it to work if you spend a little time troubleshooting.

> **- Hibernation**

Oh boy. When I was still going to the university, I used Ubuntu (Dapper/Feisty? I don't remember) on my laptop and I quickly learned that I shouldn't bother with hibernation. Now, with Gutsy, things have (somewhat) improved. Most of the time, I can hibernate my desktop and resume without problems. Sometimes, I resume apparently without any problems, but I get an error message saying "...failed to hibernate" :confused: Other times, I get no error message, but my mouse doesn't work. And just today, I resumed fine, but none of my displays initialized (black screens everywhere). Ctrl+Alt+Del, Alt+R worked and I could reboot. Guess I shouldn't bother (again)...

That's weird.  I've never had that problem, either.  Then again, I run a desktop, so I rarely hibernate.

> **- Evolution**

Importing my emails from Outlook Express took some work but it was painless. I had to import my contacts by hand though, I don't know if Outlook's export or Evolution's import screwed up. I added some appointments in the calendar, set the alarms and...nothing. For several days. Then I guess the planets got in the right alignment because the alarms started working.

Yesterday, I got two emails from HR people asking for my diplomas (I'm looking for a job). So I scan them (on a Windows PC as JPEGs), use "convert" (I don't remember from which package) to get PDFs, attach them in my emails and click send. Today, both persons replied saying they couldn't open the files. Hmm. I try the PDFs on the Windows PC with Acrobat and they work fine. I attach them again and send an email to my web-based account. What do I get? 1.dat and 2.dat, both unreadable of course.

That was the last straw. Needless to say, this was something important and may have hurt my chances at getting a job :mad:

That certainly sounds frustrating.  I never use Outlook or Evolution, so I never experience problems like this.  I'm strictly a web-based mail guy.

> **- Conclusion**

Total timespan : I don't know, 2-3 weeks, on and off. In the end, I'd rather go through the hassle of calling Microsoft to be able to reactivate Windows than continue fighting Ubuntu. I'm really disappointed with my experience. I knew I would have to make many sacrifices (gaming for one), but this is just too much. I always considered Linux to be "by programmers for programmers" and this continues to be true (for me at least). I still use Ubuntu at my part time job for Web development, but as a general purpose OS for my desktop, it just fails.

If you expected learning a radically different operating system to be quicker and/or easier than a 6-minute phone call to Microsoft, well, I'm not sure what to tell you.  Anyway, it sounds like what's failing is the software for that operating system, not the OS itself.  If you don't like Evolution, why don't you see what else there is?

The cool thing about Ubuntu isn't that it's free, but that it's community-supported and has an entirely different selection of software.  I've never had an easier time encoding video than on Ubuntu.  I love the feel of the OS when browsing the internet.  As noted above, I really like the Linux version of TwinView, and so I watch a lot of movies by outputting through my video card to the TV.  Sure, I do like tinkering around with command-line computing.  Perhaps most of all, though, I absolutely love Hydrogen Audio, a drum sequencer, for which there is no comparable Windows alternative.

Ubuntu is tough to learn, especially for one so accustomed to Windows.  I'm not saying that you *should* stick with it, but only that if you do, you might feel differently about it once you learn how to deal with those unhappy quirks.  The big question is, are you interested enough to keep trying?

Whichever you choose, good luck!

---

### Post by stchman on 2008-04-04
> **belaj said:**
> Hello!

I recently upgraded my PC and upon installing Windows, I discovered that I could not activate it because I went over my activation limit. So I said screw it, I'm installing Ubuntu. I'm gonna try (again) to use Linux as my main OS. The difference here is that I had the intention to switch over for good and ditch Windows completely.

However...well just read on to see what were the major issues I encountered.


**- Multiple monitors support**

It just sucks. nVidia TwinView is a poor hack compared to its Windows version. I have a LCD (1280x1024), CRT (1024x768) and a TV. I set up TwinView using the LCD and CRT, TV was a separate X window. On the CRT, I lose the bottom 256 pixels unless I specify a panning domain (bleh). Gnome doesn't see the two logical screens and stretches the panels and the login screen across the two monitors.

I tried Xinerama and it's MUCH better. I actually get three screens and I can move the windows between monitors. But then Compiz doesn't work... And Gnome lacks features to take advantage of this configuration (like a Send To Next Screen keyboard shortcut, which KDE apparently has). Some apps remember their position (on which screen), some open on whichever screen the cursor is on. Some apps like OpenOffice show their splash screen on the second screen and the app window on the first screen :confused:

Also, rendering seems inconsistent. For example, the Mines game takes a full 3-4 seconds to render the playing field. OpenOffice is slightly unresponsive. Although I didn't investigate this issue, so the cause could be anything.

And yes, I know TwinView is not the fault of the community/developers, but it's still a big issue for me.


**- Hibernation**

Oh boy. When I was still going to the university, I used Ubuntu (Dapper/Feisty? I don't remember) on my laptop and I quickly learned that I shouldn't bother with hibernation. Now, with Gutsy, things have (somewhat) improved. Most of the time, I can hibernate my desktop and resume without problems. Sometimes, I resume apparently without any problems, but I get an error message saying "...failed to hibernate" :confused: Other times, I get no error message, but my mouse doesn't work. And just today, I resumed fine, but none of my displays initialized (black screens everywhere). Ctrl+Alt+Del, Alt+R worked and I could reboot. Guess I shouldn't bother (again)...


**- Evolution**

Importing my emails from Outlook Express took some work but it was painless. I had to import my contacts by hand though, I don't know if Outlook's export or Evolution's import screwed up. I added some appointments in the calendar, set the alarms and...nothing. For several days. Then I guess the planets got in the right alignment because the alarms started working.

Yesterday, I got two emails from HR people asking for my diplomas (I'm looking for a job). So I scan them (on a Windows PC as JPEGs), use "convert" (I don't remember from which package) to get PDFs, attach them in my emails and click send. Today, both persons replied saying they couldn't open the files. Hmm. I try the PDFs on the Windows PC with Acrobat and they work fine. I attach them again and send an email to my web-based account. What do I get? 1.dat and 2.dat, both unreadable of course.

That was the last straw. Needless to say, this was something important and may have hurt my chances at getting a job :mad:


**- Conclusion**

Total timespan : I don't know, 2-3 weeks, on and off. In the end, I'd rather go through the hassle of calling Microsoft to be able to reactivate Windows than continue fighting Ubuntu. I'm really disappointed with my experience. I knew I would have to make many sacrifices (gaming for one), but this is just too much. I always considered Linux to be "by programmers for programmers" and this continues to be true (for me at least). I still use Ubuntu at my part time job for Web development, but as a general purpose OS for my desktop, it just fails.

Multi monitors are not really needed when you have numerous workspaces.

Yes, suspend and hibernate do not work very well in Ubuntu.  There are some work arounds.

Blame M$ for their own proprietary mail format.  Thunderbird and Evolution use the same format so they work well.  Outlook Express is a security flawed mail client anyway so using it is a risk.  To get your email off OE install Thunderbird and TBird will import from OE.  After that you can get them into Ubuntu.

I have been using Ubuntu for over a year now and am very happy with it.  I only use XP for gaming, nothing else.  Heck, when I was on XP I used almost exclusively open source apps like Firefox, Thunderbird, Foxit, Notepad++, 7-Zip, Trillian, Irfanview, Infrarecorder, utorrent as they did not corrupt the system like the "professional" apps did.

I am sorry that your experience was bad, but for most the experience is pleasant.

---

### Post by Steve Angelidis on 2008-04-04
Its not relevant to my set up. So I haven't tried it. But check out the following: [http://howtoforge.com/howtos/linux/ubuntu]("http://howtoforge.com/howtos/linux/ubuntu")

Might be useful to you.

All aspects of Ubuntu work great for me except the hibernate. But booting and shutting down are so much faster than Vista was, that I don't mind. I just shut her down.

---

### Post by Hmarroqu on 2008-04-04
i less than three ubuntu

---

### Post by crjackson on 2008-04-04
> **belaj said:**
> Hello!

I recently upgraded my PC and upon installing Windows, I discovered that I could not activate it because I went over my activation limit. So I said screw it, I'm installing Ubuntu. I'm gonna try (again) to use Linux as my main OS. The difference here is that I had the intention to switch over for good and ditch Windows completely.

However...well just read on to see what were the major issues I encountered.


**- Multiple monitors support**

It just sucks. nVidia TwinView is a poor hack compared to its Windows version. I have a LCD (1280x1024), CRT (1024x768) and a TV. I set up TwinView using the LCD and CRT, TV was a separate X window. On the CRT, I lose the bottom 256 pixels unless I specify a panning domain (bleh). Gnome doesn't see the two logical screens and stretches the panels and the login screen across the two monitors.

I tried Xinerama and it's MUCH better. I actually get three screens and I can move the windows between monitors. But then Compiz doesn't work... And Gnome lacks features to take advantage of this configuration (like a Send To Next Screen keyboard shortcut, which KDE apparently has). Some apps remember their position (on which screen), some open on whichever screen the cursor is on. Some apps like OpenOffice show their splash screen on the second screen and the app window on the first screen :confused:

Also, rendering seems inconsistent. For example, the Mines game takes a full 3-4 seconds to render the playing field. OpenOffice is slightly unresponsive. Although I didn't investigate this issue, so the cause could be anything.

And yes, I know TwinView is not the fault of the community/developers, but it's still a big issue for me.


**- Hibernation**

Oh boy. When I was still going to the university, I used Ubuntu (Dapper/Feisty? I don't remember) on my laptop and I quickly learned that I shouldn't bother with hibernation. Now, with Gutsy, things have (somewhat) improved. Most of the time, I can hibernate my desktop and resume without problems. Sometimes, I resume apparently without any problems, but I get an error message saying "...failed to hibernate" :confused: Other times, I get no error message, but my mouse doesn't work. And just today, I resumed fine, but none of my displays initialized (black screens everywhere). Ctrl+Alt+Del, Alt+R worked and I could reboot. Guess I shouldn't bother (again)...


**- Evolution**

Importing my emails from Outlook Express took some work but it was painless. I had to import my contacts by hand though, I don't know if Outlook's export or Evolution's import screwed up. I added some appointments in the calendar, set the alarms and...nothing. For several days. Then I guess the planets got in the right alignment because the alarms started working.

Yesterday, I got two emails from HR people asking for my diplomas (I'm looking for a job). So I scan them (on a Windows PC as JPEGs), use "convert" (I don't remember from which package) to get PDFs, attach them in my emails and click send. Today, both persons replied saying they couldn't open the files. Hmm. I try the PDFs on the Windows PC with Acrobat and they work fine. I attach them again and send an email to my web-based account. What do I get? 1.dat and 2.dat, both unreadable of course.

That was the last straw. Needless to say, this was something important and may have hurt my chances at getting a job :mad:


**- Conclusion**

Total timespan : I don't know, 2-3 weeks, on and off. In the end, I'd rather go through the hassle of calling Microsoft to be able to reactivate Windows than continue fighting Ubuntu. I'm really disappointed with my experience. I knew I would have to make many sacrifices (gaming for one), but this is just too much. I always considered Linux to be "by programmers for programmers" and this continues to be true (for me at least). I still use Ubuntu at my part time job for Web development, but as a general purpose OS for my desktop, it just fails.

While most of your problems can be overcome with some tweaking and application changes you have not asked for help in this thread anyway.

This thread should be moved from the support section to the Ubuntu Testimonials & Experiences section.

---

### Post by JoshuaRL on 2008-04-04
> **Steve Angelidis said:**
> Its not relevant to my set up. So I haven't tried it. But check out the following: [http://howtoforge.com/howtos/linux/ubuntu]("http://howtoforge.com/howtos/linux/ubuntu")

Might be useful to you.

All aspects of Ubuntu work great for me except the hibernate. But booting and shutting down are so much faster than Vista was, that I don't mind. I just shut her down.

Yeah on that one.  I could never get my hibernate working at all, but then when i needed to lock it down i just locked the screen.  And if I got low on battery I shut her down and came back with the powersource.  It booted up so fast I could have it running before I got it plugged in.

---

### Post by aysiu on 2008-04-04
> **crjackson said:**
> 
This thread should be moved from the support section to the Ubuntu Testimonials & Experiences section. Moved.

If the OP had asked before switching, I could have saved her or him two to three weeks and said, "Don't bother." Ubuntu isn't by programmers for programmers, but right now it's not ideally suited for people who need dual display and consistently working hibernation.

---

### Post by bodhi.zazen on 2008-04-04
Ah, beaten by aysiu

> **aysiu said:**
> Moved.

If the OP had asked before switching, I could have saved her or him two to three weeks and said, "Don't bother." Ubuntu isn't by programmers for programmers, but right now it's not ideally suited for people who need dual display and consistently working hibernation.

Shhh ... don't tell that to my dual monitors they are working flawlessly (and I have the not-work appropriate screen shots to prove it).

I was going to say, Linux is not a drop in replacement for Widows. It takes longer then a few weeks to learn any OS, including Windows.

I suggest the OP dual boot for a while and ease into the transition. Asking for help also works well on these forums. Add a dash of patience and willingness to learn new tricks ...

If that is too much to ask, best stay with what you know :lolflag:

---

### Post by wPwLUi3N on 2008-04-04
I totally agree that linux some time leads to frustation especially when the hardware is not working.

But you have to see that its not linux who is responsible but the hardware manufacture.

Every time one person goes and buys windows they get more encouragement to support windows and ditch linux.

But if you stay with linux, first you disitinguish yourself from the millions out there and second the small problems will get solved with time.

In the end you will have better efficiency than you  had before.

---

### Post by aysiu on 2008-04-04
Just to clarify, I didn't see dual display is *impossible* or *always difficult*; I just said Ubuntu is not currently *ideally suited* for people who need dual display.

You *may* have a good experience if your computing needs involve the following, but I wouldn't *recommend* Ubuntu to you: [list][*]ATI[*]Windows-only games[*]Adobe CS3[*]AutoCAD[*]Advanced features in Microsoft Office[*]Suspend/hibernate[*]Dual monitors[*]Lexmark Printers[*]Dial-up modem[*]Broadcom or Atheros wireless[*]Latest iPod[*]Five-button mouse[/list] If, however, your computing needs involve the following, I would recommend Ubuntu to you: [list][*]Intel graphics card [*]Wired ethernet connection[*]Single display[*]Desktop (as opposed to laptop) [*]Regular keyboard and mouse [*]Simple program needs (email, web browser, basic office needs, music, pictures)[/list]

---

### Post by belaj on 2008-04-04
> **Leetbumble said:**
> As far as the multiple monitors issue... screw all other tools. Nvidia has a tool which you download from their website with the driver for your card. you run it and it mods ur xorg.conf file. I have a 19inch non-widescreen and a 20inch widescreen and all i had to do was download these two items, run the app with the system being in text mod and when it restarted BOOM! dual monitors and I actually have wine for games and compzi-fusion running at full speed all the cool tricks and tweaks.

Configuration is not the problem, functionality is. The issue I have with TwinView is:
One monitor is 1280x1024, the other is 1024x768; you get one 2304x1024 X window. The bottom 256 pixels on the smaller monitor are inaccessible. And like I said, Gnome sees 1 large screen and not 2 smaller combined screens.

> **hurtstotalktoyou said:**
> If you expected learning a radically different operating system to be quicker and/or easier than a 6-minute phone call to Microsoft, well, I'm not sure what to tell you.

Learning is not the issue...I have a Computer Science degree and have used different Linux distros for various periods of time. I'm well aware that it's gonna take more effort to get things working. What gets me is that some things just don't work, period. Like Compiz+Xinerama...I spent days researching the problem and the answer is that there's some issue with X/composite/nVidia and there's no solution.

> **hurtstotalktoyou said:**
> Anyway, it sounds like what's failing is the software for that operating system, not the OS itself.

Good point, but then again, an OS without good software is pretty useless. I guess my rant is against GNU/Linux in general, not Ubuntu.

> **hurtstotalktoyou said:**
> If you don't like Evolution, why don't you see what else there is?

As for Evolution, I like it. I like the interface, I like the integration with the Gnome panel (calendar)... it's not that it doesn't meet my needs, it's that some things are broken. Come on, sending emails with attachments to a Windows PC... pretty basic don't you think?

> **stchman said:**
> Multi monitors are not really needed when you have numerous workspaces.

Not the same thing. Physical space > virtual space, e.g. full screen app on one monitor, other things on a secondary monitor.



I can accept the fact that I won't be able to do everything I did on Windows and that I'll have to make sacrifices. I'm fine without Compiz and Xinerama gives me what I wanted, but it's...wonky. I feel like I'm running beta software. What's the alternative to X/Xinerama? Give up multiple monitors?

I want for this to work, to stay with Ubuntu. But if it's gonna take me a month of research and messing around to get everything working, is it worth it?

---

### Post by Urichhai on 2008-04-04
To bad people still have to kick microsoft around. I have been using Vista,XP Pro and Ubuntu as desktops and I run Server2003 and Ubuntu server edition on several machines in my house and they all have there pros and cons. I have seen the problems he is talking about and have had to reinstall all of the OS's several times due to a Grub failure. Problem is I am testing all of this for a company who is trying to decide which to go with and they and I are leaning towords MS due to compatability issues with other companies we will be working with. Linux has been around long enough to have gotten past all of the problems they have and its to bad the developers cant get on board enough to make a real stab at MS. kind of reminds me of Apple in a way.

---

### Post by bodhi.zazen on 2008-04-04
Your monitor problem should be an easy fix.

Try running

```
gksu nvidia-settings
```

If you make a mistake, exit X (ctrl-alt-backspace if needed) an try again. Once they are working save the changes.

+1 on the suggestion to go to a web based email client. try gmail.com (or any other). You can send and receive emails with attachments to any os running a web browser.

---

### Post by Urichhai on 2008-04-04
:biggrin:I totally agree with this post and well said.
=D> aysiu

---

### Post by belaj on 2008-04-04
> **bodhi.zazen said:**
> Your monitor problem should be an easy fix.

Try running

```
gksu nvidia-settings
```

If you make a mistake, exit X (ctrl-alt-backspace if needed) an try again. Once they are working save the changes.

Again, functionality, not configuration :)
TwinView in Linux with different resolutions just isn't usable.

> **bodhi.zazen said:**
> +1 on the suggestion to go to a web based email client. try gmail.com (or any other). You can send and receive emails with attachments to any os running a web browser.

Sorry, but that's unacceptable. I value my privacy and keep personal emails on my machine.

---

### Post by Urichhai on 2008-04-04
Sorry, but that's unacceptable. I value my privacy and keep personal emails on my machine.[/QUOTE]


What? so who do you use for email or are you running your own ISP?
Oh or its all internal email system and none from outside.

---

### Post by belaj on 2008-04-04
> **Urichhai said:**
> Sorry, but that's unacceptable. I value my privacy and keep personal emails on my machine.


What? so who do you use for email or are you running your own ISP?
Oh or its all internal email system and none from outside.

Once I download emails from my ISP, they're gone from their servers and they delete all emails older than 60 days anyway. And even if my emails stay in their backups, I'm much more comfortable having them in the hands of a company with whom I have a contract and which is Canadian (tough privacy laws in Canada), as opposed to GMail or the like.

---

### Post by Toet on 2008-04-04
After downloading the newest Ubuntu install CD, I experienced a md5 check error. So I decided to try Windows for once.

Oh man, what a pain this Windows. Under Linux I have six sets of keyboards, mice and monitors, all running there own session on one computer.

Couldn't get it to work with Windows, it just doesn't work.

Under Linux I have raid5 working with 5 different harddrives, couldn't get it to work on Windows.

I use mplayer to batch convert my m4a's to mp3, Media Player doesn't do it, I tried it for 3 weeks.

And than I had to pay for all the apps, or encounter illegal activities to get them available. Under Linux I just select them in Synaptic.

Going to download the CD again, cause Windows is no good.

	:-\"



-------------------------------------
Six headed desktop: [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

-------------------------------------
Brainstorm commercial:
[[IMG]http://brainstorm.ubuntu.com/idea/2098/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/2098/)

---

### Post by 3rdalbum on 2008-04-04
That Evolution problem is extremely strange. I've sent documents through Evolution to prospective employers and had them recieved without problems. I know it's been without problems because I've seen those documents in the interviewer's hand on the day.

---

### Post by Urichhai on 2008-04-04
> **belaj said:**
> Once I download emails from my ISP, they're gone from their servers and they delete all emails older than 60 days anyway. And even if my emails stay in their backups, I'm much more comfortable having them in the hands of a company with whom I have a contract and which is Canadian (tough privacy laws in Canada), as opposed to GMail or the like.

Dude they all do that and unless you are worried about someone reading something illegal than you have no worries.

---

### Post by stchman on 2008-04-06
> **belaj said:**
> 
Not the same thing. Physical space > virtual space, e.g. full screen app on one monitor, other things on a secondary monitor.



I can accept the fact that I won't be able to do everything I did on Windows and that I'll have to make sacrifices. I'm fine without Compiz and Xinerama gives me what I wanted, but it's...wonky. I feel like I'm running beta software. What's the alternative to X/Xinerama? Give up multiple monitors?

I want for this to work, to stay with Ubuntu. But if it's gonna take me a month of research and messing around to get everything working, is it worth it?

Instead of getting another monitor, you could get say a 24" with a resolution of 1920x1200 and use multiple workspaces.  Problem solved.

---

### Post by stchman on 2008-04-06
> **belaj said:**
> Hello!

I recently upgraded my PC and upon installing Windows, I discovered that I could not activate it because I went over my activation limit. So I said screw it, I'm installing Ubuntu. I'm gonna try (again) to use Linux as my main OS. The difference here is that I had the intention to switch over for good and ditch Windows completely.

However...well just read on to see what were the major issues I encountered.


**- Multiple monitors support**

It just sucks. nVidia TwinView is a poor hack compared to its Windows version. I have a LCD (1280x1024), CRT (1024x768) and a TV. I set up TwinView using the LCD and CRT, TV was a separate X window. On the CRT, I lose the bottom 256 pixels unless I specify a panning domain (bleh). Gnome doesn't see the two logical screens and stretches the panels and the login screen across the two monitors.

I tried Xinerama and it's MUCH better. I actually get three screens and I can move the windows between monitors. But then Compiz doesn't work... And Gnome lacks features to take advantage of this configuration (like a Send To Next Screen keyboard shortcut, which KDE apparently has). Some apps remember their position (on which screen), some open on whichever screen the cursor is on. Some apps like OpenOffice show their splash screen on the second screen and the app window on the first screen :confused:

Also, rendering seems inconsistent. For example, the Mines game takes a full 3-4 seconds to render the playing field. OpenOffice is slightly unresponsive. Although I didn't investigate this issue, so the cause could be anything.

And yes, I know TwinView is not the fault of the community/developers, but it's still a big issue for me.


**- Hibernation**

Oh boy. When I was still going to the university, I used Ubuntu (Dapper/Feisty? I don't remember) on my laptop and I quickly learned that I shouldn't bother with hibernation. Now, with Gutsy, things have (somewhat) improved. Most of the time, I can hibernate my desktop and resume without problems. Sometimes, I resume apparently without any problems, but I get an error message saying "...failed to hibernate" :confused: Other times, I get no error message, but my mouse doesn't work. And just today, I resumed fine, but none of my displays initialized (black screens everywhere). Ctrl+Alt+Del, Alt+R worked and I could reboot. Guess I shouldn't bother (again)...


**- Evolution**

Importing my emails from Outlook Express took some work but it was painless. I had to import my contacts by hand though, I don't know if Outlook's export or Evolution's import screwed up. I added some appointments in the calendar, set the alarms and...nothing. For several days. Then I guess the planets got in the right alignment because the alarms started working.

Yesterday, I got two emails from HR people asking for my diplomas (I'm looking for a job). So I scan them (on a Windows PC as JPEGs), use "convert" (I don't remember from which package) to get PDFs, attach them in my emails and click send. Today, both persons replied saying they couldn't open the files. Hmm. I try the PDFs on the Windows PC with Acrobat and they work fine. I attach them again and send an email to my web-based account. What do I get? 1.dat and 2.dat, both unreadable of course.

That was the last straw. Needless to say, this was something important and may have hurt my chances at getting a job :mad:


**- Conclusion**

Total timespan : I don't know, 2-3 weeks, on and off. In the end, I'd rather go through the hassle of calling Microsoft to be able to reactivate Windows than continue fighting Ubuntu. I'm really disappointed with my experience. I knew I would have to make many sacrifices (gaming for one), but this is just too much. I always considered Linux to be "by programmers for programmers" and this continues to be true (for me at least). I still use Ubuntu at my part time job for Web development, but as a general purpose OS for my desktop, it just fails.

Did you even try to set up multi displays?  I have a spare LCD and hooked it up to my PC.

Display 1 - 24" 1920x1200
Display 2 - 19" 1280x1024

Nvidia drivers 169.12

I was able to setup muli-display in under 5 minutes.  I still like virtual desktops but multi monitors proved EXTREMELY easy.

I had the 19" setup as the monitor to the right and was able to drag windows from one monitor to another.  The monitor even have different resolutions and it worked.

---

### Post by calc on 2008-04-06
> **stchman said:**
> Instead of getting another monitor, you could get say a 24" with a resolution of 1920x1200 and use multiple workspaces.  Problem solved.

I used to have 2 24" 1920x1200 monitors for use on my desktop but my wife claimed one of them. :lolflag: Really 2 24" were so wide it was hard to use them in side by side layout anyway. After working at one place where I had a triple head setup I've found that it is easier to use multihead if they are setup like /- or /-\ (angled monitors) instead of side by side.

---

### Post by crjackson on 2008-04-07
> **belaj said:**
> 
Sorry, but that's unacceptable. I value my privacy and keep personal emails on my machine.

Have you tried Thunderbir & Lightening?  I send attachments of all types all the time with no problems.  I like it much better than Evolution.

---

### Post by calc on 2008-04-07
> **crjackson said:**
> Have you tried Thunderbir & Lightening?  I send attachments of all types all the time with no problems.  I like it much better than Evolution.

Thunderbird mail sorting is nearly useless if you happen to use IMAP instead of POP due to the issue in LP bug #119899. The problem has seemingly existed for nearly 6 years but they still haven't corrected it. Somehow it didn't bite Thunderbird in Ubuntu until version 2.0 was uploaded, which was when I had to switch over to Evolution. :-\

---

### Post by crjackson on 2008-04-09
> **calc said:**
> Thunderbird mail sorting is nearly useless if you happen to use IMAP instead of POP due to the issue in LP bug #119899. The problem has seemingly existed for nearly 6 years but they still haven't corrected it. Somehow it didn't bite Thunderbird in Ubuntu until version 2.0 was uploaded, which was when I had to switch over to Evolution. :-\

I don't use IMAP anymore so I can test it.  I also don't care much for Evolution but for other reasons.  I used to send attachments using Evolution and I NEVER had a problem with it.  Could the fact that you are ussing IMAP possibly be related to your problems with regards to attachments?

There's got to be a decent email client that will suit your needs.

---


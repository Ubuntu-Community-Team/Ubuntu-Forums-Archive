---
title: "My experience as a first time Ubuntu user"
date: 2010-02-16
forum: Testimonials &amp; Experiences
---

### Post by nipsnertz on 2010-02-16
Two weeks ago, I loaded Ubuntu on an older Dell laptop to try to breathe new life into it.  I am a fan of Linux and a reasonably computer literate guy so I loaded 9.10 and logged in.   First I tried to connect to the internet with my wireless card.  This failed and took me 4 days of googling and searching web forums to fix with ndiswrapper.  next I tried to play a DVD and I got a gibrish error message that again took more research to fix.    At this point, I am starting to regret ever loading Linux. 
 
 I did not expect Linux to be as out-of-the-box  bug free as Windows but I did expect the documentation and error messages to be a little more user friendly.  For example, the DVD fix truned out to be a simple fix after I googled the wierd message that I got ("no URI Handler" ??? ).  
 
I hope that Ubuntu developers and supporters can try to understand that Ubuntu users need better system messages and better documentation to allow them to work with this OS.

---

### Post by steveneddy on 2010-02-16
Supported hardware would be easier to use the first time obviously, but you did find the issue and fix it, right? good.

Look at the links in my sig. for DVD playback there are some libraries that you may need and there are lots of other instructions in the links in my sig to help you out.

You could also try purchasing a new lappie from someone like System76.com and have supported hardware from the start.

I will agree that Linux is not simple all of the time, but I believe that your hardware issues are not Linux issues, they are the issues of the manufacturers not wanting or caring to release Linux drivers for their specific hardware so the community must "reverse engineer" the windows drivers, or in your case, write a script file to "help" the OS use the wireless drivers.

So just keep plugging along, read the links in my sig and remember, Google is your friend.

---

### Post by Ubu2010 on 2010-02-16
> **nipsnertz said:**
> Two weeks ago, I loaded Ubuntu on an older Dell laptop to try to breathe new life into it.  I am a fan of Linux and a reasonably computer literate guy so I loaded 9.10 and logged in.   First I tried to connect to the internet with my wireless card.  This failed and took me 4 days of googling and searching web forums to fix with ndiswrapper.  next I tried to play a DVD and I got a gibrish error message that again took more research to fix.    At this point, I am starting to regret ever loading Linux. 
 
 I did not expect Linux to be as out-of-the-box  bug free as Windows but I did expect the documentation and error messages to be a little more user friendly.  For example, the DVD fix truned out to be a simple fix after I googled the wierd message that I got ("no URI Handler" ??? ).  

I hope that Ubuntu developers and supporters can try to understand that Ubuntu users need **better system messages and better documentation** to allow them to work with this OS.

The man pages, info pages (most Linux distros), and help.ubuntu.com (Ubuntu-specific help) are all good sources of documentation, and there are many others, but these three sources are all supported by Ubuntu.

---

### Post by pricetech on 2010-02-16
> **nipsnertz said:**
> I did not expect Linux to be as out-of-the-box  bug free as Windows

A common misconception.  Winders is NOT bug free, out of the box or otherwise.  Many people think it is because they buy a computer with winders already set up for them and assume that winders "just works" when it fact it was made to work.

The documentation mentioned above, along with the information you find on the Web is at least as good as anything you'll find for winders and in many cases even better.

Any lack of hardware support is the fault of the hardware manufacturer, not the OS developer.

Nonetheless, if you're willing to learn you'll find the Linux community glad to teach and you'll find that you can solve a great many more of your owen problems than what you could with winders.

Just wanted to point that out.

---

### Post by jdrodrig on 2010-02-16
> **nipsnertz said:**
> Two weeks ago, I loaded Ubuntu on an older Dell laptop to try to breathe new life into it.  I am a fan of Linux and a reasonably computer literate guy so I loaded 9.10 and logged in.   First I tried to connect to the internet with my wireless card.  This failed and took me 4 days of googling and searching web forums to fix with ndiswrapper.  next I tried to play a DVD and I got a gibrish error message that again took more research to fix.    At this point, I am starting to regret ever loading Linux. 
 
 I did not expect Linux to be as out-of-the-box  bug free as Windows but I did expect the documentation and error messages to be a little more user friendly.  For example, the DVD fix truned out to be a simple fix after I googled the wierd message that I got ("no URI Handler" ??? ).  
 
I hope that Ubuntu developers and supporters can try to understand that Ubuntu users need better system messages and better documentation to allow them to work with this OS.


Thanks for sharing.

I am sorry Ubuntu failed to provide you a 100% smooth out-of-the-box experience. I hope in the long-run Ubuntu's benefits outweight these costs for you.

---

### Post by nipsnertz on 2010-02-17
All good points. I appreciate everyone's discussion. I listed this post because I am hoping that future distros of Ubuntu will give users a better out-of-the box experience than what I got. I realize that some things will be difficult: like providing soltuions for a myriad of hardware configs. However, other things should be possible: like helpful-descriptive error messages . Why do I need to know what a "URI handler"  is to play a DVD??
 
Thanks to all that responded to this thread, and many thanks to all of the members of this forum that help people like me with linux problems.

---

### Post by HappyFeet on 2010-02-17
Someone who had never used windows would find it just as frustrating. I have seen very cryptic error messages in windows also. Be patient, and it will come.

---

### Post by stalkingwolf on 2010-02-18
> I did not expect Linux to be as out-of-the-box bug free as Windows 

I recently reinstalled window on an old everex stepnote.  I had the original
rescue disk!!!   Something on the disk is borked.  got all kinds of errors.
Nothing would work couldnt install anything.

Tried my xp pro version.  No drivers for several things.  found drivers.

WINDOWS cant even find drivers in its own driver file.

reinstalled 8.04    works fine.

---

### Post by cbwcjw on 2010-02-18
Sometimes I wish things were easy to find. Oftentimes, you can get wireless to work with just

```
sudo apt-get install ndisgtk
```

It stinks how It took me weeks to find this, but the answer is in fact simple. That's the problem. Info is sometimes hard to find, instructions and wikis not comprehensive.

However, I took that opportunity to improve the ubuntu wiki, and edited the ndiswrapper article to help.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/)

---


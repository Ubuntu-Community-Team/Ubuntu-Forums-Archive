---
title: "First Karmic impressions of a new user"
date: 2009-10-30
forum: Testimonials &amp; Experiences
---

### Post by Asmodai on 2009-10-30
My only contact with the Linux desktop world so far was with Ubuntu Jaunty, which wasn't very usable due to frequent disk I/O lockups and subsequent file system errors. I assumed it was ext4 not being stable yet at the time.
That being said, Karmic now runs very well for me. I didn't have a single crash or freeze so far.
-- (feel free to jump over the next paragraph, since I'm no longer sure it's not a hard disk defect (this HD has been lying around unused in the garage for a few years). Just happened again, this time Ubuntu refused to mount the root filesystem and it was necessary to run fsck manually ) --
-- ouch, have to take that back before even finishing the post - started with Empathy and other applications no longer starting or just showing coming up with a blank window, even the shut down/restart dialog. Clicking on the place where the restart button was supposed to be worked, though. When viewing some logs, it seems that entries abruptly stopped about half an hour before I restarted (did some browsing and typing, so I didn't immediately notice that something was wrong). Although I closed Firefox before restarting (and saving the tabs), the tabs that were restored now are those from a while back. Ubuntu also just did a file system check when it booted. --


First thing I found a bit surprising is that Karmic boots a little slower than Jaunty (~40s for Jaunty, ~50s for Karmic), even though I did a clean reinstall.

I quite like the new brownish default theme - good job on that.

Next thing I noticed was the new Software Center. I think it should be possible to view all available applications in one single list like before, so you can browse through it to look out for any software you might want to install. Especially since it's not always clear which category you would find a program in - for example, I tried to install Wine. The search didn't turn up with anything, so I looked in &quot;System Tools&quot;. Or maybe it's in &quot;Accessories&quot;? Or &quot;Other&quot;? Maybe even &quot;Universal Access&quot;? After that I realized it wasn't listed, but yeah. Categories can be confusing. It would also be nice if you could view details while installing a new application (which new packages are being installed and how much disk space are they going to take?). Otherwise it's nice - loads fast too and the detailed descriptions are useful (can't remember having that in Jaunty).

About Empathy: setting it up is very easy, alright. Then I got a new notification that someone was messaging me - I proceeded to click on the notification like a maniac, expecting a conversation window to pop up - but no luck. I understand that the notifications are supposed to not get in the way, but by default, maybe the middle mouse button could be used to trigger an useful action when clicking on the notification (opening a conversation with the user, in this case). Took me until today to realize that I don't have to keep scrolling up and down the contacts list to look out for any blinking icons indicating that there are new messages. Maybe the symbol in the gnome bar could turn red or blue when there are new messages? Because dark grey doesn't catch your attention at all. Also, I'm missing an option to have Empathy open up a conversation window automatically when someone sends a message. The current behaviour is good if you're working and don't want to be interrupted but it is unconvenient in all other cases.
Since instant messaging is one of the primary things many people are using their computer for, I think it's quite important to make it as easy and intuitive as possible *and* to give some more configuration options to please everyone.

Another thing that can be quite irking is that when pressing print screen, the screenshot dialog takes several seconds to come up. I assume it's mostly due to the PNG compression - I think it would be better behaviour if the window came right up and the PNG compression was done in the background while you're choosing the file name/place.

Just noticed that in Network, Windows (Vista) computers and all their shared folders are listed - awesome. That doesn't even work in Windows XP, where I have to enter the computer and resource name manually if I want to access it.

Media-related stuff works great after having installed SMPlayer - I suppose having MPlayer installed by default isn't an option due to legal issues?
Some problems with Flash remain - moving the mouse over a playing YouTube video will cause it to come to a standstill (sound keeps playing, though) and flash files containing video streams (not on YouTube, though) usually stop playing after a few seconds. Not even unselecting/reselecting &quot;Play&quot; from the context menu resumes the video, like it usually does when the same happens under Windows (also using Firefox).
I suppose these issues are a problem of Adobe's Flash Plugin, so Ubuntu developers won't be able to do much. I hope the free flash alternatives become usable in the near future, as to not remain dependant on Adobe's mercy.

Ubuntu One is great - online storage that easily integrates into the file system without installing extra software is what I've been missing under Windows XP.

Once/if I manage to tackle the last &quot;big&quot; thing, namely setting up the latest Code::Blocks svn build with a cross-compiling environment allowing me to develop and debug Windows applications (I really hope debugging is possible), I'm going to switch to Ubuntu completely (provided I find a way to fix the disk problems). There are some smaller usability issues, but overall Karmic is quite charming.

Cheers,
David

---

### Post by akand074 on 2009-10-30
Yes, I agree I like the new theme! The new features are great too like Ubuntu Software Centre that could be very useful, I like how its very organized, I mean I understand where your getting at but I usually google around for ubuntu software when I need it, but the Ubuntu Software centre allows me to just browse around for neat applications in a particular category that I may be interested in at the time and thats much better than looking through all the software when maybe perhaps you just want to browse around for a game, or multimedia software for example. There are cases where it may be more difficult to find something you need especially when your not sure of specifics, but that is what I use google for.

The boot speed I find to be much slower, your quoting ~40 to ~50, but I use to boot in ~20 seconds at most into jaunty, ~25 seconds to fully log in, where as now its taking about ~50 seconds to a minute to boot in. 

Unlike you, I had no problems with Jaunty or any previous version at all. With Karmic I've had numerous crashes. I have never seen the crash icon before Karmic, and I've been having some problems with flash and firefox though. It has gotten better, youtube videos play now so I assume other videos would, but still having trouble with links from megavideo for example, where I click the play button and nothing happens. Though that may not be a Karmic related problem but its been working fine before.

I've never used any linux messengers, I've been on pidgin a few times but I run a virtual machine of windows at all times just for the general windows stuff that I would need to do so I run windows live from there so thats not really a problem for me, though I did open up empathy to check it out and it seems sort of plain. Haven't looked into that much.

Overall Karmic is definitely great but a few bug fixes and a faster boot up would be nicer, even if they had to remove a bit of the new flashy boot up.

---

### Post by Asmodai on 2009-10-30
Sure, usually you know which software you're going to install anyway. Still, adding the possibility of viewing all applications is easy to implement and comes with no disadvantages. It doesn't even need to be listed under categories, it would be enough if it was just a menu entry.

> **akand074 said:**
> The boot speed I find to be much slower, your quoting ~40 to ~50, but I use to boot in ~20 seconds at most into jaunty, ~25 seconds to fully login, where as now its taking about ~50 seconds to a minute to boot in. 
It's interesting that these deviations between Jaunty and Karmic can be so drastically different on various computers. It seems that quite a few people actually do get better boot times with Karmic. But I hope Lucid Lynx will improve times for everyone.


> **akand074 said:**
>  I've never used any linux messengers, I've been on pidgin a few times but I run a virtual machine of windows at all times just for the general windows stuff that I would need to do so I run windows live from there so thats not really a problem for me, though I did open up empathy to check it out and it seems sort of plain. Haven't looked into that much.
I'm using Pidgin on Windows, since it's much more considerate with memory than the MSN Messenger or the ICQ messenger. *And* it supports both protocols and even more if you need them. Empathy looks similar to Pidgin, although I prefer Empathy's contacts list. With the choice of icons, you can quickly see who's available and who is not. Simple, but functional. If the two points I mentioned are addressed then personally, I'll be perfectly happy with Empathy. Running a VM for that kind of stuff seems like a bit of a hassle to me.

---

### Post by akand074 on 2009-10-30
> **Asmodai said:**
> 
It's interesting that these deviations between Jaunty and Karmic can be so drastically different on various computers. It seems that quite a few people actually do get better boot times with Karmic. But I hope Lucid Lynx will improve times for everyone.


Yeah it could be because I'm running a quad-core that I got such fast boot speeds, but even on my laptop it didn't take much longer. I'm rather excited for Lynx, I think it will be the best Ubuntu out yet. The boot speed I had on jaunty was amazing, I wouldn't ask for more, I would just prefer if they brought it back. Still working over some issues on Karmic but over all it has some nice features but it seems like a work in progress, and that hopefully lynx will be the improved version

---


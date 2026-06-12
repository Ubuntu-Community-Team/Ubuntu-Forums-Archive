---
title: "Ubuntu 7.10 Impressions/Rants"
date: 2007-10-25
forum: Testimonials &amp; Experiences
---

### Post by sixstorm on 2007-10-25
Just wanted to share my experiences with 7.10 thus far.  I have never used Ubuntu as my primary OS just because of the lack of driver support when it comes to newer hardware.  I bought an older Dell last year from a good friend and Ubuntu worked fine, it was just that things like Beryl/CF doesn't work smoothly with older hardware.  Now that I have better hardware, Beryl/CF works smoother but there is the problem of no sound or something of the sort.  So which one do you sacrifice, speed/eye candy or stability/assurance?  

I just bought a new Compaq laptop (Intel T2310, 1GB RAM, Intel X3100, 120GB HDD) two weeks ago and decided to try Ubuntu out on the laptop side of things.  Actually, Vista Home Premium is on there and it is SLOW.  Boot times are like 2-4 mins!!!  I waited until 7.10 released and downloaded/installed the x64 version.  Things were ok at first, however sound worked 50% of the time and CF needed to have a swift kick in the rear end just to be enabled.  I worked and worked, searching the forums and Googling just about everything.  FINALLY!  It all works!  I'm so happy . . . until updates come along and break CF.  I actually made a post about it but it was ignored . . :(

After doing a reinstall, my sound was completely MIA and I had to make a few workarounds just to get CF to work.  I even sat down last night for two hours just to get my sound to work!  Guess what the sound does now?  Works on startup and YouTube videos, but I can't HEAR MY MUSIC on ANY player!!!  WTF?  I know that Intel's HDA apparently seems to be a PITA on the forums but come on guys.  Hasn't this chipset been out for quite a while now?

I guess it finally hit me earlier tonight.  Maybe since 7.10 is still "new", maybe I should just stick with 7.04 for a little while.  It's been out for a little while and it's had time to mature.  I popped in my 7.04 CD and "initramfs" (whatever it is) popped up and wouldn't let me load the LiveCD.  So now I'm redownloading the ISO just for craps and giggles.

I've got a nice rig that I use for gaming (Intel Q6600, 2GB RAM, 74GB Raptor, NVIDIA 8600GT) and Ubuntu 7.10 x64 is installed on it as well.  I cannot replace Ubuntu with Windows XP on this machine just because I game and I also review hardware for NVNews.net.  Everything runs great, but the mobo I'm using has an on-board X-Fi audio chipset and there are no drivers out there to pacify it.  Tough luck huh?

I've got all of my music on my laptop and I want to be able to play it when I want.  I don't own a Mac anymore so I've got to have something to hook my iPod into.  I also believe that Beryl/CF is a necessity.  Everything just seems to flow 10000x better than just plain ol' Metacity.  Metacity is just too stiff for me.  

Most responses to threads like these are "Well, Linux isn't for your type".  Let me say this before you do say that lol.  Ubuntu has opened my eyes to Linux and I don't regret any experience with it.  Just working with getting things to work does show you more about the OS than you might have wanted to know, but it's a good thing.  I'm a computer science information systems major and I love to play around with stuff like this.  

I love Ubuntu, don't get me wrong.  I love just to have an alternative to plain jane Windows.  Once Ubuntu can put out a release that supports more hardware, get better driver support (even on the newer stuff) and possibly even get more into the gaming scene (guess that's Wine's problem), it'll be one heck of an OS.  As for now, I'm going back to 7.04 and see if my problems can get worked out.  If not I'll just suck it up and use it regardless.  I'm not giving up! 

To Ubuntu Devs - I'm sure that you've noticed nothing but hate threads even since Gutsy released but I'm here to assure you that you guys are doing an EXCELLENT job.  Keep up the good work and your heads up.  Let's just work on stability for the next release please?

---

### Post by sixstorm on 2007-10-25
Just to make note, no other version of Ubuntu even loads up on my laptop but 7.10 so I guess I'm screwed.  :(

---

### Post by 3rdalbum on 2007-10-26
I had troubles with an Intel HDA audio chipset on a friend's laptop, but I installed the latest release candidate version of ALSA (it's actually pretty easy) and it works perfectly now. Try looking up Intel HDA on the Ubuntu wiki.

---

### Post by linuxlizard on 2007-10-26
*it was just that things like Beryl/CF doesn't work smoothly with older hardware*

Hey that's not true! I set up kubuntu feisty fawn on my folks computer with beryl, emerald and all the bells and whistles and their computer and video card are at least 5 years old now. Everything runs smooth as silk!

---

### Post by sixstorm on 2007-10-26
> **3rdalbum said:**
> I had troubles with an Intel HDA audio chipset on a friend's laptop, but I installed the latest release candidate version of ALSA (it's actually pretty easy) and it works perfectly now. Try looking up Intel HDA on the Ubuntu wiki.

I've got ALSA .015 installed and it's still f'd up.  Only startup sounds and anything in Firefox works, no MP3s work.  Silence isn't golden in my case lol.

linuxlizard - I've tried Beryl on a few older junkers and unless you have a NVIDIA card, it won't work/perform properly.  ATI sucks and integrated graphics are a 50/50 shot.

---

### Post by rustybronco on 2007-10-26
> **sixstorm said:**
>  I've tried Beryl on a few older junkers and unless you have a NVIDIA card, it won't work/perform properly.  ATI sucks and integrated graphics are a 50/50 shot. I had a radeon 7000ve on my 7.04 install running compiz so it can be done.

[http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)   look for rustybronco

---

### Post by sixstorm on 2007-10-26
> **rustybronco said:**
> I had a radeon 7000ve on my 7.04 install running compiz so it can be done.

[http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)   look for rustybronco

Oh I wasn't saying it could be done, it would just be a PITA lol.  I did have a ATI 9800 Pro and I thought I was going to lose my mind.  Bought a cheap 6200 and everything was peachy.

---

### Post by bd@cb8be8510 on 2007-10-26
It took me, after upgrading from Feisty to Gutsy, almost a week to get my wireless network running again. I had to read a lot of technical stuff in the forums, which didn't help after all. (Notice, as my wireless network wasn't running, I had to switch to another pc, in order to be able to browse the ubuntu forums). Finally, I tried to install a new usb-wireless-driver from serialmonkey.com.  It helped! (Strange, in Feisty I had no problems with my wireless network)

What I don't understand is, why they released Gutsy after all. A lot of problems with usb-wireless cards were reported when evaluating the release-candidate. I have a sad feeling about this. I couldn't use my system for about a week. Linux does not install right out of the box, even updating is cumbersome (read the forums!). I love working with my pc in Ubuntu, but I will not advice it yet to my friends :(

---

### Post by cwej on 2007-10-26
Not much of a rant really. I love Ubuntu and tremendously appreciate the community that makes it possible. 

I have one issue that 's only a mild irritaiton. In 7.04 the Firefox version installed came with Javascript 1.5. -- I need Javascript 1.5 to access a couple of very important copllaboration web sites, including "WebTycho" at the University of Maryland University College, but others requiring 1.5 (...that's Javascript, not Java by the way -- different).

Firefox 2.0.0.8 natively supports Javascript 1.5, but the Ubuntu version retrogrades to 1.4. My workaround is Opera, but does not work as well as the real Firefox. 

This capabiliy regression is a little baffling, but I'm sure that there must be a technical reason? Does anyone know why Firefox was dumbed down? Was this a security issue? Some other performance issue? Just curious, because I'm looking for better workarounds.

---

### Post by sixstorm on 2007-10-26
> **bd@cb8be8510 said:**
> It took me, after upgrading from Feisty to Gutsy, almost a week to get my wireless network running again. I had to read a lot of technical stuff in the forums, which didn't help after all. (Notice, as my wireless network wasn't running, I had to switch to another pc, in order to be able to browse the ubuntu forums). Finally, I tried to install a new usb-wireless-driver from serialmonkey.com.  It helped! (Strange, in Feisty I had no problems with my wireless network)

What I don't understand is, why they released Gutsy after all. A lot of problems with usb-wireless cards were reported when evaluating the release-candidate. I have a sad feeling about this. I couldn't use my system for about a week. Linux does not install right out of the box, even updating is cumbersome (read the forums!). I love working with my pc in Ubuntu, but I will not advice it yet to my friends :(

I totally sympathize with you on this one.  There is an online installer in the "Networking/Wireless" section that automatically detects what wireless card you have and installs "appropriate" drivers.  Thank goodness for that!  I noticed that you have a USB wireless card so I can't say I'm in the same boat as you are.

On my laptop, 7.04 LiveCD won't even boot up!  It goes to "BusyBox".  What the heck am I supposed to do with that?  I want to install 7.04!  Gutsy is fine, but the driver support and just overall stability is just terrible and inexcusable.  Isn't a new release supposed to be better than the previous release?

I'm certain that the Ubuntu dev team notices these things and will improve with updates.  Or maybe they are just putting more work into the next LTS release.  I'm expecting a lot more with the next release.

---

### Post by ChuckL on 2007-10-27
I totally appreciate your comments and experiences with Ubuntu and Linux in general. As someone who has been using MS products for years (pre-windows) and someone with some Unix experience, I can honestly say that I came to Linux kicking and screaming. I have also used Apple products (as far back as Apple IIs.) 

What has always bothered me has been those who are so radically fixated on a particular mindset that they cannot see beyond the end of their nose. Case is point is the myriad of rabid rants against MS that you find (including this forum) that upon reflection make absolutely no sense. 

I currently have five systems running Ubuntu Server 7.10 (recently upgraded all from Fiesty 7.04) and I love it. I used to run SUSE Enterprise Server but found it less than satisfactory for my needs. I also run the Ubuntu desktop (GNOME) environment on all my servers. Why? Because I absolutely abhor, hate, detest command line interfaces. I think they are archaic and non-intuitive, difficult to use, and most of all impossible to see what one is doing in many cases. Does that mean that I find those who are enamored with shells and command lines somehow beneath me? No, to each their own. 

I do find, as much as I really enjoy Linux, that there is also much that MS has to offer. One of the major problems with Linux is that it is Open Source. Yep. Because it is Open Source there is no one central issuer of product and thus no one consistent set of commands, product, etc. For instance, Redhat, Novell, Canonical, etc. each have their own distros. Guess what, they are all "radically" different; from obtaining updates and new software to the way that applications are configured, they are all different. Now to the avid Linux geek this is OK, but to the office worker who wouldn't be able to stumble around with even the slightest difference (and believe me that is 99% of the computer users) it spells the death knell to using Linux. 

I find much to admire and like about Linux but I also find much that I dislike about it as well. That doesn't mean I will quit using it, just that I believe there are reasons to use one system for certain things and another for other things. Case in point. I have tried to use Firefox on both WIndows and Linux and have found it SLOWWWWW and difficult to get to work correctly. I recently installed IE6 on my Linux machines and have consistently obtained faster and better performance. On one machine (2.8Ghz, 3.3G Mem) it takes 21 secs (with performance tweaks) to load the Ubuntu Forums home page using Firefox; it takes 5 secs using IE6 running on WINE. 

Another example is Evolution. Try as I might I cannot get it to load HTML email with images in anything short of a minute while Outlook consistently loads those pages in seconds. 

I could go on and on but I believe I have made my point. I would never consider switching back from Ubuntu and Linux but neither would I consider leaving the MS world entirely. I also believe that Macs have a place although I often wonder why anyone would pay the premium that must be paid for one.

---

### Post by 3rdalbum on 2007-10-28
Mac users do tend to feel that command-lines are archaic and non-intuitive. I was a Mac user for a long amount of time, but once I started using the command-line a bit (this was Linux a couple of years ago), I didn't mind it so much. Some things are definitely more efficient on the command-line.

All the same, I do tend to write GUIs for things that I often used the command-line for. My most recent GUI is for encoding video for my Sony Walkman.

---

### Post by rustybronco on 2007-10-28
> **sixstorm said:**
> Oh I wasn't saying it could be done, it would just be a PITA lol.  I did have a ATI 9800 Pro and I thought I was going to lose my mind.  Bought a cheap 6200 and everything was peachy. It wasn't a pita to do on the 7000ve, but the geforce2 mx400 was, on the other hand my geforce fx5900 was a breese.

---

### Post by LLauranzonIII on 2007-10-28
7.10 works perfect for me.  I don't see any reason for CF/Beryl so I don't care if it works or not.

Sorry to hear about the audio issue though.

---

### Post by floke on 2007-10-28
Warning!

These thoughts are banned:

[http://ubuntuforums.org/showthread.php?t=594210](http://ubuntuforums.org/showthread.php?t=594210)

Beware.

---

### Post by rustybronco on 2007-10-28
> **ChuckL said:**
> 
What has always bothered me has been those who are so radically fixated on a particular mindset that they cannot see beyond the end of their nose. Case is point is the myriad of rabid rants against MS that you find (including this forum) that upon reflection make absolutely no sense. no worse than a debate between owners of chevy, ford or dodge, there will always be zelots, but at what percentage? low in my opinion. 

> **ChuckL said:**
> I do find, as much as I really enjoy Linux, that there is also much that MS has to offer....Guess what, they are all "radically" different; from obtaining updates and new software to the way that applications are configured, they are all different. Now to the avid Linux geek this is OK, but to the office worker who wouldn't be able to stumble around with even the slightest difference (and believe me that is 99% of the computer users) it spells the death knell to using Linux. I find there is nothing wrong with microsoft operating systems and for most people that is all they will ever know and use until someone or something changes it, but some of us have a bad taste left in our mouths from the business practices of m-soft and have made a choice not to use  it. also don't discount  the power of a grass roots effort to promote linux, But because most people use m-soft that equates a death kneel to linux, surely you jest.

---

### Post by sixstorm on 2007-10-28
I haven't meant to bring up a flame war or anything.  I've just tried all three major platforms and I know each strengths and weaknesses.  Each have their place in the computing world.  I just hope that the Ubuntu dev team can focus more on stability with hardware support and drivers, whether it be an update or the next release.  

Linux definitely won't be taken off my laptop, I'll be using it for school.   I throughly enjoy using Ubuntu and will continue to use it for my everyday office and web needs.  Hopefully we can see some stronger gaming support through Wine :D

---

### Post by sixstorm on 2007-10-28
I forgot to mention.  All of my Ubuntu laptop problems are solved.  My sound just needed to be "redirected" to Alsa instead of Coxentant Digital. The only "new" problem is that my laptop won't wake from sleep properly, aka it freezes up.  But from what I've heard, this doesn't work on anybody's laptop.

---

### Post by equal on 2007-10-30
I'm in the process of downloading the 7.04 Gnome CD again. I've always been the guy who wants to have the latest greatest thing, and suddenly... 

Well, first off, my rants. My laptop often doesn't wake up from sleep mode, which has never been an issue until I installed Gutsy. For some reason, I can't load my iPod. It sees the unit, but claims it's a read-only file system, even after I explicitly tell it otherwise. My computer has even just randomly locked up out of nowhere. 

Bit torrent programs don't seem to be running as smoothly, the movie players are much jumpier, even after installing the restricted drivers (great idea, by the way).

But there is some praise. This is the first time I've gotten 64bit to function equally as well as 32bit. Flash works (finally!!), everything loads and runs. I initially thought my problems were coming from the 64bit OS, so I installed the 32bit, but no. The problem seems to be fundamentally with Gutsy.

So for now, I'll revert back to Feisty. Here's hoping they take some extra time if necessary and give us a 100% solid LTS, even if it has to be 8.06 or even further. Devs! No one will fault you for taking a year to program the next update if it's worth the wait!!

---

### Post by newbie2 on 2007-10-30
>  Last week, I moved from Ubuntu 7.04 (Feisty Fawn) to 71.0 (Gutsy Gibbon), and was sorely tempted to try the upgrade installation that was available. I did—and it failed. No harm done, however—and I had meticulously backed up all my data onto an external drive, anyway.

That done, I proceeded with a fresh install, but still ran into a snag because the installer didn’t seem to know how to handle the fact that I had three internal hard disks. I disconnected the other two drives and the new operating system installed without a hitch. Now all I have to do is reinstall all the applications I had and iron out a couple of minor kinks before I get my system back to the state it was in—just before the upgrade. What a pain! 
[http://www.manilastandardtoday.com/?page=business6_oct30_2007](http://www.manilastandardtoday.com/?page=business6_oct30_2007)
:rolleyes:

---

### Post by samuraiCat on 2007-10-30
> **sixstorm said:**
> Just wanted to share my experiences with 7.10 thus far.  I have never used Ubuntu as my primary OS just because of the lack of driver support when it comes to newer hardware.  I bought an older Dell last year from a good friend and Ubuntu worked fine, it was just that things like Beryl/CF doesn't work smoothly with older hardware.  Now that I have better hardware, Beryl/CF works smoother but there is the problem of no sound or something of the sort.  So which one do you sacrifice, speed/eye candy or stability/assurance?  

I just bought a new Compaq laptop (Intel T2310, 1GB RAM, Intel X3100, 120GB HDD) two weeks ago and decided to try Ubuntu out on the laptop side of things.  Actually, Vista Home Premium is on there and it is SLOW.  Boot times are like 2-4 mins!!!  I waited until 7.10 released and downloaded/installed the x64 version.  Things were ok at first, however sound worked 50% of the time and CF needed to have a swift kick in the rear end just to be enabled.  I worked and worked, searching the forums and Googling just about everything.  FINALLY!  It all works!  I'm so happy . . . until updates come along and break CF.  I actually made a post about it but it was ignored . . :(

After doing a reinstall, my sound was completely MIA and I had to make a few workarounds just to get CF to work.  I even sat down last night for two hours just to get my sound to work!  Guess what the sound does now?  Works on startup and YouTube videos, but I can't HEAR MY MUSIC on ANY player!!!  WTF?  I know that Intel's HDA apparently seems to be a PITA on the forums but come on guys.  Hasn't this chipset been out for quite a while now?

I guess it finally hit me earlier tonight.  Maybe since 7.10 is still "new", maybe I should just stick with 7.04 for a little while.  It's been out for a little while and it's had time to mature.  I popped in my 7.04 CD and "initramfs" (whatever it is) popped up and wouldn't let me load the LiveCD.  So now I'm redownloading the ISO just for craps and giggles.

I've got a nice rig that I use for gaming (Intel Q6600, 2GB RAM, 74GB Raptor, NVIDIA 8600GT) and Ubuntu 7.10 x64 is installed on it as well.  I cannot replace Ubuntu with Windows XP on this machine just because I game and I also review hardware for NVNews.net.  Everything runs great, but the mobo I'm using has an on-board X-Fi audio chipset and there are no drivers out there to pacify it.  Tough luck huh?

I've got all of my music on my laptop and I want to be able to play it when I want.  I don't own a Mac anymore so I've got to have something to hook my iPod into.  I also believe that Beryl/CF is a necessity.  Everything just seems to flow 10000x better than just plain ol' Metacity.  Metacity is just too stiff for me.  

Most responses to threads like these are "Well, Linux isn't for your type".  Let me say this before you do say that lol.  Ubuntu has opened my eyes to Linux and I don't regret any experience with it.  Just working with getting things to work does show you more about the OS than you might have wanted to know, but it's a good thing.  I'm a computer science information systems major and I love to play around with stuff like this.  

I love Ubuntu, don't get me wrong.  I love just to have an alternative to plain jane Windows.  Once Ubuntu can put out a release that supports more hardware, get better driver support (even on the newer stuff) and possibly even get more into the gaming scene (guess that's Wine's problem), it'll be one heck of an OS.  As for now, I'm going back to 7.04 and see if my problems can get worked out.  If not I'll just suck it up and use it regardless.  I'm not giving up! 

To Ubuntu Devs - I'm sure that you've noticed nothing but hate threads even since Gutsy released but I'm here to assure you that you guys are doing an EXCELLENT job.  Keep up the good work and your heads up.  Let's just work on stability for the next release please?

What is it with Compaq and HP latops? 

Anyway, you could wait, or you could try what I'm going to try: Put together a dual boot with 7.04 and 7.10. That way, when 7.10 is worked out, you can easily switch. Just don't use the same /home for both!

---

### Post by sixstorm on 2007-10-30
I've made a pretty good decision on my Ubuntu install.  After getting everything back to normal, more problems kept arising.  For example, if I switched to an Openbox session and back to Gnome, my panels and desktop items would disappear. They were still there but just transparent.  WTF?  I turned Visual Effects off and the problem was solved.  Maybe CF doesn't fully support my GFX chipset like I thought it did.  

So I'm reinstalling Ubuntu 7.10 x64 again and just using regular Metacity and Gnome.  I'm also going to try and get Openbox installed/customized just for learning purposes.  Wish me luck!

---

### Post by ksousa on 2007-10-30
My unique OS since three years ago is Ubuntu. For my work or leisure i have not any problem with this fantastic Linux distro. Is not out of box indeed, but his fantastic the evolution to achieve this. I don't want to compare it with any other OS, because they are all different, but for all my needs he is enough.
No virus ... no spyware ... candeyes supreme (compiz) ... and ... the most important ... a "NOBEL PRIZE" forum with fantastic guys all around the world trying to help all the people ... really UBUNTU.
Maybe the next evolution can be the perfection ... but if it happened, for the first time i rest disappointed :)

---


---
title: "New to Ubuntu - Softwear suggestions"
date: 2016-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by digi84 on 2016-11-04
Hello,

I am new to Ubuntu and Linux in general.  I have been reading alot of articles of first steps and what not and every article seems to have a different stance(crazy Internet world, huh?)

I was just hoping to get some suggestions for the following things.

Suggestions for a email client.  Ubuntu comes with Thunderbird I see, but is there a better one to use?

Suggestions for MP3 player/Video player.  - This is the one consistance.  Every article seems to suggest VLC media player, but most the articles are a year or more old.  Any better suggestions there?

Finally Suggestions for web browser.  I am most comfortable with firefox(as it is what I have always used on windows).  Chrome was also suggested and so was Chrominum.  Any suggestions here would be great too.  

Thanks everyone!

Threads merged; this with post #2.
Please do not create duplicate threads; if you need to add information either use "Edit Post" in the first post, or simply reply to your own first post.

---

### Post by cariboo on 2016-11-04
I use Thunderbird,and have been using it since it's inception, use Audacious for mp3's and VLC for video, and Chromium-browser for web browsing. It all comes down to personal preference. What suits one person, may not work for you. That's the great think about using a Linux distribution.

Installing and removing packages is fairly simple, so I'd suggest you install what has been suggested and try them out.

---

### Post by digi84 on 2016-11-04
> **cariboo said:**
> I use Thunderbird,and have been using it since it's inception, use Audacious for mp3's and VLC for video, and Chromium-browser for web browsing. It all comes down to personal preference. What suits one person, may not work for you. That's the great think about using a Linux distribution.

Installing and removing packages is fairly simple, so I'd suggest you install what has been suggested and try them out.

Great!  Thank you for the suggestions!  My only trouble with Thunderbird so far is that it has a long delay from when I receive an email to when it tells me.  I went in and changed the setting to notify me after 1 minute(instead of 10) after a email is received.  Still, it takes 45 minutes to an hour before it notifies me.  I get the notification on my phone and reply to it before Thunderbird even tells me.

---

### Post by TheFu on 2016-11-04
I use thunderbird - don't use gmail.  It is standards compliant, so if gmail follows the standards, it will work.

I use firefox for my main, safe-site, browser with a few extensions.  I will not use chrome (installing the browser from the largest advertising company in the world just seems foolish to me). I use chromium, but only inside a *container* that doesn't have write access on the system. There are known google-connections that chromium automatically uses. Some people are even more paranoid about it than me and have forked chromium and removed all internal hard-coded google connections.

Haven't screwed around with WINE in years. Used to run Quicken under it, but only 80% of that program worked. Prefer native Linux solutions that provide 80% of what you need.  I run Quicken inside a virtual machine with Win7 running. No surprises. It just works. The VM host is qemu-kvm on Linux/Ubuntu.

For audio, I've used clementine, audacious, xmms, and a few other client-server tools over the years.  Generally just tell my plex client to play my "best-of" playlist. Easier.

For video, I generally use Kodi for TV/projector stuff, Plex's web interface for laptop playback or remote streaming through a VPN tunnel to wherever I am.  VLC is a great player and I use is all the time for quick videos, but right now my Raspberry Pi is playing a movie using Kodi + PlexBMC.  mplayer and mpv are other popular video players.  mpv seems to have better support to use the video support inside our GPUs today. On a low-end or very busy system, that can be very important. Hardware codec support can be much better for video playback.

Check out alternativeto.net for popular alternatives to programs you know.  It has rankings, which is usually pretty reasonable. Filter by Linux.

"Best" is highly, highly, highly, subjective.  Also, trying to do things the same why you did on some other OS will lead to frustration. Linux isn't Windows or OSX.  If you only point-n-click, you'll only use 10% of the power that Linux provides and the GUIs change every few years (why, I haven't a clue).  I've been using the same shell cmds and script for the last 20+ years and most of the time, they just work.

For example, every week, I randomize my "best_of" audio playlist using a script.  This happens automatically - via cron on the system that holds the audio files.  I just need to run **mplayer /path/to/playlist.m3u** on the machine that has speakers connected and forgetaboutit.  mplayer has been around and playing audio files for at least a decade.  Before that, I used xmms and before that I used a webserver with playlists that winamp could play (gnump3). gnump3 is still around.  

If you have a Linux desktop - you have a Linux server that can be available from anywhere in the world, if you setup a vpn. Just sayin'.

---

### Post by digi84 on 2016-11-04
> **TheFu said:**
> I use thunderbird - don't use gmail.  It is standards compliant, so if gmail follows the standards, it will work.

I use firefox for my main, safe-site, browser with a few extensions.  I will not use chrome (installing the browser from the largest advertising company in the world just seems foolish to me). I use chromium, but only inside a *container* that doesn't have write access on the system. There are known google-connections that chromium automatically uses. Some people are even more paranoid about it than me and have forked chromium and removed all internal hard-coded google connections.

Haven't screwed around with WINE in years. Used to run Quicken under it, but only 80% of that program worked. Prefer native Linux solutions that provide 80% of what you need.  I run Quicken inside a virtual machine with Win7 running. No surprises. It just works. The VM host is qemu-kvm on Linux/Ubuntu.

For audio, I've used clementine, audacious, xmms, and a few other client-server tools over the years.  Generally just tell my plex client to play my "best-of" playlist. Easier.

For video, I generally use Kodi for TV/projector stuff, Plex's web interface for laptop playback or remote streaming through a VPN tunnel to wherever I am.  VLC is a great player and I use is all the time for quick videos, but right now my Raspberry Pi is playing a movie using Kodi + PlexBMC.  mplayer and mpv are other popular video players.  mpv seems to have better support to use the video support inside our GPUs today. On a low-end or very busy system, that can be very important. Hardware codec support can be much better for video playback.

Check out alternativeto.net for popular alternatives to programs you know.  It has rankings, which is usually pretty reasonable. Filter by Linux.

"Best" is highly, highly, highly, subjective.  Also, trying to do things the same why you did on some other OS will lead to frustration. Linux isn't Windows or OSX.  If you only point-n-click, you'll only use 10% of the power that Linux provides and the GUIs change every few years (why, I haven't a clue).  I've been using the same shell cmds and script for the last 20+ years and most of the time, they just work.

For example, every week, I randomize my "best_of" audio playlist using a script.  This happens automatically - via cron on the system that holds the audio files.  I just need to run **mplayer /path/to/playlist.m3u** on the machine that has speakers connected and forgetaboutit.  mplayer has been around and playing audio files for at least a decade.  Before that, I used xmms and before that I used a webserver with playlists that winamp could play (gnump3). gnump3 is still around.  

If you have a Linux desktop - you have a Linux server that can be available from anywhere in the world, if you setup a vpn. Just sayin'.

Thank you very much for your suggestions!  Are there any good Linux native solutions for WoW and other games without a linux clients?  Or would you say VM would be my best bet?

---

### Post by Bucky Ball on 2016-11-04
Thunderbird, VLC, Firefox. Not a gamer at all, but [Steam and Valve]("https://wiki.ubuntu.com/Valve") seem to be where it's at. 

Just a few more: Libreoffice for Office, GIMP for Photoshop, Skype is natively available from the repositories, and one of my personal favourties, Zim desktop wiki. Not really a replacement for anything but very handy. ;)

If you're want to have a good look around, I think Synaptic Package Manager is better than Software Centre (if that's what it is still called). Always look in one of the package managers (i.e. in the official repos) for the app you are after. Installing from there always best. Not like Win like that. You don't need to go looking all over the net for what you're after (generally). 

You should maybe go back to your other thread and tell responders there you are now here and taking their advice. Looking for alternatives. :)

(PS: You mentioned the page you were looking at was older so you were wondering if the apps there were still relevant? Simple solution. Check in a package manager and if it's there, it's still supported and will (should) run on your system.)

---

### Post by digi84 on 2016-11-04
> **Bucky Ball said:**
> Thunderbird, VLC, Firefox. Not a gamer at all, but [Steam and Valve]("https://wiki.ubuntu.com/Valve") seem to be where it's at. 

Just a few more: Libreoffice for Office, GIMP for Photoshop, Skype is natively available from the repositories, and one of my personal favourties, Zim desktop wiki. Not really a replacement for anything but very handy. ;)

If you're want to have a good look around, I think Synaptic Package Manager is better than Software Centre (if that's what it is still called). Always look in one of the package managers (i.e. in the official repos) for the app you are after. Installing from there always best. Not like Win like that. You don't need to go looking all over the net for what you're after (generally). 

You should maybe go back to your other thread and tell responders there you are now here and taking their advice. Looking for alternatives. :)

(PS: You mentioned the page you were looking at was older so you were wondering if the apps there were still relevant? Simple solution. Check in a package manager and if it's there, it's still supported and will (should) run on your system.)

Sounds great!  Thank you!  I don't really use photoshop of skype but I got the Libreoffice.  Zim desktop wiki...that does that do?

Well my other threads are still up cause my Ethernet still isn't working and I want it to.  The Dongle works but its a much slower speed than my ethernet.  Also I am still having trouble getting my USB ports(except the USB 3.0) to work.  I really want to get it all working right so I don't have to switch over to Windows just to use the internet.

---

### Post by Bucky Ball on 2016-11-04
All good. 

[Zim]("http://zim-wiki.org/") is less complex than it looks. It is a simple, lightweight desktop notekeeper for personal, local wiki pages. I keep a lot of links and other things for here in Zim for instance. The beauty with Ubuntu is you can install an app from your package manager, play for awhile, don't like, uninstall. All gone. :)

You might also get some joy [here]("http://www.linuxalt.com/").

It took me literally a few years to work out what exactly was best for my situation and that is still tweaked from time to time. You have the opportunity to get it just how you like, but that takes a bit of using Ubuntu and getting to know what's possible and what's out there.

Almost second nature with a new install for me now: install Xubuntu-core, which comes with pretty much nothing apps-wise, install Synaptic Package Manager and a desktop environment and then only the apps I use/need/want and that's it. One lightweight, lightening fast OS. Just how I like it (I need no bells and whistles). :)

PS: Not to do with any of this, but FYI and in case you don't know: LTS = long-term support, support for five years (for instance 16.04 LTS = 2016, April so until April 2021). The rest are interim, non-LTS releases which have nine months support.

---

### Post by digi84 on 2016-11-04
> **Bucky Ball said:**
> All good. 

[Zim]("http://zim-wiki.org/") is less complex than it looks. It is a simple, lightweight desktop notekeeper for personal, local wiki pages. I keep a lot of links and other things for here in Zim for instance. The beauty with Ubuntu is you can install an app from your package manager, play for awhile, don't like, uninstall. All gone. :)

You might also get some joy [here]("http://www.linuxalt.com/").

It took me literally a few years to work out what exactly was best for my situation and that is still tweaked from time to time. You have the opportunity to get it just how you like, but that takes a bit of using Ubuntu and getting to know what's possible and what's out there.

Almost second nature now with a new install for me now: install Xubuntu-core, which comes with pretty much nothing apps-wise, install Synaptic Package Manager and a desktop environment and then only the apps I use/need/want and that's it. One lightweight, lightening fast OS. Just how I like it (I need no bells and whistles). :)


Awesome!  As always, thank you so much, I appreciate the advice.  I know alot of my questions are probably dumb, but I guess I gotta start somewhere, right?

---

### Post by Bucky Ball on 2016-11-04
> **digi84 said:**
> I know alot of my questions are probably dumb, but I guess I gotta start somewhere, right?

+1. Not dumb questions and yes, we all gotta start somewhere. If it wasn't for this place and the Ubuntu diaspora sprinkled about the interwebs I'd probably still be floundering eight or nine years later! The only dumb thing would be not asking the questions and breaking your install because you didn't. :) (Although breaking and working out how to fix is the way some people go about learning more about Ubuntu.)

Very few of us here started computing with Ubuntu/Linux. We mostly got here through Win or Mac or some other means of computer experience so we all understand the learning curve involved in a new OS. When people complain that they can't just sit down and use Ubuntu like the OS they're used to, we ask whether the first time they sat in front of <OS here> they magically knew how to use that. That would be a 'no'.

With any new OS there will be a learning curve. This one has been more than worth it for me at least. :)

---

### Post by digi84 on 2016-11-04
> **Bucky Ball said:**
> +1. Not dumb questions and yes, we all gotta start somewhere. If it wasn't for this place and the Ubuntu diaspora sprinkled about the interwebs I'd probably still be floundering eight or nine years later! The only dumb thing would be not asking the questions and breaking your install because you didn't. :) (Although breaking and working out how to fix is the way some people go about learning more about Ubuntu.)

Very few of us here started computing with Ubuntu/Linux. We mostly got here through Win or Mac or some other means of computer experience so we all understand the learning curve involved in a new OS. When people complain that they can't just sit down and use Ubuntu like the OS they're used to, we ask whether the first time they sat in front of <OS here> they magically knew how to use that. That would be a 'no'.

With any new OS there will be a learning curve. This one has been more than worth it for me at least. :)

Yeah I hear you!  It took a long time to learn as much about Windows as I do.  I started using it back with Windows 95(those were dark days).  I've always disliked Windows and disliked Mac OS even more.  So I am happy for an alternative.  Just gonna take awhile to learn.  Biggest thing that is throwing me off is that things(ethernet, USB ports) don't seem to just want to work.  Gotta go all the go around for it.  

So far I love the interface of Ubuntu.  I activated the workspace switcher.  Love it, so nice to have 4 desktops to control the clutter when multi-tasking.

---

### Post by TheFu on 2016-11-05
> **digi84 said:**
> Yeah I hear you!  It took a long time to learn as much about Windows as I do.  I started using it back with Windows 95(those were dark days).  I've always disliked Windows and disliked Mac OS even more.  So I am happy for an alternative.  Just gonna take awhile to learn.  Biggest thing that is throwing me off is that things(ethernet, USB ports) don't seem to just want to work.  Gotta go all the go around for it.  

So far I love the interface of Ubuntu.  I activated the workspace switcher.  Love it, so nice to have 4 desktops to control the clutter when multi-tasking.

I loved Win95!  Compared to what we had prior, it was amazing! At the time, Linux still sucked too - at least in my mind as a relative noob.  Took a few years of daily, Unix, use to appreciate it.  If you don't use the GUI, things Unix-like don't change much over time.  Let me assure you - non-working USB and ethernet is really the exception.  Wifi used to be a hit or miss thing - now it sorta "just works" most of the time time.  Over the years, I've been burned by getting HW that didn't work with Linux - sometimes the vendor advertised (Linux Support) and it worked for 1 kernel that was 3 yrs old, nothing newer.  Eventually, I learned to buy well-supported HW for my needs.  I have an entire list of things I try to buy and another list of things I avoid now. Not written down, but hard-learned lessons about HW.  One of the hardest learned was printers - even different models from the same maker have vastly different support under Linux.

Truly, we were all new at some point. I remember my brain hurting from all the data coming in when I first was exposed to Unix systems. It was a few years later that I tried to learn Linux and a few years after that where I started to enjoy it.

About Zim - there are lots and lots of tools like that. I use gnote on my laptop. It is tiny, very light.  The files are sync'd to my primary desktop daily, automatically.  Since I avoid most things in the cloud, it is really nice that rolling your own cloud is not too hard on Linux (for certain values of hard).  If you are a computer person, I'd encourage learning about networking between systems the Unix way.  There is an entire world that does it differently, faster, in 50 different ways to how Microsoft does it.  Learn ssh, scp, sftp, sshfs, rsync, NFS.  These things will change your interconnected life. Right now, I have about 15 windows open - most are on other boxes. 1 is running patches for all the systems on my network through a tiny script. Takes about 15 min a week. Some are remote GUI logins with the screen being displayed here.  Others are text ssh sessions, running batch things like transcoding video (making it 25% of the prior size), one is controlling some music playback on a raspberry pi connected to a stereo system here. Another is creating a media mirror (for large files, normal versioned backups are just too much).  Most of the systems are running in a private cloud, but a few are at other locations 500-5K miles away.  With fast network, there really isn't much difference in my access between my laptop and the remote box 5K miles away.

Other little tools I use:

• gnote - quick note taking app
• alarm-clock-applet - timer / alarm clock
• geeqie - photo viewer    
• gcalculator - quick calculator
• gnumeric - quick spreadsheet when libreoffice is too much
• firejail - quick containers for GUI apps Ubuntu 16.04+
• KeePassX - password manager (v1 and v2 compatible)
• xdotool - automate/replace keys w/ commands/scripts
• alsamixer / amixer - sound controls
• pcmanfm / caja - file managers (for USB mounts and sftp)
• rsync - amazing sync tool

IMHO, humanity's greatest discoveries/inventions:
[LIST=1]
[*]Fire
[*]Wheel
[*]Unix
[*]ssh
[*]rsync
[*]Zero (the idea that nothing is something)
[*]Germ Theory
[/LIST]
I joke, but you get the point.  ssh is so centric to my daily life, can't imagine how I'd work without it.

---

### Post by digi84 on 2016-11-05
> **TheFu said:**
> I loved Win95!  Compared to what we had prior, it was amazing! At the time, Linux still sucked too - at least in my mind as a relative noob.  Took a few years of daily, Unix, use to appreciate it.  If you don't use the GUI, things Unix-like don't change much over time.  Let me assure you - non-working USB and ethernet is really the exception.  Wifi used to be a hit or miss thing - now it sorta "just works" most of the time time.  Over the years, I've been burned by getting HW that didn't work with Linux - sometimes the vendor advertised (Linux Support) and it worked for 1 kernel that was 3 yrs old, nothing newer.  Eventually, I learned to buy well-supported HW for my needs.  I have an entire list of things I try to buy and another list of things I avoid now. Not written down, but hard-learned lessons about HW.  One of the hardest learned was printers - even different models from the same maker have vastly different support under Linux.

Truly, we were all new at some point. I remember my brain hurting from all the data coming in when I first was exposed to Unix systems. It was a few years later that I tried to learn Linux and a few years after that where I started to enjoy it.

About Zim - there are lots and lots of tools like that. I use gnote on my laptop. It is tiny, very light.  The files are sync'd to my primary desktop daily, automatically.  Since I avoid most things in the cloud, it is really nice that rolling your own cloud is not too hard on Linux (for certain values of hard).  If you are a computer person, I'd encourage learning about networking between systems the Unix way.  There is an entire world that does it differently, faster, in 50 different ways to how Microsoft does it.  Learn ssh, scp, sftp, sshfs, rsync, NFS.  These things will change your interconnected life. Right now, I have about 15 windows open - most are on other boxes. 1 is running patches for all the systems on my network through a tiny script. Takes about 15 min a week. Some are remote GUI logins with the screen being displayed here.  Others are text ssh sessions, running batch things like transcoding video (making it 25% of the prior size), one is controlling some music playback on a raspberry pi connected to a stereo system here. Another is creating a media mirror (for large files, normal versioned backups are just too much).  Most of the systems are running in a private cloud, but a few are at other locations 500-5K miles away.  With fast network, there really isn't much difference in my access between my laptop and the remote box 5K miles away.

Other little tools I use:

• gnote - quick note taking app
• alarm-clock-applet - timer / alarm clock
• geeqie - photo viewer    
• gcalculator - quick calculator
• gnumeric - quick spreadsheet when libreoffice is too much
• firejail - quick containers for GUI apps Ubuntu 16.04+
• KeePassX - password manager (v1 and v2 compatible)
• xdotool - automate/replace keys w/ commands/scripts
• alsamixer / amixer - sound controls
• pcmanfm / caja - file managers (for USB mounts and sftp)
• rsync - amazing sync tool

IMHO, humanity's greatest discoveries/inventions:
[LIST=1]
[*]Fire 
[*]Wheel 
[*]Unix 
[*]ssh 
[*]rsync 
[*]Zero (the idea that nothing is something) 
[*]Germ Theory 
[/LIST]
I joke, but you get the point.  ssh is so centric to my daily life, can't imagine how I'd work without it.

For sure it was innovative at the time.  But if you tried to go back to Win95 today, you definitely wouldn't be happy right?  Even just stepping up to Win98 was a huge improvement at the time.

Cool thanks for the suggestions!  How does gcalculator differ from the default calculator?  With firejail what is a container and why do you want them?  What is ssh and how do you utilize it with Ubuntu?  Isn't ssh just how the file system is built with Linux distros?

---

### Post by TheFu on 2016-11-05
No need to quote entire messages. Just the relevant parts, if that is important - usually code. Save bandwidth for people paying by the bits on dialup.
I vaguely remember loving the interface compared to anything else available at the time. I was running OS/2 at home and had 12 Unix workstations at work. Win95 interface was better.  Changed jobs to a place using WinNT3.51 ... old interface. Even though it was more stable, I didn't switch until NT v4.0 came out with the newer interface.  

Today, I use a very minimal interface. No buttons. No menus.  Keyboard acceleration for the 10 programs I use all the time and an xterm for everything else. I miss fvwm from '96.  Just sayin'.  I very much dislike all the DEs and their bloat.  I know Linux with X/Windows can easily run with headroom in 8MB of RAM.  Everything larger than that is bloat in my book.  Unity is the king of bloat. I won't touch it - if I want an OS that DEMANDS over a Gig of RAM, I'd run Vista.

I have no idea what any default applications are for Unity-Ubuntu. Don't load it. Never use it. Don't know anyone who does enough to care.  Plus, since I'm running specific applications, I need to know the real name, not what some GUI menu says the name is.

Containers are an advanced idea, but very useful.  Google "Linux containers" to get an idea. Some people might call these "sandboxes", but that isn't anywhere near the same level of security as a "container" when we look deep inside the OS support layers.  Containers aren't 100%, but just another layer of protection outside what we already do to protect ourselves on the internet from "bad actors."

Don't know what ssh is?!!!!!!!!  I suspect we are very different computer users. ssh is how every Unix system in the world, including most switches and routers are managed from anywhere else in the world. It is how people network between 2 systems or 5,000 systems or 200,000 systems. OSX supports ssh.  Basically, every OS that isn't Windows has ssh support and there are good ssh clients for Windows.  Just haven't seen a secure, sshd (that's a server daemon) for Windows. A year ago, MSFT said they were working on it. Someday .... 

What can ssh do? [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)  ssh is a way I can be "at home" even when I'm overseas.  ssh is how I can manage a router in Nepal from Georgia.  ssh is how the backups on my systems can happen through a secure tunnel in the middle of the night.  sftp is how I can access any files on any of my systems, anywhere in the world, from wherever I am at the time, provided there is internet (rural Alaska, Nepal, Argentina, Costa Rica or NC mtns excepted).  Really ssh is just the secure transport layer - it is other tools that do the magic, but without ssh, they wouldn't be nearly as useful.  I can manage virtual machines from anywhere in the world - create new ones, shutdown unneeded ones, modify storage, RAM, CPU on others.  ssh lets me have a remote desktop that can be accessed from anywhere in the world (effectively), so even in locations with heavy govt spying, I don't have to worry that they can access sensitive personal or corporate data ... because that data is safe back in my home country under physical locks.  ssh rocks, completely.

Ok - we are well beyond the OP.

---

### Post by digi84 on 2016-11-05
Okay, so I'll save containers for a little ways down the road, once I learn the basics, lol.  

Awesome!   Thanks for the link, I will give it a read! Yeah I don't do much with  networking.  I only have the one computer, well unless you count the  smartphone.  Yeah, I've been up till recently, a life long DOS and  Windows user.  So I don't have any working knowledge of SSH.

---

### Post by Bucky Ball on 2016-11-05
> **digi84 said:**
> Okay, so I'll save containers for a little ways down the road, once I learn the basics, lol.

Good idea. For now, I'd say stick to what is relevant to your needs now and learn about that. Once you've got your feet wet and have some idea what you're doing and where you want to go with it, spread your wings! :)

You may never use SSH or Firebird, but you are probably always going to want a word processor, a music and video player, email and a browser. Aim for getting across the basics, which it looks like you are and that's a good thing.

---

### Post by bearlake on 2016-11-06
Not sure what you are using for a software package manager. [Synaptic]("https://help.ubuntu.com/community/SynapticHowto") is very handy.

---

### Post by digi84 on 2016-11-06
> **bearlake said:**
> Not sure what you are using for a software package manager. [Synaptic]("https://help.ubuntu.com/community/SynapticHowto") is very handy.



I have mainly been using Ubuntu Software Center but I do have Synaptic installed.  What is the benefit of Synaptic vs Ubuntu Software?

---

### Post by bearlake on 2016-11-06
> **digi84 said:**
> I have mainly been using Ubuntu Software Center but I do have Synaptic installed.  What is the benefit of Synaptic vs Ubuntu Software?

It's great for updating the packages you have and installing the packages required when installing new programs.

Included in the link posted, there is a good write up on all the things it supports and offer.

Ubuntu Software Center hasn't been helpful as lately been rather new to the different flavors.

---

### Post by Bucky Ball on 2016-11-06
> **digi84 said:**
> What is the benefit of Synaptic vs Ubuntu Software?

You get a MUCH better look, if I can put it that way. Synaptics is more 'open' in that you can see all the programs, tells you all the dependencies an app requires when you install, apps are split into categories so it is easier to see what's out there, you can find and look at all software in the repos easily.

As with all apps Ubuntu, install it, try it, don't like, uninstall. :)

Personally, I haven't used Software Centre or any of its siblings in years. I use a custom setup and haven't even had it installed in years! :)

---

### Post by vasa1 on 2016-11-07
> **digi84 said:**
> ...  What is the benefit of Synaptic vs Ubuntu Software?
Turning it around, and from what I remember, Ubuntu Software Center (or whatever it's known as now) was supposed to provide "user reviews" and pay-for applications, magazines, etc. Like some of the posters here, I too haven't used it in quite a while.

---


---
title: "My Kubuntu experience so far 7.04"
date: 2007-05-14
forum: Testimonials &amp; Experiences
---

### Post by ezrollers on 2007-05-14
I finally decided to ditch my dual boot setup and move full time to kubuntu 7.04. I had been using xp 

and ubuntu 6.10 before. 

I booted with the livecd and tried to install it, tried being the key word here as the installer 

crashed twice, not a very auspicious start. 
I went back to windows, double checked the md5sums and they were ok.

I restarted again and this time I managed to go through the whole installation progress without any 

hitches.

Once in my shiny kubuntu 7.04 I set about configuring soundstorm. It took me a bit of extra time, as 

nvmixer needs a library called libstdc++ version 5. I thought that since I had v6 installed that 

should be a superset of all previous libraries plus something new, alas I was wrong. After I 

installed it nvmixer works fine, so I'm a happy camper.

I then tried to install a few programs, bittorrent clients, newsreader, firefox, vlc and a few other bits and bobs.
Adept packet manager crashes halfway.

I try running firefox but it crashes twice. I try running VLC and the system hardlocks. So I 

introduce my index finger to his new friend the reset button, they used to know each other very well 

in the win 95 and 98 days, but they aren't in such good terms anymore, kubuntu will try its darnest 

this weekend to rectify this, but I get ahead of myself.

I uninstall everything and try again. This time it goes thru fine. I do notice that it is taking an 

awful long time to download anything, but don't really think much of this at the time.

I should say that I chiefly use my computer as a media centre, therefore my 5.1 logitech speakers 

coupled to soundstorm are IMHO a very good platform, a lot cheaper than getting a new puter with a 

super dupa creative sound card, but I digress. Sound and video are paramount. A close second is the 

ability to, erm, "obtain" tv shows quickly.

I try VLC and BOOM, second system hardlock of the day. Promptly followed by hardlock number 3, they 

are coming thick and fast now. The reset button is a very happy chappy after all this years of 

neglect he is the king of the hill he used to be, I can almost see it smiling.

I think that it might be a problem with my ntfs partition, so it mount it read only. I manage to 

close VLC before it crashes the system. I try from an ext3 partition and this time i'm not so lucky, 

enter hardlock number 4.

VLC doesn't work is my conclusion, therefore I try to install mplayer. Adept manager makes another 

hash of it and mplayer doesn't work. I'm a bit annoyed but help is at hand I decide to do it the old 

fashioned way. I dust off my linux install skills, i.e. I remember that one types

./configure
make
make install


I get the source for mplayer, compile it and it runs fine, but unfortunately I've never been able to 

get 5.1 sound out of mplayer for HD releases of tv shows.

I try kaffeine and after messing about with the sound settings ( I set speakers to pass thru) it 

works as it should. Voice coming from centre speaker, music and noise from satellites and subwoofer.

I am indeed very happy.

We watch a documentary "God spoke" with AL franken and my gf remembers a very funny video on youtube, 

Fox version of 12 days of Christmas.

Much to her delight I find it, much to our annoyance it takes my about an hour to sort out the sound 

on youtube, I suppose the price you pay for having soundstorm.

At this point, I'm thinking that I have spent the best part of the weekend trying to do something 

that in windows would have taken 2'5 hours. (Unattended install + drivers + firefox + opera + office 

+ vlc + newsbinpro + bittornado + mplayer + deamon tools + nero).
I also reflect on how I haven't had a system lockup in windows xp in years, and I've already had four 

with ubuntu, granted that one of them could be related to the installation pro

By now it is sunday and the F1 grand prix is fast approaching. Java is not installed and therefore no 

live timings. I download and install the plugin just in time for the second start.

Firefox crashes 3 times while the GP is running, I still wonder why I watch F1, the positions are 

fairly defined after the start bar accidents or mechanical failures, and sure enough out of corner 3 

come Massa, Hamilton, Raikkonnen and ALonso, podium: Massa, Hamilton, ALonso Raikkonnen out with 

engine failure.

Anyway, My girlfriend wants me to install a virtual machine, so that she can use a couple of programs 

that work only in windows, I know about wine just bear with me. I try to find a set of instructions 

for Xen, but my patience has well and truly run out by now so I go with vmware server.

It starts downloading and speed is about 30 KB/s (i have a 4mbps cable connection). I try using 

konqueror instead, but speed is similar. I use my laptop to see if there is a problem with the server 

and speeds are steady at about 180 KB/s

I am informed that I should blacklist the ipv6 protocol, which I duly do. I reboot for what must be the 20th time of the weekend and try again to download vmware server. It makes absolutely no difference whatsoever.

I search these forums and the interweb at large. I try a few things mainly to do with DNS servers, but download speed barely goes above 40 KB/s

To sum up my experience thus far:

Kubuntu appears to be less stable, more troublesome and less functional than windows xp.

I was ready for it being more troublesome, but less stable and 40KB/s download speed are simply unacceptable

Today is monday and I'm going to install OpenSuse on one partition and Opensolaris on another and take it from there. I might even go back to 6.10, who knows

---

### Post by jfrancis on 2007-05-14
Yikes!  Sounds like you had a real headache of a weekend there.  I am still a beginner in this stuff so I can't comment, only that I run ubuntu and not kubuntu, and for me I have not had any crashes though I use mine for more simpler tasks than you.

How much TV is available online now anyway?  Do the mainstream channels have live feeds and if so how can I access it?

Anyway, good luck with the new installations.

---

### Post by ezrollers on 2007-05-14
Not that much live content

loads of shows to download once they've broadcasted

---

### Post by lzfy on 2007-05-14
Well I guess I'm luky then :)  Kubuntu installed fine, everything works out of the box, no crashes even with beryl. Codecs, java and flash where installed in 10-15 minutes. I guess your hardware is the troublemaker here. Good luck.

---

### Post by samjh on 2007-05-14
My only problem with Kubuntu is with Adept and some strange UI errors in Thunderbird.

But it is true I think, that Kubuntu is not as polished as some others.

---

### Post by maniacmusician on 2007-05-14
I used to have issues like Adept crashing in early 6.10 and earlier, but I haven't since then.

Try installing using the Alternate CD? I hate installing from the Live CD as it's considerably slower and doesn't offer any discernible advantages except for people that have never seen a Linux desktop before. I don't think I've ever had an error with the alternate CD that wasn't my fault (Once I had a bad CD, and another time I had bad RAM in the computer)

---

### Post by icecruncher on 2007-05-14
I agree, live cd's are a pain especially wth the old computers. 
Must say that I had no problems with the alternate. 
Hope things get less complicated for you.

---

### Post by ezrollers on 2007-05-14
i'll give the alternate cd a whirl

It can't hurt. thanks for the suggestion.

---

### Post by Cheizzz on 2007-05-14
My experiences with kubuntu have also been less then pleasure-able to say the least.
A lot of stuff which works great in ubuntu doesn't do its work in kubuntu and some nice things like the restricted drivers manager are just missing. And adept is horrible. 
I have tried kubuntu many times now as I am quite impressed by the great looks and features of KDE, but I keep running back to ubuntu because it works so much smoother.
Kubuntu needs a lot of work and love to keep up with ubuntu. Just my 2 cents of course.

---

### Post by ezrollers on 2007-05-15
My already low appreciation of kubuntu got lower yesterday.

I tried to setup samba and comitted the mistake of expecting it to be a 5 minute job, boy was I in for a surprise.
Admitedly, it is my own fault as I've barely used linux for the past 3-4 years, so my recollection of how one is supposed to configure samba was hazy at best. 

On top of that I was a bit pressed for time which didn't not help. In the end I gave up. I could see the files on a windows shared folder, but could not read them, copy them or otherwise do anything with them.

Fed up I installed kubuntu 7.04 from the alternate cd. 

Changed settings in xserver, who on their right mind would run any sort of CRT at 60 Hz, but that is beside the point. I blacklisted ipv6. Rebooted

Tried to download vmware server, 50 KB/s
tried to download ubunut alternate iso 50 KB/s
Speed from repositories ~ 50 KB/s

I was so f#~ked off I almost sent my work laptop flying thru the window.

I put my maxtor hdd with a windows install still on it. changed BIOS settings to boot from it and back to Windows.

Newsgroup speed 475 KB/s

There is nothing wrong with my hardware.

I've not given up yet though. Ubuntu 7.04 is gonna get installed this afternoon.

I'll also test downloads on the ubuntu installation on my Maxtor HDD.

---

### Post by afonic on 2007-05-16
Generally I'd agree Kubuntu is not so polished and hassle free as Ubuntu as I use both and I can see the differences.

However, they are essentially the same OS (they use the same repository, just the DE changes) so hardware detection problems, hard locks or installing software like Apache or Samba will have the same problems in both enviroments.

---

### Post by pawitp on 2007-05-16
> **ezrollers said:**
> 
Tried to download vmware server, 50 KB/s
tried to download ubunut alternate iso 50 KB/s
Speed from repositories ~ 50 KB/s

I put my maxtor hdd with a windows install still on it. changed BIOS settings to boot from it and back to Windows.

Newsgroup speed 475 KB/s


What about downloading vmware server without acceleration on windows or ubuntu alternative iso?

---

### Post by ezrollers on 2007-05-21
I keep having fun with my kubuntu distro.
I managed to solve the download problem. It appeared to be confined to Mozilla based browser, I installed opera and it works fine. Incidentally, so do Konqueror and Firefox now.

On sunday I bought a couple of plane tickets and I thought it would be nice to be able to print them. Some airlines, make that check-in people, want, insist, on seeing your booking reference, even if your passport is more than enough, but I digress.

I set about install drivers for my canon pixma mp180 printer. After following several guides, trying different drivers I managed to print using the turboprint driver, only downside is that there is a big  effing watermark, which I can get rid of for the princely sum of €30, remind me again why I started using free software?

So I can pay €30 to print, I imagine that the scanner works too, or I can print in windows out of the box, only a driver install needed. 

Another, unrelated, issue was the inability of bittornado to save its settings. Sorted that one out, fairly quickly. Just changed the settings on the config gui file on $HOME/.Bittornado/

Why it won't save them from the gui is beyond me, but that seems to epitomize linux for me.

I am also pissed off at vmware server for not install winxp from my unattended CD. Can't say it is a linux problem, because I can't remember if it worked on windows.

I still soldier on undeterred though. I must be masochistic or smth

---

### Post by Rashid584 on 2007-05-21
I admire your persistence :p

I dunno why you're having such a bad experience...Kubuntu works pretty much perfect for me :S

One thing I noticed, you tried to use a lot of apps which are unnecessary. There's no need to install vlc or mplayer, kaffeine comes with Kubuntu and works great ;) (if you have codecs). No need for Bitornaod...use KTorrent. No need for daemon tool or nero, use K3B...you get the picture.

I agree about Kubuntu being behind Ubuntu...its unfortunate and kind of annoying. Canonical should invest more resources into Kubuntu. Some may argue Ubuntu is downloaded at least twice as much as Kubuntu...but maybe thats because of the gap in quality? Vicious circle...

-Rashid

---

### Post by ezrollers on 2007-05-21
> **Rashid584 said:**
> I admire your persistence :p

I dunno why you're having such a bad experience...Kubuntu works pretty much perfect for me :S

One thing I noticed, you tried to use a lot of apps which are unnecessary. There's no need to install vlc or mplayer, kaffeine comes with Kubuntu and works great ;) (if you have codecs). No need for Bitornaod...use KTorrent. No need for daemon tool or nero, use K3B...you get the picture.

I agree about Kubuntu being behind Ubuntu...its unfortunate and kind of annoying. Canonical should invest more resources into Kubuntu. Some may argue Ubuntu is downloaded at least twice as much as Kubuntu...but maybe thats because of the gap in quality? Vicious circle...

-Rashid

I appreciate what you mean about using kaffeine, which works absolutely fine, and other applications, but I'd still like to choose what I use.

This is in no way directed at you, just a general gripe of mine.

[rant]
why do people feel the need to point out that there is an alternative program when asking for help?

I didn't ask for help to choose a different program, I asked for help on how to run this program. Use program x or y instead is not very helpful

[/rant]

What's with usage of memory. I did a free -m after restarting the xserver and it showed 80 mb free outta 1 GB

what's up with that?

---


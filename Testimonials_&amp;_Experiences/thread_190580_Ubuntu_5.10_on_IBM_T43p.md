---
title: "Ubuntu 5.10 on IBM T43p"
date: 2006-06-06
forum: Testimonials &amp; Experiences
---

### Post by lagerratrobe on 2006-06-06
First post on this forum, from a first-time Ubuntu user.  Thought I'd share some feedback about my Ubuntu 5.10 install on an IBM T43p Thinkpad.  

Pro's:
- All hardware properly detected "out of the box". This includes: SATA hard disk, battery, sound, wi-fi, ethernet, Touchpad AND IBM mouse "nub".
- Clean, minimal, user interface and application menus.
- Decent set of applications included in default install.
- Automatic notification of available updates.

Con's:
- Rythym Box MP3 player seems unable to play MP3's encoded by Windows media player.
- Inability to play DVD movies without installing additional CODECS.
- Inability to play .mp4 or .mov files without additional work.
- Network administration for multiple connections not very transparent.
- Slow to boot up due to myriad services trying to load.  (aka "Why am I waiting for my NIC?")

Overall, this is a really nice distro imo.  With some tweaks, it will probably work as well, or better, than my previous DSL Linux HD install - with less speed, but a great deal more flexibility.

BTW, in case there are other T43p users out there reading this post. This is one of the ONLY distro's I've tried that properly implements the ipw2200 drivers for our Intel wifi.  That includes having it work properly with DHCP AND wpa_supplicant.

Cheers.
--

---

### Post by mostwanted on 2006-06-06
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by jdong on 2006-06-06
[QUOTE=lagerratrobe]First post on this forum, from a first-time Ubuntu user.  Thought I'd share some feedback about my Ubuntu 5.10 install on an IBM T43p Thinkpad.  
[/quote]
thanks for doing so! We love hearing everyone's experiences.
May I also suggest installing/upgrading to 6.06? It's a huge improvement from 5.10, which was already pretty awesome :). It should also solve a lot of your problems, too.

> 
Con's:
- Rythym Box MP3 player seems unable to play MP3's encoded by Windows media player.
- Inability to play DVD movies without installing additional CODECS.
- Inability to play .mp4 or .mov files without additional work.

All three of these are due to various patent restrictions. The MP3 problem may have solved itself (Fluendo now offers a legal Linux decoder... encoders are still at your own risk/expense), but until the patent situation changes Ubuntu will not be able to ship with such support. However, we are all working on ways to make it easier for users to enable multimedia support, such as the Automatix project to make a simple one-click GUI for this setup.
> 
- Network administration for multiple connections not very transparent.


Agreed... Linux definitely still shows some of its Unix roots... that is, has "dedicated always-on network connection" in its heart :)

That is beginning to change -- for example NetworkManager provides a very stolen-from-OSX approach for laptop users to roam across networks. NetworkManager is in 6.06.

> 
- Slow to boot up due to myriad services trying to load.  (aka "Why am I waiting for my NIC?")

Dapper Drake has improved bootup speeds dramatically through bottleneck analysis. There are, however, technical reasons for how Breezy loads. Everything before the GUI loaded before the GUI for a reason... X Windows (the GUI environment) does need networking set up (at least no more hostname changes) and does not play well with time skew (such as NTP sync changing the time) after it's initialized. Dapper now boots to a login screen well under 60 seconds on reasonably modern hardware, and logging in to a ready desktop only takes 15 seconds or so on top of that.

---

### Post by lagerratrobe on 2006-06-06
Hi Jdong,

I appreciate your reply, and the explanations you included.  I will give 6.06 a shot and report back in this thread how it works out.  As far as DVD's and MP3's go, I understand the patent restrictions, but regardless of the reasons, it remains something somewhat more difficult to enable these functions in Ubuntu, as compared to Windows.

lol  I have to laugh when I read that last sentence, because I know it will invite heat.  Let's just say that I don't run Linux usually for entertainment purposes, but I decided to try those things out in Ubuntu because the interface is so clean.  Eventually it will all work out.
--

---

### Post by HeavyAl on 2006-06-07
I just saw this and had to post. I dont have the t43 - that must be an awesome system to work on, but I do have a t40 that I've been running Ubuntu on for quite a while and just recently upgraded it to Dapper. The hardware in the thinkpads seems to just 'work' without any really major problems. And ubuntu is the best Linux distro I've ever worked with. It is really so amazing that people were able to get theri stuff together and come out with such a spotless os.

So far the only problem I've had with dapper is that the buttons on the applications are inexplicably corrupted. Its not on all the applications, and there is no rhyme or reason as to why its happening but it doesnt affect the functionality so I'm not too worried about it.

/me Drinks to yet another amazing Ubuntu release.

Great job people!

---

### Post by lagerratrobe on 2006-06-22
Ok, wanted to follow up on my earlier post about running Ubuntu 5.10 now that I've updated to 6.06.  I have to say that overall, the upgrade has fixed just about every complaint I had posted before.  Here's a quick rundown of what I've seen that is different, and better.

- All hardware buttons work WITH screen widgets.  They all worked fine in 5.10, but now I can actually see the volume bar move when I toggle up.down/mute.

- Boot up time is significantly faster than before.  No lag for network time server sync, or NIC initialization.

- Network Manager is great,  I'm even able to connect seamlessly to my corporate WPA wifi network.  HOWEVER, to make it work properly you MUST flush your /etc/network/interfaces file.  Otherwise it the NM app won't do a darn thing for you. This is the only thing left in mine:

auto lo
iface lo inet loopback

Once I had removed all of the old entries from that file and rebooted, the Network Manager found all the wifi networks in my building and allowed me to connect very easily.

Very, Very, Very, nice job.  Awesome.

---

### Post by jdong on 2006-06-22
I'm glad to hear that many of your problems were addressed with Dapper :)

Enjoy using Ubuntu, and never hesitate to ask us questions!

---

### Post by lagerratrobe on 2006-06-26
Is there a configuration utility that exists for enebling an external monitor with a laptop?  I have a Dell FPW 2405 that I'd like to use with my laptop and Ubuntu.  I suspect I'm going to have to edit my xorg.conf file manually, and I'm really not exited about the idea.

Thanks
--

---


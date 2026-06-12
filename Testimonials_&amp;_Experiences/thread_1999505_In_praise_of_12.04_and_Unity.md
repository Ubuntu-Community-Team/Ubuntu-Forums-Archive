---
title: "In praise of 12.04 and Unity"
date: 2012-06-08
forum: Testimonials &amp; Experiences
---

### Post by v4169sgr on 2012-06-08
I'm a long time Linux user, and have been running Ubuntu since 5.10 [experimentally] and 6.04 [as the main desktop]. Before then, I was running RPM distributions like Mandrake [as was then] and Suse.

On Monday, I performed a fresh install of 12.04 on new hardware, having plugged in a RAID0 of two disks with all my 10.4 system and user data files on it. The fresh install went straight on to an OCZ Vertex 4 128 MB SSD.

This is a family PC / entertainment centre / server. The main uses are :-
* web browsing
* email
* flash videos [very important!] - mainly TV on demand catch up services like BBC iPlayer, 4OD etc, and YouTube
* word processing / spreadsheets / presentation software, mainly for the children's homework
* photo management [all our photos since 2005 are stored on a shared 'gllery']
* mp3 and other music [including burning to CDs]
* games - standalone and flash
* the Ubuntu variant of LTSP

Most of the use targets above have been met straight out of the box on this new hardware. I did not really have hours and hours to exhaustively check to see that all the hardware would be supported, so it was great that:
* Sound
* Networking
* Printing
were all supported right out of the box. I did need to do a little tinkering with the sound to make sure the additional sound card was selected.

USB management is right-out-of-this-world!!! For the first time that I can remember in Linux [going back a LOOONG way], USB has truly become 'plug-and-play'. Awesome!

My RAID0 arrays were detected very smoothly during the install process, an alternate install 64 bit, with manual partitioning, as promised. I was pleased that there was no faff there and I could label all my current and old partitions the way I wanted. I managed to install grub on /dev/sda by accident because that was the default, hence the first boot never happened, but a quick flourish with the install CD in recovery mode and a reinstall of grub to /dev/sdc later, and we were on our way.

For the use cases above, including for thin client desktops, Unity is actually a really good interface. Well thought out, fast and functional, without too many problems, it just gets out of the way and lets the user do their thing. The Launcher is simple and intuitive: it took me only a short time to realise how straightforward it is to add and take off applications. I really like the ability to 'click and navigate' by application on the Launcher in one click - so easy. The Dash is truly excellent, a lot better than the 'Beagle' abomination I had to disable last time around. It's a little slow on fresh boot [I mean, it takes 2-3 seconds to refresh, but come on what is that ? :)] but after that it is super-quick. I did install the classic menu indicator, but I think I must have used it once LOL. I did miss the Gnome 2.x applets, that is until I found out about indicators, which are mostly a drop-in replacement.

User management is a bit more of a faff than it needed to be - I needed to install the Gnome users-and-groups widget to complete user configuration, but only because I am really picky about things like maintaining the correct UUIDS etc. I like the 'Ubuntu Tweaks' application too, but can't actually remember using it to change anything - just nice having the security blanket of having it there :) The login screen is a bit different to what we were used to - I used the 'human list' theme on GDM for years and years because it was a smooth drop-in replacement for the 'human list' theme from my Suse and Mandrake days. Seeing your desktop on the login screen, and not seeing the user's icons shall take a little getting used to [no 'human list' on LDM that I know of], but these are small things.

Areas I did have problems with [running around screaming tearing my hair out LOL] were :-
* First, third, fifth etc boots never completed. This was critical and needed to be solved before the users got their mitts on the system. The solution was a bug in 11.10 that was apparently not triaged properly [thread here: [http://ubuntuforums.org/showthread.php?t=1997417](http://ubuntuforums.org/showthread.php?t=1997417) ]. The problem was a race condition in performing a health check on the RAID before they settled, coupled with the purple screen getting in the way of the error message, with the result that the boot hung infinitely;
* Thin clients' video was in reverse video and tiled, making it unusable. I did not realise for a while that this is because the Ubuntu 2D is needed [see thread here [http://ubuntuforums.org/showthread.php?t=1998133](http://ubuntuforums.org/showthread.php?t=1998133) ]. I've now managed to set that session to the default, so the user's don't have to remember to switch to get a usable desktop;
* After taking the repo update from firefox 12 to 13, flash in thin clients broke [see thread here: [http://ubuntuforums.org/showthread.php?t=1998922](http://ubuntuforums.org/showthread.php?t=1998922) ]. I gave up on solving the problem here as it is clear that Mozilla and Adobe won't play nice, so instead will use Chromium / Chrome to play flash in thin clients. Reminds me of the four or five web browser days back 5+ years ago ;)
* I was struck down by the SMURF effect [blue faces in flash videos, ewwww! ;/]. You can say anything you like, but I'm not going to start playing with plugin .so files all over the place that work today, don't work tomorrow etc like in the 'bad old days', so I did not downgrade to a really old and crusty flashplugin .so, but instead just switched off the Nvidia driver - problem solved. I hardly miss it anyway, the open-source drivers are that good.

I now have a usable, fully functional system that the users will accept and hopefully like using, including Google Earth, Picasa goodness etc. It has taken a bit more toil and effort than I was prepared for, but frankly, if this was not open source and I had similar issues, I'd be a lot more stuck than I have been!

Overall, in meeting my goals of a user-friendly 'just switch on and use' application that is also very low maintenance, I'd say we are not there yet, but Ubuntu 12.04 and Unity take us a big step closer.

Nice job, guys :)

---

### Post by v4169sgr on 2012-06-08
This is why I *love* open source :-

I've just read

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

and applied the fix to libvdpau1:

```
sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1
```

_(NB read the entire article before applying to your system!!!)_

Result: SMURF effect banished! SCORE :)

Can't imagine such reactivity in the M$ world lol

---

### Post by 3rdalbum on 2012-06-09
> **v4169sgr said:**
> This is why I *love* open source :-

I've just read

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

and applied the fix to libvdpau1

Nvidia's engineers need a kick up the backside. People have been having this problem with Nvidia's drivers since 2008 or maybe even earlier. The problem predates VDPAU. It shifts from one card to another in each driver version.

A better reason to love open-source is not because the VDPAU developers work around Nvidia's bugs, but because the open-source nouveau driver has NEVER introduced a Smurf bug. Better code quality and perhaps even better testing.

Any Nvidia software engineers listening? Fix your freaking drivers. It's embarrassing. Not even ATI users have silly problems like this.

---


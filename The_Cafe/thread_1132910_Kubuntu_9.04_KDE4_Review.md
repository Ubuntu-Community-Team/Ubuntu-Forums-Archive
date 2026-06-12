---
title: "Kubuntu 9.04 KDE4 Review"
date: 2009-04-22
forum: The Cafe
---

### Post by NightwishFan on 2009-04-22
Kubuntu 9.04 Jaunty RC Review

The last time I visited KDE, was using 4.1 with Kubuntu 8.10 and OpenSUSE
11.1. Both were fairly usable, although incomplete. I assumed this time around I would be using the GNOME desktop, to avoid having potential problems on any of my supported installations.

I took a gamble and installed the AMD64 version of Kubuntu Jaunty.

I was greeted by a new, very minimal boot splash screen, which I had heard about. The boot time itself, even from live CD was considerably faster.

The default KDM was mainly unchanged, which is no problem. At least it matches the splash screen and default theme, which is great on first impressions.

The first login on KDE4 always seems to be slow, but it was not unreasonably
so. I had no problem with it.

The default desktop uses the KDE air wallpaper and the oxygen theme, with a
slightly Kubuntuized color scheme. That is only slightly a disappointment, as
Kubuntu could easily have it's own wallpaper. Then again, like I said, it
matches the splash and KDM.

By default the desktop is configured to use the folder view widget. I prefer
this, as it basically prevents clutter, though the option is available to use
your desktop as a file container. (Classic Mode).

I figured once I got the installation going, I would play around with some of
the applications. I always boot a live CD with some media on a USB drive to
test, without tying up the hard drive. The installer looks great with QT, and
has a redesigned time zone chooser, which shows the current selected time zone rather than only a map.

Preceding the partitioning in the installer, I was informed my flash drive was mounted, and was given a choice if I wanted to unmount it or not. It informed me that if I did not mount it, I could still use it while installing. Fantastic.

The partitioner itself has gotten a rewrite, and now shows the size of the
partitions. I chose to manually edit them, so I could format my XFS root
partition to EXT4, and my separate ext3 boot partition. This allows me to
use a file system that is questionable with grub as root. No problems there.

Another change to the installer is to the check box that greeted us in Intrepid, which allowed us to set up the system to log in automatically. It is now two choices, which are explained in plain English. Perhaps done to avoid mistakes and confusion.

The installation preceded as always, showing off the new look to the oxygen
progress bar, which now looks very smooth. Whilst the installation took it's
own course, I explored the other applications on the live CD.

Due perhaps to space constraints, the Kubuntu RC CD is lacking many
applications. Ktorrent, Digikam, and KSCD among others. It also does not have
any screen savers by default. Another feature it was lacking by default is other plasma themes, having only Oxygen. (Not Aya or the others). This is
of no concern to anyone except those without an Internet connection. Much
functionality remains, and it is only a RC, of course. Please not these programs are "available" just not on the installation CD.

One thing that there was no lack of was plasma widgets. Dozens at the least.
More plasma widgets than I would ever need. Some of the more interesting ones
include: LCD Weather Station, Monitors for CPU, TEMP, HD Space, Mini Web
Browser, etc. There is an excellent Network Manager widget, and a very visually appealing 3D globe.

A widget I did not expect, or even hear of was the Lancelot menu. It is
seemingly an alternative to the kickoff menu, and is very nice. The menu
features a more compact, single pane design. It is similar to the GNOME menu
on OpenSUSE, though more interactive. The icon is a goblet, which I liked, but many would not I assume. It seems to be a work in progress, as it acts
more like a window than a menu on Kwin. It is worth a try if it catches your
fancy.

By default Kubuntu uses kickoff however. It now has a sleek dark look, and is
far more responsive and fast.

The ZUI (zooming interface) makes a comeback in this release, and it seems very stable. It also features it's new, and easier to use design, and a widget to change activities.

For those of you who do not understand this feature or it's use, it is similar to a virtual desktop, however, rather than contain separate windows, it has separate widgets. An example of it's use is to have one activity with widgets for communication and folder views for work, and another with a more colorful wallpaper and photos of your family to casual use. You can have different desktop backgrounds and widgets on each activity, and they can be switched at will.

At about this time my installation finished. It only took about 15 or so
minutes. I rebooted, and was ready for the first boot, which I was going to
time. Midway through however, my backup drive was scheduled for a check, and I was forced to delay until next boot. The fsck on my 100+ GB ext3 partition
seemed faster, I do not know if any improvement was done here.

Regardless, I shut down at KDM, and timed the boot process. I started the count at right after the grub timeout, and ended it when I could type at KDM. It took just under 12 seconds with my root partition as ext4. Impressive indeed Ubuntu developer padawans. Don't underestimate the force.

My system specs are NOT impressive. (Not shabby but very outdated.)

CPU: AMD Athlon(TM) 64 X2 Dual Core Processor 3800+
RAM: 861.0 MB
GPU: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)

I tested login time using the KDE Autostart module, and adding Konqueror. On
the second login (the first is always oddly long), it only took about 8
seconds. Which seems a bit slow, but it is actually a huge improvement over KDE 4.1, which took far longer on Kubuntu 8.10, Fedora 10, and OpenSUSE 11.1. Note I do not have preload installed, only the default installation.

As I have a Nvidia card, the first thing on my agenda was to enable Nvidia
drivers. I do not have an Internet connection on my target system, so I
downloaded the packages manually and installed them via DPKG. DKMS still makes an appearance, which is good, as I do not have to re-download my drivers.

When I used jockey-KDE to activate the nvidia 173 driver, nothing happened. It did not ask me to authenticate. It simply did nothing. So I did what any
somewhat technical user would do: I used the command line options.

When I manually told the program to install the Nvidia drivers, I was given the standard GUI authentication, although no main window appeared. I was given a message, saying that jockey-KDE has crashed, however the driver was still activated. I logged out and restarted the X-server, and lo and behold I had 3D acceleration.

About this time I noticed that I could drag the calendar from the clock applet away from the panel, which was interesting. When I did this, plasma crashed, however it restarted itself promptly.

I also noticed that the time on my clock was set up incorrectly. Which was odd, as it stayed correct through installations of Debian, Ubuntu, Fedora 10, and OpenSUSE 11.1. I opened the system settings to correct this. When I set the time right, it must have been CPU/IO intensive, as my desktop effects were automatically disabled. I was given a clean and easy to understand message, saying that my desktop effects were disable due to system load and I could enable them with a few keystrokes (alt+shift+f12). Cool, and they can be toggled at will as well!

KWin itself has improved a great deal. Employing motions physics, windows feel more natural when they are interacted with. The default plasma theme works will wallpapers of all colors, and does not stay blue. Many more effects were added, and they have a more verbose configuration. (Love the falling snow! :D)

Krunner is similar to previous releases, and have a few more options, such as
opening favorites. No big deal.

Ah! Almost got you. Yes there is now a secondary interface for Krunner, called Quicksand, which is more task oriented. It is similar to GNOME-DO, though animated. You just slide to the left to get what you need.

Both interfaces feature all the plug-ins, such as power management, browsing
favorites and starting a mail to Kmail contacts. You can also run basic
calculations.

Upon opening beloved Amarok, KDE informed me with a message (similar to the on that stated my desktop effects were suspended) that I could extend the
functionality of Amarok. When I clicked on the announcement it showed me a
dialog where I could check functionality such as mp3 and flash playback.
Obviously a way for package kit to automatically install Xine plug-ins, and
other extras. I was impressed by this as it is quite a few steps up in
usability. Browsing other apps I found this does not just install multimedia,
but I was informed I could enhance my nepomuk search features as well.

Amarok itself is, well Amarok. Clean and fluid interface, support for playing
and downloading from Jamendo. Which is all I really need as for on-line stores. It takes a bit getting used to the new interface, but I do not mind it. It plays my music and looks good doing it.

One thing that bothered me horribly on 8.10 and OpenSUSE 11.1 is the fact that GTK+ applications never seemed to obey any part of my QT theme, even when I told it to. Never fear! The sole GTK application on my system was Nvidia-Settings, and it obeyed my dark theme, and even had clean smooth oxygen buttons and lines! Excellent!

I am going to wrap it up fairly shortly, as I am sure if you even had the
patience to read this far you are getting annoyed with me by now!

As far as the other applications go, a few of them, such as gwenview crashed on me once, but no so again. Everything feels very stable. Much of the System
Settings were re-written and re-organized, and are much simpler and elegant. As for that, the only bug I noticed was that I cannot set a custom background for KDM. It only appears blue. Annoying, but tolerable. I can put up with the themed greeter. I hope they fix it soon enough, though.

Dolphin has had improvements. It does not seem to feature the new mouse-over
previews, however the slider bar to change icon size works well. There are
still some slowdowns with certain files. (I had trouble selecting a large .deb file, and it locked up dolphin (well not locked up but it was really slow).

Konquerer is fast! Nuff' said.

K3b KDE3 is still the default burner, no problems there, soon enough the KDE4
one will be ready. It does not follow the KDE4 theme or color schemes.

OpenOffice.org 3.0.1 works great, and does not crash plasma widgets anymore,
which always happened using my Nvidia card. It does not follow my KDE theme
though.

The system monitor has a new look. It is more similar to Gnome-System-Monitor.


THE AFTERTHOUGHT:

I wrote this absurdly long review in a pretty short time actually, about 1 hour.

Only a week ago I was skeptical about KDE in both stability and it's potential for the future. I doubt no longer! KDE4.2 impressed me not because of its many new features, many of which I was aware of. However when actually used those features, they simply blew me away with their speed and pure geeky fun! It combines intuitive ease of use with almost needlessly cool features.

I highly advise any and all to try out the KDE desktop. If you are skeptical, even then perhaps try it out. Problems are few, and it has many of the original features of KDE 3.5.

Ubuntu+KDE4=GO!

---

### Post by wolfen69 on 2009-04-22
good review, but i am going to pass on kubuntu. it is and always will be the red-headed step child of shuttleworth. i will use mandriva if i want kde. (and i'm not dying for it)

---

### Post by =^,^= on 2009-04-22
I had to give up on kubuntu jaunty and return to hardy.

The open source ati driver just isnt up to the job of supporting kde and plasma!

---

### Post by MasterNetra on 2009-04-22
My issue with kubuntu has been that it didn't come with a gui option to control/disable the touchpad on my Dell Latitude D530. While ubuntu does. Neither Hardy or Interpid Kubuntu versions have it. :/ And I really hate tap-click with a passion.

---

### Post by Dragonbite on 2009-04-22
Thank you for that review! I look forward to trying Kubuntu 9.04 after I get my other systems cleaned up and updated.

Oh, and have they yet fixed the kicker menu to use the Kubuntu logo instead of the default KDE?  It is one thing that has irked me since I first laid eyes on Kubuntu!

---

### Post by NightwishFan on 2009-04-23
I believe it uses the KDE Logo, it did as of RC..

It is a great release of KDE, however, poor as a distro. I use it because I like the Ubuntu base and KDE desktop. It is my best option, better than buggy SUSE (No offence, I love SUSE, but 11 series is horrible with everything but YAST).

---

### Post by Trail on 2009-04-24
The new release sounds kind of tempting to try (however, I am kinda annoyed by kubuntu in general, to be frank). But incidentally I tried KDE4 on Arch and it flies, so it might take a while more till I try kubuntu again :)

---

### Post by Asteryx on 2009-04-24
Used to be a big fun of KDE 3 but migrated to Gnome (Ubuntu) ever since the KDE 4 "upgrade" disaster ... It's not that KDE 4 is inherently bad, it's rather the abysmal way the migration was handled. In my opinion KDE 4 is still not ready and I fear KDE desktop project will pay dearly for their mishandling of this matter (especially for the length of time it'll take to complete the migration).

I would like to see a comparison: how much interest and how many downloads Kubuntu/KDE 4.2.2 has attracted with this latest release versus Ubuntu 9.04 compared to same for the 8.04 release (in percentage) ? I fear KDE might be in for a bit of a shock ... and an unpleasant one for sure.

OK, enough with that, here is my first impression of Kubuntu 9.04. Unfortunately is **still** cannot handle dual monitors (i.e., laptop + external display) properly !!!!! Ubuntu 9.04 (GNOME) does it with elegance, simplicity and efficiency. I still have to edit xorg files manually to have KDE handle dual-head setups. What a disgrace !!!

Then I still have problems with VmWare (which do not occur in Gnome).

For some reason after spending last year (maybe more ...) in Gnome (Ubuntu) exclusively I feel now like a stranger in KDE 4 and suddenly missing the Gnome interface. I personally don't feel the urge to spend more time in KDE so I'll get back to Gnome. Maybe it's just me but if there are more people out there that feel the same, then KDE team should get reeeeeeeeeally worried.

Good review by the way !

---

### Post by JohnFH on 2009-04-24
Have to agree with Asteryx.  I've been a Kubuntu user for the past 18 months (KDE 3.5), and tried Kubuntu Jaunty for the past few weeks.  It looks great but the occasional crash and stability issues are still there.  I've now switched to Gnome permanently and the crashes and sluggishness have gone away.  KDE 4.2 is still not ready and this time I've lost patience and gone back to Gnome.

---

### Post by Mehall on 2009-04-24
I've said it time and time again, don't judge KDE purely on Kubuntu.

You NEED to try another distro, Mandriva probably being the best KDE one out there.

---

### Post by Dragonbite on 2009-04-24
For KDE experience I usually first think of openSUSE. In the openSUSE forum there was talk comparing it with Mandriva.

So for KDE experience I would try openSUSE or Mandriva for better results.

---

### Post by CraigPaleo on 2009-04-24
> **Mehall said:**
> I've said it time and time again, don't judge KDE purely on Kubuntu.

You NEED to try another distro, Mandriva probably being the best KDE one out there.

What would you recommend by way of Debian/apt-based distros?

Aside from that, I've always been curious as to why Gnome is faster on some people's machines but not mine. Does Gnome handle multi-cores better? I have a single core sempron and KDE has always been faster. That's the reason I keep it installed but I just can't seem to get used to it.

---

### Post by Asteryx on 2009-04-24
Hi Mehall,

You may be right about Mandriva and KDE 4 - can't comment on that since I have never used that distro.

But ... if only our life would be so simple ...

I've been using Ubuntu for years now. So you know yourself, after a while you gradually get to "know" the OS in its intimacy (at least on the details that matter to you).

So switching to a different distribution is a big step into the unknown - and you really have to question yourself if it's worth the pain to do it. Mandriva I think is RPM "based" - but I really like APT. Ubuntu has a large community footprint - if I have a problem, there is quite a big chance someone else faced it as well. Will it be the same with Mandriva ? Will I find in Mandriva's repositories all the packages I use in Ubuntu ? What gothcas to watch for there ? How about files location - how much it differs when compared to Ubuntu ? And so on.

I use Linux to earn a living so I do not have the luxury to try Mandriva out at the office and see how it goes.

As regarding trying it at home, after reaching a certain age you have (or you should have anyway) more important things in your life to look after (i.e., kids) than learning a new distro. You start seeing your Linux OS more as tool than a purpose on itself - if Ubuntu/Gnome does the job for you, why bother with anything else ?

I younger individual might beg to differ though ...;)

Strictly speaking about Kubuntu now, how much KDE "population" it actually "owns" ? What **if** over the time many kubuntu users migrate to Ubuntu rather then other distro ? The fact that other distros may offer better KDE 4 experience it's great but still bad news for KDE team if those distros end up owning a small piece of the total Linux "market". 

Rhetoric question, I know, but I wonder who initially boasted that KDE 4.0 was ready for masses ? Was it KDE team or Kubuntu ?

Oooops, I think I am digressing from the original theme :roll:

---

### Post by Mehall on 2009-04-24
> **CraigPaleo said:**
> What would you recommend by way of Debian/apt-based distros?

Aside from that, I've always been curious as to why Gnome is faster on some people's machines but not mine. Does Gnome handle multi-cores better? I have a single core sempron and KDE has always been faster. That's the reason I keep it installed but I just can't seem to get used to it.

Install Debian, then install kde. That's pretty much it.

Well... Knoppix and Backtrack both run KDE. Not used Knoppix, but Backtrack is pretty sweet, and Backtrack4 is Ubuntu based.

Oh, and K-DEMar is supposed to be nice, but I ain't used it.


EDIT:

You can install apt in Mandriva, IIRC. Apt-rpm works fine. And almost every distro runs Synaptic these days, so the GUI you use will almost always be the same.

And I don't know who said it. The KDE team certainly made it known it was "release early, release often", so people must have though a major version of 4.0 meant stable (when it's not, that would be equivalent to Revision4 version 0.0 )

---

### Post by NightwishFan on 2009-04-24
Kubuntu Hardy with KDE 4.0 was fairly stable, actually. KDE itself was released as "stable" but it was unfinished. Kubuntu Jaunty is fairly good as far as KDE4 goes, is all. I was surprised.

It keeps up with other distros, but it is true it does not get the attention it deserves. I use Kubuntu sometimes merely because I like the Ubuntu base and release date.

---

### Post by Dragonbite on 2009-04-24
What gets me is there are KDE apps I would like to use but they don't seem to play-nice in Gnome so I'm left with 2 choices[LIST=1]
[*]Jump to KDE (Kubuntu most likely) completely for these apps
[*]Deal with the Gnome/GTK versions when able to
[/LIST]

Or would it be better to try LXDE?

---

### Post by NightwishFan on 2009-04-24
What applications do not work in GNOME. (Just asking)

I have found QT4 apps work great. (And on ubuntu they look Gnome-ish which is great)

---

### Post by Dragonbite on 2009-04-24
> **NightwishFan said:**
> What applications do not work in GNOME. (Just asking)

I have found QT4 apps work great. (And on ubuntu they look Gnome-ish which is great)

[LIST]
[*]KDEnlive crashed on me when I was trying to save a .avi file
[*]Kontact works sort-of, though my purpose of using it is for video chat and it freezes the app when I try and configure that. I know that may not be a Gnome issue but I haven't tried it in KDE yet (planning to).
[/LIST]
Some have worked though
[LIST]
[*]Krita has worked alright from my few test runs
[*]Quanta Plus has worked for the most part
[/LIST]

I haven't tried kPIM (KMail and etc.) yet. I would also like to fool around with Okular because it has some features (text selection) that Evince seems to be missing. 

I don't know which ones are KDE 4 apps and which are KDE 3 apps if that makes a difference. If they look like they fit in, that's kudos plus.

---

### Post by Asteryx on 2009-04-24
I guess each individual will use different parts of KDE, function of their needs.

For me, I can't live without Kate and Konsole. If you remember, the Konsole version of KDE 3 had an option of increasing the spaces between the lines :guitar:. Oh man, those were the days, I loved that feature ... but it's now gone from KDE 4 :( ... always wondered why ...

Dolphin is hmmm ... OK (somehow) but annoying when doing certain tasks. Nautilus seem much more suited for quick jobs. And I like better how Nautilus handles the "bookmarks" compared to Dolphin. Well that's my impression anyway - your millage might vary of course :).

Another think which keeps me glued to Gnome is the fact that I can increase the fonts dpi gradually (as apposed to 96/120 hard thresholds in KDE). I don't know if you can do that in KDE without getting your hands dirty (if indeed possible).

Lastly (I don't want this topic to degenerate into KDE vs Gnome) I might be wrong on this one, but I have always felt that Firefox was always "meant" to be used under Gnome. It's like it looks better and it's more snappier under Ubuntu. I dare to say that even OpenOffice is better integrated with Ubuntu. Or am I hallucinating :shock:?

---

### Post by chucky chuckaluck on 2009-04-24
> **Dragonbite said:**
> What gets me is there are KDE apps I would like to use but they don't seem to play-nice in Gnome so I'm left with 2 choices[LIST=1]
[*]Jump to KDE (Kubuntu most likely) completely for these apps
[*]Deal with the Gnome/GTK versions when able to
[/LIST]

Or would it be better to try LXDE?

you could try something like openbox and just let the apps be what they are. in qtconfig, you can select gtk style and the qt apps will use the gtk theme.

---

### Post by kamitsukai on 2009-04-24
Unfortunately I'd only tried KDE4 on kubuntu till only a few weeks ago until I played around with Mandriva on a friends PC and I was literately blown away it was on the verge of brilliance 

Kubuntu brings a bad name to the KDE desktop....

---

### Post by /// on 2009-04-24
> **kamitsukai said:**
> unfortunately i'd only tried kde4 on kubuntu till only a few weeks ago until i played around with mandriva on a friends pc and i was literately blown away it was on the verge of brilliance 

kubuntu brings a bad name to the kde desktop....

+1

---

### Post by pelle.k on 2009-04-24
> Kubuntu brings a bad name to the KDE desktop....
I've always been a fan of kubuntu, and i certainly don't agree with you. Kubuntu is **THE** distro that got me interested in KDE, and it's basicly the only KDE distro that still interests me apart from pardus.
I did avoid the later 3.5.X releases though, and the 4.1 releases. That had nothing to do with kubuntu really, but KDE.

Kubuntu KDE is very modular, it uses QT equivalent tools to replace GTK eqvivalents where possible (synaptic->adept/kpackagekit, firefox->konqueror, jockey-gtk->jockey-kde, gimp->krita etc etc), and while that may not appeal to the average user, i love that they really strive to keep it "qt". Also, you can't go wrong with a "debian" base system, unless you're into arch that is ;)

Mandriva use a lot of GTK applications in their default KDE setup, and i'm a purist by nature, so that doesn't appeal me very much, even though mandriva certainly is a very good kde desktop. Same goes for pclinuxos. And most other kde distros.

---

### Post by thisllub on 2009-04-24
I hate Nepomuk.
A pointless buggy piece of work that does nothing but spoil the KDE experience.

However KDE4 still crashes for ridiculous reasons like opening widget properties.

I don't mind playing with it but I wouldn't work with it.

---

### Post by hotweiss on 2009-04-25
KDE4 is almost ready... Will give it another go when 4.3 is released. 4.2.2 still had a few annoying bugs.

---

### Post by NightwishFan on 2009-04-25
I personally do not like dolphin. The only feature I like is the easy way to increase icon size.

I find KDE4... cluttered. That is the main reason I do not use it. As far as what I really like about it is krunner. It just seems easier to use than GNOME-Do.

Most of the other features blew me away, I just wish they would focus on making it work more smoothly. Stability/Speed > Coolness. Rather than adding an unfinished or buggy feature, they should just not implement it at all until it is ready, or mark the release unstable. (As they did with 4.0, which everyone still used anyway, -> Fedora).

As for the applications that did not work in GNOME. Kdenlive always crashes. I barely ever get it to work. So no surprise there. The other application I have no idea, just make sure you are not using backports or unstable software. In Kubuntu hardy I installed kdenlive from backports by accident. The regular one worked fine.

---

### Post by Doug77 on 2009-04-25
> **kamitsukai said:**
> Unfortunately I'd only tried KDE4 on kubuntu till only a few weeks ago until I played around with Mandriva on a friends PC and I was literately blown away it was on the verge of brilliance 

Kubuntu brings a bad name to the KDE desktop....

Can you guys elaborate on that a bit for me please?  What's so bad about Kubuntu, and what makes Mandriva better?  

I'm trying to decide between Kubuntu, Mandriva, or Sidux.  I've only tried Ubuntu and Kubuntu 8.10, and I really like the KDE set up.  It looked fantastic, I liked the oxygen theme, I love the plasmoids, I like the bouncing cursor showing me that something was loading, I like the higher configurability, I liked the file browser (is it Dolphin?) more than Nautilus.  

But overall there were too many glitches and bugs: my mouse sensitivity would reset after suspend, my icons in the taskbar would disappear and gnome ones would appear (granted, I had installed Ubuntu 8.04, then later upgraded to 8.10 and then installed the KDE desktop over Gnome), it would crash, dropbox took a lot of fiddling to get working and wouldn't work perfectly, it would do the disk check and reboot and do it again and again, and so on (I had it set up to check the disk periodically on shut down instead of startup).  

So at the moment, I'm thinking of trying either Mandriva or Sidux.  Or trying Kubuntu 9.04, hoping that the new version and a fresh install would solve most of my problems.  

So please, any input would help, what makes Kubuntu so bad in your opinion, and Mandriva or others so much better?

---

### Post by pelle.k on 2009-04-25
> So at the moment, I'm thinking of trying either Mandriva or Sidux. Or trying Kubuntu 9.04
As for myself, i really do encourage you to check mandriva out. Trying new stuff is can only broaden your perspective.
However, remember that intrepid was based on KDE 4.1. It was not mature enough to be the default kde desktop if you ask me. KDE 4.2.2 is the first release in a long time that is usuable (IMHO of course).

Mandriva has the famous mandriva control center (a lot more point and click system configuration than kubuntu), it's own implementation of networkmanager (had 3g connectivity long before networkmanager had it), a streamlined theme (that goes well with GTK apps as well), different streamlined kernels for desktop and laptop computers made by "manbo labs", and top notch hardware recognition.

---

### Post by 3Miro on 2009-04-25
At first I was very disappointed from KDE 4.1, but then looked at it carefully and realized that most of the problems were incompatibility with GTK and I was using some GTK apps.

Then I made the upgrade to 4.2 (when it came out for kubuntu 8.10) and I am not trading it for anything. My reasons to use KDE:

1. Apps such as Kaffeine, Amarok, Dragoon, kTorrent.
2. Kwind and smooth effects (much smoother than compiz)
3. Great integration between the native apps, KDE apps directly interface with each other in a neat way.
4. I was used to FireFox and considered it a minus that I had to switch to Konqueror, but then I realized that except for some eye candy Konqueror is better (stable, light weight, additional security, split screen).
5. Dolphin is great with the split screen options.
6. Network manager sux, installed WICD and had no trouble with it (on the same matter, gnome NM also sux, i.e. static IP is hard to set up, if not impossible).
7. Nice integrated widgets to monitor temperature and CPU usage.
8. Folder view.
9. File watcher.
10. KDE

Everyone that has been hurt by 4.0 and 4.1, give 4.2 a try.

---

### Post by cookieforyou on 2009-04-25
I installed Kubuntu 9.04 (with KDE 4.22) when it appeared and am largely impressed with it.  Firefox crashes occasionally, but I'm not sure whether that's because of KDE 4.22 or Firefox itself.  I haven't (yet) tried Ubuntu 9.04 and Firefox together.

One thing I would like to know is whether Plasma (desktop) IS KDE 4.22, or is it a desktop effect of KDE 4.22, like compiz.

I will be sticking with KDE for now.

---

### Post by SuperSonic4 on 2009-04-25
Plasma is part of KDE 4.2 and has been since KDE 4.0
You can turn a lot of plasmoids off though.

---

### Post by igknighted on 2009-04-25
> **cookieforyou said:**
> I installed Kubuntu 9.04 (with KDE 4.22) when it appeared and am largely impressed with it.  Firefox crashes occasionally, but I'm not sure whether that's because of KDE 4.22 or Firefox itself.  I haven't (yet) tried Ubuntu 9.04 and Firefox together.

One thing I would like to know is whether Plasma (desktop) IS KDE 4.22, or is it a desktop effect of KDE 4.22, like compiz.

I will be sticking with KDE for now.

It is neither... Plasma is like nautilus and gnome-panel rolled into one.  It handles panels and icons and widgets the way those other things do in Gnome.  It is much more than an effect, as it is a fundamental shift in how these things are handled, but there is much more to KDE 4.2.2 than Plasma.

---

### Post by igknighted on 2009-04-25
> **Asteryx said:**
> Used to be a big fun of KDE 3 but migrated to Gnome (Ubuntu) ever since the KDE 4 "upgrade" disaster ... It's not that KDE 4 is inherently bad, it's rather the abysmal way the migration was handled. In my opinion KDE 4 is still not ready and I fear KDE desktop project will pay dearly for their mishandling of this matter (especially for the length of time it'll take to complete the migration).

I feel your blame is placed with the wrong group for the migration fiasco.  KDE devs simply wrote code... they never released a buggy distro.  It is 100% the responsibility of each individual distro to package and release the software it feels best meets its goals.  If you thought that Kubuntu (or any other KDE distro, for that matter) was too buggy, then your complaints should go to the people who packaged and released buggy software.

Unfortunately, in the year+ leading up to the KDE4 release many predicted exactly what happened.  KDE 4.0 was never going to be feature complete, and distros should have known this.  Unfortunately, most of the blame has fallen on the KDE team (rather unfairly, IMHO).  No one is boycotting Mandriva, Opensuse or Fedora for releasing the wrong software.  But many to this day wont touch KDE because of the distro maintainers mistakes.

EDIT: Sorry to DP... completely unrelated topics, thought it should be split

---

### Post by tbroderick on 2009-04-25
> **Doug77 said:**
> Can you guys elaborate on that a bit for me please?  What's so bad about Kubuntu, and what makes Mandriva better?  


Kubuntu has major stability issues for me. KDE would crash daily. Mandriva has been rock solid. No crashes. Same with Opensuse. 

You should try Mandriva out. The latest release, 2009.1, should be out in the next couple of days.

---

### Post by mohitchawla on 2009-04-25
My review, although a smaller one. ;)  (review based on spending less than 2 days with Kubuntu 9.04 !)

**Background**: 

Past Gnome user. Been forever KDE-indifferent, a bit on the disliking side rather. e17 admirer. Happily settled with Openbox (Crunchbang ) presently. Also, playing with KDE 4.2 these days (Kubuntu 9.04), which takes us to the review. 

**Motivation**:

Oh well. The never ending debates on forums & slashdot. The hype etc. And also, KDE being the only environment I haven't really tried or experimented with.

**So, how's it going ?**

It was very refreshing, the first time I saw the desktop. Well what else can one expect with oxygen & all the blue ! :P

Well, Plasma is really cool. I started without knowing anything & was confused about all the widgets mechanism & how anything or everything really worked in KDE. But it wasn't hard out to figure out that everything on the desktop can be arranged simply as widgets...and as the thread starter mentioned, there are a whole lot of those to select from. Also, thanks to the thread starter for mentioning the **Lancelot** widget, I find it pretty useful & convenient. So I removed the panel (as I couldn't figure out and haven't figured out still how to make it transparent) and  arranged the desktop alright, with a few initial configuration issues. Now talking about effects (very cool), I really like them...subtle & easily configurable. Haven't used the applications much except Konqueror & Kopete.

Here's a screenshot.  
[IMG]http://i44.tinypic.com/2i7ofsz.png[/IMG]

Okay, those widgets at the bottom right don't look that weird on my 7 inch screen! (EDIT: They actually do...just made them smaller)


**Conclusion**:
Okay, so not really a review, but thought I'd share anyway. ;)
Apart from a few hang ups ( which I am not sure were caused by KDE or the ext4 file system ), I have been really hooked to this thing and would continue with this for some time to come.  Cheers.

---

### Post by oack on 2009-04-25
> **Doug77 said:**
> Can you guys elaborate on that a bit for me please?  What's so bad about Kubuntu, and what makes Mandriva better?  

I'm trying to decide between Kubuntu, Mandriva, or Sidux.  I've only tried Ubuntu and Kubuntu 8.10, and I really like the KDE set up.  It looked fantastic, I liked the oxygen theme, I love the plasmoids, I like the bouncing cursor showing me that something was loading, I like the higher configurability, I liked the file browser (is it Dolphin?) more than Nautilus.  

But overall there were too many glitches and bugs: my mouse sensitivity would reset after suspend, my icons in the taskbar would disappear and gnome ones would appear (granted, I had installed Ubuntu 8.04, then later upgraded to 8.10 and then installed the KDE desktop over Gnome), it would crash, dropbox took a lot of fiddling to get working and wouldn't work perfectly, it would do the disk check and reboot and do it again and again, and so on (I had it set up to check the disk periodically on shut down instead of startup).  

So at the moment, I'm thinking of trying either Mandriva or Sidux.  Or trying Kubuntu 9.04, hoping that the new version and a fresh install would solve most of my problems.  

So please, any input would help, what makes Kubuntu so bad in your opinion, and Mandriva or others so much better?

Mandriva does for kde what Ubuntu does for Gnome!

---

### Post by Asteryx on 2009-04-27
> **igknighted said:**
>  [...] But many to this day wont touch KDE because of the distro maintainers mistakes.


I fear it will be worse than that as the time goes by. The public general perception regarding KDE 4, as I can feel it now, is that it is cool, looks great, exciting new features BUT don't consider it if you are up to something serious. And changing a "perception" cemented in over a long period of time will be a far harder thing to do than fixing KDE 4 bugs. And it will take time, at least the same amount of time it took for it to settle in.

Ironically, I think every new release of a KDE 4 based distribution (kubuntu 9.04 included) "which is not there yet" and silently advertised as "complete" , does nothing more than hardening the above perception into casual user's mind.


> **igknighted said:**
> I feel your blame is placed with the wrong group for the migration fiasco. [...]


You may be right here although ... I am wondering who were the first to advertise to the masses the initial KDE4 version as 4.0 ? Was it the KDE devs or the distros ? The reasons for doing so instead of naming it like alpha-NN, 3.NN, etc. to highlight its true development status, or whatever that 4.0 figure meant are of little importance now. What matters is that whoever party stubbornly did it fought a "general perception" of what ".0" it is thought it should be - and they lost the battle big time (I'd say the chances of winning it were zero anyway). And we see the consequences now.

So if I were "kubuntu", I would actually rename version 9.04 and any further versions as "beta" for as long as necessary until KDE 4 is really really ready. I do not think that will turn users away from it but rather it will go a long way towards changing peoples mood about Kubuntu and KDE 4 in general.

My 2 cents.

---

### Post by infoseeker on 2009-04-27
Kubuntu 9.04 with KDE 4.2.2 ROCKS. Well done guys. MUCH better than SUSE 11.1

---

### Post by Firestem4 on 2009-04-27
I've gotta say that Kubuntu 9.04 is a big improvement over 8.10. While 9.04 in itself isn't a remarkable upgrade; the stability, performance, and polish of K9.04 is very good. Much more so than 8.10 was.

Kubuntu 8.10 was the first Linux/KDE distro that I used. Since then I am a huge fan of Chakra (Arch+KDEmod). While KDEmod is fantastically better than Kubuntu, I really like the improvements the Kubuntu team has done to 9.04. They are stepping it up compared to before.

So far the only issue I have had with 9.04 is a coding error related to KDE4.2.2 (problem exists in other distro's).

---

### Post by samira455 on 2009-06-17
I am working with kubuntu 9.04 and I enjoy it but sometimes my task manager and what is in it become very slow for example the application launcher takes at east 2 second to sets its content! and switching between 2 windows take a lot time to complete and switching between 2 windows in konsole takes at least 2 seconds.
would you please tell me why this happen? and how can I solve this?

---

### Post by oobuntoo on 2009-06-17
I've been using Kubuntu since 2005. The only release that I totally skipped was the 8.10 version. I've had my share of complaints about Kubuntu, mostly about small but persistence annoyances that I kept seeing release after release. Since I've been using Kubuntu for so long, I know work-arounds for most of these annoyances. From time to time, I would hear people say that KDE implementation on distro x or distro y is better than KDE on Kubuntu and I would check them out. Recently, I've tried Arch Linux 64-bit, with both KDEMOD and the official KDE repo, for about a month. I am now back to using Kubuntu again.

So, what's my point? As always, grass seems greener on the other side of the fence. Every other KDE distro that I've tried have their own annoyances as well as the things that I like. For example, Arch Linux installation and setup involve too much manual intervention, not ideal for inexperience Linux users. After, I've setup every thing the way I like and a few system updates later, few thing started to break. Amarok would not start anymore. When I started Dolphin, or any apps, as root, I couldn't access any file. I also found Ubuntu community/forum to be vastly superior when I needed help.

There are things I really like about Arch. First of all, it's a rolling release. Pacman pakage manager is simply awesome; very fast. The packages are mostly up to date; Kernel, nvidia proprietary driver, etc... If you are someone who doesn't mind manual intervention, the installtion and setup procedure actually give you more insight on how Linux works.

So next time you hear someone says that distro x's or y's  is better than Kubuntu's KDE, take it with a BIG grain of salt. You'll find that other distros have their own kinks. This is a fact of life in the world Linux.

---

### Post by automaton26 on 2009-06-17
I agree that "the grass is always greener".

After investing time in working out how to customize Kubuntu, and how to work around certain problems, I'm happy that it is now sufficient for me to do the tasks I require. And that's all a computer is for me - it's just a tool, and life's too short etc.

I was impressed in the improvements from 8.10 to 9.04, but I'm not changing anything again, at least until the next LTS has been out for a few months.

---

### Post by NightwishFan on 2009-06-17
You probably should start your own thread, however I will give you a quick rundown.

1. Disable desktop effects by pressing shift+alt+f12. You should notice when they are disabled. Is the system more responsive? If so then you may have a problem with your graphics card. If it is an Intel card, then performance may improve soon, if ATI, make sure you have the ATI drivers installed. If Nvidia, you may just have an old card. Please check your system specs. EDIT: You can also go into Ubuntu recovery mode when you boot up. If it is not visible you have to press esc when it says. Then repair the xserver there.

2. Insert the disk you installed Kubuntu with in the drive, and run this command.
```
cd /media/cdrom0 && md5sum -c md5sum.txt
```
If it shows errors, please reburn the disk and install with a new one. That may be the source of your problem. If it shows nothing, and just lists files, then your disk is fine.

3. If the above two do not work, please find out your system specs by installing kde system info, hardinfo (prolly best option), or perhaps run the command:
```
sudo lshw
```

After you find the system info, post a new thread and answer any questions there. Good luck sir!

---

### Post by WheelsOfSteel on 2009-09-27
I didn't read all the messages, but did enjoy NightWishFans opening post.

It's often the case that I and others only post when they have a problem, this time I am pleased to say this isn't the case.

After a clean Jaunty install onto my HP DV7 yesterday, I just wanted to mention that I was very impressed with the results.

Obviosly, it's early days and having had the audio issue with my previous 8.10 install, I was prepared for that one which seemed to be the only issue.

I even expected the network widget to have issues, but no.  Connected to my hidden wep network without issues and without the need to have knetworkmanager assist.  (I updated an older HP 5125(?) a few weeks earlier and had to install knetworkmanager to get it working.  That machine does have the notorious Broadcom chip-set though).  

Not a huge fan of the constant prompts from the wallet, and after I turned it off the network lost it's password and didn't seem to be able to store it.  Need to play around with that one.

Ext4 was my filesystem of choice.  Didn't really do any research before-hand, but figured I would give it a shot.  No problems as yet.  I try to have my user files on other disks or at-least duplicated, so when it comes to upgrades it works out easier.  Plus, my regular tar backup's make relatively easy work of restoring things.  In for a penny...

Stability wise, compared to 8.10, i'd say better.  On the previous release I had to jump into the command line at boot-time to change KDE setting to get it to come-up a few times. Simply because I added an available widget that didn't seem to like my set-up.  As said, early days but have added various widgets and she still comes-up - which is nice.


I did notice more the Thunderbird email client cpu issue.  I wondered what app needed >80% cpu, then killed Thunderbird and got my answer.  

As I tend to mainly use imap and just dupe the emails locally, I can live with just firing it up now and again.  I have decided to use the email feature of Opera, which I am going to give more of a go.  Prefer the interface more than Firefox, but always had problems with the Flash plugin.  Not this time and with the help of Automatix, it now works.  (Gota have my BBC Radio 4)

Performance also seems better, but not huge.  Will keep an eye on this as I do allot of heavy simulation work using mySQL, but need to restore the db's.

Anyway, I could go on, but just wanted to say that I was impressed with the install to my HP dv7 laptop and I will stay with KDE as I much prefer this to GNome, but do run Gnome on some of my servers + NXServer/Client.  Great combination.

Not sure how I feel about the 6month release cycle though?

---

### Post by NightwishFan on 2009-09-28
I was a very big KDE fan when I wrote this, and in the few months since I actually use GNOME now. I do respect and like the Kubuntu teams work on KDE, I hope they get more attention. Though I doubt I will use KDE in the future.

---


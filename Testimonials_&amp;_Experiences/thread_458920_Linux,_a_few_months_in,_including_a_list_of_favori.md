---
title: "Linux, a few months in, including a list of favorite points."
date: 2007-05-30
forum: Testimonials &amp; Experiences
---

### Post by Intertricity on 2007-05-30
Feisty Fawn has proven to be the breakthrough version of Linux that has finally enabled me to experience what this OS set has to offer. I installed within a few days of its official release, and being pleasantly surprised to get most everything working out of the box, I've been able to delve into deeper layers of expertise at my own pace.

I must make a quick note that this would not have been possible without the wealth of programs offered to the console user out of the box. Programs like cal and fortune are pre-installed, waiting the curious newbie. Other useful utilities lay dormant in wait for their discovery and utilization, quietly patient until the user is ready to take advantage of them.

A thing I've learned about Linux is that when you finally learn how to do something with it, you can automate it, connect it to something else, or apply its concepts to Windows to get what you want.

Here is a list of things I've come to love about Linux- but it must be noted that above all, by far, the most useful and important application I've come across in Ubuntu itself is apt-get, which has made all of my Linux progress possible:

**1. Vim.**
I've been using vim since my days of being too lazy to FTP things to my server. Having it handy via the console makes keeping personal notes even more of a crucial utility. Its ability to utilize make also makes for a great programming environment.

**2. Crontab**
It is there when I go to sleep, to turn off XMMS off after an hour. It is there to wake me up in the morning to the gentle melodies and dialogue of my favorite movie in VLC, at just the right scene. It is my dependable reminder, calendar, and necessity.

**3. Config files**
Although cryptic at first- should the system go down at any time, saving my xchat, gaim, firefox, etc. settings is as simple as saving the .* files in my home directory.

**4. GIMP**
After getting my wacom to work in Linux, I've discovered that GIMP is every bit as capable as photoshop for what I require it to do. Not only this, but I will never need to worry about losing an official CD ever again. Freedom from CD's! What a concept.

**5. Virtual Desktops**
Where would I be without Ctrl+Alt+Left/Right? At one point I thought this a silly extra, it soon become perhaps one of my most favored desktop utilities. Many times I will want to examine a file I've saved to the desktop, but not wish to touch or minimize any of my current open windows. Using another virtual desktop performs all the actions of "show desktop" but in a much more useful way. Not to mention its handiness in its ability to compensate for not having a second monitor. I'd feel boxed into a desktop without this feature.

**6. SSH**
Sometimes a friend will borrow my laptop to browse something. I get loads of fun by SSH'ing into it, and opening all sorts of random pictures onto the screen while they browse. Oh yeah, it's also an effective way to administrate a computer I can't reach, that part's nice too.

**7. Calendar**
The calendar that can be made to appear in the top right corner of gnome by simply clicking on the time stamp button is a wonderful little widget. At first I thought it was annoying that I had to click it yet again to make it go away- but the beauty made itself apparent whenever I needed to keep that calendar open while working in another application. It turns out keeping the calendar on the top was a good idea after all.

**8. XMMS**
Need my winamp fix, this fixes it. =)

**9. The Console**
I think the console revolutionized my whole way of computing. My friends are horrified at the console, but I see it for its sheer beauty and power. I sometimes find myself trusting console programs more than gui programs, having this feeling that the simplicity of the console lent its programmer more time to work on quality of function rather than quality of gui. By the way, let us not forget the usefulness of screen ^_-;;

**10. Shell Scripts**
Having edited a few shell scripts for my own purposes, for example an FTP script that uploads anything I want to a particular directory on my server, I've found that script uncannily handy to share pictures with friends on a moment's notice by typing "./upload picture.jpg" rather than opening a client. "./remove picture.jpg" lets me take that picture down just as quickly if that picture was for a few eyes only. Other shell scripts may be automated and chained to crontab to truly realize the advantages Linux has to offer.

These are only a few luxuries I've come to enjoy using this operating system. Every small battle is an intellectual enlightenment of understanding and appreciation. Although I dual-boot, I use Windows mainly to play games and to deal with matters of schoolwork that must be completed on a Windows system. I have no problems with dual-booting, there is no passionate issue between using either or for me. I simply prefer the luxuries and freedoms offered to me by Linux, and use Windows when I think it is appropriate or practical.

---

### Post by 3rdalbum on 2007-05-30
Wow, you really are getting into the system! Two tips for you:

There's a graphical program called gCronTab - you might have to compile from source, but it's a graphical frontend for your Crontab.

Or, if you just want to set a one-time command (i.e. "This file apparantly will take 3 hours to download, I'll tell my computer to switch off in 4 hours"), you can use the "at" command:

```

sudo at now + 4 hours
halt

```

Press Control-D after you've typed the commands you want to schedule. The "atq" and "atrm" commands may come in useful too - check out their man pages.

---

### Post by Intertricity on 2007-05-31
Ooh, that at command looks handy, thanks!

---

### Post by Geekkit on 2007-05-31
Nice to see your feedback/experience. I too find 7.04 to be the breakthrough distribution of Ubuntu and in fact Linux in general. I've been waiting for this moment for a long long time. To be able to make use of my hardware and to also have a feeling of peace knowing that no monkey business is going on is too good to be true.

For me, I echo your favorites and append to them the following:

**Font rendering**
Ever since Gnome started using Cairo for rendering I've noticed an improvement that is really hard to top. I look back on threads in various forums from, say, 2004, where you will find complaints of cheesy font rendering on the screen. I've said it before and I'll say it again: UBUNTU/LINUX/GNOME FONT RENDERING IS STUNNING! ABSOLUTELY BEAUTIFUL!

**Media Support**
Download your favorite CODECS (no harder than Windows either) and you can stick with two programs to listen/view media: Totem for ALL videos (WMV, MPEG, AVI, Quicktime) and RhythmBox for all music including streaming.

**Stable**
I cannot stress this enough. This is the most stable version/flavor of Linux/Ubuntu I've ever tried. Actually I even got 7.04 running on an old IBM Thinkpad which really blew my mind since it's over five years old

**This Forum**
I remember the "good ol' days" where you would read through man pages, Web pages, and spend hours of tweaking and fiddling only to come up short and not know how to fix/install something. A post in a newsgroup would yield hollers of "RTFM!!" where you'd try and remind those that read your two page post about how much time you did in fact spend trying to make it work. These forums are the blood of Ubuntu. I've found more answers looking in here than anywhere else. Even if I do a Google search, inevitably the link always winds up here.

I'm still on 7.04, I've been performing tweaks of all kinds, installing/uninstalling software and have not had any trouble. I'm still blown away by how little memory I'm actually using from RAM. Oh yeah, if you haven't already tried, download Frozen Bubble ... it's bloody addictive - and it's a very polished game!

;)

---

### Post by bobbocanfly on 2007-06-01
> **3rdalbum said:**
> Wow, you really are getting into the system! Two tips for you:

There's a graphical program called gCronTab - you might have to compile from source, but it's a graphical frontend for your Crontab.

Or, if you just want to set a one-time command (i.e. "This file apparantly will take 3 hours to download, I'll tell my computer to switch off in 4 hours"), you can use the "at" command:

```

sudo at now + 4 hours
halt

```

Press Control-D after you've typed the commands you want to schedule. The "atq" and "atrm" commands may come in useful too - check out their man pages.

Thanks for that one! Will help so much with downloading movies with this rubbish connection

---


---
title: "Hello World!"
date: 2007-02-25
forum: The Cafe
---

### Post by sylathnie on 2007-02-25
I just thought I would introduce myself before I start bothering you all with lots of questions.
I'm a long time MS user (DOS->Vista) but I am intrigued by the customizability of linux. I have purchased a book and am trying to get Ubuntu installed and working on my main PC. So far it has been nothing but problems but I am determined to get it to work. It's taken me almost a week of fiddling and such to get the graphical interface to display (that's gnome right?) Now on to the next problem Linksys WMP54G v4.1 wireless adapter! Hopefully my next post will be from Linux rather than from windows. (After I print the 9 page NDISWrapper wiki in an attempt to install some drivers.)
I will give it to you folks. You certainly know how to make an experienced computer geek feel  like a newbie all over again. Nobody writes a cryptic how-to like a linux user.

Looking forward to picking your brains!

Sy

---

### Post by fuscia on 2007-02-25
> **sylathnie said:**
> I will give it to you folks. You certainly know how to make an experienced computer geek feel  like a newbie all over again. Nobody writes a cryptic how-to like a linux user. 

when i first started using linux, i really did miss people assuming i was an idiot and asking me if my computer was turned on. you'll get it.

---

### Post by roderikk on 2007-02-25
Not that I had as much trouble as you did, but I felt about the same. As long as you assume it is like learning a new language, conceptually completely different, you'll be ok in the long run. I am really glad I made the switch and would never even consider going back.

Welcome to the club!

---

### Post by chrish670 on 2007-02-25
> **sylathnie said:**
> I just thought I would introduce myself before I start bothering you all with lots of questions.
I'm a long time MS user (DOS->Vista) but I am intrigued by the customizability of linux. I have purchased a book and am trying to get Ubuntu installed and working on my main PC. So far it has been nothing but problems but I am determined to get it to work. It's taken me almost a week of fiddling and such to get the graphical interface to display (that's gnome right?) Now on to the next problem Linksys WMP54G v4.1 wireless adapter! Hopefully my next post will be from Linux rather than from windows. (After I print the 9 page NDISWrapper wiki in an attempt to install some drivers.)
I will give it to you folks. You certainly know how to make an experienced computer geek feel  like a newbie all over again. Nobody writes a cryptic how-to like a linux user.

Looking forward to picking your brains!

Sy Welcome Sy, 

On stepping away from MS products...theres certainly a lot to unlearn here. Where I was too used to Windows solving most of my config problems on the fly, now - I'm being forced to think about how to set up and configure a device to get it up and running. (arrrgh! pulling hair out.) Right now I'm also stuck configuring a linksys wireless card to work on my Toshiba laptop.  Sure theres plenty in print here in the forums about this particular card (id'ed as a Broadcom 4318 (air force one)), but because everyones PC configs are different, it is going to take a couple of weeks of reading to get mine deployed and  working correctly.  Unlike MS theres no 5 min wizard fixes here. Welcome to the world of Linux.. heh

---

### Post by adam.tropics on 2007-02-25
> **sylathnie said:**
> You certainly know how to make an experienced computer geek feel  like a newbie all over again. Nobody writes a cryptic how-to like a linux user.

Looking forward to picking your brains!

Sy

It's a journey, but a worthwhile one.

---

### Post by TheWizzard on 2007-02-25
don't reboot!

---

### Post by darkhatter on 2007-02-25
learning to program ew

---

### Post by Daveski on 2007-02-25
> **TheWizzard said:**
> don't reboot!

I agree with this. Most Windows users seem to have fully accepted that everytime they change something they need to reboot - even if the OS does not tell them they need to. I love figuring out what I need to do to get something working without the catch-all reboot. A good example was me stupidly pulling out the PS/2 mouse connector. I figured out how to stop and restart the mouse driver (without using the mouse) to get my mouse working again without having to reboot.

---

### Post by Sammi on 2007-02-25
> **sylathnie said:**
> Nobody writes a cryptic how-to like a linux user.
That's not necessarily true. Aysiu(a moderator and user of this forum) has made some great easy to read Ubuntu installation and configuration  instructions: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You should check them out. He has also written a great essay for new Ubuntu users who are eager to learn/unlearn, named "[The Linux Desktop Myth]("http://www.psychocats.net/essays/linuxdesktopmyth")".[]("http://www.psychocats.net/essays/linuxdesktopmyth")

---

### Post by DarkN00b on 2007-02-25
Welcome sylathnie! 

With that Linksys card you've got... I just got the same card today (except it is a ver.3 )!

If it uses the Broadcom (BCM43xx ) chipset then definitely use the how to [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"). It worked perfectly for me.

To check your chipset type, open a terminal and type
```
iwconfig
```

Here's what mine looks like:

```
 eth1      IEEE 802.11b/g  ESSID:"*****"  **Nickname:"Broadcom 4318"**
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:49:22:3B:06   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=43/100  Signal level=-58 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Native Ubuntu support without ndiswrapper.

Check it out anyway and good luck!

---

### Post by sylathnie on 2007-02-25
Ironically I do most of my rebooting to get back to windows so I can download things and ask questions on these forums. Sooner or later I will get my network card working and then maybe I can try and do something with Linux besides simply trying to get it to work.

One question, and I'm not trying to be negative here. (I want this to work). Does it ever stop being a battle to get things to work? So far I've just run into roadblock after roadblock to getting my system even doing the most basic tasks. I don't mind a little work to make things function in favor of having more control over my system but if every new piece of hardware I install is going to involve downloading 5-6 files and 1 week of research I'm not sure if I have the time to be a linux user. (That and I don't think I can afford the printing costs of keeping all the how-tos and suggestions around to try out)

Ok </rant> as long as every stays as helpful as they have been I'm sure I will get it figured out sooner or later.

Rebooting... going back to linux to try to get the network card working.

Thanks for the welcomes and encouragement all!

---

### Post by DarkN00b on 2007-02-25
Adding new hardware can be a pain if you don't do your homework before buying it. After your first install or two, you learn what you need to do from then on. It really isn't much harder than Windows once you learn how, its just a different process.

Edit: OOPS -- Installing Ubuntu is a lot easier than installing Windows. Tweaking is a longer process because Ubuntu is so much more customisable. Once you learn the process of getting a smoothly working system going, it becomes easy. All it takes is knowledge - just like windows.

---

### Post by maniacmusician on 2007-02-25
Yup, it does get easier. My first time was a nightmare as well. As time goes on, you figure out what works and what doesn't; sort of like you had to the first time you used Windows.

You may also have to make some changes to your hardware configuration, if you have absolutely incompatible hardware. You seem to have been very unlucky regarding hardware (most of my stuff worked), or it could be that you just haven't got used to the linux way of doing things yet.

---

### Post by FuturePilot on 2007-02-25
It's definitely worth learining. I'm so glad I'm using Ubuntu as my main OS. It's so much better. It does help getting a couple installs under your belt because then you learn what you did right and what you did wrong. Just don't get discouraged and keep at it. That's the best advice.

---

### Post by adam.tropics on 2007-02-26
> **sylathnie said:**
> Ironically I do most of my rebooting to get back to windows so I can download things and ask questions on these forums. Sooner or later I will get my network card working and then maybe I can try and do something with Linux besides simply trying to get it to work.

One question, and I'm not trying to be negative here. (I want this to work). Does it ever stop being a battle to get things to work? 

Hey, just keep a notebook and pen handy while you're starting out, and so long as you're 'willing' to at times look at things from a new point of view, then yes, it will get far easier over time. Not too much time either.

You may find that you have a couple of experiences while new, where you tweak the thing to within an inch of its life, then step over the edge, and end up doing fresh installs. Like anything else, they get a hell of a lot quicker if really needed. But please keep backups. Linux is very safe, and a pleasure to use, once you're used to it, but things can and will go wrong in the interim. So for heaven's sake keep personal stuff backed up, and all will be fine.

---

### Post by The Noble on 2007-02-26
One important thing to remember is that there are literally guides for _whatever_ you need, just google or search the forums. Also remember that we are all willing to help you whenever you need it, so don't hesitate to ask. Also, don't worry! That overwhelming feeling after moving to linux only lasts a month or two until it is replaced by a feeling of freedom, so just hold on and enjoy the ride!

Edit: You will see that linux has a big differene compared to windows in the reasoning and logic solving department. I'm sure everyone that uses windows know how to solve a problem by a reboot (hah!) or reinstalling over the software, but what separates real users over masters is the insight to find and fix the problems (and not masking it). Linux is all about your power, so just remember that you own that bloody computer in front of you; don't let it win!

---

### Post by TheWizzard on 2007-02-26
> **sylathnie said:**
> 
One question, and I'm not trying to be negative here. (I want this to work). Does it ever stop being a battle to get things to work? So far I've just run into roadblock after roadblock to getting my system even doing the most basic tasks. I don't mind a little work to make things function in favor of having more control over my system but if every new piece of hardware I install is going to involve downloading 5-6 files and 1 week of research I'm not sure if I have the time to be a linux user. (That and I don't think I can afford the printing costs of keeping all the how-tos and suggestions around to try out)


no worries! 
i'd advice you to make installation notes. and use the command line as much as possible! the history command is very useful in order to track down what you did the last time. and backupt the /etc folder. here al you configuration files are stored en may give hints how to configure your next install!

---

### Post by ironfistchamp on 2007-02-26
With regard to the battle to get things to work, I have frequently won the battle. I will get things working just as I want and think "Hmm now what?" 

The answer is to find something that breaks your computer and have a whack at fixing it. 

One thing I love (I mean I absolutely adore it) is the fact that a fresh install, although hardly ever necessary, is easy and damn quick. Recently I borked my half-hearted attempt to intsall KDE on my Ubuntu Edgy. I somehow managed to make GNOME display light grey areas (say #EEEEEE-#CCCCCC) as very dark grey (similar to #666666). Had no idea but within about 30mins I had downloaded and install Feisty herd 4. With Windows I had to install XP twice in a day and each took me roughly 3 hours each. 

Erm I forgot my point. Nevermind.

Ironfistchamp

---


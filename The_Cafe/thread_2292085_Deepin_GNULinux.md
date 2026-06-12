---
title: "Deepin GNU/Linux"
date: 2015-08-25
forum: The Cafe
---

### Post by Welly Wu on 2015-08-25
I am trying to get my VMWare Workstation 11.1.0 64 bit GNU/Linux software product to install Deepin 14.3 64 bit GNU/Linux in a guest virtual machine, but it does not boot off of the ISO file. Does anyone here know what is going on here? How can I try this in a guest virtual machine successfully?

---

### Post by Welly Wu on 2015-08-25
Nevermind. I downloaded it again from Mega and it works. Sorry, but I had a bad ISO file.

---

### Post by Lars Noodén on 2015-08-25
I don't see any links to torrents on the download page, I can't read much there, but if torrents are available I would use them.  Torrents are better because of the built-in error checking so the need to manually check the SHA256 or MD5 hash is eliminated.

---

### Post by Welly Wu on 2015-08-25
I successfully installed Deepin 14.3 64 bit GNU/Linux in a guest virtual machine and it takes forever to download updates from The People's Republic of China. At first blush, it appears to be quirky and the English language is not their forte. It looks and feels like a toy desktop operating system. It is visually attractive and it comes with unique software packages, but it sure feels like a toy with which to play. It is fairly easy and simple to learn how to use and I like the welcome screen that teaches new users to the basics of how to navigate the desktop environment and window manager. What exactly makes Deepin so special if I dare ask?

---

### Post by Welly Wu on 2015-08-25
I finally figured out to launch the Deepin Store to change my download mirror. Now, it's much faster. I installed VMWare Tools successfully. This seems to be a semi-polished GNU/Linux distribution, but there are some rough edges around the corner still lurking. I find it to be an odd distribution even though it is based upon Ubuntu 14.04.x 64 bit LTS GNU/Linux. Give me more time to figure this one out on my own.

---

### Post by QIII on 2015-08-25
Looks like it was designed by ToysRUs.

---

### Post by RichardET on 2015-08-25
What else are you running as a VM?

---

### Post by Welly Wu on 2015-08-25
Right now, I am running OpenSuSE 13.2 64 bit, Elementary OS "Freya" 64 bit, Linux Mint 17.2 "Rafaela" 64 bit, PC-BSD 10.1.2 64 bit, Deepin 14.3 64 bit, and I plan to include OpenBSD 5.7 64 bit later this week. I am also interested in Netrunner OS 16 "Ozymandias" 64 bit, but I need to do my research. I follow Infinitely Galactic on Google's YouTube and I watch his videos about various GNU/Linux distributions and I give it a go myself using VMWare Workstation 11.1.0 64 bit. I'll give Netrunner a try on Friday or this weekend. I'm more interested in Deepin right now, but I'm having a problem activating the hot corners feature. It doesn't seem to work well.

Deepin has a lot of unique features that aren't fully baked. The Deepin Store keeps telling me that upgrades are taking place, but it seems to get stuck and it doesn't tell me the status of my last upgrade. The hot corners don't seem to work well either. The Deepin Store is full of software packages that come from the Ubuntu Software Center, but the Deepin apps themselves are not truly groundbreaking. There seems to be a reliability problem with getting the some features to work. When I installed Deepin, it detected VMWare Workstation and it told me to install it bare metal for the best experience. It has a pretty user interface, but the English language version does not communicate well and it is a bit confusing to figure out the imperfect English translations to get features to work.

---

### Post by RichardET on 2015-08-25
I have tried to like PCBSD;  I just can't make myself like it;  If one wants FreeBSD, then do take the time to install the base OS, and add desired packages separately;  the result will be much better.

---

### Post by Lars Noodén on 2015-08-25
> **Welly Wu said:**
> and I plan to include OpenBSD 5.7 64 bit later this week

I'm guessing that'll be 64-bit x86 (aka amd64) not any of the other 64 bit architectures ;)
OpenBSD is nice in that it does nothing that you didn't specifically tell it to do.  But things have moved on quite far since 5.7.  If you are interested in trying the latest, then I would go with the snapshots instead.  It has a shorter, faster development and lifecycle than most other OSes.  The snapshots are where the active development is.  You might also try [BitRig](https://github.com/bitrig/bitrig/wiki/Faq) which is forked from OpenBSD.

---

### Post by Welly Wu on 2015-08-25
PC-BSD 10.x 64 bit is nice, but I can't figure out how to get my VMWare Tools to work. The guest display automatic resizing feature doesn't work. I have to set it to 1440 X 900 pixel resolution. Does anyone know how to fix this issue so the display will resize itself automatically using VMWare Workstation 11.x 64 bit?

I played with Deepin and it seems to be pretty shallow. The Deepin Store is a rebranded Ubuntu Software Center. The Deepin apps remind me of the Elementary OS "Freya" apps, but Freya has more polish and it is more usable. Deepin is designed for the Chinese market and it clearly shows. There are not a whole lot of unique apps other than Codeweavers CrossOver which I already paid for. It's going to take me some time to get this guest VM up to my standards.

PC-BSD is much more interesting than Deepin. The warden and jails features are cool, but I need to read the official manual to learn more about them. It seems that updating PC-BSD takes a longer period of time because it removes a bunch of software packages and then adds the latest new versions to replace the old ones and this is time consuming. There are not a lot of software packages in the App Cafe either. It seems pretty sparse. I a committed to learning more about BSD UNIX and getting my knowledge, experience, and skill sets up to par with GNU/Linux. I enjoy using PC-BSD. It is very interesting and fun.

I would not switch to PC-BSD in the future though. I'll stick with the latest Ubuntu 64 bit LTS GNU/Linux as my primary desktop operating system. It just works and why break it?

---

### Post by RichardET on 2015-08-25
I find that OpenBSD is highly superior to PC-BSD within a VMware VM.  You don't to install vmware tools with OpenBSD;  I would go with OpenBSD, dump PC-BSD.

---

### Post by Welly Wu on 2015-08-25
I'm keeping PC-BSD 10.x 64 bit for now. I need an easy to use BSD UNIX desktop operating system that is safe to learn more about it. OpenBSD is coming later this week. It is for more advanced BSD UNIX users and I need to read the official manual very carefully to learn how to install and use it. I plan to keep both BSD UNIX desktop operating systems within VMWare Workstation 11.x 64 bit for a long period of time. These are my learning projects. I don't know much about BSD UNIX not even the rudimental basics. I have a lot to learn and it will take me several years before I am comfortable using both PC-BSD and OpenBSD. I am so new that I don't even have a preference yet.

Deepin is kind of disappointing. It's mostly glitz with little substance. I won't delete it, but I will continue to learn more about it. It just does not impress me as much as Ubuntu. It's okay to hand to a child or teenager who wants to learn more about GNU/Linux, but it lacks enough customization and flexibility for me to use it for too long. It sort of has an Apple Macintosh OS X Yosemite 64 bit look and feel to it similar to Elementary OS "Freya" 64 bit. Freya is in my opinion to be much more polished and stable. It is well engineered and tested. It's kind of simple and basic for my needs, but it is an undoubtedly high quality software project. Deepin doesn't have any of that. It merely gets by and it does not show anything unique. Behind the pretty facade, there is not much inside of it to make it worth installing bare metal on my desktop PC.

---

### Post by brad-bogar on 2015-08-25
I gave Deepin a try and it is very poor indeed. The crossover app crashes and lags when trying to run a very simple app (radmin) and the networking breaks repeatedly even with a properly setup smb.conf. Not for me.

---

### Post by Welly Wu on 2015-08-25
So, it's a dud huh? I guess I won't spend too much time getting it up to my own standards. Oh well.

---

### Post by portalhavoc on 2015-08-25
> **QIII said:**
> Looks like it was designed by ToysRUs. 

LOL! It kind of does! 

"I don't want to grow up, I want to be a Deepin kid!" :P :lol:

---

### Post by Welly Wu on 2015-08-30
It's not terribly good, but it's not awful now that I have been using it for a few days. The Deepin Store is unique with its own apps, but they are rather shallow and limited. You'll need to depend on the Ubuntu software repository for the majority of your software packages. The number of mirrors worldwide closely track the Ubuntu standard mirrors and the Deepin Chinese mirrors are awfully slow if you live in the United States of America. The user interface is like a toy, but it has a visual charm that looks clean and modern. The hot corners do activate, but I need to hover and click on the lower left and lower right along with top left hot corners to trigger functions. I like the ability to organize multiple desktop application shortcuts into one like putting a bunch of toys in a box when it's time to clean up your room. I have never seen that feature in any other GNU/Linux distribution and it could be useful in limited usage case scenarios. The English translation is passable, but it is clear that the Deepin team are not native English speakers like myself with an English degree. It is wickedly fast. Boot up and shut down times are insanely fast. At its core, it just does not impress. It's a bit hollow on the inside. This is mostly cosmetic stuff that constitutes the Deepin brand.

I will keep using it because it reminds me of what I already took for granted with Ubuntu 64 bit LTS GNU/Linux. Comparing these two directly against each other is not fair, but there are a few similarities. For those of you who knocked Canonical, Ltd. for creating the Ubuntu Unity desktop environment and window manager years ago and came back to it, try Deepin 14.3 64 bit GNU/Linux and I dare you not to get angry if not downright hysterical. It's a joke. It's a featherweight. Power users need not apply. Deepin is one of the biggest disappointments that I tried thus far, but that is its intrinsic value. It is a teachable lesson in how to create, build, grow, and maintain a major GNU/Linux distribution by not doing what the Deepin team did. Sometimes, you have to learn from your own or other people's mistakes and failures to grow up.

I tried to add and install the Tualatrix Ubuntu Tweak PPA and software package and Deepin warned me that it will break the OS if I continue. So, that tool is no longer available which nullifies its utility for me.

---


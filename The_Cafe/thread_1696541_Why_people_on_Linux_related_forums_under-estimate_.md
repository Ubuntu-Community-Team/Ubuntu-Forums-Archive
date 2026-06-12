---
title: "Why people on Linux related forums under-estimate hardware"
date: 2011-02-27
forum: The Cafe
---

### Post by asifnaz on 2011-02-27
I have seen many times on different Linux related forums people come and ask for Linux distros for their older PC's .

I have seen many times people ask like :

suggest me a distro for my old PC which is a Pentium III 1Ghz with 512 ram ......

and people without any clue start shouting...

Slitaz , DSL , Puppy Linux etc 

I dare to say that hardware above mentioned (P III 1Ghz with 512 ram ) can run almost any modern Linux distro .

I am running Debian 6 on P III with 256 ram ( I use 512 mb as swap ) without any problem .

why do the people under-estimate old hardware .

I wonder how many of you tried to run Linux ( specially Debian ) on old hardware

---

### Post by snowpine on 2011-02-27
I agree that Debian is an excellent choice for older hardware. That doesn't mean SliTaz and Puppy *aren't* good choices, though, and other forum members have every right to recommend *their* favorites without being called "clueless." :)

(I agree that DSL is no longer a good option due to its current lack of support.)

---

### Post by NightwishFan on 2011-02-27
Ubuntu and Fedora I never had much luck with on older hardware. They are not slow, but not the fastest. I can barely get Ubuntu 10.10 off the ground on 386mb of RAM, but Debian on the same hardware works well. Of course I could just use a lighter WM on either.

I think Debian might be compiled more conservatively or something and that is why it works better on older hardware than more forward facing distributions. I will have to ask about that on one of the mailing lists.

---

### Post by asifnaz on 2011-02-27
> **snowpine said:**
> I agree that Debian is an excellent choice for older hardware. That doesn't mean SliTaz and Puppy *aren't* good choices, though, and other forum members have every right to recommend *their* favorites without being called "clueless." :)

(I agree that DSL is no longer a good option due to its current lack of support.)

I am not saying Slitaz or Puppy Linux are bad . I am just saying that many people assume that a bit older hardware can only handle that light weight distros .

My point is you can use old hardware (anything like Pentium III with 512 mb ram ) for almost any modern linux distro

---

### Post by Slave2Metal on 2011-02-27
Some users just don't know, because they've never tried.  I did try installing ubuntu on a P4 1.3ghz and 128mb of ram.  Ask me how it ran?  It wouldn't even load and I later found out how much ram cost for this specific machine and it was a no go.  I believe in most cases, memory to be the determining factor.

---

### Post by snowpine on 2011-02-27
Let's agree to disagree. I will continue recommending SliTaz, CrunchBang, AntiX, etc. for older hardware, based on my excellent results with these lightweight distros on Pentium 3 computers. :)

---

### Post by lisati on 2011-02-27
Sometimes people just don't know: it took me about 4 years before I realized that one of my machines was capable of running a 64-bit OS. It would be nice if it was dual-core or better, but at least it works!

---

### Post by Hur Dur on 2011-02-27
Just because it will run, doesn't mean it has to be recommended. I doubt anybody would recommend Ubuntu for a computer with 256mb RAM or less. Sometimes DSL, SliTaz, and Puppy are just shots in the dark, and other times, they are necessary. Although, I do wish people would stop recommending Puppy and SliTaz for machines with less than 64mb RAM. Really when it comes to lightweight distros, those are the 3 that pop into people's mind. Although there are alot of other ones (Blueflops, TinySofa, Finnix, etc.) they don't come with as much functionality as SliTaz, DSL, or Puppy. Also, Debian requires quite a bit of tweaking to be functional on a computer with less than 64mb RAM, so it is generally not recommended to novice Linux users.

TL;DR: Most people who recommend them don't have outdated machines, or base their opinion on what others recommend.

---

### Post by handy on 2011-02-27
I think that many people who recommend the known lightweights are doing so to give the end user the best chance of having the fastest machine for the hardware they have asked about.

---

### Post by doas777 on 2011-02-27
I've always held that ubuntu past 8.x is a 2006 class OS meaning it runs best with a 2+GHZ cpu, 1+GB ram, and 256+ MB of non-shared VRAM. granted you don't need the whole ubuntu experience (compiz, IO caching, Disk indexing, HD video), but if you want it, you will need a machine manufactured after '06.

or do you really contend that a single core 1.4 GHZ chip will run 1080p video stutter-free?
even the CoreAVC codec for H.264 wont run that efficiently (especially without multiple cores for multithreaded decoding).

if you don;t want the whole ubuntu experience, then it makes sense to me to use a lighter distro.

---

### Post by ki4jgt on 2011-02-27
I have an old Compaq laptop which has 64MB of RAM. I don't think I can run anything on it.

---

### Post by NightwishFan on 2011-02-27
Possibly Debian with 486 kernel + fluxbox? Or a dedicated light distro.

---

### Post by iFargle on 2011-02-27
I used to run Ubuntu on an old PIII 500Mhz, 324MB RAM, 32.0MB nVidia graphics card.. Ran great! couldn't use any compiz or desktop effects, of course, but it got the job done 8)

---

### Post by koleoptero on 2011-02-27
A friend of mine runs ubuntu on a p3 800mhz and 512mbyte ram, and he has no complaints. Granted it isn't speedy, but it works.

> **doas777 said:**
> I've always held that ubuntu past 8.x is a 2006 class OS meaning it runs best with a 2+GHZ cpu, 1+GB ram, and 256+ MB of non-shared VRAM. granted you don't need the whole ubuntu experience (compiz, IO caching, Disk indexing, HD video), but if you want it, you will need a machine manufactured after '06.

or do you really contend that a single core 1.4 GHZ chip will run 1080p video stutter-free?
even the CoreAVC codec for H.264 wont run that efficiently (especially without multiple cores for multithreaded decoding).

if you don;t want the whole ubuntu experience, then it makes sense to me to use a lighter distro.

What on earth does HD video have to do with ubuntu, and what is that "ubuntu experience" thing you're talking about. You won't be able to play HD video on any distro with that hardware, and you'll be able to play HD video with any distro on modern hardware. So ubuntu is kinda irrelevant to your example.

---

### Post by Hur Dur on 2011-02-27
> **ki4jgt said:**
> I have an old Compaq laptop which has 64MB of RAM. I don't think I can run anything on it.

KolibriOS (Not Linux), Debian (Disable some tty, install either IceWM or JWM, and make a pretty big swap partition. Or just run it headless), BasicLinux, Blueflops, TinySofa, Arch Linux (I've heard of a tweak to run the installer on 64mb), DSL, Devil Linux, NetBSD (Not Linux, but it runs on toasters) and, of course, MINIX (Not Linux.)

---

### Post by doas777 on 2011-02-27
> **koleoptero said:**
> A friend of mine runs ubuntu on a p3 800mhz and 512mbyte ram, and he has no complaints. Granted it isn't speedy, but it works.



What on earth does HD video have to do with ubuntu, and what is that "ubuntu experience" thing you're talking about. You won't be able to play HD video on any distro with that hardware, and you'll be able to play HD video with any distro on modern hardware. So ubuntu is kinda irrelevant to your example.


ubuntu has features built in, that make use of newer class hardware. the full "ubuntu experience" of course, would be the user experience when ubuntu is operating at full capacity with all features enabled, as the distro designers intended.

however you reinforce my point. that hardware is not capable of supporting somthing you should be able to do with on a modern OS. as such a full-featured desktop OS does not seem to be the thing you are looking for in this case. get something designed to run efficiently on older/less-provisioned hardware.

---

### Post by koleoptero on 2011-02-27
> **doas777 said:**
> ubuntu has features built in, that make use of newer class hardware. the full "ubuntu experience" of course, would be the user experience when ubuntu is operating at full capacity with all features enabled, as the distro designers intended.

however you reinforce my point. that hardware is not capable of supporting somthing you should be able to do with on a modern OS. as such a full-featured desktop OS does not seem to be the thing you are looking for in this case. get something designed to run efficiently on older/less-provisioned hardware.

Although I agree with you, to the point of planning my escape from gnome to xfce in the next ubuntu cycle, you can still work with modern distros on older hardware, so it's basically what the user wants. I wouldn't mind having to dig some config files to get things working my way in a more "cranky" DE like xfce or using openbox, but some other users might prefer the sacrifice in performance over the ease of use they get running more "modern" environments like gnome or KDE. Also the fact that the developers meant an OS to be used with some features doesn't make it obligatory, unless you're in the windows or *[SIZE="1"]*shivers*[/SIZE]* OSX worlds. Linux does give you that freedom.

---

### Post by XubuRoxMySox on 2011-02-27
I don't find Xfce "clunky" at all. To me it's "Gnome Lite," which for me is not only faster, but simpler; yet without the sacrifice of any features I like. Multiple panels (one that is invisible unless I mouse over it - the only thing in that panel is my task bar - the other one is like a "dock," only nicer, transluscent, and has my cool applets like weather and analog clock) and easy-to-use menus. I do find it easier on my modest hardware than Gnome was, no slower on it than LXDE was, and intuitive enough for other kids who share the computer to figure out without any coaching or instruction.

But I think most distros will run just fine on just about any hardware newer than 10 years old anyway regardless of the desktop environment. It's just that they might run more responsively with a "lightweight" desktop environment, and faster yet without one. Openbox (ala Crunchbang Linux) was super-mega-ultra quick on my lappy! But not quite as intuitive and fully featured as Xfce, and because I share the 'puter with others I needed something anyone could use... Xfce fits the bill and I find the difference in speed is so smalll as not to really matter. It still beats heck out of Windows XP for speed and simplicity, even if only because it doesn't need to load all that antivirus/anti-spyware/anti-adware/optimizer/etc bloatware and keep it running in the background.

I think that those daemons and stuff going in the background prob'ly do more to the speed than the choice of a desktop does. And I'll side with Snowpine on recomending the ultralight distros for reeeeeally old hardware (Crunchbang, AntiX, Slitaz, Puppy, etc).

-Robin

---

### Post by NightwishFan on 2011-02-27
I agree. XFCE is really great for new users and even good for people who like things more Unixy. I will probably run any old computers using XFCE instead of LXDE.

---

### Post by Khakilang on 2011-02-27
I did try Slackware on a Pentium 4 2.0GHz with 256MB RAM. It give an error of insufficient RAM for graphic installation. I think if the installation using text mode. It shouldn't be a problem. I did install Debian 5.0 Lenny and its works great. All the PC need is an extra RAM.

---

### Post by ki4jgt on 2011-02-28
> **Khakilang said:**
> I did try Slackware on a Pentium 4 2.0GHz with 256MB RAM. It give an error of insufficient RAM for graphic installation. I think if the installation using text mode. It shouldn't be a problem. I did install Debian 5.0 Lenny and its works great. All the PC need is an extra RAM.

Speaking of slackware, Slax was the first OS (Besides Windows) I had ever ran. :-( I wish the Ubuntu website was like the Slax one. It actually lets you build your distro before you download it. You can install every package you want, and then place it on a USB stick or burn it to a CD. Can't tell you how many months, I used a live slax USB which I had installed everything on from the website and no hard drive.

---

### Post by lisati on 2011-02-28
> **ki4jgt said:**
> I have an old Compaq laptop which has 64MB of RAM. I don't think I can run anything on it.

I have an old desktop, of uncertain vintage (late 1990s), with 64Mb RAM and a 3Gb HDD (not the original). It happily and slowly runs a CLI version Ubuntu 6.06, which, sadly, is past its "use by" date.

---

### Post by uRock on 2011-02-28
I have a Dell with a P4 and 1GB RAM and it could not do flash media in browsers or play any games until I added a vid card that had another 512MB RAM. I can't imagine trying to do these tasks with full blown ubuntu on a machine with only 512MB RAM. I'd have to tell it to do something, then come back later to see how it went.

---

### Post by mazato on 2011-02-28
> **asifnaz said:**
> I have seen many times on different Linux related forums people come and ask for Linux distros for their older PC's .

I have seen many times people ask like :

suggest me a distro for my old PC which is a Pentium III 1Ghz with 512 ram ......

and people without any clue start shouting...

Slitaz , DSL , Puppy Linux etc 

I dare to say that hardware above mentioned (P III 1Ghz with 512 ram ) can run almost any modern Linux distro .

I am running Debian 6 on P III with 256 ram ( I use 512 mb as swap ) without any problem .

why do the people under-estimate old hardware .

I wonder how many of you tried to run Linux ( specially Debian ) on old hardware


People underestimate old hardware maybe because they have very new hardware and they haven't tried running an up to date distro on such an  old hardware. They  might just basing their knowledge on assumptions and measurements on their new hardware. Now, I took the time to read all pots on this thread and I'm not saying that all other mentioned distros do not work, I'm just answering what the OP asked at the beginning.



I actuallly run Lubuntu on a Thinkpad X20 with a 500 mhz and 320 RAM, I only use it for browsing mostly.

---

### Post by NightwishFan on 2011-02-28
To be honest I wish I had an old machine to test out Debian on, the oldest hardware I personally tested it on had 1gb, and of course, it flew. I plan on picking up some used machines, perhaps even 128mb of RAM, and testing out what works on them. If I can get them satisfactory enough, I will probably install Debian XFCE on them and donate.

---

### Post by mazato on 2011-02-28
@ NightwishFan, I have been thinking on that idea for years now, but haven't had the time to work around it!
How will you find people who need these recovered machines?.
I think this is a great and noble idea, if you continue to peruse on it, good luck finding more discarded machines!

---

### Post by NightwishFan on 2011-02-28
People always could use a computer, especially kids in grade school of limited means. I will support only debian stable or ubuntu lts for the machines, but after they leave my hands, they can feel free to install windows on them, they just wont get as much help from me.

---

### Post by barbedsaber on 2011-03-01
I was running ubuntu on my 1.6ghz atom netbook.

it tested my patience
less than windows would have, but still...

---

### Post by uRock on 2011-03-01
> **barbedsaber said:**
> I was running ubuntu on my 1.6ghz atom netbook.

it tested my patience
less than windows would have, but still...
Really, 10.04 works great on my netbook.

---

### Post by johntaylor1887 on 2011-03-01
> **asifnaz said:**
> 

I am running Debian 6 on P III with 256 ram ( I use 512 mb as swap ) without any problem .



Yeah, as long as you don't multi-task, play flash videos full screen, watch hi-def videos, 3D games, etc. No problem. 

As long as you only do basic surfing and write simple text files, then yeah, it's a good computer. Enjoy!

---

### Post by NightwishFan on 2011-03-01
It could probably handle any task but hd multimedia or 3d games, so I do not see the problems. ;/

---

### Post by lisati on 2011-03-01
> **barbedsaber said:**
> I was running ubuntu on my 1.6ghz atom netbook.

it tested my patience
less than windows would have, but still...

That's nothing: the machine I mentioned [here]("http://ubuntuforums.org/showpost.php?p=10503658&postcount=22"), which flies along at a whopping 133 MHz, tested my patience while finding a flavour of Ubuntu that would actually install, let alone work. That's right, 133 megahertz!

---

### Post by johntaylor1887 on 2011-03-01
> **NightwishFan said:**
> If I can get them satisfactory enough, I will probably install Debian XFCE on them and donate.

If possible, get 256mb ram for Debian. I have done much testing on older hardware with various distros, and can tell you that debian will run on 128, but it will be pretty slow, even with a minimal install. The best distros I've tried on 128 or less is Tiny Core Linux, followed by Slitaz.

---

### Post by NightwishFan on 2011-03-01
Yeah a full gnome desktop is not very fun on 256mb but it works. (Doing so right now).
```
 free -m
             total       used       free     shared    buffers     cached
Mem:           245        241          3          0          2         59
-/+ buffers/cache:        179         65
Swap:         2859        225       2634

```

Granted I am on 64-bit and have a lot of stuff running (evolution, totem, banshee, and firefox)

---

### Post by barbedsaber on 2011-03-01
It really depends on how you use your computer

Personally, I have some 50gb of music that a program has to keep track of and search through all the time, I don't remember the last time I had less than 6 tabs open in chrome (and before I had FF with some 6 quintillion addons), I watch HD movies, and use fullscreen HD flash content. I have a torrent client keeping track of some 200 torrents 24/7, and I mash alt-tab like a madman between my half a dozen programs that I'm flogging at any one time.

Some people browse one tab at a time, don't listen to music, or have smaller collections, don't watch movies, and really just work with documents.

Good thing about linux is there's a solution for both of those people.

---

### Post by K.Mandla on 2011-03-01
I suppose I should weigh in. I run Debian Squeeze at 120Mhz / 80Mb, Crux at 150 Mhz / 32Mb and Debian Lenny at 133Mhz / 32Mb. The trick isn't getting the machine to run the software, it's to get your perspective in line with how best use Linux at low speeds.

---


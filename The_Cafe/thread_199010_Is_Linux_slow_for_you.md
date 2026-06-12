---
title: "Is Linux slow for you?"
date: 2006-06-18
forum: The Cafe
---

### Post by v8YKxgHe on 2006-06-18
Hey,

I've used Windows for years now, and recently i've been on Ubuntu for about 3 days now, and I seriously find it very slow. Here is my PC spec:

AMD X2 3800
ATI X800XT
DFI LanParty UT Ultra-D
2x SATA2 RAID 0 WD hard drives
Tagan 530w PSU
1GB ( 4x256 ) Corsair PC3200

Windows will boot in like < 20/30 seconds, yet Ubuntu takes near a minute to boot, then it has to load Gnome which takes around 10 seconds but with Windows it's < 5. 

Applications load amazingly slow, with Windows Firefox opens instantly yet with Ubuntu/Linux ( I've tried many distros, all have this problem ) it takes around 10 seconds to load, or sometimes it doesn't even load at all. 

Generaly the whole Gnome desktop feels slow and slugish to do anything. Windows is just instant really, Ubuntu/Linux isn't ( even with ATI drivers installed )

---

### Post by aysiu on 2006-06-18
For boot time, Windows is almost always faster.

It sounds, though--based on what I've read in numerous threads over the past year--as if people have had varied experiences as far as application loading time and responsiveness.

You may want to look into trying KDE or XFCE. XFCE in particular is very fast.

---

### Post by v8YKxgHe on 2006-06-18
hello again =)

Yeh i've been thinking of trying XFCE, seems good. KDE I think looks childish ( espically with that big dragon everywhere! ) and feels bloated, I use to have Ubuntu Hoary on KDE, didn't like it at all ( though I liked how custimizable it was )

---

### Post by aysiu on 2006-06-18
You can change the big dragon. You can also tweak KDE to be less "bloated" and more minimalistic using the *kpersonalizer* application.

You'd be amazed--with the right settings--how snappy and uncluttered KDE can be, even on a machine with 128 MB of RAM; though, you probably have more than that.

---

### Post by Hg80 on 2006-06-18
i have an amd x2 4400 1 gig of ram and find that linux may take a bit longer to load from boot but once in gnome its far quicker, to me this sounds like a driver or hardware issue conflicting somewhere have you tried reinstalling Ubuntu?

---

### Post by v8YKxgHe on 2006-06-18
Woops, forgot to add my ram spec, 1GB ( 4x256 ) Corsair PC3200.

Hum, if I just do " sudo apt-get install kde-desktop " and then xfce-desktop, will that install both KDE and XFCE?

Edit: Hg80, i've re-installed Ubuntu about 12 times now ( was trying to get XGL working before, but i've gave up now ) and it's not just Ubuntu - FC5, Suse 9.1, Arch Linux, Vector Linux, Mandrake are all slow.

---

### Post by jinx099 on 2006-06-18
AlexC:  do you have your fglrx driver installed?  Ubuntu felt much faster after getting fglrx working, i didnt think thered be a big difference but there is.

---

### Post by aysiu on 2006-06-18
I would advise this instead: ```
sudo aptitude update
sudo aptitude install kde-core
sudo aptitude install xubuntu-desktop
``` *aptitude* is preferable to *apt-get* because it remembers what dependencies came along with the metapackage (in case you want to remove it later).

Since you complained about KDE being too bloated, *kubuntu-desktop* is probably too much, so I would advise *kde-core* instead.

---

### Post by v8YKxgHe on 2006-06-18
Jinx, yes - I did, but when I have them installed my GPU fan is constantly at 100% which is loud! So i've removed them and are back on the, mesa drivers is it? I didn't notice that much difference to be honest

Aysiu, thanks - I shall try that in a min.

---

### Post by woedend on 2006-06-18
the single biggest "speed up" feeling is the appropriate graphic drivers...too bad about ATI.  It just makes everything "feel" faster.
Ubuntu can be made fast, but you have to start stripping it.  At one point I had boot down to 21 seconds or so...with initng it can be even lower.  
Windows cheats and pretends to be ready when it's not.  When I see gnome, it's ready to go...when windows loads up, I normally wait 30 seconds to a minute before digging into anything.
Firefox normally takes about 3 seconds to load the first time, <1 second each subsequent time because it's loaded in memory.  If you really want instantaneous firefox windows, keep one open at all times, each new instance will be immediate.  
My computer doesn't have the specs yours does...I just want you to know that it's unfortunate things are so slow for you but it's not the "norm".

---

### Post by Kvark on 2006-06-18
Boot and application start up times doesn't bother me because I almost never close the applications so I almost never have to open them again. I just leave all applications related to the same task laying on a workspace for weeks and then return to that workspace whenever I want to use them again.


You can use [bum]("https://wiki.ubuntu.com/BootServices?highlight=%28bum%29") or [InitNG]("https://wiki.ubuntu.com/InitNG") to speed up boot times.

---

### Post by oskie on 2006-06-18
I am happy bit my boot times under Dapper and it is about the same as with windows on my dual boot machine. I have had what seemed to be faster boot times with Fedora Core 5 but I never did any comparisons. SuSE was notoriously slow for me. With Dapper, certain apps boot more slowly in Linux (openoffice for instance is very slow despite disabling java runtime). But all in all I find Dapper much more stable, snappy and responsive than winblows. XFCE is fast but a little too spartan for my tastes. I still might try out xubuntu though. I prefer speed to eye candy.

---

### Post by Biltong (Dee) on 2006-06-18
[QUOTE=aysiu]For boot time, Windows is almost always faster.
[/QUOTE]

Am I the only person on the planet that found the opposite to be true? 
I am using a trusty Intel P2/256 Ram and used to run XP. When XP started up I got up and made myself a slow cup of coffee, cos it took that long.

Ubuntu/Gnome in comparison is really fast - in fact I dare not go anywhere so I'm coffee starved. :-)

Now I have downloaded Kubuntu/KDE and am back to XP speeds again, so I think it is all due to the processor type.

Am I right?

---

### Post by nalmeth on 2006-06-18
I rarely ever reboot so it's not a big deal for me, but
you can speed up performance in certain ways. 

You can [turn off unnecessary processes to speed up boot-time]("http://doc.gwos.org/index.php/Speed_up_boot"), and I think [BUM]("http://ubuntuforums.org/forumdisplay.php?f=75") can do this too. 

You can [prelink]("http://www.ubuntuforums.org/showthread.php?t=74197") the application libraries to make programs open faster. With prelink you have to be careful not to interupt the 'prelinking' after you install new 
apps or get new updates, as it can lead to breakage. I have safely been using prelink on my laptop with dapper for at least 2 months, and have had no problems. But user beware nonetheless

Ubuntu comes in a safe stable package, but you can go and do anything you want to it.

---

### Post by sharkboy on 2006-06-18
I have the same processor as you do, and when I tried ubuntu I had the same experience. Turning off the powernowd demon helped a lot -- do cat /proc/cpuinfo to see what speed your processors are currently running at. My guess is they are running at 1GHz instead of 2 GHz like they should.

Still, ubuntu is too slow for me. I'm back with regular debian which works a lot better and faster on my machine.

---

### Post by UbuntuniX on 2006-06-18
Nope,
I have Intel Celeron and a 250 GB hard drive,
Windows XP Pro is partitioned about 160 GB and ubuntu is partitioned about 90 GB,
Windows is extremely laggy yet ubuntu is very fast and smooth :)

Also Windows is full of errors (not caused by viruses),
but ubuntu is perfect :)

GO UBUNTU!!!

---

### Post by v8YKxgHe on 2006-06-18
[QUOTE=sharkboy]I have the same processor as you do, and when I tried ubuntu I had the same experience. Turning off the powernowd demon helped a lot -- do cat /proc/cpuinfo to see what speed your processors are currently running at. My guess is they are running at 1GHz instead of 2 GHz like they should.

Still, ubuntu is too slow for me. I'm back with regular debian which works a lot better and faster on my machine.[/QUOTE]

I shall do that when I'm on Ubuntu ( On windows atm, because of the speed issues, plus I like the polish of Windows apps that Linux doesn't offer =) ) 

nalmeth, I tried prelinking about a 2 weeks ago and didn't see any difference at all.

---

### Post by Jucato on 2006-06-18
For me, Linux is fast, but the boot process is slow (35 seconds), if I compare it to Windows XP. But the difference is in Linux, once I log in, KDE loads fast and everything is fast after that. In Windows, when I login, I have to wait for almost half a minute for thinks to be working.

But my real issue is the boot up speed. I've already disabled unneccessary services from starting at boot (using KDE's built in service manager, how nice), but that only shaved 5 seconds off (original booting was 40 seconds or more).

---

### Post by aysiu on 2006-06-18
[QUOTE=Biltong (Dee)]Am I the only person on the planet that found the opposite to be true? 
I am using a trusty Intel P2/256 Ram and used to run XP. When XP started up I got up and made myself a slow cup of coffee, cos it took that long.[/QUOTE] You're probably not the only person, but you're one of few, based on what I've seen on these forums.

The general consensus seems to be (and, yes, it is *general*) that Windows boots more quickly, but Ubuntu's a bit snappier after boot (with the one exception of Microsoft Office as opposed to OpenOffice).

---

### Post by nuvo on 2006-06-18
XP does get to the desktop quicker for me, but I still have to wait for it to finish starting up my virus scanner, firewall and so on before it can actually be used.
With Ubuntu, booting is slightly slower to get to the desktop, but once started, my system runs quicker even though I use XGL \ Compiz.

---

### Post by oyvindaa on 2006-06-18
Linux has never been slow for me. It's been faster than Windows on all the versions I've tried, with all my usual applications installed.

---

### Post by ComplexNumber on 2006-06-18
linux feels fast for me.

---

### Post by fuscia on 2006-06-18
on my old POS, the default install of breezy felt to be the same speed as ME. using apps like dillo and sylpheed-claws, in openbox, made it much faster. dapper, using kde, on my new laptop (system76), is as fast as i could ever want.

---

### Post by RAV TUX on 2006-06-18
On my older computer Linux has a faster boot and page rendering time then windows for me, but  on my second desktop which has Intel EM64T Dual-core they are about equally as fast but this has nothing to do with windows but with my hardware(when I run Linux on this computer it is just as fast).

I found PC-BSD to have the fastest install, boot and page rendering time, overall.

---

### Post by G Morgan on 2006-06-18
For a lighter machine (i.e. less installed) XP definately gets to a working state quicker. From login to workable desktop Linux is very consistent as it doesn't slowdown over time from a collection of bootup garbage and tends te be faster than most XP setups. In terms of boot to login both are generally consistent but Linux can be made to boot much quicker with a few things. Most distros tend to add sleep commands into the boot scripts 'just in case' removing these can speed up the boot process by a good 10 seconds. Also using InitNG can make a great difference since it activates services in parallel as opposed to linearly. If you want a good idea how fast Linux can boot you should see a Gentoo box.

In terms of general speed, I find Windows struggles badly under high loads. With Linux I can get 7/8 apps running without any noticable slowdown. I think this is mainly to do with how both OSes manage virtual memory and the fact that Linux HDDs don't fragment to serious levels. Result, Linux performs better when its got no slack to work in, when the processor and RAM are both pushed to their limits Linux runs more smoothly than XP.

---

### Post by disturbed1 on 2006-06-18
There is no comparison between Windows (2000/XP) and Ubuntu for application launch, and actual application usage.

For boot up times my Ubuntu is 2x faster than 2000, but slightly slower than XP. However, once XP displays the desktop, the hard drive still had to grind away to load all of XP's background services, the antivirus app, and the antispyware app. So I'd put the actual pressing of the power button to a completely useable desktop about equal between ubuntu and XP, with a slight edge to XP.

Firefox renders, and launches faster in Ubuntu compared to XP. There is no competition here. (I added MOZ_DISABLE_PANGO=1 to /etc/environment)

On a fresh boot of both XP and Ubuntu, XP's explorer has a launch advantage compared to Nautilus. Use the machine on for 3 weeks (or even 24 hours ;) ), Ubuntu has the same performance as the first minute of use, XP does not - advantage shifts to Nautilus for speed. After a couple of days of use, even Internet Explorer in XP tends to have a much slower launch and rendering time.

If your apps are loading slow you can do a couple of things to speed them up. Use prelink (forum search there's a how to on this), and either tune your file system, or use a faster FS like JFS or XFS. Using prelink and JFS dropped Gedit's load time from ~3-4 seconds to almost instant.

Follow the other advice of disabling not needed startup services. Ubuntu tries to be an all for one type of distro. This has it's fall backs, and advantages. Advantage that no matter what combination of hardware you have, Ubuntu has a good chance of working out of the box, down fall is that it takes a little tweaking to remove everything you don't need. I kind of like this, I would rather have to remove things already there, than search for answers on how to add things correctly that aren't.

---

### Post by Mishal on 2006-06-18
Linux is slower for me than Win XP. Its boot slower and the desktop responsiveness and application launch times are all slower than in XP. Nautilas windows even leave behind ugly trails (and yes, I HAVE indeed installed the nvidia driver for my video card).
My system is somewhat old with AMD AthlonXP 2000+ and 512MB RAM and a prehistoric 32MB Riva TNT 2 card but Windows XP uses these same hardware to be much faster than Linux.

Though I have shifted to Linux for 98% of my PC work, the slower speed is one of the drawbacks I have to live with. :)

---

### Post by Somenoob on 2006-06-18
I used XP for about 3 years, and i find Linux to be faster in my opinion.

If Win is faster in any case, than it's probably due to incorrect configurations in Linux.

---

### Post by rai4shu2 on 2006-06-18
In my experience, they are about the same speed. I think Gnome looks better, but then again Gnome 2.14 is a little more cutting edge than XP/SP2.

---

### Post by angkor on 2006-06-18
[QUOTE=AlexC_]Hey,

AMD X2 3800
1GB ( 4x256 ) Corsair PC3200

Windows will boot in like < 20/30 seconds, yet Ubuntu takes near a minute to boot, then it has to load Gnome which takes around 10 seconds but with Windows it's < 5. 
[/QUOTE]

I have the same proc and amount of mem you have and Ubuntu is just as fast if not faster than xp. My machine boots way faster than 1 minute. Gnome loads in > 4 secs (default, no extra apps).

Some apps load faster in windows because a lot of programs are being preloaded. Once the app is loaded it usually responds faster in ubuntu than in xp.

My experience is that Ubuntu (Linux in general) is a lot faster when you multitask, with my system I can use (and keep open) 10-20 apps for days without losing speed.

---

### Post by yaztromo on 2006-06-18
For me Windows has always been faster.

Load times for firefox and MS office are lightning in XP. Can't say the same for openoffice or firefox in linux.

But I think what makes Windows feel faster in generally is GUI responsiveness. Windows has hardware accelaration whereas Xorg doesn't. This should all change with AIGLX I hope.

---

### Post by graigsmith on 2006-06-18
> 
AMD X2 3800
ATI X800XT
DFI LanParty UT Ultra-D
2x SATA2 RAID 0 WD hard drives
Tagan 530w PSU
1GB ( 4x256 ) Corsair PC3200


whaaaaat?  i have less of a system than that, and mine boots faster than that.

Hmm. did you install the proper kernel for your system? or are you still using the 386 kernel?

---

### Post by arkangel on 2006-06-23
i have  a decent  Laptop   1Gb ram 100 Gb HD  centrino 1.86  and ati X700  128mb  y use double  boot (just because  autocad  and inventor but in a 10 gb partition ) Ok  booting Xp is faster than  Linux , but i dont care i can  wait  30 more seconds ;)  once gnome is loaded  , then I compare how much things I can do at the same time  than  in a similar situation under windows (no virtual  desktops for example have u tried to open 3 Internet explorer  a word and an excel session at the same time )  so no way is  slower than xp  once u get used to it , then you have your file  /home/user   whatever you do  is there in the best way you can image  no more my Docuement , My pcitures  My Panties, etc 

once I had to install a rar utility , in windows Xp  do :  seach in google ,  navigate in the site , find the download link  , open the file , accept the agreement,  specify the directory ,  answer some stupid questions , use the rar 
under ubuntu:  open synaptic, search rar , mark  the suitable option , click apply , use rar   :)

---

### Post by Stormy Eyes on 2006-06-23
Sure, with Windows you get to a desktop faster. But the desktop is unusable until Windows finishes loading all of its daemon processes. With Linux, the system starts its daemon processes first, and then brings up X. As for slow-loading apps; try using prelink. I find it works well for me. There are howtos on the forum if you search for them.

---

### Post by Skye on 2006-06-23
When I first bought my laptop and started it up for the first time, I was dismayed.  Windows took something like 15 minutes to start, and once into the desktop, ran like a pentium 166 (this is on Sempron 2800+).  I considered brining it back, thinking I had recieved a defective model or something.

But, I had already been using Ubuntu (Breezy) on my Desktop, so I wanted to install Ubuntu on the lappy before I got a replacement.  So, I installed Dapper (Flight 6, I think.)

What a difference!  I got to a working Desktop in under 2 minutes, and once there, everything just *worked.*  So, it was just windows crapping out, and not a bad laptop.

I admit, I am a fairly dedicated Linux fanboy, (in a quiet sort of way- not the rabid, foaming at the mouth kind) but that experience just reinforced my love of Ubuntu and Linux in general.  And the laptop now runs Linux exclusively.

---

### Post by Ubunted on 2006-06-23
Breezy and earlier were definitely slower than XP.

Dapper is still a little slower to boot and open first-run programs, but the disk cache keeps everything else pretty damn quick otherwise.

---

### Post by theturner on 2006-07-02
Dapper isn't bad in terms of speed, but if you've used BeOS before, everything else is dog slow for you.

---

### Post by Kimm on 2006-07-02
Are you sure you have the right kernel?
The kernel installed by default is an i386 kernel for old Intel machines. It will work with AMD and new CPUs, but for most installing the i686 kernel will provide a performance boost, but in your case, you'll want the k7 kernel

---

### Post by mips on 2006-07-02
I have a XP partition on my hd which i rarely use and it really is full of junk. I find it way faster than dapper and I have done all kinds of optimisations to dapper which helped. In XP things just open up faster, I know the loading seems faster but it's really not due to loading stuff in the background.

---

### Post by bruce89 on 2006-07-02
My XP install is mucked right up (after resizing it down), takes 5 minutes to boot up after login.  It shouldn't be like this.  It also recreates my dad's user every time he logs in.  It sounds as if a reinstall might be on the cards.

---

### Post by v8YKxgHe on 2006-07-02
> My XP install is mucked right up (after resizing it down), takes 5 minutes to boot up after login. It shouldn't be like this. It also recreates my dad's user every time he logs in. It sounds as if a reinstall might be on the cards.

You never have any luck with XP!! 

Well Linux is running OK now, even better that i've got XGL installed ( Damm I loev XGL, so good ) And I'm using it as my primary OS for about a week now =) I love it.

---

### Post by Mr.X on 2006-07-02
Linux is super fast, i've never had any problems (If i do, i just ask - so many helpful users on IRC/Forums its great ;) )

---

### Post by TuxCrafter on 2006-07-18
I do want to say that the shutdown of a tweakt linux is far more faster than a tweakt windows xp pro

---

### Post by Engnome on 2006-07-18
> **yaztromo said:**
> For me Windows has always been faster.

Load times for firefox and MS office are lightning in XP. Can't say the same for openoffice or firefox in linux.

But I think what makes Windows feel faster in generally is GUI responsiveness. Windows has hardware accelaration whereas Xorg doesn't. This should all change with AIGLX I hope.

Agree, however I get a faster gui in Linux by using an extremely light theme. But even with a heavy theme i still like gnome better not just because it has a better layout but the windows gui hangs/lagggs alot for anything that requiers more than average cpu power/hhd access.

Nothing you can do about FF and such (exept maybe prelink...)

---

### Post by Carrots171 on 2006-07-18
Sometimes Linux can be slow because of a driver issue, usually with the motherboard/video card. For me, Linux is very fast.

---

### Post by K.Mandla on 2006-07-18
I would agree that XP boots faster, but personally I find that to be an optical illusion.

In my experience, the desktop might appear sooner, but it's still loading crud. And invariably, I still have to wait for the crud to finish before I can get started.

That being said, I've put Gnome and XFCE on the same machine, and Gnome lags considerably behind XFCE. For that reason I almost exclusively use Xubuntu, unless I've got a machine that's in the 2Ghz+ range.

Just my $0.02. ;)

---

### Post by Carrots171 on 2006-07-18
> **K.Mandla said:**
> In my experience, the desktop might appear sooner, but it's still loading crud. And invariably, I still have to wait for the crud to finish before I can get started.

Yeah, that's one of the things that I hate about Windows XP. :mad:

---

### Post by BWF89 on 2006-07-18
Back in late 2004 when I was useing Fedora Core 2 at first everything was relitively fast. And after a couple of days of useing it everything got extremely slow and sluggish. The screensavers, clicking on menus, even the games. But that was 2 years ago, it's probably inproved since then.

---

### Post by Kilz on 2006-07-18
> **K.Mandla said:**
> I would agree that XP boots faster, but personally I find that to be an optical illusion.

In my experience, the desktop might appear sooner, but it's still loading crud. And invariably, I still have to wait for the crud to finish before I can get started.


My thoughts exactly. My wife sees my Ubuntu start up and take a little longet to get to the login. But after I do I can start an application. She on the other hand logs in to XP and then has to wait as antivirus, antispyware, messangers, ect start before she can run anything.

---

### Post by briancurtin on 2006-07-18
everything about Arch Linux has been faster than Windows for me.

---

### Post by fuscia on 2006-07-18
linux is fast, but no way is it four times faster than a ppc.

---

### Post by Boomy on 2006-07-19
It is slower than the second coming for me. Ok, it's not that slow just using apps, browsing the net, etc. But when it comes to demanding tasks, like copying a 1 gig folder for instance, it is slow. That is because I have a SATA drive and Linux is slow as hell with SATA. Just do a search here and you will see, and nobody has an answer, because you cannot tweak SATA drives with HDPARM, so my SATA drive works at about 20mB/s. My USB 2.0 external drive is almost as fast. In Windows, I could copy a gig+ folder in under a minute, it takes 10 minutes or more now. :/

---

### Post by mdsmedia on 2006-07-19
It sounds to me like it depends on the hardware/drivers Linux is running.

I was on again off again Linux (never seriously) until a few years ago. Last year someone on a local LUG list suggested I try Linux (I suggested I was going to give it another go, probably with Ubuntu).

I tried the Live CD and contrary to most opinion on the forums I thought the Live CD ran fast...it was one of the things that impressed me enough to take the plunge and dual-boot (again). Ubuntu just felt so crisp and clean...I guess on a Live CD it would.

But I was so sick of how slow XP had become on my HP notebook that I decided if Ubuntu was as good as I'd been told I'd TRY to give it a serious go.

It's now my main OS. I boot into XP for some specialist programs and I've uninstalled a lot of stuff I don't need in XP anymore. XP's still slow, and Ubuntu is still crisp and clean. If the cpu light is on for more than about 25% of the time I close down Firefox or Thunderbird...sometimes OpenOffice....and it is back to clean again.

Some of the software seems to drag the RAM a bit, after a while, but in XP, if the RAM is dragged to maximum and I close a few programs it's still running at about 85% RAM used.

OpenOffice can be a real glutton for processing power and RAM, especially running a powerpoint presentation or large spreadsheet full of macros. Linux itself is so much cleaner and quicker than XP I feel dirty when I run XP. I can't wait to get back home to Ubuntu again.

---


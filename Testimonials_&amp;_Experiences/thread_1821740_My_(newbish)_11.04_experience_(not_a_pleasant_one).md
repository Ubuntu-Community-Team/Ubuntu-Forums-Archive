---
title: "My (newbish) 11.04 experience (not a pleasant one)"
date: 2011-08-09
forum: Testimonials &amp; Experiences
---

### Post by tyhjyydesta on 2011-08-09
Hi all, I decided to give Linux a shot and wanted to share my user experience (about my inability) to install it successfully. Well to be more precise my inability to install Ubuntu 11.04 x64 properly. 

My biggest problem: how the hack to get Nvidia GTX 580 to work properly with the system. After fresh install the awesomeness called "Unity" felt terribly sluggish, with horrible lags while ALT + TAB-ing, dragging windows and with just basically "everything". Aslo the OpenGL performance in games generally sucked the same way as in GUI = like hell. I was trying to play some Quake Live and due constant stuttering it gave me the impression that I am running it at ~20fps at best (while I am used to silky smooth 120fps from Windows)

Of course installing the drivers from additional hardware haven't solved anything so I tried installing latest NVIDIA drivers from their site (to no avail as well). Later I reinstalled the system and even installed 10.10 x64 - and here I succeeded in installing NVIDIA drivers following this guide [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074) 
with good performance in OGL games as well so I would have probably stick with 10.10 if there weren't for another problem: Zooming images in firefox resulted in extremely poor (or one could call it "sh***y") quality. Like if they used the most primitive resize fitler possible even subpar to those used in old doom game (remember massive pixelization when you were close to wall ?) One of the so called "workarounds" I found for that was that you should "turn of zooming images" and zoom only texts. Ingenious, right ? Or alternatively if let's say: Ubuntu wasn't working with my soundcard  the workaround  would be to throw it away and to use the crappy onboard chip. etc. Excellent ! Sorry to say that but "workarounds" like that made me extremely angry if for nothing else due to suggestion of unacceptable (at leas for me) compromises in functiunality and since other web browsers contained rendering bugs as well (artifacts all over the displayed page) I decided to gave up on 10.10 and give 11.04 one more shot. 

So I switched to classic view (no effects), uninstalled everyting graphically related compiz, mesa or whatever nvidia*, followed the guide for installing NVIDIA that worked in 10.10 and guess what ? It didn't work in 11.04. 
Than I was suspecting it may have something to do with problem mentioned here: [http://ubuntuforums.org/showthread.php?t=1722306](http://ubuntuforums.org/showthread.php?t=1722306)
but managed to get black screen boot in the process so out of despair I decided to give KUbuntu 11.04 x64 a try (though I didn't expect much difference in drivers support compared to Ubuntu 11.04) but surprisingly - it worked out of the box. After OS install the 270 something NVIDIA drivers were correctly installed all the effects, windows dragging ALT + TAB-ing even games - all was very smooth as I would expect. I just had to enable 120 Hz refresh. 

Though I totally did not expect it the Ubuntu vs. KUbuntu user experience for me was night and day so far. Main reason for that being the NVIDIA driver problem but even if Unity + OGL have worked Unity would probably still felt "artificial" or even "retarded" (how else would you call placing minimize / maximize buttons on the left of window by default) - maybe if I had more time using the Unity I would feel different but after my recent experience I have very little reasons to give it another shot. 

The only significant problem I registered in KUbunntu so far was the appereance of white squares on certain flash sites under firefox (luckily other browsers are OK on this), Opera not displaying scrollbar in youtube video on mouse over (but you have to click to show it). While those bugs are still kinda lame - other than that I really like KUbuntu (and hate Ubuntu). In KUbuntu everything looks nice and clean and just works. No doubt the desktop (basically I mean KDE) experience is superior to Windows (starting to have feeling you can do so much more in KDE with many more options etc.) 

If there is any other newb out there struggling getting NVIDIA to work with "Natty" then I highly recommend on trying KUbuntu. Those two latest releases of Ubuntu I tried felt to me like unfinished betas with principal problems which never should have been there (and which frankly I did not expect). After many, many hours of headaches I still wasn't able to get it working. Was it because I haven't tried hard enough or are my complaints fair ? And is it just me or why are there so many problems with flash support on Linux ?? I don't mind doing complicated thing in a complicated way but having proper support for VGA and flash seem essential enough they should work without bugs out of the box, shouldn't they ??

---

### Post by Linuxratty on 2011-08-09
> **tyhjyydesta said:**
>  they should work without bugs out of the box, shouldn't they ??

 Yes they should. My Nividia used to work perfectly in Lucid until back in March,then the problems started and I had to reinstall the Nividia drivers every bloody day,day in day out..Boot Lucid Lynx,install the stupid drivers.

 Compiz won't even work in the latest Mint thanks to this problem...So now I'm on Meerkat.

I no longer have to install the drivers every day,just several times a week. Day before yesterday,no install,yesterday and today,I installed the drivers.
So when I boot up I right click on the desktop to see what I have to do . If I have to install the drivers,I also have to  turn off and turn on Conpiz and save the current settings,recheck my mouse fireball and wobbly windows which ALWAYS uncheck themselves when this driver crap starts.
 Am I sick of this? Oh yeah. You would think after SIX MONTHS SOMEBODY would fix this?
Maybe?
:roll:](*,)

---

### Post by tyhjyydesta on 2011-08-10
> **Linuxratty said:**
> You would think after SIX MONTHS SOMEBODY would fix this?

Does all that mean there is no one that succeeded installing reasonably recent (non-legacy) NVIDIA hardware + drivers under 11.04 Natty ? Is it just difficult (esp. for a newb) or completely impossible ?

Btw. you were lucky that web browsing worked for you under Meerkat (as this functionality was broken for me under 10.10 as well, no web browser would work acceptably out of box :( ) 

Well, anyone can say whatever he wants about Windows but fact is I have never experienced as many major bugs (like the absolutely basic functionality not working out of box) for last 3 years using Win Vista / 7 x64 (while XP x64 admittedly was not that great) as I have witnessed in just under 1 week on Ubuntu. I wonder how many of newbs will turn back on Linux because of similar experience. ( before they realize that Kubuntu is so much better :D - at least if we speak about 11.04  )

---

### Post by wazupwiop on 2011-08-10
Kubuntu has its advantages over ubuntu at times.  Kubuntu tends to work better with Nvidia graphics cards from what I understand.  I think the devs made a huge mistake in 11.04.  Unity should not be default, it should be optional and no more.

---

### Post by kindledwind on 2011-08-10
Don't feel bad. I ran 11.04 for a few months. It got borked up because I thought I'd give gnome 3 a shot....definitely not the right move. So, on re-install, I remembered what a headache it was to get 11.04 anywhere close to useable in the first place. My machine has dual Nvidia cards, and the linux drivers can't run them at the right resolution anyway, so 11.04 only works with a terminal window on a fresh install. Unity is a dead horse before it gets out of the gate. Maybe after fiddling with it for a few days I could get something useable, but I don't have the time for it.

So, I sit here watching 10.10 install & do it's updates....and cruise the forum to kill a little time.  Don't get me wrong, I really like Ubuntu, but if Unity stays, I'll probably go to Mint or straight to debian for the long haul. Unity certainly wasn't the brightest move in my book. 

todd

---

### Post by wazupwiop on 2011-08-10
> **kindledwind said:**
> Don't feel bad. I ran 11.04 for a few months. It got borked up because I thought I'd give gnome 3 a shot....definitely not the right move. So, on re-install, I remembered what a headache it was to get 11.04 anywhere close to useable in the first place. My machine has dual Nvidia cards, and the linux drivers can't run them at the right resolution anyway, so 11.04 only works with a terminal window on a fresh install. Unity is a dead horse before it gets out of the gate. Maybe after fiddling with it for a few days I could get something useable, but I don't have the time for it.

So, I sit here watching 10.10 install & do it's updates....and cruise the forum to kill a little time.  Don't get me wrong, I really like Ubuntu, but if Unity stays, I'll probably go to Mint or straight to debian for the long haul. Unity certainly wasn't the brightest move in my book. 

todd

I may end up switching to Kubuntu if Unity doesn't go away.  I think that Unity has some potential, but it really needs some work before it is installed as the default desktop.

---

### Post by Tamlynmac on 2011-08-10
> tyhjyydesta

Thanks for sharing your experience. Sorry you had problems and doubt you are the only one.

I've remained in the 10.04 environment. After receiving feedback from another member, I installed Xubuntu (xfce) on 2 of our desktops. It works great and I would recommend it to all those users who aren't satisfied (for any reason) with 11.04.

Good Luck and if Kubuntu meets your requirements and that of your system, then I hope you continue enjoying the experience. IMHO one of the true benefit of Linux is the significant number of available choices. Ubuntu alone has numerous flavors.

---

### Post by FormatSeize on 2011-08-11
** Nevermind. Didn't read carefully.

---

### Post by b0whunter on 2011-08-12
When I installed ubuntu 11.04 on my desktop, it fell right back to gnome as my G-Force GTX 260 drivers werent installed. But few seconds after logging into gnome, a notification popped-up asking if I wanted to install the nvidia drivers. I clicked and agreed. installed the drivers and reboot (an old windows habit i guess) and unity started right off the bat, without any lag, actually its super fast! And everything else just seem to work perfectly so far.  Never tried KDE, so I cant say which is better, but after some time getting used to (back from win7) im loving it more than win7.

---

### Post by cariboo on 2011-08-12
I've been using nvidia exclusively for the 6 years, without any problems. I have 5 system running everything from a 6600GT agp to a 218GT with a pci 6250LE, 8400GS and 9400GT in between. I normally run the latest testing version, and except when the drivers haven't been available from Ubuntu, I've used the default drivers without any problems. 

The only system I have to do anything extra on is a system in my shop that's connected to a KVM. On that system I have to run nvidia-xconfig, in order to get the monitor resolutions detected properly.

The system I'm using presently is running a 9400GT with two monitors connected. All I had to do was run nvidia-settings to set the resolution of the second monitor.

---

### Post by 3rdalbum on 2011-08-13
My GTX260 works okay on Natty with Unity. No performance problems. It leaves  the graphics card in an inconsistent and confused state sometimes and I can't boot up until I've unplugged the card from its power and plugged it back in again; but Unity 2D doesn't cause that problem.

I should report a bug on this behaviour. And if you're having problems, you should report a bug too.

---

### Post by Erik1984 on 2011-08-14
I'm a Kubuntu user myself but I find it very strange that the performance compared to Ubuntu is so different in your experience. I have seen benchmarks where Kwin kame out pretty well on FPS in games but not the differences you report. Glad Kubuntu works for you but still I wonder what causes the difference. Outside the desktop environment Kubuntu en Ubuntu should be the same system with the same Nvidia drivers.

---


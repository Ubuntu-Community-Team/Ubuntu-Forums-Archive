---
title: "3D acceleration works on VMware workstation 6.5"
date: 2008-07-01
forum: Virtualisation
---

### Post by Masoris on 2008-07-01
VMWare workstation start to support 3D acceleration feature on 6.5 version.You can read release note on here: [http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html](http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html)

It supports only Windows XP guest yet.
> Accelerated 3-D graphics on Windows XP guests — Workstation 6.5 virtual machines now work with applications that use DirectX 9 accelerated graphics with shaders up through Shader Model 2.0 on Windows XP guests. Hosts can be running Windows 2000, Windows XP, Windows Vista, or Linux.

It is currently beta 2 state. You can join beta testing on this website: [http://communities.vmware.com/community/beta/workstation6.5b](http://communities.vmware.com/community/beta/workstation6.5b)

So I downloaded it and install VMware 6.5 beta on my Ubuntu 8.04. I could install it without any problem on new GUI installer. What I most interest is 3D games works or not. So I start to test 3D feature. I downloaded and installed 3Dmark03, 3Dmark05 and 3Dmark06. I tried to get score. But 3Dmark03 and 3Dmark06 was freezed during benchmark, so I cannot get result. I finally get 3Dmark05 result: 469 points. Yes it's very bad result :(

And I tried few games on VMware. Simcity 4 works and playable but It has graphical flaw that makes my eye pain. MMORPG mabinogi also works but because of critical graphical defect. Many part of screen looks just white, it was very hard to play. Civilization also works, but all units are rendered just black object.

On VMware 6.5, I could run many 3D games and utility. But most of them has graphical flaw that makes hard to play and to use. And above all, the 3D graphic was very slow. I only got 0~5 fps when play a game.

It is still beta, I hope more powerful graphic acceleration on final release.

---

### Post by Shaythong on 2008-07-10
May I ask what kind of graphics card you have? Thanks for the information. :)

---

### Post by Masoris on 2008-07-11
> **Shaythong said:**
> May I ask what kind of graphics card you have? Thanks for the information. :)

I use *GeForce 7100 / NVIDIA nForce 630i* Motherboard.

---

### Post by Shaythong on 2008-07-29
> **Masoris said:**
> I use *GeForce 7100 / NVIDIA nForce 630i* Motherboard.

Wow! I have a very similar card: GeForce 7150m and the nForce 630i too. Except I heard that the 7100 can go up to 256mb of dedicated memory while the 7150m can only go to 128mb.

Anyway, I have tried out VMWare Workstation 6.5 before on Ubuntu Hardy. I had to disable PulseAudio for a while because that was giving me problems.

I tried running Daemon-Tools on there and it worked fine. I also tried GTA: SA 1.00, and it worked good, but there were some graphics errors, like most objects were white. Guild Wars seems works on VMWare but it seems to work better on Wine currently.

But it's still in beta, so I can't say that much. From your images of the 3DMark tests, it didn't look like it went too well. But thanks for posting the images up! :D

---

### Post by mikedep333 on 2008-08-20
I just tried VMware Workstation 6.5 RC (6.5.0 build-110068) on Ubuntu 8.04.1 64-bit. 3D acceleration wouldn't work, as evidenced by a pop-up when my Windows XP VM starts up (even before XP is installed.) I tried disabling 3d compiz-fusion effects, so I think that it is either due to an issue with my nvidia driver from envy (173.14.12) or the fact that I am on 64-bit. You guys still might have better luck with 6.5 RC, at least on 32-bit.

BTW: Masoris, according to this:
[http://www.hardwarezone.com/articles/view.php?id=2387&cid=6&pg=7](http://www.hardwarezone.com/articles/view.php?id=2387&cid=6&pg=7)
The 7100 series at most can get 1030 in 3DMark05, so your score isn't too bad.

---

### Post by Shaythong on 2008-08-21
> **mikedep333 said:**
> I just tried VMware Workstation 6.5 RC (6.5.0 build-110068) on Ubuntu 8.04.1 64-bit. 3D acceleration wouldn't work, as evidenced by a pop-up when my Windows XP VM starts up (even before XP is installed.)

You should try checking out this thread at the VMware community forum. I haven't tried the solution there myself, but it should work for you. Good luck!

[http://communities.vmware.com/message/1029944#1029944](http://communities.vmware.com/message/1029944#1029944)

Let us know how it goes, does 3D Acceleration work pretty stable on the RC1 release? :)

---

### Post by Masoris on 2008-08-27
> **mikedep333 said:**
> 
BTW: Masoris, according to this:
[http://www.hardwarezone.com/articles/view.php?id=2387&cid=6&pg=7](http://www.hardwarezone.com/articles/view.php?id=2387&cid=6&pg=7)
The 7100 series at most can get 1030 in 3DMark05, so your score isn't too bad.

I run 3DMark05 again on VMware 6.5.0 build-110068. And I got 779 points (66% faster than beta2), but it still very slow. :(

---

### Post by darco on 2008-08-30
What about the other settings you have for your VM? What do you have for memory settings? I see that VMWare recommends 512mb but I am curious if by maxing  out the mem settings this may help overall. I noticed in the Server edition, if i chose 2 processors rather than the default 1 my system goes haywire...I am going to d/l VMwareWS RC and see what I find.....

darco

---

### Post by darco on 2008-08-30
I installed the RC version  and I suddenly realized I no longer can access VMWare server but I was able to open all my vm  (3) w/WS ...
I like WS way more than Server....Enabled 2 processors, no issues, able to see all my USB drives.full screen mode, using 2 gigs of ram....man that Unity mode is pretty cool.....Running XP pro SP3 as guest...IE8 in PornMode rocks! 
I enabled 3D support and d/l CombatArms an Online combat game and yes there are glitches in the game, no screenshot but it was like playing w/the invisble man, I could only see partial Uniforms and weapons, but not the faces...kinda funny...oh well I can only imagine VMware only getting better as time moves on...

darco

---

### Post by irishdunn on 2008-10-10
I almost had to clean my keyboard off from the joysplosion I had about this announcement... but then I saw this thread and realize it might be too good to be true so far. Thanks for testing guys, keep it up!

---

### Post by whythankyou on 2008-10-10
Linux Guest next please!

---

### Post by -Rick- on 2008-10-10
> **whythankyou said:**
> Linux Guest next please!
[Already there]("http://www.cs.toronto.edu/~andreslc/xen-gl/")

---

### Post by s00laco on 2008-10-21
Can we please have some posts from users with "real" 3D graphics cards to test with?
I mean no offense, but a 7100 wouldn't even be able to play WOW in the best of circumstances, better than my old FX5500 used to, and would most definitely be the one major factor in the incredibly low 3Dmark scores. (you merely need to do some quick Google searches for nVidia 7100 benchmark results, and if you happen to even find any, you'll find they won't be far off the results posted here earlier in this thread)

If someone has a proper gaming machine with an 8800GT or even the deplorable 8600GTS would at least be a worthwhile test.
Also - the only way to really get a proper feel for this would be to test it both in the XP guest environment, and then test it on the same machine with a proper installation of XP (other drive, other partition, however you like) and compare the two tests.

I say XP because this is technically the gamer's OS of choice, though Vista 64 seems to be working fine for a lot of people these days, but they're still a minority over-all.

Specifics of the rest of the core components installed on the machine would also help us get a clearer picture of the operating environment.
I don't know if I'll be able to test this myself, but if I do, my machine ain't all that flash-hot either (though I at least have a 7600GT manufacturer overclocked - but even then, it's AGP)

edit: I would like to point out that while the majority of my post focuses on other OS's - the whole purpose of this thread is related to the functionality and practicality of using VMware to run 3D programs from a Ubuntu host; any question of "off topic" should be satisfied by this fact.

---

### Post by frumple on 2008-10-21
Just to add my 2 cents...

I using VMware 6.5 Beta with 3D acceleration on an ASUS A8Js notebook featuring a Nvidia Geforce 7700go card with 256MB dedicated NVRAM. 

I not a serious gamer, but I work with Solid Works parametric 3D CAD, and after spending years on dual boot, this is the first time I managed to get rid of my Windows partition and only boot onto Linux. The rendering performance is only a little lower than on the non virtual Windows, even on large assemblies. 

Also the Unity feature is really good, giving any windows application an almost complete integration onto Gnome. 

Before switching to VMWare 6.5, I've tried previous versions os VMWare, Qemu and Sun's VirtualBox, the latest is really good, but the software performance was a lot slower and their Seamless feature, analog to Unity, is buggier. Of course that VirtualBox is in constant evolution and possibly become a same level alternative for VMWare in a couple of years. 

Eduardo

---

### Post by Shaythong on 2008-10-21
I agree, the unity feature is really nice. The "exclusive mode" is a little buggy with full screen applications and stuff. If only VirtualBox had some type of 3D Acceleration like the new VMWare. :)

---

### Post by houdodu on 2008-10-27
> **Shaythong said:**
> You should try checking out this thread at the VMware community forum. I haven't tried the solution there myself, but it should work for you. Good luck!

[http://communities.vmware.com/message/1029944#1029944](http://communities.vmware.com/message/1029944#1029944)

Let us know how it goes, does 3D Acceleration work pretty stable on the RC1 release? :)

The forums seem broken. What did this solution include?

---


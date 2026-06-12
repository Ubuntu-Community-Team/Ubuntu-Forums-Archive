---
title: "Is there a System76 laptop with a higher end graphics adapter?"
date: 2012-06-27
forum: System76 Support
---

### Post by HDave on 2012-06-27
My Dell XPS crapped out and I need to score a new laptop ASAP.  I've been running Ubuntu for years, so a System76 is a no-brainer for me, but on the website there seems to be only display option seems to be "Intel HD Graphics 4000".

I do quite a bit of screen sharing, software development, virtual machines, heavy compiz, movie playing, 3d visualization work all of which stressed out the nvidia card in my Dell XPS laptop to the max.  I assume the Intel 4000 won't cut it.

I'm not really much of a gamer, so I don't need something too over the top.

---

### Post by brdmn on 2012-06-27
> **HDave said:**
> My Dell XPS crapped out and I need to score a new laptop ASAP.  I've been running Ubuntu for years, so a System76 is a no-brainer for me, but on the website there seems to be only display option seems to be "Intel HD Graphics 4000".


That's the GPU built into the Sandy Bridge processors.  I think I read somewhere in this forum that there are no extra slots in the S76 laptops, so you may not have the option to add a discrete graphics processor.

Update: This is the thread I was thinking about... [http://ubuntuforums.org/showthread.php?t=1905451](http://ubuntuforums.org/showthread.php?t=1905451)

---

### Post by 3Miro on 2012-06-27
In the past, there were System76 models with Nvidia GTX560 or GTX580 video cards. There was a bit of a slow time for System 76 machines around the time when Intel came out with new CPUs and Ubuntu moved to the 12.04 LTS. I would assume that higher end System 76 machines will be coming just around the corner.

BTW: I have Intel HD 3000 from System76 and the only thing I cannot do is wine video games. I can do virtual box and native Linux 3D stuff just fine. Intel 4000 should be fast enough for most tasks.

---

### Post by HDave on 2012-06-28
Thanks for the feedback guys.  I'm going to call them and see what the ETA is on a high-end graphics laptop.  I'll report back when I find out.

---

### Post by HDave on 2012-06-28
Finally heard back from their sales support. 

I am so bummed..they have nothing with a higher end graphics card and have no near term plans to have one either.


ARRGRGGGRG!!!!

---

### Post by 3Miro on 2012-06-28
Check with ZaReason:

[http://zareason.com/shop/Laptops/](http://zareason.com/shop/Laptops/)

---

### Post by Penguissimo on 2012-06-28
> **HDave said:**
> Finally heard back from their sales support. 

I am so bummed..they have nothing with a higher end graphics card and have no near term plans to have one either.


ARRGRGGGRG!!!!

Wait, they told me at the end of May that they would be testing systems with AMD cards and they should have a better idea of where they could go with those within a few weeks. By "no near term plans" did they mean they wouldn't have anything out next week, or that it could be another year?

I really want to go with S76, but it's been almost four months since they sold the high-end laptops. Should have ordered in February when I had the chance. :(

---

### Post by Carborundum on 2012-06-29
isantop answered this in another thread:
> **isantop said:**
> The problem is that if I say something wrong, and even if you don't hold it against me, someone else will. ;-) That and the fact that I really have no information about it. _We'll hopefully have it sooner than a year,_ but beyond that I don't have the information to get more specific.
My underlining.

---

### Post by Penguissimo on 2012-06-29
> **Carborundum said:**
> isantop answered this in another thread:

My underlining.

Oh yikes, hadn't seen that. Thanks for the catch!

If it could really be as long as a year, it might be time to start looking somewhere else :(

---

### Post by GOVATENT on 2012-06-30
I want to press buy right now so bad. But dell is offering some random laptop with an AMD gpu at the same price. I figure it's gotta be more reliable than the intel HD 4000. I don't dual boot or care for windows games. I just want my native linux games to work right and to be able to use Virtual box and multitasking to run fine. I want to support a linux company and not dell or some other crummy OEM which puts linux users as last. I think I might just go with the s76 anyways. As long as they will stand by to support the hardware with ubuntu i don't mind a performance hit. Although I'm coming from a very high end laptop which I'm selling to my brother for the price of this s76. I just don't like the trackpad in ubuntu. It's a macbook pro. :P I've been researching the intel hd 4000 for over a week now.

---

### Post by 3Miro on 2012-07-01
Intel HD 4000 is faster than some low end AMD and Nvidia Video cards. Intell still falls short of the very high end AMD and Nvidia, but they are good enough for regular desktop use. As I said earlier, I am using Virtual Box and external 1920x1200 monitor just fine on my Intel 3000.

AMD is a reliable company, but I am not sure how reliable DELL is, especially if you have to deal with Ubuntu support issues. Unless I want a very high end video card (i.e. GTX 670), I wouldn't go with anything other than System76. You should also check ZaReason, they have high end Nvidia laptops with pre-installed Ubuntu.

---

### Post by Penguissimo on 2012-07-01
> **3Miro said:**
> Intel HD 4000 is faster than some low end AMD and Nvidia Video cards. Intell still falls short of the very high end AMD and Nvidia, but they are good enough for regular desktop use. As I said earlier, I am using Virtual Box and external 1920x1200 monitor just fine on my Intel 3000.

AMD is a reliable company, but I am not sure how reliable DELL is, especially if you have to deal with Ubuntu support issues. Unless I want a very high end video card (i.e. GTX 670), I wouldn't go with anything other than System76. You should also check ZaReason, they have high end Nvidia laptops with pre-installed Ubuntu.

The biggest problem for me is that I need a laptop with a Firewire port since I do a lot of audio recording (and I do most of my gigs onsite, so a desktop isn't an option), and there just aren't any of those in the S76 lineup right now :( A better graphics card would be nice (since I also play a bit of Starcraft 2) if non-essential, but the Firewire port is unfortunately non-negotiable :(

---

### Post by jakobcreutzfeldt on 2012-07-02
The Intel HD 4000 graphics chip on the latest Ivy Bridge architecture is actually quite satisfactory for me.  I can run Amnesia: The Dark Descent on fairly respectable settings at a decent frame rate with a bit of tweaking.
  
*Edit: nevermind, I got the facts wrong here and mixed up AMD and Nvidia. *
Before you go and drop money on a Dell for its AMD card, stop and consider why System76 currently has nothing available like that. Their primary business is to offer systems which run seamlessly with Ubuntu. Currently, the laptops which use AMD *[Edit: no, Nvidia] *cards tend to use Optimus, allowing them to fall back to the integrated Intel chip when you're not doing anything that needs strong graphics computation. Optimus, if you search around online, simply does not work in Linux. Previously, System76 did a hardware multiplexer to make it work but they said that now they can no longer do it. On the other hand, you do have the Bumblebee project which is a FOSS attempt to bring Optimus support to Linux. However, that is quite new and almost certainly not ready for System76 to depend on yet. 

The point is that if you go and get that Dell or whatever just because it has an AMD card on it, don't expect it to be simple to get everything up and running with Linux smoothly. Chances are, you'll be stuck using the Intel chip only, despite having dropped some money to get the AMD *[Edit: this is false and only applies to Nvidia]*. Do a lot of searching online for forum posts by people with the laptop you want to try to verify that everything will work out of the box first.

---

### Post by Carborundum on 2012-07-02
> **jakobcreutzfeldt said:**
> The Intel HD 4000 graphics chip on the latest Ivy Bridge architecture is actually quite satisfactory for me.  I can run Amnesia: The Dark Descent on fairly respectable settings at a decent frame rate with a bit of tweaking.

Before you go and drop money on a Dell for its AMD card, stop and consider why System76 currently has nothing available like that. Their primary business is to offer systems which run seamlessly with Ubuntu. Currently, the laptops which use AMD cards tend to use Optimus, allowing them to fall back to the integrated Intel chip when you're not doing anything that needs strong graphics computation. Optimus, if you search around online, simply does not work in Linux. Previously, System76 did a hardware multiplexer to make it work but they said that now they can no longer do it. On the other hand, you do have the Bumblebee project which is a FOSS attempt to bring Optimus support to Linux. However, that is quite new and almost certainly not ready for System76 to depend on yet. 

The point is that if you go and get that Dell or whatever just because it has an AMD card on it, don't expect it to be simple to get everything up and running with Linux smoothly. Chances are, you'll be stuck using the Intel chip only, despite having dropped some money to get the AMD. Do a lot of searching online for forum posts by people with the laptop you want to try to verify that everything will work out of the box first.
Optimus is NVIDIA's technology. AMD uses something very similar called Hybrid Graphics mode. Unlike Optimus, Hybrid Graphics is officially supported under Linux with the proprietary Catalyst driver, but - from what I've read - tends not to work particularly well anyway.

---

### Post by jakobcreutzfeldt on 2012-07-02
Argh....you're right. I was thinking about it on my way to work that I needed to go back and fact check because I might have mixed up the two but you beat me to it.    I'm putting on my dunce cap now. :(

I've gone back and placed corrections in my original post so as not to spread my confusion.

Anyway, the point still remains that both AMD and Nvidia seem to be a bit of a pain in Linux, whereas Intel seems to generally work pretty reliably, albeit with less impressive power.

---

### Post by isantop on 2012-07-02
> **GOVATENT said:**
> I want to press buy right now so bad. But dell is offering some random laptop with an AMD gpu at the same price. I figure it's gotta be more reliable than the intel HD 4000. I don't dual boot or care for windows games. I just want my native linux games to work right and to be able to use Virtual box and multitasking to run fine. I want to support a linux company and not dell or some other crummy OEM which puts linux users as last. I think I might just go with the s76 anyways. As long as they will stand by to support the hardware with ubuntu i don't mind a performance hit. Although I'm coming from a very high end laptop which I'm selling to my brother for the price of this s76. I just don't like the trackpad in ubuntu. It's a macbook pro. :P I've been researching the intel hd 4000 for over a week now.

The HD 4000 will handle many Linux games very well. We tested a Gazelle with every title in the most recent Humble Indie Bundle on maximum detail settings (where applicable), and every title ran fine. In terms of reliability, You're going to be much better with Intel since A) there's less hardware to break, and B) the driver support with Ubuntu is much, much better. 

Intel graphics have garnered a reputation over the past few years for being very slow and unsupported. But the situation is now turned around completely. Intel graphics adapters feature full driver support out of the box in Ubuntu, with no additional drivers needed. On top of that, the recent Sandy Bridge and (particularly) Ivy Bridge chip designs have rendered low end discrete graphics completely obsolete.

---

### Post by dodo3773 on 2012-07-02
I am so bummed out you guys are not offering nvidia chips in your laptops anymore.

---

### Post by Penguissimo on 2012-07-02
> **dodo3773 said:**
> I am so bummed out you guys are not offering nvidia chips in your laptops anymore.

It's not really their fault, since Nvidia insist on putting this Optimus crap in their mobile GPUs and then refuses to support it on Linux. But I do wish we had any word on whether or not we'll be seeing AMD chips in S76 laptops anytime in the next couple months :(

---

### Post by brdmn on 2012-07-02
> **isantop said:**
> Intel graphics have garnered a reputation over the past few years for being very slow and unsupported. But the situation is now turned around completely. Intel graphics adapters feature full driver support out of the box in Ubuntu, with no additional drivers needed. On top of that, the recent Sandy Bridge and (particularly) Ivy Bridge chip designs have rendered low end discrete graphics completely obsolete.

The fact that Intel graphics works out of the box is a huge draw for me.  I suffered through ATI's proprietary drivers back in the day, and frankly, there is something very comforting about using non-proprietary drivers...

[Although, at least proprietary drivers for linux seem to be a bit more streamlined than those for Windows.  To get the scanner on my sister's HP multifunction printer working, I had to install what seemed like a gigabyte of software.]

---

### Post by GOVATENT on 2012-07-03
Update from me: I went for the system76. Playing the waiting game. I am very happy I went with them. Just buying it I had such a great experience with the company. No OEM could offer what they are giving me. I did a ton of research and the Intel HD 4000 will be a perfect fit for me. Plus knowing it should work good in linux is a plus for me. I don't like leaving ubuntu.

---

### Post by HDave on 2012-07-04
> **3Miro said:**
> Check with ZaReason:

[http://zareason.com/shop/Laptops/](http://zareason.com/shop/Laptops/)

Thanks for the tip, those are perfect, but WOW....expensive.  I may just bite the bullet and get a System76...stay tuned.  I've also heard that Dell is working on a high-end Ubuntu laptop...codenamed [project sputnik]("http://en.community.dell.com/techcenter/b/techcenter/archive/2012/05/07/developer-laptop-launches-project-sputnik.aspx").  I contacted Dell and currently it seems like a long way off...

---

### Post by Bluebearbevis on 2012-07-04
Good evening from Aurora, Colorado, home of System76.  Unbelievable, What happened to nVidia graphics?  I'm the owner of a Panp6 (gasp, from back in the good ol' days?) and soon will be upgrading to?  Sorry dudes off Parker Ave., but has anyone heard of R&J Tech?  You can get the computer that System76 used to sell, except you don't get their driver and you have to install ubuntu yourself.  Step it up and I'll still go with you guys, because your support is super fantastic and that too is important.

Richard

---

### Post by Penguissimo on 2012-07-04
> **Bluebearbevis said:**
> Good evening from Aurora, Colorado, home of System76.  Unbelievable, What happened to nVidia graphics?  I'm the owner of a Panp6 (gasp, from back in the good ol' days?) and soon will be upgrading to?  Sorry dudes off Parker Ave., but has anyone heard of R&J Tech?  You can get the computer that System76 used to sell, except you don't get their driver and you have to install ubuntu yourself.  Step it up and I'll still go with you guys, because your support is super fantastic and that too is important.

Richard

Just note that if you want to go that route, you'd probably need to opt for the AMD 7970M, since Nvidia's refusal to support this Optimus crap (used in all their new mobile GPUs) is the reason there's been such a delay in the new System76 laptops to begin with.

I too hope to be able to buy from System76, but I need to get a new computer pretty soon :( I've talked to a few people who have bought the Clevo computers being sold by R&J, and it seems like they've gotten everything working OK in various Linux distros, so I'm keeping my fingers crossed that our favourite team will get things together sometime in the next month or so!

---

### Post by Bluebearbevis on 2012-07-04
Hello again,

So now I'm curious.  I first installed Ubuntu on an old Dell Dimension Desktop when I replaced the hard drive and didn't have the wingdohs xp disc.  An nVidia 5200 something, awesome with Ubuntu Jaunty Jackalope.  Loving Linux and never looking back, I purchased a Pangolin Performance from System76 in late 2009.  Again nVidia, this time a g105m.  Always ultimately incredible performance after correcting(usually self inflicted)wounds. See past posts about System76 exemplary support.  12.04 64 bit working flawlessly on ol' Panny, guess I'll wait until nVidia gets it's act together, in the mean time, whom to write, where to post?  Tom?  Ian?

Sincerely,  Richard

---

### Post by GOVATENT on 2012-07-10
I get my laptop on the 12. One day left not counting tonight. I can't wait!! I was thinking of doing a video review for the florida loco team blog or miami local ubuntu user group.

---

### Post by isantop on 2012-07-11
> **GOVATENT said:**
> I get my laptop on the 12. One day left not counting tonight. I can't wait!! I was thinking of doing a video review for the florida loco team blog or miami local ubuntu user group.

Let us know if you decide to do the review! We'd love to hear your feedback, and we can even share it on our social networks if you wish!

---

### Post by 3Miro on 2012-07-11
> **Bluebearbevis said:**
> Hello again,

So now I'm curious.  I first installed Ubuntu on an old Dell Dimension Desktop when I replaced the hard drive and didn't have the wingdohs xp disc.  An nVidia 5200 something, awesome with Ubuntu Jaunty Jackalope.  Loving Linux and never looking back, I purchased a Pangolin Performance from System76 in late 2009.  Again nVidia, this time a g105m.  Always ultimately incredible performance after correcting(usually self inflicted)wounds. See past posts about System76 exemplary support.  12.04 64 bit working flawlessly on ol' Panny, guess I'll wait until nVidia gets it's act together, in the mean time, whom to write, where to post?  Tom?  Ian?

Sincerely,  Richard

Nvidia has problems only with Optimus (a.k.a. Hybrid Graphics). The older models that had just Nvidia graphics work great with 12.04 (as well as other versions of Ubuntu).

---

### Post by bakelitedoorbell on 2012-07-13
> **isantop said:**
> Intel graphics have garnered a reputation over the past few years for being very slow and unsupported. But the situation is now turned around completely. Intel graphics adapters feature full driver support out of the box in Ubuntu, with no additional drivers needed. On top of that, the recent Sandy Bridge and (particularly) Ivy Bridge chip designs have rendered low end discrete graphics completely obsolete.

My Serp5 has a nvidia 260M - how would that compare to the new integrated graphics?  Would a 260M now be considered low end?

---

### Post by isantop on 2012-07-13
> **bakelitedoorbell said:**
> My Serp5 has a nvidia 260M - how would that compare to the new integrated graphics?  Would a 260M now be considered low end?

You would definitely see equivalent or better performance on the HD 4000 graphics. The 260M was a high-mid range card when it was released, but would be considered lower end by today's standards.

---

### Post by HDave on 2012-07-13
Well, I just caved and ordered my Pangolin with the Intel graphics 4000.  I can't wait any longer and figured I could give it to my wife if things improve.  Their customer support said it runs compiz very well.  I hope it does...though I am sure I won't be running my 3D CAD vizualization stuff on it :-(

I'll report back once I get a chance to really use it.  I did max out the processors and memory so at least I can run a handful of Virtualbox VMs at the same time.

I've always had success with nVidia on laptops with Ubuntu in the past and am really disaapointed to hear that their new technology isn't working with Linux.  I guess this is what Linus was referring to when he said FU to nvidia during that speech a couple weeks back.  At the time, I thought he went overboard...now that it's hit me in the head, I'm reconsidering...

---

### Post by isantop on 2012-07-13
> **HDave said:**
> Well, I just caved and ordered my Pangolin with the Intel graphics 4000.  I can't wait any longer and figured I could give it to my wife if things improve.  Their customer support said it runs compiz very well.  I hope it does...though I am sure I won't be running my 3D CAD vizualization stuff on it :-(

I'll report back once I get a chance to really use it.  I did max out the processors and memory so at least I can run a handful of Virtualbox VMs at the same time.

I've always had success with nVidia on laptops with Ubuntu in the past and am really disaapointed to hear that their new technology isn't working with Linux.  I guess this is what Linus was referring to when he said FU to nvidia during that speech a couple weeks back.  At the time, I thought he went overboard...now that it's hit me in the head, I'm reconsidering...

This is exactly what he was referring to. Optimus, and Nvidia's refusal to work on getting it working in Linux.

---

### Post by GOVATENT on 2012-07-13
So fear not! I got my laptop Thursday Night. I've been using it for 24 hours and I love it!!! I already ran all my day to day stuff except for virtualbox. I also tested a lot of the games I want to play on here. Everything runs better than on my old laptop and even my desktop. I'm very happy with the power of the HD4000. Again you can't max all settings and go trigger happy, but I play most games at the 1080p option when available with average settings and it all plays great for me. This is the perfect computer. Video review to follow very soon. I just have been so busy.

---

### Post by Futurian on 2012-07-17
I use Nvidia's CUDA technology on graphics processing units for general purpose programming. This is called GPGPU. It gives you a parallel processing computer. My panp5 has limited capacity, but computers with more capable Nvidia cards can approach supercomputer performance.

CUDA works with Ubuntu 11.04 and 10.04 [http://www.nvidia.com/content/cuda/cuda-downloads.html](http://www.nvidia.com/content/cuda/cuda-downloads.html) . Maybe laptops could be developed with newer Nvidia graphics cards and older versions of Ubuntu. This alternative may be unappealing in some ways, but it would enable the use of more modern graphics cards for a broader range of uses with Linux.

I haven't been able to upgrade most of my Ubuntu installations since 11.04, in part because of the Nvidia issue. I do run 12.04 in VirtualBox on one system, but can't do my heavy computing (including GPGPU) in that environment.

GPGPU works on both Nvidia (programmed in CUDA or OpenCL) or AMD (programmed in OpenCL only, but that is fine), so there may be other possibilities.

---

### Post by 3Miro on 2012-07-17
> **Futurian said:**
> I use Nvidia's CUDA technology on graphics processing units for general purpose programming. This is called GPGPU. It gives you a parallel processing computer. My panp5 has limited capacity, but computers with more capable Nvidia cards can approach supercomputer performance.

The Tesla and the high end Quadro can beat small clusters, nothing that you can get on a laptop can ever compete with a supercomputer. If you need such a high end machine you should get a desktop and System76 does sell pretty powerful Nvidia desktops.

Wine games is the most GPU demanding apps you can ever hope to run on a laptop, and Intel 4000 is good enough for pretty much everything else.

> 
CUDA works with Ubuntu 11.04 and 10.04 [http://www.nvidia.com/content/cuda/cuda-downloads.html](http://www.nvidia.com/content/cuda/cuda-downloads.html) . Maybe laptops could be developed with newer Nvidia graphics cards and older versions of Ubuntu. This alternative may be unappealing in some ways, but it would enable the use of more modern graphics cards for a broader range of uses with Linux.

Last I checked (a few years ago), the main reason why CUDA worked only with older versions of Ubuntu was because Nvidia was very slow to support newer versions of GCC. I could use CUDA on newer versions if I install and use older GCC. I don't know if this is still valid.

At any rate, the reason why System76 doesn't use Nvidia has nothing to do with CUDA or Nvidia support for CUDA. Nvidia doesn't support Optimus, which includes all GPU functionality on the laptops.

> 
I haven't been able to upgrade most of my Ubuntu installations since 11.04, in part because of the Nvidia issue. I do run 12.04 in VirtualBox on one system, but can't do my heavy computing (including GPGPU) in that environment.

Can you run GPGPU under Virtual Box at all? Virtual Box tends to be slower in general and it doesn't work well with the GPU, for example you cannot play 3D games under Virtual Box. Am I wrong?

> 
GPGPU works on both Nvidia (programmed in CUDA or OpenCL) or AMD (programmed in OpenCL only, but that is fine), so there may be other possibilities.

Currently AMD has better GPU support for laptops than Nvidia, but while AMD hybrid graphics is getting there, it is not good enough yet.

If you absolutely must use Nvidia on your laptop, look at the ZaReason model with GTX670, but you may experience issues with Optimus. You can alternatively get an older machine with GTX560 or GTX580, those did not use Optimus and work quite well (although you will not get much of a battery life).

---

### Post by Futurian on 2012-07-17
Your points are all well-taken, 3Miro, and yes, it does take a high-end desktop with high-end graphics cards to come anywhere close to a supercomputer. But I can't lug a desktop around, so it is handy to be able to develop on a laptop and then transfer the code to the desktop machine. And System76 does indeed have some very good desktop machines for this purpose.

Optimus seems like a good idea; wish it worked better with Linux.

---

### Post by 3Miro on 2012-07-17
> **Futurian said:**
> 
Optimus seems like a good idea; wish it worked better with Linux.

On paper it is good, but unfortunately there are limitations in both Xorg and current Nvidia driver to make this practical. At most, some people have been able to set their machines to swithc graphics with reboot or restart of Xorg. System76 aims at providing smooth performance, hence they will not sell Optimus until it is works right.

I wish it worked well too, but unfortunately it doesn't.

---


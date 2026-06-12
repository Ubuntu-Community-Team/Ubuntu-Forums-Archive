---
title: "What do you think of the new GRUB?"
date: 2010-01-08
forum: The Cafe
---

### Post by llawwehttam on 2010-01-08
What do you think of the new grub? Personally I think it needs refining and shouldn't have been released yet but it looks like its going to work well in the future.

The thing i miss most is the password feature. It was so easy to put #Passwd -md5 yourhash   into grub legacy. It looks very promising though as the password setup I have seen with GRUB2 allows multiple users with different passwords and allows different levels of access.

---

### Post by markbuntu on 2010-01-08
I disto hop. Grub2 uses UUIDs. These change. This is problematic.

---

### Post by FuturePilot on 2010-01-08
> **markbuntu said:**
> I disto hop. Grub2 uses UUIDs. These change. This is problematic.

That is not Grub2 specific. Grub legacy can also use UUIDs. It depends on how the distro wants to do it. Ubuntu uses UUIDs

---

### Post by fromthehill on 2010-01-08
grub legacy works for everything I need.
it boots my OSses, It doesn't need to do anything more

If I add a new kernel I just edit a line in menu.lst
Keep It Simple Stupid

---

### Post by Techsnap on 2010-01-08
Very pointless at the moment, why even include it in Ubuntu. The fact that the Fedora team chose not to include it in something so cutting edge says something. Now for example I installed Ubuntu on one drive and GRUB on another, this took about 20 seconds to load the menu on each boot, that is a complete joke! Also it's not even final, when I tried Ubuntu 9.10 it was 1.97 beta 4, beta bootloaders, that's silly.

LILO has always worked great and I will continue to use it for many years.

---

### Post by NoaHall on 2010-01-08
> **Techsnap said:**
> Very pointless at the moment, why even include it in Ubuntu. The fact that the Fedora team chose not to include it in something so cutting edge says something. Now for example I installed Ubuntu on one drive and GRUB on another, this took about 20 seconds to load the menu on each boot, that is a complete joke! Also it's not even final, when I tried Ubuntu 9.10 it was 1.97 beta 4, beta bootloaders, that's silly.

LILO has always worked great and I will continue to use it for many years.

They were hoping to get it all tested ready for 10.04

---

### Post by Techsnap on 2010-01-08
> They were hoping to get it all tested ready for 10.04

In all honesty, I think that grub-legacy would be a wiser choice for an LTS.

---

### Post by llawwehttam on 2010-01-08
> **Techsnap said:**
> In all honesty, I think that grub-legacy would be a wiser choice for an LTS.

This is starting to be my opinion too but best wait and see what they come up with. You never know what they might pull out of their sleeves.

---

### Post by NoaHall on 2010-01-08
> **Techsnap said:**
> In all honesty, I think that grub-legacy would be a wiser choice for an LTS.

Well, progress has to happen somehow.. But I agree. A boot-loader is vital. You don't want a beta version of it.

---

### Post by mizukiov on 2010-01-08
no it sucks.

---

### Post by VCoolio on 2010-01-08
I'm not into bootloaders, so I don't care much. I voted ok, because it works and it doesn't come in my way. I know I could stop the old grub too from spawning, but anyway, karmic doing it automatically is fine with me. I don't dual boot anymore, so I rarely need to do something with the grub menu. Again, I'm no expert, this is just a moderate end user being ok with how it works.

---

### Post by 23meg on 2010-01-08
> **Techsnap said:**
> In all honesty, I think that grub-legacy would be a wiser choice for an LTS.

Which is to say: grub-legacy, which has been entirely unsupported upstream for some time, and boots our default filesystem thanks to an unofficial patch, would be a wiser choice for a release we'll have to support for five years?

---

### Post by markp1989 on 2010-01-08
i dont like the new grub, i dont know why they put a beta version in 9.10 , arch hasnt even updated to that yet.

---

### Post by blueshiftoverwatch on 2010-01-08
I voted "I don't care". I installed Ubuntu, saw that there was an update for Grub, installed it, and use it to boot between Ubuntu 9.10, Windows XP, and Windows 7. I don't really do anything deeper with it than that. I sometimes go days without turning off my computer anyway.

---

### Post by NoaHall on 2010-01-08
I locked the version of GRUB to legacy, because I want my system to be stable, not running beta. Well, a beta bootloader anyway.

---

### Post by Nerd King on 2010-01-09
Grub 2 has some nice features, but it's a tad slow for my tastes (given that on my desktop the BIOS takes an age to faff about, having the bootloader do it as well is just annoying). Having said that, it makes sense to put it out as it's basically usable and they can make sure it's ready for the LTS.

---

### Post by gn2 on 2010-01-09
I have Grub 2 on my Mint 8 laptop.
It works and that's all it needs to do.
I don't care whether it's Grub, Grub 2 or Grub 42 so long as it works.

---

### Post by Techsnap on 2010-01-09
> Which is to say: grub-legacy, which has been entirely unsupported upstream for some time, and boots our default filesystem thanks to an unofficial patch, would be a wiser choice for a release we'll have to support for five years?

Yeah because a beta bootloader is any better?

---

### Post by 23meg on 2010-01-09
> **Techsnap said:**
> Yeah because a beta bootloader is any better?

Depends on what "beta" refers to. Gmail was "beta" until a year or so ago. Firefox 3 carried the "beta" label when it shipped as the default browser on an Ubuntu LTS release, even though it was deemed as "RC quality" by upstream. 

"Beta" is just a label, one that doesn't point to a specific and universal degree of quality. Different projects have vastly different ways of classifying their release quality thresholds. It takes more than a single word to judge the quality or "readiness" of a piece of software, and you have to evaluate such labels on a per-project basis. For GRUB, here's a summary of what it means (from the upstream release planning document):

> Note:: We would like to claim that GRUB 2 is 'beta' at this stage.
'beta' means that GRUB 2 has the same usability as GRUB Legacy.

---

### Post by scouser73 on 2010-01-09
I suppose it's fine, but I leave the PC on for days at a time so I rarely see GRUB2.

---

### Post by Techsnap on 2010-01-09
> Depends on what "beta" refers to. Gmail was "beta" until a year or so ago. Firefox 3 carried the "beta" label when it shipped as the default browser on an Ubuntu LTS release, even though it was deemed as "RC quality" by upstream.

I mean as in taking longer to show the menu then booting the OS!

---

### Post by forrestcupp on 2010-01-09
To someone who just uses the default setup, there is really no difference between grub and grub 2.  Which is disappointing.  I thought it would look a little nicer.

> **23meg said:**
> Which is to say: grub-legacy, which has been entirely unsupported upstream for some time, and boots our default filesystem thanks to an unofficial patch, would be a wiser choice for a release we'll have to support for five years?
Good point.  In 5 1/2 years, Ubuntu will have long updated to a more stable grub 2, and grub-legacy will be extremely deprecated.  

Why would they put a dead bootloader in an LTS when there is already a stable one that is being developed?  Beta doesn't necessarily mean unstable.  Sometimes it just means that there are still features to add.

---

### Post by SlugSlug on 2010-01-09
I found it a  slower that legacy-grub, mine used to hang for about  2secs saying gurb loading....

anyway a miss-hap with backintime and I had to re-install - I went back to 9.04

---

### Post by bartos on 2010-01-09
i have screwed up two systems with it.
B.S.

---

### Post by Sahkolihaa on 2010-01-09
Voted no, as I have to disable my SATA controller for any ubuntu version to install correctly. If I leave the SATA controller enabled during install, GRUB throws a 'Error 15: File not found!' message at me once the system has rebooted from the install.

---

### Post by louieb on 2010-01-09
I voted YES for one reason - the os-prober really shines.

---

### Post by llawwehttam on 2010-01-09
> **louieb said:**
> I voted YES for one reason - the os-prober really shines.

I agree with that. That is one of its best features.

---

### Post by Miguel on 2010-01-09
It was a decision taken with hindsight. The reason to adopt grub2 is giving it a lot more mileage for 10.04. One great feature of grub2 is being able to boot from EFI. Although I don't know if this is enabled in the ubuntu build, this should be great for apples. 

There certainly are teething problems, but there are many other distros switching to grub2. Even Debian will switch to grub2 with Squeeze. There must be a reason behind this.

---

### Post by Twitch6000 on 2010-01-09
> **NoaHall said:**
> They were hoping to get it all tested ready for 10.04

So they put the pain on general users. The pain of waiting forever until the os loads. The pain of using an unstable version. I find that very stupid and silly.

---

### Post by NoaHall on 2010-01-09
> **Twitch6000 said:**
> So they put the pain on general users. The pain of waiting forever until the os loads. The pain of using an unstable version. I find that very stupid and silly.

If you don't like it, stick with Debian or a LTS.

---

### Post by Twitch6000 on 2010-01-09
> **NoaHall said:**
> If you don't like it, stick with Debian or a LTS.

Oh so now I should just leave humm. Wow I state a fact and get told to leave that is really welcoming. 

OH well I use OpenSuse anyways. Atleast it is stable.

---

### Post by NoaHall on 2010-01-09
> **Twitch6000 said:**
> Oh so now I should just leave humm. Wow I state a fact and get told to leave that is really welcoming. 

OH well I use OpenSuse anyways. Atleast it is stable.

No, I agree with you. I'm just saying, if you want stable, I wouldn't use the Ubuntu short term releases :) I froze the version of grub so it wouldn't update because I like stable.

---

### Post by Techsnap on 2010-01-09
> No, I agree with you. I'm just saying, if you want stable, I wouldn't use the Ubuntu short term releases  I froze the version of grub so it wouldn't update because I like stable.

Well what is it againt Twitch's comment if you don't like the new GRUB yourself.

---

### Post by NoaHall on 2010-01-09
> **Techsnap said:**
> Well what is it againt Twitch's comment if you don't like the new GRUB yourself.

I was just saying.

---

### Post by SonicSteve on 2010-01-09
Some of you will wonder why I bothered to post in this thread at all but  I figure that I'm a fairly typical Ubuntu user.

1. I've used it now for 3 years
2. It was my first good experience with Linux.
3. I have a very in depth understanding of computers and software but not programing.
So then,

From my point of view I didn't even notice that Grub 2 was being used. I can't say if using UUID's vs. /dev/sda1 mounts are better, worse or indifferent. 

I can say that I didn't notice it, which is probably a good thing. You only notice changes when one of two things happen, it breaks and you think it sucks, or it wow's you and think it's great. Since neither one happened I'm still quite indifferent until someone can convince to join their camp, two camps that I didn't even know till now existed.

---

### Post by phrostbyte on 2010-01-09
I think it's was a good idea, but it hasn't shown its potential in Karmic. GRUB 2 supports things like a fully graphical menu system with extensive scripting support. We need some artists to have at it. 

It's also has a much simpler architecture (2 stage bootloader instead of 3 stages), and just generally cleaner and more modular code then grub-legacy.

---

### Post by starcannon on 2010-01-09
Mixed feelings here.
For me it broke Wubi.

For me it works fine on a regular install.

I don't really see that it's any different as far as what I see when I'm booting my computer, so when it works I fall under the "don't care" vote.

When it doesn't work I fall under the "Don't like it" vote

---

### Post by Scruffynerf on 2010-01-10
Hate it. 

It seems especially bad on dual-boot machines - it appears to routinely *corrupt* the windows MBR, rendering it unfixable, even from a Windows Installation CD, using the -fixmbr- option (which kills grub2, renders windows AND Ubuntu unbootable, and the restore grub options just plain don work, as there is no longer a stage 1)

Personally, I think that it should have had much more beta testing over a wider audience.

---

### Post by cenzorrll on 2010-01-10
i've had absolutely no problems with grub2, there was a bit of a learning curve, but i think it has much better features than grub-legacy.  you can still easily edit menu entries, options etc.  and it searches for kernels on it's own, which makes dual booting/playing with other OS's much easier.

---

### Post by xuCGC002 on 2010-01-10
I absolutely DESPISE IT. Waiting 2 extra seconds for boot-time? This is just unthinkable. What were the devs thinking? Now my boot time is *5* seconds! FIVE WHOLE SECONDS!

---

### Post by hbtorana on 2010-02-03
Basically completely annoying and of no use to the ordinary user.
Has serious problems.
I have 3 tb drives, 8gb ram, dual quad core. Windows vista 64 starts in under 8 seconds. (very slim) and full startup of v64 takes about 15 seconds max.
koala install from cd, boot at least a minute. sometimes it randomly does not find the buntu partition and drops to some completely useless prompt.
Seriously get rid of it.  If someone wants it they can choose to install it.
Crap totally crap.  

I installed linux cause I was sick of waiting for windows, now it is even more annoying than windows.  

And then the xserver is a bloody joke as well. Using over 500mb ram with no apps open. open firefox and it balloons out to 1.2gb ram.

---


---
title: "can you recommend a distro that will teach me abit more about linux, please?"
date: 2006-08-20
forum: The Cafe
---

### Post by ice60 on 2006-08-20
hi, i only just installed Dapper yesterday, and i realised i can get it setup and configure everything without any problems, which i'm very happy about. 

however, i want to learn more about linux, but i tend to get abit side tracked with the internet, so if i don't really have a problem with a distro my learning grinds to a halt.

so, can you recommend a distro for me to try out? it doesn't necessarily have to be very difficult to setup, i don't think i'll enjoy that! just something that will let me learn abit more. all i really want it to have is a decent package manager and for it not to have to run KDE. the only distros i've used properly are Ubuntu and SUSE.

i was thinking of Slackware or Arch. what do you think? thanks.

---

### Post by Kernel Sanders on 2006-08-20
> **ice60 said:**
> hi, i only just installed Dapper yesterday, and i realised i can get it setup and configure everything without any problems, which i'm very happy about. 

however, i want to learn more about linux, but i tend to get abit side tracked with the internet, so if i don't really have a problem with a distro my learning grinds to a halt.

so, can you recommend a distro for me to try out? it doesn't necessarily have to be very difficult to setup, i don't think i'll enjoy that! just something that will let me learn abit more. all i really want it to have is a decent package manager and for it not to have to run KDE. the only distros i've used properly are Ubuntu and SUSE.

i was thinking of Slackware or Arch. what do you think? thanks.


Gentoo. If you can get to grips with that, you'll learn a LOT about linux.

---

### Post by Reshin on 2006-08-20
> ***John* said:**
> Gentoo. If you can get to grips with that, you'll learn a LOT about linux.

Seconded

---

### Post by ice60 on 2006-08-20
> ***John* said:**
> Gentoo. If you can get to grips with that, you'll learn a LOT about linux.

thanks, i will try Gentoo at some point, but not on the computer i'm going to use because i have a much faster computer i can put Gentoo on and i know it will irritate me knowing that when i'm watching the GCC.

i forgot to say i was thinking of BSD too, i think the one that's just recently been realised to something like 6.01. documentation and/or other support would be good too.

---

### Post by christhemonkey on 2006-08-20
Thirded :p

---

### Post by lizzard on 2006-08-20
I'd suggest [Gentoo ](http:www.gentoo.org) too.
It's high configurable and you will do a lot of configuration by yourself, so you will learn more about how a linux system is working.

---

### Post by tseliot on 2006-08-20
Try Arch if you want to learn about BSD init scripts and some manual settings **without** having (necessarily) to compile things from scratch.

---

### Post by jimmygoon on 2006-08-20
Maybe after Gentoo or even possibly before it, you could try LFS (linux from scratch)... They've got a book and you use a guide to literally install linux... from scratch.

---

### Post by ice60 on 2006-08-20
well, maybe i should think about Gentto then, especially considering the support it has. i suppose i can put it on this computer (the faster one) and maybe put Arch on the other. that would be great :cool: then BSD after that :p 

thanks everyone for the help :)

---

### Post by ice60 on 2006-08-20
OK, i'm going to get both Gentoo and Arch. does gentoo have more then one version? i thought i heard it has something like a stage1 stage2 and stage3 installs. is that correct? 

if i have a x86 and i start from [here](http://gentoo.inode.at/) is this the download i need below? thanks (i must have been wrong about the different stages, i didn't see them)
 
/releases/x86/current/installcd/install-x86-minimal-2006.0.iso

[color=blue]EDIT[/color] OK these are the stages, what should i get?
[http://gentoo.inode.at/releases/x86/current/stages/](http://gentoo.inode.at/releases/x86/current/stages/)

---

### Post by christhemonkey on 2006-08-20
From wikipedia:
[QUOTE='http://en.wikipedia.org/wiki/Gentoo_Linux#Stages']Stages

Traditionally installation could be started from one of three base stages:

    * Stage 1: System must be bootstrapped and the base system must be compiled.
    * Stage 2: System has already been bootstrapped, but the base system must be compiled.
    * Stage 3: System has already been bootstrapped and the base system already compiled.
[/QUOTE]

Gentoo reccoments stage 3 installs:
> From November 2005 the installation documentation recommends a stage 3 install and optional recompilation of the system after the installation using custom compiler settings (CFLAGS/USE flags) to create a more optimized system.


---

### Post by John.Michael.Kane on 2006-08-20
Ice60 theres a Gentoo live-cd aswell

Gentoo Minimal Installation CD would be an option.Note You can use this Installation CD to install Gentoo, but only with a working Internet connection.

---

### Post by ice60 on 2006-08-20
thanks, christhemonkey :) i'll do the stage3 then, it sounds good to me.

SD-Plissken, thanks. i just remembered i've got the gentoo livecd somewhere, i'll have a look for it and try it out.

anyway, while i waited for someone to help me pick which Gentoo stage to get, i started downloading Arch. i installed it and all i can say so far is Pacman is pretty quick. that's all i can say because all i've done is update afew things. although i'm in the middle of installing Gnome now :cool: thanks for all the help :)

---

### Post by cstudent on 2006-08-20
I believe that only stage3 is suppoorted now. Gentoo also has some very good documentation in helping you install it.

---

### Post by croak77 on 2006-08-20
I give a thumbs down to Gentoo. I don't think you will learn a lot about linux but more about Gentoo's linux. If you want to learn about linux, I'd suggest coming up a task you want to do. Like compiling your own kernel. And then read some docs and try it out. No real point installing Gentoo unless you really want to use Gentoo distro tools.

---

### Post by hanzomon4 on 2006-08-20
> **croak77 said:**
> I give a thumbs down to Gentoo. I don't think you will learn a lot about linux but more about Gentoo's linux. If you want to learn about linux, I'd suggest coming up a task you want to do. Like compiling your own kernel. And then read some docs and try it out. No real point installing Gentoo unless you really want to use Gentoo distro tools.

I agree with that, because you can take it one step at a time without getting lost.

---

### Post by papangul on 2006-08-20
I also agree with that (thumbs down to Gentoo), if you use gentoo you just learn about kernel compilation, options available for compiling individual packages and the settings of some config files in /etc. 

If I were you I would try to install LFS.

---

### Post by GhostDawg on 2006-08-20
One thing about Gentoo, if you have patients to watch it compile all those programs for hours & hours go right ahead. But I use Sourcemage instead of Gentoo. It's a source based distro.

I would start with Archlinux, Crux, or even Slackware!

---

### Post by X.Cyclop on 2006-08-20
You can use any distro.

It's the same, no matter if you're using Ubuntu or Gentoo. You'll learn the same commands, the same programming languages and you'll have the same packages.

The only difference is that you'll need to compile EVERYTHING instead of marking apps in Synaptic (or typing apt - dpkg).

;)

---

### Post by DoktorSeven on 2006-08-20
"As the old saying in the Linux community goes, 'If you learn Red Hat, you learn Red Hat. If you learn SuSE, you learn SuSE. But if you learn Slackware, you learn Linux.'"

:)

---

### Post by LKRaider on 2006-08-20
I would start with a Debian minimal install and configure my way up from there. You'll learn how to use the CLI, the commands and packages/programs, all that is useful for any linux out there, without being hassled by re-compilations all the time and dependency-hell, but at the same time being free to manually compile anything you want if so you wish.

Also, on that same system you can compile your own custom kernels as in any other distro and I would recommend you try it.

Mess with it, blow it up, whatever. If all goes awry, it is simple to reinstall it to a step you already feel confortable with (with extra packages), without waiting for it to recompile from scratch yet again.

That being said, you could do the same with Ubuntu also.

---

### Post by Kindred on 2006-08-21
Yeah, Arch is beautiful.  Good luck.

---

### Post by ice60 on 2006-08-21
it's seems you all travel around in groups, the recommend, ot not to recommend Gentoo, i mean.

well, i installed Arch and i really like it. there's a fair bit on manual configuration during the install, then when you first bootup all you have is a root login and the Pacman package manager. so you have to build the whole system form there.

it installed perfectly, apart from one thing, i couldn't get xorg configured, i even tried running the Dapper livecd and taking that xorg, but the Dapper livecd must have something it filters xorg through because it as alot of things i don't have loading up.

i tried writting it manually then adding bits from all of these ways of configuring xorg - installing and running hwd like this - hwd -x, then 'X -configure', then xorgconfig, then hwd -s, then xorgcfg -textmode which finally allowed me to get to the desktop :cool:

i'll come back to this thread when i next want to try a new distro to decide what to try next. i think i should try something without a package manager so i'm forced to compile everything. i'm really bad at finding deps. if something doesn't work first time i tend to go crazy and install loads of libs which i don't need. i have to start reading the files which are created during compilation to find the deps. needed

---

### Post by garba on 2006-12-27
> ***John* said:**
> Gentoo. If you can get to grips with that, you'll learn a LOT about linux.

yes, gentoo is the best distro to fool yourself into believing that you learnt something about a *nix like os :rolleyes:

---


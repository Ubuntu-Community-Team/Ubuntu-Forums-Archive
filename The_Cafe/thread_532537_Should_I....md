---
title: "Should I..."
date: 2007-08-22
forum: The Cafe
---

### Post by kiv on 2007-08-22
I have been using Ubuntu on my pc (single booting) for 8 months now & I love it.

However, I have just purchased a new laptop to take to uni to study computing. Which, no doubt, will invlove some windows based object orientated programming.

The laptop - Philips X58:
Intel Core 2 Duo
2gb Ram
120gb hard drive
Intel 950 graphics
Bluetooth,firewire etc...
Windows Vista.

Now I LOVE Ubuntu and I want to install it on my laptop. At least i think I do, however, something is holding me back and I don't know what. Maybe its because its new. Maybe it's because of the programming at uni. each time I run the live cd on my laptop I get closer & closer to actually installing it.

I think I just need some encouragement and solutions to the programming. I also do alot of web design, so anything on that front would be helpful too. 

Any comments regarding particular variations of ubuntu/linux that you prefer/may be better to install on a laptop will be welcome too.

---

### Post by Jamie Jackson on 2007-08-22
I'm running Ubuntu with XP in a Virtual Machine. Of course you have to have the XP license to do this legitimately, but you might not know that you can do the VM stuff (with VMWare Server, even) legitimately and for free.

I have a core 2 duo and 2GB RAM, and it runs pretty smoothly (not so with 1GB RAM).

I rarely use the Windows, even though I'm in a 100% Windows (on the desktop) corporation.

Does that help?

---

### Post by jimrz on 2007-08-22
dual boot?

---

### Post by blithen on 2007-08-22
There are INSANE amounts of small programming tools. Gedit is one of them actually, it has syntax high lighting. If you want something a little better then that go with SciTE Text Editor. But this also depends on what programming language you want to use. I only do a tiny amount of python so this is perfect for me. Good luck!

---

### Post by WanderingKnight on 2007-08-22
> There are INSANE amounts of small programming tools. Gedit is one of them actually, it has syntax high lighting. If you want something a little better then that go with SciTE Text Editor. But this also depends on what programming language you want to use. I only do a tiny amount of python so this is perfect for me. Good luck!

He was talking about Windows development.

If so, I'll back the VMWare suggestion. Though, personally, I would switch careers (do something related to UNIX programming :D) [j/k].

---

### Post by Jamie Jackson on 2007-08-22
As a head start, here is how ridiculously easy it is now to install the (free) vmware server:

echo -e '\ndeb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main\n' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install vmware-server

During this process, it asks for a serial number, of which I got five by registering with VMWare (again, for free).

The thing VMWare doesn't give you for free is VM creation software, but there are online services that do this for you very easily. For instance, this one does it, for free--no registration. [http://www.easyvmx.com/](http://www.easyvmx.com/)

I was shocked I could use all this powerful software for free, easily, and legitimately.

---

### Post by igknighted on 2007-08-22
Why would your Uni REQUIRE windows development tools?  I have never heard of such a thing.  We did all our development in OO languages in a Mac lab (I used Linux outside of lab) and learned CLI/text-editor.  My second uni programs mainly on Gentoo and FreeBSD machines.

The only language that would require you to use windows is C#.  I rather doubt you would be in a C# class unless you took something very specialized.  I would go without windows and express shock and outrage at the thought of using it if they try to make you.

---

### Post by kiv on 2007-08-23
I am aware of VM stuff but have never tried it as i do not have a legit copy of windows xp. what is the vm server that is free and legit?

Also i forgot to mention that I do not wish to dual boot on my laptop.

Oh and i found out from a friend already doing the bsc computing course that it is C# (C sharp) that I will be using.

---

### Post by popch on 2007-08-23
> **kiv said:**
> i do not have a legit copy of windows xp. 

Your OP says that your laptop came with Vista. The Windows license I am familiar with allows me to downgrade, i.e. to use an older version of the software than the one I have a license for.

In that case, you could legally install XP in place of Vista, provided you have the installation material.

Read your license.

---

### Post by kiv on 2007-08-23
> **popch said:**
> Your OP says that your laptop came with Vista. The Windows license I am familiar with allows me to downgrade, i.e. to use an older version of the software than the one I have a license for.

In that case, you could legally install XP in place of Vista, provided you have the installation material.

Read your license.

Ahh I remember reading that somewhere in the past! .. thank you!

So install ubuntu & then run xp in a virtual machine.. what VM solution would you all recommend?

---

### Post by popch on 2007-08-23
> **kiv said:**
> Ahh I remember reading that somewhere in the past! .. thank you!

So install ubuntu & then run xp in a virtual machine.. what VM solution would you all recommend?

That's certainly what I would recommend. In fact, that's my setup at home at the moment.

Since I am not a student any more and have money, I went to the expense of actually - gasp - ***buying*** VMWare, which is a very powerful beast.

---

### Post by igknighted on 2007-08-23
> **kiv said:**
> I am aware of VM stuff but have never tried it as i do not have a legit copy of windows xp. what is the vm server that is free and legit?

Also i forgot to mention that I do not wish to dual boot on my laptop.

Oh and i found out from a friend already doing the bsc computing course that it is C# (C sharp) that I will be using.

Ouch on the C#

I am sure that if you are a CS student you will have access to XP for free.  Most Uni's are a part of the MSDNAA.  Just by being in a CS course I was able to download Vista Business, XP Pro, MS Virtual Machine (or w/e its called), .net and a few more things.  Its a good deal if you have use for them ;)

Any reason you are so against dual booting?  It seems like it would be the best solution for you.

---

### Post by igknighted on 2007-08-23
> **popch said:**
> That's certainly what I would recommend. In fact, that's my setup at home at the moment.

Since I am not a student any more and have money, I went to the expense of actually - gasp - ***buying*** VMWare, which is a very powerful beast.

Why would you buy a free program?  You just need to register on their site for a serial #.  I know they make a more advanced version, but I don't see what it offers that server does not.

---

### Post by kiv on 2007-08-23
> **igknighted said:**
> Ouch on the C#

I am sure that if you are a CS student you will have access to XP for free.  Most Uni's are a part of the MSDNAA.  Just by being in a CS course I was able to download Vista Business, XP Pro, MS Virtual Machine (or w/e its called), .net and a few more things.  Its a good deal if you have use for them ;)

Any reason you are so against dual booting?  It seems like it would be the best solution for you.

Im against dual booting becase it seems a bit defeatist to me. In that I want to do everything ubuntu. Also, if im dual booting it makes me feel like "this is silly cos i could do everything in xp" - which is not what I want to be feeling cos I love ubuntu and I am growing to hate windows more and more.

The vm solution does sound about the best option atm. What is the best VM setup ?

---

### Post by popch on 2007-08-23
> **igknighted said:**
> Why would you buy a free program?  You just need to register on their site for a serial #.  I know they make a more advanced version, but I don't see what it offers that server does not.

Sorry, slight omission. I meant to say that I bought VMWare ***Workstation.*** That's not free but worth every buck I paid for it.

If you do not need all those functions, you will be perfectly fine with VMWare server or VMWare player.

---

### Post by Jamie Jackson on 2007-08-23
> **kiv said:**
> Ahh I remember reading that somewhere in the past! .. thank you!

So install ubuntu & then run xp in a virtual machine.. what VM solution would you all recommend?

I suggested one in post #6: VMWare Server (I gave some install commands for it.) It's slick.

---

### Post by kiv on 2007-08-23
> **Jamie Jackson said:**
> I suggested one in post #6: VMWare Server (I gave some install commands for it.) It's slick.

thank you very much!

---

### Post by kiv on 2007-08-23
now i need a web design solution!

im currently using dreamweaver.. I like using a combo of code plus wysiwyg. Is there a good alternative you can recommend.

If so .. i will install ubuntu on my laptop tonight..

---

### Post by SOULRiDER on 2007-08-23
I have the same problem actually, at Uni we use Visual Studio for programming in .NET C++. I of course hate it. Since i dont want to install windows on my computer (and it actually doesnt want to either for some reason....) what I do is use VMWare and thats it...

---

### Post by Foxmike on 2007-08-23
I heard tha NVU is a good editor... I doubt you find a complete remplacement of Dreamweaver, tho

---

### Post by kiv on 2007-08-23
Im about to install ubuntu now..

thanks all.. I'll be back later to tell you how it went.

---

### Post by igknighted on 2007-08-23
> **kiv said:**
> now i need a web design solution!

im currently using dreamweaver.. I like using a combo of code plus wysiwyg. Is there a good alternative you can recommend.

If so .. i will install ubuntu on my laptop tonight..

Quanta+ is the way to go.  My boss bought me Dreamweaver for working on our website, and I have since given it up in favor of Quanta+.  The WYSIWYG is not as advanced as Dreamweaver (I'm not sure any wysywyg is), but the code completions and everything else are better in Quanta+.

NVU is an older, abandoned project.  There has been some talk of it coming back under the name Kompozer or Compser, possibly by the Mozilla team.  So I would avoid it for now, but keep your eyes open.

---

### Post by kiv on 2007-08-23
thanks. im right in guessing quanta is open source?

---

### Post by igknighted on 2007-08-23
> **kiv said:**
> thanks. im right in guessing quanta is open source?

Yes.  It is a KDE app though (although I don't think it imports the kde-libs as dependencies... at least portage didn't bring them in on my gentoo box).

Link: [http://quanta.kdewebdev.org/](http://quanta.kdewebdev.org/)

---

### Post by Jamie Jackson on 2007-08-23
> **kiv said:**
> now i need a web design solution!

im currently using dreamweaver.. I like using a combo of code plus wysiwyg. Is there a good alternative you can recommend.

If so .. i will install ubuntu on my laptop tonight..

I hope you find something, I never did. All the Linux wsiwyg editors that I found were terrible, for one reason or another. (Well, I never buy software, i just look for free stuff, so I didn't evaluate any commercial stuff.) However, I rarely ever use a wysiwyg editor, even when I was on Windows, opting instead for a text-editor. (I settled on Eclipse.)

...of course wysiwyg vs. text is purely a personal preference, so I'm not trying to push you toward text editing.

---

### Post by madcow72 on 2007-08-23
Just wanted to put in my 2 cents on this.  I totally agree with you on running a VM over dual boot.  (Dual booting gets REALLY old after just a few times!)  I used to run VMware on both of my computers, but have now switched over to Innotek's vmserver.  It was actually way easier to set up than VMWare and I've had less problems with it also than VMWare.  

Often, for some unexplainable reason, some permissions would change on my virtual machine with VMWare and I would be unable to open it when I needed to.  Innotek's version does not have these problems, which was the deciding factor.

---

### Post by kiv on 2007-08-23
quanta looks a bit.. well ... outdated.

arg might have to run dreamweaver in a VM. 

whats the performance hit for photoshop/dreamweaver while using VM?

---

### Post by madcow72 on 2007-08-23
I have a 2.4GHz P4 processor with 1.5GB RAM, and I barely notice the difference with those programs in my VM as compared to a native install.  Your specs are better than mine, so my guess is things'll work just fine.

---

### Post by igknighted on 2007-08-23
> **kiv said:**
> quanta looks a bit.. well ... outdated.

arg might have to run dreamweaver in a VM. 

whats the performance hit for photoshop/dreamweaver while using VM?

It's probably because Gnome can't theme QT apps properly.  It looks great in KDE :D.  Although if you were refering to the website, yeah... I laughed really hard at a web developer site that looked like that.

---

### Post by kiv on 2007-08-23
> **madcow72 said:**
> I have a 2.4GHz PII processor with 1.5GB RAM, and I barely notice the difference with those programs in my VM as compared to a native install.  Your specs are better than mine, so my guess is things'll work just fine.

thanks for clearing that up.

---

### Post by madcow72 on 2007-08-23
A quick note:  Right after you install your Windows Virtual Machine, the virtualization will look pretty bad until you install either "VMware tools" (VMWare) or "Guest Additions" (VirtualBox) after making your Windows Virtual Machine.  This will greatly enhance the visual performance of the virtual machine and make it look close to a native install.

---

### Post by kiv on 2007-08-24
thanks! Im guessing there are guides on here for all of that?

---

### Post by lyceum on 2007-08-24
I feel your pain. I think it has something to do with being new. Like paining your new car. When I got my last laptop it came with XP. I never even say it once. But I did sit there for a bit thinking before approving the install. I am glad I did though. My next laptop will have Ubuntu by default.


:popcorn:

---

### Post by Jamie Jackson on 2007-08-24
> **kiv said:**
> thanks! Im guessing there are guides on here for all of that?

Just take it a step at a time & come back for help when you're ready.

---

### Post by kiv on 2007-08-27
well I have ubuntu installed on my laptop & I the world is now a much better place.

Lat night I installed virtualbox and managed to get xp running like a dream - all ready for when I need to program in C# at uni.

Thanks guys.. once again you have been fantastic!

:popcorn:

---


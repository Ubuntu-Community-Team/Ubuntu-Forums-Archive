---
title: "- Windows inside Ubuntu - QUESTIONS"
date: 2005-12-18
forum: The Cafe
---

### Post by nalmeth on 2005-12-18
Everyonce in a while I come across a thread somewhere talking about installing Windows inside Linux of different sorts, and recently came across one for Ubuntu:

[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

This is attractive for me, because I think the idea of running Windows inside of Ubuntu is very enticing! Also, while gaming is very possible under Ubuntu, I wonder if it would be easier to just install windows under Ubuntu and run games from there. I think I already have a Windows CD somewhere, compiling cedega failed (I will post this problem when I get home from work tonight), and I don't want to pay for transgaming.

But before I try this, I have a few questions for anyone who might already have tried, or anyone who has heard about this:
Will Windows actually be running on X? Will Ubuntu still be active? 
  --If so, what kind of performance do you get running 2 OS's at the same time? 
    --If poor, is it a worthwhile solution to play games (high 3D-accel)?

Even if you don't tell me what I want to hear, I think I would do this anyway, for the fun of it, but please tell me anything at all you know about this topic. I will have more questions to follow I'm sure.

thanks folks

---

### Post by tageiru on 2005-12-18
[QUOTE=nalmeth]Will Windows actually be running on X? Will Ubuntu still be active?[/QUOTE]
Well Windows would render its graphics onto a SDL window mimicing a graphics card. It is just like mplayer when it is using SDL output.
[QUOTE=nalmeth]--If so, what kind of performance do you get running 2 OS's at the same time?[/QUOTE]
Not very good
[QUOTE=nalmeth]--If poor, is it a worthwhile solution to play games (high 3D-accel)?[/QUOTE]
Forget about 3d-accelerated games.

---

### Post by Rackerz on 2005-12-18
[QUOTE=tageiru]Well Windows would render its graphics onto a SDL window mimicing a graphics card. It is just like mplayer when it is using SDL output.

Not very good

Forget about 3d-accelerated games.[/QUOTE]

Thats exactly what i expected to hear, but not what i wanted to hear.

---

### Post by nalmeth on 2005-12-18
me too unfortunatly..

any suggestions otherwise?

I don't want to reboot to play games..

If your idea is winex / cedega based, I will post my cedega problems in the gaming forum later tonight.

---

### Post by Master Shake on 2005-12-18
Haven't tried it, but VMWare has a free player...  Methinks I'll test this out this week...

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

EDIT:  Never mind.  You need the full version of VMWare for that.

---

### Post by ember on 2005-12-18
Well, the performance in VMWare Windows is o.k., but not superior - it is not the thing you will want to use, if you play games, but it's very useful for development and testing.
If you are more interested in games, I can recommend a membership option for Cedega, I was able to play Warcraft III and Frozen Throne with it, Warhammer 40 K worked halfway at that time. I guess, it's better now, I just do not have the time to play anymore (or if I manage to, I use GameCube or Xbox).
If it's standard applications, try wine (free) or Crossover Plugin (commercial).

Best,
ember

---

### Post by nalmeth on 2005-12-18
Cool, thanks for replies.

If it means paying for cedega/transgaming, I will pass because I do have my xbox, fully decked out too. I actually had to use it as a computer for a while...

I think I may try Crossover, and I'm going to keep working on getting Cedega compiled.

---

### Post by xequence on 2005-12-18
I ran XP in XP with VMware and it was horrible. Ofcourse, even one XP doesent go well in 192MB RAM so...

I doubt you could play doom 3 or UT2004 at 1600*1200 resolution, but you should be able to get some older games running.

---

### Post by ember on 2005-12-18
[QUOTE=nalmeth]
If it means paying for cedega/transgaming, I will pass because I do have my xbox, fully decked out too. I actually had to use it as a computer for a while..
[/QUOTE]

Well - it's 5$ a month and you have to sign for only 3 months. That's about two drinks in a club (at least in Germany), plus you support a company that helps open source development (at least I think, things from cedega are getting back into winex after a while).
So maybe you'll give a try.

---

### Post by nalmeth on 2005-12-18
True enough man. 
It's not like I can't afford it. But look at it this way. I would rather spend hours to get it going for free. Hours in which I could be working and easily make up the cost (or spending it on a couple drinks). It's really about freedom. Why should I have to pay even minimally to run games that I have already paid for?
I thought a major point about open-source was that if somebody made a product, released the code, and then charged you to use it, somebody else could take that code and make a free version. Granted, a project like cedega is huge, and requires lots of developers, and incidentally, money. It would be a huge undertaking for anyone to open it. 

Sort of like a situation I had with a buddy whose computer he wanted to setup with ubuntu. The problem was that his USB Wireless adapter needed a driver that wasn't available freely. His only option was to pay a company (linuxiant) $20. He was not impressed, nor was I. Why should he have to pay again for a driver he has already paid for? 
BTW The driver on the CD did not work. I tried a program that was supposed to setup a windows wireless driver. 

Well now his computer is sitting idle, because windows will not reinstall, and ubuntu is useless with no internet.
Sorry, not useless, but you know what I mean.

Please don't take my words out of context, because these are basically isolated incidents. I do intend to compile cedega for free, and after I am impressed by their product, I may donate.

When I installed Ubuntu, it was under the idea that it will be totally free, and always free. I intend to stick to that and not pay a dime for more services.

PS
I am planning to donate to many specific open-source outlets that have really earned my appreciation and respect. I am not just a cheap-skate :D 
Linux has saved me a lot of money, which I don't desperately need, and I will support the community.

---

### Post by imagine on 2005-12-18
[QUOTE=nalmeth]But before I try this, I have a few questions for anyone who might already have tried, or anyone who has heard about this:
Will Windows actually be running on X? Will Ubuntu still be active?[/QUOTE]
The whole concept is called virtualisation, that means a virtual machine, a virtual computer is created on top of the host system (Ubuntu in your case). In that virtual machine you can install an operating system just like on a real computer.
That got nothing to do with the X server, the applications in the virtual machine don't know anything about the host system. (Of course you need the X server to display the virtual machine though)

[QUOTE=nalmeth]If so, what kind of performance do you get running 2 OS's at the same time?[/QUOTE]
With a current version of VMware about 95% of the host system. 
However you need enough memory for both Ubuntu with all its applications and Windows with all its applications together. If the virtual machine needs to start swapping then it gets much slower.
Just remember: There's only one thing that's better than much RAM: Even more RAM!

[QUOTE=nalmeth]If poor, is it a worthwhile solution to play games (high 3D-accel)?[/QUOTE]
3D acceleration inside the virtual machine is sort of experimental [1] and of course it also depends on *what* games you want to play. Quake 4 needs way more resources than eg Warcraft. Other virtualisation software as Qemu doesn't have 3D acceleration yet AFAIK.
However I don't have any real experience with that, so it would be nice if you could try it out and report back here : )

Of course you need working 3D acceleration in your host system (Ubuntu) to even think about using DirectX-accelerated games in the guest system.




[1] [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d.html)

---

### Post by nalmeth on 2005-12-18
hmmm 
qemu was the way I was going to go originally, but no 3D supports scratches that idea.
I heard VMware was commercial, but if I can find a free / trial version I will definatly give it a go and report my findings.

I wish there was some WindowsLite version or something, but what can you do?

What if I ran win98 or something? Could I still play games, maybe with lower memory usage? 

I'm not thrilled about the chances of this working anymore, but I'll try anything.

Regarding this virtual workstation, could I perhaps have it setup to deliver an internet connection to the host system via a usb network adapter (for a different problem)?
hmm this sounds impossible :(

EDIT:
I have 512 mgs of ram, and a ready 3D-accelerated host (not spectacular). Does that help this cause?

---

### Post by imagine on 2005-12-19
[QUOTE=nalmeth]qemu was the way I was going to go originally, but no 3D supports scratches that idea.[/QUOTE]
Umm I don't use Qemu, so maybe there is 3D support and I'm just not aware of it. But I doubt that.

[QUOTE=nalmeth]I heard VMware was commercial, but if I can find a free / trial version I will definatly give it a go and report my findings.[/QUOTE]
Yes. VMware Workstation is closed source and it costs money, about 150 EUR here to be exactly.
However there's a trial version of VMware Workstation and also a free of charge player since a couple of weeks. The player can run existing virtual machines but not create or modify them. It's similar to Adobes PDF: The creator costs money, the reader doesn't.
See my other posting [1] for download locations and links how to create a virtual machine without actually purchasing VMware Workstation. This is legal, although I think VMware is worth every Cent.

The Windows drivers for the virtual hardware can be extracted out of the trial version of the Workstation, if you decide not to buy it. It's a simple *.iso image.

[QUOTE=nalmeth]I wish there was some WindowsLite version or something, but what can you do?

What if I ran win98 or something? Could I still play games, maybe with lower memory usage?[/QUOTE]
There's also Win4Lin. It's supposed to work quite well with Win9x, but I have no experience with that.

[QUOTE=nalmeth]Regarding this virtual workstation, could I perhaps have it setup to deliver an internet connection to the host system via a usb network adapter (for a different problem)?[/QUOTE]Yes.
Make sure Windows recognizes your USB WLAN adapter, create a TCP/IP connection over two virtual NICs between the guest and the host and set up the guest (Windows) as a gateway for the host (Ubuntu), if you know how to turn your Windows box in a router.
But obviously this is not really a straightforward solution.


[QUOTE=nalmeth]I have 512 mgs of ram, and a ready 3D-accelerated host (not spectacular).[/QUOTE]512 MB would mean 256 MB to Ubuntu and 256 MB to Windows. Not real fun, but it should work.



[1] [http://ubuntuforums.org/showpost.php?p=584904&postcount=24](http://ubuntuforums.org/showpost.php?p=584904&postcount=24)

---

### Post by nalmeth on 2005-12-19
thanks for indepth explanation imagine!

The USB Adapter part is for a friend of mine. He can't get linux drivers without paying for them, and ndiswrapper won't work for his driver. I kind of dismissed this option at first, but if you think it can be done its worth trying. I think he actually has a gig of ram so this may work out.

It seems like gaming isn't *totally* workable, but I think its still worth trying. Perhaps I could create a really chopped down user, run fluxbox or xfce to give up most memory for the windows workstation. 
With luck, hopefully I'll be able to change RAM settings or something.

I really like this idea tho! Even though it won't be perfect, it would be really cool to have a fluid closed/open source system. The best of both worlds. And since I would only use the windows portion for a very limited amount of tasks, I might be able to spare some RAM.

hmm maybe more RAM is the answer for everything

---


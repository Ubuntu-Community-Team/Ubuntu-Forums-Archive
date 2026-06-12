---
title: "VirtualBox and Vista physical"
date: 2008-05-06
forum: The Cafe
---

### Post by cyxodus on 2008-05-06
I'm a Mac guy stuck using Windows Vista (yuck!) and I thought I would try out Ubuntu. Linux seems nice but its a bit slanted to the programmer/engineer type (what's up with compiling?). What I want to do is see if I can get VirtualBox to run the physical Vista so I can access my Adobe pro design apps (don't get me started on Gimp or Inkscape).

How do I do this? I can't make heads or tails out of any documentation I have read online. Can someone explain it to me in simple instructions that don't require a degree.

---

### Post by LaRoza on 2008-05-06
> **cyxodus said:**
> I'm a Mac guy stuck using Windows Vista (yuck!) and I thought I would try out Ubuntu. Linux seems nice but its a bit slanted to the programmer/engineer type (what's up with compiling?). What I want to do is see if I can get VirtualBox to run the physical Vista so I can access my Adobe pro design apps (don't get me started on Gimp or Inkscape).

How do I do this? I can't make heads or tails out of any documentation I have read online. Can someone explain it to me in simple instructions that don't require a degree.

Ubuntu and many other distros are not designed for programmers. In fact, almost everyone on this forum isn't a programmer.

Compiling is needed for creating binary (or byte code) programs. I don't understand that question really. Most software for Windows, OS X and Linux is compiled. The reason why compiling software packages is possible in Linux is because of the open source model. In Windows/OSX, you usually get a binary package and that is it. In the free world, the source is available. This allows Linux to run on many different configurations (including many processors) unlike Windows or Mac OS X. Most of the time, in Ubuntu, programs are packages and precompiled and are installed easily. The package format is .deb, you just double click it and it is easily installed. 

VirtualBox can't do what you seem to want, you have to reboot into Vista, or install Vista in VirtualBox (I don't know if that will work, depending on the system requirements of the applications you want to use)

Reboot into Vista.

---

### Post by SunnyRabbiera on 2008-05-06
you know you really dont have to compile anything if you dont have to with Ubuntu.
The source code is there because of the philosophy behind open source software... sometimes binaries can cause problems.
Also your argument against GIMP and inkscape, well at least they dont cost $900...

---

### Post by cyxodus on 2008-05-06
> **SunnyRabbiera said:**
> Also your argument against GIMP and inkscape, well at least they dont cost $900...

I don't mean to slight both programs but I'm a professional graphic design/comic letterer and neither of these programs are up to the standards that I and other pros use. Btw, that's $1800.

---

### Post by cyxodus on 2008-05-06
> **LaRoza said:**
> VirtualBox can't do what you seem to want, you have to reboot into Vista, or install Vista in VirtualBox (I don't know if that will work, depending on the system requirements of the applications you want to use)

Reboot into Vista.

I have read about people talking about using a physical Vista already installed.

---

### Post by SunnyRabbiera on 2008-05-06
> **cyxodus said:**
> I don't mean to slight both programs but I'm a professional graphic design/comic letterer and neither of these programs are up to the standards that I and other pros use. Btw, that's $1800.

and with that kind of price I can buy four desktop computers, for me programs should NEVER price higher then the compuer... I mean what are we paying for, the box?

---

### Post by FuturePilot on 2008-05-06
VirtualBox is capable of using a physical disk.
See section 9.9 of the manual
[http://www.virtualbox.org/download/1.6.0/UserManual.pdf]("http://www.virtualbox.org/download/1.6.0/UserManual.pdf")
Whether it's possible with Vista I don't know. I tried something similar with VMWare Server and Vista and it just BSODed on me. Then when I tried to actually boot Vista, it kind of blew up. :shock:

> Linux seems nice but its a bit slanted to the programmer/engineer type (what's up with compiling?). 
You will probably never need to compile anything on Ubuntu for everyday use. That's an old stereotype that is no longer true especially with distros like Ubuntu. I know very very little about programming. I have not needed to compile anything in a very long time. Actually since 6.06 and that was almost 2 years ago.

---

### Post by LaRoza on 2008-05-06
> **cyxodus said:**
> I don't mean to slight both programs but I'm a professional graphic design/comic letterer and neither of these programs are up to the standards that I and other pros use. Btw, that's $1800.

The use of those programs isn't part of the topic of this thread. The issue is, I think, virtualizing an existing installation of Vista. If you wish to use this thread to debate the merits of various graphics programs, it will be moved to recurring discussions. Some pros use open source programs. In the end, use what works. No need to debate it here.

> **cyxodus said:**
> I have read about people talking about using a physical Vista already installed.

I believe that can be done with some versions of VMWare, but I am almost certain that VirtualBox can't do that, unless I am missing something.

---

### Post by cyxodus on 2008-05-06
Thanks guys. Btw, I'm just responding to Sunny. He's the one that took it in that direction.

---

### Post by LaRoza on 2008-05-06
> **SunnyRabbiera said:**
> and with that kind of price I can buy four desktop computers, for me programs should NEVER price higher then the compuer... I mean what are we paying for, the box?

If such programs allow someone to make money, it makes sense.

@OP Your first post brought up three points: Compiling, GIMP/Inkscape (you forgot Krita), and VirtualBox. Only one is important. Please don't try to cause flamewars...

---

### Post by FuturePilot on 2008-05-06
> **LaRoza said:**
> 
I believe that can be done with some versions of VMWare, but I am almost certain that VirtualBox can't do that, unless I am missing something.

My post above ;)

---

### Post by LaRoza on 2008-05-06
> **cyxodus said:**
> Thanks guys. Btw, I'm just responding to Sunny. He's the one that took it in that direction.

I was wrong, it can be used that way. But, I do suggest you don't do it unless you are willing to spend a lot of time and effort and I think it will most likely not work. Use what allows you to do your work the easiest. Using Linux this way will likely just make you think Linux is hard to use and not worth it. Indeed, for that requirement, Linux is not the best solution for you.

(Sunny is female I believe)

---

### Post by LaRoza on 2008-05-06
> **FuturePilot said:**
> My post above ;)

Interesting, but I still think it won't work for this person. Running Vista in such a way looks "dangerous" and using it with a rather higher end program will probably fail.

Of course, it would be very cool if it did work.

---

### Post by cyxodus on 2008-05-06
> **LaRoza said:**
> @OP Your first post brought up three points: Compiling, GIMP/Inkscape (you forgot Krita), and VirtualBox. Only one is important. Please don't try to cause flamewars...

What is Krita?

I'm not flaming here, I'm just stating why I want to use VirtualBox.

---

### Post by cyxodus on 2008-05-06
I don't want you guys to misunderstand me, I have a lot of respect for Linux and its users.

---

### Post by LaRoza on 2008-05-06
> **cyxodus said:**
> What is Krita?

I'm not flaming here, I'm just stating why I want to use VirtualBox.

Krita is another popular graphics program. It probably isn't a solution for you though, as the GIMP and Inkscape didn't have what you wanted. It is typically used with KDE.

It probably wasn't your intent, but it laid very fertile ground for complaints. Even I spend a bulk of my first post discussing compiling on Linux and that still has nothing to do with the problem at hand. (About compiling, you can also do it for Windows and OS X, that is how free software is used on Windows/Mac OS X)

Hope everything works out.

---

### Post by cyxodus on 2008-05-06
What I would like to do is run Illustrator and Photoshop via Wine.

---

### Post by LaRoza on 2008-05-06
> **cyxodus said:**
> What I would like to do is run Illustrator and Photoshop via Wine.

[http://appdb.winehq.org/appbrowse.php?catId=19](http://appdb.winehq.org/appbrowse.php?catId=19)

Depending on the versions used, you may have success.

---

### Post by popch on 2008-05-06
> **cyxodus said:**
> I'm a Mac guy stuck using Windows Vista (yuck!) and I thought I would try out Ubuntu. Linux seems nice but its a bit slanted to the programmer/engineer type (what's up with compiling?). What I want to do is see if I can get VirtualBox to run the physical Vista so I can access my Adobe pro design apps (don't get me started on Gimp or Inkscape).

How do I do this? I can't make heads or tails out of any documentation I have read online. Can someone explain it to me in simple instructions that don't require a degree.

Glad you like Linux and, especially, Ubuntu. Rest assured, under normal circumstances nobody has to compile anything in order to get things done. It just possibly might depend on the kind of hardware you have.

As far as I am concerned, you do not have to explain why you have to use the applications you do use. We should take that as a given. I do.

IN PRINCIPLE, you can run Windows in VirtualBox (or in VMWare, for that matter), and you can run it off a virtual disk or a partition on your real disk. 

If you want to use your Windows in a VirtualBox only, I see no reason to leave Windows in a 'real' partition. There might, however, be speed and performance issues which I am not aware of.

There are HowTos which describe that fairly well. Also, there is an entire subforum here which is called 'Virtualization', and it is crawling with nice and knowledgeable people who are just waiting for your questions.

There is one drawback. I seem to have read that Vista's EULA forbids you to virtualize VISTA. There's no such thing in the EULA for XP. Since I do not own a Vista license, I can not go and look.

---

### Post by cyxodus on 2008-05-06
Both Krita and Karbon14 look good but I can't use Karbon because I use automated actions in my lettering. I can create a word ballon in one second.

---

### Post by cyxodus on 2008-05-06
Again, thanks guys.

---

### Post by leftythrower on 2008-08-01
I know this post may be a little late, but I've read that it depends of the version of vista you have in regards to whether or not it violates the EULA. The lower versions it does, the only two that it doesn't violate is in Enterprise and Ultimate versions. 8-)

---

### Post by chris4585 on 2008-08-01
i presume physical virtualization is only for windows?

or rather:

host = ubuntu, guest = windows

and not

host = ubuntu, guest = ubuntu

---

### Post by kieloS. on 2009-03-10
I'm not sure if this will work, but in fact that I've tried this in the oppsite direction, it may work...
(Think it's written for Win XP, but as I said.. I've to use Linux (Debian Lenny) virtual, 'cause in another way I may loose my work)
[http://dotneverland.blogspot.com/2008/08/running-your-physical-windows-xp.html](http://dotneverland.blogspot.com/2008/08/running-your-physical-windows-xp.html)

You may probably have to tinker, but this'd be normally for Linux, I'd say.. I've never heard of users which didn't had to do that for getting whatever they wanted.

[SIZE="1"]Besides..
As I know, it's possible to use Photoshop CS to CS4 in wine, I've tried CS2 and CS4, which is possible since the last update of wine (CS has platinum state on AppDB => [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17))
And for illustrator: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=20](http://appdb.winehq.org/objectManager.php?sClass=application&iId=20)
Also, I think you're able to get things in gimp or inkscape which are as good as Photoshop could do, it's just more complicated.
I say this because I also do graphical stuff and I learned that there are many possibilities to do an artwork.
For more information about wine or such things.. I'd say read or post in another forum/thread.[/SIZE]

greeting

---


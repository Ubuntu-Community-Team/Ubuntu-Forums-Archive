---
title: "Statistics proving that Ubuntu has a performance edge over XP on identical hardware?"
date: 2008-07-12
forum: The Cafe
---

### Post by Jim! on 2008-07-12
Can anyone provide me with statistics proving that Ubuntu has a performance edge over Windows XP on identical hardware? 
I've heard many things about Ubuntu being superior to Windows XP, and to a certain extent I have always believed that performance wise Ubuntu is faster and more efficient then Windows XP in that Ubuntu has a more efficient kernel, and handles system resources better over all. 

I don't know why I never questioned it before, I've always just assumed that what I have heard on forums and Linux news sites was fact. 

If you have any head to head comparisons between Ubuntu and XP please post up links. Thanks.

PS: I heard this on another forum: **"It doesn't bother you that Ubuntu's default filesystem DOES experience fragmentation but that Ubuntu has no tool to defrag it?"**

Is this true?

---

### Post by FuturePilot on 2008-07-12
> **Jim! said:**
> 

PS: I heard this on another forum: **"It doesn't bother you that Ubuntu's default filesystem DOES experience fragmentation but that Ubuntu has no tool to defrag it?"**

Is this true?

Not totally true. It is true that Ext3 will fragment, but it takes a lot, and I mean **a lot** to make it fragment to the point where you see performance problems. Other file systems like NTFS and FAT fragment very easily.

There are actually a few tools in the repos for defragging. Also there's a thread around here with a defragging tool that [jdong]("http://ubuntuforums.org/member.php?u=780") wrote.

---

### Post by Lostincyberspace on 2008-07-12
Once an ext3 reaches 85-90% capacity it starts to fragment because space is starting to run out.

---

### Post by LaRoza on 2008-07-12
> **Jim! said:**
> Can anyone provide me with statistics proving that Ubuntu has a performance edge over Windows XP on identical hardware? 

Assuming hardware is fully supported on both, XP will be faster by itself.

> 
I've heard many things about Ubuntu being superior to Windows XP, and to a certain extent I have always believed that performance wise Ubuntu is faster and more efficient then Windows XP in that Ubuntu has a more efficient kernel, and handles system resources better over all. 
Linux is faster than XP. Try something lighter, like Debian. Ubuntu is rather slow compared to Arch, Slackware, Debian, etc, even with GNOME or KDE.

> 
I don't know why I never questioned it before, I've always just assumed that what I have heard on forums and Linux news sites was fact. 
XP is seven years old remember. 

> 
If you have any head to head comparisons between Ubuntu and XP please post up links. Thanks.
Linux, by itself, is very fast (fast enough to run on NASA's probes and cell phones and routers and it is used on super computers). Distros vary. Slackware and Arch are very fast, and require very little hardware (32 MB of RAM I think, for Slackware). Ubuntu, OpenSUSE and thers require more because they have more.

---

### Post by YaroMan86 on 2008-07-12
> **LaRoza said:**
> Assuming hardware is fully supported on both, XP will be faster by itself.


Linux is faster than XP. Try something lighter, like Debian. Ubuntu is rather slow compared to Arch, Slackware, Debian, etc, even with GNOME or KDE.


XP is seven years old remember. 


Linux, by itself, is very fast (fast enough to run on NASA's probes and cell phones and routers and it is used on super computers). Distros vary. Slackware and Arch are very fast, and require very little hardware (32 MB of RAM I think, for Slackware). Ubuntu, OpenSUSE and thers require more because they have more.

I agree somewhat, though I think it would depend a bit on the hardware and how well it is supported. I've noticed on my machine Ubuntu runs like a dream, but I have to fight XP on a lot of things.

---

### Post by Jim! on 2008-07-14
> **LaRoza said:**
> Assuming hardware is fully supported on both, XP will be faster by itself.
OK Thanks, thats the kind of answer I was looking for. So when it comes down to it, XP is a faster OS compared to Ubuntu when running on the same hardware.


> **LaRoza said:**
> Linux is faster than XP. Try something lighter, like Debian. Ubuntu is rather slow compared to Arch, Slackware, Debian, etc, even with GNOME or KDE.
Do you use another OS besides Ubuntu? Like any of the above mentioned by any chance?


> **LaRoza said:**
> XP is seven years old remember.
Thats true, so It's designed for older hardware which would explain why its faster then Ubuntu on the same (modern) harware.


> **LaRoza said:**
> Linux, by itself, is very fast (fast enough to run on NASA's probes and cell phones and routers and it is used on super computers). Distros vary. Slackware and Arch are very fast, and require very little hardware (32 MB of RAM I think, for Slackware). Ubuntu, OpenSUSE and thers require more because they have more.
Linux is fast, but Ubuntu, which is an OS based of linux (runs off the linux kernel) is slower then XP which is capable of 'all' the same things as Ubuntu. I was asked this recently:

>  Name something you can do in Ubuntu that you can't in XP.

I replied with 'Wobbly Windows', It wasn't an entirely serious response but it was true and was the the first thing that popped into my head when asked this. The reply I got was:

> Can you name something useful? 
Nothing. I can't think of one useful thing you can do in Ubuntu that you can't do in XP. Of course I still prefer Ubuntu over XP any day.

EDIT: I did find one useful thing that Ubuntu has and XP doesn't, Ubuntu can be run as a live CD.

---

### Post by hyper_ch on 2008-07-14
> **Jim! said:**
> OK Thanks, thats the kind of answer I was looking for. So when it comes down to it, XP is a faster OS compared to Ubuntu when running on the same hardware.

Depends... the more things you install (firewll, antivirus, games, office, .....) and the longer you use it the slower it becomes. A pure, freshly installed XP is faster (in the beginning) - but you want more than just an OS ;)

---

### Post by klange on 2008-07-14
> **LaRoza said:**
> Assuming hardware is fully supported on both, XP will be faster by itself.

Heh? My Gutsy *Live CD* was considerably faster than XP on one of my machines. (Except for booting)

---

### Post by Jim! on 2008-07-14
> **hyper_ch said:**
> Depends... the more things you install (firewll, antivirus, games, office, .....) and the longer you use it the slower it becomes. A pure, freshly installed XP is faster (in the beginning) - but you want more than just an OS ;)

Proof?

I'm talking about the Operating Systems using the required equivalent, So If Ubuntu had similar applications installed (minus anti-virus and possibly firewall) So things like an Office program and Games it would probably run slower then an XP install, and as long as XP was maintained then over time it would probably stay superior over Ubuntu in terms of Speed. And over an even longer period of time Ubuntu could become slower then XP still, due to fragmentation as Ubuntu has no defrag tool and is in need of one. (Ubuntu begins to fragment when around 80% of the hard disk is used.

---

### Post by jomiolto on 2008-07-14
> **Jim! said:**
> OK Thanks, thats the kind of answer I was looking for. So when it comes down to it, XP is a faster OS compared to Ubuntu when running on the same hardware.

You should also note that performance depends on the applications you're using. For example, I used to use a Windows-only dictionary application when I was still using XP, and later when I tried the same application in Wine (same hardware), it was actually much faster than on XP (despite being a Windows application). On the other hand, I've observed Firefox being slower on Linux than on Windows.

Also, on Windows you usually need to have anti-virus and firewall running all the time, and some of those programs can have a very negative effect on performance.

> **Jim! said:**
> Nothing. I can't think of one useful thing you can do in Ubuntu that you can't do in XP. Of course I still prefer Ubuntu over XP any day.

EDIT: I did find one useful thing that Ubuntu has and XP doesn't, Ubuntu can be run as a live CD.

Well, you can have most of the Linux features on XP, but many of them require installation of extra applications, while you get those things in Linux installed by default -- I'm talking about things like virtual desktops, command line interface (which a lot of people like to use) and all the available applications (Firefox, BitTorrent-client, OpenOffice.org, etc.).

Then there's of course package management. I've heard of there being some projects to bring package management to Windows too, but I have no idea what the status of those projects are. Package management is probably the biggest reason why I originally converted to Linux from Windows (back then I was using Gentoo, and Portage simply blew my mind -- I had never seen something similar before).

---

### Post by Canis familiaris on 2008-07-14
> Name something you can do in Ubuntu that you can't in XP.
(1) Perform daily activities without worrying about Malware, trojans and Virii.
(2) Have an OS which does not slowdown over time.
(3) Perform even advanced tasks in Command line interface.
(4) Compiz Cube. Or at least there is no way I know to get that Cube in XP/Vista.

And many more

---

### Post by Canis familiaris on 2008-07-14
> **LaRoza said:**
> Assuming hardware is fully supported on both, XP will be faster by itself.

Not nessecarily. Windows has the tendency to slow down with time.
Agreed in my PC Windows boots up faster ie. 35sec as compared to Ubuntu's 65sec, but that is because I have stripped Windows to bare minimum and installed nothing but games, I've not installed even Office(any) or any anti-virus or anti-spyware which are essential if you use Windows as your primary OS.
After booting Ubuntu is as faster as Windows if not faster. (In Ubuntu I have various services installed too, In Windows I have minimum.)
Also Windows has the tendency to slow down over time.

---

### Post by hyper_ch on 2008-07-14
> **Jim! said:**
> I'm talking about the Operating Systems using the required equivalent,
Comparing just speeds of OSes won't do much good ;) what you're going to use an OS for if you have no applications installed on it?

If you want a pure OS installation of Ubuntu then you'd do a server install only - and that is way faster than WinXP. But as said, an OS without any application is (nearly) useless.

> **Jim! said:**
> and as long as XP was maintained then over time it would probably stay superior over Ubuntu in terms of Speed.
With security patches applied and constant booting/rebooting etc. XP will become slower over time. Ubuntu will stay the same.

> **Jim! said:**
> And over an even longer period of time Ubuntu could become slower then XP still, due to fragmentation as Ubuntu has no defrag tool and is in need of one. (Ubuntu begins to fragment when around 80% of the hard disk is used.
If you just want to compare OSes who are you going to fill up the harddisk? Ubuntu will only become **file-**fragemented when you try to put a larger file on it than a free block exists... so 80% doesn't say anything. If you use a 10 GB harddisk, then 20% are 2gb... that could become **file-**fragmented quickly.... however if you put in a 1.5 TB disk then 20% are roughly 300 GB... so even when you rip a blueray dvd onto it, it's unlikely to become **file-**fragmented

---

### Post by jomiolto on 2008-07-14
> **Jim! said:**
> Proof?

I'm talking about the Operating Systems using the required equivalent, So If Ubuntu had similar applications installed (minus anti-virus and possibly firewall) So things like an Office program and Games it would probably run slower then an XP install, and as long as XP was maintained then over time it would probably stay superior over Ubuntu in terms of Speed. And over an even longer period of time Ubuntu could become slower then XP still, due to fragmentation as Ubuntu has no defrag tool and is in need of one. (Ubuntu begins to fragment when around 80% of the hard disk is used.

The main reason Ubuntu is slower than XP is because it usually comes with Gnome (or KDE). If you try some other, lighter Window Manager, there's no comparison really; for example Openbox flies compared to XP's crawling.

I have no idea about the fragmentation, though. Never had any problems with it (Ubuntu uses so little hard drive space that there's usually no reason to let your root partition run nearly full). And there actually *are* defrag programs for Linux, although they're very seldom used, because they aren't usually needed.

In my personal experience, Ubuntu is faster than Windows XP on most hardware (only exception being if you're low on memory, since modern Ubuntu uses more memory than XP) even with the default Gnome desktop. The difference comes especially pronounced if you are running several heavy applications (OpenOffice.org, Firefox, Eclipse, etc.) at once and switching between them. I've always observed Windows to be slow at multitasking.

Other people might have different experiences, though, and comparing performance is a complex issue.

---

### Post by Canis familiaris on 2008-07-14
> **Jim! said:**
> 
PS: I heard this on another forum: **"It doesn't bother you that Ubuntu's default filesystem DOES experience fragmentation but that Ubuntu has no tool to defrag it?"**

Is this true?
Listen to me:
Windows deframenter SUCKS. YES IT SUCKS.
It "defragments" your disk by putting all the data continous and when size of a file increases the filesystem fragments it. It is unbelievable how quickly the Windows file system fragments after you defrag it.
The only advantage I see of it is that since it puts data contilogous, it is much easier to resize it and install Linux. :)

---

### Post by quinnten83 on 2008-07-14
try this [link]("http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/")
[http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/](http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/)

---

### Post by frup on 2008-07-14
Well ubuntu certainly runs faster on my machines than xp ever did, although I haven't checked any of the machines bought in the last 2.5 years.

64 bit Ubuntu can support more than 4gb of ram.

considering most XP and even vista installations are 32bit I'd say that is a plus. Multiple workspaces come by default, Advanced image editing (GIMP) by default, Office by default. (all free too, no license problems). F-spot photo manager by default. Bit-torrent by default. Functional CD/DVD Burning tools by default.

It's not about whether XP can do it or not though, it's about how well each one does it. Ubuntu certainly feels a lot better to use. Ubuntu is ready to use after a 15minute installation (depending on disk size etc) in which you can even use the internet with the LiveCD. Once installed, things will just work or be easy to get working IF they do in fact work. With XP you will need to spend additional time installing many, many drivers. 

Once installed, ubuntu is a complete, self contained, usable system.
XP will require you to use internet explorer or have installation CD's before you can do anything. 

With ubuntu if you didn't like firefox, even though it comes with it by default, you CAN uninstall it. you don't even have to use it to get a new browser, you could use wget or apt-get to install another browser.

Ubuntu can read ext3 disks, xp can't
Ubuntu can read XP, network with XP etc, XP can't network with Ubuntu or read ubuntu's native formats.

---

### Post by Jim! on 2008-07-14
> **frup said:**
> Well ubuntu certainly runs faster on my machines than xp ever did, although I haven't checked any of the machines bought in the last 2.5 years.


> 64 bit Ubuntu can support more than 4gb of ram.

considering most XP and even vista installations are 32bit I'd say that is a plus. Multiple workspaces come by default, Advanced image editing (GIMP) by default, Office by default. (all free too, no license problems). F-spot photo manager by default. Bit-torrent by default. Functional CD/DVD Burning tools by default. I'm talking about the OS on equivalent, supported hardware (take note that XP is seven (7) years old). So 4 gigabytes of ram is useless in this scenario.


[QUOTE]It's not about whether XP can do it or not though, it's about how well each one does it. Ubuntu certainly feels a lot better to use. Ubuntu is ready to use after a 15minute installation (depending on disk size etc) in which you can even use the internet with the LiveCD. Once installed, things will just work or be easy to get working IF they do in fact work. With XP you will need to spend additional time installing many, many drivers. 

[QUOTE]Once installed, ubuntu is a complete, self contained, usable system.
XP will require you to use internet explorer or have installation CD's before you can do anything. 

With ubuntu if you didn't like firefox, even though it comes with it by default, you CAN uninstall it. you don't even have to use it to get a new browser, you could use wget or apt-get to install another browser.

I'm not talking about installation procedure, I'm talking about an already installed, usable OS.

> Ubuntu can read ext3 disks, xp can't
Ubuntu can read XP, network with XP etc, XP can't network with Ubuntu or read ubuntu's native formats.

Windows XP can read the Ext3 file system. ([http://en.wikipedia.org/wiki/Installable_File_System](http://en.wikipedia.org/wiki/Installable_File_System))


PS: I'll get to answering all the points everyone has brought up I only just check this thread now and quite a number of large responds have come back with some good points. So for the people that posted a little earlier I'll be getting back to you in a minute;)

PPS: This is just some discussion regarding which OS performs better on identical, supported hardware. I'm not trying to prove that Windows XP is better then Ubuntu. (I prefer Ubuntu over XP)

---

### Post by Jim! on 2008-07-14
> **Anurag_panda said:**
> Listen to me:
Windows deframenter SUCKS. YES IT SUCKS.
It "defragments" your disk by putting all the data continous and when size of a file increases the filesystem fragments it. It is unbelievable how quickly the Windows file system fragments after you defrag it.
The only advantage I see of it is that since it puts data contilogous, it is much easier to resize it and install Linux. :)

The fact remains that Windows has the tools necessary to defragment, Ubuntu does not (Ext3).

---

### Post by hyper_ch on 2008-07-14
because Ext3 does not need any such tools ;)

---

### Post by wrtpeeps on 2008-07-14
> **Anurag_panda said:**
> (1) Perform daily activities without worrying about Malware, trojans and Virii.
(2) Have an OS which does not slowdown over time.
(3) Perform even advanced tasks in Command line interface.
(4) Compiz Cube. Or at least there is no way I know to get that Cube in XP/Vista.

And many more

K, I'd like to counter argue.

1. This can be done in windows. 
2. Ok.
3. Command line? How can you use that as an advantage. You perform advanced tasks in windows using the GUI. No different.
4. This is just eye candy, and not an advantage.

---

### Post by Canis familiaris on 2008-07-14
> **Jim! said:**
> The fact remains that Windows has the tools necessary to defragment, Ubuntu does not (Ext3).

EXT3 does not need to defragmenting, period.

And there are ways to defragment a Linux filesystem. Though they are tricky but it is tricky to fragment a Linux filesystem as well. ;)

---

### Post by Jim! on 2008-07-14
> **jomiolto said:**
> The main reason Ubuntu is slower than XP is because it usually comes with Gnome (or KDE). If you try some other, lighter Window Manager, there's no comparison really; for example Openbox flies compared to XP's crawling.

GNOME is Ubuntu's default 'out of the box' GUI so for this discussion lets compare Ubuntu using GNOME compared to Windows XP. Some other people have mentioned similar facts as well like Installing Ubuntu server addition, while that is still an Operating System that is not a fair comparison since it is text based and has no GUI. 

Sorry for not making it very clear with the whole GUI thing;)

---

### Post by Canis familiaris on 2008-07-14
> **wrtpeeps said:**
> K, I'd like to counter argue.

1. This can be done in windows. 
2. Ok.
3. Command line? How can you use that as an advantage. You perform advanced tasks in windows using the GUI. No different.
4. This is just eye candy, and not an advantage.

1. Please tell me a method. I want to SECURE my sister's notebook as much as my Ubuntu from Spyware and Virii. Please tell me a way. I'm desperate.

3. That is an advantage for advanced users and enthusiasts like me. But maybe you are right, not an advantage for most users.

4. It improves UI and increases productivity IMO.

---

### Post by Jim! on 2008-07-14
> **Anurag_panda said:**
> (1) Perform daily activities without worrying about Malware, trojans and Virii.
(2) Have an OS which does not slowdown over time.
(3) Perform even advanced tasks in Command line interface.
(4) Compiz Cube. Or at least there is no way I know to get that Cube in XP/Vista.

And many more

Did you read my entire post? As I said before after naming "Wobbly Windows" (Which was an indirect way of referring to Compiz) I was asked:
> "Can you name something useful? "

All the things you named are not exactly 'must have useful features'. With the exception of not worrying about things like Malware and Viruses which it seems have become something the large user base of Windows users have become to think is a normal thing, unfortunately. However in this case there are many solutions and preventative measures to this problem and it's very likely Ubuntu would suffer from Viruses, etc if it had a market as large as Windows.

---

### Post by Jim! on 2008-07-14
> **hyper_ch said:**
> because Ext3 does not need any such tools ;)

Why do people continue to deny this, if the file system experiences fragmentation then its an issue. Ultimately it has an effect on performance and there are no available tools to fix the issue. Ubuntu (and many other linux OS's) needs some sort of tools for defragging the file system.

---

### Post by Canis familiaris on 2008-07-14
> **Jim! said:**
> it's very likely Ubuntu would suffer from Viruses, etc if it had a market as large as Windows.
No it wont. Linux is secure from scratch. Security in Windows is an afterthought.
Also to your information, Linux completely rules in market in server market and still does not suffer as many attacks as the Windows servers.

---

### Post by Jim! on 2008-07-14
> **quinnten83 said:**
> try this [link]("http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/")
[http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/](http://mssaleh.wordpress.com/2008/05/19/ubuntu-804-lts-vs-windows-xp-sp3-application-performance-benchmark/)

Thanks for the links I'm going to take a look now. Looks like a long read so I won't be replying to this thread for a while. (Its also getting quite late so I might just go to sleep:D)

---

### Post by hyper_ch on 2008-07-14
> **Jim! said:**
> Why do people continue to deny this, if the file system experiences fragmentation then its an issue. Ultimately it has an effect on performance and there are no available tools to fix the issue. Ubuntu (and many other linux OS's) needs some sort of tools for defragging the file system.

Why do you insist on this?
[http://tldp.org/LDP/sag/html/filesystems.html](http://tldp.org/LDP/sag/html/filesystems.html)
> 
Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.


---

### Post by barbedsaber on 2008-07-14
> **Anurag_panda said:**
> No it wont. Linux is secure from scratch. Security in Windows is an afterthought.
Also to your information, Linux completely rules in market in server market and still does not suffer as many attacks as the Windows servers.

+ freaking one 

its not just lack of market share that keeps us safe from the ****heads out there, its security from the ground up eg not running as root by default.

---

### Post by Canis familiaris on 2008-07-14
> **Jim! said:**
> Why do people continue to deny this, if the file system experiences fragmentation then its an issue. Ultimately it has an effect on performance and there are no available tools to fix the issue. Ubuntu (and many other linux OS's) needs some sort of tools for defragging the file system.
The likelyhood of fragmentation is very less in EXT3. And that is why there are to tools available in Ubuntu or any other major distro to defragment to files system. But there ARE WAYS TO DEFRAGMENT LINUX FILE SYSTEMS as well.
BTW What is the size of Hard Disk you have? That will make the clarification easier.

P.S. Though I never call an OS better than the other, I only talk of their advantages and disadvantages but if you just want to listen "Windows is better" then I'll say it just to make you happy. :lolflag:

---

### Post by zmjjmz on 2008-07-14
Huh?
Wasn't it pointed out earlier in this thread that there **are** defrag tools for Linux?
And if you want proof about a maintained XP install being slow, I'll show you my mom's Thinkpad T42.
4 years now, and it's insanely slow.
Same with my dad's large Fujitsu notebook-thing.

The problem is, XP doesn't maintain itself.
Ubuntu does.
Because you don't need to maintain XP, you lose productivity time equal to the marginal speed boost you get from using XP.
In my experience though, XP has never been faster than my Ubuntu install, and  this holds true on **greater** hardware than mine.

---

### Post by Canis familiaris on 2008-07-14
> **zmjjmz said:**
> 
In my experience though, XP has never been faster than my Ubuntu install, and  this holds true on **greater** hardware than mine.
Correct. Ubuntu only takes longer to boot. But performing tasks in Ubuntu(read GNOME) is as fast as XP, if not faster.
Judging speed of an OS only by bootup time is unfair, unless one takes far too much time which is also not the case. And of course Windows bootup and tasks slows down over time.

@Mods: Shouldn't this be moved to Recurring Discussions.

---

### Post by the_darkside_986 on 2008-07-14
WinXP usually does run faster, as long as the users avoid installing software that cannot be easily removed, which is pretty much any XP software except open source ports. But it's not really a fair comparison to compare an old OS that lacks proper builtin DVD tools with a more modern feature-filled OS such as Ubuntu. A more suitable comparison would be newest Ubuntu release vs. newest Windows release. I'm sure Linux kernel v. 2.4.* is faster than any of those above. I used to run Redhat 9 and Windows XP on a system with 64 MB of RAM and a garbage Celeron CPU. Even after adding another 64 MB of RAM, Fedora 5 was unusable, Xubuntu 7.04 wouldn't even boot, etc. All those are using kernel 2.6.* as far as I know.

---

### Post by wrtpeeps on 2008-07-14
> **Anurag_panda said:**
> 1. Please tell me a method. I want to SECURE my sister's notebook as much as my Ubuntu from Spyware and Virii. Please tell me a way. I'm desperate.

3. That is an advantage for advanced users and enthusiasts like me. But maybe you are right, not an advantage for most users.

4. It improves UI and increases productivity IMO.

Er, a cli is not an advantage over anything. You can do the exact same thing with GUI.

People who argue CLI is better are the people who think using a CLI makes them look smarter.

as for #1, being smart, having an antivirus and a firewall and not opening files called omgfreepr0n.exe will keep you safe.

---

### Post by Canis familiaris on 2008-07-14
> **the_darkside_986 said:**
> WinXP usually does run faster, as long as the users avoid installing software that cannot be easily removed, which is pretty much any XP software except open source ports. But it's not really a fair comparison to compare an old OS that lacks proper builtin DVD tools with a more modern feature-filled OS such as Ubuntu. A more suitable comparison would be newest Ubuntu release vs. newest Windows release. I'm sure Linux kernel v. 2.4.* is faster than any of those above. I used to run Redhat 9 and Windows XP on a system with 64 MB of RAM and a garbage Celeron CPU. Even after adding another 64 MB of RAM, Fedora 5 was unusable, Xubuntu 7.04 wouldn't even boot, etc. All those are using kernel 2.6.* as far as I know.

64 MB RAM! Why didn't you try Puppy Linux, Arch or Slackware?
I have run XP in 64MB RAM and it crawled.

Compare Ubuntu with Vista?
Then Ubuntu is certainly faster.

---

### Post by Canis familiaris on 2008-07-14
> **wrtpeeps said:**
> Er, a cli is not an advantage over anything. You can do the exact same thing with GUI.


Didn't I admit in my last post that it is not an advantage for all people.

> **wrtpeeps said:**
> 
People who argue CLI is better are the people who think using a CLI makes them look smarter.
CLI makes them WORK smarter.:popcorn:


> **wrtpeeps said:**
> 
as for #1, being smart, having an antivirus and a firewall and not opening files called omgfreepr0n.exe will keep you safe.
No it will not.
When I had Windows I used anti-virus, anti-spyware as well as a firewall but didn't help me at all. And I never blindly clicked an executable. Still I suffered from Spyware if not Virii.

---

### Post by wrtpeeps on 2008-07-14
> **Anurag_panda said:**
> Didn't I admit in my last post that it is not an advantage for all people.


No CLI makes them WORK smarter.:popcorn:

OUt of all the advantages of linux over windows, the CLI is one of the worst ones you could possibly have chosen.

And, it doesn't make anything work smarter. It works the same way, you just need to remember the command instead of pushing a button. :)

---

### Post by Canis familiaris on 2008-07-14
> **wrtpeeps said:**
> OUt of all the advantages of linux over windows, the CLI is one of the worst ones you could possibly have chosen.

And, it doesn't make anything work smarter. It works the same way, you just need to remember the command instead of pushing a button. :)

It is the biggest advantage of *nix platform over Windows.
Developers can use the power of the CLI tools as a front end of GUI without re writing again in case GUI is required.
It gives FAR too much Flexibility which you could not even dream with a GUI.
It can arguably save time too in many situations.

---

### Post by Dixon Bainbridge on 2008-07-14
> **Jim! said:**
> Can anyone provide me with statistics proving that Ubuntu has a performance edge over Windows XP on identical hardware? 
I've heard many things about Ubuntu being superior to Windows XP, and to a certain extent I have always believed that performance wise Ubuntu is faster and more efficient then Windows XP in that Ubuntu has a more efficient kernel, and handles system resources better over all. 

I don't know why I never questioned it before, I've always just assumed that what I have heard on forums and Linux news sites was fact. 

If you have any head to head comparisons between Ubuntu and XP please post up links. Thanks.

PS: I heard this on another forum: **"It doesn't bother you that Ubuntu's default filesystem DOES experience fragmentation but that Ubuntu has no tool to defrag it?"**

Is this true?

It also depends alot on how well the software for the relevent platform is written. I've found some XP apps to be very very quick on similiar spec'd hardware in comparison to ubuntu. I think so much is dependent on code and use of resources and it gets over looked alot. Someting thats well written on XP, like audiograbber for example, can rip and encode faster than Grip or soundjuicer, but other XP based rippers can be slower performing the same task.

---

### Post by wrtpeeps on 2008-07-14
> **Anurag_panda said:**
> It is the biggest advantage of *nix platform over Windows.
Developers can use the power of the CLI tools as a front end of GUI without re writing again in case GUI is required.
**It gives FAR too much Flexibility which you could not even dream with a GUI.**
It can arguably save time too in many situations.

Such as?

---

### Post by fiddledd on 2008-07-14
I'm going to throw a spanner in the works concerning the CLI. I use the CLI at times in XP because I always run (and always have run) as non Admin. 

For instance:
If I want to change the permissions of a file I start cmd.exe as Admin and use "icacls"

I use pulldown (a cli app) for video, so I use a .bat file to execute it (I use the same name for the .mpv for each video). 

The easiest way to take ownership of a file is through the CLI (takeown and icalcs).

---

### Post by bryncoles on 2008-07-14
on defragmentation - as has been mentioned earlier, ext3 filesystems only become fragmented when the drive is 85-90% full. i cant believe no-one has pointed out that windows defragmentation tools need at least 10% free space in order to be able to defragment a drive (see windows own defragmentation tool to confirm this - its a message it gives you as it starts up i believe). 

thus, the time ext3 is JUST STARTING TO FRAGMENT is the same point at which windows can NO LONGER DEFRAGMENT a drive.

---

### Post by wrtpeeps on 2008-07-14
> **bryncoles said:**
> on defragmentation - as has been mentioned earlier, ext3 filesystems only become fragmented when the drive is 85-90% full. i cant believe no-one has pointed out that windows defragmentation tools need at least 10% free space in order to be able to defragment a drive (see windows own defragmentation tool to confirm this - its a message it gives you as it starts up i believe). 

thus, the time ext3 is JUST STARTING TO FRAGMENT is the same point at which windows can NO LONGER DEFRAGMENT a drive.

I think it needs the 10% so it can move stuff about easier.

Vista will defrag your system once a week by default, so it isn't a problem.

---

### Post by Canis familiaris on 2008-07-14
Source: Wikipedia
> The actual disc recording in K3b is done by the command line utilities cdrecord or wodim, cdrdao, and growisofs. As of version 1.0, K3b features a built-in DVD ripper.

K3b was voted LinuxQuestions.org's Multimedia Utility of the Year (2006) by the majority (70%) of voters

So developers of K3b had to only design the GUI and use the existing cdrecord tools.
The power of Linux command line helps the GUIs as well.

As per flexibility:
Rename extensions 1000 files of type say xyz1.txt to xyz1000.txt to .txt.bak
Try doing that in GUI.
In CUI, it is only one command.

This is just a simple example. There are much more complex and real world examples as these.

---

### Post by wrtpeeps on 2008-07-14
> **Anurag_panda said:**
> Source: Wikipedia


So developers of K3b had to only design the GUI and use the existing cdrecord tools.
The power of Linux command line helps the GUIs as well.

As per flexibility:
Rename extensions 1000 files of type say xyz1.txt to xyz1000.txt to .txt.bak
Try doing that in GUI.
In CUI, it is only one command.

This is just a simple example. There are much more complex and real world examples as these.

Your first point here is arguing at how a gui is built on top of a cli command. Reinforces my point. 

If the command line was so great, why did they create the GUI? Same commands, GUI, so neither is more powerful than the other.

As for the second point, fair enough.

---

### Post by Canis familiaris on 2008-07-14
> **wrtpeeps said:**
> Your first point here is arguing at how a gui is built on top of a cli command. Reinforces my point. 

If the command line was so great, why did they create the GUI? Same commands, GUI, so neither is more powerful than the other.

As for the second point, fair enough.

I could counterargue:
If GUI was so great why did they built it on top of a command line tool. LOL! I'm just kidding. 

I'll give you another example.
I use Virtualbox to test new distros and run Windows XP programs which I occassionally test.
Now since I have to frequently run WinXP in Virtualbox, I found it cumbersome to run Virtualbox and then run XP in it.
So I created a launcher on the desktop which ran a command which invoked Virtualbox to run WinXP. Now I can double click an icon and run WinXP.
If Virtualbox did not accept command line arguments through its commandline VBoxManage and just came as a GUI would I have the ability to create such a desktop shortcut?
GUIs are only enhancements to command line tools which make simple daily tasks easier.

---

### Post by LaRoza on 2008-07-14
> **Jim! said:**
> OK Thanks, thats the kind of answer I was looking for. So when it comes down to it, XP is a faster OS compared to Ubuntu when running on the same hardware.

Do you use another OS besides Ubuntu? Like any of the above mentioned by any chance?

Linux is fast, but Ubuntu, which is an OS based of linux (runs off the linux kernel) is slower then XP which is capable of 'all' the same things as Ubuntu. I was asked this recently:

Nothing. I can't think of one useful thing you can do in Ubuntu that you can't do in XP. Of course I still prefer Ubuntu over XP any day.


I didn't read the entire thread, but realised I had posted and decided to answer.

Yes, I use a bunch of other OS's. Ubuntu is the slowest and most bloated of the ones I use. That also means it comes with the most. Ubuntu is just a distro, and is loaded with a lot of software. Something like Debian Base is the bare minimum and flies (but just has the base system). XP is all one thing, with no choices. 

Remember, XP and Ubuntu are operating systems for desktop computers, so they will be able to do the same general tasks.

As for what I can do (but can't in Vista) is use my computer as a security camera and server allowing me to use a webcam as a motion activated streaming video over the internet (don't worry, my firewall is blocking for those interested). Vista still has problems with my webcam, and "motion" was in the repos.


> **WindowsSucks said:**
> Heh? My Gutsy *Live CD* was considerably faster than XP on one of my machines. (Except for booting)

A clean install of XP versus a clean install of Ubuntu with all drivers is different. XP has almost nothing by itself (whereas Ubuntu has a lot, everything but certain codecs, which even XP lacks)

---

### Post by Canis familiaris on 2008-07-14
> **LaRoza said:**
> 
Yes, I use a bunch of other OS's. Ubuntu is the slowest and most bloated of the ones I use. That also means it comes with the most. 
So you havent used OpenSUSE? Have you? :p

P.S. You have changed the caption "Resistance is Futile" to [SIZE="4"]&#2354;&#2366;&#2352;&#2379;&#2395;&#2366;[/SIZE]
So you have transliterated LaRoza.

I think you should have [SIZE="4"]&#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;[/SIZE](translation for Resistance is Futile)

---

### Post by HansKisaragi on 2008-07-14
Ubuntu have **always** been faster then XP, at least for me.

My current setup uses 19 sec to boot, there is no slowdown or anything compared to XP.

Iv **_never_** been so happy with an OS before.

[[IMG]http://i230.photobucket.com/albums/ee215/viiral/th_hardy-20080707-1.png[/IMG]](http://i230.photobucket.com/albums/ee215/viiral/hardy-20080707-1.png)

---

### Post by Canis familiaris on 2008-07-14
> **Viiral said:**
> Ubuntu have **always** been faster then XP, at least for me.

My current setup uses 19 sec to boot, there is no slowdown or anything compared to XP.

Iv **_never_** been so happy with an OS before.

[[IMG]http://i230.photobucket.com/albums/ee215/viiral/th_hardy-20080707-1.png[/IMG]](http://i230.photobucket.com/albums/ee215/viiral/hardy-20080707-1.png)

Which DE do you use?
19 sec is FAST! Really FAST!
My Ubuntu boots in 45-50sec(if I count time from GRUB not power on)

What have you done to make Ubuntu so fast?

---

### Post by HansKisaragi on 2008-07-14
> **Anurag_panda said:**
> Which DE do you use?
19 sec is FAST! Really FAST!
My Ubuntu boots in 45-50sec(if I count time from GRUB not power on)

What have you done to make Ubuntu so fast?

I use Gnome ;)

* Removed boot Splash screen
* Added so that profile loads up at boot.
* Removed the boot menu timeout, it steals 3 sec. :3
* Removed Printer and Blue-tooth service as i don't use those.

I used bootchart" to check the bootime ..

```
sudo apt-get install bootchart
```

Reboot, get the bootchart from 

```
/var/log/bootchart
```

---

### Post by timzak on 2008-07-14
On an older computer, I did some stopwatch comparisons of application load times comparing Windows 2000 (8 years old) and Xubuntu 8.04.  Basically, Xubuntu used a little more ram for the OS itself (~100 MB vs ~80 MB) but it used less memory for apps and it loaded apps faster than Windows 2000 did.  I used cross platform apps as much as possible, such as gnumeric, abiword, firefox, thunderbird, etc. all performing the same tasks or opening the same documents.  The difference was not night and day, rather it was a few seconds here or there.  Nothing you'd notice without the aid of a stopwatch.  But I did find it impressive that a brand new OS such as Xubuntu 8.04 could keep up with an 8 year old OS in terms of performance.

---

### Post by Martje_001 on 2008-07-14
> **Jim! said:**
> Nothing. I can't think of one useful thing you can do in Ubuntu that you can't do in XP. Of course I still prefer Ubuntu over XP any day.
Run more computers parallel to combine their processor power, I've done it once, but it's hard to setup. You CANNOT do this on MAC OS or Windows.

---

### Post by LaRoza on 2008-07-14
> **Anurag_panda said:**
> So you havent used OpenSUSE? Have you? :p
I have used it, but I don't now. 

> 
P.S. You have changed the caption "Resistance is Futile" to [SIZE="4"]&#2354;&#2366;&#2352;&#2379;&#2395;&#2366;[/SIZE]
So you have transliterated LaRoza. 

Yep. I am so clever aren't I :-) 
> 
I think you should have [SIZE="4"]&#2346;&#2381;&#2352;&#2340;&#2367;&#2352;&#2379;&#2343; &#2357;&#2381;&#2351;&#2352;&#2381;&#2341; &#2361;&#2376;[/SIZE](translation for Resistance is Futile)

I already did :-)

I am getting pretty good (with only online text, see [http://laroza.pbwiki.com/Hindi](http://laroza.pbwiki.com/Hindi)) and can read it pretty well. I can "see" the words as wholes, especially "hai", obviously, since it is so common.

I did a transliteration of "Resistance is futile", but decided to go with LaRoza. I may change it later.

---

### Post by Canis familiaris on 2008-07-14
I see the text in your sig.
Very Clever. ;)

EDIT: A useful site for you
[http://www.shabdkosh.com/](http://www.shabdkosh.com/)
[SIZE="4"]&#2358;&#2348;&#2381;&#2342;&#2325;&#2379;&#2358;[/SIZE] = Shabdkosh(Google did not transliterate properly in this case, had to cut copy paste from this site) means Dictionary.
But I think you would have already discovered it. :)

---

### Post by Twitch6000 on 2008-07-14
> **Jim! said:**
> The fact remains that Windows has the tools necessary to defragment, Ubuntu does not (Ext3).

WRONG WRONG WRONG
I think there is a defragger even in the repos of ubuntu.
Then there has been a member that made a defragger.
Also a few other people from debian forums.
Here is the one a member made and works with anything I have tried.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

---

### Post by Canis familiaris on 2008-07-14
> **Twitch6000 said:**
> WRONG WRONG WRONG
I think there is a defragger even in the repos of ubuntu.
Then there has been a member that made a defragger.
Also a few other people from debian forums.
Here is the one a member made and works with anything I have tried.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

Yes and it is pretty cool. And best of all it only does file level defragmentation. And does not place files contilogously as the Windows defragger does.

---

### Post by Twitch6000 on 2008-07-14
> **Anurag_panda said:**
> Yes and it is pretty cool. And best of all it only does file level defragmentation. And does not place files contilogously as the Windows defragger does.

Indeed =].Only thing I dislike about the python defragger is I have to compile it lol.

---

### Post by Canis familiaris on 2008-07-14
> **Twitch6000 said:**
> Indeed =].Only thing I dislike about the python defragger is I have to compile it lol.
It ran out of the box in my system. Just dragged the executable into the terminal and it worked.

---

### Post by Canis familiaris on 2008-07-14
Post Deleted

---

### Post by perce on 2008-07-15
> **wrtpeeps said:**
> Your first point here is arguing at how a gui is built on top of a cli command. Reinforces my point. 

If the command line was so great, why did they create the GUI? Same commands, GUI, so neither is more powerful than the other.



Having both a cli and a gui is of course better than having either one alone; the more options, the better. Moreover a cli is scriptable, which means that you can automatize complex tasks:
[http://en.wikipedia.org/wiki/Shell_script]("http://en.wikipedia.org/wiki/Shell_script")

This is not something that every user can do (for example I can't) but its an everyday tool for professionals.

---

### Post by Polygon on 2008-07-15
> **Twitch6000 said:**
> Indeed =].Only thing I dislike about the python defragger is I have to compile it lol.

...you don't have to compile python programs, they are just text files (you can open them in a text editor)

and by itself the windows defragmenter sucks. it hasnt been updated in years and there are much better programs out there (i found a nice cli one that seems to do a much better job then the windows one), but since windows doesnt let you move the page file and some random files there can never be 'true' defragmentation.

---

### Post by timzak on 2008-07-16
> **Viiral said:**
> I use Gnome ;)

* Removed boot Splash screen
* Added so that profile loads up at boot.
* Removed the boot menu timeout, it steals 3 sec. :3
* Removed Printer and Blue-tooth service as i don't use those.

I used bootchart" to check the bootime ..

```
sudo apt-get install bootchart
```

Reboot, get the bootchart from 

```
/var/log/bootchart
```

I just tried bootchart last night and got 23 seconds without any tweaks to try and speed it up.  I knew it booted pretty fast, but didn't realize it was that fast.  I'll post the bootchart this evening if I get a chance.

---

### Post by ryaxnb on 2008-07-16
> **Jim! said:**
> Did you read my entire post? As I said before after naming "Wobbly Windows" (Which was an indirect way of referring to Compiz) I was asked:


All the things you named are not exactly 'must have useful features'. With the exception of not worrying about things like Malware and Viruses which it seems have become something the large user base of Windows users have become to think is a normal thing, unfortunately. However in this case there are many solutions and preventative measures to this problem and it's very likely Ubuntu would suffer from Viruses, etc if it had a market as large as Windows.


Well, compiz does have some useful features, notably the improved task-switching, similar to Windowskey+Tab in Vista or Expose on Mac. I know of no Expose clones for XP, although there are some for Vista. Expose is very handy. The shelf is also handy, as is certain other compiz features. Although the Cube itself is useless, the Virtual Desktops are hard to find in XP (require PowerToy) and don't work as well as in Linux. Another feature missing in XP is the complete customization, which is advantageous because some customization (such as choosing a lighter WM or picking a different menu system) allows me to be more productive. Finally, some OSS apps don't work well on XP. And I like having them. Not to mention the remote control and remote access of Linux is superb, Windows has better "Remote Desktop" but Linux has better SSH, FTP, SFTP, NFS, Telnet, Rlogin, remote X, NX server, etc.

---

### Post by angryfirelord on 2008-07-17
> **Twitch6000 said:**
> WRONG WRONG WRONG
I think there is a defragger even in the repos of ubuntu.
Then there has been a member that made a defragger.
Also a few other people from debian forums.
Here is the one a member made and works with anything I have tried.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
It's a start, but it only does base level defragmentation. The defrag tool in Windows at least allows you to repair corruption. I'd like to see a similar tool from the ext devs themselves rather than rely on someone's python script. (no offense to jdong)

---

### Post by instabin on 2008-07-21
Decided to not validate this thread with a post.

---

### Post by Giant Speck on 2008-07-21
> **instabin said:**
> Decided to not validate this thread with a post.

Well, good for you.

*claps*

---

### Post by Frak on 2008-08-06
> **Anurag_panda said:**
> (1) Perform daily activities without worrying about Malware, trojans and Virii.

I very rarely worry about any of that on my SP3. I have no anti-anything as of now, and when running Linux scans, it finds nothing. Plus, with SP2 came that "oh so important feature" known as the firewall. It DOES work, and it DOES help.

> **Anurag_panda said:**
> (2) Have an OS which does not slowdown over time.

After 6 months at one release of Ubuntu, it felt like it had slowed to something I'd expect on Windows 98. This was just doing basic things, nothing special.

> **Anurag_panda said:**
> (3) Perform even advanced tasks in Command line interface.

I'll quote a friend of mine on this one.

> LOL. Like grandma really needs to be able to type "sudo apt-get install photoparade-i386"

> **Anurag_panda said:**
> (4) Compiz Cube. Or at least there is no way I know to get that Cube in XP/Vista.

There is software, its called DeskSpace, its $25 (used to be free, but made by somebody else, bought and improved by Otaku). In the least, Compiz-Fusion is somewhat bloated and can help and hurt productivity. There are arguments on both sides, and they both have valor, so I won't step into it.

---


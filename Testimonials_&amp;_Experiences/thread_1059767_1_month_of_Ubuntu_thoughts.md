---
title: "1 month of Ubuntu: thoughts"
date: 2009-02-04
forum: Testimonials &amp; Experiences
---

### Post by yankeeDDL on 2009-02-04
Hello,

I've installed Ubuntu 8.10 (64bit) first on an old laptop, just to "get the feel", and then I made the move on my "main" home PC, in dual-boot with Windows XP.
Some background:
1) PC specs: Athlon 64 3200+ (2.0GHz), 4GB DDR, 2HD sata, Asus A8N-VM, ATI HD2600XT, Printer Epson R300, Webcam Logitech Quickam Connect STX
2) Reasons to leave Windows: after 3 years windows felt ... slow. I'm getting tired to re-format/re-install. The system is fairly stable: hardly any crash, but then again, it is used mostly for email, web browsing, photos, file-sharing and some simple MS Office tasks. Office 2007 is also incredibly slow to load and the interface ... well, I just cannot get comfortable using it (and I have used Windows since DOS 5.0, going through most, if not all, versions of Windows and Office).
Also every now and then some virus pops up, caught by the antivirus. It happened once that the AV crashed while flagging a virus and the whole system was infected.

So ... my Ubuntu experience. In 2 words: very positive.
I have easily upgraded to OpenOffice 3.0 and I can access and edit all the documents I had created with Office 2007.
I have full access to all Windows XP files and documents, so porting my settings and files was a breeze. The only minor inconvenience is for the emails: I had to boot into windows, install Thunderbird, port all emails from Outlook 2007 to TB and then port them from TB-Windows to TB-Ubuntu (but this last step was just a move).
Ubuntu feels quick and responsive, it's intuitive and I was comfortably customizing it in a matter of hours. I have installed some more software through the add/remove panel and it was as easy as it could possibly be.
Two very nice surprises: I read many problem in setting up the webcams. In my case the webcam was found immediately. I did need to make a little change in how I launch Skype, but the trick was easily solved.
Same nice experience with the printer: I went trhough forums to find out what to expect. I downloaded drivers from a Japanese site .. then when I plugged it in Ubuntu recognized it right away and was ready to print immediately.

Now the not-so-good-parts: I cannot completely "kill" my windows partition for the following reasons:
1) There isn't a decent translation software in Linux. I tried OmegaT and I could not get it to work. I am used to Systran.
2) Other non-mainstream software, like Voipstunt, don't offer Linux versions. I tried installing it with Wine but did not work. I will use Ekiga, but haven't got to it yet
3) Mainstream software like Photoshop don't have a Linux version. Gimp does not handle properly 16bit TIFF images so I don't really have an alternative. I don't use AutoCAD, but the same would apply
4) Games. Again, the difference in offer between Windows and Linux is stunning. If you're into games, you really don't have much of a choice. I hardly use the PC for gaming but I do have some old ones installed on Windows which I like to keep available.
5) OpenOffice is a great software. It's more responsive than MS Office and has all you need. I love the auto spell check in Excel which MS does not have. There are some shortcomings that I find incredible for a cumminity-based software, like font scaling in Impress (=PowerPoint): a key function in making nice-looking presentations.


Final considerations:
a) I am glad I switched to Ubuntu. I wished I had done it sooner. I will push whomever I know to give it a try.
b) Linux is now mature enough that you don't need to be a guru to use it, however, the average Window user will probably have some difficulty at first. I guess the same would happen transitioning from Ubuntu to Windows, but the fact of the matter is the chance of somebody moving from Windows to Ubuntu is far higher than the opposite.
c) Recent data on OS market share ([http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=10](http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=10)) shows Linux at 0.83% vs 86% of Windows XP+Vista. It is no wonder that major software houses don't spend much effort supporting Linux. It's a pity, but I cannot imagine this changing until Linux's popularity grows significantly. I hope that happens sooner rather than later: it's a pity that so many people use expensive, inefficient and buggy software when such a nice alternative is available.
d) The Linux community rocks. Is that simple.

---

### Post by 3rdalbum on 2009-02-04
> **yankeeDDL said:**
> 
b) Linux is now mature enough that you don't need to be a guru to use it, however, the average Window user will probably have some difficulty at first. I guess the same would happen transitioning from Ubuntu to Windows, but the fact of the matter is the chance of somebody moving from Windows to Ubuntu is far higher than the opposite.

That's true - I switched from the classic Mac OS to Ubuntu and then bought a dual-boot Win XP/Ubuntu machine. Windows was indeed difficult to get to grips with, and I still don't have really any idea what I'm doing in that platform.

Classic Mac OS to Ubuntu was easier than Ubuntu to Windows.

Good write-up, I'm glad you're enjoying Ubuntu.

---

### Post by hyper_ch on 2009-02-05
depending on your machine you could consider virtualizing windows instead of dual-booting.

vmware supports up to directx 0.9c, photoshop runs well there...

if you have not a too old machine you really might want to consider that. Furthermore, if you setup windows with no net access you won't need antivirus and personal firewall to slow it virtually down either.

---

### Post by solwic on 2009-02-05
> **hyper_ch said:**
> depending on your machine you could consider virtualizing windows instead of dual-booting.

vmware supports up to directx 0.9c, photoshop runs well there...

if you have not a too old machine you really might want to consider that. Furthermore, if you setup windows with no net access you won't need antivirus and personal firewall to slow it virtually down either.

VMWare is doing directx now?  Seriously?  I've read stuff like this before only to find that they do OpenGL that almost works, and directx is nowhere to be found.  

Be nice if they got it working....  :)

---

### Post by hyper_ch on 2009-02-05
vmware server 1.0.6 should be able to (you need to manually enable it, search for directx vmware), vmware server 2.x no clue... and vmware workstation 6.5 has enabled it by default.

---

### Post by jbysmith on 2009-02-05
> **hyper_ch said:**
> vmware server 1.0.6 should be able to (you need to manually enable it, search for directx vmware), vmware server 2.x no clue... and vmware workstation 6.5 has enabled it by default.

I've toyed with the DirectX support in VMWare 6.5. (I understand VirtualBox does too now, haven't tried it yet.)  I'd rate it a definite "not great, not bad", but it actually works.  On my meager test system that I tried it on the 3D framerate wasn't so hot, but it's an older Athlon XP with an AGP 8X 7800GS video card.  I do need to try it on my faster X2 64 with a PCI-E 16 2.0 video card one of these days.

But yea, that aside, both VMWare and VirtualBox run absurdly smooth under Linux, much better than under a Windows host.  I literally use mine on a daily basis, mostly working on some Visual Studio 2008 code, occasionally documentation in Microsoft Word 2007. (Sorry, I just like it better than OpenOffice.)  Having a lot of physical memory will significantly help too, that'll let you allocate more RAM to the virtual machine without crippling either OS.  My one system only has 1.5GB, so I typically allocate the VM 512-768MB, my personal system has 4GB though so I give it significantly more, and XP runs very nicely in a VM.  

I prefer this to dual-booting as they're both running at the same time, altho I still occasionally boot into a physical XP partition just for the odd game once in a while.

---

### Post by hyper_ch on 2009-02-05
vbox supports only opengl but not directx and directx worked great for me... but then I got a bit a newer video card (GeForce 9500 GT), I assigned 2gb ram to the vm... got Intel E2220 2.40G dual core runing 64bit host (32bit guest).

anyway, this is way offtopic now :)

---

### Post by bbabu84 on 2009-02-06
> **yankeeDDL said:**
> Hello,

Now the not-so-good-parts: I cannot completely "kill" my windows partition for the following reasons:
1) There isn't a decent translation software in Linux. I tried OmegaT and I could not get it to work. I am used to Systran.
2) Other non-mainstream software, like Voipstunt, don't offer Linux versions. I tried installing it with Wine but did not work. I will use Ekiga, but haven't got to it yet

etc.



For all your needs, except for maybe gaming, it is easy to have a windows installation within Ubuntu using Virtualbox.  I reinstalled using my xp cd and key within virtual box.  After installing the needed software, I operate it without connecting it to the "network".  It shares its files with the host (specific folder only).  The advantage is that I run it without a virus scanner.  You would be surprised at how fast Windows runs if it didn't have Mcafee slowing it down.  I have a backup copy of the original virtual disk, so if I get a virus by mistake, I can roll back to the original version quickly.  So far it has worked like a charm.  No unnecessary rebooting back and forth between Linux and Windows.

BB

---

### Post by yankeeDDL on 2009-02-11
Actually, having WinXP in Virtualbox is my plan (as I said, no big need for gaming). I still need to move some of the stuff from Windows partition over.
My disappointment comes from the fact that I will still to keep Windows alive. Technically, I will need a Windows' license to do that.
Of course one can find "free" online licenses ... but that's not the point.

About Virtualbox: I am running VB 2.1.2 on my WinXP laptop (that's how I started to 'play' with Ubuntu and got the confidence to switch over in my desktop.
I actually did not have any real issue, except the lack of any 3D acceleration (would be nice to have AWN installed, but it's not possible on Vbox).
I have also installed Vbox 2.1.2 in Ubunto (guest OS is WinXP, actually, in case you're familiar with it: "TinyXP"; a stripped down version, very small memory footprint: google it if you like).
I am still not able to use USB devices in TinyXP which is a bit of a problem 'cause my Dell Axim runs the horrendous Windows CE and needs the horrendous active-sync to backup. Don't get me started.

I have seen some threads in Vbox's forums regarding using DirectX wrapped in OpenGL, by using WineD3D libraries. It's not clear to me if it works both ways (Ubuntu host and WinXP guest or, WinXP host and Ubuntu guest). So far I haven't got it to work. 
I'd say the technology is far from being ready for prime-time.

---

### Post by hyper_ch on 2009-02-11
well, you don't have to immediately drop all windows programs. The more you use linux the less you will use windows.

---

### Post by yankeeDDL on 2009-02-11
> **hyper_ch said:**
> well, you don't have to immediately drop all windows programs. The more you use linux the less you will use windows.

I know ... and that's why I said it was a pity that Linux has such a small market share: it's no surprise that some SW/HW is only designed for Windows platform.
Hopefully things will change. Like Steve Ballmer said: Linux is a cancer: we know who's market share is going to unstoppably eat up. For once, I agree with MS ;)

---

### Post by hyper_ch on 2009-02-11
> **yankeeDDL said:**
> it was a pity that Linux has such a small market share
Depends on what market share you look at.

---

### Post by wolfen69 on 2009-02-11
**hyper_ch:** thanks for the repo generator in your sig. i've been looking for something like that. especially good for helping the newbies.

---

### Post by yankeeDDL on 2009-02-12
> **hyper_ch said:**
> Depends on what market share you look at.

This one: [http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=10](http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=10)

---

### Post by hyper_ch on 2009-02-12
now add to that all routers, all servers, tons of other devices and finally you'll see linux is top ;)

---

### Post by moster on 2009-02-12
OMG, Iphone is coming near linux at his 0,8% marketshare... It will soon be clash of titans :)

---

### Post by yankeeDDL on 2009-02-13
> **hyper_ch said:**
> now add to that all routers, all servers, tons of other devices and finally you'll see linux is top ;)

Don't get me wrong ... but routers and servers don't need to be connected to mobile phones or PDA via bluetooth, nor they need to have powerful 3D graphic cards.
I'm afraid that as long as the 'everyday' PC comes with Windows installed, Windows will keep dominating, IE will be the most common web browser (tell me, who in his right state of mind would use IE to browse the internet?) and support for Linux will have to rely to the Linux community itself.
I hope I'm wrong.

---

### Post by hyper_ch on 2009-02-13
> **yankeeDDL said:**
> Don't get me wrong ... but routers and servers don't need to be connected to mobile phones or PDA via bluetooth, nor they need to have powerful 3D graphic cards.
So? They still are computers ;) and as said, that graph above depends on what you define as market share. If you take all computers then the majority will run linux.
And imagine an internet without servers... there won't be much left of an internet, right?

---

### Post by moster on 2009-02-13
When I think little more, you are right. Chinese phones runs linux. I had oportunity to hold in hand one of that spectacular piece of tehnology. And everybody knows that china has over 1 billion people. Linux wins!

sorry, I forgot smiley, here it is :)

---

### Post by solwic on 2009-02-13
> **moster said:**
> When I think little more, you are right. Chinese phones runs linux. I had oportunity to hold in hand one of that spectacular piece of tehnology. And everybody knows that china has over 1 billion people. Linux wins!

sorry, I forgot smiley, here it is :)

:lolflag:  :biggrin:

---

### Post by hyper_ch on 2009-02-13
> **moster said:**
> When I think little more, you are right. Chinese phones runs linux. I had oportunity to hold in hand one of that spectacular piece of tehnology. And everybody knows that china has over 1 billion people. Linux wins!
The said thing is people don't know that they are using linux :(

---

### Post by solwic on 2009-02-13
> **hyper_ch said:**
> The said thing is people don't know that they are using linux :(

Be nice if they did.  I'm not one for "converting the masses", but it would be nice to live in a world where people were better informed about the technology they used.

---

### Post by moster on 2009-02-13
Why are you so sad? Everything is happend as it suppose. Unix was not suppose to run on desktop. And linux is is clone of unix. Linux is just fine server. Apple did miracle and make from BSD (correct me if I wrong) an usable desktop. But Apple have money and they exactly know what they want. And important thing, have just one boss. In other hand linux do not not have money, and it is spread at too many varieties and divided at so many flavors. Point is, none of distro cannot compare to windows because they all lack of something. Ubuntu just go most furthest to became usable.

---

### Post by its_jon on 2009-02-13
> **moster said:**
> Why are you so sad? Everything is happend as it suppose. Unix was not suppose to run on desktop. And linux is is clone of unix. Linux is just fine server. Apple did miracle and make from BSD (correct me if I wrong) an usable desktop. But Apple have money and they exactly know what they want. And important thing, have just one boss. In other hand linux do not not have money, and it is spread at too many varieties and divided at so many flavors. Point is, none of distro cannot compare to windows because they all lack of something. Ubuntu just go most furthest to became usable.

Maybe out of the chaotic universe that it the Linux pool of thought a superior alternative to Microsoft has emerged in the form of Ubuntu.

Who knows what else the Linux pool of thought will spawn. Possibly something even better for the desktop than Ubuntu.... 
So many other applications and varieties for Linux regardless of which flavor best suits the desktop.

The desktop is but one application Linux now excels in through Ubuntu.

Linux also operates MP3 players and the country China

I think one flavor of Linux can conquer Microsoft. It looks as if Ubuntu is capable of doing this.

Time to pick up the flag and start waving it though ! That is why Microsoft are at the top.... They don't wait for others to tell them their product is great.... they have told the world their product is great themselves ever since win95 .... Im not saying Linux has to lie as well !.... just be better at self promotion :)

---

### Post by solwic on 2009-02-13
> **its_jon said:**
> 
I think one flavor of Linux can conquer Microsoft. It looks as if Ubuntu is capable of doing this.

Time to pick up the flag and start waving it though ! That is why Microsoft are at the top.... They don't wait for others to tell them their product is great.... they have told the world their product is great themselves ever since win95 .... Im not saying Linux has to lie as well !.... just be better at self promotion :)

I'm torn on this point.  On the one hand I'd love to see somebody take Microsoft down.  Or at least knock them down a peg or two.  I'm not an MS hater, and if they ever produce a product superior to Ubuntu, I'll consider using it.  I don't even care if Microsoft maintains their dominance of the desktop/laptop marketshare...as long as they earn it by producing and selling a quality product.

On the other hand...the flag waving, self-promoting, throw-your-arm-out-of-socket-patting-yourself-on-the-back stuff isn't my gig.  I love Ubuntu, it's a great OS...but in the end it's just an OS.  Is it really something to rally around?  To push on people by trying to achieve dominance?  

I think it's enough that Ubuntu is available and free of charge and has a good community built around it.  My PC works great, and I can customize the ^%#$@! out of it.  

Why force everyone else to do what I do?

---

### Post by dnguyen1963 on 2009-02-13
Hi YankeeDDL,

How do you get Skype to work for 64 bit Linux?  I could only find Skype for 32 bit and could not install on my computer because it was for i386 only.

Thanks.

---

### Post by hyper_ch on 2009-02-13
dn: add medibuntu repos

---

### Post by oldrocker99 on 2009-02-13
I've been using Ubuntu since 8.04 came out and I'm NEVER going back to Micro$loth.

Ever.

:guitar:

---

### Post by moster on 2009-02-13
> **its_jon said:**
> Maybe out of the chaotic universe that it the Linux pool of thought a superior alternative to Microsoft has emerged in the form of Ubuntu.

Who knows what else the Linux pool of thought will spawn. Possibly something even better for the desktop than Ubuntu.... 
So many other applications and varieties for Linux regardless of which flavor best suits the desktop.

The desktop is but one application Linux now excels in through Ubuntu.

Linux also operates MP3 players and the country China

I think one flavor of Linux can conquer Microsoft. It looks as if Ubuntu is capable of doing this.

Time to pick up the flag and start waving it though ! That is why Microsoft are at the top.... They don't wait for others to tell them their product is great.... they have told the world their product is great themselves ever since win95 .... Im not saying Linux has to lie as well !.... just be better at self promotion :)

Your words sound like prophecy! Maybe... But I feel that I still waiting for "the chosen one". Maybe I just do not recognize it. hm....

---

### Post by yankeeDDL on 2009-02-14
> **dnguyen1963 said:**
> Hi YankeeDDL,

How do you get Skype to work for 64 bit Linux?  I could only find Skype for 32 bit and could not install on my computer because it was for i386 only.

Thanks.

I found the 64bit deb:
[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)
The link was on this page:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Enjoy :)

---

### Post by yankeeDDL on 2009-02-14
> **hyper_ch said:**
> So? They still are computers ;) and as said, that graph above depends on what you define as market share. If you take all computers then the majority will run linux.
And imagine an internet without servers... there won't be much left of an internet, right?

Yes, they are. And it's all good.
My point was on regard of graphic drivers, applications to sing mobile phones, PDAs, games and some specialized software (AutoCAD, Photoshop).
All of this is a Windows-only world these days. And that's because of the computer that would make use of such programs, Linux covers a very very small portion.

Until Linux goes in the PC of an "everyday" user, we won;t get better support from the graphic cards, we'll keep getting Windows-only tools for syncing our mobile phones ...

---

### Post by hyper_ch on 2009-02-14
> **yankeeDDL said:**
> Until Linux goes in the PC of an "everyday" user, we won;t get better support from the graphic cards, we'll keep getting Windows-only tools for syncing our mobile phones ...

The problem is how to make it go on everyday's computer? Those people that have heard of linux will think it's as hard to install and use as 5-10 years ago - a lot has happened meanwhile.

If you could make those people aware that they use linux everyday without even thinking about it, it might help with a mind-shift.

In some ways, it's a chicken/egg problem. People don't use linux because it's not so well supported. And it's not so well supported because people don't use it.

---

### Post by BigSilly on 2009-02-14
Funny all this. I'm getting a new PC soon (Dell Ubuntu), and I'll be giving this one to my dad, who's not used a computer since the classic Sinclair ZX Spectrum.

"Dad, here's my PC for you. I've pre-installed Ubuntu Hardy Heron. I've set it up to be safe for you on the internet. However, because it's Linux, you'll not be able to download and execute .exe files".

"Download and shoot who?"

".exe files. You have no idea what I'm babbling about have you?"

People defend Windows with things like, "well I'm used to this and that". But that's all it is. Because MS stole this market, people have had time to acclimatise to Windows and it's ways. I'm going to set up this PC with 8.04 for my dad, show him where to get software from, and it'll be interesting to see how he gets on. I'm willing to bet, that with less prior knowledge colouring his judgement, he'll have a better experience than most coming fresh from Windows.

Certainly for me, coming from Windows years ago and not that experienced, I've had a brilliant time with Ubuntu and Linux in general.

---

### Post by dnguyen1963 on 2009-02-27
Thanks, YankeeDDL.  I got Skype to work, but only with Skype headset.  It does not recognize the internal microphone well.  The sound from there is horrible.  The sound from Skype USB headset is crystal clear.

---

### Post by yankeeDDL on 2009-03-03
> **dnguyen1963 said:**
> Thanks, YankeeDDL.  I got Skype to work, but only with Skype headset.  It does not recognize the internal microphone well.  The sound from there is horrible.  The sound from Skype USB headset is crystal clear.

dnguyen, I suggest you open a separate tread to ask for help on this. Seems like an hardware/driver related question. Good luck.

---


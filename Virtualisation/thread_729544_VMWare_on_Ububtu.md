---
title: "VMWare on Ububtu"
date: 2008-03-20
forum: Virtualisation
---

### Post by R@inm@n on 2008-03-20
How does WMWare run on Ubuntu?

I used it on Windblowz quite a bit, but as I plan to soon dump XP forever, i'm wondering how well VMWare runs when installed in Ubuntu.

Any known problems or hiccups?


 Thanks,


 R.

---

### Post by pietjanjaap on 2008-03-20
vmware server (is free) runs ok.

---

### Post by fjgaude on 2008-03-20
I've been using VMware servre on Ubuntu for over a year and think it is great, stable, full-featured, and free.

---

### Post by R@inm@n on 2008-03-22
Unlike Ubuntu, which has large problems with graphics card drivers, if I install Win XP on VMServer in Ubuntu, it should have no problems with my graphics card...correct???


   R.

---

### Post by Kiri on 2008-03-22
Virtualization relies on the host hardware configuration I believe. So if you have problems in ubuntu with your graphics card, then you will have problems in the virtual XP too unfortunately.

---

### Post by R@inm@n on 2008-03-22
Ohh ratz!  I was hoping not to...:(


Not much point installing it then, I guess... :(


 Thanks,


  R.

---

### Post by pietjanjaap on 2008-03-22
Vmware server runs ok on ubuntu.
You should solve your graphics card problem, because ubuntu wil work slower without.
But you can install vmware even if you have problem with the right driver.
After install of vmware do not forget to install the tools of vmware, then vmware works faster and more features.
Vmware has its own hardware(is software), and not of your ubuntu hardware.

---

### Post by StOoZ on 2008-03-22
what kind of problems are you experiencing with your graphics card?
drivers?
if so, you might want to check 'Envy':
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by R@inm@n on 2008-03-22
It's ok...i've already been through the "Envy" graphics driver mess...:(

The problem isn't with Ubuntu, it's with the graphics card manufacturers, who havn't come up with a decent working set of drivers for open source OS's.

My Graphics work fine in Win XP, and I have basic but good graphics here in Ubuntu, although rather 'primitive' compared to Windows.

My original question was when [if] I install VMWare Server in Ubuntu and then load Win XP into VM ... because it's Win XP i'm using ... would it 'see' my graphics card as it does in a 'normal' Win XP enviroment?

Or would it only work as a basic card because it takes it's information through Ubuntu ???

I need a definitive answer please, from someone who is actually running VMWare Server in Ubuntu and has installed Win XP in VM Ware.


Thanks,



   R.

---

### Post by Kiri on 2008-03-22
Perhaps this thread might confirm some of your questions:
[http://ubuntuforums.org/showthread.php?t=717441]("http://ubuntuforums.org/showthread.php?t=717441")

---

### Post by R@inm@n on 2008-03-22
Thanks for the link Kiri. I read the post.

So then ... it seems that installing Ubuntu in Win XP would be better than installing Win XP in Ubuntu... :)

Seriously, I don't think it's worth all the mucking about with VMWare if it isn't going to do what I want.

I guess i'm stuck with dual booting Win XP and Linux.

Ah well, there are much worse things ...   :lolflag:



  R.

---

### Post by Kiri on 2008-03-23
Yeah. At the moment I am running XP and trying out various distros in vbox. But my plan is to switch to linux and run XP in vbox for the windows apps I need. 
But I am still going to keep a dual boot for times when I need to boot back into XP (like doing heavy graphics stuff)

---

### Post by deepclutch on 2008-03-23
I hope viruses wont affect XP when run in vmware-server from Ubuntu host. :p true?

---

### Post by Kiri on 2008-03-23
> **deepclutch said:**
> I hope viruses wont affect XP when run in vmware-server from Ubuntu host. :p true?

Unfortunately I think windows is still susceptible to virus in a VM...

---

### Post by dcstar on 2008-03-23
> **R@inm@n said:**
> Unlike Ubuntu, which has large problems with graphics card drivers, if I install Win XP on VMServer in Ubuntu, it should have no problems with my graphics card...correct???


Ubuntu has** some ** issues with certain video cards, not "large problems".

Most of these issues seem to be with people having new hardware that is not supported by the kernel, or they have just some minor configuration issue and a couple of forum searches provide the solution.

If you bothered to post the details of your video card - or actually done a seach to see if there are any actual problems - then you may get some actual information that is relevant to you.

---

### Post by R@inm@n on 2008-03-23
> **dcstar said:**
> Ubuntu has** some ** issues with certain video cards, not "large problems".

Most of these issues seem to be with people having new hardware that is not supported by the kernel, or they have just some minor configuration issue and a couple of forum searches provide the solution.

If you bothered to post the details of your video card - or actually done a seach to see if there are any actual problems - then you may get some actual information that is relevant to you.


Oh here we go..in comes the smart one.

I didn't "bother" to post the details simply because it's a waste of time.

If you did your own homework you would know that some graphics cards are just hopeless in Ubuntu.

I found that out early in my Ubuntu experience, so please don't come in here like you know it all spouting about "searches" and "actual problems" etc..

 I've already been through the graphics card nightmare on Ubuntu and Mint, thank you.

For your information, it is an ATI card, which are well known to be very poorly served by the manufacturers, and the open source drivers are terrible, compared to windows.

Been there, done that.

 Anyways, it seems that my original question about Virtualization has been answered, so we need go no further with this.


Thanks.


  R.

---

### Post by feed_sparky on 2008-03-23
I agree with dcstar, what kind of card do you actually have? and what problems are you having? I myself have an ATI Radeon Xpress 200m that is working perfectly for me.

---

### Post by R@inm@n on 2008-03-23
My ATI graphics cards work perfectly for me, too...in both Ubuntu and XP.

However ... I have ATI cards in all the 5 computers here in my home  LAN. My children and friends use these to do some homework, but mostly to play computer games, like Doda, WOW, Hellgate, Diablo 2 Starwars,  etc..etc.. in windows...no problem.

I wanted to get away from windows computers and go over to Linux but because the graphics card drivers in open source are so poor, i'm not able to do that.

Anything that requires gaming style 3d acceleration and more complicated rendering is pretty hopeless in Linux, so i'm sort of stuck with dual-booting right now.

I asked my original question about VMWare because I thought that it may have been a way around having to dual-boot.  I've used VMWare Server, ACE and Workstation in Windows enviroments before, so I know it works fine.

What I didn't know was whether running VMWare in Linux would let me run windows games efficiently for the kids to play in VMWare, hence my question about that.

Anyways.....that's about it.  On the computers that I have installed Linux on here, all run dual-boot perfectly, I have windows XP on one HDD, and Linux on the second HDD. All the LAN computers are set up the same way.

I encourage the kids to do their work on Linux, and then they play games on Windows.

I had hoped to dump Windows completely, but it seems that that won't happen until we get decent graphics card drivers from ATI.



Someone once said to me that Linux isn't a game-players OS.

My answer to that is>   It should be, because that's where the young generation hang out, and that's the way to get them into using Linux instead of Windows.


  Thanks,




     R.

---


---
title: "Virtualization or Dual Boot"
date: 2009-02-08
forum: Virtualisation
---

### Post by Jack Shankle on 2009-02-08
I have a dual boot system going with Vista and xppro on HD 1 and
Ubuntu on HD2. It is my intention over time to finally stop using
Windows. At the present time I am finding the constant rebooting
from Windows to Ubuntu time consuming. 
I recently heard about "Virtualbox" and wondered if putting XP
on the Ubuntu drive under "Virtualbox" would be a good idea?
Reason being I want to move my programs to XPPro where I can get 
to them easily while I convert them to "FASM" without the constant 
rebooting.
I got the following on Ubuntu when looking up Virtualbox and can't
tell which one to use:   
     virtualbox ose
     virtualbox ose-source
     virtualbox ose-guest-source
     vboxgtk
     virtualbox ose-dbg
I other words I don't know how to install "Virtualbox".
Hope this is posted in the right place.
Thanks for any help.

---

### Post by Dedoimedo on 2009-02-08
Hello,

Using virtualization has limitations:

Memory and hd consumption.
Some programs, mainly 3d won't run in guest operating systems.
You will have to learn a few things how to interface with virtual machines.

Advantages are scalability and flexibility.

You can download VB from the repositories, as you wanted, this is the OSE version, which has no USB support. You can also manually download from the official site, the PUEL version, which has USB support.

If you go with OSE, then you need ose, ose-source and guest-source.

Check my website, I have quite a bit on virtualization.

Cheers,
Dedoimedo

---

### Post by marcgh on 2009-02-09
Thanks for the link!

---

### Post by Jack Shankle on 2009-02-09
My question is embarrassing but what can I do.
I have a dual boot situation.
HD 1 has Vista and XP Pro
HD 2 has Ubuntu on which I think I have put Virtualbox for about 10Ga.
I did successfully download it from Ubuntu.

Now the embarrassing part. Where the devil is the Virtualbox?
My purpose in a virtualbox is to bring over from Vista a program that
I wrote and place it in the virtualbox for reference. Then I can rewrite
it in FASM to run on a Linux OS.
How do I get it into the Virtualbox?

Thanks for any help.

2% Ubuntu working on 3%

---

### Post by Victormd on 2009-02-09
Don't worry about your questions... we've all been there.
You'll find virtual box under the Application menu (System - if I'm not mistaken... I'm not in Ubuntu now and will confirm when I get home). In Virtual Box, you will be asked to create a virtual machine where you can set the size of the HD (this will be a file so it does not affect any existing OS), memory allocated to the machine, video memory, sound, USB, etc...

Then Virtual Box will allow you to "boot" the virtual machine (you will see a start up window in Ubuntu) and you will be able to boot from the XP CD in this virtual environment. Don't worry about messing up any existing OS as all of this is done in a virtual environment and the only thing being affected is your virtual HD (specified earlier). Once you've installed windows in this virtual environment, you can boot into it any time you want from inside ubuntu so you will be running windows inside ubuntu. As mentioned earlier, there are limitations to this use and you should keep in mind that you will be using RAM for Ubuntu and Windows at the same time so you should make sure you have enough for both (2-3GB of RAM should be enough)...

Hope this gets you started. When I get home I'll stop by to check locations and make sure I didn't leave any important information out.

---

### Post by Therion on 2009-02-09
The biggest drawback, IMO, to virtualization over dual-booting, is the lack of accelerated 3D.

Here's an overview of how to install Windows XP in a virtual machine (Linux host).  I'd suggest downloading the latest version of VirtualBox from their website though, the download link the article is outdated.  Be sure you get the PUEL (Personal Use/Evaulation License) because the Open-Source version has NO support for USB.

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by Jack Shankle on 2009-02-10
I thank you all for your replies.
I went to the site by Therion and these are the problems I had 
following the Tutorial.

1: I guess you have to save the file and then execute it. The
other way I can't find it.
2: My XP cd is one of those Dell reinstallation CDs.
So am I dead?
3: Applications/ system tools doesn't show the Virtualbox program
in Ubuntu.
4: compile gives error: dependency is not satisfiable: libxerces27.
   Runnung Ubuntu 8.10

Virtualbox won't work on my Puter because the CD is a reinstallation CD.
Tell me I am wrong.
Do I have any alternatives solutions??????????????????? 


Nothing is ever easy......

2% Ubuntu working on 3%

---

### Post by krustybaguette on 2009-06-21
I came upon your post looking for the same information but as regards the problem of a Dell recovery disk I can help. I have Toshiba Satellite but made a "slipstream" installation disk. Go to 

[http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml](http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml)

for instructions on how to create a disk that will let you install an up-to-date version of your Windows OS without having whatever "essentials" Dell thinks should be on your system.

Using the slipstreaming disk avoids having to "decrap" a machine after installing Windows.
:popcorn:

---

### Post by krustybaguette on 2009-06-21
[QUOTE=Victormd;6706030]Don't worry about your questions... we've all been there.

should keep in mind that you will be using RAM for Ubuntu and Windows at the same time so you should make sure you have enough for both (**2-3GB of RAM** should be enough)...

I've been using Ubuntu installed on my Windows XP laptop and have run out of space so am about to install a new 250 GB hard disk. I'm leaning toward virtualization for ability to switch between OS's without a reboot, but only have **1 GB RAM** which is maxed out according to Toshiba spec sheet. (A15-S127) If I split the memory between OS's will I be OK? I'm not a heavy duty gamer. Digital photos probably would be the most RAM dependent files I use.  

Anyway, this is an old thread but info was still helpful for me.

KB

---

### Post by buldozerceto on 2009-06-21
virtualization with vmware player!!!

---


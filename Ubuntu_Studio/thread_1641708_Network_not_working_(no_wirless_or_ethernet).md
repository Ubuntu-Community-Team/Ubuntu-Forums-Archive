---
title: "Network not working (no wirless or ethernet)"
date: 2010-12-09
forum: Ubuntu Studio
---

### Post by suquet.paul on 2010-12-09
I use Ubuntu 10.10 as my main OS, and have an alternate hard drive with Ubuntu Studio 10.10. 

Ive been using Ubuntu for years now.

My machine is a Lenovo T400 7417-CTO
// Intel C2D @ 2,8Ghz 6MB L2
// 4GB DDR3

Again, I've had NO problems whatsoever in Ubuntu Desktop, (been using it in THIS machine since 9.10, with NO problems)

I installed Ubuntu Studio 10.10 yesterday, and I couldn't get any networking interface to work. Tried it all; apparently Ubuntu Studio isnt recognising my networking hardware... ive tried soft switches and hard switching; ive tried the Fn + F5 thingy... nothing.

What else can i do?!

I really WANT to use Ubuntu Studio in my recording studio, but for now im frickin' stuck with win 7.

Paul.

---

### Post by pedrinho98765 on 2010-12-09
> **suquet.paul said:**
> I use Ubuntu 10.10 as my main OS, and have an alternate hard drive with Ubuntu Studio 10.10. 

Ive been using Ubuntu for years now.

My machine is a Lenovo T400 7417-CTO
// Intel C2D @ 2,8Ghz 6MB L2
// 4GB DDR3

Again, I've had NO problems whatsoever in Ubuntu Desktop, (been using it in THIS machine since 9.10, with NO problems)

I installed Ubuntu Studio 10.10 yesterday, and I couldn't get any networking interface to work. Tried it all; apparently Ubuntu Studio isnt recognising my networking hardware... ive tried soft switches and hard switching; ive tried the Fn + F5 thingy... nothing.

What else can i do?!

I really WANT to use Ubuntu Studio in my recording studio, but for now im frickin' stuck with win 7.

Paul.
Hello, man!!
What is your network card ???

---

### Post by suquet.paul on 2010-12-09
> **pedrinho98765 said:**
> Hello, man!!
What is your network card ???

I actually dunno... i know it supports N, and i know it is an Intel Pro Wireless card... i just cant remember the exact model. its a 5000 series if im not mistaken. Is there any way i can verify that on Ubuntu or Ubuntu Studio?

Thanx!;)

I read somewhere in the forum that i needed to install Ubuntu Studio with the machine hooked up via ethernet, so that it would be recognized, so i just tried that. Im rebooting after install right now.


---

Ok, so, ethernet browsing WORKS! 
Im runing the "aditional drivers" wiz right now to see if im missing something.

--

Nope... nuttin'.. 181MB of update (which im installing as we speak) but no drivers...


Anything else i can do?

Im in my office, and here, i do have a wired network, but i dont in my home studio nor my entire home...


----------------------------
Alright! More great news!!!
I open up terminal; and type "iwconfig" 

I now see my wlan0 card! 

IEEE 802.11abg ESSID:off/any
Mode: Managed  Access Point Not-Associated  Tx-Power=15 dBm
Retry long limit:7  RTS thr:off  Fragment thr:off
Power Management:off


Now, ive tried, using "Network Settings" under <system><administration>; and ive manually added the SSID of my network, and the wepkey.. but terminal keeps saying the same thing, and of course, i cant do jack s... 

Please help...

---

### Post by Pablo_F on 2010-12-10
Hi, 

You can always start from a ubuntu desktop instalation and do a:

sudo apt-get install ubuntustudio-audio*

(When you are asked about it, yes, you want realtime and memlock privileges)

sudo adduser your_user_name audio

Reboot. 

Then you can tweak a lot but this is a start.

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2010-12-10
Hi Paul
All you need to do is open synaptic and install gnome network manager, the studio build leaves it out on purpose.

---

### Post by suquet.paul on 2010-12-10
> **cchhrriiss121212 said:**
> Hi Paul
All you need to do is open synaptic and install gnome network manager, the studio build leaves it out on purpose.

Yeah, i read the daemon used to give some problems to stablity... but, nuttin the jack UI won't...

I like ubuntu Desktop, but i LOVE studio's login screen, and the audio clips that come with it by default, and ohh the wallpapers... i know its all customizable, but... being a windows user for most part of my life, im used to formating every 3 months... this, of course aint necessary in a ubuntu box, but still, everytime a new version comes out, i do a clean install; after all, ive got my hard drive partitioned to mount "/" in HDD0 and "/home" in HDD1...

Yesterday, i managed to use wifi with studio, but, i couldnt get the daemon. I installed software center and installed a "WiFi analyser" or something like that.. but it aint the same... Ubuntu Desktop just runs so smoothly, i think sudo apt-get install ubuntustudio-audo IS the best option.. 


Ill try to install GNOME NETWORK MANAGER now, and if im not successful enough, i suppose ill do a clean desktop install again today.


Thank you all for your time and support, i never really used the forums before, everytime i had a  problem, id just google it and most of the time, somebody already had it and solved it.. even with machine-specific bugs (such as my lenovo s10-3...). Didn't think forums would be so helpful and quick.

Thank you so much.

---

### Post by suquet.paul on 2010-12-10
> **Pablo_F said:**
> Hi, 

You can always start from a ubuntu desktop instalation and do a:

sudo apt-get install ubuntustudio-audio*

(When you are asked about it, yes, you want realtime and memlock privileges)

sudo adduser your_user_name audio

Reboot. 

Then you can tweak a lot but this is a start.

Cheers, Pablo

Hey! That sounds like the best idea. I "thought" i would be logical Ubuntu had the ability to do this, i mean, if you can use ubuntu and turn it to kubuntu so easily... (i trust ill be the same thing with 11.04... turning unity back to gnome.. i didnt really like unity in a desktop... its ok in a netbook tho...); i just didnt know how or even hot to search for this.

Spain huh? Saludos desde México!
Es mundialmente sabido que españa tiene mucha cultura linux. Aquí en méxico se venden todas esas publicaciones mensuales de "Sólo Linux"... pero llegan varios meses atrasados.
Te agradezco el tip!

---


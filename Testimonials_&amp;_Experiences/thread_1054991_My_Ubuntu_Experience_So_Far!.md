---
title: "My Ubuntu Experience So Far!"
date: 2009-01-30
forum: Testimonials &amp; Experiences
---

### Post by dvl300 on 2009-01-30
I was testing windows 7 but had planned to downlad and install ubuntu before but was having problems installing my wireless Buffalo-N-Infiniti usb adaptor, but i still had another shot at ubuntu again!,installed it again but this time using the live cd not wubi! shrunked my 500GB hardrive in half before hand, then halfed windows 7 parition so i had 250GB left! then halfed the windows 7 partition again to just 100GB then with the remaining 350GB split it into two partitions one 100GB swap partition and one 250GB partition for ubuntu(quick note-always have a swap partition trust me you'll need it!)once installed! i had another crack at installing my Buffalo-N-Infiniti usb adaptor again by first installing ndis-wrapper, did not work?-dont why oh wait now i do!

Turns out the next day i took the live cd to one of my friends who had a computer with a cable internet connection as mine is wireless hence the need to install a wireless adaptor! anyways i popped in the live cd and once booted went to add/remove-programs then typed in windows wireless and clicked on the this link 
and downloaded and then when i got home installed the following files in order

1.ndiswrapper-common_1.52-1ubuntu1_all.deb
2.ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb
3.and last but not least ndisgtk_0.8.4-1_i386.deb
and wouldn't you just know it my Buffalo-N-Infiniti usb adaptor worked!

So what was the problem?-your wondering?
well given that i downloaded ndis-wrapper on its own using windows 7 and then installed it in ubuntu using the terminal and didn't have the neccessary repositorys/packages needed!/installed!, obviously it wasn't going to work!
(only just found out!)

Then updated everything!-took about 15-20mins!

Then installed compiz and then installed wine-but still can't seem to install Adobe Photoshop CS3!
(so i have lefted this for now!)

Then i took on the task of modifying the bootloader image from ubuntu logo to my choice
(nightmare!)

First time! i had done this!-everything went well up until i restarted!, i had added vga to every kernel line
(why-o-why!-i-don't-know)
and got the default view of ubuntu loading all files in black and white!

So i edited the grub bootloader again and only added vga to the first kernel for the first option to boot ubuntu!

Worked! after restart- i got the linux penguin bootloader following some instructions of the internet! second restart!

What a nono! wouldn't even boot just froze oh joy!, so i rebooted manually didn't work then rebooted again and booted into recovery and re-installed all packages and then resume normal boot!

It works did at least three reboots! just make sure!, but another problem my add/remove program was corrupted and i had to re-install it via the terminal!

Then the most abvious problem arised! my graphics driver needed activating and re-installing again!-so i could continue using desktop cube and other effects provided by compiz

As up until now i still can't customise the bootloader to load the image i want!-so i am stuck with the linux penguin image-i suppose it will have to do!

And still can't install Adobe Photoshop CS3 using wine!

but apart from intial problems! i am fullying enjoying ubuntu! once my windows 7 beta period has ended! i will be re-paritioning and formatting that partition so ubuntu uses my whole 500GB hardrive!

---

### Post by hyper_ch on 2009-01-30
> **dvl300 said:**
> one 100GB swap partition
What do you need a 100 GB swap partition for?

---

### Post by dvl300 on 2009-01-30
so my system runs faster, extracting files, running multiple programs etc!+well cos i can-why the hell not!

---

### Post by hyper_ch on 2009-01-30
swap is harddisk space that's treated as ram. Compared to ram swap is really, really really slow. And 100 GB is just way too much :) swap is mostly used if you have memory intense things running or when you want to hibernate/sleep the computer. 1x - 2x the size of the ram is normally used and if you run 32bit OS you can't even address more than 4 Gb. That means if you have 1 GB ram, 100 GB swap then you will effectively only be able to use 1G ram + 3GB swap.

---

### Post by Vince4Amy on 2009-01-30
> so my system runs faster, extracting files, running multiple programs etc!+well cos i can-why the hell not! 

That's not how swap works.

---

### Post by dvl300 on 2009-01-30
thanks for the heads up! i'll re-parition it later tonight!
quick question though how much swap partition maximum can be used with a 64-bit version installed?
(my custom computer built by me support's 64-bit operating systems)

---

### Post by hyper_ch on 2009-01-30
a 64 bit cpu on a 64bit mainboard with a 64bit OS installed can address
2^64 bytes (compared to only 2^32 bytes on 32bit)

---

### Post by dvl300 on 2009-01-30
thanks!
any idea?
how to be able to install Adobe Photoshop CS3-with wine?
due to when i have all the extracted setup files for Phtoshop+Wine installed+configured
setup.exe does not run!

---

### Post by hyper_ch on 2009-01-30
have a look at the appdb on the wine homepage. There might be instructions. I know that CS2 runs.... but depending on your system, is there a reason you don't run it in a virtual winxp through vmware or virtualbox?

---

### Post by dvl300 on 2009-01-30
i would but i have tried several times to install qemu and run winxp but no luck!

although i have ran ubuntu and windows xp with vmware in windows vista no problem!

---

### Post by hyper_ch on 2009-01-30
vmware needs a patch to run on 8.10, virtualbox should run flawlessly (although I prefer vmware because it supports directx 9.0c)

---

### Post by dvl300 on 2009-01-30
okay thanks!
i was thinking of using vmware?

---

### Post by hyper_ch on 2009-01-30
my recommendation is would be to run vmware workstation (not free). Otherwise current is vmware server 2 (I tried to run that on an old win xp machine but didn't like it) so I have only experience with vmware server 1.0.x. For either one you need this patch (have a read through):  [https://bugs.launchpad.net/ubuntu/+bug/263837](https://bugs.launchpad.net/ubuntu/+bug/263837)

And for enabling directx/3d acceleration have a look here: [http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d.html](http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d.html) - I don't know if that applies also to vmware server 2. In vmware workstation 6.5 3d acceleration is enabled by default (but you need to have an opengl 2 video card)

---

### Post by dvl300 on 2009-01-30
okay thanks!

---

### Post by dvl300 on 2009-02-11
!UPDATE!
!good news!
i am now using Sun xVM VirtualBox
instead of vmware
-dont get me wrong vmware is good but?!
i could'nt be bothered honestly!

and Sun xVM VirtualBox ain't all that bad?
i have ran multiple os's virtually on multiple desktops!
and all have ran smoothley

all in all
i am enjoying UBUNTU!

alot!

so its time to say bye bye
WINDOWS!

haha i can get more fps for halo in UBUNTU then i get in windows
mad or what?!

thanks to everyone who made UBUNTU!
:guitar:

---

### Post by hyper_ch on 2009-02-11
vbox is lighter than vmware... however vmware offers more options ;) but if you don't need directx 9 vbox is fine (and even they will get directx 9 to run sometime...) :)

---

### Post by Luiggipro on 2009-02-11
Im glad to hear that you are enjoying your ubuntu experience. I use ubuntu and Im very satisfied with it, I can record my music, edit my videos, etc, and everything works just fine :guitar:

---

### Post by solwic on 2009-02-12
> **Luiggipro said:**
> Im glad to hear that you are enjoying your ubuntu experience. I use ubuntu and Im very satisfied with it, I can record my music, edit my videos, etc, and everything works just fine :guitar:

+1.  It sometimes just takes a little ingenuity and a little help from the forums here to get everything working.  

In the end it is definitely worth the effort.  :)

---

### Post by dvl300 on 2009-05-22
Today i officially converted to Ubuntu:KS
Wiped my hard drive clean! got rid of windows :biggrin:
And re-installed the latest Ubuntu!

bye bye windows for good!:-({|=
thanks again for a brilliant os!:KS

---

### Post by K7522 on 2009-05-22
Excellent to hear! You've finally made the ultimate transition and gotten rid of the safety net.

It's always an interesting realization knowing that you haven't needed to boot the other OS in weeks or months.

Congrats on the successful switch!

---


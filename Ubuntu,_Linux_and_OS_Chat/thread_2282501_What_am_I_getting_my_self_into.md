---
title: "What am I getting my self into?"
date: 2015-06-14
forum: Ubuntu, Linux and OS Chat
---

### Post by shadow8 on 2015-06-14
At this moment I am looking for a ubuntu iso that comes KDE as its main interface(insted of gnome/xfce)
little explination why: For work I need fully working KDE it's a dependancy for work programs(why they use KDE I do not know)

I have been a user of prebuilt envoroment linux (sone one else sets everything up) for 15 years now
I have only really started self admining linux for the last 6 months(installing programs and such)
I can code a great many things in a snap and down a redbull in 2 seconds flat

I know windows like the back of my hand up untill windows 7 all the way from 3.1
I know arch linux more then any other linux
I know some ubuntu particuler things from working with a ubuntu server(mostly just apt-get)
I know KDE like the back of my hand well atleast from a user standpoint

I have a home network boot server and personal home network fileserver/process server(it runs basic things for my home network) and home network booting system (I know how to properly install to it over installing to the computer being used)

Things I must avoid when installing an os is changing my boot loader from grubs 2 at any point(most operating systems install their own bootloader some times its grubs sometimes its something else)

the system
Network based raid ssd 100 gig scan hold drive
Storage raid on the server of 8 teras partitionable
Backup ssd 100 gig arch linux install 
an ssd 50 gig swap system partition(the partition mentioned is actualy host to a bunch of smaller partitions used for linux-swap)

This means the actual "hard drives" that store stuff are on the server in a raid configuration. 
localy I have a 100 gig arch install. For when theres no network conection or the local drives come out of sync. this also happens when I boot and the last booted disk is not avalible in network, In this event it usualy formats the scan hold partition because theres nothing to put there. Boot any linux (or windows) connect to the server via ssh, and send the command "syncremotesystemtocore". This is an alias that runs the script file of the same name and makes the server force feed the scan hold partion with bootable materal. I have a live drive setup that will rebuild my partition system and then ask me for a live drive/cd of controll os. If I installed this on a second or 3rd computer in the house the syncremotesystemcore will force feed all of the scan hold drives. No I did not set up my network raid if my server were to clunk out on me I would need to get some one to fix it for me(It's all dependent on the server on the computer conecting to the system. It's really just a bootloader an os to remote use server, and something that makes the scan hold the exact same as the scan hold drive of the server with same shuuid. Yes there is a second SSD in the server with a 100 gig partition same as the scan hold of my actual computer. And yes if a made a second 100 gig partition on the server I could run a second computer on the network the same way. Truth be told I have 2 of the exact same laptop set up in the same configuration they each boot diffrent operating systems at times but they can both boot the same os partition and all just not at the same time)

I currently have 12 bootable operating systems installed the timer is set to 10 minuets and it auto boots designation Z the following is a direct port from my boot screen with () comenting 
this is hows its written in my boot menu

Welcome Master What operating system need you today?
1. Windows 7
2. Hackantosh osx(aka Mac OS X but not on an actual mac computer)
3. Censored NDA Munchy(this is actualy a minimalist install and only boots so far as instant reboot its a part of my scan hold drive system that comes from work its actual only there to maintain compatability with work network going back and forth public information states that it runs standard linux kernnels my personal ones running 3.18 and its only compatable with KDE)
4. Censored NDA Crunchy(repeat of 3 diffrent ui setup for better work flow)
5. Arch linux(no GUI options installed see entry 5 for GUI based arch)
6. Manjaro KDE(its a fancy arch linux )
7. Manjaro KDE coders wet dream setup(same as 6 diffrent layout good for coding)
8. STEAM OS
9. MEDIA SYSTEM(KODI linux os)
10. This is where I hope to install ubuntu1
11. This is where I hope to install ubuntu2
12. This is where I hope to install Another linux
13. This is where I hope to install yet another linux
110. This is where windows 10 goes when work gives me a free copy(yes we are getting them microsoft paid for because of what we do)
HELL. Rasbery pi passby possesion encoder(turns laptop into rasbery pi like device used for work)
X. Manjaro KDE SERVICE(local)
Z. Sync my system (Its a copy of linux with barshrc containing the code to sync scan hold and reboot in 1 operating system selection

Yes both my laptops go to work with me. Yes they are mine. My work has a take it home with you program while at work booting 3-4 does not auto restart insted it takes me to my secure work enviroment. This is the larger reasion why we get to take home the network booting system from work. If I paied the extra for the security sute from work my home copy would be able to acsess my work raid directly and other related systems. Yes I bought the server threw work I buy acceptable hardware they build it and install it for $50(we have to play for the techs time spent setting it up. Company policy because it's not one of their servers but the tech can't say no to setting it up or service calls. That is also company policy. Besides out techs get paied by task not hour. 2 hours at 25$ an hour well spent service calls are only 15$ an hour thankfully if I ever need and its a 1 hour job for dignostic and basic repair). The home version is there for compatability. Yes I do work with windows and mac stuff thats the real reasion I have the installs 1 and 2. They come as part of the server it just needs A windows installed and A mac os installed. They don't have to work but they do for mine booting the respective work and home windows and mac os. Dependent on the network conected.
My hackntosh setup is rather weird it has drivers for its drivers(theres a driver for each of my hardware that makes it so that genaric drivers work in place of the real driver don't ask how I didn't set it up a guy from work did and thats how he explained it he also setup the rest of my server)

We are able to use other operating systems at work of our own chosing so long as they are kde complient I have a respective boot for every boot entry that boots an os so my work raid has 2 copys on manjaro and a copy of arch just like at home

I can also SWAP operating systems meaning if I just kill power the operating system remains running on the server, and all operating systems are set to compleatly ignore my power button on the local machine if I need a power button theres a softswitch on the server that presses the powerbutton on the os. This is done at a bootloader point the os never gets accses to the local power button only the switch set up on the server. I think an example it better

lap1 starts windows lap 2 start manjaro both compleatly boot I press the power button on the laptops and they cut power
then lap 1 starts media system lap 2 starts manjaro coder power button is pressed on lap 1 and it boots back to windows where its exactly where i left it as it it was never shut down then from windows i can ssh into both manjaros

However if the server was sent to shutdown ALL my operating systems shut down then the server

The operating systems still need to make use of my laptops hardware (meaning only this laptop hardware configuration can boot the windows or what ever but the servers ram and cpu are used to make a ghost of the hardware from the laptop to keep it from losing devices)
The server its self is 128 gigs ram and 2x8 core 3ghz ish processers with the cooling system safely clocked to 5ghz
Some really really funky video card that has 2 actual ram slots and 1 hdmi port and has a cpu socket on the other side with a 3ghz quad core and the video card is actualy made by the company i work for i am told its called an omni match video card(tech room name) I have the r381 model its a beast its in 2 sections and 1 of them is mounted on the othercaseish(the case is actualy 2 side by side with the center being wide open and ice cold the one main board case mount holds 1 section of the video card for server the other side main board case mount holds the mainboard.
1x 8 terra raid controlled by a ssd
1x 250gig 2X SSD's
1x Bootme live drive(this is the drive i have to push my live image to and boot from to install a new os)
1x 250gig Bootme live inactive drive storage (this drive stores my bootme live drive images as whole partitions I can store 125 live drives on this
1x 5ghz duo core (clocked state) that sits on a pci card and I have no idea what it does



Things to keep in mind for play(maybe even improve with knolage gained from post)
I have a ubuntu server box running x2go xfce for remote veiw hate it rather be using KDE cause I know it so much and its what I use for everything else linux
I Have a Steam library that can actualy fill a full 3 TERABYTES with everything installed I prefer using linux installs over windows and mac installs
While I have steam os its also not where I tend to play my steam games that install is for hdmi-tv 1-4 gamepads joysticks ect kinda setup aka sitting back on the sofa playing with a controller or used as a stream point for some games(steam inhoem streaming) steam os is I find the best host for their in home streaming for games
I maintain minecraft servers (thus I need to be able to log into them with their respective mods)java

many linux have issues finding my ethernet or wireless or both i could care less about ethernet as my network has a nice packet compresser (my internet goes into my os enviroment from the server. but local network hardware drivers are needed to maintain internet threw the server. Meaning without wireless driver for the laptop installed the install Wont survive reboot so I may need to get the driver to the live drive)

I HAVE ATI aka AMD video card and offical ATI arch linux drivers Brick the install
open sorce seams to work fine but has been shaky as of late newer installs of linux some games and with latest reinstall of manjaro 1 open gl is broken from install well atleast from java and most games

NOW FOR THE REAL REASION I AM POSTING my questions
1. Is there an image I can make a live drive from that has kde over gnome already there(I hear ubuntu defaults are gnome)
2. What exactly is kde gnome xfce? what would you call them?
3. is it possible for 1 user to use kde by default and others use xfce by default
4. would 3 allow for something like "ssh user@host -x kde
5. if I installed xfce on my linux system would i be able to do the same with xfce?
6. given my setup above is there a way to set up an entire desktop to be the remote system and pager on local or remote controll the same set of desktops?(i understand i may have to make some settings always match) an exaple of this would be manipulating both my manjaros as pager desktops on my ubuntu as an example
7. last time I tryed to install ubuntu as my first linux os to install it hated my laptops hardware wireless failed ethernet failed i had to manualy download packages to a hard disk and manualy install ended up bricking the install in an hour went on like this for a cople days snaped the live cd in half(this was before the server moved in)
8. How hard am I going to have to work to get it to locate the network?
9. Will ubuntu remeber my wifi password?
10. How big is the inital install?
11. if i can boot the inital install long enough to catch the wifi is linux going to bitch about missing files before the cross snyc can catch?
12. though to 11 is it posible to make it auto connect to wifi X without user interaction on start?
13. with proper settings with it be easy to make use of my multi os with ubuntu ie acsessing my manjaro with ubuntu apps or vice versa?

Yes I use alot of operating systems I am actualy hoping that this guy from work sells me his old laptops(he has 5 of the same laptop I am using some are broken but with all 5 you can easaly cobble together another 2 of the laptop I am using)

I have also noticed that when running games and such the ram is the same size as local in terms of "gb" but if i brake it down into kb every os is diffrent from each other and from both laptops Why might that be? also cpu of local apears to be more powerfull (the laptops are quad cores at 2.5ghz but the system imformation from os is "4 cores 5ghz each" and i have only ever been able to keep 4 operating systems started Any ideas why this might be? is ubuntu going to give me the same lie of 5ghz?


Strange tidbit I work for an R&D company who tests computer hardware I get paied more to keep my yap shut then I do for actual work

---

### Post by cooleryawner on 2015-06-14
You probably want Kubuntu, Ubuntu but with KDE instead of Gnome or Unity. Gnome, Unity and XFCE are all types of Desktop Environments, its the whole GUI of the OS basically. 9, it should remember. 10. The install takes much faster than Windows install, and the OS takes up about 8 GB i believe. 12. It should autoconnect on boot after it connected the first time. 13. Yes and no. You can not start Ubuntu apps in Manjaro and vice versa. But you can grab and put files from Ubuntu to Manjaro and from Manjaro to Ubuntu with ease. That's all I can help you with, Have a good day.

---

### Post by grahammechanical on 2015-06-14
Your post is too long to read. Have heard of Kubuntu?

[http://www.kubuntu.org/](http://www.kubuntu.org/)

Regards.

---

### Post by newb85 on 2015-06-14
Kubuntu is one way to go. It's also trivial to add KDE or any of its necessary components to a regular Ubuntu install. They can easily be found in the software center.   (If you're going that route, you may want to find out what specifically are the dependencies if your work program, rather than install all the KDE default apps. I doubt you really need most of them.)

---

### Post by sudodus on 2015-06-14
That's a big wall of text ;-)

I'm not sure anybody can answer all questions. I can start with some of them. But first of all I suggest that you learn about Ubuntu and maybe particularly ***Kubuntu***, since you will need KDE. Kubuntu is an official community flavour of Ubuntu with the KDE desktop environment. And the best way to learn about it is to

- [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

 - Install Kubuntu in a separate computer before you start messing with your multiboot or multi-virtual-machine system. If you can't get a separate computer for testing, you can make an installation to a USB 3 pendrive and run it without interfering with the internal drives of the computer.

> NOW FOR THE REAL REASION I AM POSTING my questions
1. Is there an image I can make a live drive from that has kde over gnome already there(I hear ubuntu defaults are gnome)
Kubuntu> 
2. What exactly is kde gnome xfce? what would you call them?
desktop environments> 
3. is it possible for 1 user to use kde by default and others use xfce by default
Yes, but it can be messy with doublets of application programs. It is cleaner to have separate installed systems, but will use more disk space.> 
4. would 3 allow for something like "ssh user@host -x kde
Yes, ssh and sftp (outbound) come with the Ubuntu flavours. You can easily install openssh-server.> 
5. if I installed xfce on my linux system would i be able to do the same with xfce?
ssh is independent of the desktop environment. Xubuntu is the Ubuntu flavour with xfce.> 
6. given my setup above is there a way to set up an entire desktop to be  the remote system and pager on local or remote controll the same set of  desktops?(i understand i may have to make some settings always match)  an exaple of this would be manipulating both my manjaros as pager  desktops on my ubuntu as an example
7. last time I tryed to install ubuntu as my first linux os to install  it hated my laptops hardware wireless failed ethernet failed i had to  manualy download packages to a hard disk and manualy install ended up  bricking the install in an hour went on like this for a cople days  snaped the live cd in half(this was before the server moved in)
There may be or may not be proprietary drivers for your graphics and wifi chips. An alternative is to switch to linux friendly hardware, that works out of the box.> 
8. How hard am I going to have to work to get it to locate the network?
It is hard to say, particularly without exact knowledge of your hardware. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card
> 
9. Will ubuntu remeber my wifi password?
yes> 
10. How big is the inital install?
Depending on flavour and version 2,5 - 5 GB approx. plus swap> 
11. if i can boot the inital install long enough to catch the wifi is  linux going to bitch about missing files before the cross snyc can  catch?
12. though to 11 is it posible to make it auto connect to wifi X without user interaction on start?
In many cases yes (I think)> 
13. with proper settings with it be easy to make use of my multi os with  ubuntu ie acsessing my manjaro with ubuntu apps or vice versa?

You can access files from other partitions (belonging to other os's) but do *not* expect to run an app belonging to another OS.

---

### Post by shadow8 on 2015-06-14
For the hardware questions I am sure I can sum it up with this
acer timeline aspire 5820t (i have 2 of these laptops)

as for the installing to the boot server so long as I properly point at things and it does not overwrite grubs2 with another bootloader(I can fix a grubs 2 in a flash from the server its self) so not really too worried
oh on a side note i have a whole 5 gig partition at the very front of the partition list as a boot partition(the place where grubs2 is installed)


I was wondering what was up with the kubuntu and xubuntu and such.

As for getting linux friendly hardware that tends to be hard when going with a laptop espeshaly when you gots to get more then 1 of the same system i know my server box is 100% linux friendly
and they are not "virtual systems" the boot server I use is compamany tech you may actualy start seeing thease bad boys for sale at bestbuy in a few years
but it is based on virtual system ideas but its more making use of home network systems(i can still fit a whole another "raid" on there so thats easyly another 8-20 teras depending on the drives used

to my understanding a raid is a config of drives that gives you x partinal space just like a drive but theres more to it in the back end but for an end user a raid is just a better "drive" 

And thankyou guys for your answers so far i am going to go read up on kubuntu now

---

### Post by oldfred on 2015-06-14
Ubuntu's default install is to put a new copy of grub2's boot loader into the MBR if BIOS based, or in the sda drive's efi partition if UEFI based.

Only with BIOS does telling installer when using Something Else install option will you be able to choose another location for where to install grub2's boot loader. Do not attempt to share a separate /boot partition or grub partition. You could install grub2's boot loader to the Kubuntu partition which normally is not recommended as it converts to blocklists or hard coded addresses. But you must know how to then add Ubuntu to your other grub install.

If you boot into live mode and want to install without grub you can do this, but again you must then configure your other grub install to boot Ubuntu.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b. 

Ubuntu does keep in / (root) links to most current kernel. Advanced users boot link from another grub rather than a specific kernel.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by mastablasta on 2015-06-15
> **shadow8 said:**
> 

As for getting linux friendly hardware that tends to be hard when going with a laptop espeshaly when you gots to get more then 1 of the same system i know my server box is 100% linux friendly
and they are not "virtual systems" the boot server I use is compamany tech you may actualy start seeing thease bad boys for sale at bestbuy in a few years
but it is based on virtual system ideas but its more making use of home network systems(i can still fit a whole another "raid" on there so thats easyly another 8-20 teras depending on the drives used

to my understanding a raid is a config of drives that gives you x partinal space just like a drive but theres more to it in the back end but for an end user a raid is just a better "drive" 


Linux can run well in virtualbox. jam the PC with enough RAM and you are good to go. no need for various installs on baremetal. though I am not sure why kind of work you do (drivers maybe?!!).

RAID is meant for redundant disk array. it actually stands for **R**edundant **A**rray of **I**nexpencive **D**isks. ofcourse it can be modified to add disks of different site to same pool. so called RAID 0. Raid 0 in my opinion is asking for trouble. one drive goes bye-bye (and it can go) - all drives go bye. in some home use it maybe makes sense. but I doubt that in your case. RAID 1 and others are basically images of drives (usually used on servers. one drive goes you replace it and data is then synced form others. it's not a backup solution, it just provides redundancy in case of disk failure.

also you can run KDE programs in Gnome and vice versa. You can also develop KDE programs in Gnome .

---

### Post by Bucky Ball on 2015-06-15
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If you have specific support requests regarding Ubuntu please post them in the appropriate support forum(s). Thanks.

The Ubuntu equivalent of an OS with KDE is Kubuntu. Hopefully you'll get some other suggestions of non-Ubuntu OSs that use KDE here. Good luck.

---

### Post by shadow8 on 2015-06-16
> **oldfred said:**
> Ubuntu's default install is to put a new copy of grub2's boot loader into the MBR if BIOS based, or in the sda drive's efi partition if UEFI based.



this sutes me quite perfect actualy as the system its self uses grub2 boot loader (its really just a matter of resourcing the config or updating it)

As for a virtual enviroment that would be extreamly counter productive. Unless i am wrong on this "you can't hook physical hardware in a virtual enviroment" IE I can't hook up a radion Xwhatever video card and then make it scream(in short my job is to push the limits of a sample of hardware and find the braking point or glitches along the way 3rd party quality controll and we test alot of diffent hardware all the way up to an unreleased new designed server tower (hosting companys wanna make sure it will live up to custamer expectation))

given that i got a conferm of grubs 2 i am going to go download kubuntu and check it out

(oh i found out why KDE is so nesary most our inhouse software uses it as its interface structure or controled by a kde widget)

---

### Post by LastDino on 2015-06-17
> **shadow8 said:**
> this sutes me quite perfect actualy as the system its self uses grub2 boot loader (its really just a matter of resourcing the config or updating it)

As for a virtual enviroment that would be extreamly counter productive. Unless i am wrong on this "you can't hook physical hardware in a virtual enviroment" IE I can't hook up a radion Xwhatever video card and then make it scream(in short my job is to push the limits of a sample of hardware and find the braking point or glitches along the way 3rd party quality controll and we test alot of diffent hardware all the way up to an unreleased new designed server tower (hosting companys wanna make sure it will live up to custamer expectation))

given that i got a conferm of grubs 2 i am going to go download kubuntu and check it out

(oh i found out why KDE is so nesary most our inhouse software uses it as its interface structure or controled by a kde widget)


That sounds like a fun job. And yes, you can't do that in VM. There is also option of booting ISO's directly from grub, if that interests you. Should look like this
[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

---


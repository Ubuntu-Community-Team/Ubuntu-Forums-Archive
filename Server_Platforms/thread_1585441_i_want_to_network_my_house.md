---
title: "i want to network my house"
date: 2010-09-30
forum: Server Platforms
---

### Post by arnavk007 on 2010-09-30
so as you read i want to network my house with a file and print server and here i list the various systems i have :--

system A : will be used as the server . it's a laptop with a centrino duo clocked at 1.67 ghz 1 gig ram 80 gig hdd i want to share an external/usb hdd along with my hp laserjet using it. comfortable using linux but the problem is that i have ubuntu installed on a partition it prints using my printer but it doesnt have option of print on both sides(manual).

system B :- its my new desktop which i will recieve by 15th after transferring data to this one i will wipe system a which is my current sys clean and experiment with it. It will use win 7

system C :- another lappie with vista

my ps3

i have a airtel wifi router

so plz help

i will be running my lappie 24/7

---

### Post by loopodoopo on 2010-09-30
I guess you need Samba for the file and printer sharing. 

An introduction to Samba you can find here: 

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

To stream movies, music and pictures to you ps3, use ps3 media server

[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")

---

### Post by annoyingrob on 2010-09-30
I 2nd PS3 media server. Also, because it's a DLNA compliant media server, it will also show up on windows media player (11 and above I believe)

---

### Post by loopodoopo on 2010-09-30
Do you have problems installing it?

---

### Post by arnavk007 on 2010-09-30
no actually i will receive the desktop on 15th October
then i will transfer data and wipe this lappie clean and begin the process of making it a server.
then i will require real time help now i only want to try the process once. i am using win 7 but have ubuntu installed on a partition so would like to test printer sharing. When i connected my printer to ubuntu it prompted me to download hplip drivers. after that my printer was running but only printing black and white . after some tinkering with cups default setting i got it to print colour but could not find the option of both sides printing .
also i think the best option for me would be :-
install ubuntu server on full hdd
make it possible for me to use putty and configure it from my new desktop.
install required software and drivers
connect my printer and external hdd to it.
now i am stuck will it be possible for it to share with 777 permissions both the external and internal hdds along with my printer.
btw for network printing which drivers will be used the ones supplied by hp or those in ubuntu:confused::confused:

---

### Post by arnavk007 on 2010-10-01
sorry for another question
the upnp server should be use cli and i should be able to set it up so that it actually streams all data to my ps3
would i have torrent support in cli
like i set up some folder where i dump torrent files ubuntu automatically scans it and downloads the torrents to another pre-specified folder

---

### Post by arnavk007 on 2010-10-01
hey what if i install ubuntu server
make it an openssl server only
then use putty to install lxde on it 
install all required things 
then do apt-get groupremove lxde
my server is ready

---

### Post by arnavk007 on 2010-10-01
hey the command to install lxde is apt-get install lubuntu-desktop or something else

---

### Post by randomsrvapps on 2010-10-01
I suggest you dont use a laptop Ive done it before didnt take long before the hard disk died and the thing filled up with dust.
this is what i did;
I got a old computer from the rubbish dump, Pentium 3 cpu 450 MHZ and i spent a hundred bucks on two 1tb IDE hdds and setup raid then I installed ubuntu server and it works like a charm Im currently using it for a hp photosmart printer with samba (dual sided printing works) + im using webmin to configure it easy peasy, web server and squid proxy server.
its been running for months now and hasn't missed a beat  

you should check webmin out its perfect for what you want [http://webmin.com](http://webmin.com)

---

### Post by the_original_billq on 2010-10-01
The throttle on the laptop solution is going to be the USB-attached disk.  USB 2.0 max is only 40 MB/s, so if you're trying to stream video to multiple clients, that's not really going to make you very happy.

You'd be much better off using a crappy old PC with cheap IDE drives and a decent RAID controller.

---

### Post by arnavk007 on 2010-10-02
the truth is this that i dont actually watch many hd videos
so it will be used mostly for data transferring , music streaming and most probably saved youtube videos streaming 
just wanted to ask if i download ubuntu server 10.10 when its released can ne1 of u just list the required steps so that i can keep myself ready before my pc comes
my tv supports dlna so will ps3mediaserver be able to stream to it directly or will i require my ps3

my current steps which i will follow are:- 
download ubuntu server 10.10
make it an open ssh server
install lubuntu-desktop  with midori rather than ff for occasional mailcheck and doing things like uploading and downloading which takes time
install hp-lip from hp website (even with nvidia drivers i have seen running the driver from their website is better than drivers provided by ubuntu or fedora)
install samba and cups
try to make it a server (i require help here any guide you can point me to)
install ps3 media server
any other thing to do
btw do i require apache for outside access as i have dyndns enabled and could use ssh over internet to give tasks to my lappie

---

### Post by arnavk007 on 2010-10-02
installing lubuntu would be better or enlightenment 17
how can i install all the necessary codecs and things for media streaming

---

### Post by arnavk007 on 2010-10-02
just wanted to know if apache is necessary for remote access to files or samba will do

---

### Post by arnavk007 on 2010-10-03
ya everyone so i will start the server installation tomorrow plz give me last minute tips on how to start the work
i think i should start with 10.04 server and will do a
apt-get do-release upgrade if i am right

---

### Post by CharlesA on 2010-10-03
Only last minute tip I have is to make sure you have a good backup, if needed.

---

### Post by arnavk007 on 2010-10-03
thx charles A
so i am backing up the data at the moment
still ill only give a small 15gig partition to ubuntu which i will increase when necessary

---

### Post by arnavk007 on 2010-10-04
ill wait for 10.10 as currently my win 7 installation has started giving problems so will not take risks

---

### Post by arnavk007 on 2010-10-09
at what time is ubuntu 10.10 going to be released so i download it will do installing next weekend

---

### Post by CharlesA on 2010-10-09
It'll be released on the 10th, when it's ready.

---

### Post by arnavk007 on 2010-10-09
> **CharlesA said:**
> It'll be released on the 10th, when it's ready.

I wanted to know the exact time like fedora releases at 10 am pacific on that date
so in that way what is the time when ubuntu will be released

---

### Post by CharlesA on 2010-10-09
> **arnavk007 said:**
> I wanted to know the exact time like fedora releases at 10 am pacific on that date
so in that way what is the time when ubuntu will be released
See here: [http://ubuntuforums.org/showthread.php?t=1591483](http://ubuntuforums.org/showthread.php?t=1591483)

---

### Post by arnavk007 on 2010-10-11
so downloaded the ubuntu 10.10 server will install it on sunday
can i have gui on the server as i will also be using it as a spare machine just to check mail and stuff

---

### Post by CharlesA on 2010-10-11
You can install a GUI on it, yes.

See [here]("https://help.ubuntu.com/community/ServerGUI") for more info.

If you just want it as a spare machine and not really a dedicated server, there isn't really any reason to run the server version, as the desktop version can run services just fine (and it includes a GUI by default)

---

### Post by arnavk007 on 2010-10-12
Does the server edition has laptop power saving enhancements like powering down hdd

but the problem with desktop edition is that it is full of crap. 

I'll be using it as a spare machine acting as a 24/7 server accessible frm anywhere in the world with inet access

---

### Post by CharlesA on 2010-10-12
I'm not sure if that's a part of Gnome desktop or not. I've not really used Ubuntu server on a laptop before.

The machine I've got spins down the external drives when they are not in use for a while, but as far as I know, it doesn't spin down the internal ones.

---

### Post by arnavk007 on 2010-10-12
oh
but would i be able to access samba from outside the network
also is there any way to give print jobs from my iphone using email or some other way

---

### Post by CharlesA on 2010-10-12
I'd say allowing samba open access to the internet would be a bad idea.

You'd be better off using SSHFS or SFTP to grab files.

As for the other things, I don't know.

---

### Post by arnavk007 on 2010-10-12
what about something i heard known as ajaxplorer
also if i wanna access external devices from other pcs
will going to /dev/whatever work or i something else required

---

### Post by arrrghhh on 2010-10-12
Well if it's a mounted drive, it's usually in /media - unless it's part of the system, which case the mount point could be anywhere.

Ajaxplorer is a good way to manage files remotely - not sure if you can transfer files as well, but it should work.

External devices from other PCs... like on your LAN?  If they're linux-to-linux, NFS is my preferred protocol on a LAN.  Samba if they're windows-to-linux.

---

### Post by arnavk007 on 2010-10-13
Ok then will look into samba
the irony to all this discussion is that I still haven't installed ubuntu
cuz haven't recieved my new pc

---

### Post by arnavk007 on 2010-10-13
[http://www.labnol.org/software/print-files-on-linux/17841/](http://www.labnol.org/software/print-files-on-linux/17841/)
[http://www.labnol.org/internet/print-from-mobile-phones/17827/](http://www.labnol.org/internet/print-from-mobile-phones/17827/)

i think this would allow me to do remote printing
one question though will i need to have libreoffice to print doc and docx things , also a pdf reader

also is it possible for me to have this print queue print only when the printer is on

---

### Post by arnavk007 on 2010-10-24
So the problem Is that Dell is asking for more time to deliver my pc
fcking Dell
don't worry I want to do the config in the next two weeks or so
I tried using the live USB function but it wants me to install ubuntu to my hard disk
now what I would like to do is that install ubuntu server on a raid of two 4 gig pen drives or may be try for a 16gig one
my laptop can boot from USB 
I would then do the configuration in the pen drives
when my pc comes will then boot from the pen drives only
I will then spin down the internal hdd permanently to save power

give ur two cents

---

### Post by arnavk007 on 2010-10-24
Got into a problem
I tried doing the raid of flash drives by the following way
I have a 2 gig pen drive with ubuntu live USB on it
it is the server 10.10 32 bit edition
I boot from it and afterwards pluton a USB hub which has the two pen drives plugged into it
but the installer hangs at a point where it shows scanning disks at 45%
without these pen drives it works fine but I don't install ubuntu

---

### Post by arnavk007 on 2010-10-25
Even booting from cd gives those problems

---

### Post by arnavk007 on 2010-10-25
It worked out I used only one 16 gig drive and success

---

### Post by arnavk007 on 2010-10-25
I installed lxde
but am not able to install hplip
it says I don't have gcc but I wrote a small cpp program and was able to compile it
what to do now

---

### Post by arnavk007 on 2010-10-26
Plz help how do I install hplip
also I saw e17 screenshots can I install it if yes then how
btw why is no one replying to my queries
please help especially for hplip as without it no print sharing

---

### Post by arrrghhh on 2010-10-26
> **arnavk007 said:**
> Plz help how do I install hplip
also I saw e17 screenshots can I install it if yes then how
btw why is no one replying to my queries
please help especially for hplip as without it no print sharing

You can just use CUPS for printer sharing... That's what I do, then everyone can just print to an IP printer.  Easy.

---

### Post by arnavk007 on 2010-10-27
Without hplip will the printer work
I will try tonight

---

### Post by arrrghhh on 2010-10-27
> **arnavk007 said:**
> Without hplip will the printer work
I will try tonight

I don't know... I used hplip in KDE, but I never set it up on my server.

---

### Post by the_original_billq on 2010-10-27
if you want to build code, apt-get install build-essential.
you probably don't need hplip.  cups is the way to go.

---

### Post by arnavk007 on 2010-10-28
So I was able to install hplip using apt get
q1 what would be the command to suspend /dev/sda could I do something to make it run on startup
also after I checked the share printer box in cups webui I was not able to access the printer using a windows system
local printing works fine but it is only black n white any workaround available
I would like a script which copies dev sdb to media Arnav data. After every hr as I have read that flash drives die earlier
if I copy the files which I have backuped that is dev sdb If I copy them to a new pen drive will it be bootable
also what is the default filesystem in ubuntu ext 3 or 4

---

### Post by arnavk007 on 2010-10-28
how do i install ajaxplorer
also the laptop hangs at the login screen no mouse working no keyboard nothing
help every1

---

### Post by arnavk007 on 2010-10-28
i am able to login using putty what should i do??????
help asap:confused::confused:

---

### Post by arrrghhh on 2010-10-28
Dude you NEED to give us more information.  You seem to just come here and post without even trying to find answers to your problems.

Trust me, nearly 100% of what you are trying to do has been done successfully by someone else - so go out there and read!  Then when you're stuck, you can go thru all the steps you've tried and say I'm stuck at X step, what am I missing.

Instead, you're just posting at random with very little information asking for "help asap".  Please do your due diligence, and then let us know where you're stuck.  It'll help you learn, and it'll make our job of helping you a heckuva lot easier.

---

### Post by arnavk007 on 2010-10-29
ok arrrghhh
lemme list the steps :-
i downloaded ajaxplorer and unzipped it. then i turned off my laptop and went out
after two hours i started my laptop and it got stuck at the gdm login window
i see the cursor but pressing keys on keyboard and moving the mouse no response
so i tried using ssh to access my system i started putty on another laptop and whoa was able to login 
then after some searching i decided to turn of the gui so i typed sudo init 3
the screen on my laptop went blank nothing could be observed
then i typed shutdown - r now i could see some text on my laptops screen and it rebooted still got stuck at the login window

now can you help

---

### Post by arrrghhh on 2010-10-29
> **arnavk007 said:**
> ok arrrghhh
lemme list the steps :-
i downloaded ajaxplorer and unzipped it. then i turned off my laptop and went out
after two hours i started my laptop and it got stuck at the gdm login window
i see the cursor but pressing keys on keyboard and moving the mouse no response
so i tried using ssh to access my system i started putty on another laptop and whoa was able to login 
then after some searching i decided to turn of the gui so i typed sudo init 3
the screen on my laptop went blank nothing could be observed
then i typed shutdown - r now i could see some text on my laptops screen and it rebooted still got stuck at the login window

now can you help

Uhm... you're running GDM on a server?  Trying to fit a square peg into a round hole it sounds like.  Just install ubuntu-desktop, don't install the server edition if you want GNOME.

Did you actually shutdown your laptop?  You said 'turned off'...

---

### Post by arnavk007 on 2010-10-29
> **arrrghhh said:**
> Uhm... you're running GDM on a server?  Trying to fit a square peg into a round hole it sounds like.  Just install ubuntu-desktop, don't install the server edition if you want GNOME.

Did you actually shutdown your laptop?  You said 'turned off'...

I run lxde not gnome I use openbox as window manager
I think lxde also uses gdm I was not sure
ya I actually shut it down but I think my sever was doing something in the background cuz it took a lot of time for it to shut down

---

### Post by arnavk007 on 2010-10-30
Could anyone help please

---

### Post by arrrghhh on 2010-10-30
Sorry, I don't do DE's on -server systems... Can't really help you.

---

### Post by arnavk007 on 2010-10-30
can anyone please help me
maybe Charlesa
i wont be able to continue without help

---

### Post by Boondoklife on 2010-10-30
> **arnavk007 said:**
> can anyone please help me
maybe Charlesa
i wont be able to continue without help

I took a quick stroll through this tread and it is a friggin mess! If you are looking for a no fuss way for getting alot of the functionality you want, I would do the following.

1) for your file server, just install the Desktop version you can share files and what not just fine with it. Don't bother with a server edition or putting other GUI's on it. Just run it with stock gnome and call it a day.

2) for a printer solution, why not just get a network ready printer. I swear by my HP c4795 and can print from any system to it, even my windows mobile phone! It was dirt cheap at bestbuy a while back and is prolly cheaper now.

3) as for accessing your files remotely, you could just install a VPN service on the file server and you will be able to get into your files and browse them just like you are at home from anywhere you have an internet connection (as long as you dont run into a firewall issue). If this seems a little over whelming, then you could also get a VPN appliance and use it to gain access to your network. These are pretty cheap on ebay.

I know that all of this can be done from a central box but in your case you seem to be running into all kinds of issues and this way might be easier.

---

### Post by arnavk007 on 2010-10-30
Boondoklife thank you for help
ok i will dload the desktop version
buying a printer not an option check page 4
i live in india so no bestbuy 
will revert tomorrow

---

### Post by Boondoklife on 2010-10-30
> **arnavk007 said:**
> Boondoklife thank you for help
ok i will dload the desktop version
buying a printer not an option check page 4
i live in india so no bestbuy 
will revert tomorrow

Well there may not be a bestbuy but Im sure you have access to retailers that can provide you with the needed goods. You could also try to get one of the small print server devices that convert any printer into a network one.

If you are adamant about getting all this to work with just one box, then I would suggest you get the printer working on the server. Once you have that going, then you are going to have to get very familiar with this doc: 
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)

I have used cups before just fine but it did take some tweaking, however now I would not be any assistance as I just don't use it.

---

### Post by CharlesA on 2010-10-30
> **arnavk007 said:**
> can anyone please help me
maybe Charlesa
i wont be able to continue without help

Sorry, I don't know where to start. I don't run a DE on my server and don't use CUPS to share a printer (all my printers have the ability to attach directly to the network)

---

### Post by arnavk007 on 2010-10-30
boondoklife
yes the printer works with my server
thanks for help

---

### Post by arrrghhh on 2010-10-30
> **arnavk007 said:**
> boondoklife
yes the printer works with my server
thanks for help

You'll have a much easier time setting up all the stuff you want with ubuntu-desktop - and like we've all said before, you can run ALL the same services with ubuntu-desktop.  -server is for servers - it doesn't come with a DE because for some it's not necessary.  My server isn't even plugged into a monitor ;)

At any rate, once you get ubuntu-desktop installed & setup, we should be able to get your printer up & going and all the other stuffs you wanted.  Please, read, research, search before you post - the only way we can help you is if you help yourself.  I've had to re-read documents many many times before if I didn't grasp it - after you've finished banging your head against the wall, then post.  Tell us what you've done/tried/used what-have-you, and that will help us not repeat things you may have tried.

Keep in mind, this all doesn't happen overnight - this make take you a few weeks to setup & get working how you want it.  You have to learn to tread water before you can swim :D

---

### Post by arnavk007 on 2010-10-30
arrrghhh thx for the last minute tip
one small question
should i install ubuntu on the pen drive or live usb with persistence would work
any performance difference or something

---

### Post by Boondoklife on 2010-10-30
I personally would not install an OS onto a USB stick as you can quickly wear out the drive. Get a USB hard disk if possible.

You could customize the OS and tweak everything to write to a RAM disk but yea that would just be not worth the time and effort.

---

### Post by arnavk007 on 2010-10-30
i hv a usb hdd but wont use it
i want to install it on a pen drive to save power as then the internal hdd wont be used and i could spin it down
i will use the usb hdd to store data

---

### Post by Boondoklife on 2010-10-30
> **arnavk007 said:**
> i hv a usb hdd but wont use it
i want to install it on a pen drive to save power as then the internal hdd wont be used and i could spin it down
i will use the usb hdd to store data

Well you may wanna look into creating a Ram drive and having your logs and other accessed file written to it instead of the pendrive, if you don't you will find it to have a very short lifespan and dead server. You could even go as far as to setup a software raid 1 with two thumb drives that way if one dies you can replace it but again that will get costly after they start dying.

---

### Post by arnavk007 on 2010-10-30
i have only 1 gig ram will it work also i require windows on this laptop for the next 10 days or so
i have 5 4 gig pen drives but only 3 usb ports to spare

---

### Post by arrrghhh on 2010-10-30
I wouldn't install the OS on a pendrive, Boondoklife speaks the truth - you'll wear out the pendrives quickly & the server will die.

Also, you'll probably have worse performance than a traditional hard drive.  Now if you purchased an SSD hard drive... that's another story.

---

### Post by arnavk007 on 2010-10-30
ok then best option partition then install on internal hdd

---

### Post by arnavk007 on 2010-10-31
> **Boondoklife said:**
> Well you may wanna look into creating a Ram drive and having your logs and other accessed file written to it instead of the pendrive, if you don't you will find it to have a very short lifespan and dead server. You could even go as far as to setup a software raid 1 with two thumb drives that way if one dies you can replace it but again that will get costly after they start dying.
Is it possible for me to use a pen drive for the same and copy those logs to internal hdd every 24 hrs
this will reduce use of hdd and will save power + i can save pen drives and other things
if yes then how to

---

### Post by arnavk007 on 2010-10-31
i do not think a vpn will work as it will require me to have a static ip which i dont have
would ajaxplorer be a better idea
it uses apache

---

### Post by CharlesA on 2010-10-31
You can use something like dyndns if you have a dynamic ip.

---

### Post by arnavk007 on 2010-10-31
i have dyndns but i was thinking if i set up port forwarding then i can do like this :
xxxxxx.dyndns.org:somenonstandardport
i will then bookmark this link on all devices
i will put a password and taraaa
my isp blocks port 80 cuz even when using edge doing port 80 lands me on my routers config page

---

### Post by arnavk007 on 2010-10-31
i have installed 10.10 desktop
what to do now??????

---

### Post by arnavk007 on 2010-10-31
Got into a problem
I marked samba apache and some other packages for install in the software centre
while it was installing I put down my laptops screen
I then went to take bath
when I returned the LEDs of laptop were not lit
so I pressed the power button it showed a login window and then turned off
now I can't install samba it says already installed but it's not so

---

### Post by arnavk007 on 2010-10-31
hey was able to do samba and stuff
how do i install ajaxplorer
i extracted the zip file into /var/www/ now what to do

---

### Post by arrrghhh on 2010-10-31
> **arnavk007 said:**
> hey was able to do samba and stuff
how do i install ajaxplorer
i extracted the zip file into /var/www/ now what to do

I see you've read their [documentation](http://www.ajaxplorer.info/wordpress/documentation-3/) *very* thoroughly... :rolleyes:

Assuming everything's been setup, you should just browse to that link on your apache server.

---

### Post by arnavk007 on 2010-11-01
Arrrghhh what do you mean everything has been set up
also how do I browse to the link 
I got into a problem
I wanted to set up static ip for my laptop
I tried out a guide on cyberciti.biz 
but now I am not able to access the net

I will put the /etc/interfaces file after some time

---

### Post by arnavk007 on 2010-11-01
so here is the /etc/network/interfaces file which i edited

---

### Post by arnavk007 on 2010-11-01
Could anyone please help

---

### Post by CharlesA on 2010-11-01
> **arnavk007 said:**
> Could anyone please help

No offense, but no one is going to walk you step by step thru all the steps required to get Ajax up and running, especially when there is [documentation]("http://www.ajaxplorer.info/wordpress/documentation-3/") on it already.

We are all volunteers here and you need to do at least some of the work, else you'll never learn how to use the different parts of yer system.

---

### Post by s.fox on 2010-11-01
Insulting other members will not be tolerated.  Thread Closed.

I would also advise that you read some of the samba documentation and then post back when you hit a specific problem.

---

### Post by Elfy on 2010-11-01
This thread appears to be a constant bump - you need to work out what it is you are needinfg and then put it in one post. Constantly adding posts is in effect a bump - if you wish to do so then leave at least 24 hours between posts.

As it stands this thread appears to be going nowhere. 

As has been said you need to at least start looking for information yourself. 

You will also need to collect your thoughts and repost as this one is now closed.

---


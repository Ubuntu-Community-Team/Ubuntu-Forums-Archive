---
title: "I need some help"
date: 2009-02-09
forum: Server Platforms
---

### Post by chato92 on 2009-02-09
Ok so i have never used ubuntu i have installed ubuntu server edition on my pc but now i want to add a gui because i have no idea how to use the command line so could some one help me out and could i have some links on how to do this and how the pc with ubuntu server has to be connected to my other computer and any info that might help me out THANKS !!!!

---

### Post by spiderbatdad on 2009-02-09
```
sudo apt-get install ubuntu-desktop gdm
```

---

### Post by skunkbad on 2009-02-09
There is a nice Ubuntu server administration that you can buy at your local bookstore. It's great, even though it's made for an older version of the OS.

---

### Post by chato92 on 2009-02-09
> **spiderbatdad said:**
> ```
sudo apt-get install ubuntu-desktop gdm
```

ok so i typed it in asked me for my password entered it and then it told me this 

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop

What went wrong what should i do??

---

### Post by lostscotsman on 2009-02-09
Sorry to sort of jump in here but would one of the many smart people here be willing to answer another new guy question?

---

### Post by Sorivenul on 2009-02-09
> **chato92 said:**
> What went wrong what should i do??
Have you retrieved the updated package lists?
```
sudo apt-get update
```
Then try the install again.

> **lostscotsman said:**
> Sorry to sort of jump in here but would one of the many smart people here be willing to answer another new guy question?
It is generally good practice to start a new thread pertaining to your issue. Go to the subforum you wish to post in and select "New Thread" at the top of the page. Please, make sure to search the forums first though before posting, as it is quite possible your question has been answered before.

---

### Post by chato92 on 2009-02-09
[QUOTE=Sorivenul;6708349]Have you retrieved the updated package lists?
```
sudo apt-get update
```
Then try the install again.


ok so i entered the line you gave me but it says Failed to fetch [http://security.ubuntu](http://security.ubuntu) blah blah blah 

should i erase my computer and re install it ??

---

### Post by Sorivenul on 2009-02-09
> **chato92 said:**
> should i erase my computer and re install it ??
No. Do *not* reinstall, yet.

Was that the only "Failed to fetch" line you received? Are you actually connected to the internet on the Ubuntu machine? Ping something and post back if you are connected for sure.

Also, did you edit your /etc/apt/sources.list by any chance?

---

### Post by chato92 on 2009-02-09
there where more than 4 lines and below that it also says some index files failed to download, they have been ignored, or old ones used instead

i have all my cables connected to my modem and router and its working because i have internet on my laptop but i think i did get some sort of error when installing should i reinstall it??

and a question how am i supposed to have my server computer connected to my other computer or how does the server computer work

how do i ping something??

---

### Post by Sorivenul on 2009-02-09
> **chato92 said:**
> there where more than 4 lines and below that it also says some index files failed to download, they have been ignored, or old ones used instead

i have all my cables connected to my modem and router and its working because i have internet on my laptop but i think i did get some sort of error when installing should i reinstall it??

and a question how am i supposed to have my server computer connected to my other computer or how does the server computer work

how do i ping something??
To ping try:
```
ping bbc.co.uk
```
If it works, just hit CTRL+c to cancel the action. 

If this is working, there is probably something wrong with your /etc/apt/sources.list

If there is something wrong with this file, you could manually edit it with direction from us, or at your option reinstall since this appears to be a fresh install (make sure to backup any important data, anyway).

As far as getting the server working with your other networked computers, lets wait until you get the server itself working. ;)

---

### Post by chato92 on 2009-02-09
ok well i typed in ping bbc.co.uk and it said 

ping: unknown host bbc.co.uk

and i dont have anything on this computer at the moment because i dont know how to do anything at all any suggestions ??

---

### Post by Sorivenul on 2009-02-09
> **chato92 said:**
> ok well i typed in ping bbc.co.uk and it said 

ping: unknown host bbc.co.uk

and i dont have anything on this computer at the moment because i dont know how to do anything at all any suggestions ??
That generally means the connection isn't recognized/isn't active.

I typically don't suggest a reinstall, but as you don't have anything on the machine at the moment, reinstalling may be your best option. Reburn you install CD, possibly downloading the Desktop CD instead and then installing the server components with:
```
sudo apt-get update
```
```
sudo apt-get install tasksel
```
```
sudo tasksel
```
Select LAMP and let the installer do its business. 
You may also want to install the Server kernel:
```
sudo apt-get install linux-server
```

Or, if you choose to install Server instead of Desktop, follow the [Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/") or [this tutorial]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts").

---

### Post by chato92 on 2009-02-10
so if i download and install the desktop cd and install it i can have internet or whatever and i can also install the server components and have a gui

---

### Post by Sorivenul on 2009-02-10
> **chato92 said:**
> so if i download and install the desktop cd and install it i can have internet or whatever and i can also install the server components and have a gui
Generally, yes. If you are connecting via Ethernet, it shouldn't be an issue. Wireless (if you use it) may be another issue.

Side note:
Make sure to burn the CD at a slow speed, as this helps prevent write errors. Also, it may be worth your time to run the "Check CD For Defects" option from the CD menu during the boot process.

---

### Post by chato92 on 2009-02-10
well its going to be connected by ethernet like my other desktop but i have a laptop that i do use the will there be any problems?? and im downloading the desktop cd right now

---

### Post by sharon.gmc on 2009-02-10
I wonder if it worked.  I installed Ubuntu but I had the same problem so I changed back to Linux

---

### Post by chato92 on 2009-02-10
ok im installing the desktop ubuntu right now but once it finishes how do i add the server commponents?? where do i enter the lines?

---

### Post by hyper_ch on 2009-02-10
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by chato92 on 2009-02-10
ok i tried to change the name of this thread but it dint work but i will remember what you said in the future

---

### Post by chato92 on 2009-02-10
ok i finished installing but i dont have internet what should i do ??

and where do i enter the lines so i can install the server components

---

### Post by Sorivenul on 2009-02-10
> **chato92 said:**
> ok i finished installing but i dont have internet what should i do ??

and where do i enter the lines so i can install the server components
Applications > Accessories > Terminal
Then enter the commands I gave earlier.

Some applications can also be installed through "Add/Remove..." as well as System > Administration > Synaptic Package Manager.

---

### Post by chato92 on 2009-02-10
do i need to have internet to install them because i have all my stuff connected to the pc and it doesnt have any internet

 help

---

### Post by Sorivenul on 2009-02-10
> **chato92 said:**
> do i need to have internet to install them because i have all my stuff connected to the pc and it doesnt have any internet
Okay then...  We need to check what devices you are using on the computer. If you know the exact ethernet card post it here. Otherwise in Applications > Accessories > Terminal type:
```
lspci | grep network
```

Note the "|" is a vertical bar, not an "l" or a "1". This will list your hardware and select the information regarding your network devices, then print it to the terminal. Post the output here. 

I've never heard of a computer not having *any* internet out of the box with Ubuntu, but there's a first time for everything. Also, have you checked Network Manager (the applet should be in the toolbar at the top of the screen) to make sure networking is enabled? 

And yes, you do need to have internet to install. Or a CD with all the files needed (quite a few in this case).

---

### Post by chato92 on 2009-02-10
well i typed it in and i dint get any thing it just went down to the next line and it told me to enter my password and i did and it dint do any thing and it tried it again and nothing and i do have networking enabled

---

### Post by tommynz1975 on 2009-02-10
In terminal some times called command line

could you type 
```
sudo lspci
```

and give us the responce.
Welcome to the world of ubuntu

---

### Post by chato92 on 2009-02-10
Yeah i figured it out thanks any way 
heres what i got on this old pc 

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:08.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)

---

### Post by Sorivenul on 2009-02-10
What type of computer is this, exactly?

Of note, VIA is notorious for Linux incompatibility. I have no experience with their products, but it is possible you need to enable a "restricted" driver. Go to System > Administration > Hardware Drivers and see if there is anything to enable there. 

If you can, post the output of:
```
ifconfig
```
This should spit out information regarding the names of any recognized network devices. From there we can try to manually request an IP in the terminal with something like:
```
sudo dhclient eth0
```
If "eth0" is your interface.

---

### Post by chato92 on 2009-02-10
i believe its a custom built computer my dads friend gave it to me 
if its no good after ill just use install ubuntu on my dell machine much quieter too 
 


ok so entered ifconfig and then it gave me this

 Link encap:Local Loopback  
 inet addr:127.0.0.1  Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING  MTU:16436  Metric:1
 RX packets:488 errors:0 dropped:0 overruns:0 frame:0
 TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:0 
 RX bytes:33872 (33.8 KB)  TX bytes:33872 (33.8 KB)

and then i typed sudo dhclient eth0 but it said ERROR while getting interface flags: no such device  and then i tried to only sudo dhclient and i got this

Listening on LPF/pan0/5e:c8:07:3a:ed:50
Sending on   LPF/pan0/5e:c8:07:3a:ed:50
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Sorivenul on 2009-02-10
What this means is that your network card, whatever it may be, is not recognized. If it isn't recognized it can't be configured. If it can't be configured, no internet, and so on... :| 

If you are willing to install it on your Dell, thats great, otherwise I'm sure somebody more familiar with your chipset may come along with a solution. Sorry I couldn't be of more help.

---

### Post by yknivag on 2009-02-10
Try entering:

```
sudo lshw -C Network
```

will give an idea of whether the card has been detected and whether a driver is in use or not.

---

### Post by chato92 on 2009-02-10
yeah thats probably thats what im going to do because its going to be quieter too and more ram i think im just going to switch the hard drives and reinstall the Ubuntu ill repost in a while and if someone knows how to make it work with my system please help

---

### Post by chato92 on 2009-02-10
ok i got this when i entered sudo lshw -C Network

does this help?

i will wait for a response so i dont have to reinstall the OS

*-network
     description: Ethernet interface
     physical id: 1
     logical name: pan0
     serial: 5e:c8:3a:ed:50
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
link=yes multicast=yes

---

### Post by yknivag on 2009-02-10
Interesting. It seems your Ethernet interface has been configured on the pan0 name (this is usually used for bluteooth)

It is, at least, being claimed by a driver and is Enabled.

Try:
```
sudo dhclient pan0
```

---

### Post by chato92 on 2009-02-10
Ok this is what i got

There is already a pid file /var/run/dhclient.pid with pid 10166
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/5e:c8:07:3a:ed:50
Sending on   LPF/pan0/5e:c8:07:3a:ed:50
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by cariboo on 2009-02-10
Your network adapter isn't being shown when you run **lspci** or **lshw**. It may be defective. Have you got another network adapter you can try?

Jim

---

### Post by yknivag on 2009-02-10
OK. Can you post the output of:
```
cat /etc/networking/interfaces
```
and also try
```
sudo ifdown pan0 && sudo ifup pan0 && sudo dhclient pan0
```

---

### Post by chato92 on 2009-02-10
well i dont think its defective because i can access the internet when i had XP installed on it 

Heres what i got

cat: /etc/networking/interfaces: No such file or directory
sudo ifdown pan0 " sudo ifup pan0 " sudo dhclient pan0
[sudo] password for server: 
ifdown: interface pan0 not configured
ifdown: interface  sudo ifup pan0  not configured
ifdown: interface sudo not configured
ifdown: interface dhclient not configured
ifdown: interface pan0 not configured

---

### Post by chato92 on 2009-02-11
ok so no one seems to know what to do so what if i keep Windows XP on my dell machine and i install ubuntu on VMWare and then install the server components or just install the server edition and add the gui what do you guys think?

---

### Post by jimv on 2009-02-11
Just download the Desktop CD and install that.  There's no significant difference between the Desktop Edition and the server edition.  You can install install anything on the Desktop edition that you can on the Server edition.  The bonus is that the Desktop edition comes with a GUI already.

---

### Post by Sorivenul on 2009-02-11
> **chato92 said:**
> ok so no one seems to know what to do so what if i keep Windows XP on my dell machine and i install ubuntu on VMWare and then install the server components or just install the server edition and add the gui what do you guys think?
If you're going to do that, you could just as easily try the WUBI installer. It should be on the CD.

If you are actually going to run Ubuntu as a server, however, I strongly suggest running it natively as opposed to virtually. I've had a hard time ever getting a server running steadily in a virtual environment. Just my two cents.

Good luck!

---

### Post by chato92 on 2009-02-11
ahh if you read through the this thread youll see that i downloaded both and i am currently runnning desktop version but i cant get internet on it so i am going to use my dell with xp on it and im going to install either the desktop or server version of ubuntu with VMWare so i can run it off my computer because its probably etter to just use one computer with both because i leave it on all the time so i dont have to use both computers

---


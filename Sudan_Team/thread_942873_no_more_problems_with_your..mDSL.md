---
title: "no more problems with your..mDSL"
date: 2008-10-09
forum: Sudan Team
---

### Post by ahsaeed on 2008-10-09
hi all .. many people were wory about that ubuntu don't support their internet wireless card they .. i had had the same problem .. but no it's no more ...!
**well in 8.04 **
i did the following :
1-in terminal :
*lsusb *
that to list ur USB devices
and here u will have a list of ur usb devices..
2-
*sudo modeprobe usbserial vendor=xxxx  product=xxxx*
the xxxx should be filled from the list that u got from the first step.. 
3- then use Kppp or gppp to add ur configurations ..
note that may not work from the fist time and u may need to restart ur system...




**and for 8.1 **
u don't have to do none of the above .. just in the network settings add ur username and the password  to the ppp connection and that is all!


and good luck!:guitar::lolflag:

---

### Post by Jefferies on 2008-11-09
None of this works for the AC8700 CDMA2000 1X mDSL Wireless Data Terminal used by Sudani.

Anyone know how to make it work?

---

### Post by Netcowboy on 2008-11-10
well don't know about cards but my Sudani mdsl USB modem work just fine with Hardy (8.4 ) and Intrpid (8,10 ) ,don't  know but I think there was a post about this issue in Linux4sudan.org fourms you may need to check it out 

Ubuntu ROCKs !:lolflag:

Regards 
Samer

---

### Post by Jefferies on 2008-11-12
@Netcowboy

Thanks.

Yes, there is this thread in the Linux4Sudan forum:

[http://www.linux4sudan.org/viewtopic.php?p=2497&sid=fd0f61f56fe7ee604e93d58144cca4d9#2497]("http://www.linux4sudan.org/viewtopic.php?p=2497&sid=fd0f61f56fe7ee604e93d58144cca4d9#2497")

Unfortunately (for me) it is entirely in Arabic!

I am an absolute beginner in Arabic (as well as Linux).

I would be extremely grateful if you could translate it for me.

I do hope that is not too much bother.

Many thanks in advance.

---

### Post by Netcowboy on 2008-11-12
well Jefferies I use da same mdsl modem you use :D
open you terminal ( applications ===> accessiories ===> terminal)

modify your wvdail.conf:
 sudo gedit /etc/wvdial.conf 

you gave it a shot and use mine 
[PHP][Dialer Defaults]
modem = /dev/ttyUSB0
Phone = #777
Username =sudani
Password =sudani
New PPPD = yes
[Dialer mdsl]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 9216000
Init = ATZ

Phone = #777
Username = sudani
Password = sudani
New PPPD = yes
[/PHP]

put that instead of yours

( I got more setting cause I use Gnome ppp )
after you did this save it then
type : [PHP]wvdial mdsl[/PHP]



ps: modem = /dev/ttyUSB0 <=== if it didn't work try another one

sorry I'm not good at helping lol

UBUNTU Rocks :lolflag:
Regards 

Samer aka Netcowboy

---

### Post by Jefferies on 2008-11-14
Thanks for the help, Netcowboy; however, things are still not working.

At console I entered the code as required. I did not get the same output as you indicate. In fact all I received was the following:

[PHP]Phone = #777
Username = sudani
Password = sudani
New PPPD = yes[/PHP]

I assume this is because I was not using Gnome PPP.

What is Gnome PPP?

If this means KPPP, I cannot install it as I do not have it on the installation disc... and guess what? You need an internet connection to install it. This is bloody frustrating and I am beginning tto believe a lot of my colleagues who know more than me who argue that Ubuntu is badly supported and poorly maintained.

I am now disinstalling Ubuntu as it clearly is simply wasting my time.

---

### Post by Netcowboy on 2008-11-14
Jefferies if you want I can call you to guide you send me your number in private message

---

### Post by Jefferies on 2008-11-15
@Netcowboy

Many thanks again.

The problem resolves itself upon the fact that there is a known (and typically for Ubuntu, it appears) unresolved bug in 8.10.

Aftedr setting up wvdial.conf as you indicate, the log reports that I do not have permission to use gnome pppd. This has now been complained about, bug reports logged and Heaven knows what else since the distro was first put up. Absolutely nothing has been done about it. The advice offered on these forums is at best flaky, at worst wrong or misleading.

Who in their right minds fails to give USER permissions for Gnome PPPD?????

Apparently, the script kiddies at Ubuntu do... and then do sweet FA about it when it is pointed out to them.

This is most frustrating. "Advice" includes: "Check man wvdial.conf for how to set up paths in wvdial.conf"... there is NO ADVICE about how to do this in that manual.

Look, it strikes me, that if Ubuntu wish to get ahead in the developing world (which is one of their mission statements), then they would do well to get themselves sorted out before releasing distros with such show-stopping bugs as not allowing anyone other than ROOT to use Gnome PPPD.

I have seriously had enough.

---

### Post by Jefferies on 2008-11-15
Apologies, netcowboy, but as a matter of principle and security I do not private message and I never release my private number.

---

### Post by Jefferies on 2008-11-15
Right, here we go:

After adding the code to wvdial.conf:

[PHP][Dialer Defaults]
modem = /dev/ttyUSB0
Phone = #777
Username =sudani
Password =sudani
New PPPD = yes
[Dialer mdsl]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 9216000
Init = ATZ

Phone = #777
Username = sudani
Password = sudani
New PPPD = yes  [/PHP]

and typing:

[PHP]wvdial mdsl[/PHP]

The following error is generated:

[PHP]Unable to tun /usr/sbin/pppd.
Check permissions, or specify a "PPPD Path"[/PHP]

This is a reported bug in 8.10 that still has yet to be resolved. See:

[http://ubuntuforums.org/showthread.php?p=6038861]("http://ubuntuforums.org/showthread.php?p=6038861")

The issue is that gnome-pppd can't gett online as normal user, but only as root.

The solution is to add user to the group "dip":

[PHP]ls -l /usr/sbin/pppd[/PHP]

Having done this, running 

[PHP]wvdial mdsl[/PHP]

finds the PAP-Secrets to be flaky, hangs up and then redials, at which point it generates the message that it cannot write to PAP-secrets (no permissions) AND pumps out error 19... which suggests that the username or password are not recognised by the server!!!

To be frank, I am sceptical that you have internet connection via Ubuntu.

---

### Post by Jefferies on 2008-11-15
So, giving up on the above methods, I reinstalled Ubuntu (for about the nine zillionth time) and dutifully entered all the data above into wvdial.conf file...

This time I changed directory to root and logged in there. I ran wvdial mdsl... and it works... but only as root.

And that is, of course, the bug.

Ridiculous.

---

### Post by Netcowboy on 2008-11-15
put : Sudo before command to run it as root

---

### Post by Jefferies on 2008-11-15
Here is the solution:

As Netcowboy has it:

[PHP]sudo gedit /etc/wvdial.conf [/PHP]

Then edit to:
[PHP][Dialer Defaults]
modem = /dev/ttyUSB0
Phone = #777
Username =sudani
Password =sudani
New PPPD = yes
[Dialer mdsl]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 9216000
Init = ATZ

Phone = #777
Username = sudani
Password = sudani
New PPPD = yes [/PHP] 

Now as root:

[PHP]sudo -s
wvdial mdsl
[/PHP]

Now you have internet.

Get Gnome-ppp.

Send the gnome-ppp icon to the desktop. Right click it. Select properties. A window will open. In the command space type 

[PHP]gksu /usr/bin/gnome-ppp[/PHP]

Close the window.

Open gnome-ppp. It will ask you for root password...

Bingo!

It works.

Many thanks netcowboy...

---

### Post by Netcowboy on 2008-11-15
lol Thanks God , Ubuntu was just that far from losing a user :P ,

---

### Post by Jefferies on 2008-11-15
Again, many thanks, Netcowboy...

Now to see what I can break in Ubuntu...

or back to my old stomping grounds in Assembly Language...:shock:

---

### Post by Netcowboy on 2008-11-16
you are welcome jefferies :)

---

### Post by Jefferies on 2008-11-16
Here's some of my system:

One physical hard disk dedicated to Windows XP Professional; a second physical hard disk dedicated to Ubuntu. Both HDDs are 75 Gb.

Seem to be having quite a lot of hang-ups on restart or close down out of Ubuntu 8.10,causing me to have to hard reboot to get back in.

Also, some screen artifacts on Firefox and Thunderbird start up (momentary screen flicker and bars), although I am running the correct drivers for my graphics card (NVIDIA 173 for GeForce FX 5200).

I shall reinstall the graphics drivers and see if this clears things up.

---

### Post by Jefferies on 2008-11-16
SOLVED:

The graphics card is not keen on the "Extra" setting under System -> Preferences -> Appearance [Tab: Visual Effects]

As for the Restart/Shut Down hang-up, this seems to be due to the system attempting to restart/shut down *before* the modem has completely disconnected. I shall write a little bit of code to flag the system to wait until this task is completed before shut-down is instigated. Windows manage to do this, so should Linux... when done I shall post it here.

---

### Post by Netcowboy on 2008-11-17
hello , jef you should post this in another post with new name

---

### Post by caliston on 2009-01-31
Sorry to hijack this thread, but I wonder if folks could tell me how mDSL works technically?  I'm trying to set up a machine for use by someone in Sudan but I'm not there so I'm having to do it blind (afraid it's XP, I was going to install Ubuntu until I discovered that it wasn't wifi and got scared that I wouldn't be able to sort it out over the telephone).

Summarising for anyone who happens to be reading this, I've managed to figure out mDSL is:
EVDO over CDMA, network infrastructure supplied by ZTE
USB connection uses a ZTE dongle - comparing pictures I think it's an MG478 or AC8700
Dongle first appears as a mass storage device, installs drivers into Windows automatically from that, and then switches to being the network device, which appears to be ID 05c6:6000 Qualcomm, Inc. 
Setup in the host OS is very similar to 3G GSM dongles - in other words not too different from an old dialup modem
NTC applies filtering for pornography but not (it is claimed) political content


What I'd like to know is the network environment:
Is there NAT?  Do you get a global IP address (ie not 10.*.*.*, 192.168.*.* or 172.16-31.*.*)
Are there any proxies that must be used?
Any ports inbound/outbound that are blocked?
What sort of bandwidth do you get up and down (I'm interested in central Khartoum)?
What sort of latency (ping times etc)?
Do things like voice over IP work? (what programs - Skype, Google Talk, other SIP?)


Is anyone able to fill in some details?  Thanks!

---

### Post by Netcowboy on 2009-01-31
Hello There Cliston , there no problems with Sudani mdsl zte modem(AC8700) , now ubuntu networkmanager Detect it as modem (just updated days ago - sudo apt-get update should do it :)- [https://bugs.launchpad.net/bugs/321213](https://bugs.launchpad.net/bugs/321213) -), you just need to setup an account number is #777 user= sudani pass=sudani , I neva got how they made their network it's 10.*.*.*
 about ports and so i don't think it's worked cause the type of network they have, torrents always report ports closed , neva managed to connect to any service 80,8080 looks like every port blocked (ports work with sudatel wired dsl),if it xp you got asoftware came with you just have to setup it , Note : sudani have another mdsl modem it's from LG i think but I've no clue about it ,
hope i was helpfull enough 
Samer

---

### Post by caliston on 2009-02-08
Thanks, that's really helpful.

So it seems it's fairly tightly locked down as far as ports go. Looks like Skype is going to be the best VOIP solution (if it'll work)... have to see what happens.  If I can manage to remote login to the machine then I can test it from outside.

Good to know that Ubuntu works on mDSL... I think I won't install it this time, but will see how it goes...

---

### Post by fathhi001 on 2009-03-01
hi there while im seekin de ubuntu forum website, accidently found your threads,im trying to make mdsl sudani works with unbuntu, ive been struggling for two weeks but still cant, its freaken complicated,i reconfiged the wvdial text as uve described,even though when i try to access as a root, i get the same problem. so I accessed the internet via windows,because there is no connetion with ubuntu and downloaded the gppp dial up, according to rules wvdial doesn't work and it runs as a command line, thus the gppp won't even work because its the same functions comparing with wvdial but it runs graphically.I did call the main help center of ZTE and i got their helps,they have sent me this program "zteac8700forlinuxsystem" but still have some problems to open it , it says the archive can't access the files. by the way my ubuntu is installed inside windows as a dual boot.

ubuntu 8.04 hardy.

---

### Post by Netcowboy on 2009-03-02
Hello fathhi001 , you can use sudani zte mdsl with network manager but to do this you need to make Network-Manager detect your modem , you need to this check it on this link [http://www.linux4sudan.org/web/viewtopic.php?f=18&t=580]("http://www.linux4sudan.org/web/viewtopic.php?f=18&t=580")

---

### Post by Jefferies on 2009-05-08
For some reason best known only to themselves, the Ubuntu developers have failed to include wvdial in Ubuntu 9.04. However, all is not lost.

You will need to get wvdial and certain dependencies. These can be obtained at:

**[http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial)**

I found I needed only the following dependencies:

[For wvdial] libuniconf4.4

[For libuniconf4.4] libwstream4.4-base *as well as* libwvstreams4.4-extras

[For libwvstream4.4-base] libxplc0.3.1.3

Then as I showed above to configure wvdial.conf...

---

### Post by Jefferies on 2009-05-08
Further to the above...

A far simpler solution is now offered in Jaunty:

Simply open Network Connections. Click on the Mobile Broadband tab, next highlight the Auto Mobile Broadband (CDMA) connection and select "Edit". On the Mobile Broadband tab, fill in the fields (Number: #777; Username: sudani; Password: sudani). Now apply and then close.

Fire up the connection and away you go...

Hence, no wvdial included in Jaunty, I suppose.

---

### Post by zero-n on 2009-10-07
Yeah that work for me well in jaunty it's so much easy thanks

---

### Post by alab0 on 2011-02-15
Thank u Jefferies,Surely it's work successfully :p

---


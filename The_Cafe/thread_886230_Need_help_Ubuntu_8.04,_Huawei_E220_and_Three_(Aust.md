---
title: "Need help: Ubuntu 8.04, Huawei E220 and Three (Australia)"
date: 2008-08-10
forum: The Cafe
---

### Post by Sergicles on 2008-08-10
Hi All, 

Has anybody managed to setup a Huawei E220 HSDPA modem on Ubuntu 8.04 with Three (Australia) as a provider?

I know there are a lot of posts here, that talk about wvdial.conf, etc. However none of them seem to work for me.  Additionally, I am not after running a terminal command (wvdial hsdpa for example) every time I want to connect.  The modem is for the Eee PC running Ubuntu 8.04, mainly for use on public transport, hence I just want to click &#8220;connect&#8221; and, errr, get connected.

Is there a sane way of configuring the modem and connecting to the network using some sort of a GUI application?  If so, is there a detailed &#8220;howto&#8221;?

Also, I am aware of the Vodafone utility, however it refuses to connect for some reason &#8211; basically doesn&#8217;t want to work for me.  Also, it&#8217;s hardwired for Vodafone dial numbers and net access name (I haven&#8217;t had the time to look at the source yet).

So, any step-by-step instructions to get the Huawei E220 modem working with Three (Australia) and tips for configuring GUI apps would be VERY appreciated.  

Thanks,
   Serg

---

### Post by sirwilliamthenice on 2008-08-11
there is a great walkthrough on this site... providing you have the information i have listed below handy.. 
shows you how to set up a gui app as well.. personally i have no issue type in at the pormpt.. its only two words and i can see whats going on. 

[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/](http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/)

**provider info**

Australia - Three - Gutsy, wvdial.conf - (ellyaht)

[Dialer 3g]

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
username = username
Password = password
Dial Command = ATDT
Baud =466600
Init4 = AT+CGDCONT=1,"IP","3netaccess"

i took this of another post which has a huge list of providers it is here.. 

[http://ubuntuforums.org/showthread.php?t=633981](http://ubuntuforums.org/showthread.php?t=633981)



hope thats some help to you.

---

### Post by Slingshot on 2008-08-11
> **Sergicles said:**
> Hi All, 

Has anybody managed to setup a Huawei E220 HSDPA modem on Ubuntu 8.04 with Three (Australia) as a provider?

I know there are a lot of posts here, that talk about wvdial.conf, etc. However none of them seem to work for me.  Additionally, I am not after running a terminal command (wvdial hsdpa for example) every time I want to connect.  The modem is for the Eee PC running Ubuntu 8.04, mainly for use on public transport, hence I just want to click “connect” and, errr, get connected.

Is there a sane way of configuring the modem and connecting to the network using some sort of a GUI application?  If so, is there a detailed “howto”?

Also, I am aware of the Vodafone utility, however it refuses to connect for some reason – basically doesn’t want to work for me.  Also, it’s hardwired for Vodafone dial numbers and net access name (I haven’t had the time to look at the source yet).

So, any step-by-step instructions to get the Huawei E220 modem working with Three (Australia) and tips for configuring GUI apps would be VERY appreciated.  

Thanks,
   Serg

Check in with cyberknutt over at the Whirlpool 3 forums. This is his site [http://3.themuses.org/]("http://3.themuses.org/"). I believe he has had some dealings with Ubuntu and the soap-on-a-rope from 3 :).

Good luck.

---

### Post by mips on 2008-08-11
Just install the Vodafone Mobile Connect client for linux and change your settings to suite the 3 network. It is very simple to use and is GUI based.

[http://www.betavine.net/bvportal/web/linux_drivers](http://www.betavine.net/bvportal/web/linux_drivers)
[http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux](http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux)

There was a long thread on this in the networking section that I'm trying to locate. Suspect it was moved to the archive.

EDIT: Found the thread
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)

The settings you need to know for Three Australia are,
Carrier:              Three
APN:                  3netaccess
Username:          a
Password:           a
Gateway:            [FONT=Verdana][SIZE=1]DNS:  					202.124.68.130, 202.124.76.66[/SIZE][/FONT]

Just check as the VMC client might already have this network listed under networks.

---

### Post by Sergicles on 2008-08-11
Got it going :) 

sirwilliamthenice; your dialer definition was what I needed, solved 98% of my issues.  The last 2% was me forgetting to rerun wvdial to generate a default conf file.  Bah!

At the end, I decided to go with the console... Just have a button, on the pannel, that runs in the terminal.  Seems to be a better option to gnome-ppp or typing stuff manually. 

Thanks again :)



Serg

---

### Post by sirwilliamthenice on 2008-08-11
glad to be of assistance..
but all thanks should go to the original posters it should.. 

its fine with wvdial.. plus typing in terminal makes you look 733T on the train on the way to work. 

:)

---

### Post by Sergicles on 2008-08-11
Yeah, I am going for the more of an inconspicuous look

---

### Post by ColombianBootloader on 2008-12-11
hi there

well, I have tried to fix my e220 with my Ubuntu version 8.04. but I got the following screen when I run the wvconfig. I did change the parameters using gedit. but I just got the next output.

sasswillo@sasswillo-laptop:/$ wvdialconf

Editing `/etc/wvdial.conf'.


Scanning your serial ports for a modem.


Modem Port Scan<*1>: S0   S1   S2   S3   

WvModem<*1>: Cannot get information for serial port.

ttyUSB0<*1>: ATQ0 V1 E1 -- OK

ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei

ttyUSB0<*1>: Speed 9600: AT -- OK

ttyUSB0<*1>: Max speed is 9600; that should be safe.

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK

ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK

ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK

ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei

ttyUSB1<*1>: Speed 9600: AT -- OK

ttyUSB1<*1>: Max speed is 9600; that should be safe.

ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK


Found a modem on /dev/ttyUSB0.

Modem configuration written to /etc/wvdial.conf.

/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6670': Permission denied

/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor

ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

any suggestions??? I just do not know what is wrong..please any help is more than welcome

---

### Post by cdekter on 2008-12-11
You need to run wvdialconf as superuser (using sudo)

Incidentally, I have the Huawei E160G USB stick, and I've got it working perfectly just using Network Manager 0.7 on Hardy. There is a PPA somewhere that lets you install nm0.7 on Hardy - a quick Google should find it.

---

### Post by ColombianBootloader on 2008-12-18
Hi there...

Well I should be honest with you mate, I am pretty newby to Ubuntu, and therefore to Linux. I am learning and I admit it is quite challlenging, but I liket it. so first things first, lol..how could I become a superuser and what is a PPA?? are u talking about an application that I have to download and use in Ubuntu, and if it is that how could I use it if I am usuing the e220 in windows?? by the way if there is a good tutorial in all these, well I am more than welcome to know read it lol..
I would appreciate a quick answer from anyone, I just want to stop using Windows as much as I can use it, I am getting really annoyed with the virus stuff lol...thank you.

---


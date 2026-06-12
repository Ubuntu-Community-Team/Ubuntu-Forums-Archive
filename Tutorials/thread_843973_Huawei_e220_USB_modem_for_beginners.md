---
title: "Huawei e220 USB modem for beginners"
date: 2008-06-29
forum: Tutorials
---

### Post by Fingers &amp; Thumbs on 2008-06-29
***[COLOR="Navy"]Welcome to my first HOWTO.[/COLOR]***

   Before I begin, I would like to point out that I am NOT a computer expert, but after 6 months spent with [COLOR="DarkOrange"]ubuntu[/COLOR] I have come to love computers as I no longer feel restricted or dictated to by my OS, in fact, I feel liberated, and I would like to thank all of the forum members as it is their contribution that makes all of the hurdles of computing shrink to a size that I feel I can approach with confidence.

  As a result, I now feel confident enough to write a HOWTO and believe I actually have one to fill a much needed gap.

  Anyway.....

Initially when I was trying to set up my e220, it was, quite simply, a headache. There are dozens of threads, within these forums alone, and countless elsewhere, but as these were generally responses to threads along the lines of "HELP!! Modem not working" they're generally asking for that users specific outputs and troubleshooting them, without explaining what was actually going on.

One HOWTO exists by tazz_tux, and I must acknowledge this as it definitely helped me a gain a better understanding, although for a n00b like myself much of it was over my head.

***[SIZE="3"][COLOR="Blue"]So lets get your modem working shall we......[/COLOR][/SIZE]***

Firstly, you should make sure you have wvdial installed, it is in the repositories, you can either open synaptic package manager and look for it there.[U][COLOR="Red"]

Main menu >System >Administration >Synaptic Package Manager[/COLOR][/U]

 or open a terminal and type

```
sudo apt-get install wvdial
```

Now, with your modem plugged into an available USB port...
(note:: this is more reliable connected directly to your computer as opposed to a hub, and also, some users report problems with the longer cable, but I have had no such problems on the 5 I have set up personally.)

```
sudo wvdialconf
```

What this does is reads all of the settings you will need directly from your modem and writes them to a file called wvdial.conf. Without sudo it will read from the modem but cannot write the file.

IMPORTANT!! You should NOT edit any of the completed lines in wvdial.conf, the settings that the above command wrote to that file are unique to your modem/service provider, so copying anyone elses from a thread will only prevent yours from functioning. However you will need to edit 3 lines of text: Phone, Username and Password.

Again, in a terminal type...
```
sudo gedit /etc/wvdial
```

This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone
; Password
; Username
```

As you can see, Phone, Password and Username are not designated and are also preceded by a ; followed by a space. First of all delete the ;'s and spaces so that P,P and U respectively are the first characters on their lines. now following the same format as the completed fields add ( = )to each line and give them a value, so you should have something that looks like this.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = Anything
Username = Anything
```

Before you save the file and exit, make a note of the second word in the first line, in the case of my example (Defaults) This is the name of the profile you will need to invoke for a connection.

How you wish to connect now is a matter of preference, I will now explain your options and try to outline the pro's and cons of each.

Firstly, If you feel happy having a connection with no GUI, no taskbar applet or any visual feedback on your desktop, then it's very easy.

Press _[COLOR="Red"]Alt-F2[/COLOR]_ and type 

```
wvdial Defaults
```

Or replace the word Defaults with whatever was in the first line of your wvdial.conf.

If you wish for your modem to connect automatically at log on, take your mouse to the the panel menu and navigate >System >Preferences >Sessions and under the "Startup Programs" Tab, click the "Add" button and where it says "Command" Type:

```
wvdial Defaults
```

Be sure also to fill in the "Name" box, but what you type in there is up to you, simply "Modem" or "E220" is ideal for your own future reference.





Now you may prefer a graphical user interface to get connected, if so you have a few choices.

If you use gnome then i recommend *[COLOR="Lime"]gnome-ppp[/COLOR]*

```
sudo apt-get install gnome-ppp
```

for kde, *[COLOR="Lime"]kppp[/COLOR]*

```
sudo apt-get install kppp
```

Another one some people are using is vodafone-mobile-connect-card-driver-for-linux, (what a mouthful) but you will not find this in the repositories and it is quite a bulky program (like it's name) that requires rather a lot of python dependencies. It does have some extra functions but I am yet to see any of them work, although to be fair I have not tried it with a vodafone sim, but it will still connect you nonetheless.

Whichever utility you choose the following instructions are the same.

If you closed your text editor after saving wvdial.conf then type:

```
gedit /etc/wvdial.conf
```

To bring it back up. Notice there was no sudo this time? Don't worry, Admin privaleges aren't necessary as we won't be editing the file, we just need that information at hand.

All that needs to be done is to complete any fields in your ppp's GUI's settings, using wvdial.conf as reference.

[COLOR="Blue"][B]Some points of possible confusion explained.
[/B][/COLOR]
*[COLOR="RoyalBlue"]What's an init string??[/COLOR]*

see the line in wvdial conf that looks something like  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK, well that's what you need to put in the init string box.

*[COLOR="RoyalBlue"]What's the phone number??[/COLOR]*

My connection is with 3uk, so the number I set mine to dial is *99#
If you have another provider it will no doubt be different, but google should be able to answer that, or contact your provider.

That's it, click connect you should be up and running. try opening up your browser and searching, if all is well, happy browsing. Perhaps you get a message saying "Offline Mode" This is just Firefox thinking it knows best, simply click on the browsers "File" in the tool bar and de-select "Work offline"

*[COLOR="RoyalBlue"]Still no connection???[/COLOR]*

If you're using a GUI to connect, there may be a function called "Stupid Mode" selecting this "apparently" forces your modem to ignore init strings,and will usually sort this problem, but at this point I am unable to explain why and I'm only just scratching at what an init string does myself so I'll avoid any further details here to avoid confusion or giving misleading info. I may edit this at a later date if I consider it appropriate

If your GUI doesn't have this option, or you have opted for my no-GUI approach, then you can go back to....

```
sudo gedit /etc/wvdial.conf
```

And add the line...

```
Stupid mode = 1
```

Now I hope you are connected.

As I mentioned at the beginning, I am no expert, I am just relaying my experience of setting up 5 such modems, perhaps this HOWTO doesn't work for you, if so leave a message, I'm quite sure I've read just about everything on the net about setting it up under linux, so if you have a problem, I've probably heard it before, and will probably know where to look.

One final note, If you have used this HOWTO and are still having problems, please let me know. Maybe you think I could have been clearer about something. In any case all feedback will be welcomed and appreciated. If you have got it working, which I sincerely hope you have, please leave a message saying which type of setup you opted for, which GUI, or no GUI, this could prove helpful to others in the future.

Just as I hope you have found this helpful.

---

### Post by chmac on 2008-06-29
Using Ubuntu 8.04 I plugged in my Huawei E220 and it worked. Finding software to make it work was a little troublesome. Gnome-ppp worked fine, but the various data card specific apps (vodafone mobile connect for linux / umtsmon) failed.

I [upgraded to NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059") and it now works flawlessly for me. Well, not quite flawlessly, I have to manually edit my routing table to set the modem as the default route instead of wifi (I have both connected), but it works very well. :)

---

### Post by Fingers &amp; Thumbs on 2008-07-01
That's the great thing about ubuntu, huh.
  Just about any piece of hardware can be made to work with it if you have the patience and inclination, and when enough users are using or trying to use a particular piece of kit or type of equipment, a simpler, automatic solution generally finds it's way into the default desktop environment.
  So that's great news that Network Manager 0.7 will be including support for mobile broadband connections, although as it is currently only at the development stage and therefore could potentially leave a user with no connection, and I have mine working without issue, I'll personally be waiting for the official final release.
  Thanks for posting this info chmac, I will definately be following this developement closely.

---

### Post by Melindrea on 2008-07-18
You sir, rock. =)

I finally grew tired of Vodafone's moodiness, and found this HOW-TO. No waiting for ten minutes before Vodafone decides that it doesn't feel like finding my modem, just... immediately, working! =)

---

### Post by KJE on 2008-07-18
Great job.....
Thanks very much.......

---

### Post by Fingers &amp; Thumbs on 2008-07-18
Thanks for the feedback guys.

just a quick update, I have got the modem working with Network Manager 0.7, but it has a few ideosynchracies so until I get to the bottom of it I will refrain from adding it to the Howto. It works with very little setting up, and FF3 doesn't go offline, but there are some minor quirks I would like first to understand.

---

### Post by cpetercarter on 2008-07-24
We have ignition! Great stuff! Many thanks.

---

### Post by zenkaon on 2008-07-28
OK, after reading this thread I decided to go out and buy a 3 pay-as-you-go Huawei E220 on the UK 3 network.

I am running hardy heron on a Toshiba laptop.

When I run wvdialconf I get:

```

john@Gluon:~$ sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```

I have had a look in my system logs. In messages I see
```

Jul 28 19:15:46 Gluon kernel: [  390.154199] airprime 2-2:1.0: airprime converter detected
Jul 28 19:15:46 Gluon kernel: [  390.154325] usb 2-2: airprime converter now attached to ttyUSB0
Jul 28 19:15:46 Gluon kernel: [  390.154364] usb 2-2: airprime converter now attached to ttyUSB1
Jul 28 19:15:46 Gluon kernel: [  390.154403] usb 2-2: airprime converter now attached to ttyUSB2
Jul 28 19:15:46 Gluon kernel: [  390.154411] usbcore: registered new interface driver airprime
Jul 28 19:15:46 Gluon kernel: [  390.164652] usbcore: registered new interface driver libusual

```

and in syslog I see

```

Jul 28 19:15:55 Gluon kernel: [ 1041.995611] airprime ttyUSB0: airprime_open - failed submitting read urb 0 for port 0, error -2
Jul 28 19:15:55 Gluon kernel: [ 1041.995720] airprime ttyUSB1: airprime_open - failed submitting read urb 0 for port 1, error -8
Jul 28 19:15:55 Gluon kernel: [ 1041.995875] airprime ttyUSB2: airprime_open - failed submitting read urb 0 for port 2, error -8

```

Can anyone point me in the right direction.

I have tried this on XP, it works fine, so no modem problem.

---

### Post by zenkaon on 2008-07-28
Ah ha, only minutes after posting my problem I have solved it. Brilliant!!

I install Network Manager 0.7 SVN using this thread:
[http://ubuntuforums.org/showthread.php?t=797059&highlight=huawei+e220](http://ubuntuforums.org/showthread.php?t=797059&highlight=huawei+e220)

Fantastic, I now have broadband all over the UK and can do it all on ubuntu!!!

The new nm-applet looks really neat as well, nice :guitar:

---

### Post by oceanpink on 2008-07-30
hi thanx for this guide as im completely new to linux. I have just bought the elonex webbook and the 3uk huawei e220. the webbook runs on harty heron and the help files mention  networkmanager 8. I need help finding my way around and feel like im  drowning here. my questions are  where do i put in the codes? and do I  need to install the modem to a windows pc first. thanx again confused newbie.

---

### Post by oceanpink on 2008-07-31
Good news! after going back and forth  I have managed to find the terminal (Applications - accessories - terminal )  I put in 1st set of codes and GREAT it found the huawei but when i put in codes: sudo gedit /ect/wvdial. the wvdial ( /ect)- gedit, window comes up and its a blank page. Im half way there now, can anyone please tell me how to get the next page so i can edit it. thanx from a very ubuntu tech newbie

---

### Post by chmac on 2008-07-31
> **oceanpink said:**
> hi thanx for this guide as im completely new to linux. I have just bought the elonex webbook and the 3uk huawei e220. the webbook runs on harty heron and the help files mention  networkmanager 8. I need help finding my way around and feel like im  drowning here. my questions are  where do i put in the codes? and do I  need to install the modem to a windows pc first. thanx again confused newbie.

Have you upgraded to NetworkManager 0.7? Do that first. Then simply plug in your modem. Nothing else required. Then under NetworkManager, right click the icon, go to Edit Connections > Mobile Broadband, then either edit the existing connection or create a new one. Enter the relevant info, and it should work.

---

### Post by mundo on 2008-08-03
> **chmac said:**
> Have you upgraded to NetworkManager 0.7? Do that first. Then simply plug in your modem. Nothing else required. Then under NetworkManager, right click the icon, go to Edit Connections > Mobile Broadband, then either edit the existing connection or create a new one. Enter the relevant info, and it should work.

How can I obtain "NetworkManager 0.7". I have looked in Synaptic Package Manager but can't find it.

---

### Post by mundo on 2008-08-03
Sorry, didn't see the link in your post:

[http://ubuntuforums.org/showthread.php?t=797059]("http://ubuntuforums.org/showthread.php?t=797059")

---

### Post by daithi81 on 2008-08-03
I had the same problem as oceanpink above. After I try the sudo wvdialconf command I get the following response:

```
david@David-Desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<Info>: Device or resource busy
Modem Port Scan<*1>: S0   
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
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
ttyUSB1<Info>: Exec format error
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB3<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB3<*1>: Speed 9600: AT -- OK
ttyUSB3<*1>: Max speed is 9600; that should be safe.
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB4<Info>: Exec format error
ttyUSB5<Info>: Exec format error
Modem Port Scan<*1>: USB5 

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB3<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
david@David-Desktop:~$ 



```

Any ideas?

---

### Post by cpetercarter on 2008-08-03
I think that oceanpink's problem may simply be a typo. It should be ```

sudo gedit /etc/wvdial.conf
```
and not
```
sudo gedit /ect/wvdial.conf
```
@daithi81
I think you have successfully completed the first step. The response says that wvdial has found a modem and has written information about the modem configuration to /etc/wvdial.conf. Now you have to open that file (see above) and edit it, as in post #1 in this thread.

---

### Post by chmac on 2008-08-03
If you [upgrade to NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059") (which is very easy), you should find that your modem "just works" with no real configuration required. I think you'll find it much easier than editing configuration files.

---

### Post by cpetercarter on 2008-08-04
My reason for not using Network Manager 0.7, instead of the method developed by the OP in this thread, is that the [HowTo on installing Network Manager]("http://ubuntuforums.org/showthread.php?t=797059") warns:

> Make sure you can configure your network by hand if this breaks your networking so you can recover it. If you can't afford to be without network connectivity do not try this!

I general I try to avoid software which might break my system.

---

### Post by shr2004 on 2008-08-04
Thanks a lot for the tutorial, with its help I managed to get connected.
Previously I was unable to connect, actually its my fault. in the browser I used auto proxy, but when I set to no proxy then I can connect, I am now using the script given in the following thread which is a nice menu driven program, any one interested can check it at: [http://ubuntuforums.org/showthread.php?t=709331](http://ubuntuforums.org/showthread.php?t=709331)

Thanks

---

### Post by chmac on 2008-08-05
> **cpetercarter said:**
> I general I try to avoid software which might break my system.

True. I'm running NetworkManager 0.7 and it works well. Occasionally the applet dies and I need to restart it by pressing ALT-F2 and then typing "nm-applet". But otherwise, it works fine for me.

I'd suggest the upgrade to 0.7 is less likely to "break" your system than trying to mess around with the networking settings yourself. It's also *much* easier than the other approaches, in my opinion.

---

### Post by cpetercarter on 2008-08-05
Ideally, Ubuntu would support plug-and-play for all mobile broadband modems, but unfortunately we are not there yet. Network Manager 0.7 looks like an important step towards this objective, and I am sure that you are right when you say that it is easy to use, easier that editing a config file.

My point was simply this. If I edit a config file and mess up, I can always go back to where I started (provided that I have, where appropriate, made a back-up of the original file before starting). If I use a programme like Network Manager and it does something unexpected to my network setup (and the How To suggests that it might do this), I don't know where I would start in putting things right.

---

### Post by chmac on 2008-08-05
> **cpetercarter said:**
> My point was simply this. If I edit a config file and mess up, I can always go back to where I started (provided that I have, where appropriate, made a back-up of the original file before starting). If I use a programme like Network Manager and it does something unexpected to my network setup (and the How To suggests that it might do this), I don't know where I would start in putting things right.

If your networking settings are borked by NM 0.7 you could uninstall it. It's not a permanent upgrade. You could downgrade if you have problems.

---

### Post by Fingers &amp; Thumbs on 2008-08-08
I must apologise for my absence over the past couple of weeks, free time has been somewhat limlted. Thanks chmac for stepping in and offering support.

I am currently using NM 0.7, but as it does not work as flawlessly (for me) as my original instructions, I am still refraining from supporting it in the main body of my howto. 

Some points I would like to make about NM 0.7:

1. Don't be afraid to try it, if it doesn't work for you an uninstall will return you to your previous state.

2. I found it to recognise my modem easily without much prompting from myself, although I can't say for sure if this is because I had already gone through the steps outlined in this howto, or if it is completely independent of these steps. (cpetercarter makes a good point, that is; with the steps in the howto it is clear to see what files and programs are doing what and why, but with NM 0.7, one really doesn't know why it's doing what it is.)

Perhaps chmac or indeed anyone else could enlighten me as to how to resolve the issues I'm having with NM 0.7:

1. To garuntee that I will be able to connect after boot up I must have the dongle unplugged at boot time (very annoying, as I don't always remember to unplug and if it fails I have no option but to reboot)

2. Quite often nm-applet reports 3 GSM modems forcing me to guess which one is really the modem (only mildly bothersome but nonetheless an annoyance)

All in all though I am quite pleased with NM 0.7, truly a step in the right direction. Once it has been polished it will certainly make things a lot better for those of us who require mobile internet.

---

### Post by chmac on 2008-08-08
> **Fingers & Thumbs said:**
> 1. To garuntee that I will be able to connect after boot up I must have the dongle unplugged at boot time (very annoying, as I don't always remember to unplug and if it fails I have no option but to reboot)

I have the same issue. The problem is that if your modem is plugged in on boot, it will automatically be dialled on boot. So it's connected automatically by another application. I think unplugging and replugging should allow NM to manage it though.

> **Fingers & Thumbs said:**
> 2. Quite often nm-applet reports 3 GSM modems forcing me to guess which one is really the modem (only mildly bothersome but nonetheless an annoyance)

This is due to the way the modem presents itself to the computer. It presents 3 serial USB devices. The first one is the "modem" the other two are for other stuff. So normally the first time I plug in my modem, I get the 3 devices. On subsequent plug ins, I get only 1 device.

I have these two issues. They're not really related to NetworkManager itself though. It's part of the wider system and how it handles the modems.

Cheers - Callum.

---

### Post by wayneandleanne on 2008-08-08
thanks:lolflag:

---

### Post by Fingers &amp; Thumbs on 2008-08-08
Thanks chmac, I'm pretty sure those issues will be ironed out in time, maybe it's not an issue with many dongles. It's surely the fact that the e220 contains that virtual cd which is confusing things. Even though I prefer the wvdial method because it works without any of these issues, I'm going to be sticking with NM for the time being, as I know once these issues are sorted, all other methods will be obsolete. I hope it gets sorted quite soon, or I may be forced to give up and return to wvdial.

---

### Post by chmac on 2008-08-08
> **Fingers & Thumbs said:**
> I hope it gets sorted quite soon, or I may be forced to give up and return to wvdial.

The issues shouldn't affect the functionality of the system though. If you boot with the modem plugged in, unplug and re-plug, and it should work. Does that work for you?

Otherwise, having three modems listed instead of 1 is purely a visual thing. Just use the first one and ignore the others.

The manual dial up method is fine, but it doesn't notify HAL when you connect / disconnect. So applications like Firefox, Evolution, Liferea, etc don't automatically switch on/offline.

---

### Post by dorothy on 2008-08-10
yeah, no.

chmac, I followed the instructions on your link and this basically nuked all my network connections. I just got done re-installing 8.04 again... there's an hour out of my life I'll never get back. 

On my Eee PC, running the default Xandros, my E220 works like a charm. 

I'd say getting mobile broadband to work under Hardy Heron 8.04 is anything BUT easy.

---

### Post by chmac on 2008-08-11
> **dorothy said:**
> yeah, no.

chmac, I followed the instructions on your link and this basically nuked all my network connections. I just got done re-installing 8.04 again... there's an hour out of my life I'll never get back. 

On my Eee PC, running the default Xandros, my E220 works like a charm. 

I'd say getting mobile broadband to work under Hardy Heron 8.04 is anything BUT easy.

Sorry to hear about your troubles.

What were the issues with your network settings? What was "nuked"?

If you un-install NetworkManager 0.7, you'll be able to revert your network settings. A full OS reinstall should not be necessary.

My experience with mobile broadband on Ubuntu, after upgrading to NM 0.7, has been painless.

---

### Post by dorothy on 2008-08-11
> **chmac said:**
> Sorry to hear about your troubles.

What were the issues with your network settings? What was "nuked"?

If you un-install NetworkManager 0.7, you'll be able to revert your network settings. A full OS reinstall should not be necessary.

My experience with mobile broadband on Ubuntu, after upgrading to NM 0.7, has been painless.

Mine has been anything BUT painless.

The network applet completely disappeared and I had not network connectivity. 

I am runing Ubuntu 8.04, fully updated, on an iBM ThinkPad x24 using a Huawei E220 from Vodafone Ireland.

---

### Post by chmac on 2008-08-11
> **dorothy said:**
> The network applet completely disappeared and I had not network connectivity.

The applet in the system tray? That happens to me now and then. Press ALT-F2 and type nm-applet and press enter, it should pop right back. A little inconvenient, and potentially very problematic if you don't know how to restore it. Did you have any other problems?

---

### Post by Fingers &amp; Thumbs on 2008-08-11
Ooop!

Hahah, I forgot about the disappearing applet issue. It is due to these problems that I am yet to include NM 0.7 in the howto. NM 0.7 potentially requires less setting up, which may seem preferable to a new user, but as it does not run flawlessly I still prefer to recommend wvdial with or without it's graphical front ends. It may require some setting up, but should just work every time without issue after that.

Although, as I have mentioned before I would still encourage people to give NM 0.7 a try, if it doesn't work how you would like, an uninstall would take you right back so no issues there. But, as I am unable to help anybody resolve the issues with NM 0.7 (I can't even help myself with them) it would not be right for me to add it to the howto.

I am supprised that not one of these issues has been resolved yet, I feel a return to wvdial is iminent for me; I don't like swearing at poor defenceless inanimate objects. Particularly such expensive ones.

---

### Post by chmac on 2008-08-11
> **Fingers & Thumbs said:**
> Hahah, I forgot about the disappearing applet issue. It is due to these problems that I am yet to include NM 0.7 in the howto.

In my experience the applet only crashes when trying to connect to a network. It hasn't crashed during use at all for me. So long as you know how to restart it (alt-f2, nm-applet, enter) I find it to be a minor inconvenience.

Plus, NetworkManager updates HAL, which is *huge* in my view. Otherwise, you switch from a wired/less network onto 3g and have to manually tell Firefox, Evolution, Liferea, etc that you're back online. Then tell them again that you're offline. NM is just so elegant... :)

But I feel like we're all repeating the same points over and over, so I'll leave it at that.

---

### Post by JC Cheloven on 2008-08-12
@ fingers & chmac:
Thanks for all the useful info posted in this thread. 

I dedided to give NM7 a try. I've just installed it, currently at the point of 'restart required', and willing to thank you now, just in case I don't get any nework connection at restart :-D

BTW, chmac, I'd have love to see a more precise hint about uninstalling NM7 and reverting to the previous state. If I get no network connection, I'm unsure if aptitude/synaptic will do ...  Anyway, here we go...

EDIT: well, I'm back. It didn't work for me. Installed NM7, rebooted, plugged the E220, and nothing happened. Created a mobile broadband connection in NM7 with username and psw 'orange' as I saw somewhere else, gave my pin, and still nothing. Tried both gprs and gsm. I'm not specially adept to networking, so I may be missing something. Anyway, NM7 seems to be better and more responsive than NM6, and at least manages ok my wired connection. I'm about to try the method of the OP, and will come back again (if I'm still able to connect LOL )

btw to the OP: a couple details: to launch graphical apps like gedit, is better to use gksudo than sudo. I've read elsewhere [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) that quite serious problems may arise using sudo with some graphical apps (although perhaps not with gedit, it is better to spread the good habits). Also it is a mistype in the code box asking to run sudo gedit /etc/wvdial. The file should be wvdial.conf, I think ;-)

EDIT: Back again. Ran sudo wvdialconf, got the /etc/wvdial.conf file, but it has this inside: 

```

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

```

This is not as expected; I guess wvdial is not detecting my e220, which blinks twice each 2.7sec, meaning that it's searching for a net. Perhaps it is messing around with NM7, which I installed previously, or with my wired connection, which I have on? I don't think so... Any ideas, guys?

---

### Post by dorothy on 2008-08-13
> **Fingers & Thumbs said:**
> ***[COLOR="Navy"]Welcome to my first HOWTO.[/COLOR]***

   Before I begin, I would like to point out that I am NOT a computer expert, but after 6 months spent with [COLOR="DarkOrange"]ubuntu[/COLOR] I have come to love computers as I no longer feel restricted or dictated to by my OS, in fact, I feel liberated, and I would like to thank all of the forum members as it is their contribution that makes all of the hurdles of computing shrink to a size that I feel I can approach with confidence.

  As a result, I now feel confident enough to write a HOWTO and believe I actually have one to fill a much needed gap.

  Anyway.....

Initially when I was trying to set up my e220, it was, quite simply, a headache. There are dozens of threads, within these forums alone, and countless elsewhere, but as these were generally responses to threads along the lines of "HELP!! Modem not working" they're generally asking for that users specific outputs and troubleshooting them, without explaining what was actually going on.

One HOWTO exists by tazz_tux, and I must acknowledge this as it definitely helped me a gain a better understanding, although for a n00b like myself much of it was over my head.

***[SIZE="3"][COLOR="Blue"]So lets get your modem working shall we......[/COLOR][/SIZE]***

Firstly, you should make sure you have wvdial installed, it is in the repositories, you can either open synaptic package manager and look for it there.[U][COLOR="Red"]

Main menu >System >Administration >Synaptic Package Manager[/COLOR][/U]

 or open a terminal and type

```
sudo apt-get install wvdial
```

Now, with your modem plugged into an available USB port...
(note:: this is more reliable connected directly to your computer as opposed to a hub, and also, some users report problems with the longer cable, but I have had no such problems on the 5 I have set up personally.)

```
sudo wvdialconf
```

What this does is reads all of the settings you will need directly from your modem and writes them to a file called wvdial.conf. Without sudo it will read from the modem but cannot write the file.

IMPORTANT!! You should NOT edit any of the completed lines in wvdial.conf, the settings that the above command wrote to that file are unique to your modem/service provider, so copying anyone elses from a thread will only prevent yours from functioning. However you will need to edit 3 lines of text: Phone, Username and Password.

Again, in a terminal type...
```
sudo gedit /etc/wvdial
```

This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone
; Password
; Username
```

As you can see, Phone, Password and Username are not designated and are also preceded by a ; followed by a space. First of all delete the ;'s and spaces so that P,P and U respectively are the first characters on their lines. now following the same format as the completed fields add ( = )to each line and give them a value, so you should have something that looks like this.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = Anything
Username = Anything
```

Before you save the file and exit, make a note of the second word in the first line, in the case of my example (Defaults) This is the name of the profile you will need to invoke for a connection.

How you wish to connect now is a matter of preference, I will now explain your options and try to outline the pro's and cons of each.

Firstly, If you feel happy having a connection with no GUI, no taskbar applet or any visual feedback on your desktop, then it's very easy.

Press _[COLOR="Red"]Alt-F2[/COLOR]_ and type 

```
wvdial Defaults
```

Or replace the word Defaults with whatever was in the first line of your wvdial.conf.

If you wish for your modem to connect automatically at log on, take your mouse to the the panel menu and navigate >System >Preferences >Sessions and under the "Startup Programs" Tab, click the "Add" button and where it says "Command" Type:

```
wvdial Defaults
```

Be sure also to fill in the "Name" box, but what you type in there is up to you, simply "Modem" or "E220" is ideal for your own future reference.





Now you may prefer a graphical user interface to get connected, if so you have a few choices.

If you use gnome then i recommend *[COLOR="Lime"]gnome-ppp[/COLOR]*

```
sudo apt-get install gnome-ppp
```

for kde, *[COLOR="Lime"]kppp[/COLOR]*

```
sudo apt-get install kppp
```

Another one some people are using is vodafone-mobile-connect-card-driver-for-linux, (what a mouthful) but you will not find this in the repositories and it is quite a bulky program (like it's name) that requires rather a lot of python dependencies. It does have some extra functions but I am yet to see any of them work, although to be fair I have not tried it with a vodafone sim, but it will still connect you nonetheless.

Whichever utility you choose the following instructions are the same.

If you closed your text editor after saving wvdial.conf then type:

```
gedit /etc/wvdial.conf
```

To bring it back up. Notice there was no sudo this time? Don't worry, Admin privaleges aren't necessary as we won't be editing the file, we just need that information at hand.

All that needs to be done is to complete any fields in your ppp's GUI's settings, using wvdial.conf as reference.

[COLOR="Blue"][B]Some points of possible confusion explained.
[/B][/COLOR]
*[COLOR="RoyalBlue"]What's an init string??[/COLOR]*

see the line in wvdial conf that looks something like  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK, well that's what you need to put in the init string box.

*[COLOR="RoyalBlue"]What's the phone number??[/COLOR]*

My connection is with 3uk, so the number I set mine to dial is *99#
If you have another provider it will no doubt be different, but google should be able to answer that, or contact your provider.

That's it, click connect you should be up and running. try opening up your browser and searching, if all is well, happy browsing. Perhaps you get a message saying "Offline Mode" This is just Firefox thinking it knows best, simply click on the browsers "File" in the tool bar and de-select "Work offline"

*[COLOR="RoyalBlue"]Still no connection???[/COLOR]*

If you're using a GUI to connect, there may be a function called "Stupid Mode" selecting this "apparently" forces your modem to ignore init strings,and will usually sort this problem, but at this point I am unable to explain why and I'm only just scratching at what an init string does myself so I'll avoid any further details here to avoid confusion or giving misleading info. I may edit this at a later date if I consider it appropriate

If your GUI doesn't have this option, or you have opted for my no-GUI approach, then you can go back to....

```
sudo gedit /etc/wvdial.conf
```

And add the line...

```
Stupid mode = 1
```

Now I hope you are connected.

As I mentioned at the beginning, I am no expert, I am just relaying my experience of setting up 5 such modems, perhaps this HOWTO doesn't work for you, if so leave a message, I'm quite sure I've read just about everything on the net about setting it up under linux, so if you have a problem, I've probably heard it before, and will probably know where to look.

One final note, If you have used this HOWTO and are still having problems, please let me know. Maybe you think I could have been clearer about something. In any case all feedback will be welcomed and appreciated. If you have got it working, which I sincerely hope you have, please leave a message saying which type of setup you opted for, which GUI, or no GUI, this could prove helpful to others in the future.

Just as I hope you have found this helpful.

These instructions worked PERFECTLY... however, the Network Monitor applet doesn't list the 3G connection and this sucks... as driver support for the E220 is built into the kernel shouldn't this whole process be a bit more "plug and play"?

At any rate, these instructions got it working... it ain't pretty but it works. 

FYI, I am using an IBM ThinkPad X24 with Ubuntu Hardy Heron 8.04 in the Republic of Ireland and Vodafone is the I.S.P.

---

### Post by mundo on 2008-08-14
> **chmac said:**
> My experience with mobile broadband on Ubuntu, after upgrading to NM 0.7, has been painless.

My experience has also been painless up to now but I ran the update manager last night and now I can't connect my USB modem.  Has anyone else experienced this?

---

### Post by chmac on 2008-08-14
> **mundo said:**
> My experience has also been painless up to now but I ran the update manager last night and now I can't connect my USB modem.  Has anyone else experienced this?

Can you confirm which version you've upgraded to?

What happens when you connect the USB modem? Can you dial out via GnomePPP?

Edit: I'm using NetworkManager version 0.7.0~svn3758-PPA4 (according to synaptic) and it's working great for me.

---

### Post by mundo on 2008-08-15
Not great for debugging this problem but I upgraded to an Alpha Version Ubuntu 8.10 Intrepid Ibex just for the sheer hell of it to see if this fixed it. However, I now cannot access Wifi or Mobile Boradband.

The version of Network Manager that I am using is 0.7~~svn20080807t145225+eni0-0ubuntu1~nm1~hardy1

---

### Post by chmac on 2008-08-15
> **mundo said:**
> Not great for debugging this problem but I upgraded to an Alpha Version Ubuntu 8.10 Intrepid Ibex just for the sheer hell of it to see if this fixed it. However, I now cannot access Wifi or Mobile Boradband.

The version of Network Manager that I am using is 0.7~~svn20080807t145225+eni0-0ubuntu1~nm1~hardy1

Can you give us a bit more information about what's not working, or any error messages you're receiving?

---

### Post by mundo on 2008-08-15
It just attempts to connect and the network manager icon spins round in the top right hand corner of the screen for about a minute then it says "Disconnected: The network connection has been disconnected".

Where can I find the log files so that I can get more information on the problem?

---

### Post by chmac on 2008-08-15
> **mundo said:**
> Where can I find the log files so that I can get more information on the problem?

Check out syslog. You can do that in System > Administration > System Logs. Look in the syslog and messages logs. Or from a terminal you can `tail -f /var/log/messages` or `tail -f /var/log/syslog` to watch the log live while you try NetworkManager.

---

### Post by mundo on 2008-08-15
Hmm, seems to be 'Activation failed for access point' after 'DHCP transaction took too long'.

Related posts: 
[http://ubuntuforums.org/showthread.php?t=674178](http://ubuntuforums.org/showthread.php?t=674178)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251")

---

### Post by chmac on 2008-08-15
> **mundo said:**
> Hmm, seems to be 'Activation failed for access point' after 'DHCP transaction took too long'.

I don't know if it will help, but I've had similar problems in the past. I was able to get networking to work by connecting with NetworkManager, waiting until it had connected ok, then killing it. It's messy, but it got me on to a WPA connection which was causing me problems. If you're having the problem described in your first link, it might help. Otherwise, I'd suggest starting a new thread as this seems like an issue with NetworkManager 0.7 on Ubuntu 8.10 alpha.

---

### Post by mundo on 2008-08-15
My issue is that it doesn't even connect at all so I can't try your method.  Like I said in an earlier post it was all working like a dream on 8.04 until I ran system update so some related update must have inteferred with it.

I think I will reinstall 8.04 and NM 0.7 then keep an eye on the updates and see if this happens again. Thanks for your quick responses to my posts, much appreciated. At least we will have NM 0.7 officially in the release for October which should mean that these issues will be resolved and it will "just work" which is what we all want!

---

### Post by chmac on 2008-08-15
> **mundo said:**
> My issue is that it doesn't even connect at all so I can't try your method.  Like I said in an earlier post it was all working like a dream on 8.04 until I ran system update so some related update must have inteferred with it.

Ah, ok. I misunderstood from the discussion on the other thread. Are you trying to connect wireless or mobile broadband?

If mobile broadband, try GnomePPP instead. NetworkManager just dials the connection, the kernel should take care of all the hardware stuff. You need to add some custom init strings (there are instructions on this thread somewhere I think).

If it's wireless that's not working, you could try the network configuration tool, but it doesn't support WPA (I think).

You can disable NetworkManager with the command `sudo /etc/init.d/network-manager stop`.

> **mundo said:**
> I think I will reinstall 8.04 and NM 0.7 then keep an eye on the updates and see if this happens again. Thanks for your quick responses to my posts, much appreciated. At least we will have NM 0.7 officially in the release for October which should mean that these issues will be resolved and it will "just work" which is what we all want!

My system is 8.04, fully updated, and it's working for me. Not sure which update might have borked NM for you. Hopefully you can either get it working in 8.10, or it "just works" if you re-install 8.04. :)

---

### Post by DodoBandit on 2008-08-15
Hi, 

Has anyone managed to get the E220 working on an Elonex One yet? I can't even find the flippin terminal!!

I think they've only been out since Weds

Rgds/Pete

---

### Post by mundo on 2008-08-16
Here's a question, if I have uninstalled Network Manager completely then how can I reinstall it if I can no longer connect to the internet from that pc?

---

### Post by chmac on 2008-08-18
> **mundo said:**
> Here's a question, if I have uninstalled Network Manager completely then how can I reinstall it if I can no longer connect to the internet from that pc?

An excellent point! I haven't personally uninstalled NetworkManager so I haven't had this issue. You can download the .deb files though. However, to do that you would need to have them saved in advance.

If you have problems with NetworkManager I'd suggest disabling it (`sudo /etc/init.d/network-manager stop`) and then configuring the network manually. That can be a pain for wireless networks, but for wired networks it's fairly painless. System > Administration > Network should be sufficient for most wired networks. Then if you can plug in, you could un/reinstall NetworkManager.

---

### Post by mundo on 2008-08-18
I decided to bite the bullet on this one and reinstall Hardy which means that I am back to normal and able to connect with WPA wireless and Mobile broadband.  It was only a test PC as I am still experimenting with Ubuntu so it wasn't much effort.

---

### Post by nurburgracer on 2008-08-19
This How To Guide really helped me. I was struggling for at least a week to try and get my internet connection going. After installing ubuntu I needed to update, but with no internet connection it was a classic catch22. Fortunately a friend of mine let me download the updates then the How To Guide worked. I prefer using wvdial without the GUI without stupid mode. I have set up the GUI with GnomePPP and is working fine. I initially tried to use the Vodafone-mobile-connect-for-linux program. It was so tempremental. Thanks again for a great guide.

---

### Post by Death-inc on 2008-08-22
Hi there Fingers & Thumbs I am a noob when it comes to Ubuntu. I loaded it on to my machien about three days ago and had a problem with the e-220 Modem. Then i found this page after searching on google for hours. I followed it to the T and it work. I just have add that I have a vodaphone contract from South Africa name Vodacom and the number that we use to dail in is *99***16#. Thanks for the "How To Manual" it really came in handy.

---

### Post by mundo on 2008-08-23
Does anyone know how to stop the "Vodafone MC Installer" icon from appearing on the Desktop everytime you plug in the USB modem?

---

### Post by Sleepy-zz-John on 2008-08-23
Hi,  I'm very happy because I've just managed to get myself on-line with my E220 on the UK Three network, and I used the command "wvdial three" to activate it.

But now, since no network connection is displayed when I'm online,   how do I close the internet connection when I've finished?    I'm looking for a more elegant solution than simply unplugging the dongle or closing Ubuntu.:)

---

### Post by Sleepy-zz-John on 2008-08-24
> **Sleepy-zz-John said:**
> Hi,  I'm very happy because I've just managed to get myself on-line with my E220 on the UK Three network, and I used the command "wvdial three" to activate it.

But now, since no network connection is displayed when I'm online,   how do I close the internet connection when I've finished?    I'm looking for a more elegant solution than simply unplugging the dongle or closing Ubuntu.:)

OK - found the answer myself now.   Just had to type Ctrl C into the terminal window showing the wvdial sequence and the connection closed elegantly.

Moving on,  my next question is how can I see my session data usage?  Of course UK Three cap my monthly data usage, so I need to keep track of what I use on Ubuntu and add it to what Three's Win XP dialler shows me I've used.

---

### Post by chmac on 2008-08-25
> **Sleepy-zz-John said:**
> Moving on,  my next question is how can I see my session data usage?  Of course UK Three cap my monthly data usage, so I need to keep track of what I use on Ubuntu and add it to what Three's Win XP dialler shows me I've used.

I recommend installing vnstat. It's the simplest method I've found.
`sudo apt-get install vnstat`

Then you need to create a database for ppp0 which is done with:
`sudo vnstat -u -i ppp0`

Then when you want to check usage, in a terminal, type `vnstat` and `man vnstat` for more options.

You can also open System Monitor (System > Administration), which has some information about network usage, but it's not very detailed and doesn't keep a log. Vnstat is the way to go.

---

### Post by Sleepy-zz-John on 2008-08-25
> **chmac said:**
> I recommend installing vnstat. It's the simplest method I've found.
`sudo apt-get install vnstat`

Then you need to create a database for ppp0 which is done with:
`sudo vnstat -u -i ppp0`

Then when you want to check usage, in a terminal, type `vnstat` and `man vnstat` for more options.

You can also open System Monitor (System > Administration), which has some information about network usage, but it's not very detailed and doesn't keep a log. Vnstat is the way to go.

Good Answer!  Many thanks for that.    vnstat installed easily and looks to be doing the job fine.

Moving on a bit further now,  I still have to keep reverting to Win XP to check my local mobile signal strength from the Three network.   I'm rather far from their nearest cell transmitter and have to hang my E220 up in one of the windows on a USB extension cable for best results. The Windows s/w that comes from Three displays up to 5 bars to show the strength of the 3G or HSDPA signal.   Just wondering if there's any way I can see my signal strength in Ubuntu.

---

### Post by chmac on 2008-08-25
> **Sleepy-zz-John said:**
> Just wondering if there's any way I can see my signal strength in Ubuntu.

I think the vodafone app will do that. Otherwise you could try UMTSMON. It's a single binary you download (you can put it in ~/bin). It seemed to work ok for me, although it wouldn't connect. I don't use it now as I generally get pretty good coverage. Let us know if it works though. :)

---

### Post by lancs_atul on 2008-08-26
Hi,
Pls excuse my ignorance - I'm new to ubuntu..all help greatly appreciated!!
I have a dual boot laptop, Vista and Ubuntu.
My 3G Huawei E220 works fine in Vista but get the following errors in Ubuntu - 

sudo wvdialconf  /etc/wvdial.conf

This are the screen results: 
Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

I've read the thread about using Network-Manager 0.7
I don't have internet connection on Ubuntu courtesey the errors above .
Through Vista I've been to the website to download Network-Manager 0.7:
[http://ppa.launchpad.net/network-manager/ubuntu/pool/main/n/network-manager/](http://ppa.launchpad.net/network-manager/ubuntu/pool/main/n/network-manager/)
But I don't know what to download(packages) and how to install it in Ubuntu - Again pls pardon my ignorance

Please help!!
Thanks

---

### Post by IanB2 on 2008-08-27
I too am having problems getting a 3G T Mobile web'n'walk stick III working.

If I use the first installation method I too get:

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.


So I tried the second installation method, and installed the latest version of network manager (on two different laptops). The installations are both working fine however when I plug in the usb stick, nothing seems to happen. I've created an new 3g connection manually (although I'm not too sure of the T-Mobile settings) but the network manager applet does not give me the option of selecting 3g, just my wired network.

It appears that the software is simply not picking up the 3g usb card???

Any ideas??

---

### Post by chmac on 2008-08-27
> **IanB2 said:**
> So I tried the second installation method, and installed the latest version of network manager (on two different laptops). The installations are both working fine however when I plug in the usb stick, nothing seems to happen. I've created an new 3g connection manually (although I'm not too sure of the T-Mobile settings) but the network manager applet does not give me the option of selecting 3g, just my wired network.

It appears that the software is simply not picking up the 3g usb card???

Any ideas??

It appears that your modem is not being correctly detected by the kernel. If you read back on this thread, there are probably debugging steps suggested somewhere. Try looking at `dmesg | tail` or `dmesg | less`. You're looking for something that indicates the modem being plugged in. I'm not an expert on that, but somebody else might have more useful advice. :)

---

### Post by IanB2 on 2008-08-28
> **chmac said:**
> It appears that your modem is not being correctly detected by the kernel. If you read back on this thread, there are probably debugging steps suggested somewhere. Try looking at `dmesg | tail` or `dmesg | less`. You're looking for something that indicates the modem being plugged in. I'm not an expert on that, but somebody else might have more useful advice. :)

Thanks ..... I MAY have a faulty usb stick .... need to investigate further. Cheers!

---

### Post by chmac on 2008-08-28
> **IanB2 said:**
> Thanks ..... I MAY have a faulty usb stick .... need to investigate further. Cheers!

Do you get any lights on the modem? Have you been able to try it on another machine? In Ubuntu the modem will be recognised right away, no installation of software required, it will "just work", so if you have another Ubuntu install, you could easily test it.

---

### Post by IanB2 on 2008-08-28
> **chmac said:**
> Do you get any lights on the modem? Have you been able to try it on another machine? In Ubuntu the modem will be recognised right away, no installation of software required, it will "just work", so if you have another Ubuntu install, you could easily test it.

Thanks for your help .... I've installed a fresh copy of xubuntu on another old desktop and followed your instruction to update the network manager ..... this time it worked!! Awesome!

It was probably the usb port on my old laptop that was causing the problem.

I'm looking forward to the release of Intrepid.

---

### Post by CypherHackz on 2008-08-31
Thanks for the reply. I can connect to my 3G broadband using wvdial. But the problem is, my connection disconnect automatically after 30 seconds or so when I am idle. Is there has any way to change it?

-cypher.

---

### Post by mundo on 2008-09-03
> **mundo said:**
> Does anyone know how to stop the "Vodafone MC Installer" icon from appearing on the Desktop everytime you plug in the USB modem?

Has anyone had any thoughts on this?  I remember seeing a post on this but I have searched for ages and can't find it now.

---

### Post by chmac on 2008-09-03
> **mundo said:**
> Does anyone know how to stop the "Vodafone MC Installer" icon from appearing on the Desktop everytime you plug in the USB modem?

I installed and un-installed the vodafone software and I don't remember a desktop icon. I don't have one now anyway. I haven't done anything specific to remove it though. Does the icon appear when the modem is plugged in? Have you removed the vodafone software?

---

### Post by mundo on 2008-09-03
Yes, the icon appears when the modem is plugged in and a folder window appears with the file contents, setup.exe, autorun.inf and helper.exe. I have to then close this folder window which is just a minor annoyance that I'd like to fix.

Since a fresh install of Ubuntu I have not installed the Vodafone software .

---

### Post by dmaskal on 2008-09-03
Thanks for you detailed and educational explanation. I now can dial out.
However I still have trouble with log in -detail below. I would apreciate you help.

One odd thing I noticed is the "result" does not show the complete 'username'. Not sure if this is normal security masking or the fact that the username (dmaskal@toast.net) includes @toast.net


Modem=US Robotics 5637
Laptop=Evo N610c / Ubunto 8.04 (dual boot/Windows XP Home Edition)

Wvdial.conf:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 5600
Stupid mode = 1
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = 5800082
Username = <username>
Password = <password>

Result:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT8509615
--> Waiting for carrier.
ATDT8509615
CONNECT 26400/ARQ/V34/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
UQKT2 *** Welcome to oak2-dial2.popsite.net ***
Login: 
--> Looks like a login prompt.
--> Sending: dmaskal
dmaskal
Password: 
--> Looks like a password prompt.
--> Sending: (password)
** Bad Password
Login: 
--> Looks like a login prompt.
--> Sending: dmaskal
dmaskal
Password: 
--> Looks like a password prompt.
--> Sending: (password)
** Bad Password
Login: 
--> Looks like a login prompt.
--> Sending: dmaskal
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Sep  2 15:19:59 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 7680
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08][08]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08][08]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08][08]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08][08]&#65533;[06][08]
--> Disconnecting at Tue Sep  2 15:20:03 2008
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by chmac on 2008-09-03
> **mundo said:**
> Yes, the icon appears when the modem is plugged in and a folder window appears with the file contents, setup.exe, autorun.inf and helper.exe. I have to then close this folder window which is just a minor annoyance that I'd like to fix.

Since a fresh install of Ubuntu I have not installed the Vodafone software .

Ok, I understand. The modem presents two devices to the computer. One is a flash drive, regular USB memory, which contains the Windows drivers for the modem itself. On a Windows machine, you plug in the device, that memory is auto-run, the driver installs, then the modem switches over and only shows the "modem" device to the computer. It's a nice idea.

It seems like you're seeing the memory and the modem at the same time. In some ways, handy, you could probably dump stuff on that memory and use it on other machines. :)

As for how to disable it, there are codes to switch usb devices. I remember seeing something about it. Try searching for huawei device codes, usb codes, change codes, stuff like that.

---

### Post by mundo on 2008-09-04
Thanks Chmac.  I've got the E172 so this comes with a Micro SD slot.  I haven't used this yet so I think I'll get a Micro SD card then play around with the options that you have suggested and make sure that I can still use the modem and the memory.

---

### Post by chmac on 2008-09-04
> **mundo said:**
> Thanks Chmac.  I've got the E172 so this comes with a Micro SD slot.  I haven't used this yet so I think I'll get a Micro SD card then play around with the options that you have suggested and make sure that I can still use the modem and the memory.

That modem will be a little different. I guess it'll present three devices to the computer. One usb flash drive for drivers, one for the card reader, and the modem. But that's purely speculation on my part. Anyway, what you described is a usb memory device being plugged into the system, so it would appear that the E172 is presenting a memory device. You should be able to use it without any damage or interruption to the modem.

---

### Post by alarichall on 2008-09-04
Hello there. I got an E172 today, with Vodafone in the UK; I'm aware that this thread is about the E220, but you seem like kind and helpful people, so I thought I'd see if you can help me! I'm using Hardy Heron 8.04.

I'm very ignorant about Ubuntu, and I'm stuck :-( I followed the instructions at [http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059) to install NetworkManager. After doing that, my modem flashes blue or green (it varies), and when I go to the network icon on the panel, 'auto GSM network connection' is available to select. But if I select it, I see the little grey circles and the swirly blue thing going round them; the grey lights go green; and then I instantly get a little box saying 'The network connection has been disconnected' (or the computer automatically connects to a wireless network instead, if there's one available).

Incase it's helpful to add, when I type 'sudo wvdialconf' I get:

[INDENT]alarichall@Branwen:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyUSB0<Info>: Device or resource busy
Modem Port Scan<*1>: USB0 
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

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
[/INDENT]

And when I type 'sudo gedit /etc/wvdial.conf', having added my username, the phone number and a password, I get:

[INDENT][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB1
Username = alarichall
Password = somethingsecret
Baud = 9600[/INDENT]

If I type Alt-F2 and type 'wvdial Defaults' nothing visible happens.

If I install gnome-ppp and run it, I get a box with the same username and phone number as the wvdial.conf file; if I put in my password and click 'connect', I get a box saying 'can not open modem' and when I click 'log' it says:

[INDENT]--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory[/INDENT]

I tried adding 'Stupid mode = 1' to the wvdial.conf file, but it didn't make any difference.

Any help would be greatly appreciated!

Thanks!

---

### Post by alarichall on 2008-09-04
Oh wow, I've made it work! (For now.) I figured I should post what I did:

alarichall@Branwen:~$ sudo wvdialconf /etc/wvdial.conf
[sudo] password for alarichall: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
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
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
alarichall@Branwen:~$ 

[this is what you'd expect from [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220) except for the +FCLASS=0 at the end]

alarichall@Branwen:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer hsdpa] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
alarichall@Branwen:~$ 

[this is presumably not what's expected to happen! Looks at this stage like something's wrong in the /etc/wvdial.conf]

alarichall@Branwen:~$ gksudo gedit /etc/wvdial.conf

[this gives


[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttyUSB0
Baud = 9600

which is clearly no good. Changed to:


[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = vodafone
Init1 = ATZ
Password = vodafone
Modem = /dev/ttyUSB0
Baud = 9600]

]

alarichall@Branwen:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer hsdpa] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Sep  4 21:18:39 2008
--> Pid of pppd: 6544
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Using interface ppp0
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Disconnecting at Thu Sep  4 21:18:41 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Sep  4 21:19:16 2008
--> Pid of pppd: 6716
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Using interface ppp0
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Disconnecting at Thu Sep  4 21:19:17 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Sep  4 21:19:57 2008
--> Pid of pppd: 6754
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Using interface ppp0
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> pppd: h&#65533;[06][08]X&#65533;[06][08]
--> Disconnecting at Thu Sep  4 21:19:58 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 20 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Sep  4 21:20:27 2008
alarichall@Branwen:~$ 

[in the end I put it out of its misery with ctrl+c as per [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220]](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220])

[doesn't work with wvdial Default either. I try replacing the wvdial.conf with

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
Carrier Check = no
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = web
Username = web

which I got from [http://www.techyforums.com/index.php?showtopic=257&pid=272&st=0&#entry272](http://www.techyforums.com/index.php?showtopic=257&pid=272&st=0&#entry272). Oh wow!:]

alarichall@Branwen:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer hsdpa] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Sep  4 21:42:23 2008
--> Pid of pppd: 8228
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> Using interface ppp0
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 10.49.11.211
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 10.203.65.68
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 10.203.65.68
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]
--> Script /etc/ppp/ip-up run successful
--> Default route Ok.
--> Nameserver (DNS) Ok.
--> Connected... Press Ctrl-C to disconnect
--> pppd: X&#65533;[06][08](&#65533;[06][08]&#65533;&#65533;[06][08]

[I've got a steady blue light now! And, yes, it even works!]

---

### Post by chmac on 2008-09-04
> **alarichall said:**
> [I've got a steady blue light now! And, yes, it even works!]

Congrats! :)

If you want to pursue the NetworkManager route, try editing your settings. So right click on the icon, go to Edit Connections > Mobile Broadband then double click the connection. The enter "internet" in APN and web / web in username / password. Plus *99# in number. You might find it works that way.

If not, you'll get more info from System > Administration > System Log. Look in messages.

---

### Post by cooke77 on 2008-09-07
Oceanpinl, if your modem comes supplied with a LAN Cable (and the computer/modem has the required Port).....you can 'opt' to use the LAN Cable 'set-up'.
It is the 'preferred' method.....of running either an ADSL modem, OR, a Cable Broadband Modem.
I, myself, run a ADSL modem (under XP Pro)...using the ascribed 'above' method.
Works perfectly, did not have to 'conigure' a thing....in Kubuntu 8.04. (Other than to use my 'personal details', given to me by my ISP Provider/RE:..Username-E-mail Address/Password.)
I used to run Broadband (Cable)....until I had to move house. (Same deal applied....with that, too, using the LAN 'method'. No problems there, either.)

In Kubuntu, there's no need (like there is in XP Pro)to 'Install' the LAN driver...to kick-start' your Modem/LAN 'set-up'..at all. (Unless you possess a modem that Linux doesn't know of, or has NO LAN socket....which most do have.)
For me, mine just fired up. Straight-away. 
(The 'funny thing' is, that my ISP Provider does not 'support' Linux...in any 'flavor', yet, I was able to 'connect to the Internet', instantly!, regardless of that fact.)

The thing I do find most common...with computer owners/users....is that they are too impatient...to get their computer 'on-line'...let alone, to be working with no 'input' from themselves, that they always 'ignore' the obvious.

Which is, to spend some time 'learning' how their computer does work....before they start configuring. (By this, I do mean playing with it, opening things up...to see what's there...to do some solid reading, to understand/comprehend 'what' they are reading....or wanting to do 'next'.)
No, they just want their working, and, jump straight in, to mess everything up...without really knowing exactly what it is they doing to their computer...then, cry 'foul'...when it suddenly STOPS working.

You need Patience( most people don't have it)....., also, Knowledge, because Knowledge begets Experience.
In other words,...use the old adage of 'You have to learn to crawl, before you can walk..and, you have to learn to walk, before you can run.'

---

### Post by chmac on 2008-09-07
cooke77, this thread is about the Huawei E220, which is a USB 3g mobile broadband modem. There is no ethernet port, nor a similar device with an ethernet port. There's no talk of ADSL or cable modems.

---

### Post by MrPilgrim on 2008-09-17
Hi,
I seem to have got things working with my "3" mobile broadband e220 modem on my new eeePC 1000h running 8.0.4.1.  Thanks to this thread I have installed the new NM (0.7) and all seems to have (finally) been sorted.

However, sometimes if I have connected successfully and then disconnect using NM and then try to re-connect, NM reports I have successfully connected but I am unable to contact any internet address. The route appears to be fine but I can't access any sites in FF and using nslookup I cannot resolve any addresses.

If I reboot my machine and try again all seems to work again. Has anyone seen this problem or have any thoughts on what might be happening ?

Thanks
Simon

---

### Post by chmac on 2008-09-17
> **MrPilgrim said:**
> The route appears to be fine but I can't access any sites in FF and using nslookup I cannot resolve any addresses.

I've experienced a similar issue with Three in Australia. I get connected, but no nameservers are set. So `cat /etc/resolv.conf` returns two 10.x ip addresses. If I disconnect / reconnect, it sometimes works. Or, I have the nameservers saved in /etc/resolv.conf.three, so I use `sudo cp /etc/resolv.conf.three /etc/resolv.conf` and it works.

If you want more details on any of that, just let me know. Hope it helps.

---

### Post by Turev on 2008-09-18
So far so good but one thing I dont understand, we are trying to configure a modem to connect internet, we use apt-get to download something from internet. How are we supposed to download anything if we do not have internet connection? :-) (Or may be I dont know something since I am not that advanced user) Anyway, since when I issue the command "sudo apt-get install gnome-ppp" I get an error message as "E: Couldn't find package gnome-ppp" I presume this happens due to no internet connection. So the question is, how can I get gnome-ppp and install it on my computer ?

ThanX

Gokhan

---

### Post by chmac on 2008-09-18
> **Turev said:**
> So the question is, how can I get gnome-ppp and install it on my computer ?

You're right, you do need to download it from the internet. Can you connect by any other means as a temporary solution? For example, can you take your computer somewhere and plug it in with a network cable? Not so easy if you have a desktop!

You can find [gnome-ppp on the Ubuntu package site here]("http://packages.ubuntu.com/hardy/i386/net/gnome-ppp"). You should be able to download the packages by hand, save them to some sort of removable memory, and then load them onto your computer. Once you have them on your machine, you install them with:
`sudo dpkg -i blah.deb`

---

### Post by Turev on 2008-09-18
Perfect! I installed ppp successfully- that part is over... Still trying to get the modem work though...

---

### Post by chmac on 2008-09-18
> **Turev said:**
> Perfect! I installed ppp successfully- that part is over... Still trying to get the modem work though...

If you have any specific questions, fire back. If you can, I'd recommend [upgrading to NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059"). I'm not sure how you'd do that without internet, it is possible, but it might be a hassle.

---

### Post by Turev on 2008-09-19
OK here is the fireback. The modem I am using is not really e220, it is e169g (as written on modem). The funny thing is when I pressed the detect button on SETUP/modem page, it detected the device and when I pressed the connect button it got stuck giving a message "sending password" - later it could not detect the modem, and detected again etc. Now today it can not detect again.

Let me try updating the network manager...

---

### Post by Turev on 2008-09-19
Somewhat, I found an internet port with ethernet connection and made updates however nothing different happened so I focused on wvdial thing again. Here is what happens after executing wvdial command:
- Initializin modem.
- Sending: ATZ
ATZ
OK
- Sending: ATZ
ATZ
OK
- Sending ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
- Modem initialized
- Sending: *99#
- Waiting for carrier.
[actually it waits at this line for a while]
- Timed out while dialing. Trying again.
- Maximum Attepmts Exceeded..Aborting!!
- Disconnecting at ...

do you think this might happen due to weak GSM signals or is there some other problem?

Gokhan

---

### Post by chmac on 2008-09-19
> **Turev said:**
> do you think this might happen due to weak GSM signals or is there some other problem?

At first glance, I'd guess that it's because you're not sending the right initialisation strings. Check back through the thread, there are init strings listed somewhere which you can put into Gnome-PPP. One of them includes the APN which will be unique to your mobile provider.

---

### Post by ninocass on 2008-09-21
excellent guide many thanks!

I can get the 3G modem working with the steady blue LED and external IP issued.

The one snag ive hit is that the internet doesnt work, i think its a routing issue as when i take the 3G interface down and connect to my wifi i still dont get anything.

could anyone give some advice.

Many Thanks

---

### Post by chmac on 2008-09-21
> **ninocass said:**
> could anyone give some advice.

I'd suggest starting a new thread. This thread is already at 9 pages, so probably best not to diverge on a different problem too far. If you send me the link I'll be happy to chime in on the new thread, although I can't guarantee I'll be able to solve your problem! :)

---

### Post by minerbog on 2008-09-23
Hi everyone :). I've looked over all the posts in this thread and tried everything I can think of but cannot get my modem working.  I'm going with the script process because I cannot get a net connection to download NM0.7!! Anyway I really need to get this working because at the moment the mobile internet is the only argument my wife has for keeping, dare I say it, vista! Makes me shiver just saying it!! Below is the terminal message I got from using the original process in this thread.  Any help would be greatly appricated. I really don't want to pay any more to the robbing g*t gates!

gavin@gavin-desktop:~$ wvdial defaults
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Sep 22 17:14:21 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 7922
--> Using interface ppp0
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> local  IP address 92.40.133.132
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> remote IP address 10.64.64.64
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> primary   DNS address 4.2.2.4
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> secondary DNS address 4.2.2.3
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> Connect time 2.3 minutes.
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: Xï¿½[06][08]ï¿½ï¿½[06][08]
--> Disconnecting at Mon Sep 22 17:16:42 2008
gavin@gavin-desktop:~$ 

It seems to hang at the point 'Caught signal 2:' and I just crtl+c it out.

Please help.  Many Thanks.

---

### Post by chmac on 2008-09-23
minerbog, I'd suggest downlodaing Gnome-PPP and using that. If you add the right init strings, it should "just work" in my experience. :)

You can probably download it under Windows then install it with `dpkg -i blah.deb` on Ubuntu.

---

### Post by minerbog on 2008-09-23
Gnome-PPP is a cool little prog, but unfortunatly still no luck. Gnome does say how ever it is connected, but firefox doesn't work and the only IP i can ping is my own?

Again here is the log that gnome produced:

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Sep 23 16:36:37 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8328
--> Using interface ppp0
--> local  IP address 92.40.82.190
--> remote IP address 10.64.64.64
--> primary   DNS address 10.11.12.13
--> secondary DNS address 10.11.12.14

The Init strings I got from another thread are for my provider 3, but as I said I get a connected answer from gnome but nothing downloads.

Another thing I noticed is the remote IP's and DNS addresses. Is it coincidence that they run in order or its it a default linux address if it can't find the real one??

Any help would be great.

Thanks.

---

### Post by chmac on 2008-09-23
> **minerbog said:**
> Another thing I noticed is the remote IP's and DNS addresses. Is it coincidence that they run in order or its it a default linux address if it can't find the real one??

Yes, those IPs are nonsense. The default gateway doesn't matter so much if you have an internet IP. But the DNS servers will mean you can't resolve any names. Try pinging an IP directly like this:
```
`ping -c4 208.67.222.222`
```

Does that work?

Try editing /etc/resolv.conf and setting the OpenDNS servers manually like this:
```
`sudo gedit /etc/resolv.conf`
```

Then replace the two "nameserver" lines with:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Then see if you can resolve names. Use the command:
```
`getent hosts www.opendns.com`
```

If it returns nothing, no DNS response. Otherwise, if it returns an IP, you're getting names resolved.

Let us know how you get on with that... :)

---

### Post by minerbog on 2008-09-25
> **chmac said:**
> Yes, those IPs are nonsense. The default gateway doesn't matter so much if you have an internet IP. But the DNS servers will mean you can't resolve any names. Try pinging an IP directly like this:
```
`ping -c4 208.67.222.222`
```

Does that work?

No, still the only IP address I can ping is my own :(

> **chmac said:**
> Then see if you can resolve names. Use the command:
```
`getent hosts www.opendns.com`
```

If it returns nothing, no DNS response. Otherwise, if it returns an IP, you're getting names resolved.


Still nothing. It seems to be there is now DNS response whatever I do. Although, my IP is set to dynamic and I an getting a new IP address when it does connect so I assume I am getting a connection, but their not allowing me internet access!

I'm stumped!!

---

### Post by chmac on 2008-09-25
Gavin, I'm not sure what to suggest. You're getting an IP, but you can't ping anything. Check the manual for the light colours on your modem. Are you getting a 3g available light? On my E220 (from Vodafone in Australia) blue means network available, green means roaming (and big fat charges!). Then it goes flashing when connected, and drops to light blue if it's in 3g range.

Otherwise, I too am stumped. Hopefully somebody else will have some suggestions.

---

### Post by minerbog on 2008-09-25
Newly posted from my Ubuntu system with working modem!!!

Thanks for your help chmac.  The problem I had was actually quite simple. After reading may posts else where, I discovered that my Ethernet port which I had setup and used to update the install was setting the default gateway. Although I had a connection, it was trying to route to 192.168.9.254 because that was the gateway!! DOH!!!

Tip for anyone else setting up one of these, set your Ethernet connection to roaming if it isn't already, otherwise you will be ripping your hair out as much as I have been!!

Many thanks to you all

---

### Post by chmac on 2008-09-25
Hey Gavin,

Glad you got it sorted. I think that addresses one issue. Are you using NetworkManager to manage your ethernet port? If you are, and it's down, it shouldn't be specifying a route. If not, and you're doing something clever with a 3g modem and sharing internet access / whatever, then you will need to do some "magic" to get the routing tables working.

But according to [your post]("http://ubuntuforums.org/showpost.php?p=5841226&postcount=90") you also weren't getting valid dns servers. Has that also resolved itself? Or are you setting your dns servers manually?

I have that problem quite often with 3 in Australia. It connects, gets a valid IP, but no ns servers. I haven't bothered with this connection, but it is possible to "hack" a solution using NetworkManagerDispatcher. A little script to check for the nonsense DNS servers in /etc/resolv.conf, and if found, replace the whole file with a backup copy.

If you've got it working, hopefully you won't have to bother with any of that. :)

---

### Post by minerbog on 2008-09-25
yeah, its working, although gnome-ppp likes to change my resolv.conf file everytime it tries to connect.

Is there anyway to stop gnome doing this?

I'm specifying the dns manually and connecting vis wvdial.  Long winded I know but at least its working!!

---

### Post by chmac on 2008-09-25
You can change that behaviour, try /etc/dhcp3/dhclient.conf. I think you want to remove "domain-name-servers" from the "request" list. There is a way to do that on a per interface basis I think. But remember ppp0 is used for any other dial up connections also.

NetworkManager / NetworkManagerDispatcher and a simple home grown script might actually be easier.

---

### Post by irishwolfhound on 2008-10-06
Thanks a lot for this post, it works for three ireland as well. I used Gnome PPP. You have to turn on stupid mode in the setup/options tab and enter the APN 3ireland.ie in setup/networking. Other then that follow the directions at the top of the page exactly.

Thanks again

---

### Post by Turev on 2008-10-06
Guys

Just to let you know, I solved my problem with the software (actually deb file) given at address:

[http://forum.ubuntuusers.de/topic/o2-surfstick-mit-ubuntu-7.04-7.10-8-04/](http://forum.ubuntuusers.de/topic/o2-surfstick-mit-ubuntu-7.04-7.10-8-04/)

Just scroll down the page and you should be able to find a link for the file: "UMTSmon_0.8_o2.deb (226.6 KiB)"

My modem is e169g (as I stated earlier) and the program supplied in the above link just worked fine for me (did not have to deal with any settings etc...)

Cheers

Gokhan

---

### Post by uppercrustie on 2008-10-28
Right, the HOWTO is very well written and clear. For an ubuntu n00b it was great to have simple explanations about the effect of typed lines in terminal. Finally I start to understand. A couple of notes:

1. at some point during the HOWTO u say

> IMPORTANT!! You should NOT edit any of the completed lines in wvdial.conf, the settings that the above command wrote to that file are unique to your modem/service provider, so copying anyone elses from a thread will only prevent yours from functioning. However you will need to edit 3 lines of text: Phone, Username and Password.

Again, in a terminal type...
Code:

sudo gedit /etc/wvdial

This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:

Code:
[Dialer Defaults]

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone
; Password
; Username

where the terminal line should be

sudo gedit /etc/wvdial.conf

as opposed to

> sudo gedit /etc/wvdial


2. when u say:

> All that needs to be done is to complete any fields in your ppp's GUI's settings, using wvdial.conf as reference.


i was not totally clear about what u meant..

do I have to retype username and password in GNOPE PPP as well as init strings? What about in phone numbers under >setup>modem. Also do I leave the rest of >setup>networking and >setup>options as they are or do i modify/check anything??

I am running a E220 under 3uk and everything worked fine until I tried to connect.

at that point GNOME-PPP stumped to a halt when tryng to send password. Connection Log said:

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Please enter password (or empty password to stop):


then nothing... I tried checking and unchecking a few options but all to no avail.. anybody's got any suggestion?

---

### Post by yadhav on 2008-12-29
Hi, following all these steps and many more, I had been able to connect my Huawei e169G Modem in Ubuntu. I made a blog where all the steps from A to Z have been mentioned. I'm 100 % sure that if you follow it properly, yours will be connected to. Here it is:
[http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/](http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/)

---

### Post by a_salieri on 2008-12-29
Hi you all,

Please please please help me out. Can't find a solution anywhere.

I was using the e220 modem on ubuntu intrepid n it was working ok. Then suddenly it stopped. The modem just blinks blue or green. It works well on windows.

I have two installations of ubuntu 8.10 on my laptop (that's another story), and the modem funny enuf works well on the other installation, so i'm guessing some configuration file got messed up on the first ubuntu installation.

sudo wvdialconf gives me "Sorry, no modem was detected. Is it in use by another program? Did you configure it properly with setserial"

any ideas?

---

### Post by annoe_yk on 2009-01-04
hi everyone, i would like to ask some question regarding this huawei, what should i do if my ISP configuration for username and password is empty? if i'm using wvdial, it's not possible to do so.. how's the trick? anyone please help me
thank you in advance

---

### Post by Junkieman on 2009-01-05
Great tut! But I'm having a problem detecting the modem with wvdialconf. After connecting the modem, it shows the fake CD drive, but I noticed wvdialconf doesn't scan my USB ports, that could be the issue.

I have searched this thread and others, with no luck. Any suggestions would be appreciated :)

```

sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

```

---

### Post by Titomarques on 2009-02-18
hi guys, i have tried all that stuff an my connect box don't work. Maybe it's because i have firmware from Mobile Partner installed??
Any Hint please.

---

### Post by Junkieman on 2009-02-19
Hello! I got my Option 401 working on Intrepid! The reason the modem did not pick up was because the device mounts a virtual CD-ROM drive (ZeroCD), initially I used [usb_modeswitch]("http://www.draisberghof.de/usb_modeswitch/") to toggle the device state so that the system recognizes it as a modem.

I followed [this pharscape article]("http://pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html") which provided me with a more permanent solution, this article applies to various devices so it's worth giving it a go.

---

### Post by popeye on 2009-02-20
Hi, I just got the Huawei E 156 G now since two weeks. It works, but sometimes it takes several times of plugging unplugging to get it going.

Here's my /etc/wvdial.conf for reference

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
;Init3 = AT^SYSCFG=2,2,3FFFFFFF,1,2
;Init5 = AT+CGDCONT=1,"IP","3internet"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = web
Username = web

[Dialer 3g]
Init4 = AT^SYSCFG=14,1,3FFFFFFF,2,4

[Dialer gprs]
Init4 = AT^SYSCFG=13,1,3FFFFFFF,2,4

It sometimes is just not recognized.
As it seems my earlier kernel has not so many problems with it

 uname -r
2.6.24-21-generic

erik

---

### Post by Snort44 on 2009-03-09
> **Fingers & Thumbs said:**
> ***[COLOR="Navy"]Welcome to my first HOWTO.[/COLOR]***


Firstly, you should make sure you have wvdial installed, it is in the repositories, you can either open synaptic package manager and look for it there.[U][COLOR="Red"]

Main menu >System >Administration >Synaptic Package Manager[/COLOR][/U]

 or open a terminal and type

```
sudo apt-get install wvdial
```

Now, with your modem plugged into an available USB port...
(note:: this is more reliable connected directly to your computer as opposed to a hub, and also, some users report problems with the longer cable, but I have had no such problems on the 5 I have set up personally.)

```
sudo wvdialconf
```

What this does is reads all of the settings you will need directly from your modem and writes them to a file called wvdial.conf. Without sudo it will read from the modem but cannot write the file.
... you will need to edit 3 lines of text: Phone, Username and Password.

Again, in a terminal type...
```
sudo gedit /etc/wvdial
```

This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone
; Password
; Username
```

As you can see, Phone, Password and Username are not designated and are also preceded by a ; followed by a space. First of all delete the ;'s and spaces so that P,P and U respectively are the first characters on their lines. now following the same format as the completed fields add ( = )to each line and give them a value, so you should have something that looks like this.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = Anything
Username = Anything
```

Before you save the file and exit, make a note of the second word in the first line, in the case of my example (Defaults) This is the name of the profile you will need to invoke for a connection.


So far, this is working like a charm for me and Kubuntu 8.10 64 bit and a Rosewill 56K / V.92 Hardware-Based Data / Fax Modem.

The small hurdle I'm having to hop now is getting permission to write to my own computer so I can save the file.

Also, in Kubuntu, the text editor is kate.

Thanks very much for posting this tutorial!

---

### Post by MADinMelbourne on 2009-03-24
Hi Fingers and Thumbs... very new to Ubuntu, very keen to get started however having issues with the modem... followed your very clear instructions - THANK YOU - and after wvdial Defaults get

--> carrier detected Starting PPP immediately
--> starting pppd Tues 24 04 09
warning could not modify /etc/ppp/pap-secrets: permission denied
POP (Password authentication Protocol) may be flaky
CHAP (Challenge handshake) may be flaky
Pid of pppd: 6001
using interface ppp0

I copied this on paper, am at an internet cafe until it connects which is making life a little difficult.  Will be in again in 24 hours to check messages.

Oh, and I checked with service provider *99# is correct

---

### Post by d4v1dv00 on 2009-04-11
i am also using intrepid and network manager 0.7 and huawei e220. when i m in the 3G/UTMS/HSDPA coverage, things are just fine as i just need to plugin and network manager will detect and i click connect. everything just works except i can't see the speed and network throughput.

but when i goto places where only have GPRS/GSM then the modem does not work anymore. any ideas?

---

### Post by ashant_c on 2009-05-22
Hello all - thanks for shining light on this.  I'm over in Germany, and just bought myself an HSPDA/UMTM card Huawei E160 from a provider called O2.

It works alright on Win-xp.  But I'm stuck on a no-go on my Kubuntu 9.04 Dell Latitude X300.

Here's my wvdial.conf file:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
stupid mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = o2
Password = GPRS
Baud = 9600
```Couple of things don't make sense above.  Where can I find the Username and Password.  All I needed in win-xp was a 4-digit SIM card password.  But that doesn't seem to be asked above.

Also the highest speed with this service is 3.6Mbps, while the Baud above = 9600kbps.

When I connect using wvdial Defaults, here's the output:

```
ashant@feather:~$ sudo wvdial Defaults
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Fri May 22 13:26:16 2009
```

The intriguing "Invalid dial command" - wish it said more.

The modem is being detected by my laptop though...

```
ashant@feather:~$ sudo wvdialconf
sudo password for ashant:      
Editing `/etc/wvdial.conf'.      

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3
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
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


```Sorry about lots of output, but hope it helps to provide all the data needed.

Can anybody fill in the blanks for me.

TIA

Ashant Chalasani

---

### Post by ashant_c on 2009-05-23
hey hey - go this to work!!

The trick was to use umtsmon.  My laptop and network info is posted on the [last message]("http://ubuntuforums.org/showpost.php?p=7325600&postcount=111").

I had to get the package from sourceforge, which contained a pre-compiled binary, which just ran on my machine.  Here's a screen shot of the monitor window, and the settings page.

[[IMG]http://i42.tinypic.com/11kjwuu.png[/IMG]http://www.areamobile.de/static/zugang/o2.php]("http://i42.tinypic.com/11kjwuu.png")

Getting the APN right was a big part of the solution.  This is the rest of the [O2 Germany UMTS/GPRS/3G connection info]("http://www.areamobile.de/static/zugang/o2.php").

[If you understand German, this info could help]("http://www.linux-community.de/Community/Fragen/o2-Surf-Stick-UMTS-and-Linux-Compatibility").

Unfortunately the wvdial and the NetworkManager methods didn't work for me.

Thanks Fingers and everyone else.

Ashant

---

### Post by Snort44 on 2009-05-23
Glad you got it working.

---

### Post by mevan_snp on 2009-06-01
i'm using 7.10 . totally new to linux. i have typed sudo wvdialconf command , but my modem is not detected. (E220) plz help me.

---

### Post by daldred on 2009-06-06
Why use 7.10?  

I'm using 9.04 and the Huawei 200 basically 'just worked' - plugged it in and network manager recognised and configured it.  

The default settings weren't right for the package I'm on, but that took all of a minute to correct; the only odd thing then was that it asked for a password which turned out to be blank - just hit the enter key and I'm in. 

If you can upgrade to 9.04, I'd say try it!

---

### Post by daldred on 2009-06-07
> **daldred said:**
> Why use 7.10?  

I'm using 9.04 and the Huawei 200 basically 'just worked' - plugged it in and network manager recognised and configured it.  

Actually, I've just realised one thing doesn't work as I might have expected; there shoudl apparently be some storage space visible on the stick, and it doesn't show up.  There's also capacity to add a microSD.

Anyone got access to this storage space from Ubuntu?

---

### Post by Hippyrick on 2009-09-03
thanks very much for a straight answer on this issue...i'd been getting lost amongst the threads myself! :S unfortunatley when i come to check the wvdial file & alter the username etc...the file comes up empty, but it does still exist?! i've absolutely no clue as to why this would be the case? up to this point the method appeared to be working. it slightly worried me though, when it took till ttyusb2 to pick it up though, when previously it was designated usb0?...does this have a bearing at all? many thanks
fellow ubuntu noob

p.s. suppose it would help to tell you i'm running 8.04 netbook remix on a dell mini10 too! :S my bad (dopey sod!)

---

### Post by cataztrophe on 2009-11-23
:popcorn:spectacularr!! love this thread!
anyway,,
can anyone share some info about sending sms with this modem??
and i very2 helpfull if it can used with GAMMU!
thnx before.:p:p

---

### Post by OneCo-Creator on 2009-12-22
Hi. Everything worked fine up to this point:
 
Quote:
Again, in a terminal type...

Code:
sudo gedit /etc/wvdial
This will invoke your text editor (gedit) to open the file at location /etc/wvdial.conf, with administrative privaledges (sudo).

This will look something like this:


Code:
[Dialer Defaults]Init1 = ATZInit2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0Modem Type = Analog ModemBaud = 9600New PPPD = yesModem = /dev/ttyUSB0ISDN = 0; Phone; Password; Username
Quote end.
 
When I typed 'sudo gedit /etc/wvdial' into a terminal - it invoked the text editor (gedit) to open the file with the title at the top being 'wvdial (/etc) - gedit' with 'wvdial' on the tab name, but, no information / data at all ...just a blinking cursor? I having tried closing everything and starting a new terminal, but same response.  Any ideas on how to resolve, thanks in advance.

---

### Post by GeorgeVita on 2009-12-23
Hi **OneCo-Creator**, welcome to this forum!

One of your problems is the actual command which is: ```
sudo gedit /etc/wvdial.conf
```
Then you are going to copy or edit valid parameters into that configuration file.

Post more info about your modem and ubuntu version. If you are using E220 on Ubuntu 9.10 you need firstly to update Ubuntu using another internet connection and possibly search for any firmware updates for the modem.

Post any new data to follow up.

Regards,
George

---

### Post by Nisal on 2009-12-23
well this is nice stuff...very simple thanks boss

---

### Post by Cato2 on 2010-01-02
> **ashant_c said:**
> The trick was to use umtsmon.  


I also found umtsmon worked seamlessly with my Huawei E160 (similar to E220) on O2 UK, using Ubuntu Hardy 8.04 - I just put in the APN, username and password, and left everything else as default.   The only confusing thing is that umtsmon claims I'm not connected, but I really am, as proven by the ppp0 interface stats (sudo ifconfig).

Umtsmon is incredibly easy to set up, and actually **much** easier than using Windows XP (where I tried using the awful O2 Connection Manager in two versions, which just about worked but required rebooting the PC to use WiFi again, and then a complex setup using dialup networking and specific dialling strings).

I'm using O2 UK PAYG, setup details for umtsmon were:

APN: m-bb.o2.co.uk
User: o2bb
Password: password

I did get wvdial working as well, but had to manually configure the routing afterwards.  Here's my /etc/wvdial.conf config file in case it helps someone, tested on Hardy:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Username = o2bb
Password = password
Stupid Mode = yes
Carrier Check = no
Init5 = AT+CGDCONT=1,"IP","m-bb.o2.co.uk"

UPDATE: I couldn't get wvdialconf to auto detect my USB device, so I had to look in /var/log/messages for the line that gives (in my case) /dev/ttyUSB0 as the device name.

After you do "sudo wvdial", type "ifconfig" to check the ppp0 interface is up, and also "tail -22f /var/log/messages" to check on any connection messages.

To configure routing after the ppp0 interface is up:

sudo route del -net 0.0.0.0 dev eth0
sudo route add -net 0.0.0.0 dev ppp0

Then visit [http://mobilebroadbandaccess.o2.co.uk/](http://mobilebroadbandaccess.o2.co.uk/) to make sure you are really connected OK.

Once your wvdial session is over, you need to do something like this to restore your normal default route, assuming 192.168.1.1 is your home router (default gateway):

sudo route del -net 0.0.0.0 dev ppp0
sudo route add -net 0.0.0.0 gw 192.168.1.1 dev eth0

Or just use umtsmon, which automates this.

I also tried upgrading to Network Manager 0.7.1 (June snapshot from the Ubuntu PPA) but it crashed with segmentation fault and was quite hard to start up.

So: the bottom line is to just use umtsmon.  wvdial may be useful if umtsmon doesn't work or you need a command line approach.

---

### Post by Silvertones on 2010-01-07
Well I'm trying to set up a US robotics dial up USB Modem. When I enter WVDIALCONF
I end up with a screen that says "scanning your serial ports for a modem"
It scans and ends up saying Sorry'no modem was detected!Did you configure it properly with SETSERIAL?

SETSERIAL is not installed. Do I need to install and do something? Any Ideas?

---

### Post by GeorgeVita on 2010-01-07
Hi **Silvertones**, try some basic tests to determine the communication port for your modem:

- Boot **without** modem, **wait** for the system to load

- open a terminal window and try: ```
sudo dmesg -c
```
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)

- attach modem, **wait** 30 seconds

- from terminal: ```
dmesg
```
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and post it here.

- from terminal: ```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```
(if any port is created will be listed)

Regards,
George

---

### Post by Silvertones on 2010-01-07
Thanks George'
Will boot out of win & be back with info.

---

### Post by Silvertones on 2010-01-07
john@ubuntu:~$ dmesg
  
  [  149.192070] usb 1-1: new full speed USB device using uhci_hcd and address 3
  
  [  149.360927] usb 1-1: configuration #1 chosen from 1 choice
  
  [  149.859257] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
  
  [  149.862438] usbcore: registered new interface driver cdc_acm
  
  [  149.862453] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
  
  john@ubuntu:~$

---

### Post by Silvertones on 2010-01-07
john@ubuntu:~$ ls /dev/ttyu* /dev/ttya* /dev/ttyh*
  
  ls: cannot access /dev/ttyu*: No such file or directory
  
  ls: cannot access /dev/ttya*: No such file or directory
  
  ls: cannot access /dev/ttyh*: No such file or directory
  
  john@ubuntu:~$

---

### Post by Silvertones on 2010-01-07
john@ubuntu:~$ wvdialconf
  
  Editing `/etc/wvdial.conf'.
  
   
   
  Scanning your serial ports for a modem.
  
   
   
  ttyS0<Info>: Device or resource busy
  
  Modem Port Scan<*1>: S0   S1   S2   S3   
  
  ttyACM0<Info>: Device or resource busy
  
  Modem Port Scan<*1>: ACM0 
  
   
   
   
   
  Sorry, no modem was detected!  Is it in use by another program?
  
  Did you configure it properly with setserial?
  
   
   
  Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
  
   
   
  If you still have problems, send mail to <wvdial-list@lists.

---

### Post by Silvertones on 2010-01-07
So what do you think George? I need to get this going.:(
PS this is a wubi install

---

### Post by garryknight on 2010-01-07
> **Silvertones said:**
> ls: cannot access /dev/ttyu*: No such file or directory
  

Try tty**U*** as in the original post. And with the E220, you do need to wait a fair while, say 30 seconds.

---

### Post by GeorgeVita on 2010-01-08
> **Silvertones said:**
> ...
[  149.192070] usb 1-1: new full speed USB device using uhci_hcd and address 3  
[  149.360927] usb 1-1: configuration #1 chosen from 1 choice
[  149.859257] **cdc_acm 1-1:1.0: ttyACM0: USB ACM device**
[  149.862438] usbcore: registered new interface driver cdc_acm
[  149.862453] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Your modem seems to be **/dev/ttyACM0** (as show above).

>>> All commands are case sensitive: tty**acm**0 is different than tty**ACM**0

Now you need to setup /etc/wvdial.conf (or use gnome-ppp that needs installation from Synaptic).

To edit /etc/wvdial.conf use: ```
gksudo gedit /etc/wvdial.conf
```
And copy the following data (replace username/password)
```
[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```

Read more at [http://ubuntuforums.org/showpost.php?p=8611479&postcount=13](http://ubuntuforums.org/showpost.php?p=8611479&postcount=13)


Regards,
George

---

### Post by Silvertones on 2010-01-08
I'll report back. Thanks!!

---

### Post by Silvertones on 2010-01-08
> **Silvertones said:**
> john@ubuntu:~$ ls /dev/ttyu* /dev/ttya* /dev/ttyh*
  
  ls: cannot access /dev/ttyu*: No such file or directory
  
  ls: cannot access /dev/ttya*: No such file or directory
  
  ls: cannot access /dev/ttyh*: No such file or directory
  
  john@ubuntu:~$

OK using the proper capitals I get

/dev/ttyACM0

---

### Post by Silvertones on 2010-01-08
This is what I get. I also followed the inst. in the link. 

   john@ubuntu:~$ sudo wvdial /etc/wvdial.conf
  --> WvDial: Internet dialer version 1.60
  --> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
  --> Cannot get information for serial port.
  --> Initializing modem.
  --> Sending: ATZ
  --> Sending: ATQ0
  --> Re-Sending: ATZ
  --> Modem not responding.
  john@ubuntu:~$

---

### Post by Silvertones on 2010-01-08
I keep trying and I can see the light blinking on the modem when it tries to access but then it just says "modem not responding"
I tried the modem under Windows and it works fine.
BTW you did catch that this is a US Robotics mdem? Got great reviews for Ubuntu.

---

### Post by GeorgeVita on 2010-01-08
> **Silvertones said:**
> ...BTW you did catch that this is a US Robotics mdem? Yes and also this is a 'Huawei e220' (3g modem) thread ...!

Try the following:

- boot without modem, **wait** for the system to fully load
- attach modem, **wait 20 seconds** and try: ```
ls /dev/ttyA*
```
- confirm that you saw **ttyACM0** and: ```
sudo wvdial
```
- in any case post all terminal output (including your 'sudo wvdial') and also your **/etc/wvdial.conf** file

Regards,
George

---

### Post by Silvertones on 2010-01-08
confirmed I saw ttyACM0

/etc/wvdial.conf

   [Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 8352384
Password = ************
Username = ******

   john@ubuntu:~$ ls /dev/ttyA*
  
  /dev/ttyACM0
  
  john@ubuntu:~$ sudo wvdial
  
  [sudo] password for john: 
  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  --> Modem not responding.
  
  john@ubuntu:~$ 

What is this all about?It's in the above thread.

Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
  
  
Should I move out of this thread to somewere else?

---

### Post by GeorgeVita on 2010-01-08
By default **wvdial** uses **/etc/wvdial.conf** as the configuration file.

When you ran the command: **sudo wvdial /etc/wvdial.conf**
The respond was **Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf** because there is no such 'paragraph' into that file.

The command syntax is: **sudo wvdial option_paragraph**
(ex. '**sudo wvdial ATandT**' if you have an **ATandT** paragraph with specific parameters for your provider)

Read some info (from terminal):```
man wvdial
man wvdial.conf
```

I just note that as this thread regards 3g modems, we have less possibility for 'dial up users' to read it and give some help as we are reaching our 'test limits'.

>>> Your **US Robotics modem** attached at **/dev/ttyACM0**
>>> The **problem**t: **wvdial** for some reason **cannot use it**

I would open a new thread with a title 'USR dial up modem NOT working on Ubuntu 9.10 (wubi)' at '[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")' forum.

G

---

### Post by Silvertones on 2010-01-08
George thanks I'll open a new thread there. Hope you continue with your help.
Thanks

---

### Post by GeorgeVita on 2010-01-08
... a last try/note here:

Running again **wvdialconf** will change your /etc/wvdial.conf !!!

As we know the port, you must not run it again.
You can check if **/etc/wvdial.conf** is different now:
```
cat /etc/wvdial.conf
```

G

---

### Post by Silvertones on 2010-01-08
Maybe this is part of the problem. Running wvdialconf doesn't do anything with the wvdial.conf file. I logged in as root and moved wvdial.conf and then re ran wvdialconf. IT DID NOT CREATE THE FILE. I then used the gksudo gedit /etc/wvdial.conf and saved a blank file. reran wvdialconf and it did nothing. I then replaced it with the one I had entered the info manually.

wvdial.conf resides in-- filesystem/etc/wvdial.conf no folder just the file in etc. This is right?

---

### Post by GeorgeVita on 2010-01-08
NO need to login as 'root'! You have 'root' privileges using 'sudo' in front of command.

>>> Use 'standard' user, check contents of /etc/wvdial.conf with ```
cat /etc/wvdial.conf
```
Try to connect using:
```
sudo wvdial
```
and just after 'connection OR NOT' use again: ```
cat /etc/wvdial.conf
``` to check.

G

---

### Post by Silvertones on 2010-01-08
The reason I logged as root was so that I could move the wvdial.conf file out of the etc folder so i could check if sudo wvdialconf was creating the file and it's not. I put the file that I created back and rerunning sudo wvdialconf doesn't alter it.

---

### Post by GeorgeVita on 2010-01-08
OK, so no progress!

We must wait for 'new ideas' at your [thread]("http://ubuntuforums.org/showthread.php?t=1375907").

Just edit there: you do not need the output of 'sudo wvdial /etc/wvdial.conf'
but the correct output of:
```
sudo wvdial
```

It is better to edit your 1st post, do not post a new one.

G

---

### Post by Silvertones on 2010-01-09
George,
IT IS SOLVED.
I post here as it probably will affect this device as well.
It's a bug in 9.1
You need to uninstall modemmanager as a work around. I send this via Ubuntu.:D

[http://ubuntuforums.org/showthread.php?t=1375907](http://ubuntuforums.org/showthread.php?t=1375907)

---

### Post by cataztrophe on 2010-01-22
wow, nice thred!
anyway, i wanna use this modem on my server ubuntu 9.04.
please help me to mount this modem, because my server doesnt recognise it yet.

thnx before guys :D

---

### Post by rk.rox on 2011-09-21
I started using Ubuntu after 3 years since my Windows OS crashed unexpectedly. Was struggling for a month to configure my E220 USB Modem in my Ubuntu 8.04.1 and viewed your post through my mobile phone and it's Awesome!!! :guitar:

It did everything as you had mentioned, but got an Error after _Alt+F2_ 

I used the code - sudo apt-get install gnome-ppp

And the Error I got was saying that "gnome-ppp" is not available :(

again Browsed the net and found out that gnome-ppp is not coming by default in Ubuntu 8.04.1 and I had to download it separately and Installed it...

After installing gnome-ppp, BOOM !!! Now i'm using my Huawei E220 Modem with my Ubuntu 8.04.1 version :popcorn:
Thanks & Cheers !!! :KS

---


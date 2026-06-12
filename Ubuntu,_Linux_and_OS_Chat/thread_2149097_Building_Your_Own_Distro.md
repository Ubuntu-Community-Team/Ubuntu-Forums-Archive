---
title: "Building Your Own Distro"
date: 2013-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Myst1234 on 2013-05-27
Hi everyone,

In my free time I love to learn more about what Linux can do. Recently I learned about Arch Linux distro, which essentially lets you build and customize your very own distro. AWESOME!

I do have a couple questions before I even come close to going down that path though --

1, Would I be able to configure a untiy-like desktop environment from Arch? I'm so familiar with most thing Ubuntu that I would want tp stay close to it, plus I like the neat features it has :D
I was thinking maybe something with a lightweight desktop and a hidden cairo dock if all else fails, which would mimic the unity "hiding" launcher.

2. Could i keep a lot of the same packages and setups? I like being able to hit the forums with any problems and I've read that youre mostly on your own with Arch.

3. Can I configure Arch endlessly? i.e. build my own ubuntu?

4. The million dollar question here is, should i even bother with Arch? I am not an expert, I am familiar with Linux and I'd say I'm intermediate at best.

Sorry if this is in the wrong section, wasnt sure where to put this thread.

Thanks everyone!!

---

### Post by grahammechanical on 2013-05-27
Ubuntu is open source and that includes Unity. There is nothing to stop anybody from using the Ubuntu code. You are asking questions about Arch on a Ubuntu forum. Whether you get answers depends upon there being people visiting this forum who know more about Arch than you do. 

Regards.

---

### Post by Megaptera on 2013-05-28
You could also have a look at Linux from Scratch. (Quote) "Linux From Scratch (LFS) is a project that provides you with step-by-step instructions for building your own custom Linux system, entirely from source code."
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by oldos2er on 2013-05-28
Moved to Ubuntu, Linux & OS Chat.

---

### Post by Myst1234 on 2013-05-28
> **grahammechanical said:**
> Ubuntu is open source and that includes Unity. There is nothing to stop anybody from using the Ubuntu code. You are asking questions about Arch on a Ubuntu forum. Whether you get answers depends upon there being people visiting this forum who know more about Arch than you do. 

Regards.

I've been an ubuntu user so I dont know where else to go and am hoping for exactly that

---

### Post by Myst1234 on 2013-05-28
> **Megaptera said:**
> You could also have a look at Linux from Scratch. (Quote) "Linux From Scratch (LFS) is a project that provides you with step-by-step instructions for building your own custom Linux system, entirely from source code."
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

 this sounds like a much better place to start! thank you! Would I be able to stay close to ubuntu which is what I'm familiar with? 
I just want to gear the system more towards what I use it for, minus all the extra crap I never use

---

### Post by Myst1234 on 2013-05-28
> **oldos2er said:**
> Moved to Ubuntu, Linux & OS Chat.

Sorry :( wasnt sure where to put it :confused:

---

### Post by deadflowr on 2013-05-28
So what you really want is a highly personal, arch-like ubuntu.

If I was to want to go that route, I would run a strictly bleeding-edge ppa system.

---

### Post by tartalo on 2013-05-28
If you want Unity you should use Ubuntu. Unity has not been designed with portability in mind and although there are some experimental ports for Fedora, OpenSuse and Arch, one shouldn't expect them to work flawlessly.

However, you can achieve something similar to Unity's dash -not equal- using KDE + Homerun, this will work in any Linux distribution, and if all you want is a dock, well, there are tons of options.

In my opinion Arch is the way to go if you want the very latest versions of the programs, *that * is the strongest point of Arch.

Arch is indeed very configurable, but that is also true for all general Linux distributions, including Ubuntu (At least until it migrates to Mir, then things might change). If you want to build a system to suit your needs Arch is not the only choice, although their Wiki certainly helps when you take this route, I find it easier to follow the instructions in the Arch Wiki than the Debian documentation, for example.

It's true that you are a bit "on your own" with Arch, or better said, you are expected to investigate about your problem and try to fix it on your own before you ask for help, and when you do you are expected to give valuable information. This is not exclusive from Arch, you'll get the same recommendation in most other Linux forums.

Will you have the same packages in Arch? Not all of them, some things are exclusive to Ubuntu, in Arch you'll get no purchase recommendations from Amazon when you search your private documents, and there's no Ubuntu software center, but you can install easily Steam and you graphic cards closed source driver... you should have a look at the packages available in Arch and AUR to see if everything you expect is there.

Should you bother with Arch? Arch it's not for newbies, but an intermediate user willing to learn more about Linux and take control of the computer should give it a try at least.

I'd recommend to start with a Virtual Machine, like VirtualBox.

---

### Post by Myst1234 on 2013-05-28
> **deadflowr said:**
> So what you really want is a highly personal, arch-like ubuntu.

If I was to want to go that route, I would run a strictly bleeding-edge ppa system.

Meaning repositories that update regardless of ubuntu's update?

I am familiar with ubuntu which I think is why I like it. I also like a few of the GUI features, like the launch panel that can be hidden, But I feel like there is too much in this system i do not, and will never, use.

---

### Post by Myst1234 on 2013-05-28
> **tartalo said:**
> If you want Unity you should use Ubuntu. Unity has not been designed with portability in mind and although there are some experimental ports for Fedora, OpenSuse and Arch, one shouldn't expect them to work flawlessly.

Didn't know that, that's something I really enjoy.

  > However, you can achieve something similar to Unity's dash -not equal- using KDE + Homerun, this will work in any Linux distribution, and if all you want is a dock, well, there are tons of options.

I run a cairo dock on my Lubuntu 13.04 netbook, which is where I got the idea.

 > In my opinion Arch is the way to go if you want the very latest versions of the programs, *that * is the strongest point of Arch.

Arch is indeed very configurable, but that is also true for all general Linux distributions, including Ubuntu (At least until it migrates to Mir, then things might change). If you want to build a system to suit your needs Arch is not the only choice, although their Wiki certainly helps when you take this route, I find it easier to follow the instructions in the Arch Wiki than the Debian documentation, for example. 

Is there an easier to read ubuntu doc? Maybe I could just modify my current distro

 > It's true that you are a bit "on your own" with Arch, or better said, you are expected to investigate about your problem and try to fix it on your own before you ask for help, and when you do you are expected to give valuable information. This is not exclusive from Arch, you'll get the same recommendation in most other Linux forums.

Will you have the same packages in Arch? Not all of them, some things are exclusive to Ubuntu, in Arch you'll get no purchase recommendations from Amazon when you search your private documents, and there's no Ubuntu software center, but you can install easily Steam and you graphic cards closed source driver... you should have a look at the packages available in Arch and AUR to see if everything you expect is there.

Mentioned earlier, LFS, is this similar to what you're talking about above? If not, why?

 > Should you bother with Arch? Arch it's not for newbies, but an intermediate user willing to learn more about Linux and take control of the computer should give it a try at least.

I definitely want to try!

 > I'd recommend to start with a Virtual Machine, like VirtualBox.

I tried Wine once and was less than impressed. Is there a better way to go about it?

---

### Post by tartalo on 2013-05-28
> **Myst1234 said:**
>  Is there an easier to read ubuntu doc? Maybe I could just modify my current distro
There's an Ubuntu wiki (but I started using the Arch wiki to solve my doubts even before using Arch Linux, a matter of taste I guess.)

> Mentioned earlier, LFS, is this similar to what you're talking about above? If not, why?
No, Arch is more similar to Ubuntu than to LSF, it's a distribution, it has precompiled packages and tries to save work to the user, although it has a different kind of user in mind.

> I tried Wine once and was less than impressed. Is there a better way to go about it?
Wine? Did you mean VirtualBox? There are alternatives like qemu, kvm... but virtualbox is the easiest option in my opinion.

---

### Post by cortman on 2013-05-28
LFS is totally from scratch. You need to compile a toolchain including binutils, coreutils, gcc and the Linux headers, then you need to compile another toolchain compiled against the existing toolchain, then you can start compiling the actual system.
My LFS build took a week and I probably have about 25-30 hours invested in it. It is not for complete tyros; familiarity with the command line and with basic compiling using gcc is essential.
I would download VirtualBox and build Arch in it, if you are interested. Do be aware that the Arch community does not suffer fools (people who don't bother reading the documentation and simply post a whiny demand for help) gladly. You should consider yourself as being on your own as far as researching errors and implementing fixes.
Both can be a great learning experience. Good luck.

---

### Post by Sam Mills on 2013-05-28
> **Myst1234 said:**
> this sounds like a much better place to start! thank you! Would I be able to stay close to ubuntu which is what I'm familiar with? 
I just want to gear the system more towards what I use it for, minus all the extra crap I never use
For what you want, you may want to consider a command-line install of ubuntu. It will give you a bare bones install with whatever desktop environment you choose. Then you can install only the apps you want, and it will be very fast. And it will allow you to stay within the friendly confines of ubuntu. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I'm not trying to steer you away from any other methods, but be prepared to put a ton of work into something like linux from scratch. On the other hand, a command line install of ubuntu is relatively easy.

---

### Post by Cheesemill on 2013-05-29
> **Sam Mills said:**
> For what you want, you may want to consider a command-line install of Ubuntu.

+1

If you want something that uses all of the Ubuntu repositories and package management software and uses the Unity interface then stick with Ubuntu.

Do your initial installation using either the [Mini CD]("https://help.ubuntu.com/community/Installation/MinimalCD") or the server CD to get a command line only install, and then just install the packages you want and nothing else.
For example running the command...
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```
will install the Unity desktop, but won't install any of the applications that come as standard with a normal Ubuntu installation.
This will give you the smallest possible base OS to which you can add your favoured applications.

---

### Post by mastablasta on 2013-05-29
another nice how to for minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

i think this would be enough for what you want to do/have. you can do simialr with debian netinstall if you want to have even less stuff installed on start. then you just add the packages you want to add. see f it all works ok and then use remasytersys now called system imaging: 
[http://www.remastersys.com/](http://www.remastersys.com/)
[http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/)

which will create your very own distribution (based on debian/ubuntu) iso image you can then share with others or keep for yourself.

---

### Post by Myst1234 on 2013-05-29
Lots of stuff to read, thanks guys!

Seems like a command line ubuntu would be what I'm looking for. Am I going to need an install package or cd? I originally got linux ubuntu on this computer from a thumb drive.

---

### Post by Cheesemill on 2013-05-29
You can use either a CD or a USB stick to install a minimal Ubuntu.

As for which image to download you have 2 options, either go for the server CD or the mini CD. You end up with the same minimal system no matter which one you use, the only difference is that the server CD contains all of the packages needed to install whereas the mini CD downloads all of the packages you need to install from the internet during installation. The upshot of this is that using the mini CD means that your system is fully up to date from the start, whereas the server CD installation will need updating.

The server CD images can all be found at [http://releases.ubuntu.com/](http://releases.ubuntu.com/) and the mini CD images can be found at [http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/) (you're looking for the mini.iso file).

---

### Post by Myst1234 on 2013-05-30
Well I've started my build. 2 things though....

1. I cannot seem to get wireless working at all. Any tips for me there?

2. I think I accidentally partitioned the system to run off the thumb drive. When I boot without it, the computer does not go past the blank screen with a flashing cursor. Can I fix this manually? Or do I need to reinstall and be more mindful of the partitioning?

---

### Post by Myst1234 on 2013-05-30
Seems like I'm working out my wireless issue by following a couple different guides out there. Not sure if I'm able to make it permanent through any of these though. That's my concern so far with wireless. 

EDIT:: Still finding it hard to get a network and connect to it.

The partitioning is still in the front of my mind as a problem though.

---

### Post by CosmicFlux on 2013-05-30
Hi,

I'm working on a project called** GraViTTY Linux**. It stands for Graphical Virtual TTY Linux. The idea is that your environment is an attractive, modern-looking TTY-style session which allows the user to operate in a fully CLI environment whilst retaining access to graphical apps and multimedia content, such as video. It provides the user with the ultimate freedom of choice, without having to make sacrifices on either side - which is, after all, a basic tenet of Linux :)

Here are some screenshots:

**Early Environment:**
[[img]http://s7.postimg.org/9ogcs15lz/Screenshot_from_2013_05_12_02_39_14.jpg[/img]](http://postimg.org/image/9ogcs15lz/)[[img]http://s12.postimg.org/vt1woa9y1/Screenshot_from_2013_05_27_18_10_13.jpg[/img]](http://postimg.org/image/vt1woa9y1/)

**Latest Version:**
[[img]http://s21.postimg.org/63m5y7l4j/Screenshot_from_2013_05_31_01_17_39.jpg[/img]](http://postimg.org/image/63m5y7l4j/)[[img]http://s23.postimg.org/voydy28cn/Screenshot_from_2013_05_31_01_18_18.jpg[/img]](http://postimg.org/image/voydy28cn/)[[img]http://s7.postimg.org/j5fcq5487/Screenshot_from_2013_05_31_01_40_13.jpg[/img]](http://postimg.org/image/j5fcq5487/)


Cosmic

---

### Post by Myst1234 on 2013-05-30
@CosmisFlux

That looks and sounds pretty great. Kind of like what I would like to do. So perhaps you can help me through these begining build hurdles I'm facing?

---

### Post by CosmicFlux on 2013-05-30
Sure.

Are you running off a LiveCD or USB? You have the option of pre-partitioning your hard drive with gParted prior to install, as long as you know which partitions you need to create, or you could just let Ubuntu throw you into the installation partitioner and do it from there. You want to ensure you get your wireless sorted before you install though. What's happening with your wireless? Are you getting any error messages?

Cosmic

---

### Post by Myst1234 on 2013-05-30
Yes, so far my issue is not being able to set anything for it. 

Trying to connect to it gives this error message

> Error for wireless request "Set ESSID" (8B1A)
SET failed on device wlan0 ; Operation not permitted.

I've tried to follow some guides online about setting iwconfig and everything, but nothing I've read so far has worked. I continue to get that same error above.

I started from a USB

---

### Post by CosmicFlux on 2013-05-30
Start at the very beginning & let me know what you've done so far with regards to your install. Are you using Ubuntu as your distro?

How are you attempting to set up your wireless?

Also, what is the output of the **iwconfig** command? 


Cosmic

---

### Post by Myst1234 on 2013-05-30
I got the mini.iso from Ubuntu's releases page.

I used UNetbootin to configure my USB to install.

I changed the boot order to boot from the USB.

I chose a command-line install.

I waited for it all to do its thing, while connected to a hardwire ethernet cable.

So far I've only messed with iwconfig and ifconfig as I've read mainly from a post on askubuntu.com. This is where I can "force" the wireless connection with

> iwconfig wlan0 up

I can scan for networks, I know my essid and password, so once it was picked up I ran this 

> iwconfig wlan0 essid NETWORK-NAME key NETWORK_PASSWORD

And that's when I got the error above.

iwconfig read out

> wlan0   IEEE 802.11bg ESSID"NETWORK_NAME"
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

lo   no wireless extensions

eth0    no wireless extensions

---

### Post by CosmicFlux on 2013-05-30
OK, thanks.

Try running** iwconfig wlan0 essid** [FONT=Courier New]NETWORK-NAME[/FONT] **key** [FONT=Courier New]NETWORK_PASSWORD[/FONT] with a **sudo** prefix.


Cosmic

---

### Post by Myst1234 on 2013-05-30
With the sudo prefix

> Error for wireless request "Set Encode" (8B2A) :
invalid argument "NETWORK_PASSWORD"

The password is correct though, it is the same wireless network I am using on one of my other laptops as we speak.

---

### Post by CosmicFlux on 2013-05-30
Is your wireless encryption WPA/WPA2? If so then enter **which wpa_supplicant** at the command prompt to find out if you have the package installed. If not then you'll need to install it and set up a config file (just a few lines). 


Cosmic

---

### Post by Myst1234 on 2013-05-30
I believe WPA.

which wpa_supplicant read out

> /sbin/wpa_supplicant

---

### Post by CosmicFlux on 2013-05-30
OK good, that means you already have the necessary commands. 

Firstly, run **iwlist wlan0 s | grep ESSID** to make sure your Access Point/connection is listed. If so, run:

**wpa_passphrase SSID PASSWORD > wpa.conf** 

Then run **wpa_supplicant** and ensure the wext driver is listed. There will be others, but most users will want the wext driver.

Now all you have to do is is attempt to connect using the wpa.conf file and driver name as arguments, like so:

**wpa_supplicant -i[FONT=Courier New]INTERFACE_NAME[/FONT] -cwpa.conf -Dwext**

Then:

**sudo dhclient wlan0** to get an IP.

Try that and see what happens.


Cosmic

---

### Post by Myst1234 on 2013-05-30
**iwlist wlan0 s | grep ESSID **didn't return anything. Just user@computer_name:~$ almost as if nothing happened.

**wpa_passphrase SSID PASSWORD > wpa.conf  **should SSID PASSWORD be the actual password? Or as written here?

**wpa_supplicant  **wext was listed in the drivers section.

**wpa_supplicant -i[FONT=Courier New]INTERFACE_NAME[/FONT] -cwpa.conf -Dwext  **I assume the interface name would be wlan0. When I entered this I kept getting the basic read out of wpa_supplicant 
[B]
EDIT:[/B] I mis-read the line and fixed it, now I've gotten a lot of Operation Not Permitted read outs

**sudo dhclient wlan0 **&#8203;is this supposed to take very long? Or is it because the other commands were not apparently successful that this is hanging?

---

### Post by CosmicFlux on 2013-05-30
Right, well we'll assume that your SSID is available anyway and try to connect to it. 

**wpa_passphrase SSID PASSWORD > wpa.conf** <---Substitute the SSID & PASSWORD arguments for the name of your connection and your password. This will write your network settings to the specified configuration file. 

**wpa_supplicant -iINTERFACE_NAME -cwpa.conf -Dwext** <--- Yes, you would substitute INTERFACE_NAME with **-iwlan0** 

Run this as sudo and let me know if you have any more luck with it. If it connects successfully then CTRL+C to break out of it and run the command again but add -B after wpa_supplicant to run the process in the background.  

If none of this works we could use nmcli c and another script to create the connection through the Network Manager. 


Cosmic

---

### Post by Myst1234 on 2013-05-30
I'm not sure what's happening with it now.

I'm getting a lot of Invalid arguments and Device or resource busy. Association request to driver failed. Failed to initiate AP scan. 
And a few other read outs.

Amongst it all I did notice a couple things, WPA key negotiation completed and CTRL EVENT Connected.

It kept reading out repeats long enough for me to CTRL - C out of it.

I'm also having to 

> sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up

everytime I try anything related to the wireless this whole time. Even after I force it up, it will lose the connection after a few.

---

### Post by CosmicFlux on 2013-05-30
So are you managing to establish a connection, but it keeps dropping out? 


Cosmic

---

### Post by Myst1234 on 2013-05-30
That's what I think the read out is saying. It doesn't even connect for but a second though, and all the other error read outs are mixed in with the two positive ones that lead me to believe I got a connection at least for a second.

there's also some error read outs that mention Invalid EAPOL-Key MIC and could not verify EAPOL-Key MIC

---

### Post by CosmicFlux on 2013-05-31
Hmm this could be a problem specific to WPA2. I recall a bug report concerning the wpa_supplicant package relating to WPA2. I think using WPA1 may work. Have you tried rebooting? It may be an idea to do a graphical install or run the .iso as a live session and see if the GUI network manager establishes a lasting connection.


Cosmic

---

### Post by Myst1234 on 2013-05-31
After a reboot,  I forced my wireless on, input this

> **wpa_supplicant -iINTERFACE_NAME -cwpa.conf -Dwext**

And the read out is as follows

> ioct[SIOCSIWENCODEEXT]: Invalid argument
ioct[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Trying to associate with 00:bunch: of:numbers: (SSID/NETWORK_NAME' freq 2462 MHz)
ioctl[SIOCSIWFREQ]: Device or resource busy
wlan0: Association request to driver failed
wlan0: Associated with 00:bunch: of:numbers:
wlan0: WPA: Key negotiation completed with 00:bunch: of:numbers [PTK=TKIP GTK=TKIP]
wlan0: CTRL-EVENT-CONNECTED -- Connection to 00:bunch: of:numbers completed (auth) [id=0 id_str=]


And it seems to have stopped there successfully, but with a handful of seemingly unsuccessful read outs as you see above.

What should I do from here? Seems like a couple things still aren't where they should be. When I CTRL-C to stop it, and try to rerun it in the background, all the error messages come back and I do not get connection.

---

### Post by CosmicFlux on 2013-05-31
Run it again as follows:

**wpa_supplicant -iINTERFACE_NAME -cwpa.conf -Dwext & 2> /dev/null**

And then:

Run **nmcli d | grep wlan0** and tell me what the output is.


Cosmic

---

### Post by cortman on 2013-05-31
> **CosmicFlux said:**
> Hi,

I'm working on a project called** GraViTTY Linux**. It stands for Graphical Virtual TTY Linux. The idea is that your environment is an attractive, modern-looking TTY-style session which allows the user to operate in a fully CLI environment whilst retaining access to graphical apps and multimedia content, such as video. It provides the user with the ultimate freedom of choice, without having to make sacrifices on either side - which is, after all, a basic tenet of Linux :)

Here are some screenshots:

Cosmic

Very interesting! I suppose you ARE running X, however?

---

### Post by Myst1234 on 2013-05-31
> **CosmicFlux said:**
> Run it again as follows:

**wpa_supplicant -iINTERFACE_NAME -cwpa.conf -Dwext & 2> /dev/null**

And then:

Run **nmcli d | grep wlan0** and tell me what the output is.


Cosmic

Was that the proper command? I ran it and got nothing but errors, and CTRL C could not stop it. It ran for roughly 5 minutes before I decided to shut the computer down. Upon restart it said something like "Cache not found" and "Unable to read xxxxxx"

After a couple different tries, nothing changed, or worked, so I went back and am doing a fresh install, command-line again, from a USB. :(

What's going on? I just want wireless working so I can continue my custom build without being hardwired in. :?

---

### Post by Myst1234 on 2013-05-31
**UPDATE:** I have installed wireless-tools and network-manager from the new command-line fresh install and that is absolutely it thus far.

My next step will be to follow this tut - [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I have also installed, linux-firmware-nonfree, some things I've read say that could help, but I have yet to even be bale to pick up my wlan0 interface

**2nd UPDATE: **I finished the tut. I noticed upon reboot my system does not get past the splash screen (black screen with blinking cursor) unless the USB is plugged in. During the installation when it got to the partitioning section, I did everything default. 

Guided - Use Entire Disk - then it asked which disk, there are only two, the hard drive of my computer and the USB. I picked the comp's hard drive, but still I cannot boot without the USB. FRUSTRATING!

---

### Post by CosmicFlux on 2013-05-31
**_MYST1234:_**

The command was set to run in the background, surpressing all error messages. To stop it you'd need to kill it with a kill {PID} or killall command. But I am at a loss to explain your situation. The only remaining option I could suggest is to use the graphical Network Manager to establish the connection on your system and then remove X after it's been set up, if that's your wish. You *could* set the connection to use WEP, but it's not very secure and I'd not recommend it if you have the option of WPA/WPA2. 


**_CORTMAN:_**

Yes, X is running - albeit with much of the bloat removed. No window decoration, no visual effects, less processesses eating up RAM & CPU time. X runs on top of the shell, like in any other graphical environment, and the GraViTTY CLI session runs on top of X - giving you the functionality of a graphical environment but with a command line interface. There are shell functions built into the rc file that customize the output of commands, shortened command sequences (such as **get** to replace *sudo apt-get install* and **rset** to re-source the rc configuration, the **cdr** and **dvr** commands are used for CD and DVD ripping respectively.) Basically, the emphasis is on speed and providing a more intuitive CLI experience, with MovieOS-style aesthetics. 


Cosmic

---

### Post by Myst1234 on 2013-05-31
> **CosmicFlux said:**
> **_MYST1234:_**

The command was set to run in the background, surpressing all error messages. To stop it you'd need to kill it with a kill {PID} or killall command. But I am at a loss to explain your situation. The only remaining option I could suggest is to use the graphical Network Manager to establish the connection on your system and then remove X after it's been set up, if that's your wish. You *could* set the connection to use WEP, but it's not very secure and I'd not recommend it if you have the option of WPA/WPA2. 


**_CORTMAN:_**

Yes, X is running - albeit with much of the bloat removed. No window decoration, no visual effects, less processesses eating up RAM & CPU time. X runs on top of the shell, like in any other graphical environment, and the GraViTTY CLI session runs on top of X - giving you the functionality of a graphical environment but with a command line interface. There are shell functions built into the rc file that customize the output of commands, shortened command sequences (such as **get** to replace *sudo apt-get install* and **rset** to re-source the rc configuration, the **cdr** and **dvr** commands are used for CD and DVD ripping respectively.) Basically, the emphasis is on speed and providing a more intuitive CLI experience, with MovieOS-style aesthetics. 


Cosmic


I'd like to do it the right way, and I believe the router is already configured at WPA. Not my area of expertise by far. Is your Gavitty distributable? 

I used the tutorial on a very basic minimal build so I have a little bit of a GUI

> nmcli d | grep wlan0 read out

wlan0 802-11-wireless disconnected

I mainly use this computer for learning, developing and of course multimedia like music and watching movies.

---

### Post by Cheesemill on 2013-05-31
Another option for trying to sort out your wireless is to use the wicd network manager. It's usually used when you have a graphical interface running but it also has a command line interface you can use. To install and run it...
```
sudo apt-get install wicd-cli
sudo wicd-cli
```

This should bring up a GUI-like screen on the command line that can be navigated with the keyboard (do a Google image search for wicd-cli to see what I mean).

I can't remember the exact steps from here as I've not used it for years but it's pretty self explanatory.

---

### Post by Myst1234 on 2013-05-31
Thanks Cheesemill! I'll have to try this next.

I like Cosmic's Gravitty build, it's kind of what I'm looking to do. I also saw a combo of Unity and Shell being used on someone else's build, though I forget where I saw it now. It was nifty.

I really just need to get my wireless sorted out, then I can figure out the rest of my build. The first tut was helpful to get the bare bones system up and running, but had nothing for me after that. 

And I'm still curious as to why my USB is needed to boot when I clearly partitioned the system to use my comp's hard disk.

---

### Post by CosmicFlux on 2013-05-31
You may run into a problem with the wicd client not connecting to the daemon and throwing out a D-Bus error. I believe there is a bug in the latest incarnation of it. If so you could try downgrading to the previous version. 

Nah, GraViTTY is not quite distributable yet. I've got it running on both an older Acer laptop and a brand new PB EasyNote TM. Got a few bugs to iron out. 


Cosmic

---

### Post by Myst1234 on 2013-05-31
Is this thread anything to consider? [http://ubuntuforums.org/showthread.php?t=2084716](http://ubuntuforums.org/showthread.php?t=2084716)
Basically the only difference is they are talking about a server install, but others argue the mini.iso (which is what I did) install.

I'm not sure if it matters but the mini.iso I have is 13.04. I tried 12.04 and 12.10 first, but in the installation it froze and just hung there for quite some time. 13.04 is the only one that went through the entire base installation for me. Also not sure if it matters but this is all being run/built on a HP Pavillion DV6000

> [COLOR=#000000]If so you could try downgrading to the previous version.[/COLOR]

How would I do that?

p.s. let me know when gravitty is ready, I'm really interested to work with it.

---

### Post by CosmicFlux on 2013-05-31
You can find stable versions[ here ]("http://sourceforge.net/projects/wicd/files/wicd-stable/").

Let me know when you get your system up and running and I'll let you know what you need to do. Bear in mind you'll need to have X installed, even if you don't want to use it.


Cosmic

---

### Post by Myst1234 on 2013-05-31
From help.ubuntu 
> [COLOR=#333333][FONT=Ubuntu]mini.iso [/FONT][/COLOR][does not work]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/506441")[COLOR=#333333][FONT=Ubuntu] with the [/FONT][/COLOR][USB stick installation method]("https://help.ubuntu.com/community/Installation/FromUSBStick")[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

That's what I was doing. Could this be the reason I've run into a problem that should've been easily solved?

---

### Post by CosmicFlux on 2013-06-01
It's definitely a possibility. Do you have a LiveCD option with the mini.iso?

Cosmic

---

### Post by Sam Mills on 2013-06-02
> **Myst1234 said:**
> From help.ubuntu 


That's what I was doing. Could this be the reason I've run into a problem that should've been easily solved?
I thought it was a waste of space, but I found putting the mini iso on a cd worked best.

---


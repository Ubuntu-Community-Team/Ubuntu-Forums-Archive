---
title: "Need help with getting internet working"
date: 2010-07-07
forum: Ubuntu Studio
---

### Post by norskeinherjar on 2010-07-07
Ok, so, I've used Ubuntu before... never had this big of a problem with it. I just had to replace the hard drive in my laptop so I decided to install Ubuntu Studio and give it a try. The install went alright but when it started there's no network connection options, even plugging my computer directly into the router won't recognize anything. I've seen other people resolve the problem by downloading the network-manager package but I can't do that because the computer will not recognize any internet connection. 

And I've tried installing packages from the CD but it keeps telling me to insert a disc into the cd-rom drive even though there's definitely one in there.

Will someone tell me what the **** my dumbass is forgetting before I throw my laptop out the window?

---

### Post by cchhrriiss121212 on 2010-07-07
Put the studio dvd in the drive and browse to this location:
 /media/cdrom1/pool/main/n
Then install the .deb packages in network-manager and network-manager-applet. You should see it in the taskbar next time you boot.
NM is left out of the build on purpose due to interfering with the audio processing, so if you are using audio best to remove it from the autostart menu.

---

### Post by norskeinherjar on 2010-07-07
Yeah, I actually finally figured that out about an hour after posting this. Lol. Thanks though.

---

### Post by mango42 on 2010-07-08
> **cchhrriiss121212 said:**
> NM is left out of the build on purpose due to interfering with the audio processing, so if you are using audio best to remove it from the autostart menu.

I've been wondering about this 'omission' for a while. Not that I have done any research on it but could it be because of the potential security issue surrounding firewire ports rather than 'interfering with audio'?

---

### Post by cchhrriiss121212 on 2010-07-08
> **mango42 said:**
> I've been wondering about this 'omission' for a while. Not that I have done any research on it but could it be because of the potential security issue surrounding firewire ports rather than 'interfering with audio'?
I have also been wondering about nm's exclusion but information on it seems scarce. All I know about it is what I have read second hand on these forums, but it seems to be the likely reason. I think regular Ubuntu users will be using firewire as much as studio users so that wouldn't make as much sense to me.
All I can find on the studio site:
 > Network tools like NetworkManager and Pidgin will be available on
     the DVD disc repository but not installed by default

---

### Post by fritzm on 2010-07-09
> **mango42 said:**
> I've been wondering about this 'omission' for a while. Not that I have done any research on it but could it be because of the potential security issue surrounding firewire ports rather than 'interfering with audio'?

You can get more detail on the issue from Scott Lavender's message on Ubuntu-studio-devel mailing list : [http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html](http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html)

Fritz

---

### Post by sightsoundsoul on 2010-07-13
Hello, everyone. This is my first post and I'm a first time user of Linux. I'm using a preinstalled 64 bit version of Ubuntu Studio 10.04 on an Inspiron 1545 so I didn't have an install dvd. I have one now that I've downloaded from ubuntustudio.org, put on a usb drive and transferred to my laptop.

I've had my laptop for a week now and cannot connect to the Internet via wireless or wired connection. I've put off asking for help to do searches on this site as well as other places on the web since I know this issue has been encountered before.

> **cchhrriiss121212 said:**
> Put the studio dvd in the drive and browse to this location:
 /media/cdrom1/pool/main/n
Then install the .deb packages in network-manager and network-manager-applet. You should see it in the taskbar next time you boot.
NM is left out of the build on purpose due to interfering with the audio processing, so if you are using audio best to remove it from the autostart menu.

My problem is that I do not see network-manager or network-manager-applet in the taskbar upon rebooting after installing the .deb files. Network-manager does show installed in Synaptic Package Manager. Network-manager-gnome also shows installed, but there's no sign of applet. I've got a feeling that I'll need to install all of the files starting with "network-manager-" listed in Synaptic, but I'm not sure.


I've tried the steps from this thread as well to no avail:
[http://ubuntuforums.org/showthread.php?t=1479788]("http://swiss.ubuntuforums.org/showthread.php?t=1479788").

Any assistance is appreciated. Thank you.

---

### Post by cchhrriiss121212 on 2010-07-14
What happens when you type nm-applet into a terminal and press enter?

---

### Post by sightsoundsoul on 2010-07-14
It says:

[FONT=Courier New]An instance of nm-applet is already running.

** (nm-applet:1592): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager.[/FONT]

---

### Post by sightsoundsoul on 2010-07-18
I got the applet running with help from post #10 of this thread:
[http://ubuntuforums.org/showthread.php?t=1074132](http://ubuntuforums.org/showthread.php?t=1074132)

"sudo restart network-manager"

Next step is getting connection information for both wireless and Ethernet connections.

---

### Post by halfsoul on 2010-09-18
I found this thread very useful, so I created a Wiki page to help other users:
[Ubuntu Studio Network Setup]("http://help.ubuntu.com/community/UbuntuStudioNetworkSetup")

Please have a look and correct any mistakes.

Thanks again.

---

### Post by wentzr on 2012-01-18
So the answer to the question "how do i get the network manager applet to appear in the notification area" in ubuntu studio 10.04 is incredibly simple, but not often highlighted in any of these threads I've run across over the past few days. There's plenty of "fixes" suggested by people assuming it's a driver issue, backport issue, network manager isn't installed.. etc etc. 

Assuming you've already gotten that far and still have no success, here is the fix you're looking for:

In terminal:
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf 
```in gedit:
last line - change the "false" to "true". It should read:
```
managed=true
```reboot and there is your network applet. 

that's it, simple but probably the most important step in answering this question as the rest is fairly easy to deduct and figure out on your own. 

I'm running the kxstudio rt kernel on top of ubuntu studio and have hardly noticed any latency caused by enabling wifi. Expect xruns when enabling or disabling wireless, but at least now you have the ability to use wifi in a pinch instead of reboot to a different kernel.

Edit: 
Additionally, from my experience, if while setting up to install ubuntu studio 10.04 you chose to skip setting up DHCP networking, the NetworkManager software will not be installed, therefore the above file or path exist on your system.. 
That's ok though, you've got a CL terminal. Which.. you could have just gone to in the first place to do what you want network manager to do :)

to enable dhcp, the magical incantation to get you connected is:

```
sudo ip link set dev eth0 down
sudo dhclient eth0
```

---


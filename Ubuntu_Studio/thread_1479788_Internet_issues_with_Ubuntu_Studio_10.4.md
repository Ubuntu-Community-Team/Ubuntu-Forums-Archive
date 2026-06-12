---
title: "Internet issues with Ubuntu Studio 10.4"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by DonaldDock on 2010-05-11
Hello,

I recently installed Ubunutu Studio 10.4 to a partition on my windows 7 laptop. Suffice to say it was relatively clean and GRUB is working fine too. I can get to either OS without a hitch. 

My problem comes during the closing stages of the installation. It failed to configure DCHP and I did not do so manually. Now I have Ubuntu Studio on my laptop, however I have no way of connecting to the internet and need assistance here. 

I understand by default, Ubuntu Studio does not have Network-Manager installed. 
So I have downloaded the Network-Manager 0.8, but really, I have no idea on how to install it to my machine because I am pretty new to Linux and Ubuntu. 

Furthermore, I plug my ethernet cord into my laptop and still don't have  a connection.

I'm pretty experienced and somewhat advanced with Windows platforms, but I feel uber confused when I look at the files in the archive for Network-Manager. I have no idea where or how to install this and how to get my internet working correctly and any help would be awesome.

---

### Post by cchhrriiss121212 on 2010-05-11
You don't need to compile network manager from source, as it is included on the studio image in a few .deb packages:
/media/cdrom0/pool/main/n/network-manager-applet

---

### Post by DonaldDock on 2010-05-11
I tried going through Synaptic as was suggested already by someone I know, but I couldn't find anything in there for the life of me.  Someone else suggested going through terminal, however, the command they suggested did not work either.

The command was "sudo apt-get install network-manager network-manager-gnome" to no avail. It couldn't find the package I was trying to install. should I put the Installation disc in and try this?

---

### Post by cchhrriiss121212 on 2010-05-11
Yes, my earlier post shows exactly where to find it on the studio disk. It is your only option, as you cannot download things without an internet connection.

---

### Post by DonaldDock on 2010-05-13
Awesome, it worked. I had a little bit of trouble when it was trying to reference the dependency files off the disc, it was looking for them as if the image I installed was Ubuntu Studio 9.10 (Karmic). It obviously couldn't find them however.

I did a clean install of Ubuntu Studio 10.04 (Lucid) and never used any version of Ubuntu on this machine prior to that. So I can only fathom a guess that those deb files haven't been updated yet? Other than that, I don't know why it was looking for (karmic). 

Thanks for the help

---

### Post by crazyzenmaster on 2010-05-19
I have been reading the helpful comments of DonaldDock and cchhrriiss121212 and unfortunately I have the same problem (DCHP Connection error and cannot connect to the Internet). 

I have tried the suggested solutions here but could not find '/media/cdrom0/pool/main/n/network-manager-applet' within Ubuntu Studio 10.4 or Ubuntu 10.4 (lucid lynx) and even tried the installation disks for 9.10 (karmic koala).

I did find some .deb networking tools within /media/cdrom0/pool/main/n/ and installed them but still I cannot to the Internet. 

Unfortunately I am relatively new to Linux and of limited ability could DonaldDock show the process he used as I think we have the same issue?

Kind regards,
John

---

### Post by cchhrriiss121212 on 2010-05-19
If you have a studio image then you should find the .debs on there, but the regular Ubuntu image does not as it is a smaller size. Once you have found them then you just click on them to install.

---

### Post by crazyzenmaster on 2010-05-19
Thanks for the very quick reply. 

I have just done another install of Ubuntu Studio 10.04 (lucid lynx) and received the same error (as expected). Found the network-manager-applet within the image on the installation disk. Tried to load the applet and got the message "Error: Dependancy is not satisfiable: libnm-glib2 (>= 0.8~rc2~git.20091229t135236.302e62d)". 

I presume this is what 'DonaldDock' was talking about - the dependancy files are from Karmic Koala?? Do you know how I would resolve this dependancy issue? 

Kind regards

---

### Post by BorgCymru on 2010-05-23
Getting the same problems, If I open network manager from system/admin there are no adaptors or connections shown.

---

### Post by smexydiggz on 2010-05-25
Hey in order to solve this issue with UbuntuStudio 10.04 amd64/ 32bit, you'll need to reboot your machine and select from the Grub Boot Loader the Generic Recovery Mode. Be sure to connect your Ethernet cable to your machine. Continuing, you'd be taken to a blue screen with several options, select the one that says Net root, it will then recognize your connection and would assign you an IP Address through DHCP of course, then prompt as Root. Here you type 'sudo apt-get update' then 'sudo apt-get install network-manager'. Hope this helps

---

### Post by mango42 on 2010-05-27
> **smexydiggz said:**
> ...Be sure to connect your Ethernet cable to your machine.

Didja ever watch Catch22, smexydiggz? ;-)

Now, imagine yourself in a dusty old thatched village way in the outback, with only a bicycle generator to power a wifi dongle pointed at a distant and inaccessible access point...

and not an ethernet connection in sight...

:popcorn:

---

### Post by arunarun4 on 2010-06-03
Hi all..
May be this can help you connect to Internet through ethernet.

[COLOR=Red]*ifconfig -a | grep eth*[/COLOR]
This will give you the ethernet details. Be sure to check the number  after "eth"; ie "eth0". "eth1". And that is your ethernet port. This is  applicable to all further commands.

[COLOR=Red]*sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0*[/COLOR]
This will create a temporary ip. 
[I]
[COLOR=Red]ifconfig eth0[/COLOR][/I]
Use this to verify the configuration. 

[COLOR=Red]*sudo route add default gw 10.0.0.1 eth0*[/COLOR]
This will create a default gateway.

[COLOR=Red]*sudo gedit /etc/network/interfaces*[/COLOR]
This will open the interfaces file
Add the following to the end of the file. Be sure to add your port  number (eth?)
[COLOR=Red][I]auto eth0
iface eth0 inet dhcp[/I][/COLOR]

[COLOR=Red]*sudo ifup eth0*[/COLOR]
This will enable the settings

This is a small information I got from the help and support in Ubuntu  10.04. I was able to connect to Internet with the help of these  commands. Please try it . I'm sorry if this doesn't solve your problem.  I'm a newbie to ubuntu 10.04.

Thank you all :smile:

---

### Post by Spackledorf on 2010-06-08
Hi. I just installed Ubuntu Studio 10.4 because I lost my patience with Vista and am new to Linux. I'm having the same exact problems that are being described here, but I can't seem to get to the Grub Boot Loader. I Google image-searched it to make sure. I can get to a blue box that asks if I want to boot from the hard disk or CD/DVD but there is no Recovery Mode or Net Root as smexydiggz referred to. I feel like such a baby. Any help?

---

### Post by MIJ-VI on 2010-06-09
> **Spackledorf said:**
> Hi. I just installed Ubuntu Studio 10.4 because I lost my patience with Vista and am new to Linux. I'm having the same exact problems that are being described here, but I can't seem to get to the Grub Boot Loader. I Google image-searched it to make sure. I can get to a blue box that asks if I want to boot from the hard disk or CD/DVD but there is no Recovery Mode or Net Root as smexydiggz referred to. I feel like such a baby. Any help?

Hi Spackledorf.

What's the make and model # of your PC?

Which version of Ubuntu Studio 10.04? 32 bit? 64 bit?

Did you back up your personal files before attempting to install '10.04?

Did you follow an Ubuntu Studio 10.04 installation procedure similar to that which Falko Timme outlined in his "**[The Perfect Desktop - Ubuntu Studio 10.04]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-10.04")**" tutorial?

--------

BTW. Due to Ubuntu Studio 10.04 not yet having a real time kernel, and due to problems installing supplemental files from its install DVD, IMO Ubuntu Studio 9.10 is a better release save for one installation glitch whose workaround is described here:[B]

[[FONT=Garamond]HOW TO INSTALL UBUNTU STUDIO 9.10 WITHOUT HAVING THE INSTALL #%$&%# FAIL!:[/FONT]]("http://www.talkbass.com/forum/showthread.php?t=599271")
[/B]

---

### Post by cchhrriiss121212 on 2010-06-09
To get to grub, you can press shift before the OS loads. You can also download a program called startup manager from software centre that will allow you to set whether grub shows and how long for.

---

### Post by tnasty on 2010-08-13
PROBLEM FIX (for me at least)

I tried to follow [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") 's first post (2nd post overall) and I was not able to install the network manager applet from the boot disk because of dependency issues. However, I installed all packages I could under n in the boot disk that pertained to network, and then I went to the synaptic package manager and installed all the packages i could that had to do with network, and after a reboot, my wireless worked! I looked after and somewhere in this random installing I ended up installing the package [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") was talking about. I think maybe just going to synaptic and installing the package [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") mentioned alone would do the trick. Be sure to add the boot disk to the repositories in synaptic!

Cheers and thanks to all,

Mr. TNasty

---

### Post by Chembletek on 2011-05-31
> **crazyzenmaster said:**
> I have been reading the helpful comments of DonaldDock and cchhrriiss121212 and unfortunately I have the same problem (DCHP Connection error and cannot connect to the Internet). 

I have tried the suggested solutions here but could not find '/media/cdrom0/pool/main/n/network-manager-applet' within Ubuntu Studio 10.4 or Ubuntu 10.4 (lucid lynx) and even tried the installation disks for 9.10 (karmic koala).

I did find some .deb networking tools within /media/cdrom0/pool/main/n/ and installed them but still I cannot to the Internet. 

Unfortunately I am relatively new to Linux and of limited ability could DonaldDock show the process he used as I think we have the same issue?

Kind regards,
John
 
I'm getting this error too. And configuring DHCP during installation didn't work even when I was wired in. I really don't know what to do......

---

### Post by grahammechanical on 2011-05-31
Hi Chembletek

You have posted into a very old thread and it is marked as solved. This is not a good thing to do. You may not get any help. You can start a new thread with your own problem.

What version of Ubuntu Studio do you have installed? How are you trying to connect to the modem/router? By wireless or by ethernet? These things are important.

Version 11.04 of Ubuntu Studio now installs Network Manager. If you can install 11.04, then I would recommend that you do that.

If you are using 10.10 then try this:
> 
**Ubuntu Studio Internet**
**1)** Something is needed to indicate that an Internet or networking connection has been made. 

Right click the top panel and select Add to Panel. In the list presented by the dialog box select Network Monitor [Monitor network activity]. Click Add.

This action will put an icon of two connected monitors (screens) that will flash when there is network activity.

**2)** Setting up connections. Click on the Ubuntu Studio icon on the left of the top panel. Go to System>Administration>Network.

Do not go to System>Preferences>Network. It is the wrong type of network.

In the dialog box that appears select the Connections tab. Click the shield icon at the bottom and in the middle of the dialog box. It has "Click to make changes" alongside it.

Enter your login password. A list of available connections will appear. Select either Wireless Connection, Wired connection (eth1) or Wired connection (eth0) and click the Properties button.

For a Wireless connection put a tick mark against the box "Enable this connection". You may have to do this twice to get the tick mark to stick.

Make sure that the network name (ESSID) is the correct one.

Set the password type WPA Personal.

Enter the Network password. This is the wireless key or WPA-PSK key.

Set the configuration to Automatic configuration (DCHP) if that is the correct setting.

Enter if necessary the IP address, Subnet mask, Gateway address.

Click OK.

Click the make changes shield to prevent any further changes.

Click close and then reboot. Cross your fingers.

**Connection Properties wlan0**

Left or right click the Network Monitor icon.

A dialog will appear that will give the connection name, its status, an activity report (packets and Kilo bits received and sent) and signal strength. There is also a button to Configure the connection. Every time I click this button I get a Interface does not exist message even though there is an active connection.This is what I had to do to get a connection in 10.10 Ubuntu Studio. 

Regards.

---

### Post by Chembletek on 2011-05-31
11.04, but having problems with actually connecting. The help that comes with ubuntu would be straight forward if the netwrok debs on the cd worked. I have 0 access to the internet on that machine. trying to connect via wifi. I'll open a new discussion for this.

---


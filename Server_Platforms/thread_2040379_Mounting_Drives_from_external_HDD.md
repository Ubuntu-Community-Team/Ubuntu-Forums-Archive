---
title: "Mounting Drives from external HDD"
date: 2012-08-10
forum: Server Platforms
---

### Post by upalipsu on 2012-08-10
Hello everyone. I am a first time Ubuntu and Linux user, however I have a yearning to learn the art of machine talk. 

I would like to fist explain that I got so fed up with windows that I ran killdisk and clean installed Ubuntu 12.04. I don't plan on turning back. However, I am a traditional animation student attending college and have many files marooned on my Synology DS211+ external HDD. With windows I had run the Synology Assistant software packaged with the product, and it worked nicely. 

My goal is to get a version of FTP working that can stream and edit files to my laptop like the mounted normal drives on windows (without having to renter credentials on each login). 

Oddly enough, the fellows at Synology included a shell script in their Install Disk. 
[http://paste.ubuntu.com/1140403/](http://paste.ubuntu.com/1140403/)
... along with some instructions on how to install the assistant. 
[http://paste.ubuntu.com/1140404/](http://paste.ubuntu.com/1140404/)

I connected the device via Ethernet to the computer. A reoccurring notification tab on the right of the main screen heralds "Wired network (and directly below reads) Disconnected"

As I said before, I'm quite new to this (began learning about sed today) and have absolutely no idea what I'm doing. I've managed to ask around on the #Ubuntu-beginners IRC channel, yet nothing much came to light. When I ran the script in the terminal it opened and closed immediately.  I'd really appreciate a helping hand. Some of my main questions are: 

1)  Is the code provided by Synology for server versions of Linux? If so, is it possible to run this script in GUI? 

2)  If the Synology code offered is incompatible with a desktop version of Ubuntu 12.04, is it possible (and if so, how) to connect and map normal drives to the disk station with FileZilla? 

3) Will the files be accessible to a Ubuntu OS? 

Below are some additional details pertaining to the DiskDrive unit: 

IP Status: DHCP
RAID II 
Version:  3.1-1742


I wish my post could be more informative/clear. I'm still learning please bear with me.

---

### Post by clickwir on 2012-08-11
You don't have the NAS directly connected to your PC right? That needs to go through a switch first.

Also, I don't have a Synology, so I don't know what the assistant does... but it's probably not required. 

What you want to accomplish, is probably able to be done without installing extra things. I always suggest trying to do what you want without installing extra things. Like when people get a Verizon DSL CD or a Comcast CD, don't install that ****. There's nothing on there you need to get your system online.

---

### Post by rubylaser on 2012-08-11
Hello and welcome to Linux.  This is a little difficult for your first Linux task. Basically, you can set your Synology device up as a Network Share and automatically mount the share for you.  You'll just want to [enable NFS ]("http://forum.synology.com/wiki/index.php/How_to_enable_NFS_on_the_Synology_Server")on your Synology device.

And then set your machine to mount the NFS share automatically.
[https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client")

Please let me know if you need more info.

---

### Post by upalipsu on 2012-08-11
Thank you for your help :)
I have a few questions after reading over the[SIZE=2] [COLOR=DarkRed]"How to enable NFS on the Synology Server"[/COLOR][/SIZE] page. 

Currently the NAS is attached directly to the computer's ethernet port. 

[COLOR=DarkRed]"Please note that improper manipulation or modification of the Synology server may result in machine malfunction or loss of data. "[/COLOR]
-This line is a bit disconcerting to me currently. 

I'm wondering if the best way to go about this venture is to install WINE, or dare I suggest, a new version of windows on a partition of my laptop's HDD. This will allow me to install the synology assistant and change the settings to the NAS much easier (without the factor of a major screw up!).  

A few more inquiries:

[COLOR=DarkRed]"Telnet into the Synology product and perform the following [/COLOR]
 ** [COLOR=DarkRed]Enabling Service[/COLOR]**

 [COLOR=DarkRed]cd /usr/syno/etc/rc.d
 mv S83nfsd.sh.sample S83****.sh 
reboot (or /usr/syno/etc/rc.d/S83****.sh start)
 vi /etc/exports  

[/COLOR][COLOR=DarkRed]Note: * needs to be replaced with a number"[/COLOR]

[COLOR=DarkRed][COLOR=Black]Exactly what numbers am I looking to fit those examples?  
[/COLOR][/COLOR]
[COLOR=DarkRed][COLOR=Black]I believe that with some searching and reading the rest I can manage on my own. If I were to somehow screw it up, would the NAS still be accessible from windows, and the files unharmed? 
[/COLOR][/COLOR]
[COLOR=DarkRed][COLOR=Black]Perhaps I should try backing up the NAS, just to be safe![/COLOR][/COLOR]

---

### Post by clickwir on 2012-08-12
You need to connect the NAS to a switch and your PC to a switch. Unless you know how to setup static IPs for both, you will need to connect through a switch that also has something that's acting as a DHCP server.

You don't need WINE, you don't need the Synology Assistant. 

What you do need is your PC, NAS and something serving DHCP all to be connected to a switch. Until then, you won't get anywhere.

Once you have that done, you can scan and get the IP of the NAS (nmap). Then simply open a web browser (Firefox) and browse to that IP. Synology has a nice web interface, no special software needs to be installed (Assistant).

Now that you have those 2 things accomplished, you can start using the NAS.

Yes, Ubuntu will be able to see the files. What those files are and what program you'll need to open/use/access them with is a different story/thread.

---


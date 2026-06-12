---
title: "Server for the very first time"
date: 2010-10-31
forum: Server Platforms
---

### Post by amjjawad on 2010-10-31
Hi,

First of all, I hope this is the right place to post such a thread.
Second of all, the title of this thread said it all. I've never ever seen a server (unless I've never paid attention) nor used it in my entire life. Having that said, I think you know I'm level 0 when it comes to servers.

I start reading here:
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=lucida grande][LEFT][FONT=lucida grande][http://en.wikipedia.org/wiki/Server_](http://en.wikipedia.org/wiki/Server_)(computing)[/FONT]
[FONT=lucida grande] [/FONT]
[FONT=lucida grande][http://en.wikipedia.org/wiki/Home_server](http://en.wikipedia.org/wiki/Home_server)[/FONT]
[FONT=lucida grande] [/FONT]
[FONT=lucida grande][http://www.webmonkey.com/2010/02/set_up_a_home_server/](http://www.webmonkey.com/2010/02/set_up_a_home_server/)[/FONT]
[FONT=lucida grande] [/FONT]
[FONT=lucida grande][https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)[/FONT][/LEFT]
[/FONT][/COLOR][/LEFT][/FONT][/COLOR]
Also, I found two threads here which answered couple of questions I had.

[U][B]What I'm planning to do and why?
[/B][/U]1- Have a home server. I always had that idea of having one sever at home and connect all the other machines (PCs/Laptops) to that server.

2- Backup.

3- Sharing Files, Pictures, etc.

4- Connect to the interent through the home server. I live in a big house and we have only one ADSL Router/Modem. Obviously, I can't access the internet from any room unless I'm close to the router. The server will be in a place where I could connect to the interent even if I'm very far from the router.

5- I've never used Servers before so I'd like to try it now especially I started to use Linux and stopped using Windows and yes, I don't want to go back to Windows no matter what.

[U][B]My Hardware:
[/B][/U]In my signature, you can see some of my hardware but I'll list them here:

[LIST]
[*]MB - Gigabyte
[*]Intel P4 @3.00GHz
[*]2GB RAM
[*]500 SATA HDD
[*]LAN - Built in
[*]Wireless Adapter - D-Link
[*]ADSL Router - CableWireless (the brand name)
[*]Laptops - Not mine but will be connected to the server
[/LIST]
My current PC has 9 OS's installed (Multi-Boot System). 
Other laptops have Windows and I'm planning to use Linux on one of them which is PII with 64MB RAM and 4GB HDD.


_**My Questions:**_ Again, this is my first time so :)

1- Do I have to remove all the other 9 OS's and keep that PC solely for Ubuntu 10.04 32-bit Server? or it's OK to keep them? If yes, then shall I be able to boot into Ubuntu 10.04 Server after choosing it from GRUB2 Menu?

2- I read about Server Types but as mentioned above, my usages are limited and I don't need Web Server, Mail Server, etc. So, do I really need a Server (Ubuntu 10.04) OS to do that? or Ubuntu 10.04 Desktop Edition is up to this job?

3- I guess this should be the first Question. Do I need any particular skills to deal with Servers? or just general knowledge will be enough?
I believe in one thing. No matter how much you read about something and learn, the real experience or the practical experience is something else. When you do something by yourself, you will never forget it.

4- Probably this is same as Question #2. I'm very bad in CLI :( I know very few commands only and I know that GUI is disabled in Servers OS. How hard that could be for someone like me? I read a reply by a friend of mine (HermanAB) at one of the threads here. He said if someone wants to use GUI on a Server then it's better to use the Desktop Edition. Thing is, I'm very interested to try and use a server but as I mentioned, I'm very weak in CLI.

5- If Ubuntu 10.04 Desktop Edition could offer all the tasks I want (listed above) so what exactly do I need to know/learn?


That's all for now.

Please, make sure to simplify your answer as much as possible :)

THANK YOU :)

---

### Post by amjjawad on 2010-11-01
Anyone?

I think I posted this thread in the right place because it says "**Server Platforms**
 Discussion regarding the [Ubuntu Server Edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition")."

---

### Post by Ryan Dwyer on 2010-11-01
> **amjjawad said:**
> 1- Do I have to remove all the other 9 OS's and keep that PC solely for Ubuntu 10.04 32-bit Server? or it's OK to keep them? If yes, then shall I be able to boot into Ubuntu 10.04 Server after choosing it from GRUB2 Menu?

It's OK to keep them, but there's not much point if you're going to be using one operating system all the time. You may as well wipe them and use the space for storage. If you do keep them, you can configure Grub to load Ubuntu Server automatically.

> **amjjawad said:**
> 2- I read about Server Types but as mentioned above, my usages are limited and I don't need Web Server, Mail Server, etc. So, do I really need a Server (Ubuntu 10.04) OS to do that? or Ubuntu 10.04 Desktop Edition is up to this job?

I would still use the server edition, but desktop works too.

> **amjjawad said:**
> 3- I guess this should be the first Question. Do I need any particular skills to deal with Servers? or just general knowledge will be enough?

You need to know how to configure the services you want to use (such as file sharing and maybe DHCP/DNS). You can find how to configure each service using Google.

> **amjjawad said:**
> 4- Probably this is same as Question #2. I'm very bad in CLI :( I know very few commands only and I know that GUI is disabled in Servers OS. How hard that could be for someone like me? I read a reply by a friend of mine (HermanAB) at one of the threads here. He said if someone wants to use GUI on a Server then it's better to use the Desktop Edition. Thing is, I'm very interested to try and use a server but as I mentioned, I'm very weak in CLI.

The desktop is essentially the server edition with a GUI and minor tweaks. That's why you may as well install the desktop edition if you want a GUI. Using a GUI probably won't help you much either - you still have to configure services by editing config files.

You might be interested in Webmin - a web based tool to manage common services. It doesn't require a GUI on the server.

> **amjjawad said:**
> 5- If Ubuntu 10.04 Desktop Edition could offer all the tasks I want (listed above) so what exactly do I need to know/learn?

Use Samba for file sharing. Learn how DHCP and DNS works, then decide if you want your server to handle that. That'll keep you going for a while.

---

### Post by amjjawad on 2010-11-01
Thanks Ryan :)

I might use my current Desktop Edition for the time being and learn more about servers or I might install the server edition on another PC (a friend of mine will give me his PC as he's not using it anymore) and have some fun with totally new stuff.

---

### Post by drdos2006 on 2010-11-01
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by amjjawad on 2010-11-02
> **drdos2006 said:**
> Here is a HOWTO which I found comprehensive and invaluable.

regards

Thanks a lot :)

---

### Post by Drenriza on 2010-11-02
I remember when i had the same questions.

What i found out was, jump out into it. Wipe the HDD and install an ubuntu server edition.

You know, google is your friend.

> 1- Have a home server.

2- Backup.

3- Sharing Files, Pictures, etc.

4- Connect to the interent through the home server.
#1 what does a home server in your eyes do?
#2 make a script to make the backup using tar. And then scp it to the server in the correct backup folder. This can be added to cron to make it reguliar. (that is probably what i would do)
#3 [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
#4 Ask on the forum general help.

I'm not doing much atm, if you want more help pm me.

---

### Post by amjjawad on 2010-11-02
> **Drenriza said:**
> 
#1 what does a home server in your eyes do?

In my understanding or in a better word, what I need is few functions or tasks that can be done by a server. Actually, I know I don't have sophisticated tasks and whatever I need at the moment can be done by any PC but I've never worked on servers so I think it's time to do that :) 

> 
#2 make a script to make the backup using tar. And then scp it to the server in the correct backup folder. This can be added to cron to make it reguliar. (that is probably what i would do)

The backup that I want is for files only not for the system. Installing most of Linux Distributions or at least what I have doesn't take more than 10 minutes so I care about my files more than the file system.
I'm still very beginner when it comes to both CLI and scripts.

> 
#3 [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Thank you :)
I forgot to ask from the beginning. Do I need Samba to share files between Ubuntu and Ubuntu as well? or it's only between Ubuntu and Windows? sorry if this is very silly questions.

Thanks again but I prefer to discuss everything here so that others could benefit from this information as well.
I like this forum because I could discuss with people from the whole world. One of the things I love about Linux is its community.

---

### Post by Ryan Dwyer on 2010-11-02
For Windows, Samba is really on the only usable option. For sharing files Linux to Linux, you'd be better of using NFS or SSHFS (my favourite) as there's much less configuration involved.

---

### Post by amjjawad on 2010-11-02
> **Ryan Dwyer said:**
> For Windows, Samba is really on the only usable option. For sharing files Linux to Linux, you'd be better of using NFS or SSHFS (my favourite) as there's much less configuration involved.

Will remember that Ryan, thanks a lot :)

---

### Post by amjjawad on 2010-11-13
Hello again :)

Finally, I got the 2nd PC from my friend. It's in another room and connected to my main PC with a cable (LAN).

The main PC is connected to the internet via Wireless Network.
My 2nd PC is connected to the internet via Cable Network and that cable is connected to the main PC.

First of all, I was unable to connect to the Internet from PC2. I fixed that by:
a) From PC1: Network Connection > Wired > IPv4 Settings > Method: Shared to other computers.

b) From PC2: Network Connection > Wired > IPv4 Settings > Method: Automatic (DHCP).

After that, I managed to connect to both PCs and I have Internet access from both PCs.

I'm still very interested about the HOME SERVER idea but I thought it's better to work in GUI first before CLI.

[U][B]My NEW plan is:
[/B][/U]
PC1 (main): Pentium 4 - 2GB RAM - 500GB HDD
PC2 (secondary): Pentium 4 - 512MB RAM - 80GB HDD

PC1 is connected to the Internet via Wireless Network.
PC2 is connected to the Internet via PC1 through Cable Network.

[B][I]PC1 is supposed to be a HOME SERVER but with Ubuntu Desktop Version for now.
[/I][/B]
I'm planning now to use **Ubuntu 10.04 _Desktop Edition_ 32bit **as a Home Server to understand more concepts, services, etc before I go for [I][B]Server Edition.

[/B][/I]I still remember Ryan when he said:

> For sharing files Linux to Linux, you'd be better of using NFS or SSHFS  (my favourite) as there's much less configuration involved.

But I have few questions:

1- How exactly can I access PC2 from PC1 and vice versa? In another words, how can I access some files on the other PC?

2- How can I access PC2 remotely from PC1 and vice versa?

3- Is there any guide or link that could help me at this point?

4- Is there anything I must be aware of at this point?

5- One of the things I wanted from beginning is to use the Home Server as a storage device for my data. I guess I still can do that even with the desktop version of Ubuntu 10.04 on the main PC, right?

6- I installed Mint 9 on PC2 (it's so slow by the way :( ) and I'm planning to install Fedora and Ubuntu 10.10 as well. Is there any problems with that? is there anything I should know?

7- Is it a must to keep my partitions on PC1 auto mounted? after all, I'm not going to shut PC1 down and it should be ON all the time and of course as long as I have GUI so all the I/O devices are attached and working so in case I need to shut it down for any reason or restart it, I can mount it again but I'm just wondering whether mounting manually will make any difference?


That's all for now :)

Thanks in advance!

---

### Post by drdos2006 on 2010-11-13
Server software on one machine, client software on the other. For Ubuntu 9.10
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added /media/sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: 
Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles
mounted /media/sharedfiles from terminal with : 
sudo mount  <serverIPaddress>:/media/sdb1/sdb1-shared      /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

---

### Post by amjjawad on 2010-12-08
> **drdos2006 said:**
> Server software on one machine, client software on the other. For Ubuntu 9.10

Addendum:    On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName    
Added /media/sharedfiles on server with :    
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:    
sudo chgrp MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: 
Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles
mounted /media/sharedfiles from terminal with : 
sudo mount  <serverIPaddress>:/media/sdb1/sdb1-shared      /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

Hi again,
I've been busy lately and couldn't start anything. Now, I'm back to business and ready for it.

[COLOR=Black][B]I have two PCs ready:
a) [COLOR=DarkRed]_PC1 (Server)_[/COLOR] has Ubuntu 10.04 Desktop Edition.

b) [COLOR=DarkOrange]_PC2 (Client)_[/COLOR] also has Ubuntu 10.04 Desktop Edition. Both PC1 and PC2 has Windows XP.[/B][/COLOR]

I have a shared partition on PC1 - Type NTFS.

I tried to read what you posted but quite honestly I did not understand much :(

I have lots of questions in mind but not sure from where shall I start?!

[U][B]Part1
[/B][/U]While I was on the shared NTFS Partition on PC1 (Server), I did this:
1- Right Click
2- Properties
3- Share
4- Tick "Share this folder"
5- It asked me to install something (Samba) and I did

I understood that it asked me to install Samba because that partition is NTFS Partition.

I also installed NFS on PC1.

On PC2 (Client), I installed Samba but didn't install NFS yet.

Now, what exactly do I have to do?

[B][U]Part2
[/U][/B]&#1611;Why do I need to add groups? I created a group using this command:

```
sudo addgroup GROUPNAME
```

Also created a folder using:

```
sudo mkdir /media/*MYSHAREDPARTITION/FOLDERNAME*
```

But I don't understand what is that and why is that?

If I could just share the whole partition and access it from the other PC, why do I have to add groups, and stuff?

[U][B]Part3
[/B][/U]Is there a simple steps to follow? whether using GUI or CLI?

Thank you!

---

### Post by amjjawad on 2010-12-08
I'm reading [this]("http://nfs.sourceforge.net/nfs-howto/ar01s03.html") right now. Hope I could find ALL what I'm looking for.

---

### Post by amjjawad on 2010-12-08
> **amjjawad said:**
> I'm reading [this]("http://nfs.sourceforge.net/nfs-howto/ar01s03.html") right now. Hope I could find ALL what I'm looking for.

Okay, the first link (above) is a bit hard to understand. I found this:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I hope it's easier.

Guys, your suggestions and/or support is highly appreciated :)
I feel a bit lost.

---

### Post by amjjawad on 2010-12-09
Ok, enough is enough. I'm totally lost!

They say it's one line to add and everything is set then after few lines they say an attacker could attack my machine, bla bla bla so what's the deal here?
Did I move to Linux (because I heard it's more secured) to read such stuff?
Beside, it's NOT one line to be added, it's lots of stuff to install, configure, etc etc.

I totally understand that Linux is NOT Windows nor Windows is Linux but this is really too much. ALL what I want to do is:

PC1 can share files with PC2
PC2 can share files with PC1
NO ONE BUT ME could access both PCs
I DO NOT want to access my machines from somewhere else, it's a home server or in a better words, a HOME NETWORK (which I need 3-4 clicks in Windows to set). I don't need to create something huge, I just want to see my files on PC2 which is in another room while I'm on PC1 and vice versa.

Is that so hard? if yes, then I would simply use Windows XP with few clicks to do that BUT I DO NOT WANT THAT. I want to do it with Linux.

Yes, I know I'm very new and beginner to this but I didn't expect it to be so much hard like that.

I'm sorry if I look nervous and frustrated but I can't help it.

---

### Post by HugoSerrano on 2010-12-09
Install Ubuntu Desktop version, create a folder named share, right click on it, press "Sharing Option", mark "share this folder". This will install all the services needed, and start them. Done.

Go to the other PC, press Places -> Network. You should see your share there. In Windows, access the share as normal.

If you only got Linux, install openssh-server in both, then you can do:
Places -> Connect to server... Choose ssh, place the IP, username. (bookmark it or not, its the difference to keep it between boots, or not). Press Connect, it will ask a password, and the time to keep it. Choose what you need.




Only users in that system can access the share.

---

### Post by amjjawad on 2010-12-10
Thanks everyone. Apparently, this is not helpful anymore.
I'm going to do it myself on my way.

Thanks a lot for everyone.

P.S.
No, this is not a SOLVED thread and if there's any admin online, I appreciate if he/she would close this thread. I'll start another one in case I need that.

---


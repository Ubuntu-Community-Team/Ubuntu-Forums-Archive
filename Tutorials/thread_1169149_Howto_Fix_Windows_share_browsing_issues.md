---
title: "Howto: Fix Windows share browsing issues"
date: 2009-05-24
forum: Tutorials
---

### Post by dmizer on 2009-05-24
Howto: Fix Windows share browsing issues

First of all, even though it&#8217;s more difficult, manually mounting shares via /etc/fstab gives many advantages including faster speeds, more reliability, and larger file transfer sizes. It is more difficult to get things working properly, but once it&#8217;s done you never have to think about it again. So, if you&#8217;re willing to put forth a bit of effort for greater rewards than this tutorial will provide, please see the second link in my signature.

Windows share browsing issues are somewhat complex in that even though your symptoms are exactly the same, the causes can be extremely different. In this howto, I will outline the five primary reasons for the problem, and provide fixes for each. Once you're finished, you should be able to browse and connect to Windows shares by clicking on "places" > "connect to server".

That said, most problems are related to hostname resolution across the network. It's important to be aware that network name resolution can be a complex and daunting task to tackle and understand. The following outlines one way of potentially fixing this problem, but there are plenty of other techniques that work just as well or better depending on your network configuration. Here is a good example: [http://ubuntuforums.org/showthread.php?t=1781455](http://ubuntuforums.org/showthread.php?t=1781455)

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 1:**[/SIZE]
Ubuntu sometimes has trouble browsing shares in workgroups that it is not a member of. It can help if you make sure that all the computers in your network belong to the same workgroup. However, even if this is not a problem it's not a bad idea (unless you have reason to do otherwise) to have your workgroup homogeneous because it can ease the difficulty of troubleshooting.

By default, Ubuntu is a member of the &#8220;WORKGROUP&#8221; workgroup, but not all Windows computers use this convention. In order to correct this problem, you&#8217;ll need to verify that all your Windows computers belong to the same workgroup. In order to check/change that, please see this Microsoft support document: [http://support.microsoft.com/kb/295017](http://support.microsoft.com/kb/295017)

If you prefer to change Ubuntu's workgroup, please see "Problem 2".

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 2:** [/SIZE]
To fix this problem will require some editing of configuration files via CLI. There are easier ways to change the workgroup that Ubuntu belongs to, but many of these methods also tend to cause other problems.

The best and most reliable way to change Ubuntu's workgroup is by editing the /etc/samba/smb.conf file. This means that it may be easier to assign all of your Windows computers to the &#8220;WORKGROUP&#8221; workgroup (as outlined under "Problem 1"). Otherwise, use the following directions to edit /etc/samba/smb.conf in order to change the workgroup that Ubuntu is a member of.


***Problem 2 - part 1***
Open this file for editing with the following command:
```
gksudo gedit /etc/samba/smb.conf
```

Scroll down to the section that looks like this:
```
 #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]WORKGROUP[/COLOR]
```

Change &#8220;[COLOR="Red"]WORKGROUP[/COLOR]&#8221; in &#8220;workgroup = [COLOR="Red"]WORKGROUP[/COLOR]&#8221; to match your Windows workgroup.

***Problem 2 - part 2***
It may also help to add netbios name = [COLOR="Red"]computer-name[/COLOR] just below "workgroup = WORKGROUP".

Your "[COLOR="Red"]computer-name[/COLOR]" can be anything, but common convention is to use the name you gave it when you installed Ubuntu (everything after the "@" symbol on the CLI prompt).

For example, here's my CLI prompt:
```
dmizer@[COLOR="Red"]shinkansen[/COLOR]:~$
```
And here's my smb.conf file:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = [COLOR="Red"]shinkansen[/COLOR]
```

Now, save the file by clicking on "File" > "save", close gedit, and restart samba with the following command (Pre Jaunty):
```
sudo /etc/init.d/samba restart
```
If, after running the above command, you see this error (Since Jaunty):
```
sudo: /etc/init.d/samba: command not found
```
Use the following command (or reboot) instead:
```
sudo service smbd restart
```

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 3:**[/SIZE]
Ubuntu is unable to reliably browse Windows host names by default. Enabling this ability will also require a conf file edit.

[COLOR="Red"][B]---CAUTION---
If you are using Firestarter, uninstall it before making this edit. Firestarter may prevent the machine from booting after this change is made. Use GUFW instead.
---CAUTION---[/B]
[/COLOR]
***Problem 3 - Part 1***
Open /etc/nsswitch.conf for editing with the following command:
```
gksudo gedit /etc/nsswitch.conf
```
Find the line that looks something like:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
For this line, [order IS important](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15). You&#8217;ll need to add the &#8220;wins&#8221; option before dns, so the line reads like this:
```
 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Now, save the file by clicking on "File" > "save" and close gedit.

***Problem 3 - Part 2***
You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
```
sudo apt-get install winbind
```
Then, either restart networking or reboot.

***Problem 3 - Jaunty/Karmic***
Some Karmic users are reporting name resolution failure even after performing all the steps in this howto. If you have a local DNS server, do not perform this edit. Usually small home networks do not have a local DNS server but most office networks do. If you are unsure, talk to your office sysadmin. Either way, the following edit may solve some issues.

Open /etc/samba/smb.conf for editing with the following command:
```
gksudo gedit /etc/samba/smb.conf
```
Find the line that looks something like:
```
;   name resolve order = lmhosts host wins bcast
```
Just as with Problem 3 - Part 1, order is important when editing this line. You'll need to remove the [semicolon](http://en.wikipedia.org/wiki/Semicolon), and move "host" to the end of the line so that it looks like this:
```
   name resolve order = lmhosts wins bcast [COLOR="Red"]host[/COLOR]
```
[SIZE="1"]Bug report here: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)
Thanks to [audiomick](http://ubuntuforums.org/showpost.php?p=8180459&postcount=179) for this information.[/size]

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 4:**[/SIZE]
Firewalls block samba browsing. If you're sharing files over samba, that probably means you're on a LAN with only indirect (usually via a firewalled gateway/router) access to the Internet. This means that you probably don't need a firewall at all. If you think you DO need a firewall, you should really think about how wise it is to poke holes in it to facilitate samba file sharing.

If you simply must have a firewall and have decided that it's a good idea to allow samba access through it, start by checking all of your Windows computers to make sure that your firewalls allow Samba browsing. Also, since Jaunty, Ubuntu has enabled the UFW by default. This interferes with network browsing. Finally, if you&#8217;ve installed Firestarter or any other firewall tools, you may run into this problem. To correct this, you&#8217;ll need to add rules to allow the following ports:
[LIST]
[*]Port 137/UDP - used by nmbd
[*]Port 138/UDP - used by nmbd
[*]Port 139/TCP - used by smbd
[*]Port 445/TCP - used by smbd
[/LIST]

First of all, determine if you have a firewall in place or not. To check for firewalls, run the following command:
```
sudo iptables -L
```
A disabled firewall should look like this: [http://pastebin.com/f564e1a42](http://pastebin.com/f564e1a42). If not, then you have a firewall enabled.

If the UFW is enabled, here&#8217;s how to add UFW rules for samba browsing in Jaunty:
```
sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24
```
Make sure to change 192.168.29.0/24 so that it matches your own network IP range.

[SIZE="1"]Credit for the UFW edit goes here: [http://ubuntuforums.org/showthread.php?t=1225549](http://ubuntuforums.org/showthread.php?t=1225549)[/SIZE]

If you're using firestarter, uninstall it. The default firewall in Jaunty is UFW, you can manage it via it's GUI interface by installing gufw.

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 5:**[/SIZE]
While sometimes share browsing problems can be caused by Ubuntu, some browsing problems are caused by the Windows machines on your network. Even if you cannot browse from Ubuntu but you can browse shares between Windows machines, the problem can still be a misconfiguration on your Windows computer.

Here are three common problems with the configuration of your Windows computers.

***UAC drive protection:***
If your trying to connect to Vista or Win7, you may not be able to connect to any UAC protected drive/directory. Because of this, sharing entire drives will not give you access (unlike it did in XP). Believe me when I say ... this is a very good thing. You don't want your entire system hanging out there for all to see. It's possible to override this protection but I wouldn't advise it.

Instead, share a single folder that your Vista user has control over (double check permissions). If you want an entire drive to be dedicated to sharing, then share the first folder on the drive and put everything else inside it like so:

D:/ddrive-shared/Music
D:/ddrive-shared/Movies
D:/ddrive-shared/Pictures
D:/ddrive-shared/Documents
D:/ddrive-shared/Other
etc 

More information here: [http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)
Related Ubuntu discussion here: [http://ubuntuforums.org/showthread.php?t=1176221](http://ubuntuforums.org/showthread.php?t=1176221)

***Windows 7 configuration:***
First of all, remove Windows Live ID Sign-in assistant if you have it installed. More information here: [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

Windows 7 seems to be bent on wanting you to use "HomeGroup" file sharing, but this will not work with Samba, it will only work with other Windows 7 computers, and you're probably better off disabling it if you need things to work correctly in a mixed network.

In order to get simple file sharing to work, you'll need to click on the "Change advanced sharing settings", and make sure you have network discovery, file and printer sharing, and public folder sharing enabled in the "home or work" profile (also, make sure that "home or work" is labeled as your current profile). You should be able to use 128 bit encryption, and use either enable or disable password protected shares (depending on how much security you desire).

Then, go to "Change adapter settings", right click on your connection and select "properties". Click on the "Internet protocol version 4 (tcp/ipv4)" and select "properties". Then click on "advanced ..." (at the bottom), and select the "WINS" tab. Make sure that "Enable LMHOSTS lookup" is enabled (no need to import), and make sure that "default" is selected for NetBIOS setting.

Now, go to a folder (try the public folder first), and right click on it. Select "properties", and click on the "sharing" tab. Click on "Advanced sharing", and put a check mark in "Share this folder". Change the "share name" if you like, and click on the "permissions" button. Make sure you have permissions set as you desire (a checkmark in "change" = writeable). If you've enabled password protected shares, you'll have to tweak settings here to make sure that your Ubuntu user is included for permission.

In some situations, you will find it necessary to add your Ubuntu username and password as an account on your Win7 machine. This may seem tedious, but that's the way secure Samba servers work.

Once this is all set, then your folder will show "shared" and it's network path will be displayed.

***Failed to retrieve share list from server:***
If you have addressed all of the above fixes and you still get the "Unable to mount location: Failed to retrieve share list from server" error message when trying to browse your network, this may be related to Windows "Event ID 2011".

Please see the fix noted here: [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)
[SIZE="1"]Huge thanks to [mickeythemoke]("http://ubuntuforums.org/showpost.php?p=10405454&postcount=490") for finding this.[/SIZE]

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

If you have addressed all of the above issues, and you are still unable to browse Windows shares, you may have more luck and better results by following the CIFS tutorial in my sig. Otherwise, feel free to post here and I'll do what I can to help resolve the problem.

------
version history:
[SIZE="1"]2009-06-04: Included Vista specific information
2009-06-20: Updated UFW configuration
2009-06-25: Included directions for verifying firewalls
2009-07-29: Changed UFW firewall rules to reflect findings given in this thread: [s][http://ubuntuforums.org/showthread.php?t=1225549](http://ubuntuforums.org/showthread.php?t=1225549)[/s](incorrect)
2009-08-05: Removed name resolve order edit from problem 2 as it could possibly conflict with the winbind daemon.
2009-08-20: Corrected UFW rules per this post: [http://ubuntuforums.org/showpost.php?p=7811922&postcount=133](http://ubuntuforums.org/showpost.php?p=7811922&postcount=133)
2009-10-29: Included "name resolve order" option edit per this post: [url]http://ubuntuforums.org/showpost.php?p=8180459&postcount=179
2010-01-02: Updated firewall section to add reasoning for avoiding them, and caution against poking holes through them if they are needed.[/url]
2010-02-03: Added Windows 7 configuration instructions
2010-02-10: Added information regarding Windows Live ID Sign-in assistant.
2010-02-25: Added more Win7 specific information regarding user accounts.
2010-08-14: Removed wording which indicated that it was necessary to have all computers in the network under the same workgroup.
2010-08-30: Updated samba restart command to include the service command used since Jaunty.
2011-02-11: Added fix for "failed to retrieve share list from server" per this post: [http://ubuntuforums.org/showpost.php?p=10405454&postcount=490](http://ubuntuforums.org/showpost.php?p=10405454&postcount=490)
2011-06-24: Updated the introduction to mention and include alternative solutions.
[/size]

---

### Post by Mosaab on 2009-05-26
I had this line before:

files mdns4_minimal [NOTFOUND=return] wins dns mdns4

and I changed it to:

files wins dns

what does this mean: mdns4_minimal [NOTFOUND=return] ?

---

### Post by dmizer on 2009-05-26
> **Mosaab said:**
> I had this line before:

files mdns4_minimal [NOTFOUND=return] wins dns mdns4

and I changed it to:

files wins dns

what does this mean: mdns4_minimal [NOTFOUND=return] ?

mdns4_minimal would be used if you had a local DNS server. [NOTFOUND=return] causes your computer to check twice before moving on. Neither of these options are really necessary.

---

### Post by Mosaab on 2009-05-27
ah .. it seems when I was learning how to use bind .. it added this to the file.

---

### Post by glave on 2009-05-27
I've followed all suggestion to the letter, but I'm still getting the same 'Failed to retrieve share list from server' error when I go to network.

Wins was missing from nsswitch.conf, I had to uncomment the one line in smb.conf, all of my machines are indeed in the same workgroup, winbind was already installed. I rebooted also after all instructions were complete.

My windows machines can see EVERY machine on the network just fine, doing findsmb, my jaunty machine sees itself, another jaunty, and a hardy machine.

If I got to location, and enter smb://hostname OR smb://ip_address, then it works perfectly, I just cannot browse the network.

---

### Post by dmizer on 2009-05-27
What about UFW?

Or another firewall configuration perhaps? Please post the output of:
```
sudo iptables -L
```

---

### Post by glave on 2009-05-27
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Sorry, forgot that. No firewall running.

And just for good measure:

```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
192.168.168.11  ARCADE         [GRUMPUS] [Unix] [Samba 3.2.3]
192.168.168.13  PENGO          [GRUMPUS] [Unix] [Samba 3.3.2]
192.168.168.137 JOUST         +[GRUMPUS] [Unix] [Samba 3.3.2]

```


Pengo is the computer I'm having the issue with (Jaunty), and it exists also for Joust (Jaunty). Arcade is running unraid which is based off slackware.

---

### Post by dmizer on 2009-05-27
How many Linux samba servers do you have on your LAN? Did you manually configure them by editing /etc/samba/smb.conf?

---

### Post by glave on 2009-05-27
Three total. Two are hand edited, purely changing the workgroup option to match the correct workgroup, and the name resolve line. The 3rd is an unraid server, and it was configured through its interface.

---

### Post by dmizer on 2009-05-27
Please attach (as .txt documents) the smb.conf files of pengo and joust.

Edit:
I'm off to bed (it's 1:30am). I'll pick this up again tomorrow.

---

### Post by glave on 2009-05-27
Done.

---

### Post by dmizer on 2009-05-27
In pengo, one problem may be this line "wins support = true". Please remove that as it doesn't do what you think it does. Please see: man smb.conf for more information on why.

Also in pengo, comment or delete this line: "/var/lib/samba -s /bin/false %u"

In joust, you'll need to add two lines.
1) name resolve order = lmhosts host wins bcast
2) netbios name = JOUST

I think there are other problems as well, but before doing too much editing I'd like to learn a bit more about why you configured these they way you did, since they're quite different. What are you wanting to do with these shares?

---

### Post by glave on 2009-05-28
Pengo is working now and can browse. Pengo was the main focus, but I'll double check all steps on Joust and post results.


The wild difference in the 2 are pretty simple, Joust was 100% hand written, and Pengo was originally from webmin. Joust isn't actually sharing or mounting anything at all, and only has samba running purely for the purpose of populating itself into the workgroup when browsing it. No real purpose other than an easy to see 'head count' when I browse shares.

Pengo will have shares soon enough, and will be mounting some other shares. Its config file is overly complicated(as I see now) so I will be trimming it down soon enough.

---

### Post by dmizer on 2009-05-28
> **glave said:**
> Pengo is working now and can browse.
Fantastic. I'll look forward to hearing about Joust now. :)

---

### Post by glave on 2009-05-28
Joust is now working as well. I hadn't completed the nsswitch.conf step on Joust.

Kudos on the help, its much appreciated. Is there a single underlying change in Jaunty that caused this to happen? I know absolutely that under Hardy and Ibex I didn't have these issues.

---

### Post by dmizer on 2009-05-28
> **glave said:**
> Joust is now working as well. I hadn't completed the nsswitch.conf step on Joust.

Kudos on the help, its much appreciated. Is there a single underlying change in Jaunty that caused this to happen? I know absolutely that under Hardy and Ibex I didn't have these issues.

Glad it's working!

The first post in this thread is the accumulated knowledge of suffering through it myself, as well as helping people with this problem for almost 3 years now, so ... no, it's not a recent development. You've just been lucky I think.

Here's one from 2007 for example: [http://ubuntuforums.org/showthread.php?t=483352](http://ubuntuforums.org/showthread.php?t=483352)

---

### Post by lavinog on 2009-05-31
> **dmizer said:**
> mdns4_minimal would be used if you had a local DNS server. 
I thought the mdns was for the avahi daemon (which used to be installed by default). It allowed name resolution in the .local domain
I could be wrong though, but it is what I always thought.

---

### Post by dmizer on 2009-05-31
> **lavinog said:**
> I thought the mdns was for the avahi daemon (which used to be installed by default). It allowed name resolution in the .local domain
I could be wrong though, but it is what I always thought.

You're quite right. It's for zero conf networking: [http://en.wikipedia.org/wiki/Zeroconf](http://en.wikipedia.org/wiki/Zeroconf)

I stand corrected.

---

### Post by fantom1979 on 2009-06-01
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=77219")Dmizer,

I was having the same problem, but after following the steps in your first post, everything is working great now.  I am a Ubuntu noob and I just wanted to say thanks for putting that info together.

---

### Post by TheMussulman on 2009-06-02
Thanks dmizer :D
My ubuntu works correctly now!!

:popcorn:

---

### Post by jhamric on 2009-06-04
The problem I'm having is that I can see one of my network Vista shares but I cannot write to it ("Create Folder/Create Document" are greyed out in File Browser). Also, drilling deeper than one folder displays no files. Strangely, I have another Vista share on the same computer that allows writing just fine. Both mount at boot-up and both have the same entry in fstab (except for the mount share name, of course!). I've tried changing permissions as root, but they don't seem to help.](*,)
 
I also cannot seem to get winbind to install on Jaunty. Rather, it seems to install, then hangs on "Starting winbind daemon" in Terminal. On reboot, the system hangs after loading the samba daemons. If I remove winbind, it  boots normally.

Any help gratefully accepted!

---

### Post by dmizer on 2009-06-04
Regarding the Vista share which you are unable to access, did you review the Vista specific information in the first post regarding UAC drives and directories? Is the folder you're trying to share owned by your Vista user or is it UAC protected?

I'm not too sure what could be causing winbind to fail. Are you on a static IP or DHCP? If you're using DHCP, See if you can find anything in the logs:
```
cat /var/log/daemon.log | grep winbind
cat /var/log/dmesg | grep winbind
cat /var/log/messages | grep winbind
cat /var/log/syslog | grep winbind
```

Also, please post the contents of the following config files:
/etc/nsswitch.conf
/etc/samba/smb.conf

---

### Post by tommy13 on 2009-06-05
Hi,
I tried all the above, but with no success. 
When I go to places->Network I see only Windows Network, while there are also other linux shared folders on the network.
When I click on Windows Network, same error appears: "Unable to mount location Failed to retrieve share list from server".
Also tried smb://192.168.0.x/shared_folder, but no luck again with error "Cannot display smb://192.168.0.x/shared_folder".
Any help would be appreciated.

---

### Post by radiot on 2009-06-05
Hello, and thanks for the helpful tutorial.  

I have a new dell mini 12 with Ubuntu 8.04 and a dual boot dual opteron running 32bit Ubuntu 9.04 and Window$. I have spent the past 36 hours attempting network them. THey are connected through a Linksys router.   I confess to being an idiot, but I have set up home networks before with Samba, Window$, and various flavors of Ubuntu. This time I am out of ideas.

Dell does not see workgroup when Opteron running Ubuntu. When I click " network servers" in left pane of Nautilus, it shows Windows Network in right pane. When I click Windows Network it thinks for a second and shows empty pane. It does (when properly configured) see workgroup when opteron running window$. Furthermore dell can access windows shares.   (properly configured means uncommenting out ";   name resolve order = lmhosts host wins bcast".) The windows machine cannot access the dell. When samba was installed on dell, as opposed to just smbfs, the window$ machine could see dell in network but not access its available shared folders. When just smbfs windows only sees itself in workgroup.

When opteron is running Ubuntu 9.04 and I click "Network" in Nautilus it shows  "Windows network, 0 bytes" in right hand pane, and when "Windows Network" is clicked it says "Unable to mount location. Failed to retrieve share list from server"

I tried solutions to problems 1, all combinations of problem 2, and problem 4.  When I opened nsswich.conf the file was blank.

First I installed Samba on both machines, then smbfs on both, then uninstalled Samba on both, then reinstalled Samba on Opteron, since that is the 'dominant' machine. 

I have firestarter installed and properly configured on dell (and similarly configured on opteron) - it can access windows with firewall active, but in an effort to limit my difficulties I have been mostly working with firestarter turned off. 

Question: as a matter of pride I would like to resolve this with samba, but am tempted to try nss, but why can dell see windows and not windows see dell?  Why does dell see windows and not Ubuntu 9.04? Why is  
nsswitch.conf blank? And finally, ideas how to get these two devils to see and talk to one another. 

Thanks in advance, sincerely.

---

### Post by jhamric on 2009-06-05
> **dmizer said:**
> Regarding the Vista share which you are unable to access, did you review the Vista specific information in the first post regarding UAC drives and directories? Is the folder you're trying to share owned by your Vista user or is it UAC protected?

I'm not too sure what could be causing winbind to fail. Are you on a static IP or DHCP? If you're using DHCP, See if you can find anything in the logs:
```
cat /var/log/daemon.log | grep winbind
cat /var/log/dmesg | grep winbind
cat /var/log/messages | grep winbind
cat /var/log/syslog | grep winbind
```

Also, please post the contents of the following config files:
/etc/nsswitch.conf
/etc/samba/smb.conf

UAC on Vista is disabled and has been for some time. I was able to write to the partition under Intrepid. I use DHCP, but I have the router set to assign a static IP based on MAC address. There are no messages relating to winbind that show up when the cat commands are entered.

Here are the nsswitch.conf files: 

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

And for smb.conf:

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = Zebedee
	netbios name = Pern-Ubuntu

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
	wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = hosts wins bcast lmhosts host 

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
	interfaces = 127.0.0.0/8 eth0 wlan0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
	bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.

#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = no

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;	load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
	printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Barsoom_Data]
	comment = Data on Desktop
	path = /media/Barsoom_Data
	writeable = yes
	browseable = yes
	guest ok = yes

[Barsoom_Media]
	comment = Media on Desktop
	path = /media/Barsoom_Media
	writeable = yes
	browseable = yes
	guest ok = yes
```

In addition, here are the relevent lines from fstab:

```
//192.168.1.2/Data /media/Barsoom_Data cifs guest,rw,exec,_netdev,gid=1000,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.2/Media /media/Barsoom_Media cifs guest,rw,exec,_netdev,gid=1000,uid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Thanks for your help.

---

### Post by cor2y on 2009-06-05
Thank you very much dmizer for the tutorial

---

### Post by dmizer on 2009-06-05
> **radiot said:**
> When I opened nsswich.conf the file was blank.

The answer to all your problems lies in the answer to the above problem.

You probably entered the command incorrectly. This file is never blank.

---

### Post by dmizer on 2009-06-05
I didn't see anything glaringly wrong with anything you posted.

> **jhamric said:**
> There are no messages relating to winbind that show up when the cat commands are entered.

Okay, I found the right log. Please try restarting winbind:
```
sudo /etc/init.d/winbind restart
```

Then post the contents of:
```
/var/log/samba/log.winbindd
```

---

### Post by radiot on 2009-06-07
Hello All,

Thank you for the help Dmizer.

I edited smb.conf and nsswitch.conf to match jhamric's, restarted samba  and winbind, but with similar problems. dell's nautilus locations says "smb:///" and opteron shows workgroup (an improvement) but when workgroup clicked, "unable to mount location - failed to retrieve share list from server". Here is the log.windbindd

```
[2009/06/05 17:29:13,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 17:29:13,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/05 17:36:06,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 17:36:06,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/05 19:07:50,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 19:07:50,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/05 19:10:03,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 19:10:04,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/05 19:48:58,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 19:48:58,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/05 19:56:26,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/05 19:56:26,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/06 20:16:36,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/06 20:16:36,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/07 00:13:43,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/07 00:13:43,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/07 12:00:34,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/07 12:00:34,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/06/07 12:29:41,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/06/07 12:29:41,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2577)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
```

---

### Post by radiot on 2009-06-07
After previous post I restarted both machines, and both failed to boot properly.  I had this same problem earlier tinkering with smb.conf and nsswithc.conf.  

Opteron (9.04) fails to boot to login screen, and it goes to detail screen where it shows firestarter FAIL's to start, and it hangs starting samba daemons. 

Dell (8.04) boots through login screen but between login and desktop error appears: "Internal Error, failed to initialize HAL".  I edited smb.conf to fix HAL issue but same error on reboot. I changed nsswitch.conf back to (below) and machine booted normally:

```
hosts:          files mdns4_minimal [NOTFOUND=return]  dns mdns4
```

Getting back into Opteron more tricky. I used live cd to get into machine and edited  nsswitch.conf and rebooted as normal.

---

### Post by ratcheer on 2009-06-07
I am having a lot of trouble setting this up. I want to be able to access a shared directory on a Win XP host. I have tried to follow all the instructions in the original post of this thread, but it still does not work. I can locate the Windows workgroup in the Network Places app, but when I try to open it is says it cannot find the list of shared directories.

The Op had this: "Firewalls block Samba browsing. Check all of your Windows computers to make sure that your firewalls allow Samba browsing." How exactly is that done? I am running the ZoneAlarm firewall on my XP host.

Thanks,
Tim

---

### Post by ratcheer on 2009-06-07
Never mind the previous post. I feel so stupid. I re-booted my Ubuntu host, now the filesharing works, perfectly.

Thank you very much for a great tutorial!

Tim

---

### Post by dmizer on 2009-06-07
> **radiot said:**
> After previous post I restarted both machines, and both failed to boot properly.  I had this same problem earlier tinkering with smb.conf and nsswithc.conf.  

Opteron (9.04) fails to boot to login screen, and it goes to detail screen where it shows firestarter FAIL's to start, and it hangs starting samba daemons. 

Dell (8.04) boots through login screen but between login and desktop error appears: "Internal Error, failed to initialize HAL".  I edited smb.conf to fix HAL issue but same error on reboot. I changed nsswitch.conf back to (below) and machine booted normally:

```
hosts:          files mdns4_minimal [NOTFOUND=return]  dns mdns4
```

Getting back into Opteron more tricky. I used live cd to get into machine and edited  nsswitch.conf and rebooted as normal.


Ah HA, Firestarter is the problem. Please remove it. If you need a firewall, use the default UFW instead. It has a nice GUI interface and all (GUFW).

If you remove Firestarter, everything should work fine.

---

### Post by dmizer on 2009-06-07
> **ratcheer said:**
> I am having a lot of trouble setting this up. I want to be able to access a shared directory on a Win XP host. I have tried to follow all the instructions in the original post of this thread, but it still does not work. I can locate the Windows workgroup in the Network Places app, but when I try to open it is says it cannot find the list of shared directories.

The Op had this: "Firewalls block Samba browsing. Check all of your Windows computers to make sure that your firewalls allow Samba browsing." How exactly is that done? I am running the ZoneAlarm firewall on my XP host.

Thanks,
Tim

For opening ports in Zone alarm: [http://www.bleepingcomputer.com/tutorials/tutorial128.html](http://www.bleepingcomputer.com/tutorials/tutorial128.html)

Double check to make sure that the XP firewall is disabled: [http://support.microsoft.com/kb/283673](http://support.microsoft.com/kb/283673)

---

### Post by mohd on 2009-06-08
Hey there , i've a strange problem 

am new to ubuntu *using 9.04* am connected with windows vista pc
i used to see it in my network folder .. and i could get in and copy the shared stuff

the last time i did , i right clicked on the other pc's icon on my ubuntu desktop and chose unmount .. now i can't see it anymore 

**note** i never installed 'samba'

---

### Post by dmizer on 2009-06-08
> **mohd said:**
> Hey there , i've a strange problem 

am new to ubuntu *using 9.04* am connected with windows vista pc
i used to see it in my network folder .. and i could get in and copy the shared stuff

the last time i did , i right clicked on the other pc's icon on my ubuntu desktop and chose unmount .. now i can't see it anymore 

**note** i never installed 'samba'

Have you followed all the tips in this howto?

---

### Post by mohd on 2009-06-08
> **dmizer said:**
> Have you followed all the tips in this howto?

I tried the tips as in problem 3 , but didn't work

---

### Post by jhamric on 2009-06-08
> **dmizer said:**
> I didn't see anything glaringly wrong with anything you posted.



Okay, I found the right log. Please try restarting winbind:
```
sudo /etc/init.d/winbind restart
```

Then post the contents of:
```
/var/log/samba/log.winbindd
```

log.windbindd is empty after restarting winbind. I don't understand how it can restart when I uninstalled it, though, since it prevented my system from starting up after installing it.

I have been able to overcome at least most of the problem. I deleted the directory; re-made it in a new directory in my home folder & assigned read-write permissions to all sub-directories/files. I still can't write to the parent directory (Barsoom_Data), though.

---

### Post by dmizer on 2009-06-08
> **jhamric said:**
> log.windbindd is empty after restarting winbind. I don't understand how it can restart when I uninstalled it, though, since it prevented my system from starting up after installing it.

I have been able to overcome at least most of the problem. I deleted the directory; re-made it in a new directory in my home folder & assigned read-write permissions to all sub-directories/files. I still can't write to the parent directory (Barsoom_Data), though.

First of all, Winbind did not prevent your computer from starting, Firestarter did.

Have you looked at the Vista specific information in the howto? I believe it's been updated since you saw it last.

Otherwise, I'm not sure I can offer much more help unless you remove Firestarter in favor of UFW, and reinstall Winbind.

---

### Post by dmizer on 2009-06-08
> **mohd said:**
> I tried the tips as in problem 3 , but didn't work

You'll need to follow the solutions provided in all four problems. You may also need to look at the Vista specific information.

---

### Post by jhamric on 2009-06-09
> **dmizer said:**
> First of all, Winbind did not prevent your computer from starting, Firestarter did.

Have you looked at the Vista specific information in the howto? I believe it's been updated since you saw it last.

Otherwise, I'm not sure I can offer much more help unless you remove Firestarter in favor of UFW, and reinstall Winbind.


As far as I know, Firestarter is not installed on my system. I find no link to it to suggest it's installed. And as I said, winbind freezes the system when trying to start; un-installing it allows a normal boot.

Yes, I have read the Vista how-to. As I mentioned originally, though, I have un-limited access to another share on the same computer with the same fstab commands. I have checked the security of my two shares in Vista against eaach other & I don't find any differences.

---

### Post by dmizer on 2009-06-09
> **jhamric said:**
> As far as I know, Firestarter is not installed on my system. I find no link to it to suggest it's installed. And as I said, winbind freezes the system when trying to start; un-installing it allows a normal boot.

Yes, I have read the Vista how-to. As I mentioned originally, though, I have un-limited access to another share on the same computer with the same fstab commands. I have checked the security of my two shares in Vista against eaach other & I don't find any differences.

My sincere apologies, it seems I got your problem confused with radiot.

I think the answer to your problem may lie in what's causing winbind to hang. There should be several older versions of the winbind log (eg: winbindd.1.gz, winbindd.2.gz), and the errors should appear in one of them.

Are your two different Vista computers installed with different versions of Vista? While chmodding the folder may have fixed the problem temporarily, it's unlikely to be a long term solution, as other computers write to the share, the permissions will change.

---

### Post by jhamric on 2009-06-10
> **dmizer said:**
> My sincere apologies, it seems I got your problem confused with radiot.

I think the answer to your problem may lie in what's causing winbind to hang. There should be several older versions of the winbind log (eg: winbindd.1.gz, winbindd.2.gz), and the errors should appear in one of them.

Are your two different Vista computers insta thatlled with different versions of Vista? While chmodding the folder may have fixed the problem temporarily, it's unlikely to be a long term solution, as other computers write to the share, the permissions will change.

log.winbindd.1 shows: 
[2009/06/04 21:09:11,  0] winbindd/winbindd.c:main(1125)
  winbindd version 3.3.2 started.

So I guess the process is starting. But why it freezes my system I don't get.

The Vista shares are on the same computer & there's only one version of Vista. The shares are just different partitions. I'm really the only one that routinely accesses the shares, especially from Ubuntu.

---

### Post by dmizer on 2009-06-10
> **jhamric said:**
> But why it freezes my system I don't get.
Are you using a wireless connection, and is it managed by network-manager?

> **jhamric said:**
> The Vista shares are on the same computer & there's only one version of Vista. The shares are just different partitions. I'm really the only one that routinely accesses the shares, especially from Ubuntu.

This is very likely just a small difference in configuration between the two shares. Probably permissions on the partitions themselves.

---

### Post by jhamric on 2009-06-11
> **dmizer said:**
> Are you using a wireless connection, and is it managed by network-manager?

Yes to both.

This is very likely just a small difference in configuration between the two shares. Probably permissions on the partitions themselves.

I've come to that conclusion, too. Damned if I can find the difference, though.:confused:

---

### Post by dmizer on 2009-06-11
I think that your system may be hanging as a result of network-manager, but the only way I can think of to test this theory would be to uninstall network-manager in favor of another tool like wicd or gnome-network-admin.

---

### Post by SergeantOreo on 2009-06-12
I'm having problems with Samba after enabling ufw, and I read through
the part pertaining to fixing it, but still have some issues pertaining to the correct commands..

You say to "Change 192.168.1.0 to match your own network", and so my local ip address is 192.168.0.106. Does this mean the command will go 

from:sudo ufw allow proto tcp to any port 135 from 192.168.1.0/24
to:sudo ufw allow proto tcp to any port 135 from 192.168.0.106/24

Cheers.

---

### Post by dmizer on 2009-06-12
> **SergeantOreo said:**
> Does this mean the command will go 

from:sudo ufw allow proto tcp to any port 135 from 192.168.1.0/24
to:sudo ufw allow proto tcp to any port 135 from 192.168.0.106/24

Cheers.

Not quite. It will be:
```
sudo ufw allow proto tcp to any port 135 from 192.168.0.**[COLOR="Red"]0[/COLOR]**/24
```
This essentially means that UFW will accept incoming connections from any computer with an IP address of 192.168.0.1 through 192.168.0.254

---

### Post by SergeantOreo on 2009-06-12
Dmizer: I just ran the commands with the address you listed, but samba still gives the error "Unable to mount location. Failed to retrieve share list from server." What should I do, short of disabling ufw?

Thanks.

---

### Post by dmizer on 2009-06-12
> **SergeantOreo said:**
> Dmizer: I just ran the commands with the address you listed, but samba still gives the error "Unable to mount location. Failed to retrieve share list from server." What should I do, short of disabling ufw?

Thanks.

Have you tried implementing the solutions to the other problems as well? If not, I suggest doing so.

---

### Post by SergeantOreo on 2009-06-13
I just followed the entire thread, and still have no results.. 
Perhaps I will have to disable ufw. :(

---

### Post by cyberjohn on 2009-06-15
First off, Thank You for the excellent instructions.  I did find that I had to turn UFW off altogether to be able to browse the windows shares.  
It is interesting that None of the remedies was necessary when I was connected to the network through a wired connection, I nedded the extra steps only when using the wireless adapter.

Now to my problem.  somewhere in this process, an icon appeared on my desktop that is labled  "my documents on john.volume"  where john is the name of a windows computer and my documents is a folder I have shared on it.  this cannot be opened, deleted, renamed or moved.  I does not appear in desktop when examined with explorer. 

Does anyone know what to do?? 
My machine is a Toshiba Satellite laptop, running Ubuntu 9.04 patched as of yesterday, with motorola wireless adapter

---

### Post by dmizer on 2009-06-15
> **SergeantOreo said:**
> I just followed the entire thread, and still have no results.. 
Perhaps I will have to disable ufw. :(
Do you have a serious need for a firewall? If you're connected to a router, usually that handles security well enough that you don't need a local firewall. Even in Windows, local firewalls don't do much other than offer peace-of-mind unless you have a direct connection to the internet.

Either way, disabling the firewall will help with troubleshooting.

> **cyberjohn said:**
> Does anyone know what to do?? 

Please post the output of:
```
ls -la Desktop
```

---

### Post by cyberjohn on 2009-06-15
total 12
drwxr-xr-x  2 johnp johnp 4096 2009-06-12 11:22 .
drwxr-xr-x 43 johnp johnp 4096 2009-06-15 16:14 ..
-rw-r--r--  1 johnp johnp  187 2009-06-10 12:21 Howto: Fix Windows share browsing issues - Ubuntu Forums.desktop

---

### Post by dmizer on 2009-06-15
cyberjohn, does it survive a reboot?

---

### Post by cyberjohn on 2009-06-15
> **Re: Howto: Fix Windows share browsing issues** 			
 			 			 		   		 		 		cyberjohn, does it survive a reboot?


Yes it does.  Is this wierd or what??

---

### Post by dmizer on 2009-06-15
Try this:
```
sudo ls -la Desktop
```

---

### Post by cyberjohn on 2009-06-15
johnp@toshlaptop:~$ sudo ls -la Desktop
[sudo] password for johnp: 
total 12
drwxr-xr-x  2 johnp johnp 4096 2009-06-12 11:22 .
drwxr-xr-x 43 johnp johnp 4096 2009-06-15 16:14 ..
-rw-r--r--  1 johnp johnp  187 2009-06-10 12:21 Howto: Fix Windows share browsing issues - Ubuntu Forums.desktop
johnp@toshlaptop:~$ 


no change.

---

### Post by dmizer on 2009-06-15
I suggest opening a new thread in the Desktop environments section: [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

---

### Post by cyberjohn on 2009-06-15
Thank you dmizer
> I suggest opening a new thread in the Desktop environments section: [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

I have done that

---

### Post by Fuitab on 2009-06-17
I'm sorry, I'm a super newb. I'm trying to access another computer's shared files on the network. I'm on problem 2 of your tut, the part that says:
```
sudo /etc/init.d/samba restart
```
I typed that in and it prints out
```
sudo: /etc/init.d/samba: command not found
```
What am I doing wrong?

---

### Post by dmizer on 2009-06-17
> **Fuitab said:**
> I'm sorry, I'm a super newb. I'm trying to access another computer's shared files on the network. I'm on problem 2 of your tut, the part that says:
```
sudo /etc/init.d/samba restart
```
I typed that in and it prints out
```
sudo: /etc/init.d/samba: command not found
```
What am I doing wrong?

It just means you probably don't have the samba package installed. You can do one of two things at this point, install samba:
```
sudo aptitude install samba
```
or try rebooting.

---

### Post by oc999 on 2009-06-23
I just wanted to add to your tutorial that it's actually easy to change the workgroup using webmin - it allows you to configure your samba server in firefox through GUI.
anyways i can't browse any network resources for some reason.. but it's not like in the tutorial .. just clicking on network gives me an error it's not like the shared folders don't appear or I can't access them .. I can't even open up network. is anyone expiriencing the same problem? 
I am using ubuntu 9.04 - all windows pcs can access my shared folders I set up with samba but I can't access the whole network - can't even browse myself (smb://[my pc name] )

---

### Post by dmizer on 2009-06-23
> **oc999 said:**
> I just wanted to add to your tutorial that it's actually easy to change the workgroup using webmin - it allows you to configure your samba server in firefox through GUI.
anyways i can't browse any network resources for some reason.. but it's not like in the tutorial .. just clicking on network gives me an error it's not like the shared folders don't appear or I can't access them .. I can't even open up network. is anyone expiriencing the same problem? 
I am using ubuntu 9.04 - all windows pcs can access my shared folders I set up with samba but I can't access the whole network - can't even browse myself (smb://[my pc name] )

Webmin is not supported in Ubuntu and may be the source of your problems. It also sounds like you may have a firewall misconfiguration. Can you post the output of:
```
sudo iptables -L
```

More information on Webmin: [https://answers.edge.launchpad.net/ubuntu/+question/2873](https://answers.edge.launchpad.net/ubuntu/+question/2873)

---

### Post by oc999 on 2009-06-23
ok I'll try deinstalling webmin .. I didn't know its not supported .. I watched a video-tutorial on setting up apache2 webserver & ftp on ubuntu and they used webmin so .. sorry .. my fault then

this is my result of *sudo iptables -L*
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

edit : deinstalled webmin - still the same problem - no network-browsing possible. is it possible that webmin caused damage I can't solve by deinstalling it ?

---

### Post by dmizer on 2009-06-24
There might be something funny in the /etc/samba/smb.conf file, doesn't look like there's a firewall interfering.

Try this:
```
sudo aptitude install samba smbfs
```

Then post the output of:
```
smbtree
```

---

### Post by oc999 on 2009-06-24
*smbtree*  gives me this :
```
OC999
    \\OC999                  oc999 server (Samba, Ubuntu)
        \\OC999\movies             
        \\OC999\mp3s               
        \\OC999\IPC$               IPC Service (oc999 server (Samba, Ubuntu))
        \\OC999\print$             Printer Drivers

```

---

### Post by juliet charley on 2009-06-24
Hi and thanks for all your help. I have followed your tutorial, and checked and rechecked all my typing, but when when I run sudo mount -a, I still get:

mount error 2 = No such file or directory

I know it I must be doing something wrong, but what? I really need to be able to see my Windows XP machine on my LAN. BTW, I am using 8.04 (since 9.04 didn't like my graphics adapter at all).

Thanks again,

---

### Post by dmizer on 2009-06-24
> **oc999 said:**
> *smbtree*  gives me this :
```
OC999
    \\OC999                  oc999 server (Samba, Ubuntu)
        \\OC999\movies             
        \\OC999\mp3s               
        \\OC999\IPC$               IPC Service (oc999 server (Samba, Ubuntu))
        \\OC999\print$             Printer Drivers

```

You said you get an error from simply clicking on a network resource. What is the exact phrasing of the error?

Open up a terminal and type:
```
nautilus
```
Then try to browse to your network share in nautilus (type smb://OC999/movies for example). Then if you still get an error, check the output in the terminal to see if it gives more information.

---

### Post by dmizer on 2009-06-24
> **juliet charley said:**
> Hi and thanks for all your help. I have followed your tutorial, and checked and rechecked all my typing, but when when I run sudo mount -a, I still get:

mount error 2 = No such file or directory

I know it I must be doing something wrong, but what? I really need to be able to see my Windows XP machine on my LAN. BTW, I am using 8.04 (since 9.04 didn't like my graphics adapter at all).

Thanks again,

It sounds like you're trying to mount via /etc/fstab? If you don't need to access the share via places > connect to server, then please see the 2nd link in my sig. That should help you resolve the above error.

If you still experience that problem, then please post in that tutorial rather than here.

---

### Post by oc999 on 2009-06-25
> Then try to browse to your network share in nautilus (type smb://OC999/movies for example). Then if you still get an error, check the output in the terminal to see if it gives more information.
thats what I tried , I'm not even sure if this is even a network related problem anymore .. its more like my nautilus is screwed up and won't work with smb:// commands ( neither with ftp ) because for some reason it adds /home/oc in front of it .. result is : 
> »/home/oc/smb:/OC999/movies« could not be found.same happens when I try to open a connection to an ftp ( [ftp://user@server.com:80](ftp://user@server.com:80) ) .. just adds my home directory to the line.
also when I click on places and then computer ... it tells me that computer places are not available ? 
do I have to reinstall ubuntu or do you have any advice on how to fix this problem ?

---

### Post by dmizer on 2009-06-25
Well, that's a first. Something is definitely not configured correctly. Though it's better to fix things rather than reinstalling, if reinstalling is an option for you, then it might be quicker than trying to figure out what's wrong (I don't know).

Otherwise, you can try opening a thread in the General section regarding your Nautilus issue.

---

### Post by oc999 on 2009-06-25
> Well, that's a first. Something is definitely not configured correctly. Though it's better to fix things rather than reinstalling, if reinstalling is an option for you, then it might be quicker than trying to figure out what's wrong (I don't know).

Otherwise, you can try opening a thread in the General section regarding your Nautilus issue. 	

I'll try asking in launchpad.net , if I don't get a solution there I'll have to reinstal,l but anyways thanks for trying and aslso thanks for the tutorial!

---

### Post by Nevis on 2009-06-27
Great job on this topic! One note; I tried all the steps with no joy then tried a reboot (old Windows habit) and all of a sudden all was well!

I only wish now I had rebooted earlier. My problem was the "Unable to mount shares issue" and now I'm not sure exactly which step solved the problem. 

Regardless, thanks again!!

---

### Post by billswan on 2009-06-28
I double-checked that everything was as it ought to be according to your tutorial, opened up Thunar and lo and behold, all the machines were there (including one that I didn't realize was turned on). :-)  I was even able to browse through the shared directory in the test machine. :-) :-)

Then something went awry.  I tried moving up a level in Thunar and got a warning "Transport endpoint is not connected."  From that point on that's all I get.  It won't even display the workgroup.

Looking for solutions I saw this first: [http://threebit.net/mail-archive/samba/msg01516.html](http://threebit.net/mail-archive/samba/msg01516.html)
But as best as I can tell from Wireshark that's not the problem at all.

Then I saw this: [https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351)
I've seen symptoms of this before (the question marks in the directory listing, for example).
Somebody notes (2008-11-17) that Dmik's workaround works on Xubuntu 8.10 (which I am using). Noticed it was reversible so I thought I'd try the manual downgrade [https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351/comments/16](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351/comments/16))... but it tells me "Package not available in this suite." 
Okay, reading on there is discussion of libsmbclient not being thread safe, and
> please update SMBNetFS package to latest git version. It does not contain the bug described here due to libsmbclient isolation in separate process.Except that I do not have smbnetfs installed. ???

---

### Post by dmizer on 2009-06-28
billswan, I moved your post here since it relates to this tutorial and not the CIFS mount tutorial. :)

Does the problem persist after a reboot? Please post the output of:
```
smbtree
```

---

### Post by bdudek on 2009-06-29
> **billswan said:**
> I double-checked that everything was as it ought to be according to your tutorial, opened up Thunar and lo and behold, all the machines were there (including one that I didn't realize was turned on). :-)  I was even able to browse through the shared directory in the test machine. :-) :-)

Then something went awry.  I tried moving up a level in Thunar and got a warning "Transport endpoint is not connected."  From that point on that's all I get.  It won't even display the workgroup.

Looking for solutions I saw this first: [http://threebit.net/mail-archive/samba/msg01516.html](http://threebit.net/mail-archive/samba/msg01516.html)
But as best as I can tell from Wireshark that's not the problem at all.

Then I saw this: [https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351)
I've seen symptoms of this before (the question marks in the directory listing, for example).
Somebody notes (2008-11-17) that Dmik's workaround works on Xubuntu 8.10 (which I am using). Noticed it was reversible so I thought I'd try the manual downgrade [https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351/comments/16](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351/comments/16))... but it tells me "Package not available in this suite." 
Okay, reading on there is discussion of libsmbclient not being thread safe, and
Except that I do not have smbnetfs installed. ???




I had the same issues as many of the posts. I checked the differences between the 8.10 and 9.04 software loads and found that gvfs-backends was not loaded. I loaded it and that did not fix the problem. So I loaded the samba4 software. Now everything works fine for me. Try uninstalling ALL samba related software using synaptic. Then load these packages:

samba4-clients
samba4-common
libsmbclient0
libwbclient
nautilus-share
gvfs-backends

I used the maintainers smb.conf file when prompted. I also changed the Workgroup in the smb.conf file. That was the only change. Now I am able to connect to all my network shares (Linux and Windows). Hope this fix work for you too. Good luck.

Bruce Dudek

---

### Post by dmizer on 2009-06-29
> **bdudek said:**
> I used the maintainers smb.conf file when prompted. I also changed the Workgroup in the smb.conf file.

These two points are extremely important, and most likely what fixed your problem.

---

### Post by Dunkaz on 2009-07-17
Thanks dmizer ....
you have no idea the hours that I have spent trying to solve this issue with Ubuntu (and ALL the other distros) not able to see Windows shares, especially on a W2K system.

Solution 2 fixed it instantly.

This was almost to the stage of a deal breaker with Linux, I need the access to Windows unfortunately but want to move forward.

Linux in general for its capabilities on older equipment, (I've got lots of it :D )
I am running Ubuntu, Kubuntu, and Mint (all based on 9.04)
Drifting off-topic but Mint seems to be coming out top at the minute for me..

Thanks for the great solution.

D.

---

### Post by armagedonc on 2009-07-19
> **dmizer said:**
> billswan, I moved your post here since it relates to this tutorial and not the CIFS mount tutorial. :)

Does the problem persist after a reboot? Please post the output of:
```
smbtree
```

Hi, 
thanks for all your work

I have followed step by step the tutorial,and I can see the shared folder in vista and vista can print from my jaunty, but I can't see the files inside the shared folder in vista.It always show :'Failed to mount windows share'.

---

### Post by gordintoronto on 2009-07-20
Just a note: I installed Juanty on a blank hard drive, and immediately could browse shares on Windows XP computers on my wireless network.  Places/Network/Windows Network/(workgroupname)/(computer name)/(sharename), (lots of double-clicking) and I was looking at the file list.

The only thing non-standard was enabling "File and Printer sharing for Microsoft Networks" on the XP system.  Most specifically, I did not change the workgroup name in smb.conf to match the name of the Windows workgroup.  I run no firewalls, and do not have Samba installed.

I thought my experience was typical....

---

### Post by CBers on 2009-07-22
Remember to use the IP address of your PC rather than the PC name when connecting, unless you have addedd entries to the /etc/hosts file !!

Been sitting for half-an-hour going through this, then it dawned on me that my UBUNTU PC can't resolve the PC name !!

Used the IP address and it worked immediately. :D

---

### Post by dmizer on 2009-07-22
> **CBers said:**
> Remember to use the IP address of your PC rather than the PC name when connecting, unless you have addedd entries to the /etc/hosts file !!

Been sitting for half-an-hour going through this, then it dawned on me that my UBUNU PC can't resolve the PC name !!

Used the IP address and it worked immediately. :D

If you follow the directions listed on the first page under "Problem 3", your Ubuntu computer will be able to resolve host names.

---

### Post by CBers on 2009-07-23
That means installing winbind correct ?? How does winbind resolve names ??

Now that I can connect via IP address, I am more than happy.

Your main suggestions helped a lot.

I can't believe I'm finding UBUNTU so difficult, considering I work with enterprise unix (HP-UX) every day !!

Still not easy to find what the ubuntu (linux) equivalent to a windows apps is, such as Windows Live (MSN Messenger), Anti-Virus software, TCP Optimizer, disk de-fragger, BlueTooth etc.

Is there a page detailing this ??

I'm only really geting into ubuntu (linux) as I want to use VDPAU on my HTPC (ASRock ION-330).

Plus, if I like it (!!) I'll install on my other PCs/laptops etc.

---

### Post by dmizer on 2009-07-23
> **CBers said:**
> That means installing winbind correct ?? How does winbind resolve names ??

Now that I can connect via IP address, I am more than happy.

Your main suggestions helped a lot.

I can't believe I'm finding UBUNTU so difficult, considering I work with enterprise unix (HP-UX) every day !!

Still not easy to find what the ubuntu (linux) equivalent to a windows apps is, such as Windows Live (MSN Messenger), Anti-Virus software, TCP Optimizer, disk de-fragger, BlueTooth etc.

Is there a page detailing this ??

I'm only really geting into ubuntu (linux) as I want to use VDPAU on my HTPC (ASRock ION-330).

Plus, if I like it (!!) I'll install on my other PCs/laptops etc.

As indicated in the howto, Ubuntu is unable to resolve Windows host names, mostly because Windows uses a proprietary method for doing so. One of the many things that the winbind daemon is able to handle is the complexities of Windows name resolution for Linux clients. Winbind is indeed used for much more than just name resolution, but this is nothing to be concerned about unless you're trying to configure your Linux client to join a Windows domain with active directory. While I admit that the winbind daemon is probably overkill for this simple task, it functions quite well in a DHCP environment where servers and clients frequently change IP addresses.

When I first started using Linux, I was coming to the table with more than 25 years of experience with Windows (including MS-DOS). This was probably my biggest setback while learning Linux. I expected things to work in certain ways. Windows ways. And, when they didn't work as I was used to, I grew extremely frustrated. So, while Linux and Unix are closely related, and are compatible in many ways, they are not identical. But, you should have a shorter learning curve than I did.

As for the rest of your questions, they are outside the scope of this thread, but I'll leave you with this. Linux is not Windows, so don't expect to find something like: Linux-app-A == Windows-app-B. You should be looking for Linux applications according to task rather than trying to find Windows equivalents.

---

### Post by glave on 2009-07-25
Has something changed recently in any updates that could've rebroken things?

After several updates and a few reboots, I noticed that I can no longer browse my network at all again on both of my ubuntu machines I've previously fixed. >.<

---

### Post by BDNiner on 2009-07-25
Thanks dmizer for a great tutorial. I have a Linkstation NAS that I have been trying to connect to all day long. I do have one problem now, the only way that I can connect to the shares on the NAS is if i disable the firewall entirely. Are there some other ports that I need to open? I have opened the ports you specified in the tutorial.

And how would I add these entries to fstab so that they mount when I boot the computer?

---

### Post by dmizer on 2009-07-25
glave,

There have been some updates to samba. If you allowed the update to replace config files (specifically /etc/samba/smb.conf), you may have to take a look through this howto again to make sure all the settings are in place. Also, double check for firewalls.

> **BDNiner said:**
> And how would I add these entries to fstab so that they mount when I boot the computer?

If you are interested in mounting via /etc/fstab, then you won't need to worry about firewalls. Please see the 2nd link in my sig.

---

### Post by glave on 2009-07-26
Smb.conf hasn't changed for me, and firewall is disabled (verified via gui).

Smbclient sees my ubuntu shares still, but browsing the network gets the cannot mount error. I've re-verified everything checked when this first cropped up, but this time everything is still in place.

---

### Post by dmizer on 2009-07-26
> **glave said:**
> Smb.conf hasn't changed for me, and firewall is disabled (verified via gui).

Smbclient sees my ubuntu shares still, but browsing the network gets the cannot mount error. I've re-verified everything checked when this first cropped up, but this time everything is still in place.

Did you double check your Windows machines for their firewall configurations as well?

---

### Post by glave on 2009-07-26
Yes. No windows machines are using firewalls at all. The primary issue though is I can't browse the network at all. I don't even really want to access windows machines, just the unraid server.

I know I can mount the shares permanently via fstab, and I've done so in the past, but I'd still like to just get this annoyance fixed as well.

---

### Post by glave on 2009-07-26
Dmizer: Just so I could test, I followed the link in your sig ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and started from scratch.

The only settings I modified were the hostname and workgroup. This pc is on a static ip, so I left wins server alone. Browsing the network in nautilus still gives me the unable to mount error.

Again, no firewall, and this was working perfectly a short time ago.

---

### Post by dmizer on 2009-07-26
> **glave said:**
> Dmizer: Just so I could test, I followed the link in your sig ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and started from scratch.

The only settings I modified were the hostname and workgroup. This pc is on a static ip, so I left wins server alone. Browsing the network in nautilus still gives me the unable to mount error.

Again, no firewall, and this was working perfectly a short time ago.

Your problem may be related to static IP then. Are all your host names added to /etc/hosts?

---

### Post by billyboy1995 on 2009-07-26
this may be a bit off topic but... do you know how to connect to a windows shared printer? i have tryed  to find someone to tell me how but nobody will tell me how. Also going back on topic i cant see my windows computes in the network thingy in the places meneu....sorry i dont know its name im a real noob with ubuntu but a geek with windows....

Thanks in advance Bill

---

### Post by glave on 2009-07-26
They were not. Yesterday I did add the 1 machine I'm interested in browsing to /etc/hosts, but still same result.

---

### Post by strictlybusiness on 2009-08-04
I had a similar problem which brought me to this thread, but the solution was on the Windows side.
After setting up Jaunty on Intel D945GCLF2, I was able to see my Vista machine on the Windows network, but unable to browse shared folders ("Failed to mount Windows share"). Followed all instructions in this thread, editing smb.conf etc, to no avail (but probably have a more correct setup now).
Curiously, one of the shared folders on the Vista machine did mount even though all the others didn't. Led me to believe that the setup was wrong on the Vista side instead, which it was.
For me, the solution was to edit the users (right click the shared folder in Vista, go to Sharing tab, click Share..., click Change sharing permissions) and make sure that Administrators, [MyUserAccount], and Everyone had permissions (just click add, type in Everyone, choose desired permission level). 
After that, my Ubuntu machine could browse all Windows shares. 
This may not be the same problem as glave and others have, but it's worth looking into.

---

### Post by strictlybusiness on 2009-08-04
Forgot to mention - while the instructions kindly provided by dmizer are excellent, adding the "wins" into smb.conf broke my XBMC, as wins also appeared in /etc/nsswitch.conf. Removed it there and XBMC works again.

---

### Post by mgmiller on 2009-08-05
> [SIZE=4]**Problem 2:** [/SIZE]
There is no easy way to change the workgroup that Ubuntu belongs to. This means that you can either assign all of your Windows computers to the &#8220;WORKGROUP&#8221; workgroup (as outlined under "Problem 1"), or edit /etc/samba/smb.conf in order to change the workgroup that Ubuntu is a member of.This is not true.

Open a terminal and enter:
```
shares-admin
```You will get a gui for changing many samba properties, including the workgroup, which is on the "General Properties" tab.

If you find this useful, you should add it to your menus in the Administration area.  I don't know why this isn't there by default.  According to its help file, it is supposed to be there under System > Administration > Shared Folders.  
It also allows you drag and drop folders you want to share into its main window, which will open a dialog box with all the sharing parameters, among many other things.  It seems to give more options than simply right clicking the folder you want to share and selecting properties and going to the "share" tab.


For even more samba tweaking fun, you can add a full gui interface:
> sudo apt-get install system-config-sambaThis will put an entry in your menus at System > Administration > Samba 
Once you run it, look in Preferences > Server Settings to change the workgroup.

This gui seems to find more things than the server-admin one.  It shows my shared printer for example, where the first one I mentioned does not.

---

### Post by dmizer on 2009-08-05
Thank you very much for that extremly helpful post. It seems the above is true even for my Hardy install. I'll look more closely at this and try to include it in the howto.
> **mgmiller said:**
> I don't know why this isn't there by default.
I surely don't know. It would have saved me a huge amount of trouble early on.

---

### Post by mgmiller on 2009-08-05
> **dmizer said:**
> Thank you very much for that extremly helpful post. It seems the above is true even for my Hardy install. I'll look more closely at this and try to include it in the howto.

I surely don't know. It would have saved me a huge amount of trouble early on.

You're welcome.

There is one other issue that has been hashed out on several other threads and that is simply not having the network browse gui work at all or as expected.  This happens to people suddenly, where it was fine one day and mysteriously stops working the next.  

What I discovered and have submitted a bug report on:
[https://bugs.launchpad.net/bugs/389909](https://bugs.launchpad.net/bugs/389909)

Is that when your ISP starts to use DNS redirection, you lose the ability to browse your local network.  If you are using a simple home network, not on AD or other fancy stuff, the fix is very simple.

Edit /etc/samba/smb.conf and:
change this:
```

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
 

to this:
# What naming service and in what order should we use to resolve host names
# to IP addresses
    name resolve order = lmhosts wins bcast host

```Notice that host has been moved from 2nd place to 4th place and the leading semi-colon [;] has been removed.


After saving the file, log off and back on and that should do it.


If you are lucky enough to have Optimum Online as your ISP, you can opt out of DNS redirection by going here:
[http://www.optimum.net/Article/DNS](http://www.optimum.net/Article/DNS)


Failing that, you may be able to find a different DNS server somewhere that does not use redirection to create a revinue stream for itself and switch to that.

---

### Post by dmizer on 2009-08-05
This is a good tip, but I've [known about](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15) the DNS redirect issue for a while. Also, I think (I'm not positive yet) that having the above mentioned edit AND the wins edit in /etc/nsswitch.conf is a conflict. I have found several people complaining that their computer will not boot with both edits in place.

So, "Problem 3 - Part 1" should provide the same results as the edit you suggest, while still allowing full Windows netbios resolution in both client and server.

---

### Post by The Pinny Parlour on 2009-08-14
I applied the "Problem 3" fix.  Unfortunately both of my Ubuntu boxes cannot see windows shares.  It keeps asking for a username and password, and no matter what I type, it just doesn't work.

what bugs me the most as this was all working fine until recently.  What the heck happened and how can I fix this mess?   :(

---

### Post by dmizer on 2009-08-14
Do you have a firewall enabled on either Windows or Ubuntu?

---

### Post by The Pinny Parlour on 2009-08-14
> **dmizer said:**
> Do you have a firewall enabled on either Windows or Ubuntu?

Hello

Thank you for your assistance.

Answer to the question is No.

---

### Post by dmizer on 2009-08-14
Just to be sure, please post the output of:
```
sudo iptables -L
```
Did you try all of the fixes listed or just the fixes suggested under "Problem 3"?

---

### Post by ishmael2k on 2009-08-14
I have read this thread and several others to try and find a solution to my problem. I am running 9.04 on my main machine (Currently, eventually it will become the file server/backup) with no problems. I can access my home network from it fine. 

My windoze machines shared files are completely accessible and I can see my Ubuntu box (tyr) from the windoze pcs just fine. BUT unless I access the Ubuntu box via its' ip address I can't get to the shared files. Gives me the following error:  

//Tyr is not accessible
Access is denied        	:frown:

When I use the ip address all works fine. Any ideas where I am missing something? I did all the steps outlined in this thread with no luck.

I need to get this resolved as I am setting this up to be a file server/backup machine for my household and want it as easy as possible for the rest to use.

---

### Post by mgmiller on 2009-08-14
Just for giggles, is it possible for you to disconnect your cable/dsl/whatever modem from your router so your local network is still up, but it is no longer connected to the internet?  See if local network browsing is better.  Try logging off and back on with one of your Ubuntu boxes while in this mode and try local browsing again.  You could also try rebooting one of the Windows boxes while set this way as well.

If things suddenly start working when you are not connected to the internet, then the suspicians are high that DNS redirection by your ISP is causing a problem.  See if your ISP offers an opt-out for this "feature".

I had all kinds of problems start suddenly, overnight, on 2 networks of about a dozen computers in different towns that I traced to this problem.  They both used the same ISP and the day they started to use DNS redirection, I had problems.

---

### Post by ishmael2k on 2009-08-14
> Just for giggles, is it possible for you to disconnect your cable/dsl/whatever modem from your router so your local network is still up, but it is no longer connected to the internet? 

Once I get home I'll give that a try. Won't be a problem as my LAN runs through an 8 port switch. 

I'll post here what the results are.

Thanks!

---

### Post by dmizer on 2009-08-14
> **ishmael2k said:**
> When I use the ip address all works fine. Any ideas where I am missing something? I did all the steps outlined in this thread with no luck.

Please post your current /etc/samba/smb.conf file.

---

### Post by The Pinny Parlour on 2009-08-14
> **dmizer said:**
> Just to be sure, please post the output of:
```
sudo iptables -L
```
Did you try all of the fixes listed or just the fixes suggested under "Problem 3"?

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
user@user-desktop:~$ 


Thank again.   Just the fix under Problem 3.  :)


user@user-desktop:~$ /etc/samba/smb.conf file.
bash: /etc/samba/smb.conf: Permission denied
user@user-desktop:~$

---

### Post by The Pinny Parlour on 2009-08-14
Some screen shots of what happens when I select the windows computer from the "Network".  I don't have any password on the windows PC.  No matter what auth credentials I enter, I always get the same result... no access.

BTW.  When attempting access to Ubuntu boxes from windows, windows prompts me for auth credentials and I enter them for my ubuntu box but it doesn't allow access.  I can see the ubuntu box listed in "My Network Places" under "View Workgroup Computers" however.

[IMG]http://img229.imageshack.us/img229/9832/66591594.png[/IMG]

[IMG]http://img219.imageshack.us/img219/8072/21397674.png[/IMG]

---

### Post by dmizer on 2009-08-14
Okay, well, I suggest that you try ALL of the fixes. If you've tried all of the suggestions and you still have a problem, we can try something else.

---

### Post by The Pinny Parlour on 2009-08-14
> **dmizer said:**
> Okay, well, I suggest that you try ALL of the fixes. If you've tried all of the suggestions and you still have a problem, we can try something else.

Still not working.  I appreciate your help but this is networking issue is a real shame for me that Ubuntu used to work fine with my network until recently. 


I'm about to reinstall and NEVER EVER EVER install an update EVER again.

---

### Post by dmizer on 2009-08-15
> **The Pinny Parlour said:**
> I'm about to reinstall and NEVER EVER EVER install an update EVER again.
That is a very bad idea. Updates are extremely important.

Please post your current /etc/samba/smb.conf file.

Also, post the output of:
```
smbtree
```

---

### Post by The Pinny Parlour on 2009-08-15
> **dmizer said:**
> That is a very bad idea. Updates are extremely important.

Please post your current /etc/samba/smb.conf file.

Also, post the output of:
```
smbtree
```

Again thank you.  Updates may well be important but I have had Ubuntu PC's rendered useless through poorly tested updates.  Seeing as Ubuntu released every 6 months, I feel that not installing any updates is quite safe IMO.  Then when the next release comes, install it fresh.

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP
        netbios name = ian-desktop

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

;	wins support = no
	username map = /etc/samba/smbusers
[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

----------------------------------------------------------------------------------------

This is interesting...  It can access my partners windows PC and can detect my Windows PC (IANP) but cannot access it.  arrrrh.

ian@ian-desktop:~$ smbtree
Password: 
WORKGROUP
	\\KIP-4D41D325E4B		
		\\KIP-4D41D325E4B\C$             	Default share
		\\KIP-4D41D325E4B\ADMIN$         	Remote Admin
		\\KIP-4D41D325E4B\CanoniP4       	Canon iP4300
		\\KIP-4D41D325E4B\print$         	Printer Drivers
		\\KIP-4D41D325E4B\My Music       	
		\\KIP-4D41D325E4B\Documents      	
		\\KIP-4D41D325E4B\IPC$           	Remote IPC
		\\KIP-4D41D325E4B\My Documents   	
		\\KIP-4D41D325E4B\E$             	Default share
	\\IANP           		
	\\IAN-DESKTOP    		ian-desktop server (Samba, Ubuntu)
		\\IAN-DESKTOP\public         	
		\\IAN-DESKTOP\Canon-PIXMA-iP4300	Canon PIXMA iP4300
		\\IAN-DESKTOP\IPC$           	IPC Service (ian-desktop server (Samba, Ubuntu))
		\\IAN-DESKTOP\print$         	Printer Drivers
ian@ian-desktop:~$

---

### Post by dmizer on 2009-08-15
You are aware that upgrading from one release to the next isn't an update. That's a distribution upgrade, and it's similar to upgrading from Win2000 to WinXP, or XP to Vista. Upgrades of that nature are bound to encounter problems on occasion. Kernel updates are also huge, they are similar to service packs on Windows (also important, and also break things occasionally).

If you want stability, just use LTS releases like Dapper and Hardy.

If you can connect to one Windows computer but not the other, I suggest comparing settings between the two Windows computers. Obviously, something is different between them.

---

### Post by The Pinny Parlour on 2009-08-15
> **dmizer said:**
> You are aware that upgrading from one release to the next isn't an update. That's a distribution upgrade, and it's similar to upgrading from Win2000 to WinXP, or XP to Vista. Upgrades of that nature are bound to encounter problems on occasion. Kernel updates are also huge, they are similar to service packs on Windows (also important, and also break things occasionally).

If you want stability, just use LTS releases like Dapper and Hardy.

If you can connect to one Windows computer but not the other, I suggest comparing settings between the two Windows computers. Obviously, something is different between them.

distro upgrade would usually have the latest updates applied I would guess. 

Thank for your help.  PC that Ubuntu can't connect to is a fresh install so I don't know WTF is going on.   

I still cannot connect from windows to ubuntu however.  I can see it listed in "view workgroup computers" but can't access ubuntu from windows.  It prompts for username password which I enter but it reappears.

arrrrrrrrrrrrrrh!

---

### Post by dmizer on 2009-08-15
> **The Pinny Parlour said:**
> distro upgrade would usually have the latest updates applied I would guess. 
Hardy still receives security and kernel updates. So, again, if you're concerned about longevity, I suggest you stick with LTS.

> **The Pinny Parlour said:**
> Thank for your help.  PC that Ubuntu can't connect to is a fresh install so I don't know WTF is going on.  
Are you sure that file and printer sharing is enabled? Sometimes it's not. Also, what version of Windows is it? 

> **The Pinny Parlour said:**
> I still cannot connect from windows to ubuntu however.

That's a different subject entirely.

---

### Post by The Pinny Parlour on 2009-08-15
> **dmizer said:**
> Hardy still receives security and kernel updates. So, again, if you're concerned about longevity, I suggest you stick with LTS.


Are you sure that file and printer sharing is enabled? Sometimes it's not. Also, what version of Windows is it? 



That's a different subject entirely.

Win XP.  It is enabled.
I'm reinstalling windows again and this time I will test it after every app and driver I install.  Will see how that goes... Computer are fun huh?  grrrr   :)

I'll be at Kitakyushu shortly. Kokura and Mojiko.

---

### Post by The Pinny Parlour on 2009-08-15
Thanks again for your assistance dmizer.  Full format and reinstall (2nd in 48 hours) has solved the issue.  I have no idea what in Windows was denying access, but it is solved.  :)

Just to add... accessing Ubuntu PC from Windows PC works like a dream now too.  \o/

---

### Post by dmizer on 2009-08-15
> **The Pinny Parlour said:**
> Thanks again for your assistance dmizer.  Full format and reinstall (2nd in 48 hours) has solved the issue.  I have no idea what in Windows was denying access, but it is solved.  :)

Just to add... accessing Ubuntu PC from Windows PC works like a dream now too.  \o/

Heh, and you were all about blaming Ubuntu's updates ;)

Glad you got it working though!

---

### Post by ishmael2k on 2009-08-16
> **mgmiller said:**
> Just for giggles, is it possible for you to disconnect your cable/dsl/whatever modem from your router so your local network is still up, but it is no longer connected to the internet?  See if local network browsing is better.  Try logging off and back on with one of your Ubuntu boxes while in this mode and try local browsing again.  You could also try rebooting one of the Windows boxes while set this way as well.

If things suddenly start working when you are not connected to the internet, then the suspicians are high that DNS redirection by your ISP is causing a problem.  See if your ISP offers an opt-out for this "feature".

I had all kinds of problems start suddenly, overnight, on 2 networks of about a dozen computers in different towns that I traced to this problem.  They both used the same ISP and the day they started to use DNS redirection, I had problems.

Did this and it cleared up the problem Now to figure out how to opt-out if possible.

Thank-you!

---

### Post by ishmael2k on 2009-08-16
> **dmizer said:**
> Please post your current /etc/samba/smb.conf file.

Here it is:

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = randl
;	netbios name = tyr

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#justice
;	wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = no

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
	guest ok = yes
	guest account = tyr

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
	read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Documents]
	path = /home/tyr/Documents
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

[Pictures]
	path = /home/tyr/Pictures
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

[Downloads]
	path = /home/tyr/Downloads
	writeable = yes
;	browseable = yes
	guest ok = yes


I was going to send it as a file but no time to compact it enough to upload.

I really appreciate any and all time you guys put into this.

---

### Post by dmizer on 2009-08-16
> **ishmael2k said:**
> Did this and it cleared up the problem Now to figure out how to opt-out if possible.

Thank-you!

If that fixed your problem, please post your /etc/nsswitch.conf file.

Also, you've commented out your netbios name in your /etc/samba/smb.conf file. This is how your Windows computers know what to call your Ubuntu computer. If you have nothing here (or it's commented out) your Windows computers have to guess.

Change this:
```
; netbios name = tyr
```
to this
```
netbios name = tyr
```

---

### Post by ishmael2k on 2009-08-16
> **dmizer said:**
> If that fixed your problem, please post your /etc/nsswitch.conf file.

Also, you've commented out your netbios name in your /etc/samba/smb.conf file. This is how your Windows computers know what to call your Ubuntu computer. If you have nothing here (or it's commented out) your Windows computers have to guess.

Change this:
```
; netbios name = tyr
```
to this
```
netbios name = tyr
```

Changed the code. (I don't know how it ended up commented out..) It looks like this did it. I am hooked up to me ISP and still able to access the Ubuntu pc from the windoze. I re-booted the windoze a couple of times to see if that would affect the access and it did not. I am going to shut both down and boot cold to see what happens.

I'll post the results in a few minutes.


Here is the nsswtch.conf:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by ishmael2k on 2009-08-16
Ok, that appears to have resolved the problem. I will be testing it out over the next few days to make sure it has taken before I move to the next step and will keep this thread notified as to any situations that arise.

Thank-you,

Ish2k

---

### Post by dmizer on 2009-08-16
> **ishmael2k said:**
> Ok, that appears to have resolved the problem. I will be testing it out over the next few days to make sure it has taken before I move to the next step and will keep this thread notified as to any situations that arise.

Thank-you,

Ish2k

Glad you're working!

---

### Post by Raven2k360 on 2009-08-17
I currently have Ubuntu Studio 9.04 x64 installed on my Desktop, and I've needed to switch from the rt kernel to generic due to stability issues. The problem I'm having is, I have a copy of Vista Ultimate 32-bit installed in Virtual Box, and it's having network sharing issues with the host machine. The Virtual machine can see my Host, but when I double-click to open the host, it asks for a username/password. 

 Now here's the kicker -- my new laptop came with Vista Home Prem 64-bit installed and it does the same thing...but both vista machines can navigate my old laptop just fine, which has standard Ubuntu 9.04 i386 installed on it. I installed standard Ubuntu 9.04 x64 on my new laptop with a dual-boot setup, and both the old laptop and new laptop can navigate my Desktop (Ubuntu Studio) just fine when they're in Ubuntu, and my X-box with XBMC can navigate as well.

 I've tried the above mods to smb.conf and nsswitch.conf, and even just sharing individual folders but nothing will allow Vista to navigate my Desktop through the network.

---

### Post by dmizer on 2009-08-17
Since everything works perfectly from all machines except the Vista virtual machine, I suggest taking a very close look at your virtual machine's networking, firewall, and file sharing configurations.

I recall once that someone had trouble browsing samba from their Windows virtual machine. The fix was related to MTU. You should double check to make sure the MTU matches across the virtual network.

---

### Post by Raven2k360 on 2009-08-17
I have a new problem now -- Since modifying my smb.conf on my desktop, the new laptop (running ubuntu) now won't mount the shared drive on the desktop.  I've run through the steps for the new Laptop, but still no change.  Also, while I was running the changes, the command for restarting samba wasn't working, saying that the command didn't exist.

---

### Post by Raven2k360 on 2009-08-17
> **dmizer said:**
> Since everything works perfectly from all machines except the Vista virtual machine, I suggest taking a very close look at your virtual machine's networking, firewall, and file sharing configurations.

I recall once that someone had trouble browsing samba from their Windows virtual machine. The fix was related to MTU. You should double check to make sure the MTU matches across the virtual network.

It's not just the VM -- it's also the new laptop if I boot into Vista.

---

### Post by patsingh on 2009-08-19
Thanks dmizer for helping me fix this problem. It went away when I turned ufw (using gufw) to allow incoming connections.

However when I turned ufw back to block incoming connections and tried the following I could not see any computers on the network.
```

sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
sudo ufw allow proto udp to any port 138 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.29.0/24
```I checked /var/log/syslog and found out that the ports 137 138 139 445 were source ports **not destination ports** so I changed it around using the GUI. I wonder if anyone else has this problem.

My result for the command

```
sudo ufw status numbered
```[FONT=monospace]Status: active

     To                         Action  From
     --                         ------  ----
[ 1] Anywhere                   ALLOW   192.168.1.0/24 139/tcp
[ 2] Anywhere                   ALLOW   192.168.1.0/24 445/tcp
[ 3] Anywhere                   ALLOW   192.168.1.0/24 137/udp
[ 4] Anywhere                   ALLOW   192.168.1.0/24 138/udp

Thanks again!
[/FONT]

---

### Post by dmizer on 2009-08-19
Thank you for the tip. I've updated the howto.

---

### Post by patsingh on 2009-08-20
Actually this is what I have to do for it to work on ubuntu-desktop/ufw
```

sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
sudo ufw allow proto udp from 192.168.1.0/24 port 138 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 139 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 445 to any
```This is to access shares on WinXP/with-firewall and Samba/Ubuntu-server/no-ufw. I will try enabling ufw on Ubuntu-server and see which settings work.

):P[COLOR=Red]Edit (20-Aug09): the problem was that I did not add the netbios_ns line
(see [http://ubuntuforums.org/showthread.php?t=806000](http://ubuntuforums.org/showthread.php?t=806000))
[/COLOR] 
This is my understanding of the problem:

Client starts a connection from a random high number port (1024-65535) to one of the above ports (137,138/udp  139,445/tcp) on the remote computer. When the remote computer replies to the high port it was blocked by ufw which is set to deny incoming connections.

My original solution (above) allowed connections to any port on the client from the specified ports on the remote computer (insecure).

The netbios_ns solution tracks which connections were initiated by the client and allows the remote computer to respond to ports that would otherwise be blocked. In other words, the remote computer is allowed to reply on the same high port within a given *timeout*.

---

### Post by bkb on 2009-08-25
My home/office setup is as follows:

Desktop running ubuntu 9.04
Laptop running Windows XP Home SP3
Laptop running Mac OS X 10.5

All are on the same local network (the desktop via ethernet, the laptops via wireless).  

I wasn't making much progress getting them to talk to each other until I went through the changes in this post.  Now file sharing is mostly fixed.  I can see and access the shared folders on both my Mac and Ubuntu. However, when trying *from* Ubuntu to my Windows laptop's, I can see the computer in Workgroup but when I try to open it, it keeps prompting me for a username and password.  Why does this happen?  What I'm really trying to do is connect as a guest and just access the shared public folder on my Windows laptop.  Is there any way to change this?

There are a couple more computers on the way this week as I'm adding a couple more Ubuntu desktops plus another Mac laptops.  Was hoping to iron out these quirks so they don't get out of hand.

As a side note - it was very easy to share the printer connected to my Ubuntu desktop (from the Windows laptop - haven't got round to adding it to my Mac).

Thanks.

---

### Post by dmizer on 2009-08-25
> **bkb said:**
> I wasn't making much progress getting them to talk to each other until I went through the changes in this post.  Now file sharing is mostly fixed.  I can see and access the shared folders on both my Mac and Ubuntu. However, when trying *from* Ubuntu to my Windows laptop's, I can see the computer in Workgroup but when I try to open it, it keeps prompting me for a username and password.  Why does this happen?  What I'm really trying to do is connect as a guest and just access the shared public folder on my Windows laptop.  Is there any way to change this?

Do you have both a password protected share as well as a public share on the Windows machine? If so, can you connect to the guest share if you cancel the password request?

---

### Post by bkb on 2009-08-27
> **dmizer said:**
> Do you have both a password protected share as well as a public share on the Windows machine? If so, can you connect to the guest share if you cancel the password request?

Thanks for your reply.  I was trying this but I would get another dialog box that said the password dialog was canceled.  However, it suddenly started working again today.  I'm still finding it pretty erratic overall.

---

### Post by clamar8 on 2009-09-05
Dear dmizer,

Many thanks for your tutorial. After addressing "Problems 1 and 2" I finally was able to mount on my Ubuntu computer a folder from my XP computer. I had so much hard times trying again and again. Your tutorials are well written. There are still so many things I don't understand but it's good when things work!

Thank you!

clamar8

---

### Post by Paul Crumley on 2009-09-06
I'm 100% new to the Linux world - had some experience years ago in the non-GUI Xenix system,but that was long ago, far away and long-forgotten, mostly.

I've been using Ubuntu for just a little over a week, and this particular problem was the most vexing so far.  The Windows '98 laptop I have, and my Win XP SP3 system both found the Linux machine, could read from it, share the printer, etc.  The Linux box, however, could only see that there is a network here.  It seemed to be trying to find my other systems via DNS into the outside world, returning some really strange ip addresses, not the 192.168.*.* I expected.  Netbios changes did nothing for this.

What fixed it for me was doing all the main steps in the first few posts, then finally finding a suggestion to install smbfs.  After installing smbfs, everything works perfectly.  I can read/write files to and from Linux and both versions of Windows.

Now on to bigger and better things, I guess.

Thanks to all for the helps and suggestions.

---

### Post by Tankerdog2002 on 2009-09-11
Hmmmmmmm......your tips wiped out my entire network. 

I don't know what happened but after following your steps, I didn't even have a workgroup anymore. May have been the winbind thing, I don't know. In any event, none of your advice worked for me. I see it helped others though and thats good.

Your wins dns advice took down my internet. I changed the nsswitch.conf back to original and the internet came back, but now my SMB network is totally hosed.

I appreciate you trying to help, but I'm a bit 'miffed at 'ya right now. I had to do a re-install.

Thanks anyway.

---

### Post by dmizer on 2009-09-11
> **Tankerdog2002 said:**
> Hmmmmmmm......your tips wiped out my entire network.

Rather than uninstalling, it would have been much better to figure out what the problem really was. That way, my advice doesn't do the same thing to someone else.

By off chance, are you running a static local network?

---

### Post by Tankerdog2002 on 2009-09-11
dmizer,

No static setup here.

Sorry that I didn't spend more time trying to find out what went haywire. Time is something I didn't have a lot of. Already wasted half a day. Got a business to run.

The reinstall fixed my problem. I'm browsing through 7 different windows drives on the network currently.

Again, 
Thanks anyway.

---

### Post by caddict on 2009-09-16
hi dmizer

i have just upgraded to 9.04 and have the usual problem...can't see shares on my XP computer. it all worked fine on 8.04

i have followed all your instructions to the letter and still cannot resolve the problem. all firewalls disabled. i can see the computer in the network window, but get that dreaded msg "unable to retrieve.." when trying to browse.

don't know what else to try...

one question: in smb.conf, should wins support = yes or no?

---

### Post by dmizer on 2009-09-17
> **caddict said:**
> hi dmizer

i have just upgraded to 9.04 and have the usual problem...can't see shares on my XP computer. it all worked fine on 8.04

i have followed all your instructions to the letter and still cannot resolve the problem. all firewalls disabled. i can see the computer in the network window, but get that dreaded msg "unable to retrieve.." when trying to browse.

don't know what else to try...

one question: in smb.conf, should wins support = yes or no?

Please post your entire smb.conf file. Delete or comment any "wins =" line (the default behavior is desireable).

"Failed to retrieve share list from server" is almost always a firewall problem. Are you sure you have disabled all firewalls on both the client (XP machine) as well as the server?

---

### Post by caddict on 2009-09-17
thanks dmizer, i wish your problems could be over

here is the smb.conf file. it has been inherited from earlier ubuntu installs

```
[global]
    ; General server settings
	workgroup = HOME
	netbios name = FOXY
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = lmhosts wins bcast host

	wins support = no

;	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	server string = samba 3.3.2
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
	writeable = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
	path = /home/samba

;	writeable = no
	create mask = 0644
;	directory mask = 0755
	force user = STEVE
	force group = STEVE
;	available = yes
;	browseable = yes
	valid users = nobody, steve
```

i have checked often that ufw is disabled both in the terminal and the gui. on xp i am using comodo which is easily disabled. so i am pretty sure

---

### Post by amegg on 2009-09-17
Unless I have missed something from all the entries in this and other places I am unable to get this completely working.

I am running 9.04.  Like others I was able to access my box from other machines from other machines on the network with the netbios name until an update and now I can't get it working.  I have disabled UFW.  I can get it so that I can browse my shares in windows, but I still cannot connect to the box via SSH and HTTP using the netbios name only the IP address.

I do not have firestarter installed only ufw and when I add wins to nsswitch.conf system boot halts on samba starting, and even with this enabled it still doesn't work after restarting networking.

I am at a loss after fiddling with this for a couple of days.

When I issue smbtree -N I get no output.

I'm sorry to add to the mess, but please help.

Thank you.

---

### Post by caddict on 2009-09-17
after trying various options i am now able to ping my windows computer by name and by ip which is big improvement over yesterday, so there is hope. still can't access those windows shares, but one step closer...

---

### Post by caddict on 2009-09-18
and now i can browse shares on another computer running vista (even with firewalls enabled)

strange that the shares on the xp computer cannot be reached...

---

### Post by dmizer on 2009-09-20
> **caddict said:**
> strange that the shares on the xp computer cannot be reached...
That would almost certainly point to a problem with the XP computer.

---

### Post by DougEdey on 2009-09-20
First off, thanks for the awesome guide. 

Unfortunately I've checked every step and can't get the list of shares from the server.

I can go direct (smb://ip/share) but that's only good if I know the share name. 

I've checked all my firewall settings :)

---

### Post by dmizer on 2009-09-20
> **amegg said:**
> ... when I add wins to nsswitch.conf system boot halts on samba starting ...

Solving this will solve your problem. I've seen this several times with others, but I have not been able to determine why.

Are you using a static network? What's your current smb.conf file look like?

---

### Post by sparker1 on 2009-09-22
Thanks Dmizer. I've been on this for days and I was going to go back to windows entirely. This information was the best I could find for my case and I am up and running with my network. Great work.

---

### Post by caddict on 2009-09-24
> That would almost certainly point to a problem with the XP computer.

yes! problem found. thanks to lorjack at tech support forums:

[http://www.techsupportforum.com/networking-forum/networking-support/393450-network-error-code-0x80070005.htm](http://www.techsupportforum.com/networking-forum/networking-support/393450-network-error-code-0x80070005.htm)

just change reg entry restrictanonymous from 1 to 0

thanks for your input dmizer :-)

---

### Post by amegg on 2009-09-25
I was using a static IP, but then after remembering to reserve the IP in my router and also assign a name there I have it set to DHCP again and I am going to put wins back into nsswitch.conf.  It doesn't really matter at this point since my router serves the name I want for the  machine now.

Thank you for the guide and for the help.  This was a big help.

---

### Post by centec2b on 2009-10-04
I just wanted to say THANK YOU THANK YOU THANK YOU

I have been banging my head against a brick wall for months trying to get Ubuntu to see windows.  Windows could see Ubuntu but not vice versa.  Now by following your guidance I can 

YIPPPEEE!

---

### Post by Aero-Z on 2009-10-21
I had problems with Network too so I tried your tips.
I got my laptop to show up on Windows XP installation and also Windows XP can see my laptop's shared folder and access it. The problem is still with my Windows 7 installation. I can see the computer and shared folder in Ubuntu (and also in XP) but I'm unable to access it. In Ubuntu I get "Unable to mount locaion. Failed to retrieve share list from server."
Tho I'm able to connect to the shared folder on Windows 7 machine with smb://IP_ADDRESS/SHARE. But I'd prefer browsing from Nautilus.
Also my Ubuntu doesn't show up on Windows 7 installation.
Any ideas?

---

### Post by dmizer on 2009-10-21
> **Aero-Z said:**
> In Ubuntu I get "Unable to mount locaion. Failed to retrieve share list from server."

This is almost always related to a firewall problem. Check for and correctly configure your firewalls on both your Ubuntu and your Win7 machines.

---

### Post by Aero-Z on 2009-10-22
> **dmizer said:**
> This is almost always related to a firewall problem. Check for and correctly configure your firewalls on both your Ubuntu and your Win7 machines.
File and printer sharing is allowed through the firewall. File sharing and discovery is working between two Windows 7 computers tho.
Maybe I have to add custom ports to Windows 7's firewall?
Also I can print from Ubuntu and XP machine to the printer which is connected locally to the Windows 7 machine (shared printer).

---

### Post by dmizer on 2009-10-22
> **Aero-Z said:**
> File and printer sharing is allowed through the firewall. File sharing and discovery is working between two Windows 7 computers tho.
For obvious reasons, Windows computers cooperate better with other Windows computers.

> **Aero-Z said:**
> Maybe I have to add custom ports to Windows 7's firewall?

Try completely disabling the firewall on the Windows 7 machine before trying to go through the effort of making custom ports.

---

### Post by Aero-Z on 2009-10-22
> **dmizer said:**
> For obvious reasons, Windows computers cooperate better with other Windows computers.



Try completely disabling the firewall on the Windows 7 machine before trying to go through the effort of making custom ports.
Still got the same problem after disabling the firewall.

---

### Post by dmizer on 2009-10-22
> **Aero-Z said:**
> Still got the same problem after disabling the firewall.

Try adding a /etc/hosts entry on Ubuntu for your Win7 machine. Here's an example for you ...
```
127.0.0.1	localhost
127.0.1.1	karmic-testing
[COLOR="Red"]192.168.1.125   Win7-netbios-name
[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Just adapt the IP address and netbios name in this line [COLOR="Red"]192.168.1.125   Win7-netbios-name[/COLOR] to the actual settings on your Win7 box.

---

### Post by Aero-Z on 2009-10-22
> **dmizer said:**
> Try adding a /etc/hosts entry on Ubuntu for your Win7 machine. Here's an example for you ...
```
127.0.0.1	localhost
127.0.1.1	karmic-testing
[COLOR="Red"]192.168.1.125   Win7-netbios-name
[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Just adapt the IP address and netbios name in this line [COLOR="Red"]192.168.1.125   Win7-netbios-name[/COLOR] to the actual settings on your Win7 box.
Still same :(

---

### Post by Aero-Z on 2009-10-22
> **Aero-Z said:**
> Still same :(
I got file sharing to work on XP machine. The picture looks like this right now:
1. Ubuntu laptop - I can see all computers - XP, Windows 7 and Ubuntu itself. Tho I can only access my own shared folder.
2. XP laptop - I can see all computers and I can access Ubuntu and XP itself. I can't access Windows 7 computer.
3. Windows 7 PC - I can see only myself.

I'm able to access XP and Windows 7 from Ubuntu by typing smb://IP_ADDRESS/SHARE NAME.

So any other ideas? :)

---

### Post by Aero-Z on 2009-10-22
> **Aero-Z said:**
> I got file sharing to work on XP machine. The picture looks like this right now:
1. Ubuntu laptop - I can see all computers - XP, Windows 7 and Ubuntu itself. Tho I can only access my own shared folder.
2. XP laptop - I can see all computers and I can access Ubuntu and XP itself. I can't access Windows 7 computer.
3. Windows 7 PC - I can see only myself.

I'm able to access XP and Windows 7 from Ubuntu by typing smb://IP_ADDRESS/SHARE NAME.

So any other ideas? :)
I got sharing working between XP and Ubuntu now. I added XP laptop to /etc/hosts file.
Still got problem with Windows 7 tho.

---

### Post by newb85 on 2009-10-22
Great tutorial!  Like a stubborn idiot, I tried to evaluate which of the steps I needed, and fought to get it to work.  Only after going through all of them did everything run like it should.

---

### Post by dmizer on 2009-10-22
> **Aero-Z said:**
> I got sharing working between XP and Ubuntu now. I added XP laptop to /etc/hosts file.
Still got problem with Windows 7 tho.

I really think your problem is going to be with your Win7 machine though. I'm in the process of recovering my Win7 virtual machine so I can do some testing, but I suggest taking a very hard look at the share configuration on your Win7 box.

---

### Post by Aero-Z on 2009-10-23
> **dmizer said:**
> I really think your problem is going to be with your Win7 machine though. I'm in the process of recovering my Win7 virtual machine so I can do some testing, but I suggest taking a very hard look at the share configuration on your Win7 box.
Yeah, the problem is in the Win7 box. I've googled and re-checked the sharing settings but nothing :( Sharing between two Win7 machines worked without problems tho. Let me know if you find anything out and I'll also keep you updated :)

---

### Post by dmizer on 2009-10-23
> **Aero-Z said:**
> Yeah, the problem is in the Win7 box. I've googled and re-checked the sharing settings but nothing :( Sharing between two Win7 machines worked without problems tho. Let me know if you find anything out and I'll also keep you updated :)

This thread may be of interest to you: [http://ubuntuforums.org/showthread.php?t=1295659](http://ubuntuforums.org/showthread.php?t=1295659)

---

### Post by newb85 on 2009-10-23
I had it working, and now I broke it, and I'm wondering if I'm trying to accomplish something impossible.

I would like to be able to mount my home directory from my laptop on my desktop and vice versa.  I installed samba on the desktop and smbfs on the laptop, installed winbind on the laptop, edited smb.conf on both machines, added the appropriate entry to fstab on the laptop, added "wins" to the hostnames, and opened the appropriate ports through ufw on both machines.  Everything was working great.

Then I tried to take it the other direction.  However, after installing samba, smbfs, and winbind and adding the line to fstab and "wins" to the hostnames, I can no longer go either direction.  Neither home directory will mount on the other machine, and I cannot browse to either of them.

Is it possible for both machines to serve as both a host and a client?

I actually don't know for sure whether the problem was started by trying to set up sharing the other direction or by installing updates.

---

### Post by dmizer on 2009-10-23
> **newb85 said:**
> Is it possible for both machines to serve as both a host and a client?

Yes it is.

Since both of your computers are using Ubuntu, you should try NFS instead of Samba. Please see the 4th link in my sig.

---

### Post by psycho5 on 2009-10-24
First off, thanks dmizer for refering me to this post from [http://ubuntuforums.org/showthread.php?p=8152650#post8152650](http://ubuntuforums.org/showthread.php?p=8152650#post8152650)

Anyways, I followed this through, and before doing so, I'd go to places> network> Windows Network and I couldn't open it, it would say "Failed to retrieve share list from server"

After following this guide, I got a little bit further. Once I went to Places> Network I could see my computer name which was the netbios name. I could also open up Windows Network only to find my computer listed in it. When I try to browse to the computer by using smb://192.168.0.4/ it gives me the same error, "Failed to retrieve share list from server"

Before I try adding the IP address for the Machines in /etc/hosts I need to know if having static IPs for all 3 machines will make a difference in putting **wins** before dns in that particular file?

I read this guide and the one here [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) but I didn't go any further than that step because I don't know what to do with static IPs if its any different. From what I understand it should be easier to find the PCs on the network if the IP is static right?

The other two computers can see each other and access their files. One has XP the other has windows 7.

EDIT:

whatever happened to the simplicity of 9.04 and below? Just right click > share, install the needed files and presto. *sigh*

I've added the firewall rules in ufw for my IP range to allow the ports. Anything else I should check on? The firewalls in the Windows PCs are already allowing network sharing through.

---

### Post by dmizer on 2009-10-24
> **psycho5 said:**
> I read this guide and the one here [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) but I didn't go any further than that step because I don't know what to do with static IPs if its any different. From what I understand it should be easier to find the PCs on the network if the IP is static right?

Just use the /etc/hosts file if you have a static network.

Please post the output of:
```
smbtree
```

> **psycho5 said:**
> whatever happened to the simplicity of 9.04 and below? Just right click > share, install the needed files and presto. *sigh*

This problem has been ongoing. It's not new. Note the creation date of this thread ... May 25th, 2009. I also created this tutorial: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) way back in October 2006 because of the same problem. I've really had very little luck getting the Nautilus share browsing to work correctly in any of the Ubuntu releases. It's the main reason why I know so much about it ... I have to constantly tinker with it to keep it working.

---

### Post by Aero-Z on 2009-10-24
Interesting. Tried smbtree command out too. As you can see I see all computers and shares there. But still can't access them from Nautilus' Network.

```
WORKGROUP
	\\PRIIT-PC       		
		\\PRIIT-PC\Users          	
		\\PRIIT-PC\Public         	
		\\PRIIT-PC\print$         	Printer Drivers
		\\PRIIT-PC\IPC$           	Remote IPC
		\\PRIIT-PC\Canon MP160    	Canon MP160 Printer
		\\PRIIT-PC\C$             	Default share
		\\PRIIT-PC\ADMIN$         	Remote Admin
	\\PRIIT-LAPTOP   		priit-laptop
		\\PRIIT-LAPTOP\public         	
		\\PRIIT-LAPTOP\IPC$           	IPC Service (priit-laptop)
	\\PIRET-LAPTOP   		
		\\PIRET-LAPTOP\SharedDocs     	
		\\PIRET-LAPTOP\print$         	Printer Drivers
		\\PIRET-LAPTOP\IPC$           	Remote IPC

```

---

### Post by dmizer on 2009-10-24
You should be able to mount the share with CIFS. Please see the 2nd link in my sig. I know it looks more difficult than simply browsing to your share in Nautilus, but at this point you'll probably have more success that way.

---

### Post by pototo on 2009-10-25
Upgraded to Karmic and now I can't connect to my samba shares. I can find it through network, and if I double click on the folder then the system mounts it, but I can't get it to mount in fstab neither manually using mount -t.

I edited smb.conf and changed workgroup to meet the workgroup of the  windows machine. Then I try to mount manually:
```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

```it gives no errors, and I can see the mounted folder on media/sharename, but there are no files inside, or I can't see them. However, in nautilus statusbar I can see the freespace in the windows share.

Any idea?

---

### Post by dmizer on 2009-10-25
> **pototo said:**
> Upgraded to Karmic and now I can't connect to my samba shares. I can find it through network, and if I double click on the folder then the system mounts it, but I can't get it to mount in fstab neither manually using mount -t.

I edited smb.conf and changed workgroup to meet the workgroup of the  windows machine. Then I try to mount manually:
```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

```it gives no errors, and I can see the mounted folder on media/sharename, but there are no files inside, or I can't see them. However, in nautilus statusbar I can see the freespace in the windows share.

Any idea?

Please see the 2nd link in my sig. Refer to the "Troubleshooting" section where it says: Files owned by root / "The folder contents could not be displayed"

---

### Post by pototo on 2009-10-25
Thank you for your quick reply, dmizer.

I tried your sollution, but it doesn't work. This is my fstab:
```
//netbiosname/sharename /media/sharename cifs guest,gid=1000,uid=1000,nounix,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```I also tried mounting on /home/user/sharename instead of /media/sharename with the same result.

---

### Post by Athlan on 2009-10-25
Hi

I read your first post in this thread, did everything according to it, but am still not able to browse the Windows Network in Nautilus.

However browsing with IPS e.g. smb://192.168.1.35/ works fine

I am having trouble browsing smb://nathan/, nathan is the name of the windows xp home box i want to connect to. This name is already listed in /etc/hosts.

Since i shut down my firewall completely, browsing the Windows Network on Nautilus at least *shows* me the network hosts.

Although browsing them leads to the error: Unable to mount location. Failed to retrieve share list from server. Please select another viewer.

I have to add, that the samba ports are opened up (137,138 udp samba / 139,445 tcp samba) So activating the gufw and/or ufw should not be a problem.

Do you have advice? smb.conf is attatched as .txt.

Thanks a lot.
Athlan

---

### Post by audiomick on 2009-10-28
Hallo everyone.
I haven't read this thread all the way through, so my apologies if I am suggesting something that everyone already knows about.

Using my Desktop PC with Ubuntu Studio 9.04,
I have not been able to see samba shares on my NAS and my Vista laptop for a couple of months now.
I had time to look at it again today, and found these:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)

[https://bugs.launchpad.net/hundredpapercuts/+bug/389909](https://bugs.launchpad.net/hundredpapercuts/+bug/389909)

I changed the smb.conf file as suggested, and was successful.
The explanation there "feels" right to me, based on how the computer has been behaving.

Michael

---

### Post by dmizer on 2009-10-28
> **audiomick said:**
> Hallo everyone.
I haven't read this thread all the way through, so my apologies if I am suggesting something that everyone already knows about.

Using my Desktop PC with Ubuntu Studio 9.04,
I have not been able to see samba shares on my NAS and my Vista laptop for a couple of months now.
I had time to look at it again today, and found these:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)

[https://bugs.launchpad.net/hundredpapercuts/+bug/389909](https://bugs.launchpad.net/hundredpapercuts/+bug/389909)

I changed the smb.conf file as suggested, and was successful.
The explanation there "feels" right to me, based on how the computer has been behaving.

Michael

Included this information under "Problem 3 - Jaunty/Karmic"

---

### Post by Visserys on 2009-11-01
I did everything you said to do on the first page of this thread and disabled the firewall on both the linux Ubuntu 9.10 machine and the Windows 7 machine. 

I am still unable to access my windows share from my Ubuntu 9.10 machine. 

The error I receive is the following : failed to retrieve share list from server

I can see the windows computer but that is the error I get when I double click on it. Originally I couldn't see anything, but after following your steps this is where I am now. 

my smb.conf is as follows:

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = holly-lappy

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts wins bcast host

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom








I am at a complete loss as to what to do. This isn't the first time I've had this problem, and always before today, Ive done the steps you've recommended and it has worked. If you have any idea whats happening I really need your help.

Thanks,

Viss

---

### Post by RealG187 on 2009-11-03
I am getting "Failed to retrieve share list from server" errors running Ubuntu in VM Ware with a Windows 7 host. I have tried with Firewall and UAC off and still had no luck...

---

### Post by Mr_Bumpy on 2009-11-03
In Karmic, with the firewall disabled, I have no problem browsing the samba shares on my network, but if I enable the firewall, I can't see any shares.  I've opened the following ports to no avail: tcp 135, 139, 445 and udp 137-139.

Interestingly, when I run findsmb with the firewall off, it spends about a minute and finds PCs on the network.  When I run findsmb with the firewall on (even if the aforementioned ports are open), fndsmb immediately returns to a command prompt and doesn't find any computers.

I know there are instructions for changes to other files (smb.conf), but if everything works with the firewall disabled, do I really need to mess with any of that other stuff?  Are there any additional ports I need to allow?

---

### Post by oldsoundguy on 2009-11-03
just corrected a massive issue of this nature .. the EASY WAY.
Went into the Windows machines and launched network Lizzard .. and changed MSHOME to WORKGROUP and tah-dah!!!!!  Everything works again!! (including the inter tie of 6 printers and the ability to move files across the network!)

---

### Post by RealG187 on 2009-11-03
> **Mr_Bumpy said:**
> In Karmic, with the firewall disabled, I have no problem browsing the samba shares on my network, but if I enable the firewall, I can't see any shares.  I've opened the following ports to no avail: tcp 135, 139, 445 and udp 137-139.

Interestingly, when I run findsmb with the firewall off, it spends about a minute and finds PCs on the network.  When I run findsmb with the firewall on (even if the aforementioned ports are open), fndsmb immediately returns to a command prompt and doesn't find any computers.

I know there are instructions for changes to other files (smb.conf), but if everything works with the firewall disabled, do I really need to mess with any of that other stuff?  Are there any additional ports I need to allow?How do you turn the firewall off in Ubuntu Karmic? I was talking about the one in Windows 7, maybe that's the problem...

EDIT: "sudo ufw disable" did nothing :(

---

### Post by Mr_Bumpy on 2009-11-03
Install gufw, then you can find a GUI option in System -> Administration -> Firewall configuration.  You can disable the firewall from there.

---

### Post by RealG187 on 2009-11-03
I was able to connect using the mount command.

Two problems:
I specifiy my username and password and only get read only (I have NTFS permissons on the share so only I can access it) I wonder, should I get NTFS to full share share to read only instead of share to full and NTFS to read only?

When I use the mount command I have to type my password in the command and if someone sees my screen they will know my password. Is there a way I can make the command prompt for my password?

---

### Post by Mr_Bumpy on 2009-11-03
Here's how I mount my network shares, and it works quite well on my network.

My example will use the following variables:
[LIST]
[*]your username: fred
[*]your password: fredRocks!
[*]server to connect to: winbox
[*]share on the server: myfiles
[/LIST]

1. Make sure the package **smbfs** is installed.

2. (optional) Make it so you can mount shares using sudo without having to enter your password.  Do this by running **sudo visudo** from a terminal, and adding the following lines at the end:
```
fred	ALL=NOPASSWD:/bin/mount
fred	ALL=NOPASSWD:/bin/umount
```

3. Make sure your mount point folder exists.  If you want the network share to show up automatically as an icon on the desktop when you mount it, then create the mount point in /media.  For example:
```
sudo mkdir /media/myfiles
```

4. The way I handle network share passwords is to create an authentication file and point to it in the mount command.  

Create a hidden text file in your home directory named ".auth.winbox.fred".  Inside that file, put the following:
```
username=fred
password=fredRocks!
```
Set the file's permissions so that nobody else can read it.  You can do this in Nautilus, or by command if you prefer:
```
chmod 600 .auth.winbox.fred
```

5. Finally, to mount your share, run the command as follows:
```
sudo mount -t cifs //winbox/myfiles /media/myfiles -o credentials=/home/fred/.auth.winbox.fred,noperm,uid=fred,gid=fred
```

The share should show up as an icon on your desktop.  To unmount, the command is simpler:
```
sudo umount /media/myfiles
```

You may need to try different combinations of the options to get the best results.  The **noperm** option ignores unix permissions on the shared files (which might help your read/write problem).  The uid/gid options were necessary to solve a problem I had where OpenOffice was opening shared documents as read-only.  Another option that might help you is **nounix**.

This command works perfectly when connecting to a Samba server running on Linux, but I haven't tried it with shares from an actual Windows box yet.

Once you've found a command that works well, you can easily make it into a script so you don't have to type all of that each time you want to mount your share (plus you can set it to connect on boot).  Let me know if you need any help with that part.

---

### Post by RealG187 on 2009-11-04
> mpg@mpg-desktop:~$ sudo mount -t cifs //192.168.239.1/Share /home/mpg/Desktop/Host -o credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg
mount: wrong fs type, bad option, bad superblock on //192.168.239.1/Share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mpg@mpg-desktop:~$
I get that error

EDIT: Nevermind, I had to install the package in step 1. I was in a rush and forgot. Funny thing is it worked in Fedora natively, and in Fedora that's the only way I can view Samba shares...

---

### Post by darwin1859 on 2009-11-04
Great tutorial - worked for me on Karmic after completing the windbind step.  Thanks!

---

### Post by RealG187 on 2009-11-05
> mpg@mpg-desktop:~$ sudo mount -t cifs //192.168.239.1/Share /home/mpg/Desktop/Host -o credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)Now what's going on ahhhhhhhhhhhhhh

---

### Post by zwdev on 2009-11-05
OK, what works for me all the time is to install or reinstall samba and here is how I do it.
Fire up a Terminal window and;

**sudo apt-get install samba**

**sudo smbpasswd -a USERNAME**

(USERNAME,is your actual username.)

**mkdir /home/USERNAME/test**

Next, backup copy of the original smb.conf file to your home folder, 

**sudo cp /etc/samba/smb.conf ~**

Now use your text editor of choice to edit smb.conf:

**sudo gedit /etc/samba/smb.conf**

Once smb.conf has loaded, add this to the very end of the file:
[B]
[test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes
[/B]
(Keep in mind no spaces between the lines and also that there should be a single space both before and after each of the equal signs.)

These settings will share the test folder we created earlier, and give your username and your username alone permission to read and write to the folder **save smb.conf**, exit the text editor, and restart Samba;

**sudo /etc/init.d/samba restart**

Samba should be working now; try accessing the shared folder from another computer on your LAN.
This worked for my broken samba on 3x 9.10 upgrades and 4 x 9.10 fresh installs, the network has 2 x vin7 machines and 2 x 6p.

---

### Post by RealG187 on 2009-11-05
The host is Windows...

---

### Post by dmizer on 2009-11-06
> **Mr_Bumpy said:**
> 
2. (optional) Make it so you can mount shares using sudo without having to enter your password.  Do this by running **sudo visudo** from a terminal, and adding the following lines at the end:
```
fred	ALL=NOPASSWD:/bin/mount
fred	ALL=NOPASSWD:/bin/umount
```

Never ever ever perform step 2. This is a potentially large security risk. To make the share mountable by anyone without sudo, all you have to do is add the line to /etc/fstab, and include the "users" option like so:
```
//winbox/myfiles /media/myfiles cifs [COLOR="Red"]users[/COLOR],credentials=/home/fred/.auth.winbox.fred,noperm,uid=fred,gid=fred
```
Then this will work:
```
mount /media/myfiles
```

For more information on how to mount shares using CIFS (as Mr_Bumpy shows), follow the howto in the 2nd link in my sig, complete with troubleshooting tips.

---

### Post by dmizer on 2009-11-06
Those of you getting the "Unable to mount location. Failed to retrieve share list from server." error _*[I]**and***[/I]_ are sure that your firewall is configured according to the directions under "Problem 3"; are any of you using Win7 in your network? If so, please see this post: [http://ubuntuforums.org/showpost.php?p=8256694&postcount=34](http://ubuntuforums.org/showpost.php?p=8256694&postcount=34)

---

### Post by RealG187 on 2009-11-06
I tried adding the mounting commands to "~/.bash_profile"

---

### Post by bapoumba on 2009-11-07
Ping [dmizer]("http://ubuntuforums.org/member.php?u=77219") : [http://ubuntuforums.org/showpost.php?p=8265736&postcount=67](http://ubuntuforums.org/showpost.php?p=8265736&postcount=67)
Cheers :)

---

### Post by Fender56 on 2009-11-07
I've read through all 20 pages of this thread and can't get my problem resolved.

I have a clean reinstall of Ubuntu 9.04, a Fedora Core 8 samba server, an Ubuntu 9.04 samba enabled laptop, and two or three Windows XP boxes.

Before the reinstall, I was able to see everything from my desktop 9.04 box from Nautilus.  Now, I can only see the other samba servers on the network.

I can attach to any machine via the smbclient cli, and through nautilus or firefox using smb://hostname with no problem.

I've followed (I think) every word of advice at the start of this thread to no avail.

I'm out of ideas at this point.  Any other pointers would be appreciated.

Below is the output of findsmb.  smbtree produced no output at all.

findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.15.5    TORINO         [FAMILY] [Unix] [Samba 3.0.33-0.fc8]
192.168.15.8    GRANDPRIX      [GRANDPRIX] [Unix] [Samba 3.3.2]
192.168.15.9    MUSTANG        [FAMILY] [Unix] [Samba 3.3.2]
root@MUSTANG:/home/fender# smbtree
Password: 
root@MUSTANG:/home/fender# 

root@MUSTANG:/home/fender# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Config files attached.

---

### Post by Fender56 on 2009-11-08
Well...

I don't know how, but it magically started working again.
Here's what I did, although I've done the same thing a half dozen times or more in the last 24 hours.

1. Uninstalled samba, samba-common, smbclients, fusesmb, smbfs, swat, winbind, and libsmbclient (I *think*).
2. Installed the samba4 counterparts of each.
3. Reboot
4. Ran some samba4-client commands: all failed in some way or other.
5. Uninstalled all the samba4 pieces I could find.
6. Reinstalled all pieces that were uninstalled in step 1
7. Reboot.

Boom.  Magic.

I'm not real sure, but I *might* not have uninstalled fusesmb in previous cycles.  If not, that is maybe what did it this time.  I hate it when things start working again and I can't confidently identify why.

I'm a little reluctant to reboot now.  :)

---

### Post by IstvanL on 2009-11-08
[http://sidux.com/PNphpBB2-viewtopic-t-14163.html](http://sidux.com/PNphpBB2-viewtopic-t-14163.html)

Try this solution. It helped me solving the same issue.
Cheers

---

### Post by dmizer on 2009-11-08
> **IstvanL said:**
> [http://sidux.com/PNphpBB2-viewtopic-t-14163.html](http://sidux.com/PNphpBB2-viewtopic-t-14163.html)

Try this solution. It helped me solving the same issue.
Cheers

You shouldn't need the client lanman auth options unless you're using a very old [noparse](Win98)[/noparse] computer as your Samba server. In my opinion, the security risks of enabling file sharing on a Win98 computer is extreme and inadvisable even in a trusted network. You should either upgrade the Win98 machine, or remove it from the network and use it as an independent workstation.

Some NAS devices have this problem, but there are other ways around that.

Thanks though.

---

### Post by dmizer on 2009-11-08
> **bapoumba said:**
> Ping [dmizer]("http://ubuntuforums.org/member.php?u=77219") : [http://ubuntuforums.org/showpost.php?p=8265736&postcount=67](http://ubuntuforums.org/showpost.php?p=8265736&postcount=67)
Cheers :)

Sweet! :)

---

### Post by Lvcoyote on 2009-11-08
Using Ubuntu 9.10, just installed this afternoon.

When I go to places/network a window opens and shows icons for the two Windows machines on the network. When I try to acces them it will not let me in.  I have a XP machine, a Win7 machine, and this Ubuntu machine  all hard wired to the router.  The two windows machines are indeed assigned to WORKGROUP.  I checked the SMB.CONF file and it reads workgroup=WORKGROUP.  I have the two windows machines working perfectly, sharing files, printers, and anything else.... all that is good.  I'm just trying to be able to share files from windows shared folders to Ubuntu

My question at this point, is which steps on the first page do you suggest I start with???

---

### Post by Lvcoyote on 2009-11-09
dmizer,
Thanks so much for this post.....  after I posted above I started going through your options one by one, and finally I am able to navigate the shared folders on the XP machine.  Sadly I am still unable to browse the Win7 machine.

Some more information....  The XP machine only had the "MyDocuments" folder shared, the Win7 machine has an entire spare hard drive shared, and thats the one I cant get in to.  Any help would be appreciated!

---

### Post by Runaway1956 on 2009-11-09
Great how-to!  Many thanks!

I've diddled with my network shares off and on for months.  My workaround for this frustrating problem, was to access the network from a virtual machine.  For some reason it worked for me, despite the fact that the Ubuntu host machine couldn't see the network.

Oh well - I followed instructions posted here, and everything works beautifully now!

Thank you, thank you, thank you!


Dmizer - I took the liberty of copy/pasting your post to another forum, and gave you credit for the solution, along with a link to this article.  View here, if you like:
[http://www.mauisun.org/vbb/newthread.php?do=postthread&f=58](http://www.mauisun.org/vbb/newthread.php?do=postthread&f=58)

And, did I say, "Thank you!"  :)

---

### Post by Hawaiisnowstorm on 2009-11-09
dmizer

I'm in really bad need of help and from reading through this thread, you seem to be the best shot.  Long story short I've been trying for about a month now to get my Linux boxes (a desktop and laptop) to see / be seen by the windows computers on my home network.  So far nothing as worked long term -  a fix will work temperately but then not work the next day -  and I'm at the point to where I don't know if its something I'm doing wrong or I have so many “fixes” on my desktop that its a hopeless battle.  I just updated my netbook to 9.10 hoping that might help to have a fresh start for the laptop to see any thing, but again nothing.

My Desktop is 9.04 with Samba 2:3.3.2 – name is HDS-Linux
My Netbook is 9.10 with Samba 2:3.4.0 – name is NetLinBox

I attached my smb config files if they are needed.

---

### Post by dmizer on 2009-11-10
> **Lvcoyote said:**
> dmizer,
Sadly I am still unable to browse the Win7 machine.
Try this possible fix: [http://ubuntuforums.org/showpost.php?p=8256694&postcount=34](http://ubuntuforums.org/showpost.php?p=8256694&postcount=34)

> **Hawaiisnowstorm said:**
> dmizer

My Desktop is 9.04 with Samba 2:3.3.2 &#8211; name is HDS-Linux
My Netbook is 9.10 with Samba 2:3.4.0 &#8211; name is NetLinBox

I attached my smb config files if they are needed.

First of all, have you been through all the fixes in the first post in this thread? If not, do so.

A couple of minor changes I can suggest to your smb.conf files.

On both HDS-Linux and NetLinBox, look for this line:
```
;   name resolve order = lmhosts host wins bcast
```
and add this line directly below it:
```
   name resolve order = lmhosts wins bcast host
```

On HDS-Linux, remove this line:
```
   usershare owner only = false
```
Reboot after making these changes.

---

### Post by Lvcoyote on 2009-11-10
dmizer,
when I open the samba.conf file, I see the global heading, but what is this "stanza" about??  The word stanza appears no where in thesamba.conf file..... is it something I need to add??  Exactly how and where should it be added???

If you look at the link you provided, it says...
> 
Those of you having problems with Win7, please try adding the following options to your [global] stanza in /etc/samba/smb.conf:
Code:

domain master = no
local master = no
preferred master = no
os level = 0


The "stanza" reference has me confused......sorry.....

---

### Post by dmizer on 2009-11-10
"Stanza" just means section. So look at your /etc/samba/smb.conf file and just add those options somewhere below here:
```
#======================= Global Settings =======================

[global]
```

---

### Post by Lvcoyote on 2009-11-10
Ok I added those lines just after the word global, still not working, getting the pop up window that says"
Unable to mount
failed to receive share list from server

Here is a copy of my smb.conf file

---

### Post by dmizer on 2009-11-10
> **Lvcoyote said:**
> 
Unable to mount
failed to receive share list from server

That's usually a firewall issue. Do you have a firewall enabled on any of your computers anywhere in your network? If so, try disabling it for testing purposes.

---

### Post by Lvcoyote on 2009-11-10
> **dmizer said:**
> That's usually a firewall issue. Do you have a firewall enabled on any of your computers anywhere in your network? If so, try disabling it for testing purposes.

The XP machine has the firewall on and it accesses it fine, I turned off the firewall on Win7 and it still gave me the same error.

---

### Post by Lvcoyote on 2009-11-10
I turned off the Win7 Firewall again and rebooted the machine, went to the Ubuntu machine and tried again and it still will not let me in.....  I attached the SMB.CONF in text format a couple posts ago if you would like to have a look...... thanks dmizer!

---

### Post by audiomick on 2009-11-10
Hallo dmizer.
Just been browsing the thread again, and feel inclined to mention, because it isn't said often enough:

Love your work!!!

Thanks from all of us :-)

---

### Post by dmizer on 2009-11-10
> **Lvcoyote said:**
> I turned off the Win7 Firewall again and rebooted the machine, went to the Ubuntu machine and tried again and it still will not let me in.....  I attached the SMB.CONF in text format a couple posts ago if you would like to have a look...... thanks dmizer!

For some reason, I've been seeing this mistake quite frequently lately. Please comment out this line by putting a semicolon ";" in front of it:
```
[COLOR="Red"]**;**[/COLOR]   dns proxy = no
```

Restart Samba, or reboot after making this change.

---

### Post by Hawaiisnowstorm on 2009-11-10
> **dmizer said:**
> Try this possible fix: [http://ubuntuforums.org/showpost.php?p=8256694&postcount=34](http://ubuntuforums.org/showpost.php?p=8256694&postcount=34)



First of all, have you been through all the fixes in the first post in this thread? If not, do so.

A couple of minor changes I can suggest to your smb.conf files.

On both HDS-Linux and NetLinBox, look for this line:
```
;   name resolve order = lmhosts host wins bcast
```
and add this line directly below it:
```
   name resolve order = lmhosts wins bcast host
```

On HDS-Linux, remove this line:
```
   usershare owner only = false
```
Reboot after making these changes.

Yes I had tryed those fixes before.  How ever, those few minor changes you suggested fixed the problem!!!! Thank you!! :D:KS

---

### Post by Lvcoyote on 2009-11-10
Well, I didnt put it there.....LOL.  It must be what 9.10 installs from the get go....????

---

### Post by Lvcoyote on 2009-11-10
Ok, I commented that out with a ";" still no joy.....:confused:

Updated SMB.CONF file in text format is attached.....

---

### Post by Muahdib on 2009-11-11
hi all

I have been searching and searching for a howto.. this one is close, and sense I cant find what im looking for I thought I would ask here. 

I have ubuntu running on one pc and vista(which I hate) on my wifes pc. I have a printer on my ubuntu system and want to share it over our small home network with her vista machine. is there a howto for that? if not can you help me?

thanks

---

### Post by mgmiller on 2009-11-11
> I have ubuntu running on one pc and vista(which I hate) on my wifes pc. I have a printer on my ubuntu system and want to share it over our small home network with her vista machine. is there a howto for that? if not can you help me?Take a look here and see if it helps:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Also I think you may get more useful help about having the printer on Ubuntu and sharing it with windows here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dmizer on 2009-11-11
> **Muahdib said:**
> hi all

I have been searching and searching for a howto.. this one is close, and sense I cant find what im looking for I thought I would ask here. 

I have ubuntu running on one pc and vista(which I hate) on my wifes pc. I have a printer on my ubuntu system and want to share it over our small home network with her vista machine. is there a howto for that? if not can you help me?

thanks

Just use CUPS to share your printer, it will work fine with Windows. Samba is too much of a pain.

Here's how to configure the Ubuntu print server: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server)
Here's how to configure the Windows client: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine)

More information: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by evilmonk on 2009-11-12
I have a weird problem, that samba won't work and the shares won't get shown on a windows machine (I tried on both XP and W7) until I log into SSH and do "sudo service samba restart". I have even tried disabling in on bootup and adding a line to rc.local, but it still doesn't work until I restart it manually in a shell.

---

### Post by oldsoundguy on 2009-11-12
> **evilmonk said:**
> I have a weird problem, that samba won't work and the shares won't get shown on a windows machine (I tried on both XP and W7) until I log into SSH and do "sudo service samba restart". I have even tried disabling in on bootup and adding a line to rc.local, but it still doesn't work until I restart it manually in a shell.


Your Windows machines also have to be set up for networking or the Linux machines can not see them.

I run 4 Linux machines, 2 windows machines, 5 printers and can and DO move information and files between them all the time and can print to any printer from any computer. (The key is making ALL computers members of the SAME network .. default for Windows is MSHome and default for Linux is Workgroup.  You have to change one set to match the other or they can not talk to each other.)

---

### Post by evilmonk on 2009-11-12
> **oldsoundguy said:**
> Your Windows machines also have to be set up for networking or the Linux machines can not see them.

I run 4 Linux machines, 2 windows machines, 5 printers and can and DO move information and files between them all the time and can print to any printer from any computer. (The key is making ALL computers members of the SAME network .. default for Windows is MSHome and default for Linux is Workgroup.  You have to change one set to match the other or they can not talk to each other.)
I have Ubuntu Karmic running as a file/print server, and the rest of the machines are with Windows, and they all use the same workgroup ("HOME"). The problem isn't that Windows machines cannot see the server at all, but with Samba not being properly run after I reboot or power on my server. After I manually restart samba via shell everything is working normally. Looks like samba is having some trouble with rights.
I hate to reinstall things after I have almost successfully configured them (the shares are working and user passwords are set), but it looks like this is the only way of solving the problem.

---

### Post by euphgeek on 2009-11-12
I just recently installed Karmic and am having problems with Samba.  I followed all the steps in your initial post but I'm still not able to connect from a Windows computer to my Ubuntu computer.  I can connect from Ubuntu to Windows without any problem though.  The problem is that when I try to connect to the Samba server, it asks me for a username and password like it used to and then it gives me the error "More data is available."  If I do it from the command line it gives me the error "System error 234 has occurred."

I did some troubleshooting on my own and found that Karmic appears it may only be listening on an IPv6 line.  Here are the relevant lines from netstat -an:

```
udp        0      0 192.168.15.100:137      0.0.0.0:*
udp        0      0 192.168.15.100:138      0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*
tcp6       0      0 :::139                  :::*                    LISTEN
tcp6       0      0 :::445                  :::*                    LISTEN
```Now in this thread: [http://ubuntuforums.org/showthread.php?t=1317225](http://ubuntuforums.org/showthread.php?t=1317225) it was suggested to add lines into the hosts file but I tried that and it didn't work.  Besides, my router is my DNS server so I don't normally use the hosts file for name resolution.  Any suggestions?

---

### Post by Crandes on 2009-11-12
I had the same problem and the ipv6 issue got cleared out after getting a hint from Fedora forums:

[http://forums.fedoraforum.org/showpost.php?p=1284182&postcount=15](http://forums.fedoraforum.org/showpost.php?p=1284182&postcount=15)

Since I already had interfaces = 192.168.0.0/24 set up, just enabling "bind interfaces only = true" did the trick for me.

Hopefully it helps.

---

### Post by Muahdib on 2009-11-12
> **dmizer said:**
> Just use CUPS to share your printer, it will work fine with Windows. Samba is too much of a pain.

Here's how to configure the Ubuntu print server: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server)
Here's how to configure the Windows client: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine)

More information: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

thank you much joy

---

### Post by euphgeek on 2009-11-13
> **Crandes said:**
> I had the same problem and the ipv6 issue got cleared out after getting a hint from Fedora forums:

[http://forums.fedoraforum.org/showpost.php?p=1284182&postcount=15](http://forums.fedoraforum.org/showpost.php?p=1284182&postcount=15)

Since I already had interfaces = [192.168.0.0/24]("http://192.168.0.0/24") set up, just enabling "bind interfaces only = true" did the trick for me.

Hopefully it helps.

I tried the solutions at your link but they didn't work.  I'm still getting the exact same errors.

---

### Post by Crandes on 2009-11-14
Do you still see tcp6 entries when you type netstat -an?

If not, then I assume you have other issues causing the problem.

**UPDATE:** I noticed on my other server that apparently the 9.10 upgrade has changed security setting to 'SHARE' instead of 'user' which was causing the 'More data is available' problem. Changing that back to 'security = user' cleared the problem out.

---

### Post by Lvcoyote on 2009-11-14
I never have been able to get Ubuntu 9.10 to connect with my Win7 machine.  Today I checked for updates and there was a boat load of Samba updates......cool, I'm thinking, maybe we'll get this working now..... What a pipe dream that was.  Not only can I still not connect to the Win7 Machine it broke the working share I had with another machine that has XP.  I went back through the first post and made sure all the changes that originally got XP to be seen and accessed from the Ubuntu machine, and they are all still there.  Now I'm totally hosed as far as this Ubuntu box sharing anything with Windows on it.......

In typical Linux fashion, it seems a concerted effort is made by those doing the development to make things as difficult as possible.....

---

### Post by Crandes on 2009-11-14
My years old smb.conf was screwed up by ipv6 and/or security = share issues which were mentioned above. I haven't had any problems with different versions of Windows including Vista and 7, all were working fine before 9.10 upgrade. Gladly it is now working again so I can freeze my config for the next few years or so :) I wish I just was wise enough not to upgrade perfectly working setup in the future ;)

---

### Post by dmizer on 2009-11-14
> **Lvcoyote said:**
> Now I'm totally hosed as far as this Ubuntu box sharing anything with Windows on it.......

In typical Linux fashion, it seems a concerted effort is made by those doing the development to make things as difficult as possible.....

Disable any and all firewalls. You don't really need them if your clients are in a trusted network anyway. I have no problems with my Ubuntu 9.10 test machine and my Win7 machine.

---

### Post by euphgeek on 2009-11-14
> **Crandes said:**
> Do you still see tcp6 entries when you type netstat -an?

If not, then I assume you have other issues causing the problem.

**UPDATE:** I noticed on my other server that apparently the 9.10 upgrade has changed security setting to 'SHARE' instead of 'user' which was causing the 'More data is available' problem. Changing that back to 'security = user' cleared the problem out.

Yes, I still see the tcp6 entries.  The only difference is I no longer see any entries for port 445.  Also, my smb.conf is the same one I was using with 8.04 with no problems and security is already set to user.

---

### Post by Lvcoyote on 2009-11-15
> **dmizer said:**
> Disable any and all firewalls. You don't really need them if your clients are in a trusted network anyway. I have no problems with my Ubuntu 9.10 test machine and my Win7 machine.

You mentioned trying that several posts back, and I did disable the firewall on both the XP and Win7 machines, still no joy.

---

### Post by Lvcoyote on 2009-11-15
This morning I turned the Ubuntu machine on and tried again, now it works perfectly......LOL.  I can browse both the XP and Win7 machines......I guess it just needed a good nights sleep.  Anyway, thanks for all the help.....seems to be working now!!

---

### Post by Andysan on 2009-11-22
Hi,

I have the dreaded failed to retrieve share list from server error when trying to browse my WORKGROUP.  I have made sure that the correct workgroup name is in smb.conf (in the correct case) and have added the UDP/TCP rules to the firewall:
```

sudo ufw allow proto xxx to any port xxx from xxx.xxx.x.x/xx
sudo ufw allow proto xxx to any port xxx from xxx.xxx.x.x/xx
sudo ufw allow proto xxx to any port xxx from xxx.xxx.x.x/xx
sudo ufw allow proto xxx to any port xxx from xxx.xxx.x.x/xx

I am able to browse to shares in Nautilus by entering smb://192.xxx.x.x.

The output of findsmb is as follows:
[CODE]
    *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
```


Have also tried copying the smb.conf file from a working Intrepid machine.  Am running Karmic, can anybody suggest a resolution please?  This is the only problem i've yet to solve.

Many thanks in advance.

EDIT - Resolved by doing a full reinstall.  Must have been something to do with me upgrading.

---

### Post by edioilha on 2009-11-22
So many THX

It solved my one week problem, I mean I was searching solution for about one week.
Thank God I found your post.
Ur the Best!

Linked to [http://ubuntuforum-br.org/index.php?topic=50885.msg335800#msg335800](http://ubuntuforum-br.org/index.php?topic=50885.msg335800#msg335800)
I hope you dont mind!
Brazil Ubuntu´s forum
A lot of guys trying to solve this issue
Didnt have a good post like yours
Sorry about my poor English

Thx

EdioIlha

---

### Post by peterroots on 2009-11-23
I have been trying to fix this on and off for weeks first on a jaunty machine then on a karmic (same machine just dist upgrade)

All is fine with the firewall off (which I did not want as computer is a laptop and not always in my nice safe network)

No samba shares with the firewall
This did not work
sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24

But this from a post somewhere in the middle of this thread did
sudo ufw allow proto udp from 192.168.1.0/24 port 137 to any
sudo ufw allow proto udp from 192.168.1.0/24 port 138 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 139 to any
sudo ufw allow proto tcp from 192.168.1.0/24 port 445 to any

Thanks for all the time you have put into providing all the information and stimulating others to contribute

---

### Post by VastOne on 2009-11-23
> **dmizer said:**
> Disable any and all firewalls. You don't really need them if your clients are in a trusted network anyway. I have no problems with my Ubuntu 9.10 test machine and my Win7 machine.

Dmizer, I appreciate everything you have done on this forum and all the help... 

I have followed everyone of your guides to a T and other suggestions as well and cannot get Ubuntu to connect to the Win 7 share getting the "Failed to retrieve share list from server"

I have never been able to get Win 7 to see any of the Ubuntu shares in any browse function but I can connect to them via IP \\192.*.*.*\share name

I am not running any type of firewall

I have never setup Samba before so this Win 7 machine and my Ubuntu Karmic are all I have ever used Samba with fwiw...

Not looking for any answer as all I needed was to get Win7 to back up to the Ubuntu machine and I can do that...

I will say that networking in the Nix world could stand some improvement?!?!? (ducking now):-#:shock:

smbtree does show all of the Win7 shares including printers

---

### Post by MrGrumpyArse on 2009-11-23
Hi, dmizer and all

Firstly  a big thanks to the author for this tutorial, using it has improved my home network a great deal.  I am however left with one irritating issue, which despite re-reading the previous 20+ pages numerous times ( and assorted links) I am unable to resolve -

I currently have on my home network the following

Ubuntu 9.10 64 bit pc
Vista Home premium 32 bit pc
XP sp3 32 bit pc (laptop wireless)
Windows 7 Ultimate 64 bit pc

All Except the Windows 7 pc can view and browse to each other and share files.
The Windows 7 pc can see and browse / share all other pc`s (including the Ubuntu pc)

The Ubuntu pc can view and share files with all pc`s except the Windows 7 pc, which is shown in nautilus when browsing the network, but attempting to access it displays a user name / password prompt!

The Windows 7 pc has firewall off, public folder sharing on, password protected sharing off, Guest account currently on, but have tried it both ways.  The Windows 7 pc has only 2 accounts, one of which is the guest account, neither of which require passwords.  I have also tried having a password and using this at the username / password prompt from the Ubuntu pc.  No combination of username / password will allow the Ubuntu pc access.

Interestingly if i do the smbtree command from terminal everything shows pretty much as expected on all pc`s except the Windows 7 pc which just shows - \\DYLAN-PC with no shares listed.  
But like i said it`s public plus 1 manually shared folder is/are accessible from all the other Windows pc`s.

I notice a number of Windows 7 issues throughout this topic and have tried a number of the suggestions but am still left with the impassable username / password prompt.

If there are any further suggestions or advice i would be very grateful as ive been trying for days on end to resolve this.  One simple folder on the Win 7 pc accessible from the Ubuntu pc would be just fine

Many thanks

MrGrumpyArse  / Mark

---

### Post by dmizer on 2009-11-23
I had shares working perfectly with Win7 for a while, but they are broken again. I won't have time to look into this seriously for a few days. Sorry. Most problems I've run into with Win7 have been related to firewall or network security (anti-virus) issues, but there are a handfull that don't seem to fit in that category.

To anyone with problems connecting to Win7 shares: What version of Win7 are you using?

---

### Post by MrGrumpyArse on 2009-11-24
Hi Dmizer and all

Following up from my previous post #240 I have been spending far too long on Google and have noticed the following points -

My Karmic 64 bit has installed Samba 3.4.0

The latest stable version of Samba is 3.4.3 ( source - [http://www.samba.org/](http://www.samba.org/))

In the release notes for Samba 3.4.3 is the following (source - [http://www.samba.org/samba/history/samba-3.4.3.html](http://www.samba.org/samba/history/samba-3.4.3.html) ) -

> This is the latest stable release of Samba 3.4.

Major enhancements in Samba 3.4.3 include:

   o Fix trust relationships to windows 2008 (2008 r2) (bug #6711).
   o Fix file corruption using smbclient with NT4 server (bug #6606).
   o Fix Windows 7 share access (which defaults to NTLMv2) (bug #6680).

Do you think this is relevant to my or others Win 7 related issues ?

Would it be worth considering compiling 3.4.3 from source ?

I would be interested in any knowledgeable replies, 
I personally am new to Linux so much of this is beyond the scope of my knowledge, although I have compiled and installed a couple of programs successfully via tutorials.

Any thoughts

Regards

Mark

---

### Post by VastOne on 2009-11-24
MrGrumpyArse

(I Love that!)

Great questions and I am looking forward to the answers to this as well

No matter what I do in reading every resolution from here and Google I am still not seeing what everyone else seems to resolve.

I now have a twitch on my eye that is of grave concern.....

I will try the new Samba to see if that resolves it...

---

### Post by VastOne on 2009-11-24
> **dmizer said:**
> I had shares working perfectly with Win7 for a while, but they are broken again. I won't have time to look into this seriously for a few days. Sorry. Most problems I've run into with Win7 have been related to firewall or network security (anti-virus) issues, but there are a handfull that don't seem to fit in that category.

To anyone with problems connecting to Win7 shares: What version of Win7 are you using?

Win 7 Ultimate 64 bit

---

### Post by MrGrumpyArse on 2009-11-24
> MrGrumpyArse

(I Love that!) Its what my better half calls me - and as they say " if the cap fits, wear it" ;)

> I will try the new Samba to see if that resolves it... Fingers crossed!

> To anyone with problems connecting to Win7 shares: What version of Win7 are you using? Windows 7 64 bit Ultimate



Regards

MrGrumpyArse / Mark

---

### Post by beh_botehnga on 2009-11-25
Problem 3 - Jaunty/Karmic solution works perfectly for me.. thanks a lot...

---

### Post by VastOne on 2009-11-25
> **MrGrumpyArse said:**
> Its what my better half calls me - and as they say " if the cap fits, wear it" ;)

Fingers crossed!

Windows 7 64 bit Ultimate



Regards

MrGrumpyArse / Mark

With a kernel update today, I am now able to see the network shares on my Win 7 machine.  I can open the shares of all within that machine with the exception of a specific directory/share I created called UbuntuShare.

I get the following error message...

Could not display smb://xxxxxx/UbuntuShare The file is of an unknown type

As a test, I created a new share on Win7 and I can now access that one no problem...So whatever credentials or smb data of the original UbuntuShare are not resolved but that is no issue as I can simply recreate or work with any new share.

My Samba version is now at 3.4.0 and I did not compile anything to et there I am assuming it was a part of this mornings update package...

I am still unable to browse the Ubuntu shares from Win7 but I can access them through IP so I am not as concerned about that lack of browse capabilities....

Hope this helps....

VastOne

---

### Post by MrGrumpyArse on 2009-11-26
Hi all....

VastOne - 

Glad to hear of your success in connecting to your Win 7 machine, even if connecting from your Win 7 machine to Ubuntu isn't quite as flawless.

For myself, I too received a number of updates including the Kernel, although my installed version of Samba was already 3.4.0 so wasn't changed.  

But after reading your reply I was quite optimistic about finally resolving my Win 7 networking woes.  Unfortunately nothing has changed at my end.  I can still see the Win 7 machine but attempting to connect to it receives the previously described password / username prompt.

I have checked and double checked the Win 7 sharing settings until i can see them in my sleep, but still no go.  I find it doubly frustrating that all my other Windows machines connect to it without fail or username/password requests.

Ironically considering your reply, my Win 7 machine can connect to the Ubuntu shares at each and every attempt.

I am now at a loss what to try next, but have noticed an alpha version of Samba 4 in Synaptec, that is becoming more tempting with every failed attempt.

I think probably my next step will be to un-install Samba etc and then re-install and start the tutorial again from scratch, but I fear i may be grasping at straws!

Either way I am not beaten yet (this comment is subject to review ;)) and will continue in my attempts to beat the Win 7 machine into submission.

I fear that if and when this is resolved it will turn out to have been caused by some embarrassing oversight or omission on my part, and rest assured I shall return and post the error so others may have a laugh.   But until then i shall continue telling myself that with every failed attempt something new is learned.

Regards

MrGrumpyArse / Mark

---

### Post by VastOne on 2009-11-27
Mark

New shares on Win7 are inaccessible also?  

The only things I have done to the Win 7 was the change in security policy following this guide - 

[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

and these changes in this forum - 

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/dfd79bc1-cf36-42b7-9911-346912f4def6](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/dfd79bc1-cf36-42b7-9911-346912f4def6)

---

### Post by jmarks on 2009-11-30
Dear dmizer,
I am posting to this incredibly helpful thread in the hopes that you will be able to answer my samba/winbind question. 
I upgraded a fully functional 64-bit 8.04 to 9.04 without a problem. When I updated to 9.10, however, I got the following errors:
```

errors were encountered while processing:
samba 
winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. trying to recover
setting up samba (2:3.4.0-3ubuntu5.1) ...
 *Starting Samba daemons
    ...fail!
invoke-rc.dL initscript samba, action "start" failed.
dpkg: error processing samba (--configure);
  subprocess installed post-installation script returned error exit status 1
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
  *Starting the Winbind daemon winbind
   ...fail!
invoke-rc.d: initscript.winbind, action "start" failed.
dpkg: error processing winbind (--configure);
  subprocess installed post-installation script returned error exit status 1
Errors were encountered whle processing:
    samba
    winbind
```Please note that I do not seem to be having issues in accessing my windows shares on my home network, but i do get this message with every package update, and it bugs me.

In 8.04 I had edited etc/samba.conf to read the following, and when I upgraded to 9.04, I elected to keep it.
My etc/samba/smb.conf is:
```
[global]
   workgroup = markshome
   netbios name = jmarks-desktop
   server string = anonymous file server
   security = user # was security= share
usernamemap = /etc/samba/smbusers  # this line added for user-level share
   printing = cups
   printcap name = cups
   load printers = yes

[common_share]
   path = /sharedfiles
   comment = anonymous share for all users
   public = yes
   writeable = yes
   browseable = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

#==================================Share Definitions
==================================================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. this will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes
valid users = %S
writeable = yes
```I really would like to understand this problem.

Thanks so much for your help.

---

### Post by MrGrumpyArse on 2009-12-01
Hi again all

Thanks Vastone for the links, 

However i have already adjusted those settings, different links but same info.  Unfortunately they didn't cure my issue.  

I am currently trying to build Samba 3.4.3 from source.  I managed this once, but due to inexperience in these things I used "make install" and had no idea where the program had installed to, or how to remove it :oops:  Anyway some more time spent on google and i think ive removed it successfully "make uninstall" from the source directory.

Now equipped with a bit more knowledge via this link -

 [http://tuxradar.com/content/compile-source-code-and-solve-problems](http://tuxradar.com/content/compile-source-code-and-solve-problems)

I will try again using "checkinstall" although im still a bit confused as to which elements of Samba my downloaded source code installs, and what I need to remove via synaptic first as there appears to be quite a few parts to samba listed.  

Maybe I will remove them all and see what happens.  I suppose I can always re-install them if required.

If anyone would like to advise me on this it would be appreciated

Regards

MrGrumpyArse / Mark

---

### Post by tamanaco on 2009-12-01
I read most of the thread, but I still have problems authenticating from a laptop running Ubuntu 9.10 to a laptop running Windows 7. The Windows 7 laptop can browse and access the folder shares in the ubuntu laptop without any issues. (The only thing is that it does not show the $print share in the Ubuntu laptop) I have no issues accessing the shares from an XP machine on the Ubuntu machine and vice-versa (including the ability to see the $print share in the Ubuntu laptop from Win XP machine) After following the instructions on the first page I was not able to access the Windows shares from Win 7, but only after I executed the command "sudo smbpasswd -a username" to add a user and password to the Samba access list... after this most of the problems of access "from" Win 7 went away. I lost a couple hours trying to access Ubuntu from Win 7 because of this. 

Btw, I have changed the encryption level to 40/56 and the "LM and NTLM &#8211; use NTLMV2 session security if negotiated in windows plus the suggested registry changes. I also made changes to the smb.conf (workgroup, netbios name, reordered "wins" in the name resolve name line and set browseable to yes) Made changes to the nsswitch.conf too. 

Don't know what else to try. Did I miss something obvious? Is there an easy way to install a later version than the default 3.4.0 without having to jump too many hoops? Something like an "optional" source that can be added to the Software Sources app -> Other Software tab to download and install a later version of Samba and its dependencies. Or of course, easy to follow step by step guide on how to download and install the latest and greatest version of Samba.

---

### Post by tamanaco on 2009-12-02
> **MrGrumpyArse said:**
> 
I am currently trying to build Samba 3.4.3 from source.  I managed this once, but due to inexperience in these things I used "make install" and had no idea where the program had installed to, or how to remove it :oops:  Anyway some more time spent on google and i think ive removed it successfully "make uninstall" from the source directory.

Now equipped with a bit more knowledge via this link -

 [http://tuxradar.com/content/compile-source-code-and-solve-problems](http://tuxradar.com/content/compile-source-code-and-solve-problems)

I will try again using "checkinstall" although im still a bit confused as to which elements of Samba my downloaded source code installs, and what I need to remove via synaptic first as there appears to be quite a few parts to samba listed.  

Maybe I will remove them all and see what happens.  I suppose I can always re-install them if required.



I'm in the same boat... I downloaded 3.4.3 and tried the steps below, but I guess I'm missing something.

1. Downloaded the samba-3.4.3.tar.gz to a temp folder
2. sudo tar xzvf samba-3.4.3.tar.gz
This extracted the tar.gz file to a subfolder called samba-3.4.3... I then changed directory to /temp/samba-3.4.3/source3  (took me a little while to figure this out) From this folder I executed the following commands.
3. sudo ./configure
4. sudo make
5. sudo make install

All of the steps above executed without a hitch and I think something was installed, but I don't think it installed over the existing installation of 3.4.0 which I had installed using the command "sudo aptitude install samba". If I run the command "smbd -V" it returns version 3.4.0. I "think" the above installed in the /usr/local/samba, but I'm not sure. I guess I did not followed the right steps... anyone care to list the steps required so that the existing 3.4.0 installation is updated to 3.4.3 using the above mentioned source file or any other method that works. Samba 3.4.3 "appears" to have a fix that addresses the specific issue I'm experiencing with win 7. Btw, I'm running ubuntu 9.10

Thanks in advance

---

### Post by SR_ELPIRATA on 2009-12-02
Oh boy, I finally got to work this and its being a nightmare.... has anyone asked why the firewall change in 9.04? networking was so easy with 8.10 :(

Ok, this is my situation...

My desktop, ubu 9.04, firewall is disabled (terminal shows same data as example), then I use a VM with virtualbox for XP, which also has the firewall set as OFF and there's no antivirus installed, so nothing else in the way.

If I try to get into the VM from Ubuntu... I get the "Failed to retrieve shares" and cant see anything inside. If I try the same from the VM with XP... it tells me that I may not have access to that machine.

Both could see each other and both are in the same workgroup, I always use WORKGROUP for all xp machines. Did the changes for Problem 3 (all 3) and Problem 2 only the netbios name.

After a couple restarts I cannot see the other PC from neither one of them. In fact, from Ubuntu I can't see the WORKGROUP anymore (when clicking on WINDOWS NETWORKS) From the VM I can see only that same machine.

I honestly dont understand why the change, it was so easy to setup the shares with 8.10... :(

---

### Post by MrGrumpyArse on 2009-12-03
Tamanaco -

I am an absolute novice at this but ill share what little I have learned.  I followed the same steps as you, with pretty much the same result.  I did belatedly learn that if you use the command "make checkinstall" instead of "make install" a .deb file is created and installed (which allows you to remove the program via synaptic package manager).

Directly after you issue "make checkinstall" you are prompted to edit various "fields" which is how the package is identified within synaptic.  I filled these in incorrectly so the package showed in synaptic as "source 3" not "Samba 3.4.3"  as i had intended, but I found it eventually and was able to remove it, again via synaptic.

I intend to try again from scratch but was hoping someone more knowledgeable may post the correct procedure.

I "believe" you have to remove the elements of Samba from synaptic prior to installing the compiled version.  But I havent tried yet so can't confirm.

_**But i must stress I am a complete novice at this **_and am only sharing what I think is correct.  I would wait for advice from a more knowledgeable source if like me you are unsure how to do this upgrade correctly 

_**My comments really are a case of the blind leading the blind!**_

If however you are more able than me, and complete the "upgrade" successfully please post back and share.

Good luck

MrGrumpyArse / Mark

---

### Post by tamanaco on 2009-12-03
MrGrumpyArse, I just tested using a couple Windows Vista computers  and like Windows XP one can share folders both ways without an issue. The problem is "specific to Windows 7" and Samba 3.4.0 when one tries to access a folder shared from Windows 7 from Ubuntu. I have no issues accessing Ubuntu shares from Windows 7. I agree with you that if we get someone with experience that has successfully upgraded to Samba 3.4.3 on Ubuntu 9.10 environment and post the steps required... we "might" have a solution.

---

### Post by VastOne on 2009-12-03
Just to jump back into this, I am at 3.4.0 Samba and can access Win7 shares from 9.10 but can only "see" the Samba shares if I browse via IP and then they show up no problem and I can connect to them.  This tells me that it is most likely a netbios issue with Win 7

---

### Post by dmizer on 2009-12-04
> **VastOne said:**
> This tells me that it is most likely a netbios issue with Win 7

Most samba issues are directly related to netbios issues, so I entirely agree. I do not know yet how to solve it. It seems to work fine for me in my Win7 virtual machine. It seems like some people are having problems, and some are not, and those are the worst kind of problems to try to track down.

---

### Post by SR_ELPIRATA on 2009-12-04
Any suggestions for me? :)

---

### Post by mikewhatever on 2009-12-05
Lust wanted to say thank you. The changes in smb.conf worked great.:D

---

### Post by jamesisin on 2009-12-06
I am having trouble with Rhythmbox playing music across a Samba share (from 9.10 to 9.10).  I don't suspect it's a Samba problem because other applications are able to play the same files (Movie Player plays anything I dump into it, for instance).  However, folks keep suggesting it's Samba.  Care to take a look at my issue?

[http://ubuntuforums.org/showthread.php?t=1326861](http://ubuntuforums.org/showthread.php?t=1326861)

---

### Post by benmandude on 2009-12-07
Thank you so much, one of those tips in there solved my problems.

---

### Post by RealG187 on 2009-12-08
> **RealG187 said:**
> I tried adding the mounting commands to "~/.bash_profile"Actually forget that, I thought to myself, I need to run the mount command as root upon boot and remembered that's that the /etc/fstab file it for.

I turned these commands
```
sudo mount -t cifs //192.168.239.1/Share /home/mpg/Desktop/Host -o credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg
sudo mount -t cifs //192.168.239.1/Backup /home/mpg/Desktop/Backup -o credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg
```

into these lines
```
//192.168.239.1/Share	/home/mpg/Desktop/Host	cifs	credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg	0	0
//192.168.239.1/Backup	/home/mpg/Desktop/Backup	cifs	credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg 0	0
```

---

### Post by ttbek on 2009-12-09
Hey there I'm having trouble accessing win 7 fileshares, but also vista and xp shares as well.  My problems started with not being able to a find a shared printer on the win 7 comp. Then there was a flurry in uninstallation & reinstallation so and I still can't access that printer.  
Enter kunji's password: 
Anonymous login successful
Domain=[HIKARI] OS=[Windows 7 Ultimate 7100] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[HIKARI] OS=[Windows 7 Ultimate 7100] Server=[Windows 7 Ultimate 6.1]

    Server               Comment
    ---------            -------
    PANDASU              

    Workgroup            Master
    ---------            -------
    MSHOME               TOSHIBA-USER
    WORKGROUP            RED


kunji@kunji-desktop:~$ smbtree
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
Enter kunji's password: 
kunji@kunji-desktop:~$ 

sudo gedit /etc/samba/smb.conf

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP
    netbios name = kunji-desktop

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts wins bcast host

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
    log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
    max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
    syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
    panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
    encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

    obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
    unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
    pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
    map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
    comment = All Printers
    browseable = yes
    path = /var/spool/samba
    printable = yes
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    valid users = kunji, nobody
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

gksudo gedit /etc/nsswitch.conf

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Any help would be much appreciated.

---

### Post by jamesisin on 2009-12-09
I don't think I can help with your Samba issue (though I will continue to watch this thread), but I did write a post on using Windows printers from an Ubuntu desktop:

[http://www.soundunreason.com/InkWell/?p=767](http://www.soundunreason.com/InkWell/?p=767)

(I don't have very good luck accessing the printer on my SBS 2003 server using the two methods mentioned in my post, so if anyone has any suggestions for improving these methods you can PM me or comment on my blog.)

---

### Post by ttbek on 2009-12-09
Hey jamesisin, those were actually both methods I attempted before I started fiddling with my Samba and Cups stuff to begin with and I attempted between changes.  At one point the Samba option to connect to the printer was gone as well, I probably didn't have all the packages installed at that point, but I got that much fixed shortly before posting here.  Thanks though all the same.

---

### Post by dmizer on 2009-12-09
Don't use samba for printing. It is an extreme pain to get working.

Use the native cups interface. It works fine with Windows printers. You may have to connect the printer directly to your computer in order to make sure you get the right drivers loaded, but after that you'll be fine.

---

### Post by ttbek on 2009-12-09
Hey dmizer, how do you use cups for it?  I've been going to system administration printing and trying everything in there.  Also I had broken other things in the process, though things are mostly fixed now. These lines needed to be commented: 

# You may want to add the following on a Linux system:
         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

and I might have been missing components, since I also installed a few others.  Now I can see other comps. on my network, but I can't log into them, except for one.  Both are win 7 machines and I can access them from each other and from a ps3.  One shouldn't even have required a password but I kept reading that you needed one on the win comp to access it, so I tried making one, but no success. I get the login dialog asking for username, domain and password and have tried the correct ones and many possible variations.  I also read this was possibly due to a bug in Samba and to install the proposed updates, so I did that, still no success.  
Thanks for all the help dmizer, I saw you've been maintaining this thread for a long time now.

---

### Post by jmarks on 2009-12-09
I am so stuck. My log.winbindd reads
```

  winbindd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/12/09 21:30:08,  0] ../lib/util/params.c:335(Parameter)
  params.c:Parameter() - Invalid parameter name in config. file.
[2009/12/09 21:30:08,  0] winbindd/winbindd.c:1248(main)
  error opening config file
```My log.nmbd reads the same:
```

  nmbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/12/09 21:31:20,  0] ../lib/util/params.c:335(Parameter)
  params.c:Parameter() - Invalid parameter name in config. file.
[2009/12/09 21:31:20,  0] nmbd/nmbd.c:858(main)
  error opening config file

```I'm running 9.10, and have no idea how to start debugging this. Could you tell me what the name of the config file that is causing these errors is? 
Thanks so much in advance

---

### Post by ttbek on 2009-12-09
Hey jmarks, I'm not certain, but my guess is the main configuration file, which you can open with: sudo gedit /etc/samba/smb.conf

---

### Post by jamesisin on 2009-12-10
> **dmizer said:**
> Don't use samba for printing. It is an extreme pain to get working.

Use the native cups interface. It works fine with Windows printers. You may have to connect the printer directly to your computer in order to make sure you get the right drivers loaded, but after that you'll be fine.

Ok.  Can you direct me to a tutorial or a how-to for accomplishing this?

---

### Post by dmizer on 2009-12-10
> **jamesisin said:**
> Ok.  Can you direct me to a tutorial or a how-to for accomplishing this?

What printer do you have (make and model)?

---

### Post by dmizer on 2009-12-10
> **jmarks said:**
> I am so stuck. My log.winbindd reads
```

  winbindd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/12/09 21:30:08,  0] ../lib/util/params.c:335(Parameter)
  params.c:Parameter() - Invalid parameter name in config. file.
[2009/12/09 21:30:08,  0] winbindd/winbindd.c:1248(main)
  error opening config file
```My log.nmbd reads the same:
```

  nmbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/12/09 21:31:20,  0] ../lib/util/params.c:335(Parameter)
  params.c:Parameter() - Invalid parameter name in config. file.
[2009/12/09 21:31:20,  0] nmbd/nmbd.c:858(main)
  error opening config file

```I'm running 9.10, and have no idea how to start debugging this. Could you tell me what the name of the config file that is causing these errors is? 
Thanks so much in advance
Please post the contents of /etc/samba/smb.conf

---

### Post by carnagex420x on 2009-12-10
NICE POST! Allot of people have major issues understand Samba or trying to get it working right. Good thread. =D>

---

### Post by jmarks on 2009-12-10
> **dmizer said:**
> Please post the contents of /etc/samba/smb.conf
 Dear dmizer,
 Here is my smb.conf. Thanks so much for your help.
```


[global]
   workgroup = markshome
   netbios name = jmarks-desktop
   server string = anonymous file server
   security = user 
# was security= share
usernamemap = /etc/samba/smbusers  
# this line above added for user-level share
   printing = cups
   printcap name = cups
   load printers = yes

[common_share]
   path = /sharedfiles
   comment = anonymous share for all users
   public = yes
   writeable = yes
   browseable = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

#==================================Share Definitions
==================================================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. this will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes
valid users = %S
writeable = yes
```

---

### Post by caleb2003 on 2009-12-10
Hi, I am having a problem with Samba on ubuntu gnome 9.10 and I am trying to access the files from an original xbox (via xbmc) and it keeps telling me 'workgroup not found'.

I have tried doing it with a kde interface and it works ok (however other things do not which is why I switched to gnome)

I posted my smb.conf file below, please let me know if it is something simple, thanks

---------

[global]
;	netbios name = WORKGROUP
server string = Samba file and print server
security = share
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
;	load printers = yes
cups options = raw
;	printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = yes
username level = 6
password level = 6
encrypt passwords = no
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
;	preferred master = no
;	domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
;	time server = no
name resolve order = wins lmhosts host
;	wins support = no
;	wins proxy = no
dns proxy = no
;	preserve case = yes
;	short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
;	server signing = no
server schannel = no
;	nt pipe support = yes
;	nt status support = yes
;	allow trusted domains = yes
obey pam restrictions = yes
enable spoolss = yes
;	client plaintext auth = no
;	disable netbios = no
follow symlinks = no
update encrypted = yes
;	pam password change = no
passwd chat timeout = 120
;	hostname lookups = no
;	smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
winbind uid = 16777216-33554431
winbind gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
;	winbind refresh tickets = no
;	winbind offline logon = no
guest ok = yes

[homes]
comment = Home Directories
path = /home
read only = no
;	available = yes
;	browseable = yes
;	guest ok = yes
;	printable = no
share modes = yes
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
;	available = yes
browseable = no
;	guest ok = yes
;	printable = no
locking = no
create mask = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
;	browseable = yes
;	writable = no
;	guest ok = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
read only = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u

[mainpclinux]
path = /home/mainpclinux
read only = no
;	browseable = yes
guest ok = yes

[VIDEOS]
path = /home/mainpclinux/Videos/
read only = no

---

### Post by Compist on 2009-12-10
Hi,

I'm running ubuntu 9.10 on a home network and can not browse to my windows shares via "place > network".  I get to Network, then I can see my workgroup, but if I try and go any further, it says "unable to mount location".
I can connect to the PC using it's IP address under connect to server, but I can't do the same using it's name.
This is odd since under 8.04 (the last ubuntu distro I used to use on an old laptop) I could simply browse to it straight from a fresh install.

I tried all the steps at the start of this thread but had no joy at all.  In fact I had to undo the edit to nsswitch.conf because it stopped aMSN from working!

Anyway, anyone got any ideas?  Because i've read through this thread and there still isn't a clear solution anywhere.  I've updated all my packages, and checked all settings on the windows PC and this one.
The workgroup is correct on both machines.
There is no firewall active on the ubuntu machine and the XP has all it's exceptions set up (and other windows machines can access it, just not the ubuntu machine).
The XP machine responds to pings from the ubuntu machine and I can even remotely shutdown the machine via the terminal using the IP.  But once again, even with the terminal, I can not interact with this machine using it's name at all.

This is extremely annoying more than anything because I can work around it just using the IP address, but why is it even happening in the first place?  How come an updated version of ubuntu seems to have lost some basic functionality of earlier distros?

Any solutions that work would be greatly appreciated.  Any additional info needed just ask.
And bare in mind that i'm quite new at this linux game, as i'm normally a windows person, so try to keep it fairly straightforward.  I'm currently trying to shake off Bill Gate's iron shackles so I can continue to use a low spec machine with much better results :)

---

### Post by carnagex420x on 2009-12-11
IDK if anyone has said this yet but on the first page where it says: 
```
 hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
``` .
Gave me a slow network and issues with my browser name resolutions.

Also... its prefreablly a good idea to keep a small smb.conf file.
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553100](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553100)

---

### Post by oldsoundguy on 2009-12-11
not enough time in my life to read all of the responses .. but for 9.10 .. I lost my Windows machines on my network.....

Went to the Windows machines and changed the default network name from MSHOME to WORKGROUP and miraculously everything showed up .. including all of the printers.

---

### Post by Compist on 2009-12-11
> **oldsoundguy said:**
> not enough time in my life to read all of the responses .. but for 9.10 .. I lost my Windows machines on my network.....

Went to the Windows machines and changed the default network name from MSHOME to WORKGROUP and miraculously everything showed up .. including all of the printers.

That's interesting... I shall have to try that as my windows workgroup is also MSHOME.
Although i've changed the workgroup name in Ubuntu to MSHOME as well, so it shouldn't make any difference, unless there's an error with Samba's actual programming and not the config files

---

### Post by Compist on 2009-12-11
YES!
Finally gotten this to work.
I did everything at the start of this thread except I put wins AFTER dns in nsswitch.conf rather than the beginning.  Putting it at the start gave me more problems than it solved, mainly because it caused aMSN to stop working entirely and seemed to slow my internet right down.
It also turns out that adding a netbios name under workgroup in the config file is also essential, as windows doesn't allow ubuntu access to it's shares without one.
For anyone else who is having this same issue, here's  the sections of my config files that I edited;

/etc/samba/smb.conf

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
   netbios name = compist-desktop

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts wins bcast host



/etc/nsswitch.conf

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Hope this helps people!

Compist

---

### Post by jmarks on 2009-12-14
> **jmarks said:**
> Dear dmizer,
 Here is my smb.conf. Thanks so much for your help.
```


[global]
   workgroup = markshome
   netbios name = jmarks-desktop
   server string = anonymous file server
   security = user 
# was security= share
usernamemap = /etc/samba/smbusers  
# this line above added for user-level share
   printing = cups
   printcap name = cups
   load printers = yes

[common_share]
   path = /sharedfiles
   comment = anonymous share for all users
   public = yes
   writeable = yes
   browseable = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

#==================================Share Definitions
==================================================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. this will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes
valid users = %S
writeable = yes
```

I learned about testparm and ran it mutiple times, commenting lines until it ran without errors. Turned out all the sqawking (and my frustration over the last 2 weeks, was the line beginning "=". All I needed to do was comment it out, and it all ran fine.

Thanks to all

---

### Post by Dookert on 2009-12-14
Just wanted to add 2 cents to this. If your using Windows 7 and are trying to access a partition/drive that is NOT in the /users/public folder of windows 7, simply enabling sharing on the partition/drive and checking off every option in the windows sharing center will not allow ubuntu to mount the drive. It will still give an: unable to mount drive error message. You have to do as dmizer said about vista, create a directory within the drive, but then....you have to enable privileges like crazy for that folder via right click->properties, and then enabling full authority for users under both sharing, and security tabs. I got it to work via trial and error. ridiculously difficult to get working for something which should be so simple. If your worried about privacy, dont allow access via the "EVERYONE" object option.

---

### Post by PrimaryMaster on 2009-12-17
When i enter command sudo /etc/init.d/samba restart it says command is not found. Though samba should be installed because when i enter smb://ip address/share I can view the files??

---

### Post by jamesisin on 2009-12-17
PrimaryMaster - Isn't that the command to restart the Samba server and don't you want to restart the Samba client?

---

### Post by dmizer on 2009-12-21
Those of you having problems with Vista or Win7, please see this post [http://ubuntuforums.org/showpost.php?p=8524499&postcount=45](http://ubuntuforums.org/showpost.php?p=8524499&postcount=45)

Let me know if that helps, and I will add it to the howto.

---

### Post by pussfeller on 2009-12-23
Steps 2 and 3 fixed for me the 'unable to mount' error I was getting from Nautilus, much obliged!

---

### Post by cdysthe on 2009-12-24
This thread should be set super-sticky!

---

### Post by maestrobwh1 on 2009-12-27
I more or less have the reverse issue: I am using Ubuntu on a host and ON OCCASION use XP on a laptop or two with my network.  When the laptops are running ubuntu, everything shares fine and all shared host folders are "browse-able" on the ubuntu guests.

However, in Win XP Pro, When I go to use Win Explorer, when I navigate to Workgroup, I only see the laptop machine.  The workgroup assigned is "workgroup" as it is in the Ubuntu host.

If posting my smb.conf would be useful, I can easily do that but that takes up a lot of space on the forum page.  I can also just post a part of it.

What I have been doing is saving my work in XP, then boot into Ubuntu on the client and either transfer or print.  Kind of cumbersome and I know that Samba is supposed to work to let XP (Pro) see the shares/printer.

---

### Post by jamesisin on 2009-12-27
maestrobwh1 - Are you trying to allow for guest access or are you using Windows permissions to access the Ubuntu's Samba share?

Either way you will want to ensure that you are using the correct permissions for the share (and one folder above the share I think).  (Your other Ubu machines might be masking a permissions issue of you are using the same username and password combination between them.)

---

### Post by maestrobwh1 on 2009-12-27
In the host, it is pretty much the default smb.conf.  I use kde (though I could also use nautilus) and use the sharing tab under "properties," which adds the share and share name of my chosen folders to the bottom of smb.conf

On occasion I use the terminal to actually mount a share (if I am using a music app like exaile or amarok for instance) to a location.  In that case, I use a credentials file with my username and password with gid uid, etc.  I DO NOT usually do this though.

In the guest Ubuntu machines, **I either use nautilus or dolphin's built in "network" function to see/use my shares.**  **My host box is called "eee-box" **so I would open the Network on the left pane, then click "Samba Shares" (Windows Network in nautilus) then "Workgroup" and I have several shared folders that DO show up (MUSIC,VIDEO,PUBLIC) so the address would be for example

**smb://eee-box/MUSIC**

I of course have made "bookmarks" for these locations within Dolphin/nautilus to save time.  Mounting or using fstab is faster but I don't generally have shares mounted for a long time, if I suspend and take my machine to work it doesn't wake properly if I forget to unmount the shares, nor does it shut down quickly.  At any rate...

[B]In windows XP Pro, if I browse into Network/Workgroup, the only thing I see on the guest is the guest machine itself (i.e. "thinkpad" and not "eee-box").
[/B]
**Am I making in incorrect assumption that I should also alt least see "eee-box" there?  **Oddly, on the host Ubuntu machine I do see "thinkpad" but not the shared guest XP machine folder "My Documents" when I "thinkpad" open.

This isn't a huge deal. It is indeed a rare occasion that I use XP.  It takes longer to boot with all the security crap that needs to load to protect that OS.  I am thinking it is an easy fix though within smb.conf for someone that knows what they are doing.

---

### Post by dmizer on 2009-12-27
> **maestrobwh1 said:**
> I more or less have the reverse issue: I am using Ubuntu on a host and ON OCCASION use XP on a laptop or two with my network.  When the laptops are running ubuntu, everything shares fine and all shared host folders are "browse-able" on the ubuntu guests.

However, in Win XP Pro, When I go to use Win Explorer, when I navigate to Workgroup, I only see the laptop machine.  The workgroup assigned is "workgroup" as it is in the Ubuntu host.

If posting my smb.conf would be useful, I can easily do that but that takes up a lot of space on the forum page.  I can also just post a part of it.

What I have been doing is saving my work in XP, then boot into Ubuntu on the client and either transfer or print.  Kind of cumbersome and I know that Samba is supposed to work to let XP (Pro) see the shares/printer.

It seems that you have a server issue, which this thread really doesn't answer to. You should still follow the steps on the first page, because they can help servers as well, but if you still have problems you should post a new thread.

When you do post a new thread, you'll need to include your entire /etc/samba/smb.conf file. You can keep the post from getting too large by using the ```
 tag like so:
[noparse][code]
/etc/samba/smb.conf
output
here

```[/noparse]

---

### Post by jamesisin on 2009-12-28
maestrobwh1 - I don't want to derail dmizer's thread.  Post a link to your new thread here and I'll follow you there.

---

### Post by crx686 on 2009-12-29
All those settings I've done, except for the installing wins for that. I have pfsense which has a DNS server on it that i am running. Also Was that suppose to fixs my secound problem run my music off the server? Thanks for your help

---

### Post by dmizer on 2009-12-29
For music, just run gnump3d: [http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html](http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html) it will work cross platform on any system that's attached to your network.

---

### Post by doas777 on 2009-12-29
> **crx686 said:**
> All those settings I've done, except for the installing wins for that. I have pfsense which has a DNS server on it that i am running. Also Was that suppose to fixs my secound problem run my music off the server? Thanks for your help

for my network music lib, i installed mt-daap (a Firefly/DAAP server) that I can connect to via rythmbox. works like a charm.

---

### Post by derekmbarnes on 2009-12-29
> **PrimaryMaster said:**
> When i enter command sudo /etc/init.d/samba restart it says command is not found. Though samba should be installed because when i enter smb://ip address/share I can view the files??

I'm having the same problem. I typed the line into Terminal as written on page 1 of the thread (and I'm positive I typed it correctly), and got back

```
sudo: /etc/init.d/samba: command not found
```I checked the init.d folder in my GUI, and there was no "samba" file, nor anything that appeared Samba-related. But the Samba directory and "smb.conf" file are right where they're supposed to be. I just installed 9.10 Karmic via download; did something go wrong, or do I need to do something differently?

Assuming the above doesn't get me anywhere: will changing my Windows computer's workgroup from "MSHOME" to "WORKGROUP" negatively affect the Windows system in any way? My parents use this computer and I don't want to screw it up.

---

### Post by gordintoronto on 2009-12-29
> **derekmbarnes said:**
> ```
sudo: /etc/init.d/samba: command not found
```I checked the init.d folder in my GUI, and there was no "samba" file, nor anything that appeared Samba-related. But the Samba directory and "smb.conf" file are right where they're supposed to be. I just installed 9.10 Karmic via download; did something go wrong, or do I need to do something differently?

Assuming the above doesn't get me anywhere: will changing my Windows computer's workgroup from "MSHOME" to "WORKGROUP" negatively affect the Windows system in any way? My parents use this computer and I don't want to screw it up.

If there are no other Windows computers, you can change the workgroup name with no negative effects.  However, I suggest using an unique name such as dereknet, which you will recognize very easily when it appears.  Then you can say, "ah ha, this works!"

I think Samba is not part of a default installation.  I have accessed Windows XP shares without it.

---

### Post by maestrobwh1 on 2009-12-29
> **jamesisin said:**
> maestrobwh1 - I don't want to derail dmizer's thread.  Post a link to your new thread here and I'll follow you there.

I posted it here.  Any help you could offer would be appreciated:-) !!!

[http://ubuntuforums.org/showthread.php?t=1367698](http://ubuntuforums.org/showthread.php?t=1367698)

---

### Post by dmizer on 2009-12-29
> **derekmbarnes said:**
> I'm having the same problem. I typed the line into Terminal as written on page 1 of the thread (and I'm positive I typed it correctly), and got back

```
sudo: /etc/init.d/samba: command not found
```I checked the init.d folder in my GUI, and there was no "samba" file, nor anything that appeared Samba-related. But the Samba directory and "smb.conf" file are right where they're supposed to be. I just installed 9.10 Karmic via download; did something go wrong, or do I need to do something differently?

Assuming the above doesn't get me anywhere: will changing my Windows computer's workgroup from "MSHOME" to "WORKGROUP" negatively affect the Windows system in any way? My parents use this computer and I don't want to screw it up.

Rebooting will accomplish the same thing as /etc/rc.local/samba restart.

Edit:
I've updated the howto to include this information.

---

### Post by rjkothari on 2009-12-31
Hi,

I'm using Ubuntu 9.10 Desktop 32 bit; and Samba share is created on a Nitix (Lotus Foundations) Server - a proprietary Linux - which has licensed SLES 10 kernel.

Without following any of the steps mentioned by you, I was able to access the Samba shares created on Nitix using Connect to Server under Places. But, I noticed that this shares were not 'persistent' in nature i.e., it would not re-connect when PC was booted. I had to manually do Places->Bookmark->click on each share bookmark to reconnect. But, in trying to solve this auto-reconnect I came across your article.

And, I decided to follow your steps to make it perfect - if it was not. But, in the process, I enabled ufw (which was 'off' earlier). But moment I turned it 'on' - whether I use the 4 rules given by you or not - it is not allowing me to see the Samba shares. I tried even giving the rules other way but still same problem. So, clearly there is something else that needs to be done in ufw setting to make it see the Windows shares on Nitix server.

In the mean time, I am disabling the ufw. Given a choice, I would love to enable ufw.

Can some one revert please?

---

### Post by ChaoticXSinZ on 2009-12-31
A note on the ordering in nsswitch.conf.

By using the one specified in the first post I was able to connect to work group computers by using their netbios name instead of an IP address and regular DNS also worked. But I experienced a delay whenever my system tried to resolve domain names such as google.ca. So I changed my setup to:

```
hosts:          files dns wins mdns4
```

Putting wins after dns since I only used WINS resloution for my printer shared through SAMBA. This removed the delay I experienced earlier.

Later on I realized that it was because of the part "[NOTFOUND=return]" which made wins not work when I placed it after dns. So theoretically this should also work:

```
hosts:          files mdns4_minimal dns wins mdns4
```

Also one more note: Placing wins after dns won't work if you use a DNS server which redirects you to an error/search page when it can't resolve (i.e. OpenDNS)

---

### Post by dmizer on 2009-12-31
> **ChaoticXSinZ said:**
> 
Later on I realized that it was because of the part "[NOTFOUND=return]" which made wins not work when I placed it after dns. So theoretically this should also work:

```
hosts:          files mdns4_minimal dns wins mdns4
```
Netbios name resolution almost never works when wins is placed after dns. It has nothing to do with "[NOTFOUND=return]". You may experience delays in DNS if you put wins before [NOTFOUND=return] however. Otherwise, local name resolution most likely won't work.

If you are getting delays when browsing the web, this means that you have another problem on your network ... usually firewall related.

If you do not have a DHCP network (or if you have a DHCP network with permanent leases based on MAC address), you can remove the winbind daemon, remove wins from /etc/nsswitch.conf and add your printer's name to /etc/hosts like so:
```
$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	tsubame.japan.dmizer.dnsdojo.net
192.168.1.100   samba-server.name

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Alternatively, you could add a local DNS server, and that should solve your problem as well.

> **ChaoticXSinZ said:**
> Also one more note: Placing wins after dns won't work if you use a DNS server which redirects you to an error/search page when it can't resolve (i.e. OpenDNS)
The reason for this is linked in the howto just after the directions for the /etc/nsswitch conf edit: [http://ubuntuforums.org/showpost.php?p=7255859&postcount=15](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15)

---

### Post by Silvertones on 2010-01-02
I've made some progress but there may be a bug in the FW. Not sure I'll  describe.

Comp. A = Ubuntu & connects to the internet via dialup
Comp. B = Windows XP no internet needed
A & B are networked via adhoc wirelessly and can see back and forth  perfectly. I can see all shares from either comp.The trouble comes from engaging the GUFW
Engage the FW fron GFUW and I can no longer see shared files back and  forth as expected.

It's been determined that I need ports 135,137,138,139,445 Both TCP  & UDP
My workgroup in Windows is called BOBO.
If I make simple rules in GFUW allowing the above ports the results are:

I can go from comp.B ( windows) to computer A (Ubuntu) perfectly.I can access the shared folder on the Ubuntu comp.
On comp. A ( Ubuntu) If I click network I see "windows network" click on  that I see " BOBO" my work group  and "Workgroup" the Ubuntu group.Click on "BOBO" and the screen changes but  is blank and says 0 items. I should see Comp. B listed but don't.
So it's getting to a point the FW is not stopping me from seeing the "BOBO" group but won't let me see the Comp. in that group.

---

### Post by dmizer on 2010-01-02
> **Silvertones said:**
> The trouble comes from engaging the GUFW
Engage the FW fron GFUW and I can no longer see shared files back and  forth as expected.
If you are on a LAN with a firewalled gateway, there's really no reason for you to be using a software firewall locally unless you're on a huge LAN with hundreds of machines.

The only reason I can see you needing a local software firewall is if the laptop is going to be regularly used on unsecured networks or have unfettered access to the WAN as with a Mobile broadband or dial up internet connection. Then, in those cases, you shouldn't have holes poked in your firewall for SAMBA access.

My recomendation is to simply disable the GUFW unless you have a valid reason for using it. If you have a valid reason for using it, then you probably shouldn't be trying to share files over SAMBA.

Edit:
Updated the howto to reflect this.

---

### Post by Silvertones on 2010-01-02
Yes I am on dial up and I do use ensecured wifi spots for large file downloads so I need the firewall. I've put in the rules that you mention of course substituting my IPs for yours. I'm secure with this. 
BUT
I can go from comp.B ( windows) to computer A (Ubuntu) perfectly.I can  access the shared folder on the Ubuntu comp.
On comp. A ( Ubuntu) If I click network I see "windows network" click on   that I see " BOBO" my work group  and "Workgroup" the Ubuntu  group.Click on "BOBO" and the screen changes but  is blank and says 0  items. I should see Comp. B listed but don't.
So it's getting to a point the FW is not stopping me from seeing the  "BOBO" group but won't let me see the Comp. in that group.

---

### Post by jamesisin on 2010-01-02
> **Silvertones said:**
> Yes I am on dial up and I do use ensecured wifi spots for large file downloads so I need the firewall. I've put in the rules that you mention of course substituting my IPs for yours. I'm secure with this. 
BUT
I can go from comp.B ( windows) to computer A (Ubuntu) perfectly.I can  access the shared folder on the Ubuntu comp.
On comp. A ( Ubuntu) If I click network I see "windows network" click on   that I see " BOBO" my work group  and "Workgroup" the Ubuntu  group.Click on "BOBO" and the screen changes but  is blank and says 0  items. I should see Comp. B listed but don't.
So it's getting to a point the FW is not stopping me from seeing the  "BOBO" group but won't let me see the Comp. in that group.

I would seek out a method of turning your firewall off when on your network and on when not.  (Perhaps someone can point you toward a method for auto-detecting your network to (dis)engage your firewall.)

Your firewall will be greatly weakened by leaving all these ports open and permissions granted.  You will be much better off using your firewall, when off-network, to protect these permitted areas.

Which version of Windows is computer B running?  Also, does computer B appear with the firewall disabled?

---

### Post by Silvertones on 2010-01-03
Thanks Jamesisn,
With the FW disengaged everything is PERFECT in both directions.
Yours is the most practical solution. I can adjust my work habits to only access the LAN when not on line.

---

### Post by dmizer on 2010-01-03
> **Silvertones said:**
> Thanks Jamesisn,
With the FW disengaged everything is PERFECT in both directions.
Yours is the most practical solution. I can adjust my work habits to only access the LAN when not on line.

You could set UFW to allow anything from a particular IP address, namely your Comp. B IP address.

Something like this may do it:
```
sudo ufw allow from comp.b.ip.address
```

Try it and see if it works.

---

### Post by Silvertones on 2010-01-03
That's what I'm trying to explain. That's the first thing I did per you instructions on page 1. Like this of course substituting my own IP address range:

sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24
Now when I press NETWORK instead of seeing nothing I get to the point were I can see the two group folders but no further.
1. BOBO
2. Workgroup

The code above that you mention in the last post is not clear to me. Lets say that comp B name is norton and the IP is 182.168.1.6 would I enter:

sudo ufw allow from comp.norton.ip.182.168.1.6

---

### Post by Silvertones on 2010-01-03
OK so now I'm embarrassed. I was making things too complicated in my rules.
KISS KISS KISS KISS
What I did to fix:

1. Open the GUFW
2. set allow both udp & tcp
3. In the from I put in the IP address of comp.B
Repeated this for comp. A 

ALL IS WELL The FW will block everything except from these two IPs and there IPs assigned for LAN only and also have subset maskes.

THANKS ALL.

---

### Post by dmizer on 2010-01-03
> **Silvertones said:**
> OK so now I'm embarrassed. I was making things too complicated in my rules.
KISS KISS KISS KISS
What I did to fix:

1. Open the GUFW
2. set allow both udp & tcp
3. In the from I put in the IP address of comp.B
Repeated this for comp. A 

ALL IS WELL The FW will block everything except from these two IPs and there IPs assigned for LAN only and also have subset maskes.

THANKS ALL.

That is fantastic! I'm glad you got it all worked out.

---

### Post by Silvertones on 2010-01-03
DMIZER,
Thanks. It was your last post that was the clue.

---

### Post by pearldrums on 2010-01-03
dmizer, can I ask you to take a look at my smb.conf and nsswich.conf files? I've been searching the forums and it seems that whenever someone has a file sharing problem you ask for the files and help them trouble shoot. I feel bad asking you as it seems you're single handedly being the tech support for all of ubuntu's samba problems, but I haven't been able to make anything work.

I just did a fresh install of Karmic (this is starting to get really easy). I right-clicked on a file and tried to create a share. It prompted me to install some file sharing software that included some samba looking stuff. I clicked yes. Then when I go to create a share it says "failed to execute child process 'testparm' (no such file or directory)"

I have done steps 2 and 3 of your main post.

smb.conf:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios = levi-HQ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```nsswitch.conf :

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by pendulous on 2010-01-06
Great guide. Worked thus far getting me to the Password required for [COLOR=Red]**workstation**[/COLOR]. 

However, I'm unable to access the shares after entering my credentials. I'm running Jaunty 9.04 as a VMWare Guest on a Windows 7 Host. I enter the username: <user> , domain: <workgroup> , password: <password> ; the dialog continues to display after selecting "connect" ... any suggestions?

---

### Post by swells on 2010-01-07
Howdy,
      First, thanks for the work you do on this thread.  I've learned a lot (although, since I'm psoting, not quite enough....)

      My question is: "What changed between 9.04 (Jaunty) & 9.10 (Karmic)?"

      On an Ubuntu 9.04 machine, I activated file sharing on a coupla folders.  Other Ubuntu, Win98SE, Win2K & XP machines saw them correctly.
      That 9.04 machine was upgraded to 9.10 and only the other Ubuntu, Win2K & XP machines can see it.
      The Win98SE machines all give the response: "[servername] is not accessible
The local device type and the network resource type are not the same."

      I suspect that if I can find what triggered the change I might be able to find a way to fix or work around it.  Any insights or ideas would be greatly appreciated.

(I've read all 30+ pages here and searched/read for the last month or so elsewhere using the error message above to try & figure it out...)

Thanks.

---

### Post by AlexeylForpostl on 2010-01-09
Thanks for the guide.
It's really excellent.
But I have some problems with samba.
I've connected Network Driver in WinXP SP2.
But after restarting the driver is unconnected (I checked "Reconnect at relogon").
But thereis another server with samba, but it's on FreeBSD.
Another man configured it.
And we connected the 2nd network driver to his server on FreeBSD and it works excellent.
After every rebooting of workstation Network driver to FreeBSD works.
But to make my driver work we must start Total Commander and click on this driver and then we can work with it.
Please help me.
Thanks a lot.

---

### Post by bkaplan on 2010-01-10
dmizer:

Thanks for this Howto.  It solved problems I've been experiencing for a long time now...

My question is very different from those posted above and is likely related to Samba's handling of permissions.  I'm running an Ubuntu 9.10 server-edition fileserver running Samba (not Samba 4) on a small workgroup having an Ubuntu 8.10 desktop, an Ubuntu 9.04 desktop, a couple of 9.10 desktops, and several XP Pro machines.  I've followed this Howto and (finally!!) have all machines and user accounts talking to the fileserver with no problems.  Performance is excellent across the network to the fileserver shares.

Permissions on the shared directory are set for all users to create and delete files, and to read, write, and execute them.  It is my intent that the share allow all users access to any files within the shared folder for creating, revising, and collaborating.

Here's an example of the problem/issue: User A saves a Word document to the fileserver share.  Seemingly, the 9.10 and XP desktops can open, edit and save the document fine (using Word or OpenOffice).  Other 9.10 and XP desktops can subsequently open, edit, and save the document.  This is the intended result.

However, once a user on the 8.10 or 9.04 desktop opens, edits, and saves the document within the share, the document is thereafter locked for editing to all others.  The only way to fix this is to chmod the locked file.  Thus, so long as only 9.10 and XP users touch the file, no issues... when an earlier Ubuntu is used, the file is locked.  (Other users can still see and open the file, it is just Read-Only.)

As an aside, the same issue seemingly arises with pure text files edited with gedit (to wit, the problem doesn't seem to be necessarily related to OpenOffice.)

Query: Ever heard of this behavior?  Can someone point me to an answer?  Is there a way to reset the permissions each time the file is "checked-in"?

TIA for any help!

Regards,
Barry

Edit: Withdrawn - sorry for any bother.  I found the answer in the following thread, in case anyone else has a similar question:

[http://ubuntuforums.org/showthread.php?t=1375183](http://ubuntuforums.org/showthread.php?t=1375183)

---

### Post by bgreenaway on 2010-01-13
Running 9.04 on a workstation in my Active Direcory domain. When opening Windows Network bookmark, my domain just 'disappears'. I have applied the 1-3 steps and they seemed to be working. I open Windows Network bookmark and my domain appears and then all of my domain workstations and servers, but then samba seems to die after a while and cannot see anything. Only way I can get it working (temporarily) again is by /etc/init.d/samba restart.

Any ideas as to why this is happening?

---

### Post by dmizer on 2010-01-13
> **bgreenaway said:**
> Running 9.04 on a workstation in my Active Direcory domain. When opening Windows Network bookmark, my domain just 'disappears'. I have applied the 1-3 steps and they seemed to be working. I open Windows Network bookmark and my domain appears and then all of my domain workstations and servers, but then samba seems to die after a while and cannot see anything. Only way I can get it working (temporarily) again is by /etc/init.d/samba restart.

Any ideas as to why this is happening?

Unfortunately, this howto only really works for simple file sharing and not for AD. I don't really know much at all about AD, so I suggest starting here: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto#Troubleshooting](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto#Troubleshooting)

Also, you might be successful by searching bug reports in launchpad.

---

### Post by BenJenkin on 2010-01-18
I have 2 xp machines and 1 Ubuntu machine. The XP machines cannot see Ubuntu and I cant see xp machines using nautilus network. When I click "Windows Network"I get the error "Unable to mount location. Failed to retrieve share list from server".
I can connect if I put smb://192.168.1.100/ into nautilus

smbtree produces no result at all

Changes made

**1)installed Windbind**
sudo apt-get install winbind

**2) Checked no firewall**

```

sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```**3)Ensured all firewalls are turned off on both XP machinese**

**4)Changed Smb.conf**
"name resolve order = lmhosts wins bcast host"
"dns proxy = no"** ->** ";dns proxy = no"
"wins proxy = no" **->** ";wins proxy = no"
"workgroup = WorkGroup" **->** "workgroup = Benglish"
Added "netbios name = Samba24"

**5)Changed /etc/nsswitch.conf **
"hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4"

**6)Checked RestrictAnonymous is set to 0 in XP**
[http://support.microsoft.com/kb/913628](http://support.microsoft.com/kb/913628)

**7)Checked smbfs is installed**
sudo aptitude install samba smbfs

**8)Reinstalled Samba multiple times**

**9)Tried using Dolphin briefly instead of nautilus but to no avail**

Key files
var/log/log.winbindd
etc/nsswitch.conf
etc/samba/smb.conf

NOTE:
if you try to browse to a share when running nautilus as root it will cause this error message like this

```

Could not find "/home/[username]/smb:/192.168.1.100"

please check the spelling and try again

```

---

### Post by BenJenkin on 2010-01-18
I found Gamba-Samba renames the smb.conf and replaces it with its own. I deleted the new one and went back to the original and started again. Now the XP computers can see the Ubuntu machine but the Ubuntu machine cant see the XP machines

---

### Post by BenJenkin on 2010-01-18
Ok now everythings fixed.

Don't install Gadmin Samba as it screws up smb.Conf

---

### Post by kbreborn on 2010-01-26
Cool, I can access shared files on Win XP after following guide from dmizer!
thanks for collecting the information and all the patience!

---

### Post by Merlinson on 2010-02-01
Another thank you from me!  Following your guide completely fixed it.

---

### Post by takayuki on 2010-02-01
And yet another thanks!  Dmizer's info got my ubuntu and xp boxes sharing for the first time ever.  Thanks!

---

### Post by AmrH on 2010-02-02
The following line is causing me problems on my Ubuntu Karmic box

 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4
after changing it to that, firefox takes too much time looking up hostnames. I've even tried to shorten the time by omitting the "mdns4_minimal" and "[NOTFOUND=return]" options; however, the lookup time is still high. Is there anyway to solve it? When I leave it to stock, I can't browse my Windows 7 shares.

---

### Post by dmizer on 2010-02-02
> **AmrH said:**
> The following line is causing me problems on my Ubuntu Karmic box

 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4
after changing it to that, firefox takes too much time looking up hostnames. I've even tried to shorten the time by omitting the "mdns4_minimal" and "[NOTFOUND=return]" options; however, the lookup time is still high. Is there anyway to solve it? When I leave it to stock, I can't browse my Windows 7 shares.

What is the brand and model of your router?

---

### Post by AmrH on 2010-02-02
> **dmizer said:**
> What is the brand and model of your router?
Quicktel with Wireless Access. Actually it was rebranded and sold by the ISP, so there's no way to know it's original model.

---

### Post by dmizer on 2010-02-03
> **AmrH said:**
> Quicktel with Wireless Access. Actually it was rebranded and sold by the ISP, so there's no way to know it's original model.

Well, look in the settings of the router to see if you can set permanent DHCP leases by MAC address. If you can, then do so for all your machines in the network.

Then, remove the winbind stuff (including the nsswitch.conf edit) and configure your host names in the /etc/hosts file as described here: [http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601)

---

### Post by AmrH on 2010-02-03
> **dmizer said:**
> Well, look in the settings of the router to see if you can set permanent DHCP leases by MAC address. If you can, then do so for all your machines in the network.

Then, remove the winbind stuff (including the nsswitch.conf edit) and configure your host names in the /etc/hosts file as described here: [http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601)
Actually here's the part in the settings that has to do with DHCP. Is it setup correctly?

[[IMG]http://img213.imageshack.us/img213/3536/hi2hiobvaiomweo.png[/IMG]](http://img213.imageshack.us/i/hi2hiobvaiomweo.png/)

---

### Post by AmrH on 2010-02-03
So you suggest assign static IPs to all the computers in the network, edit the hosts file, and remove Windbind?

---

### Post by AmrH on 2010-02-03
> **AmrH said:**
> So you suggest assign static IPs to all the computers in the network, edit the hosts file, and remove Windbind?
??

---

### Post by dmizer on 2010-02-03
Sorry, I've been trying to find an alternative solution for you. I have not been very successful.

Have you tried manually assigning DNS servers like opendns: [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

If that doesn't work, then yes, my best suggestion for you is to use static IP addresses, configure /etc/hosts, and remove winbind.

---

### Post by AmrH on 2010-02-04
I tried OpenDNS and the problem persisted, so I set up static IPs and removed Winbind. Worked like a charm, thank you for your help! 

I think it would be great if there's a way to eliminate the slow domain name resolution and at the same time give the ability to browse win shares!

---

### Post by nylle on 2010-02-06
> **pendulous said:**
> Great guide. Worked thus far getting me to the Password required for [COLOR=Red]**workstation**[/COLOR]. 

However, I'm unable to access the shares after entering my credentials. I'm running Jaunty 9.04 as a VMWare Guest on a Windows 7 Host. I enter the username: <user> , domain: <workgroup> , password: <password> ; the dialog continues to display after selecting "connect" ... any suggestions?

Hi, this is exactly the same problem I have, although I'm trying to connect to a Windows XP machine from ubuntu 9.10. It worked flawlessly from my old debian machine to the same Windowsmachine, so the problem lies somewhere in ubuntu.

Did you ever get this resolved?

//Andreas

---

### Post by killiekosmos on 2010-02-08
Dmizer, I need your help please.  On my home network I've gor 4 pcs:

PC A   is a Vista laptop

PC B  is an XP laptop

PC C  is a Win7 PC with a shared printer

PC  D is dual boot XP and Ubuntu 9.10 PC

If I boot D in XP then all 4 PCs can see and access one another and the printer.  If I boot D in ubuntu then A, B and C can access the shares on Ubuntu D and Ubuntu D can access shared folders on A and B.  However if I try to access C (Win 7) I keep getting a log in dialogue but it won't accept the password.  Same if I try to access the printer from Ubuntu D

I've worked my way through your suggestions under your sig, changing WORKGROUP name etc, but no change.

Have you any other suggestions?  (I'm new to ubuntu so easy suggestions best!)

Thanks

---

### Post by killiekosmos on 2010-02-08
FIXED

Found another link - removed Windows live ID assistant from Win 7 and now Ubuntu sees the shares!!!

---

### Post by tamanaco on 2010-02-09
Finally... just came around to check if there was a solution and Bingo!... Removing the Windows Live ID Sign-in assistant solved my problem. 

Thanks for the pointer dmizer

I did not look at the details of the bug. Is this bug something that will "eventually" be fixed by Samba developers or is this an issue on the Windows 7 side?

---

### Post by dmizer on 2010-02-09
> **tamanaco said:**
> Finally... just came around to check if there was a solution and Bingo!... Removing the Windows Live ID Sign-in assistant solved my problem. 

Thanks for the pointer dmizer

I did not look at the details of the bug. Is this bug something that will "eventually" be fixed by Samba developers or is this an issue on the Windows 7 side?

This seems to be something related to Windows Live ID Sign-in assistant, as it is apparently causing problems with file sharing between Win7 computers as well.

---

### Post by minideezel on 2010-02-13
I am also having a issue with 9.10 connecting to a windows 7 share, i have tried all of the items in the original post, i don't have a firewall running on the ubuntu machine, my win 7 network is set with homegroup off, password protected sharing off.

When i try to connect it just asks for user and pass, if i put in the comps valid user and pass it just asks for it again.

I don't have the windows sign-in assistant on my win comp.

I would appreciate any help.

Thanks

---

### Post by dmizer on 2010-02-14
> **minideezel said:**
> I am also having a issue with 9.10 connecting to a windows 7 share, i have tried all of the items in the original post, i don't have a firewall running on the ubuntu machine, my win 7 network is set with homegroup off, password protected sharing off.

When i try to connect it just asks for user and pass, if i put in the comps valid user and pass it just asks for it again.

I don't have the windows sign-in assistant on my win comp.

I would appreciate any help.

Thanks
Try logging in with the username "guest" and no password.

---

### Post by RickardL on 2010-02-18
I'm out of luck.
Trying to reach a windows 7 box from my ubuntu 9.10


I did manage to go to
Places > Connect to server > Windows share then enter all information including an admin user on my windows 7 machine

However now I cant replicate after rebooting both machines, now it refuses this too

What I want is to simply access two shares on my Windows 7 machine from my ubuntu without having to enter any passwords.

Bot h linux and windows are called WORKGROUP as far as I can see (i am not on a domain btw)
I did add the netbios name in smb.conf however I cannot ping it from my win7
From my ubuntu I can ping my win7 fine.

I cannot find any live id thing, I dont run messenger or similar so shouldnt have it.

i changed the nsswitch and installed winbind

I put wins first in the list of name resolve order

I installed gufw and clicked allow all as default and no exceptions (for testing)

On my windows 7 it now says "Ready to create" on homegroup, I take it that it's disabled.

under advanced sharing i now have these values

network discovery: on
file and printer sharin: on
public folder sharing : on
Media streaming: off
enable for 40-56 encryption: on (during testing)
password protected sharing: off (during testing)
homegroup connections: use user accounts

and I have made sure to share the folders altho only with "everyone" to read nothing else.

I have disabled firewall in windows 7

I did manage to connect straight to a share as described in the begining (altho now i cant).
Wihle that was working I tried to connect to just my win7 machine (with same win admin account) without asking it to step in to a folder/share... it refused (this was when it was working to connect straight to a share with admin account)

The error message i get when trying to connect to my win7 (i see it just fine under network btw) is:
Unable to mount location
Failed to retrieve share list from server


any help is greatly appreciated!

---

### Post by dmizer on 2010-02-18
@RickardL,

What version of Win7 are you using?

Edit:
Try this ... Open regedit in Win7, and change this key to: No
```
\HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Browser\Parameters\MaintainServerList
```

Reboot Ubuntu and see if that fixes things.

---

### Post by pranaynewton on 2010-02-20
Hi Dmizer,

I am currently running jaunty on my system, my computer is on a college lan network, i am able to browse some windows computers when i manually type in their host names or ip addresses but not able to browse other windows computers which i was able to open from windows, even using ip addresses. All these computers are on workgroup "WORKGROUP".

I have ufw disabled, findsmb lists some of the computers but doesnt list the PCs which i can browse using hostnames. I checked ipv4 on the windows computers which i haven't been able to browse, wins server has the default option enabled and the lmhosts is also being used. 

I have followed the configuration you have mentioned in your posts, but they dont seem to be working. I was wondering if a college lan network has a different samba server configuration.

Thanks in advance

---

### Post by RickardL on 2010-02-20
Thank you for the reply!

in the end I managed to solve it by creating a user for ubuntu on my win7 machine and I got it to work that way

---

### Post by fallenashes on 2010-02-22
I am sorry for being such a newbie and having almost no clue what I am doing, but I have a couple of questions as to why I can't access my windows files on Ubuntu.
**I am dual boot running windows 7 home premium 64-bit and Ubuntu 9.10**

1.  What exactly does Samba do?  Is it a stand alone program that you install and open to access your windows files, or just does its thing in the background?

2.  What does the Windows 7 configuration in the tutorial accomplish?  (I have done this, but not really knowing why)

3.  How do you run commands?  Do you run them in windows or in Ubuntu, and if it is Ubuntu, is the the terminal program?

thanks to the Ubuntgurus (:D)

---

### Post by dmizer on 2010-02-22
> **fallenashes said:**
> I am sorry for being such a newbie and having almost no clue what I am doing, but I have a couple of questions as to why I can't access my windows files on Ubuntu.
**I am dual boot running windows 7 home premium 64-bit and Ubuntu 9.10**

1.  What exactly does Samba do?  Is it a stand alone program that you install and open to access your windows files, or just does its thing in the background?

2.  What does the Windows 7 configuration in the tutorial accomplish?  (I have done this, but not really knowing why)

3.  How do you run commands?  Do you run them in windows or in Ubuntu, and if it is Ubuntu, is the the terminal program?

thanks to the Ubuntgurus (:D)

Samba is needed when there are multiple computers running at the same time on a network. Some of the computers are Windows, and some of the computers are Ubuntu.

If you just want to access files between Windows and Ubuntu where both systems are located on the same computer, then you don't need this howto, you need this howto: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by fallenashes on 2010-02-22
Well, I'm getting closer, but the darn thing still won't work.
Thanks for your help though

---

### Post by AmrH on 2010-02-23
> **AmrH said:**
> I tried OpenDNS and the problem persisted, so I set up static IPs and removed Winbind. Worked like a charm, thank you for your help! 

I think it would be great if there's a way to eliminate the slow domain name resolution and at the same time give the ability to browse win shares!
I've managed to solve the whole problem without assigning static IP addresses through following the whole procedure, but changing
 
"hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4"

to 

 "hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]dns [COLOR=black]wins[/COLOR][/COLOR] mdns4"

---

### Post by dmizer on 2010-02-23
> **AmrH said:**
> I've managed to solve the whole problem without assigning static IP addresses through following the whole procedure, but changing
 
"hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4"

to 

 "hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]dns [COLOR=black]wins[/COLOR][/COLOR] mdns4"

I'm glad you were able to solve it this way, but I am unsure why that seems to work for some people and not for others. I wish I knew so I could post a method for determining which order to use.

Thanks for the update, and I'm glad you have it working well now!

---

### Post by gordintoronto on 2010-02-23
> **fallenashes said:**
> I am sorry for being such a newbie and having almost no clue what I am doing, but I have a couple of questions as to why I can't access my windows files on Ubuntu.
**I am dual boot running windows 7 home premium 64-bit and Ubuntu 9.10**


You were sent to something much too complicated.  I dual boot Windows 7 and Ubuntu.  I start Nautilus, the file browser, pointing at "computer". (Image attached)  One of the items which appears is "62.8 Media."  That's my Windows partition.  I double-click on it, and I'm looking at my Windows C: drive.  I have full authority to read, write, delete, rename, execute, etc.  I use the same userid and password on both systems, which might be why it is so easy.

---

### Post by Sin@Sin-Sacrifice on 2010-03-01
Anyone by chance able to fix a timeout issue when browsing? I can look through the files but as soon as I start to touch them wifi cuts off and I have to restart ndiswrapper. Any help would be much appreciated. I've started a few threads on this with no response.

---

### Post by dmizer on 2010-03-02
> **Sin@Sin-Sacrifice said:**
> Anyone by chance able to fix a timeout issue when browsing? I can look through the files but as soon as I start to touch them wifi cuts off and I have to restart ndiswrapper. Any help would be much appreciated. I've started a few threads on this with no response.
Humm ... I've not seen this before.

Do you experience the same problem when wired? Do you experience the same problem with other wireless computers? Are you experiencing any other difficulties with your wireless? What wireless adapter are you using.

---

### Post by RealG187 on 2010-03-02
Please help:
[http://ubuntuforums.org/showthread.php?t=1420013](http://ubuntuforums.org/showthread.php?t=1420013)

---

### Post by Sin@Sin-Sacrifice on 2010-03-03
The other computers on the network are just clients... everything is stored on my PC. My mother's work PC and her laptop are the only other 2 other than my G1 and they both can connect to my computer just fine. It's only when I try to transfer or stream something to either of them. The G1 will connect, stream, transfer, or anything I want it to... Android is Linux though. I just found that it also cuts off when using bittorrent but only at high speeds like when downloading ubuntu. If it stays slow it will finish no problem but when I get speeds upwards of 2 MB/s I have to use my ndiswrapper restart script. I can download using other protocols without haste. Like ftp and http. 

Once my mom is done working today I will see if her computers can connect to each other and if they cut off or whatever. Another issue that might be related is that I can't see any of the Windows shares from my PC even though they are set wide open. Considering the settings on XP and 7 I should have full access to her PCs from here. Wierd... Oh and wired isn't an option because she has to have her work PC connected 24/7

I'm using the infamous Linksys wmp300n with ndiswrapper and bcmwl5 x64 windows driver on Karmic X64. It seems only the windows boxes are affected though considering my G1 (Android 1.6 cyanogen 4.2.14.1) does just fine. I streamed "Hitchhiker's Guide To The Galaxy" all the way through on it waiting for updates on the PC. 

I only get to work on this once or twice a week because I don't live here but I have my ssh and ftp servers up and running so that might help. And to combat the problem I set crontab to run my restart script at 58 min past every hour but that sucks when downloading from my PC. G1 only has an 8GB sd card and I have a ton of movies.

Thanks for the help friend.

---

### Post by dmizer on 2010-03-03
@[noparse]Sin@Sin-Sacrifice[/noparse]

On a whim, try rebooting your router and see if things improve. I've had that work more times than I can count. Sometimes router problems do indeed only manifest themselves in one computer.

---

### Post by Sin@Sin-Sacrifice on 2010-03-03
Oh that router gets restarted at least weekly. I know for a fact that the entire network, including the router, got shut down and rebooted yesterday because my mom couldn't connect to her work VPN. I thank you for the reply though. I'm thinking kicking it might help.... save that for last though.

---

### Post by dmizer on 2010-03-03
> **Sin@Sin-Sacrifice said:**
> Oh that router gets restarted at least weekly. I know for a fact that the entire network, including the router, got shut down and rebooted yesterday because my mom couldn't connect to her work VPN. I thank you for the reply though. I'm thinking kicking it might help.... save that for last though.

The only other thing I can think of is that the wireless adapter itself (driver or hardware) is the problem.

---

### Post by Sin@Sin-Sacrifice on 2010-03-04
It all works perfectly in Windows 7 so thankfully that's unlikely. I'm thinking it's ndiswrapper considering it doesn't just happen with samba. Thanks for the help anyway...

---

### Post by dmizer on 2010-03-05
> **Sin@Sin-Sacrifice said:**
> It all works perfectly in Windows 7 so thankfully that's unlikely. I'm thinking it's ndiswrapper considering it doesn't just happen with samba. Thanks for the help anyway...

I suggest opening a thread in the Networking and Wireless section of the forum. Start with the ndiswrapper stickey in that section. Good luck!

---

### Post by guitarplaya85 on 2010-03-06
I figure I'd post here and see if anyone can help.  After buying a new laptop with Windows 7, I am using my desktop, which is running Ubuntu 9.10, as a storage server for my network.  My problem seems to be that I can view my Windows 7 laptop and its shares from the Ubuntu computer, but the Windows 7 laptop cannot see the Ubuntu computer (the same applies when I boot the Ubuntu computer into XP).  My xbox can see both systems.  I tried everything in the guide posted at the beginning of this thread, but to no avail.  I also tried following Microsoft's recommended steps, but they did not work either.  Does anyone know what may be causing this and how it can be remedied?

---

### Post by dmizer on 2010-03-09
> **guitarplaya85 said:**
> I figure I'd post here and see if anyone can help.  After buying a new laptop with Windows 7, I am using my desktop, which is running Ubuntu 9.10, as a storage server for my network.  My problem seems to be that I can view my Windows 7 laptop and its shares from the Ubuntu computer, but the Windows 7 laptop cannot see the Ubuntu computer (the same applies when I boot the Ubuntu computer into XP).  My xbox can see both systems.  I tried everything in the guide posted at the beginning of this thread, but to no avail.  I also tried following Microsoft's recommended steps, but they did not work either.  Does anyone know what may be causing this and how it can be remedied?
Hello,

This thread only deals with viewing files shared from Windows computers. If you are having trouble with Windows being able to view files shared from Ubuntu, you should start a new thread.

When you do start your new thread, be sure to post your /etc/samba/smb.conf file.

---

### Post by sojakob on 2010-03-09
Hey,

I just thought i should thank you for making this Howto.
My Ubuntu experience reaches a couple of moths back, and i've often been bothered by not beeing able to run SAMBA properly and access the windows shares on my LAN. 
Turns out it was a simple firewall problem... So simple and yet i had to have you to guide me. Anyway, problem solved. Thanks!

---

### Post by marcx77 on 2010-03-12
<edit>

Realized that my problem shouldn't be in this thread. Also fixed said problem along the way :D

</edit>

---

### Post by wiz_master49 on 2010-03-12
How would I go about sharing a whole drive? I have Windows 7 acting as the server and am using Ubuntu on this laptop. The drive I am wanting to share has nothing but documents like music, videos, etc on it so it isn't a big deal about permissions and stuff. I have some folders on the drive that I am able to successfully mount on Ubuntu but I was unsuccessful doing the same with the drive. When I try to access it I get [http://i44.tinypic.com/oum9fm.jpg](http://i44.tinypic.com/oum9fm.jpg)

Any ideas?

---

### Post by RealG187 on 2010-03-24
When I connect I get "mount error(112): Host is down" and "connection reset by peer" (It shows one or the other)

[http://lists.samba.org/archive/linux-cifs-client/2005-April/000792.html](http://lists.samba.org/archive/linux-cifs-client/2005-April/000792.html)
I am using IP Addresses and am still getting this error

---

### Post by dmizer on 2010-03-24
> **RealG187 said:**
> When I connect I get "mount error(112): Host is down" and "connection reset by peer" (It shows one or the other)

[http://lists.samba.org/archive/linux-cifs-client/2005-April/000792.html](http://lists.samba.org/archive/linux-cifs-client/2005-April/000792.html)
I am using IP Addresses and am still getting this error

Have you followed all the directions in the first post? This howto is not about mounting with CIFS. It's about browsing shares with Nautilus. If you want to mount a share with CIFS, please see the 2nd link in my sig and follow the directions there.

It sounds like you have a firewall in the way.

---

### Post by dmizer on 2010-03-24
> **wiz_master49 said:**
> How would I go about sharing a whole drive? I have Windows 7 acting as the server and am using Ubuntu on this laptop. The drive I am wanting to share has nothing but documents like music, videos, etc on it so it isn't a big deal about permissions and stuff. I have some folders on the drive that I am able to successfully mount on Ubuntu but I was unsuccessful doing the same with the drive. When I try to access it I get [http://i44.tinypic.com/oum9fm.jpg](http://i44.tinypic.com/oum9fm.jpg)

Any ideas?

Sorry for the late reply.

As I suggest in the first post of this thread, you should put everything you want to share in one folder on the drive. Then share that folder.

---

### Post by Flos Headford on 2010-04-04
Thank you so much, dmizer!
I have methodically worked through this whole thread from the top, and have a much better understanding of what I need to do.
It's still not working, but I'm now confident I'm doing the right things.
Regards,
Phil

---

### Post by dmizer on 2010-04-04
> **Flos Headford said:**
> Thank you so much, dmizer!
I have methodically worked through this whole thread from the top, and have a much better understanding of what I need to do.
It's still not working, but I'm now confident I'm doing the right things.
Regards,
Phil

Are you getting any errors?

---

### Post by Rocket J Squirrel on 2010-04-12
I just want to add that I posted a question about a similar Windows share issue (see [http://ubuntuforums.org/showthread.php?t=1451837](http://ubuntuforums.org/showthread.php?t=1451837)) and was referred to this thread. I applied the fixes shown on the first page of this thread, rebooted Ubuntu, and it works. 

I'm wondering if these fixes will get overwritten if I upgrade to the next level of ubuntu, like Lucid Whatsit.

---

### Post by dmizer on 2010-04-12
> **Rocket J Squirrel said:**
> I just want to add that I posted a question about a similar Windows share issue (see [http://ubuntuforums.org/showthread.php?t=1451837](http://ubuntuforums.org/showthread.php?t=1451837)) and was referred to this thread. I applied the fixes shown on the first page of this thread, rebooted Ubuntu, and it works. 
Fantastic!

> **Rocket J Squirrel said:**
> I'm wondering if these fixes will get overwritten if I upgrade to the next level of ubuntu, like Lucid Whatsit.
Yes, they most likely will be overwritten. You will probably have to reapply them after updating to Lucid.

Sorry.

---

### Post by peterv6 on 2010-04-16
First off, I want to say ***_THANK YOU!_*** to DMIZER for this thread.  I've been working on this for days with no luck until I found the answers here!  Hopefully you can take it one more step for me (please!).

I'm running OS X Snow Leopard 10.6.3 on a MacBook Pro laptop, with Parallels 5.0.  In Parallels I'm running Windows XP Pro SP3 and Ubuntu 9.10.  

I was having problems with NT_CONNECTION_REFUSED errors before I read this thread.  Changes that were suggested resolved all the issues I had, but a new one has surfaced.  

Originally, when I ran smbtree, I could see all the information for MBP17, my OS X system, but the MBP17U (Ubuntu) and SERVER2 (XP) got the connection refused errors.  Now, I can see all the information for the Ubuntu & XP systems, but the OS X system is getting the following error:  

[COLOR="Red"][B]anonymous failed session setup with NT_STATUS_LOGON_FAILURE
[/B][/COLOR]
Can anyone help me out with this one?  I haven't found anything relevant on the web yet.
Thanks,
Peter V.

---

### Post by psymole on 2010-04-18
Hi,

dmizer I've followed all you're instructions (thx by the way) and I've read every post in this threads.
[B]
My problem:[/B] I can view all of my windows xp share and access any folder that is on the c: drive of the Xp machine. But I cant access any folder on the d: drive.

When I click on the shared folders in the d: drive from nautilus I get this error **"You do not have the permissions necessary to view the contents of "Name of the share"."**

my samba config file

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = trujillo1
;	netbios name = HAL9000

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
    name resolve order = lmhosts wins bcast host

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```

I'm using 9.10 and Xp service pack 2

---

### Post by dmizer on 2010-04-18
> **peterv6 said:**
> Now, I can see all the information for the Ubuntu & XP systems, but the OS X system is getting the following error:  

[COLOR="Red"][B]anonymous failed session setup with NT_STATUS_LOGON_FAILURE
[/B][/COLOR]
Unfortunately, I have not had much success in getting OSX to talk to Ubuntu via Samba. That's not to say it's not possible, but I just haven't been successful.

Rather than trying to get everything to work over samba, I suggest you use NFS to perform file sharing between OSX and Ubuntu. For Ubuntu, there is a nice NFS howto in my sig. You'll be able to find many good howtos for NFS in OSX online.

> **psymole said:**
> When I click on the shared folders in the d: drive from nautilus I get this error **"You do not have the permissions necessary to view the contents of "Name of the share"."**
You'll need to check two sets of permission levels on the D drive. You'll need to check all of the share permissions on all shared drives on the D drive. You'll also need to check the folder and file permissions on the folders and drive itself.

This KB article should point you in the right direction: [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

---

### Post by psymole on 2010-04-18
Thanks dmizer, will try this and see if I can figure it out

> You'll need to check two sets of permission levels on the D drive. You'll need to check all of the share permissions on all shared drives on the D drive. You'll also need to check the folder and file permissions on the folders and drive itself.

This KB article should point you in the right direction: [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

Xp securities options are confusing as hell.

will report back

---

### Post by psymole on 2010-04-18
Thanks again dmizer

Just tried this solution and my network is back 100%.

Only thing I had to do beside what you and the article linked pointed, was to un-share and re-share the folders in the windows machine. 

> **dmizer said:**
> 
You'll need to check two sets of permission levels on the D drive. You'll need to check all of the share permissions on all shared drives on the D drive. You'll also need to check the folder and file permissions on the folders and drive itself.

This KB article should point you in the right direction: [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

---

### Post by klein de usa on 2010-04-26
hi 
i have a few 8.04 computers running on a network, the only way i can share files between 8.04 computers over my network is by going into nautilus and sharing them, and let nautilus install the smb files and set permission, after that i set my smb password in terminal, and with a desk top launcher i can open a shared home directory on another ubuntu computer. i have noticed that doing it this way doesn't change my smb.conf file but it works, after made the changes at the beginning of this post i can now see the other computers, but can't open the shared files,  

my question is should i be able to open another shared file on another ubuntu computer through places > network >

i have noticed if i do a fresh install of ubuntu 8.04.3 with out any updates i can go to places > network > and see all my ubuntu and windows computers and open any shared files but as soon as i up date that computer the places > network > quits working

this is a little confusing one ubuntu computer should share with another ubuntu computer easily i would thing i'm sure there is something i'm missing ? 

any thoughts ???

---

### Post by crashley on 2010-04-27
Thanks, dmizer!
Problem 3, pts. 1 and 2, solved my connection issue from my Ubuntu 10.4 partition on my laptop to my WinXP desktop.

---

### Post by John Bennett on 2010-05-03
> **dmizer said:**
> ```
 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```

Changing the WORKGROUP name did not work for me.

Adding "wins" did work for me.

All my XP machines now show up in Nautilus.

Thank you dmizer!!!

[I]Ubuntu 10.04
MSI L1300 Netbook
Windows XP Network[/I]

---

### Post by Tonyaude on 2010-05-04
Thanks for all your info - I have followed it word for word, and can see the windows shares but no matter what I do I still get bounced back to the password screen every time I try to connect to the shares even though on the Windows machine I have turned off password sharing. No problem connecting to the Ubuntu shares from Windows.I'm running 10.04

---

### Post by Tonyaude on 2010-05-04
Thanks for all your info - I have followed it word for word, and can see the windows shares but no matter what I do I still get bounced back to the password screen every time I try to connect to the shares even though on the Windows machine I have turned off password sharing. No problem connecting to the Ubuntu shares from Windows.I'm running 10.04

---

### Post by dmizer on 2010-05-04
> **klein de usa said:**
> this is a little confusing one ubuntu computer should share with another ubuntu computer easily i would thing i'm sure there is something i'm missing ? 

any thoughts ???
Actually, if you are just using Ubuntu, I suggest you try NFS instead of Samba. It's easier to configure (even though you have to use the CLI). There is a link to a good NFS tutorial in my sig.

> **Tonyaude said:**
> Thanks for all your info - I have followed it word for word, and can see the windows shares but no matter what I do I still get bounced back to the password screen every time I try to connect to the shares even though on the Windows machine I have turned off password sharing. No problem connecting to the Ubuntu shares from Windows.I'm running 10.04
Do you also have a Samba server running on the Ubuntu computer? As odd as this may seem, the password prompt may not be from the machine you are trying to access.

---

### Post by Nevis on 2010-05-04
Excellent work on this dmizer, thanks for the effort you put in!

I believe in Ubuntu 10.04 restarting the samba daemon is now done by the command;

```
sudo restart smbd
``` 

You might want to update you original post to clarify this for Lucid users.

---

### Post by Tonyaude on 2010-05-05
> **dmizer said:**
> Actually, if you are just using Ubuntu, I suggest you try NFS instead of Samba. It's easier to configure (even though you have to use the CLI). There is a link to a good NFS tutorial in my sig.


Do you also have a Samba server running on the Ubuntu computer? As odd as this may seem, the password prompt may not be from the machine you are trying to access.

I have the Samba server running and to simplify things for the moment I have made all my passwords the same. I can see the shares in Nautilus but whatever I do (I have created a user with the same name in Windows 7 and Ubuntu and checked all the workgroup names are the same)I just get bounced back to the password screen if I try to connect directly from the icons within Nautilus OR if I take the Connect to Server from within Nautilus after putting in the password I get Could not display "smb://%5C%5Cw7-portable/". followed by "failed to retrieve share list from server"

Again many thanks for all your work

---

### Post by dmizer on 2010-05-05
> **Tonyaude said:**
> Could not display "smb://%5C%5Cw7-portable/"

It looks like you have non-ascii characters in your path name. That may be causing you problems.

---

### Post by Tonyaude on 2010-05-05
> **dmizer said:**
> It looks like you have non-ascii characters in your path name. That may be causing you problems.

The Path Name I type in is "\\w7-portable" which produces the %5c message. If I use just "w7-portable" I get "smb://w7-portable/". The rest of the error message being the same.

---

### Post by dmizer on 2010-05-05
> **Tonyaude said:**
> The Path Name I type in is "\\w7-portable" which produces the %5c message. If I use just "w7-portable" I get "smb://w7-portable/". The rest of the error message being the same.
Same results if you browse to the share rather than typing in the path name manually?

---

### Post by klein de usa on 2010-05-05
hi dmizer 
no i do have a couple of xp computers i would like to network with ubuntu but the bulk of my computers are ubuntu 8.04 one is 8.10 and i have a couple with 10.4. some are dull boot 8.04 and 10.4.

i think where i made my mistake was a while back i would go into sudo nautilus and share my home folder, ubuntu would set the permission for me then i would set the samba password in terminal. from that point i would create a desktop launcher and the command i would use is smb://xxx.xxx.x.xx/home folder share name/  this works well but i'm not able to share the printers. and never figured out how to share a second drive.  

klein@xgen2:~$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 "XGEN2"                       "WORKGROUP"
"XGEN2"                   40849a03 "xgen2 server (Samba, Ubuntu)" "WORKGROUP"
"D32K5JC1"                40011003 "Just the mommy's"            "WORKGROUP"
"LG2"                     40819a03 "lg2 server (Samba, Ubuntu)"  "WORKGROUP"
"STORAGE"                 40819a03 "storage server (Samba, Ubuntu)" "WORKGROUP"
"LG1"                     40819a03 "lg1 server (Samba, Ubuntu)"  "WORKGROUP"
"LG3"                     40819a03 "lg3 server (Samba, Ubuntu)"  "WORKGROUP"

as a result witch ever computer is started first is the one that becomes the server i would like the computer STORAGE to be the server i'm just not sure how to straighten what i have done out

---

### Post by Tonyaude on 2010-05-06
> **dmizer said:**
> Same results if you browse to the share rather than typing in the path name manually?

I'm afraid so.

---

### Post by Tonyaude on 2010-05-10
> **Tonyaude said:**
> I'm afraid so.

Hi DMIZER - Thanks for your help but for me at least this seems to have been a Windows issue. It seems that - Windows Live ID sign in Asssistant - which almost always gets installed by default with the Office Live add in, messes up SMB sharing see:- [http://social.technet.microsoft.com/Forums/en/w7itproappcompat/thread/e4fc6ba5-968e-4370-8a5c-680db85d326c](http://social.technet.microsoft.com/Forums/en/w7itproappcompat/thread/e4fc6ba5-968e-4370-8a5c-680db85d326c) So on my Windows machines I Uninstalled Windows Live ID sign in Assistant, rebooted and all is now working as it should do.

You may wish to add this info to your original and very helpful post of 25th May 2009.

---

### Post by Ambidextrous on 2010-05-22
Sensei:

I've returned to Ubuntu (now I can get my Nvidia graphics cards to function correctly) to discover that I can't connect to the Windows machines on my home network.  In Feisty, Gutsy and Hardy all I had to do - straight out of the box, so to speak - was click on "Network", double click on "Windows Network", double click on the Windows PC of my choice and see a list of shared folders.

Now, even though Lucid can "see" the other PCs :

[IMG]http://members.shaw.ca/sapient/shares.png[/IMG][IMG]http://members.shaw.ca/sapient/Shares.png[/IMG]

double-clicking produces:

[IMG]http://members.shaw.ca/sapient/Mount.png[/IMG]

I've spent a few days working through the thread and trying things as I went, but so far, what you see above is the best result I've managed.

"Asus" is running Lucid
"Kate-PC" is running Vista Home Premium, SP2
"Dell-Laptop" is running Xp Home SP3

All have static IP addresses assigned to their MACs, and each can ping the other two PCs.  The firewall on the Windows PCs is the anti-virus software (a version of F-Protect branded by my ISP) and it is set to allow file and printer sharing from the subnet.  "Asus" has no firewall other than the router.

Running *findsmb* produces:

```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.110   ASUS           [WORKGROUP] [Unix] [Samba 3.4.7]
```Running *iptables -L* produces:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```*smb.conf* is as follows:

```
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = Asus

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts wins bcast host

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
```and *nsswitch.conf* contains:

```
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```Your help would be deeply appreciated.

[IMG]http://members.shaw.ca/sapient/mount.png[/IMG]

---

### Post by mgmiller on 2010-05-22
Ambidextrous

The only things I can think of to try would be to make sure the 2 Windows machines are in the "WORKGROUP" workgroup and then, on both windows machines, go to the folders you have shared and turn off sharing and then turn sharing back on again.  You may also need to reboot the 2 windows machines after doing this, while the Ubuntu machine is running and on the network.

---

### Post by Ambidextrous on 2010-05-23
> **mgmiller said:**
> Ambidextrous

The only things I can think of to try would be to make sure the 2 Windows machines are in the "WORKGROUP" workgroup and then, on both windows machines, go to the folders you have shared and turn off sharing and then turn sharing back on again.  You may also need to reboot the 2 windows machines after doing this, while the Ubuntu machine is running and on the network.

The Windows machines both belong to the "WORKGROUP" workgroup.  (Note the title-bar in Nautilus in the original post.

I only had "Del-Laptop" available to test with, but I unshared, then re-shared the shared folders and tried to connect from the Ubuntu machine:

[IMG]http://members.shaw.ca/sapient/Opening.png[/IMG]

...and my spirits began to soar...

[IMG]http://members.shaw.ca/sapient/Mount2.png[/IMG]

Prematurely, it would seem.

Thank you for your suggestion, but the problem persists.  :(

---

### Post by dmizer on 2010-05-23
This is an enabled firewall.
> **Ambidextrous said:**
> ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination 
```

This is most likely the source of your problem. Disable the firewall unless you absolutely need it. If you think you must have a firewall, then you probably shouldn't be poking holes in it so that you can share files.

You can disable the firewall with this command:
```
sudo ufw disable
```

---

### Post by Ambidextrous on 2010-05-24
> **dmizer said:**
> This is an enabled firewall.

This is most likely the source of your problem. Disable the firewall unless you absolutely need it. If you think you must have a firewall, then you probably shouldn't be poking holes in it so that you can share files.

You can disable the firewall with this command:
```
sudo ufw disable
```

Done... but it had no effect on my ability to connect to either Windows machine.  I got the same response  "Failed to retrieve share list from server".

I edited my orignal post with the output from *iptables -L* after disabling the firewall.

---

### Post by dmizer on 2010-05-25
> **Ambidextrous said:**
> Done... but it had no effect on my ability to connect to either Windows machine.  I got the same response  "Failed to retrieve share list from server".

I edited my orignal post with the output from *iptables -L* after disabling the firewall.

Ok, make sure the settings persist after a reboot. Also, try disabling any firewalls on the Windows machines as well.

---

### Post by Ambidextrous on 2010-05-25
> **dmizer said:**
> Ok, make sure the settings persist after a reboot. Also, try disabling any firewalls on the Windows machines as well.

It did persist.

I deactivated the firewalls on the windows machines and could connect immediately - however, both firewalls were configured to "allow file and printer sharing from the subnet".  I need to find out which ports and which protocols are being used by samba and make exceptions in the firewall settings on both windows machines.

Are these the correct ports?


[LIST]
[*]Port 137/UDP - used by nmbd
[*]Port 138/UDP - used by nmbd
[*]Port 139/TCP - used by smbd
[*]Port 445/TCP - used by smbd
[/LIST]


Thank you, Sensei.

---

### Post by dmizer on 2010-05-28
> **Ambidextrous said:**
> It did persist.

I deactivated the firewalls on the windows machines and could connect immediately - however, both firewalls were configured to "allow file and printer sharing from the subnet".  I need to find out which ports and which protocols are being used by samba and make exceptions in the firewall settings on both windows machines.

Are these the correct ports?


[LIST]
[*]Port 137/UDP - used by nmbd
[*]Port 138/UDP - used by nmbd
[*]Port 139/TCP - used by smbd
[*]Port 445/TCP - used by smbd
[/LIST]


Thank you, Sensei.

These are all the ports related to samba file sharing and name resolution:
[LIST]
[*]Port 135/TCP - used by smbd
[*]Port 137/UDP - used by nmbd
[*]Port 138/UDP - used by nmbd
[*]Port 139/TCP - used by smbd
[*]Port 445/TCP - used by smbd
[/LIST]

---

### Post by klein de usa on 2010-05-29
hi 
i had posted earlier in this thread, i finally fixed my problem quite by mistake. sometime ago after i had quit messing with getting samba to work my linksys router went bad and i replaced it with one running dd-wrt unknowing to me my router does dns so when i installed a new ver of ubuntu, ubuntu picked up on this and used my router as a dns server. all i had to do was change the dns's on the older installs to my router and redo my shares in 8.04 i still had the .dmrc problem and followed the usual fix, so now i have xp,win7,ubuntu 8.04 and 10.4 all sharing files nicely.

i didn't have to make any changes to the smb.conf file or install anything other that what ubuntu does when you first share a file.   

is it passable to install or make ubuntu a dns server, if you have one computer running all the time or the first one you usualy start?

---

### Post by memeri on 2010-06-10
My problem is that windows 7 logs onto both of my ubuntu accounts automatically. I've tried to configure things to require user authentication. I have ubuntu 9.10. Here are the mostly relevant bits of etc/samba/smb.conf. I've followed your win7 instructions here. 


```
#======================= Global Settings =======================

[global]

   workgroup = usnthem
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   read only = no

#  This seems to help
   path = /home
   valid users = %S
```


This might also be relevant:

```

$ sudo pdbedit -L -w
nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:
mary:1001:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:159EA51341BD0FB531D630F25B2672BD:[U          ]:LCT-4C114AC6:
mark:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:32C5FA7B2B28B47B6959536DC914C4D0:[U          ]:LCT-4C11755A:
```

Win 7 just gives instant access to the complete directory trees of mark and mary without presenting a logon dialog. What am I missing?

---

### Post by dmizer on 2010-06-10
> **memeri said:**
> My problem is that windows 7 logs onto both of my ubuntu accounts automatically. I've tried to configure things to require user authentication. I have ubuntu 9.10. Here are the mostly relevant bits of etc/samba/smb.conf. I've followed your win7 instructions here. 

You are having a problem with Windows accessing Ubuntu, and unfortunately, this thread is only for helping you to access Windows shares from Ubuntu.

Please start a new thread. If you like, you can feel free to post a link here once you have done so.

---

### Post by memeri on 2010-06-11
Thanks

---

### Post by config.sys on 2010-06-12
Thank you! Thank you! Thank you!

I would have never found the answer to this frustrating puzzle on my own. Following your guide I was up and browsing my Windows shares in about 15 minutes.

---

### Post by jiaolu on 2010-06-15
it's such nice post .that i have register a account to post to thank op.

---

### Post by coyotearms on 2010-06-21
DMIZER, After a long hunt over the internet, I finally found this thread.  It looks very promising, but before I attempt to fix my Windows sharing problem on 10.04 with an XP, Vista and Win7 computers on the LAN, I have two questions.

First I have undone all changes suggested by others (that did not work) except for one.  I want to make sure I start from where everything was when I (recently) installed 10.04.  I had done
sudo apt-get install samba
sudo service samba restart
along the way before checking whether it was already installed.  The weird thing (to me) was the result of the restart command was
samba: unrecognized service
I don't know what that means and I don't know what will happen if I uninstall samba.

Second, I would like to read about manually mounting shares via /etc/fstab stuff that you indicate is available in the "second link in your signature."  I am so helpless I cannot even find that.

---

### Post by dmizer on 2010-06-22
> **coyotearms said:**
> 
along the way before checking whether it was already installed.  The weird thing (to me) was the result of the restart command was
samba: unrecognized service
I don't know what that means and I don't know what will happen if I uninstall samba.
In short, don't worry about that error, and don't uninstall samba. The samba server daemon has been updated in 10.04 to samba4, but this shouldn't be a concern of yours if you only want to connect to Windows shares on other computers. Just reboot after making the changes instead of running the "sudo /etc/init.d/samba restart" command. 

> **coyotearms said:**
> Second, I would like to read about manually mounting shares via /etc/fstab stuff that you indicate is available in the "second link in your signature."  I am so helpless I cannot even find that.
Signature here
|
|
|
|
|
|
|
|
V

---

### Post by varunendra on 2010-06-24
> **dmizer said:**
> In short, don't worry about that error, and don't uninstall samba. The samba server daemon has been updated in 10.04 to samba4, but this shouldn't be a concern of yours if you only want to connect to Windows shares on other computers. Just reboot after making the changes instead of running the "sudo /etc/init.d/samba restart" command. 


Is samba4 out? The one with active directory like capabilities? Or is it still under process?

Sorry for not relating to the thread. In fact I directly came up to the above quoted post of yours (dmizer) & noticed you mentioning samba4. I'm so excited about it that I couldn't help putting the question.

---

### Post by coyotearms on 2010-06-24
Dimizer, Unless installing samba uninstalls samba4, the latter was not installed when I did a fresh install of 10.04 since Synaptic Package Manager shows samba4 not installed and without the "package is supported" Ubuntu icon next to it either(?).  Nevertheless, if you say sticking with samba and not doing samba4 is o.k., I'm fine with that.

Also, between my first message and your response I implemented your steps 1 through 3, and I have reasonable results, but have a question about them.  My setup is three computers all set to workgroup XYZ with Ubuntu on computer A, Vista on computer B wired, and WinXP on computer C wireless.  When the Ubuntu computer is wired, single clicking on Network shows all three computers and Windows Network.  Double clicking on B or C gets me to those guys.  Double clicking on Windows Network gets me to XYZ, and double clicking on it show all three computers again---Great!

If I change the Ubuntu computer to wireless, the results are quite uneven, and frequently I cannot access the other wireless computer C.  I have a pretty old D-Link DI-524 Rev. E router/access, but the Ubuntu computer is only a few feet away, and when that computer is booted Win7, these same shares are found really fast. When I do nautilus smb://C from a terminal window, bookmark it and single click on that bookmark, that seems to work better, but not always either.  So what is going on that makes the wireless Ubuntu computer behave differently?

Thanks in advance!

---

### Post by dmizer on 2010-06-24
> **varunendra said:**
> Is samba4 out? The one with active directory like capabilities? Or is it still under process?

Sorry for not relating to the thread. In fact I directly came up to the above quoted post of yours (dmizer) & noticed you mentioning samba4. I'm so excited about it that I couldn't help putting the question.
Looks that way for Lucid:
```
$ aptitude search samba4
p   samba4                          - LanManager-like file server for Unix (vers
p   samba4-clients                  - client utilities from Samba 4             
p   samba4-common-bin               - Samba 4 common files used by both the serv
p   samba4-dev                      - tools for extending Samba                 
p   samba4-testsuite                - test suite from Samba 4
```

> **coyotearms said:**
> Dimizer, Unless installing samba uninstalls samba4, the latter was not installed when I did a fresh install of 10.04 since Synaptic Package Manager shows samba4 not installed and without the "package is supported" Ubuntu icon next to it either(?).  Nevertheless, if you say sticking with samba and not doing samba4 is o.k., I'm fine with that.

Also, between my first message and your response I implemented your steps 1 through 3, and I have reasonable results, but have a question about them.  My setup is three computers all set to workgroup XYZ with Ubuntu on computer A, Vista on computer B wired, and WinXP on computer C wireless.  When the Ubuntu computer is wired, single clicking on Network shows all three computers and Windows Network.  Double clicking on B or C gets me to those guys.  Double clicking on Windows Network gets me to XYZ, and double clicking on it show all three computers again---Great!

If I change the Ubuntu computer to wireless, the results are quite uneven, and frequently I cannot access the other wireless computer C.  I have a pretty old D-Link DI-524 Rev. E router/access, but the Ubuntu computer is only a few feet away, and when that computer is booted Win7, these same shares are found really fast. When I do nautilus smb://C from a terminal window, bookmark it and single click on that bookmark, that seems to work better, but not always either.  So what is going on that makes the wireless Ubuntu computer behave differently?

Thanks in advance!

It could be a couple of things. Re-check for a firewall while using Ubuntu wirelessly. Also take a look at your router settings, there could be a wireless security setting interfering with file sharing (I realize that you have an XP working wirelessly, but it can't hurt to check).

---

### Post by Drastica on 2010-06-25
Had to register just to post here. Thank you SO MUCH for this thread, Dmizer, and the rest. I was lucky, I found this page pretty quick after my first day wrestling with this issue. While I don't have it all going perfectly, (and I seriously doubt ANYONE does), it now works reliably almost all the time, and I can now browse my shares via Network in Nautilus. Oddly, xsmbrowser shows nothing at all under WINS, but both my workstations now show up in Samba Config there.

In the end, the easiest way for me was to use the hosts file to just permanantly assign those addresses to the machines. Wish it hadn't take me 3 on and off days of wrestling, but I am a very happy camper right now.

So, in short, once again, a very big THANK YOU for this thread. I will be sure to keep my eyes open here for future developments!

Oh, and a big tip you had some pages back that helped: the line

dns proxy = no

In this thread, you see it both commented, and uncommented, and if you hadn't made it very clear some pages back that that should have the ; in front, I'd still be wrestling with this. Takes two reboots for it to show for me, but if I don't put a ; in front of that line, the whole thing breaks, and I get nothing at all. With the ; there, it works, though it takes a few full reboots for some reason to settle in. Strange, but...for me...true.

Keep up the good work!

---

### Post by fhd on 2010-07-04
Thanks a lot for this thread, problem 3 solved my host browsing issues.

I'm wondering why this was necessary on Lucid Lynx (had the issue on two computers) and not on Karmic Koala (worked out of the box).

Is this a bug or a feature in Lucid?

---

### Post by dmizer on 2010-07-04
> **fhd said:**
> Thanks a lot for this thread, problem 3 solved my host browsing issues.

I'm wondering why this was necessary on Lucid Lynx (had the issue on two computers) and not on Karmic Koala (worked out of the box).

Is this a bug or a feature in Lucid?

As you can see from the date of my post and from the date of my other samba howto, this has been an ongoing issue since I started using Ubuntu back in the Hoary days. Frankly, I don't know why some machines can do it and some can't.

In this case, it's possible that both machines are trying to be the domain master browser. Here's some more information on that: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-network-browsing.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-network-browsing.html)

---

### Post by googlo on 2010-07-18
Thanx alot for posting this.... I'm a complete newbie and just installed lucid lastnight...looks great cnat wait to play with it.
 
Now I can see my Vista laptop on my Ubuntu desktop and access files and move them out of my laptop files.
 
First I followed these steps:
[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)
 
Then I found your site when I got the following message "'Failed to retrieve share list from server' "
 
 
The only issue I'm having is that I cant access my Ubuntu desktop from my Vista laptop...
I was hoping to  be able to empty out my laptop and keep the files on the desktop ( such as photos,videos...etc ) so I can access them from the Desktop when needed...
 
I can drop them into the public folder of vista laptop from Ubuntu desktop, but I would love to be able to access them from the laptop  without having to go to the other room...lazy.. yeah I know.
 
Any info you could give me to resolve that issue...or someplace to refer me to?
 
any info will be greatly appreciate it.
 
If you need me to do something to help yopu please let me know how to do it... like I said im just a two day old user.
 
Thanks again.

---

### Post by GriFF3n on 2010-07-20
Thanks dmizer, Fix #2 did the trick for me!!! :D

---

### Post by dmizer on 2010-07-20
> **googlo said:**
> The only issue I'm having is that I cant access my Ubuntu desktop from my Vista laptop...

This thread is dedicated to solving problems with Ubuntu accessing Windows. If you need help with Windows accessing Ubuntu, you'll need to start a new thread.

Feel free to leave a link here to your new post and I'll try to take a look!

---

### Post by okos on 2010-07-21
Dmizer,

Great Job!
This solved my issues.

---

### Post by coyotearms on 2010-07-23
> **dmizer said:**
> Looks that way for Lucid:
```
$ aptitude search samba4
p   samba4                          - LanManager-like file server for Unix (vers
p   samba4-clients                  - client utilities from Samba 4             
p   samba4-common-bin               - Samba 4 common files used by both the serv
p   samba4-dev                      - tools for extending Samba                 
p   samba4-testsuite                - test suite from Samba 4
```



It could be a couple of things. Re-check for a firewall while using Ubuntu wirelessly. Also take a look at your router settings, there could be a wireless security setting interfering with file sharing (I realize that you have an XP working wirelessly, but it can't hurt to check).

Yep, it was the router, a D-Link 524 Rev. E.  Its DHCP became flaky and was not updating leases.  Rebooting cured that, and after a while it was well-behaved again.

---

### Post by Shalmainia on 2010-07-24
I used to have this folder, of which I shared, now I don't... so how do I remove it?
I typed in
```
net usershare info
```
```
info_fn: file /var/lib/samba/usershares/streaming is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```

---

### Post by dmizer on 2010-07-25
> **Shalmainia said:**
> I used to have this folder, of which I shared, now I don't... so how do I remove it?

Perhaps this thread may help you in finding what's holding things up: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

I really know very little about net usershares.

---

### Post by Canyonero on 2010-07-26
> **dmizer said:**
> This thread is dedicated to solving problems with Ubuntu accessing Windows. If you need help with Windows accessing Ubuntu, you'll need to start a new thread.

Feel free to leave a link here to your new post and I'll try to take a look!

I'm having that kind of problem, and can't seem to figure it out. I've read many posts on many threads and haven't come across anything that fixes my problem. Could you please take a look at the thread I started here?: [http://ubuntuforums.org/showthread.php?p=9636515](http://ubuntuforums.org/showthread.php?p=9636515)

---

### Post by j.green on 2010-07-26
I have been at this for a while now.  Your instructions have gotten me further than I've been in days.  But of course I'm posting because everything isn't *quite* right yet.

I run an Ubuntu (Hardy) file/web server on a home network consisting (until now) of one Windows laptop (Win7).
The *new guy* on the network is an Ubuntu (Lucid) laptop.
Win7 continues to access my shares exactly as it should and is not a problem at all so we'll disregard it's existence for the sake of this exercise.

I should mention that the Hardy server has three physical drives, two of which are formatted NTFS from when I used to run a Windows server. (The third is the OS drive so it's ext3)

Of these three physical drives there are four logical drives, and thus four shares on the server:
Web, Photos, Music, and Files

_So here is the issue:_

Using Lucid laptop, all four shares show up in *Network*.
Lucid laptop can now mount and access Web perfectly (Thanks a million!)
However it can *not* mount Photos, Music, or Files.

Upon attempting to open either of those three, the error dialog reports:
[INDENT]Unable to mount location
Failed to mount Windows share[/INDENT]

After wracking my brain the only thing I can think of is that Web, being ext3, is of course mountable with no issue.  So perhaps Lucid is having an issue with the other three shares because they are NTFS?? (if it matters, I do have ntfs-3g installed on both Ubuntu machines).

Sorry for the long post but I figured the more information you had the better help you could provide.

Thanks!
- J

---

### Post by dmizer on 2010-08-05
Do all of your server's drives have an entry in /etc/fstab? If not, that's probably your problem.

---

### Post by j.green on 2010-08-05
Yes, the server's /etc/fstab file has an entry for each hard drive so they will automount on startup.

---

### Post by dmizer on 2010-08-05
> **j.green said:**
> Yes, the server's /etc/fstab file has an entry for each hard drive so they will automount on startup.

Please post the contents of /etc/fstab

---

### Post by j.green on 2010-08-05
Contents of server's /etc/fstab

Notes:
/dev/hda1 = primary OS drive (contains the www share that works just fine)
/dev/hda2 = swap space
/dev/hdb1 = music
/dev/hdb2 = files
/dev/sdc1 = photos

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6631bf9c-b68e-4d15-9aee-2cf7e5f6b240 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=1D835098019257C9 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb2
UUID=1CF5FCBE77C3FFD3 /media/hdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=7e47353c-a8fc-4094-8b5e-fc98886fe098 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /media/photos   ntfs    defaults,umask=007,gid=46     0        2
```

---

### Post by dmizer on 2010-08-05
I think your problem is the "umask=007,gid=46" options. Try this instead:
1) Find your locale:
```
locale | grep LANG
```
Mine looks like this ->
```
$ locale | grep LANG
LANG=[COLOR="Red"]en_US.UTF-8[/COLOR]
```
2) Make your fstab line look like this (locale from above in red) -> 
```
UUID=1D835098019257C9 /media/hdb1     ntfs    defaults,locale=[COLOR="Red"]en_US.UTF-8[/COLOR] 0 0
```

Test that and see if that allows your music to be seen. If so, repeat the process for the rest of your NTFS drives.

---

### Post by j.green on 2010-08-06
The locale fix worked!
Thanks dmizer, you're a rockstar. :D

---

### Post by Thomas Garman on 2010-08-06
You have to have installed the libapache2.2 and libapache-mod-dns from Synaptic to get mounts to work with SAMBA in Lucid.

---

### Post by dmizer on 2010-08-06
> **Thomas Garman said:**
> You have to have installed the libapache2.2 and libapache-mod-dns from Synaptic to get mounts to work with SAMBA in Lucid.

Humm, neither of those packages are available in the repositories I have enabled in my Lucid install.

Also, there is really no reason to need apache or anything remotely related to it in order to make samba mounting or browsing work. Perhaps you've installed ebox?

---

### Post by necromonger on 2010-08-22
this how to is great.

---

### Post by montheponies on 2010-08-29
After upgrading to 10.04 from 8.04, I had a couple of problems. The part 3 changes helped me resolve a problem with my laptop not being 'seen' by my router ie. wouldn't appear as an attached device, and subsequently couldn't be found by any other machines on the network. Also used the cifs tutorial to permanently mount my NAS share, so all good.

Many thanks :D

---

### Post by necromonger on 2010-08-29
Do you think samba will be a little bit better for new users.In 10.10

---

### Post by dmizer on 2010-08-29
> **necromonger said:**
> Do you think samba will be a little bit better for new users.In 10.10

I don't really think Samba is bad now. If you look at the howto and read through this thread carefully, you will realize that most of the problems with Samba are not software related. Many problems are related to unnecessary firewalls, permissions, and/or shallow understanding of basic networking.

No amount of coding can fix those problems.

---

### Post by SuperDupes on 2010-09-05
DMizer saves the day!  My 2 ubuntu compys can see and share.  Only problem was getting rhythmbox to play songs from my other computer, but I just found a PPA to take care of that.

Next issue:

I have a computer running windows 7 which I would love to be a part of the network.  My ubuntu compys see it, but fail to mount it, and the windows laptop can't see either of the ubuntu computers on the network.   I followed all of the instructions on your how to to no avail.  Neither ubu computers have firewalls and I have printer sharing enabled on the 7 box (I believe that allows smb?)

Anyway, kind of a noob here.

Thanks for your help!

---

### Post by SuperDupes on 2010-09-06
So,

All seems to be working now except:

To access my ubu compys from win 7, I have to type in the ip every time. They are not remembered.

I still can't access my win 7 from mu ubus.  unable to mount message.

Any Ideas?

---

### Post by oldsoundguy on 2010-09-06
make sure you have installed networking on the WINDOWS machine .. and that you have granted network access to the items and files and folders you wish to share.

---

### Post by SuperDupes on 2010-09-06
Install networking?  Shouldn't that just be already all set all there on Windows 7?  What to I need to install?

I made sure not to use homegroup, but I still can't connect to \\workgroup\mycomp from win 7

---

### Post by dmizer on 2010-09-06
> **SuperDupes said:**
> Install networking?  Shouldn't that just be already all set all there on Windows 7?  What to I need to install?

I made sure not to use homegroup, but I still can't connect to \\workgroup\mycomp from win 7

What version of Win7 are you using?

---

### Post by SuperDupes on 2010-09-07
Windows 7 pro, 32 bit

---

### Post by Artyom7 on 2010-09-10
Hi all,

I have been facing problems with setting up a file server @ home for about two weeks now.
So i have decided to compile a detailed report of the problems i am facing.
i have a very simple network setup.
One desktop running ubuntu 10.04 64 bit server
hostname artyom, ip =192.168.1.3
this one is directly connected to a wifi router via lan cable

I have 3 laptops, 2 running ubuntu 10.04 64 bit and one running windows 7 64 bit

the ubuntu laptops are setup as follows 
1:
hostname pria, ip = not set manually
2:
hostname art, ip = 192.168.1.5

the windows laptop has its ip set to automatic, ad hostname is pria_laptop

All computers are in the same room

My aim is to set up a simple file sharing server so that i can automate daily backups.
I have followed multiple how-to's, manuals, tutorials, etc. I even did the "samba by example" 
from the documentation. I even resorted to the windoze way ( reinstalling the OS ) once, but still no luck.

I am unable to access the shares of my server from any of the other machines.
i can see the server and the shares from all the laptops,but i cannot access them.
in ubuntu i get
"unable to mount windows share" ( or something like that )

in win7 I get an error saying that the location does not exist and that i should check the spelling.


i have 2 users set up on the server to access the shares
usernames : artyom and pria
both belong to the group backupusers
both have a password.
Both have been added via smbpasswd -a username
Both have been enabled via smbpasswd -e username
Both users also have accounts on the server, and the accounts are active, with home folders and all.

the smb.conf file on the server is :
```

[global]

workgroup = WORKGROUP
netbios name = artyom
security = user
name resolve order = lmhosts wins bcast host
smb ports = 139

[library]
comment = media library
path = /media/home/shared
browseable = yes
read only = yes
guest ok = yes

;[backup]
;path = /media/home/backup
;browseable = yes
;read only = no
;guest ok = no
;writable = yes

```

i commented out the second part while testing

the nsswitch.conf file line is

```

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

The reason why im puzzled by this problem is that i have successfully setup samba shares on my laptop ( art ).
the smb.conf for laptop art is:
```

[global]

workgroup = WORKGROUP
netbios name = art
security = user
name resolve order = lmhosts wins bcast host

################################
[shared]

comment = shared files
path = /home/artyom/Shared
browseable = yes
read only = yes
guest ok = yes

################################
[incoming]
comment = put your files here
path = /home/artyom/Downloads/DANGEROUS_CONTENT 
force user = netuser
force group = networkaccess
read only = no
guest ok = yes
create mask = 0775
directory mask = 0775

###############################
[Media]
comment = pirated files here
path = /home/artyom/Music
read only = yes
guest ok = no
create mask = 755
directory mask = 755
force user = artyom
force group = artyom

```
with the above configuration, it works flawlessly
[shared] share does not require anyone to enter a password, and is read only.
[incoming] is writabe by anyone, and does not need a password.
[Media] prompts for a password and acepts only the user "netuser" with the corresponding password.
this laptop's shares are accessible by both the other laptops ( win7 and ubuntu )

my server's log.smbd file is full of lines like these:
```

  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/10 19:39:30,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/10 19:39:30,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/10 19:39:30,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option

[2010/09/10 19:27:44,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service backup, path /media/home/backup

[2010/09/10 20:27:35,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service library, path /media/home/shared


```
the permissions on the shared folders are set to artyom:backupusers
backupusers is a group i created for 3 users ( pria, pria_laptop, artyom ) just to keep things organised.

ls -lv /media gives
```


total 24
drwxr-xr-x 11 administrator administrator 4096 2010-06-19 12:33 Documents
drwxr-xr-x  4 administrator administrator 4096 2010-07-18 08:55 Downloads
drwxr-xr-x  6 administrator administrator 4096 2010-07-18 08:48 Pictures
drwxr-xr-x  3 administrator administrator 4096 2010-08-20 11:32 Public
drwxr-xr-x  4 artyom        backupusers   4096 2010-09-08 19:43 backup
drwxr-xr-x 13 artyom        backupusers   4096 2010-08-28 18:29 share


```

smbclient -L artyom -U% output is :
```

	Sharename       Type      Comment
	---------       ----      -------
	library         Disk      media library
	IPC$            IPC       IPC Service (Samba 3.4.7)

	Server               Comment
	---------            -------
	ART                  Samba 3.4.7
	ARTYOM               Samba 3.4.7
	PRIA_LAPTOP          

	Workgroup            Master
	---------            -------
	WORKGROUP            ARTYOM

```
the setup seems to be simple enough not to cause any trouble. However i have been struggling with this for 2 weeks.
Am i doing something wrong?

---

### Post by dmizer on 2010-09-10
> **Artyom7 said:**
> the ubuntu laptops are setup as follows 
1:
hostname pria, ip = not set manually
2:
hostname art, ip = 192.168.1.5

the windows laptop has its ip set to automatic, ad hostname is pria_laptop


Your problem is probably that you are trying to run a static IP server in a DHCP network. Check your router's configuration and see if it has the capability of assigning permanent IP leases according to MAC address. That could solve your problem.

---

### Post by Artyom7 on 2010-09-11
> **dmizer said:**
> Your problem is probably that you are trying to run a static IP server in a DHCP network. Check your router's configuration and see if it has the capability of assigning permanent IP leases according to MAC address. That could solve your problem.

Thanks for your reply.

i have a beetel 450TC1 router. i went through all the options. all i can see is some sort of IP/MAC filters under Access Management -> Filters ( image attached ). Is that the right place to look? 

I am a bit apprehensive about messing around with the router settings. one of my laptops ( art ) is easily accessible by all others  and its ip is set to static. Maybe i should set a static ip on all the computers? Would that help?

thanks.

---

### Post by dmizer on 2010-09-12
> **Artyom7 said:**
> Thanks for your reply.

i have a beetel 450TC1 router. i went through all the options. all i can see is some sort of IP/MAC filters under Access Management -> Filters ( image attached ). Is that the right place to look? 

I am a bit apprehensive about messing around with the router settings. one of my laptops ( art ) is easily accessible by all others  and its ip is set to static. Maybe i should set a static ip on all the computers? Would that help?

thanks.

That's not what you're looking for. My best guess with the screenshot you attached would be under Advanced Setup. It may not say anything about MAC addresses. I looked briefly online and could not find a users manual for your router, if you can link to one, I'll take a look.

You may indeed have better luck if you change the entire network to static IP, but to do so correctly would mean that you would have to change the router configuration as well. Simply assigning a static IP to all the machines is not really a static network and can cause problems with name resolution.

---

### Post by Artyom7 on 2010-09-12
i found a link which has the screenshots of all the screens for this router :
[http://www.pcwintech.com/screenshots-beetel-450tc1-beetel-firmware]("http://www.pcwintech.com/screenshots-beetel-450tc1-beetel-firmware")

I could not find a manual either.

I have now resorted to reinstalling the server(again). Want to start off with a clean slate again.
will keep post the results once done.
The first time i reinstalled it today, i could not even login.

---

### Post by dmizer on 2010-09-12
> **Artyom7 said:**
> i found a link which has the screenshots of all the screens for this router :
[http://www.pcwintech.com/screenshots-beetel-450tc1-beetel-firmware]("http://www.pcwintech.com/screenshots-beetel-450tc1-beetel-firmware")

I could not find a manual either.

I have now resorted to reinstalling the server(again). Want to start off with a clean slate again.
will keep post the results once done.
The first time i reinstalled it today, i could not even login.

I did not see anything in the configuration that would allow you to configure a permanent DHCP lease.

I suggest that you start a new thread for your problem, as it is likely to be a server issue rather than a client issue, and this thread is for solving problems with clients.

Feel free to link here, and I will try to provide input if I can.

---

### Post by Artyom7 on 2010-09-12
Thanks dmizer.
i am pretty new to forums, so i might take some time to start a new thread. gotta go through forum help.

/edit :
i have posted here :
[http://ubuntuforums.org/showpost.php?p=9839610&postcount=5]("http://ubuntuforums.org/showpost.php?p=9839610&postcount=5")
Seemed like a reasonable place, since someone else has a similar problem.

---

### Post by ppafford on 2010-09-16
Fresh 10.4 install

Places -> Connect to server 
        Service type: (only one option shows) Custom Location

Places -> Network
        Error:
               Could not display "network:///".
               Nautilus cannot handle "network" locations.

Problem is I'm trying to connect to a Samba Share but I don't see any options to. I've also tried the command line and get this error:

```
smbclient -L //server/path/to/share -U username
Enter username's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```

and help on solving this would be great

---

### Post by dmizer on 2010-09-19
> **ppafford said:**
> Fresh 10.4 install

Places -> Connect to server 
        Service type: (only one option shows) Custom Location

Places -> Network
        Error:
               Could not display "network:///".
               Nautilus cannot handle "network" locations.

Problem is I'm trying to connect to a Samba Share but I don't see any options to. I've also tried the command line and get this error:

```
smbclient -L //server/path/to/share -U username
Enter username's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```

and help on solving this would be great

Try this:
```
sudo apt-get install smbfs
```

---

### Post by ppafford on 2010-09-20
Thanks but already installed:

sudo apt-get install smbfs

still no luck

---

### Post by ppafford on 2010-09-20
Thanks to Marco over at: [http://chat.meta.stackoverflow.com/rooms/181/ubuntu](http://chat.meta.stackoverflow.com/rooms/181/ubuntu)

Here is the package I was missing: sudo apt-get install gvfs-backends

[http://ubuntu.stackexchange.com/](http://ubuntu.stackexchange.com/)

---

### Post by Flos Headford on 2010-09-25
Hello, dmizer!
I've been lurking on this thread for some time: fascinating reading, and a grand display of kindness and civility it is. I've implemented  all of your Post No. 1 tips, and several more besides. I've now graduated to the point where I have a (possibly) interesting query:
I'm running Lucid and have two other Win2k boxes, all wired into my router. I can open a shared folder on one Win2k box, but not the other. I get the error:

Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Have you any pointers for this, please?
Thanks,
Phil

---

### Post by dmizer on 2010-09-25
> **Flos Headford said:**
> Hello, dmizer!
I've been lurking on this thread for some time: fascinating reading, and a grand display of kindness and civility it is. I've implemented  all of your Post No. 1 tips, and several more besides. I've now graduated to the point where I have a (possibly) interesting query:
I'm running Lucid and have two other Win2k boxes, all wired into my router. I can open a shared folder on one Win2k box, but not the other. I get the error:

Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Have you any pointers for this, please?
Thanks,
Phil
Dunno for sure how that happens when attempting to mount a Samba share. It's possible that the error is incorrect. Either way, make sure your machine is up to date:
```
sudo apt-get update
sudo apt-get full-upgrade
```

Also try rebooting.

---

### Post by turqoisehex on 2010-09-28
Thanks for the in depth solutions, but most of them seem to be targeted at issues between Ubuntu and Win. What about problems with Ubuntu browsing Ubuntu?

---

### Post by dmizer on 2010-09-29
> **turqoisehex said:**
> Thanks for the in depth solutions, but most of them seem to be targeted at issues between Ubuntu and Win. What about problems with Ubuntu browsing Ubuntu?

This is a problem I've yet to solve reliably. I'm open to suggestions. Generally, I would suggest using an alternate file sharing method for sharing files between Ubuntu servers and clients. For example, something like NFS is much less finicky, and requires far less time to configure than Samba.

Alternatively, you can use the CIFS mount method as outlined in the 2nd link in my sig.

---

### Post by turqoisehex on 2010-09-29
I read your sig links #2 and #4, both were very useful and well written. Thanks again ^__^

---

### Post by WildeBeest on 2010-11-07
dmizer,

I have 2 problems with browsing shares between Ubuntu and Windows.

I have 6 nodes on my home network.
3 Desktop PCs, 1 XP Pro, 1 - Jaunty, 1 - Lucid
3 Laptops, 2 XP Pro, 1 Win7 Home edition.

Problem 1
I can't browse any shares unless the lucid machine is on. No shares show up on the Win7 machine either.

Problem 2.
I followed your guide on setting up Win7 shares, but still can't browse them from the Ubuntu machines.
I can however browse the shares from the XP machines.

Any help is appreciated

---

### Post by dmizer on 2010-11-07
> **WildeBeest said:**
> dmizer,

I have 2 problems with browsing shares between Ubuntu and Windows.

I have 6 nodes on my home network.
3 Desktop PCs, 1 XP Pro, 1 - Jaunty, 1 - Lucid
3 Laptops, 2 XP Pro, 1 Win7 Home edition.

Problem 1
I can't browse any shares unless the lucid machine is on. No shares show up on the Win7 machine either.
Have you configured the Lucid machine to be the domain master browser? If that's the case, then this is expected behavior. The same could be true if your Lucid box is also acting as a local DNS server or as a NAT gateway.

> **WildeBeest said:**
> Problem 2.
I followed your guide on setting up Win7 shares, but still can't browse them from the Ubuntu machines.
I can however browse the shares from the XP machines.

Any help is appreciated
Are you able to connect to the Win7 shares by going to Places > connect to server ... and manually entering the Win7 connection information? While I understand that this is not as desirable as browsing the shares, it's better than nothing and could give me a better idea of what might be wrong.

---

### Post by WildeBeest on 2010-11-07
```
Have you configured the Lucid machine to be the domain master browser?  If that's the case, then this is expected behavior. The same could be  true if your Lucid box is also acting as a local DNS server or as a NAT  gateway.

```

How do I tell? I configured Samba the same as my Jaunty machine. Only my router should be the DNS server.

```
Are you able to connect to the Win7 shares by going to Places >  connect to server ... and manually entering the Win7 connection  information? While I understand that this is not as desirable as  browsing the shares, it's better than nothing and could give me a better  idea of what might be wrong. 
```

This doesn't work either. I enter the same user name/password I use to logon to the Win7 machine.

---

### Post by dmizer on 2010-11-07
> **WildeBeest said:**
> How do I tell? I configured Samba the same as my Jaunty machine. Only my router should be the DNS server.
If you had, you would know. It's not a simple matter, so I have honestly no idea why nothing would work on any machine unless the Lucid box is turned on. Perhaps if you posted the /etc/samba/smb.conf file from the Lucid box, it may shed some light on that.

> **WildeBeest said:**
> This doesn't work either. I enter the same user name/password I use to logon to the Win7 machine.
Try logging on as user guest, and no password.

If that doesn't work then double check for any firewalls or an anti-virus which may be interfering with the connection.

---

### Post by gordintoronto on 2010-11-07
> **WildeBeest said:**
> How do I tell? I configured Samba the same as my Jaunty machine. Only my router should be the DNS server.
...


Interesting. My network includes Windows XP, Lucid and Maverick. Every machine has a share, every machine can see every share. I have never "configured Samba."

---

### Post by WildeBeest on 2010-11-11
```
Try logging on as user guest, and no password.
```

No go. The password dialog just keeps reappearing.

```
If that doesn't work then double check for any firewalls or an anti-virus which may be interfering with the connection. 
```

Turned off all firewalls and anti-virus, Still no go.

Any other ideas?

---

### Post by dgilloch on 2010-11-20
I am having issues connecting to all windows shares with ubuntu 10.10. All windows machines can connect to my samba share. I am using ubuntu 10.10 as a guest operating system with Virtual Box 3.2.10 r66523. Networking is set to bridged on the virtual machine, so it would be obtaining a separate ip address from the host operating system ( windows 7 ). 

I have followed the instructions on the first page. My issue seems to be that I just can't log into the share "Password required for 192.168.0.102". I've created an smb user with the same username/password as the windows username/password for the share, (sudo smbpasswd -a dgilloch) however it seems the credentials are not accepted because the "Password required for 192.168.0.102" requiring username, domain and password pops up.

I've turned off my windows firewall completely and flushed iptables, as well as disable my antivirus on the windows side.
Something strange that I've noticed is /etc/samba/smbusers is completely blank.

-- I've used previous versions of ubuntu as guest operating systems and not had this issue before. It seems very strange. I can supply logs or results of any commands, if needed. I appreciate any help!

---

### Post by WildeBeest on 2010-11-24
hello, anyone?

---

### Post by dmizer on 2010-11-26
> **WildeBeest said:**
> hello, anyone?

I am working on this now, but I don't have a solution for you. If it means anything, I'm having the same problem.

---

### Post by dmizer on 2010-11-27
> **WildeBeest said:**
> ```
Try logging on as user guest, and no password.
```

No go. The password dialog just keeps reappearing.

```
If that doesn't work then double check for any firewalls or an anti-virus which may be interfering with the connection. 
```

Turned off all firewalls and anti-virus, Still no go.

Any other ideas?

Are you able to get connected if you go to Places > Connect to server ... change the "service type" to Window's share and enter the share information?

---

### Post by pjotr2k on 2010-11-27
Hello after reading trough this thread i finally got my networking with windows pc to work!

BUT! i tried everything in the first post and ended up with diffrent results every time.

the mpst annoying thing was when i used the problem 3 solution adding wins to the config, i got weird internet delays etc.

BUT!!!!! after reading trough all the replies etc i ended up seeing that dmizer said something interesting in post [#15]("http://ubuntuforums.org/showthread.php?p=7255859").
-------------------------------------------------------

Re: Can't connect to SAMBA share via Jaunty
Quote:
Originally Posted by Peter09  
Add wins after dns
This is incorrect. WINS should be before DNS. Some DNS providers (like OpenDNS) forward unknown DNS queries to a "did you mean" search page. To the system, this counts as a resolved host name. So in this situation, if DNS is queried before WINS then you will get a failure when trying to browse networked systems. This is becoming more and more popular by many ISP's because it's one way of avoiding typo-squatting.

------------------------------------------------------

and there it is! my dlink router had the advanced dns option set to on! and that caused the cant browse the network problem!


This could be something to put as a checklist in the first post. something like make sure if you have a router that it dosent forward bad dns queries!

Now it works great for me without fiddeling with the config files :)

for the record on dlink routers you can find the advanced dns option under SETUP->INTERNET->MANUAL INTERNET CONFIG.

just wanted to share this discovery (im new to ubuntu), and maybe this can help someone else :)

---

### Post by dgilloch on 2010-11-27
Hello,

I had a previous post and I've found my own answer. I'm extremely shocked to find out that the cause of this issue was not from Microsoft security essentials, windows firewall, security policy or my share settings (on windows 7). However, I have just uninstalled live essentials ( windows messenger ) and I am now able to connect to windows 7 shares from my Ubuntu 10.10 client. 

I am still shocked that this is causing this problem.

---

### Post by Thinkin on 2010-11-27
I finally got this working, yet I did not have advanced DNS turned on.  In my situation, the:

Use Unicasting : 	  (compatibility for some DHCP Servers) 

was turned on, when unchecked I am back to normal!

---

### Post by dnpate on 2010-11-28
How can I start samba automatically on boot up of ubuntu?
Thanks

---

### Post by dmizer on 2010-11-28
> **dnpate said:**
> How can I start samba automatically on boot up of ubuntu?
Thanks

Make sure that samba is actually installed:
```
sudo apt-get install samba
```

---

### Post by MysticOdin on 2010-11-30
> **WildeBeest said:**
> ```
Try logging on as user guest, and no password.
```

No go. The password dialog just keeps reappearing.

```
If that doesn't work then double check for any firewalls or an anti-virus which may be interfering with the connection. 
```

Turned off all firewalls and anti-virus, Still no go.

Any other ideas?

Uninstall Live-ID sign in assistant, worked for me after about a week of trying everything.

---

### Post by -genin- on 2010-11-30
I got problem with my samba... running on MM...

I share a folder with guest access...
but it cant be accessed from windows...

when I share the folder without guest access, it can be accessed with an authentication prompt...

of course with _smbpasswd -a_

I'm so confused and confusing...

this my smb.conf

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = bonjour

# server string is the equivalent of the NT Description field
   server string = bonjoir

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes
   usershare owner only = no
   disable spoolss = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

changes I've made: 
workgoup and server string
security = user (remove semicolon)
added usershare owner only = no (global section)
added disable spoolss = yes (global section)

need clue... thanks

---

### Post by dmizer on 2010-11-30
> **-genin- said:**
> I got problem with my samba... running on MM...

I share a folder with guest access...
but it cant be accessed from windows...

Sorry, but your problem is the opposite of what this thread is attempting to solve. You'll get better results if you post a request for help in the [Networking and Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section.

---

### Post by dmizer on 2010-12-01
> **dmizer said:**
> I am working on this now, but I don't have a solution for you. If it means anything, I'm having the same problem.

The latest samba updates in Maverick have fixed all of my problems. Everything now works as expected.

---

### Post by DenysT on 2010-12-01
> **dmizer said:**
> The latest samba updates in Maverick have fixed all of my problems. Everything now works as expected.

Didn't do a thing for me. I still get a box asking for user name and password to connect to a domain for my Windows 7 shares. I can access the shares on the Windows 7 PC with XP with no problem so I don't think it has anything to do with the share setup or Windows Live, which isn't on the XP machine but on the Windows 7 machine. At one time I was able to access the shares with Lucid but since I went to Maverick nothing.

---

### Post by dmizer on 2010-12-01
> **DenysT said:**
> Didn't do a thing for me. I still get a box asking for user name and password to connect to a domain for my Windows 7 shares. I can access the shares on the Windows 7 PC with XP with no problem so I don't think it has anything to do with the share setup or Windows Live, which isn't on the XP machine but on the Windows 7 machine. At one time I was able to access the shares with Lucid but since I went to Maverick nothing.

With the new updates, I did have to enter the username of guest. I left the password blank, and selected the "Remember forever" option. On my network, the Windows 7 share folders show up as locked, but the files within them are not locked.

You could also go to: places > connect to server and manually enter the Windows 7 share information.

---

### Post by DenysT on 2010-12-02
Doesn't work either way. Keeps trying to connect to a domain. Only using a workgroup setup. Could uninstall Windows Live I suppose to see if that is the problem but I like the Live Photo Gallery better than the Shotwell Photo Manager they put in Maverick.

---

### Post by dmizer on 2010-12-03
> **DenysT said:**
> Doesn't work either way. Keeps trying to connect to a domain. Only using a workgroup setup. Could uninstall Windows Live I suppose to see if that is the problem but I like the Live Photo Gallery better than the Shotwell Photo Manager they put in Maverick.

If you need "Windows Live", then you might still be able to get connected to the share by using the second link in my sig.

---

### Post by SlugO on 2010-12-11
I'm having serious problems with Samba. I can't access my Windows 7 desktop's shared folders on my Ubuntu 10.04 netbook no matter what I try.

I've tried installing samba and smbfs, configuring Ubuntu's workgroup, installed ntfs-config, removed winbind, (on Win7) allowed lower password encryption and anonymous share access but nothing seems to do the trick.

I can access Ubuntu's shared folders just fine from Windows 7. Even the netbooks's Windows XP can easily access the desktop's folders. But Ubuntu always just keeps asking for a password even though it accepts NOTHING.

I've set up a new (non-admin) account on the desktop and I'm trying to use that username and pass but it never gets accepted, except on XP. Also the desktop's shared folders are on D:\ so they're not locked.

Below is a part of my winbind log if it's useful. Does anyone have any idea what I should do? I'm running out of ideas.

```
[2010/12/11 23:20:32,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/11 23:20:32,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/11 23:20:32,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/11 23:20:32,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/12/11 23:20:32,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2010/12/11 23:20:32,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
[2010/12/11 23:20:32,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/11 23:20:32,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/11 23:20:32,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/11 23:20:32,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/12/11 23:20:32,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2010/12/11 23:20:32,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
```

---

### Post by stevebag on 2010-12-22
Thank you. This solved my problem

---

### Post by jamesringhof on 2010-12-24
THANKS A MILLION. Mate...you are my hero. this worked a treat. I got to  the end of problem 3 and all works well. it was a DNS hosts problem. Now  my ubuntu systems (3) can see each other and the windoze computers (2).  the good part? windoze can not see the ubuntu systems...hahahahaha....!  at least if a virus gets past the poor excuse for security in windoze,  it will not pass it on to the rest of the network.

Man, I am sooooooo happy.

Thanks.

---

### Post by ryu kun on 2010-12-27
I was getting "*Failed to retrieve share list from server*" error when I try to browse Windows workgroups at my office and therefore I was not able to use shared printers. I use Ubuntu 10.10. I followed your "Problem 3" (all parts) HOWTO and my problem is resolved! This was giving me a headache... _Thank you very much!_

---

### Post by RedPenguin on 2011-01-01
Thank you for this post, I was baffled as to why I could no longer browse Windows Shares when it worked perfectly for 2 days with NO changes done at all. (Ubuntu 10.10 with all latest updates).


Then I tried disabling ufw firewall (never configured by me) and everything, nothing worked.

I was even debating a reinstall of Ubuntu because I browse Win shares a fair amount.

Though finally solution 3 fixed it, and not only that made it better and faster than before.

Like instead of wait 5-10 seconds after clicking a computer, instantly almost it comes up.

---

### Post by djps on 2011-01-10
Thanks for posting this. Following the steps through to Problem 3 solved a problem that had me tearing out the last few hairs from my already bald head!

---

### Post by xqz on 2011-01-11
> **MysticOdin said:**
> Uninstall Live-ID sign in assistant, worked for me after about a week of trying everything.

Worked great for me too! Finally!

---

### Post by last1 on 2011-01-20
You know for a zero configuration utility it sure does take some configuration... :p

---

### Post by dmizer on 2011-01-20
> **last1 said:**
> You know for a zero configuration utility it sure does take some configuration... :p

I would hardly call samba a zero configuration utility. Sometimes it is, but (as is noted in this tutorial) even on Windows it often needs a great deal of attention and configuration to work correctly.

---

### Post by last1 on 2011-01-21
Ok but we do have a zero configuration utility built into the distro, right? Isn't Avahi supposed to eliminate the need to mess with configuring stuff when doing something on a LAN?

---

### Post by mickeythemoke on 2011-01-28
I have a Windows XP SP3 desktop pc which can connect to shares on my Ubuntu laptop. However although I could see Windows shares on my desktop, I kept getting **Unable to mount location: Failed to retrieve share list from server** when I tried to connect to my desktop pc shares from my laptop. I finally gained access by following the instructions on this page: [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078). I increased IRPStackSize by 3 and after rebooting, I can access windows shares on my desktop from my Ubuntu 10.10 laptop.

---

### Post by kaustavdm on 2011-01-28
Thanks dmizer,

The solutions you gave for problems #2 and #3 worked for me :) 

Cheers!

---

### Post by dmizer on 2011-01-28
> **mickeythemoke said:**
> I have a Windows XP SP3 desktop pc which can connect to shares on my Ubuntu laptop. However although I could see Windows shares on my desktop, I kept getting **Unable to mount location: Failed to retrieve share list from server** when I tried to connect to my desktop pc shares from my laptop. I finally gained access by following the instructions on this page: [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078). I increased IRPStackSize by 3 and after rebooting, I can access windows shares on my desktop from my Ubuntu 10.10 laptop.

Thank you for this. I will work on adding it to the tutorial. I will also add it to my samba mount tutorial if that's agreeable.

---

### Post by jfz on 2011-02-01
Thank you for the list.

My Samba browsing worked for a while after I upgraded one of my computers to Windows 7, and then suddenly stopped. Both he Win 7 and Ubuntu box changed a lot in the few days before it stopped working, couldn't tell what it was.

Solution for me was in Problem 5. I had something called Windows Live Essentials 2011 installed. Figured the Live Sign-in might be part of that. As soon as I clicked on it to uninstall, Windows reported that the software was not working properly and should be un-installed and re-installed.

Uninstalling it let me browse my shares from the Ubuntu box without problems again. I will pass on the re-installation suggested by Windows.

---

### Post by lisati on 2011-02-06
Now where did the "thanks" feature of the forum disappear to? Oh..... that's right it was removed some time back...... Another grateful customer here, after being referred from [http://ubuntuforums.org/showthread.php?t=1538859](http://ubuntuforums.org/showthread.php?t=1538859)

---

### Post by christosophia on 2011-02-10
greetings

Recently, I have tried to network various computers together.

It works, using Nautilus?
I can browse share folders, but only if they are all manually shared(the subfolders don't apply), and only if it's in a specific location in the "file system".
So, it's kind of annoying in a way.
The main problem is, I have some other hardrives on this computer, and I want complete access to it on the Network, on my laptop etc.
Whenever I try to share it, it says, Unable to mount location.
I cannot directly share the hardrive from "Computer" In Nautilus, but only in Media in File System.
So, it can't mount my hardrives, and thus can't share them on the network.
I have samba installed and all of that, have tried editing in a few lines in the samba conf file.
Why is there an issue with sharing certain places ?
Also, Ubuntu(10.10), seems to have some issues in general with detecting and using hardrives.
Why does the Main Hardrive Ubuntu is installed on called, "File System", and not actually detected as a hardrive?
these things are annoying.

Anyway, can someone show me how to share all of my hardrives on all of my computers.
Is there anyway, since I have the same username and password, to kind of "Remote access" any of the computers on the network... so each computer is controlling each other, depending on purpose.
Like, they all become "One".
This seems like a good idea for pretty much any home network, why don't Ubuntu developers create a GUI or a setup of some sort to establish this, rather than command like stuff and editing conf?
Seems a basic thing.


Thanks in advance.
:guitar:

---

### Post by christosophia on 2011-02-10
I'll summarize my Question/how-to.

I want to be able to share all of my hardrives on the network, but when I try to browse the Hardrives on the network, it says "Unable to mount location" - even though locally, it is mounted.

---

### Post by dmizer on 2011-02-10
> **christosophia said:**
> I'll summarize my Question/how-to.

I want to be able to share all of my hardrives on the network, but when I try to browse the Hardrives on the network, it says "Unable to mount location" - even though locally, it is mounted.

Your question is the opposite of what this tutorial attempts to solve. I suggest you open a new thread for help with your problem.

That said, you'll probably have to create hard mounts in /etc/fstab for all of your hard drives before you can share them via Nautilus.

---

### Post by billcat on 2011-02-17
Many, many thanks, dmizer :)

Your steps 1 thru 3 did the trick for my shares running both Ubuntu and Windows 7 in 64-bit.  My network is now complete.  You're definitely the man!

---

### Post by klompen on 2011-02-19
I just want to add my thanks for putting together such a comprehensive and easily followed procedure. I get very frustrated when I get Linux installed and then can't move forward because of what seem like small things like this that really should "just work". It took me a long time to hit on the right search phrase to find this, but it was worth it because it had all the information that I needed.

In my case, I have a home network of Windows XP & 7 and Ubuntu 7.10, 10.04 LTS & 10.10. Everything had "just worked" when I installed 10.04, but in hindsight I realize that I didn't have Windows 7 in the mix. When I installed 10.10 I discovered that I could not browse the workgroup with 10.04 or 10.10 even thought 10.04 had worked previously.

For 10.04 I had to do the steps in Problem 2 - part 1 & 2 and Problem 3 - part 1. For 10.10 I had to do all of these plus Problem 3 - part 2.

Thanks again for this resource. You have no idea how much it is appreciated and how much frustration this has saved!

---

### Post by CDL-WarChilde on 2011-02-19
Thanks!

redirected from google search, had to do all the parts for 10.10

I should mention that I had performed a minimal install of Ubuntu 10.10, so it didn't come with smb installed.  This tutorial was easy to follow and within 5 minutes I was browsing my XP machine.

---

### Post by John Bennett on 2011-02-19
> **dmizer said:**
> Change “[COLOR="Red"]WORKGROUP[/COLOR]” in “workgroup = [COLOR="Red"]WORKGROUP[/COLOR]” to match your Windows workgroup.

...add netbios name = [COLOR="Red"]computer-name[/COLOR] just below "workgroup = WORKGROUP".

This worked for me as long as Uncomplicated Fire Wall (UFW) is *not* running.

When UFW is running, I can see my Widows shares, but cannot browse them.  I would rather not poke holes in the firewall.  So, as described in this thread "[Firewall Blocked for Samba]("http://ubuntuforums.org/showthread.php?t=1225549&page=3")" I edited /etc/default/ufw to include;

```
# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns" 
```

I still cannot browse my Windows XP shares.  From Ubuntu versions 6 through 9 this was never a problem.  All Ubuntu 10 versions seem to have this problem.

MSI L1300 Netbook running Ubuntu 10.10 Maverick
Attempting to browse Windows XP workgroup shares.

Any help appreciated.

---

### Post by travlemon on 2011-02-21
> **John Bennett said:**
> This worked for me as long as Uncomplicated Fire Wall (UFW) is *not* running.

When UFW is running, I can see my Widows shares, but cannot browse them.  I would rather not poke holes in the firewall.  So, as described in this thread "[Firewall Blocked for Samba]("http://ubuntuforums.org/showthread.php?t=1225549&page=3")" I edited /etc/default/ufw to include;

```
# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns" 
```I still cannot browse my Windows XP shares.  From Ubuntu versions 6 through 9 this was never a problem.  All Ubuntu 10 versions seem to have this problem.

MSI L1300 Netbook running Ubuntu 10.10 Maverick
Attempting to browse Windows XP workgroup shares.

Any help appreciated.

I agree with John Bennett.  I first started testing out with Ubuntu when 9.04 was out, and this wasn't an issue at all.  I was able to browse Windows shares flawlessly, including adding printers via Samba.  I'm surprised the Ubuntu team hasn't looked into tightening that configuration for out of the box Windows networking capabilities.

Also, just wanted to add a piece of information to this very long thread. I just set up set up 3 machines with Linux Mint (an Ubuntu derivative),  and this fix works almost flawlessly every time.  However,  I did notice that experimenting can throw off your configuration, and this may effect all of your Ubuntu machines in the LAN.

For example, I decided to put **wins** before **lmhosts** in the **smb.conf** file.  This knocked out my Samba browsing on every Mint machine that I have running.  I simply edited **smb.conf** back to the way the fix instructs it should be, and restarted the samba service with **sudo service smbd restart**.  After that, I refreshed the network browser on the other machines, and it was working fine.

To make a long story short, it's definitely possible that one bad config may knock out the whole group of Ubuntu machines.  So, always verify you've followed the instructions of the original post to perfection.  I've never had it fail on me, except when I do things outside of its suggestions. I've never had to adjust any firewall settings either, just edit **smb.conf** and **nsswitch.conf**.  

Hope this sheds light for newcomers!

---

### Post by dmizer on 2011-02-21
> **John Bennett said:**
> This worked for me as long as Uncomplicated Fire Wall (UFW) is *not* running.

Please read this section carefully:
> **dmizer said:**
> [SIZE="4"]**Problem 4:**[/SIZE]
Firewalls block samba browsing. If you're sharing files over samba, that probably means you're on a LAN with only indirect (usually via a firewalled gateway/router) access to the Internet. This means that you probably don't need a firewall at all. If you think you DO need a firewall, you should really think about how wise it is to poke holes in it to facilitate samba file sharing.
Windows file sharing is one of the most common attack vectors, so if you poke holes in your firewall for samba browsing, you're essentially removing any positive effect your firewall has.

Is there a reason you need a firewall?

---

### Post by gdea73 on 2011-03-02
Hi, I'm having problems with samba sharing...

Two days ago everything was fine. I could browse shares on my Windows PC gdea73-pc-1 (netshare and www) just fine and edit files. A long time ago I noticed that from a Windows PC I had to enter my linux user/password to view netshare on THIS LOCAL machine (Ubuntu). I have a user account g73net with no password on this local machine, so I used smbpasswd -a g73net to add it to my share. I also created smbusers in /etc/samba and added this:

gdea73 = "gdea73"
g73net = "g73net"

Now, I always get "failed to mount Windows share" when trying to access *any* windows share on the network besides the Netshare on the local PC. I tried deleting smbusers, and i also typed smbpasswd -x g73net. I even deleted user g73net. Still won't work...

what do I do?

---

### Post by gdea73 on 2011-03-02
wow, different problem
 I can access shares via IP address but I can't via machine name. I didn't change anything in my smb.conf and it was working 2 days ago ...

---

### Post by mapsegarra on 2011-03-03
Hi all,

After searching, digging and testing I have no more ideas to try. I explain:

 I'm trying to setup a small local File Server (Ubuntu Server 10.04 and Samba 3.4.7) After looking at the forums about the configurations of Samba and Windows I managed to get all the network running at 99%. The remaining 1% is that the connection to Samba from Windows 7 is performed intermittently.

 XP pcs have no problem accessing, mount drives, read and write to the Samba server. It seemed that Windows 7, after edit various, either. But after a few minutes (sometimes seconds) Windows 7 is no access to the server more, and after a few minutes reconnects.

 The access is done with user authentication and permissions are handled in Ubuntu

 I record somo traffic with Wireshark, but I'm not have enogh level to draw conclusions. If it is necessary I can post too.

 Best Regards!

 Ubuntu Server 4.10 + Samba:  185.0.200.151
 PC Windows 7                         185.0.200.56
[B]
smb.conf[/B]
```

[global]
    workgroup = NPG
    server string = SERV-FICHEROS
    netbios name = SERV-FICHEROS
    wins support = no
    dns proxy = no
    name resolve order = lmhosts host wins bcast
    interfaces = 127.0.0.0/8 eth0
;    bind interfaces only = yes
    deadtime = 0

    printcap name = /dev/null
    load printers = no
    printcap cache time = 0
    show add printer wizard = no
#### Win7 Support ####
    client ntlmv2 auth = yes    
    client lanman auth = yes
    lanman auth = yes
    ntlm auth = yes

#### Debugging/Accounting ####
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
####### Authentication #######
    security = user
    encrypt passwords = yes
    passdb backend = tdbsam
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user

############ Misc ############
#    SO_RCVBUF=8192 SO_SNDBUF=8192
    socket options = TCP_NODELAY

# Maximum number of usershare. 0 (default) means that usershare is disabled.
    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

############ Shares ############
[FICHEROS-NPG]
    path = /FICHEROS-NPG
    comment = Servidor Ficheros
    hide unreadable = yes
    read only = no
    browseable = yes
#    guest ok = yes
#    create mask = 0775
#    directory mask = 077

```**pc win7 (samba log)**

```

  ixd_miguel (185.0.200.56) connect to service FICHEROS-NPG initially as user Manuel (uid=1007, gid=1011) (pid 2180)
[2011/03/01 11:26:30,  1] smbd/service.c:1063(make_connection_snum)
  ixd_miguel (185.0.200.56) connect to service FICHEROS-NPG initially as user Manuel (uid=1007, gid=1011) (pid 2185)
[2011/03/01 11:26:42,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:26:42,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:26:42,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 11:29:22,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:29:22,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:29:22,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 11:31:30,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 11:31:30,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 11:31:30,  1] smbd/service.c:1240(close_cnum)
  ixd_miguel (185.0.200.56) closed connection to service FICHEROS-NPG
[2011/03/01 12:08:35,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 12:08:35,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2011/03/01 12:41:22,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2011/03/01 12:41:22,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

```

---

### Post by dmizer on 2011-03-06
> **gdea73 said:**
> wow, different problem
 I can access shares via IP address but I can't via machine name. I didn't change anything in my smb.conf and it was working 2 days ago ...
Just follow the howto in the first page of this thread and you should be fine.

> **mapsegarra said:**
> I'm trying to setup a small local File Server (Ubuntu Server 10.04 and Samba 3.4.7) After looking at the forums about the configurations of Samba and Windows I managed to get all the network running at 99%. The remaining 1% is that the connection to Samba from Windows 7 is performed intermittently.

Your problem is the opposite of what this thread tries to solve. You'll be better off posting a separate thread. You can also have a look at the 1st link in my sig.

---

### Post by kyke01 on 2011-03-11
Hi Dmizer!!,
great tutorial thanks, but unfortunately didn't work for me.
Let me explain what I did, first of all, Samba was working perfectly with ubuntu Hardy-Heron version, now I updated to 10.04 and from windows doesn't "see" the linux machine. I can access through \\IPadress\share_folder (this means samba works fine).
But I can't browse through windows explorer. I've tried all the options that you recommend but no one works.
From ubuntu I get the error message "Unable to mount location: Failed to retrieve share list from server" Iread that it's a firewall problem, but this doesn't bother to me.
I attach my smb.conf file.

Thanks in advance
P.D. Sorry for my english

Regards!!
Kyke

---

### Post by tipiglen on 2011-03-25
Hi Dmizer,

Thanks again for the 'permanent share mount' tutorial - working perfectly.

Everything else was working perfectly until yesterday afternoon when I booted up win7 to use IE to try and change privacy settings in (of all things) facebook.  (Firefox seemed unable to open the privacy tab) IE did give me access, but little joy, but that's all by the by...

When I returned to Ubuntu (mint 9), I could no longer browse my LAN with nautilus -  I get the windows network icon, but clicking on it gives the 'Unable to mount location - Failed to retrieve share list from server' error.   I thought (sudo) restart smbd - no effect, restart nmbd - no effect.  samba "samba is not installed" - WHAT?  

Re-installed samba (samba4) restart samba gives a bunch of errors and I remembered 4 doing that before, so removed 4 and left 3 in place.

I've tried all your suggested smb.conf edits with no joy.  

When I try and install winbind it hangs at 'starting winbindd' apparently forever - bombing out leaves stuff locked and requires a reboot and dpkg configure.  Same with either cli or synaptic.  I have removed it at present, but will attempt a new install...

Samba is working fine except through nautilus (I can see (and open) shares via firefox, either by ip address or netbios name).  I've gone back to win7 and increased the stack as suggested, all to no avail.

Samba log ```
[Tue Feb 22 15:59:54 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [NT_STATUS_CANT_ACCESS_DOMAIN_INFO]
[Wed Feb 23 14:44:39 2011 GMT, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[Wed Feb 23 14:44:39 2011 GMT, 0 smbd/pidfile.c:94:pidfile_create()]
ERROR: samba is already running. File /var/run/samba.pid exists and process id 1350 is running.
[Wed Feb 23 17:17:42 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 1360 on SIGTERM
[Wed Feb 23 17:17:42 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 1368 on SIGTERM
[Wed Feb 23 17:17:42 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 1362 on SIGTERM
[Wed Feb 23 17:17:42 2011 GMT, 0 smbd/server.c:112:sig_term()]
SIGTERM: killing children
[Wed Feb 23 17:17:42 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 1350 on SIGTERM
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/server.c:366:binary_smbd_main()]
samba: using 'standard' process model
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [ldap_server: no LDAP server required in standalone configuration]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kdc: no KDC required in standalone configuration]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [cldap_server: no CLDAP server required in standalone configuration]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [dreplsrv: no DSDB replication required in standalone configuration]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_stream.c:332:stream_setup_socket()]
Failed to listen on 0.0.0.0:445 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [Failed to startup smb server task]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kccsrv: no KCC required in standalone configuration]
[Thu Mar 24 17:15:13 2011 GMT, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [NT_STATUS_CANT_ACCESS_DOMAIN_INFO]
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 2383 on SIGTERM
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 2376 on SIGTERM
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 2377 on SIGTERM
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 2375 on SIGTERM
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:112:sig_term()]
SIGTERM: killing children
[Thu Mar 24 17:17:25 2011 GMT, 0 smbd/server.c:117:sig_term()]
Exiting pid 2372 on SIGTERM
ed@ed-asus:/var/log/samba$ 
```

Any ideas?

Regards
ed
[http://tipiglen.co.uk/loveandpeace3.gif](http://tipiglen.co.uk/loveandpeace3.gif)

---

### Post by tipiglen on 2011-03-25
Hi again,

Winbind installed without problems this time.

Nautilus now shows icon for windows network and icons for ALL my own shares (on this box), but clicking on any of them still gets the same old error.   GAH! log.winbindd-idmap:
```
[2011/03/25 15:23:50,  1] winbindd/idmap.c:438(idmap_init_passdb_domain)
  Could not init passdb idmap domain
[2011/03/25 15:23:50,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2011/03/25 15:23:50,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2011/03/25 15:23:50,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
[2011/03/25 15:25:36,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2011/03/25 15:25:36,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2011/03/25 15:25:36,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2011/03/25 15:25:36,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2011/03/25 15:25:36,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2011/03/25 15:25:36,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
```

---

### Post by kennardly on 2011-03-27
Thank you very much!!! I followed you guide and I'm finally working!

---

### Post by phane on 2011-03-27
Using a Windows 7 x64 home premium server and have several computers running Ubuntu 10.10 and a couple running Windows 7, one running Vista, a PS3, and a Xoom tablet.  All of these computers were able to connect to the windows shares without problem.

Not sure exactly when, but a week or so back, all was working and now nothing but the Windows computers and my PS3 can connect.  None of my Ubuntu computers or my Xoom can connect to any shares.

I've followed the entire tutorial on the first post and no luck (I had already done most of it anyway).  All of my Ubuntu computers see nothing after I go 'Places/Network/Windows Network'.  Trying to connect directly using hostname or IP doesn't work.  My Xoom sees the computer when using ES File Explorer but when I click on the server it sits forever at 'Loading: Getting file list...'.

My suspicion is that since the Xoom is also effected, that it's likely a Windows 7 patch that caused my problem and not a Ubuntu issue.  Since I'm pretty sure I used my Xoom to connect a week or two ago, I'd guess it's something got released over the last two weeks.

Edit: Forgot to mention that all Windows computers and the PS3 connect without issue.

---

### Post by gordintoronto on 2011-03-27
Phane: no change to the router?

Windows 7 Service Pack 1 was released recently, has it been installed?

---

### Post by phane on 2011-03-29
I had service pack 1 installed the day it came out and my shares were still working.  Some of the computers are connecting via LAN through a switch without any router between them, others are connecting wirelessly through a Linksys E3000 with the firewall, NAT, and DHCP all disabled so it's basically being used as a WAP.  None of the clients, wired or wireless, can connect to the windows shares through Ubuntu or Android.  I have an old laptop with a broken LCD using IP Cop that's my primary firewall / router, but it's bypassed through the switch for any LAN traffic.  Only change to that recently was that I added the net-traffic add-on to IP Cop to see how much I should worry about the supposed wave of bandwidth caps that are coming.

```
Internet <--> Ooma <--> IP Cop <--> Switch <--> LAN
                                       ^
                                       |
                                       v
                                     E3000 <--> WLAN
```

Edit: Actually, android can connect now (for w/e reason), and (spontaneously) now I can manually connect using the Connect to Server function, but I still can't browse to it.

---

### Post by dmizer on 2011-03-29
> **phane said:**
> Edit: Actually, android can connect now (for w/e reason), and (spontaneously) now I can manually connect using the Connect to Server function, but I still can't browse to it.

Double check all your computers (particularly the Windows computers) for interfering firewalls.

---

### Post by JeffersonDavis33 on 2011-03-30
Ok,  I've tried steps one 1-3 from the first post.  As for step 4, i dont use a firewall, Step 5,  this is a server install and I'm not interested in browsing windows shares.  

I am running 10.04.2 server, a fresh install, and  using webmin to administer.  

My smb.conf is attached.  

The Win7 and XP machines on the network can see the samba shares and browse the sub directories, but they are unable to write to these shares.  (No Permission etc ....) 

dmizer has provided the most usefull posts regarding samba shares, and I was able to use this same post a few years ago to get this working, but now I'm stumped.  

Thanks for your dedication to helping us noobs.

---

### Post by dmizer on 2011-03-30
> **JeffersonDavis33 said:**
> Ok,  I've tried steps one 1-3 from the first post.  As for step 4, i dont use a firewall, Step 5,  this is a server install and I'm not interested in browsing windows shares.  

I am running 10.04.2 server, a fresh install, and  using webmin to administer.  

My smb.conf is attached.  

The Win7 and XP machines on the network can see the samba shares and browse the sub directories, but they are unable to write to these shares.  (No Permission etc ....) 

dmizer has provided the most usefull posts regarding samba shares, and I was able to use this same post a few years ago to get this working, but now I'm stumped.  

Thanks for your dedication to helping us noobs.

What you are trying to do is the exact opposite of what this howto attempts to solve.

First of all, you should double check to make sure that the samba package is actually (for real) installed [sudo apt-get install samba]. Since Ubuntu comes with some samba functionality out of the box, it may look like it's actually installed when it's not.

Secondly, if you are creating a dedicated file server you should probably avoid hosting a share in your user's directory as that could complicate permission settings.

Thirdly, you should have a look at the 1st link in my sig.

Good luck!

---

### Post by JeffersonDavis33 on 2011-03-31
Thanks for the help.  You are correct, I am in the wrong thread.  I spend so much time reading your threads about Samba issues I got lost and confused.  

I will start over with the first link in your sig and see where I end up then.  

Do recommend any particular place for the samba shares to avoid unnecessary permissions?

Thanks Again

(now lets see if I can RDP to one of my machines at home then SSH to the server........having a job really gets in the way of my hobbies.....)

---

### Post by JeffersonDavis33 on 2011-03-31
IT Works!.   I started over like I mentioned above and it works.

One of my problems was that I was over-thinking the whole Logical Volume  and how/where to mount said volumes,  with each mount being its own share etc etc etc.

That said, how is the size of the shares that I just created managed?  Do they use all the avail space on the Volume Group, or do I indeed need to mount other stuff??

Thanks Again......  Wheeee!  it works!

---

### Post by dmizer on 2011-04-01
> **JeffersonDavis33 said:**
> That said, how is the size of the shares that I just created managed?  Do they use all the avail space on the Volume Group, or do I indeed need to mount other stuff??

If you need to manage share size based on user accounts, you may want to look into ldap which will make things much easier to administrate.

There are some great ebox (zentyal) plugins for web based administration. Zentyal is lightyears beyond webmin, so I highly suggest looking into it and dumping webmin.

---

### Post by MATilley on 2011-04-02
Hello,

I currently have some windows (Win7 Ultimate 64-bit) shares automounted to my Ubuntu 10.04 laptop whenever I am on my home wireless network. I have this functionality set up using autofs/CIFS and it works well, except for one issue:

The directory listings for the mounted windows shares are incomplete, i.e. when listing the directories on the linux machine, it only lists a fraction of what is available in the actual share. One directory returns 28 of 51 files present, for example, and another 33 of 60. 

I have disabled Homegroup on the Win7 box and have followed steps in both this guide and the CIFS guide. Any ideas? 

Thank you.

---

### Post by dmizer on 2011-04-02
> **MATilley said:**
> Hello,

I currently have some windows (Win7 Ultimate 64-bit) shares automounted to my Ubuntu 10.04 laptop whenever I am on my home wireless network. I have this functionality set up using autofs/CIFS and it works well, except for one issue:

The directory listings for the mounted windows shares are incomplete, i.e. when listing the directories on the linux machine, it only lists a fraction of what is available in the actual share. One directory returns 28 of 51 files present, for example, and another 33 of 60. 

I have disabled Homegroup on the Win7 box and have followed steps in both this guide and the CIFS guide. Any ideas? 

Thank you.
Since some directories work, and some do not, this is a directory permission problem on the Windows computer. I suggest you carefully check the folder permissions on your Windows computer. Compare directories that work to directories that do not work.

Also note that if you are trying to share your entire C: hard drive, this will be expected behavior.

---

### Post by MATilley on 2011-04-02
> **dmizer said:**
> Since some directories work, and some do not, this is a directory permission problem on the Windows computer. I suggest you carefully check the folder permissions on your Windows computer. Compare directories that work to directories that do not work.

Also note that if you are trying to share your entire C: hard drive, this will be expected behavior.

Thanks for the comment, DMizer.

I'm sorry if I was not clear -- all the directories I automount with CIFS do work and are accessible, but only a fraction of the files within are shown when browsing the shares from the Ubuntu machine. 

For example, if I have a share, MyShare1, from windows it looks like the following:

```
 
D:\MyShare1>dir
file1
file2
file3
file4
file5
file6

```

But when browsing the CIFS mounted share on the Ubuntu machine, I see the following:

```

me@laptop:/net/MyShare1$ ls 
file1
file3
file4

```

In other words, an incomplete set of files is returned when browsing the share from the Ubuntu machine. However, I *can* access the files that are not listed, if I know they are there. 

Also, this is not from the c: drive, all shared folders are on an additional drive (marked d:) I have installed.

Is that more clear?

Thanks!

---

### Post by dmizer on 2011-04-02
> **MATilley said:**
> Is that more clear?

Either way (files or directories), if some of the files can be viewed and some cannot, the problem is with permissions on the Windows machine, not with the mount.

If the problem was on the Linux side of things, you would not be able to view any files at all.

That said, out of curiosity does this command list all of the files?
```
sudo ls -a /net/MyShare1
```

---

### Post by MATilley on 2011-04-02
> **dmizer said:**
> Either way (files or directories), if some of the files can be viewed and some cannot, the problem is with permissions on the Windows machine, not with the mount.

If the problem was on the Linux side of things, you would not be able to view any files at all.

That said, out of curiosity does this command list all of the files?
```
sudo ls -a /net/MyShare1
```

I see; I was afraid it might be on the Windows side of the equation. 

The sudo-ed line above does nothing more than a non-sudo-ed command.

I did hunt down something interesting on the net involving inodes:

If I add the following option - noserverino - to the CIFS mount line in my auto.foo file, more files become visible but not every file, still.

That could lead the investigation in the right direction but it seems to be getting pretty complex with regards to filesystem organization.

---

### Post by jamesisin on 2011-04-02
Approximately how many items per directory are we discussing?

---

### Post by MATilley on 2011-04-02
> **jamesisin said:**
> Approximately how many items per directory are we discussing?

From my first post above:

```

One directory returns 28 of 51 files present, for example, and another 33 of 60. 

```

---

### Post by jamesisin on 2011-04-03
I can access directories with hundreds of items in various configurations.  Can you link to the article you found which discusses noserverino?

(My inclination, like dmizer's, has been that this was a permissions issue on the server machine.  But the fact that noserverino changed the number of items displayed/accessible intrigues me.)

---

### Post by MATilley on 2011-04-03
> **jamesisin said:**
> I can access directories with hundreds of items in various configurations.  Can you link to the article you found which discusses noserverino?

(My inclination, like dmizer's, has been that this was a permissions issue on the server machine.  But the fact that noserverino changed the number of items displayed/accessible intrigues me.)

Unfortunately what I found wasn't an explanatory, technical article. In my frenetic search for a solution, I came across this bug entry:

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466)

It was a one-off kind of attempt to work around the problem, but it's not the same issue, apparently.

---

### Post by jamesisin on 2011-04-03
Have you tried forcing the permissions to inherit downward on the Windows box?

---

### Post by MATilley on 2011-04-03
> **jamesisin said:**
> Have you tried forcing the permissions to inherit downward on the Windows box?

Forgive my ignorance, but I'm not sure quite how I would do that, if I am not already. Here is a sample line from my autofs.foo script:

```

MyShare1    -fstype=cifs,username=SERVER/myname,password=mypass,iocharset=utf8,file_mode=0777,dir_mode=0777    ://SERVER/MyShare1/

```

And thanks to the both of you, dmizer and jamesisin, for your attention and interest in solving the issue.

---

### Post by jamesisin on 2011-04-03
I don't have a Windows box in front of me but it's something like this:

[LIST=1]
[*]Open the Preferences dialog for the root folder of the share.
[*]Move to the Permissions tab.
[*]Click on the Advanced button.
[*]Click on the button which talks about propegating the permissions to all child objects.
[*]Ok your way back out.
[/LIST]

Let me know if that's totally useless and I'll get on a Windows machine.

---

### Post by MATilley on 2011-04-03
> **jamesisin said:**
> I don't have a Windows box in front of me but it's something like this:

[LIST=1]
[*]Open the Preferences dialog for the root folder of the share.
[*]Move to the Permissions tab.
[*]Click on the Advanced button.
[*]Click on the button which talks about propegating the permissions to all child objects.
[*]Ok your way back out.
[/LIST]

Let me know if that's totally useless and I'll get on a Windows machine.

That was not totally useless, though on Windows 7 it was under the Security tab:

[list=1]
[*]Open folder properties.
[*]Click on Security tab.
[*]Click on Advanced button.
[*]Highlight appropriate user account and click 'Change Permissions' button.
[*]Check the box of 'Replace all child objects with inheritable permissions from this object'
[/list]

Unfortunately, it didn't make any difference in browsing from the linux machine.

---

### Post by phane on 2011-04-03
> **dmizer said:**
> Double check all your computers (particularly the Windows computers) for interfering firewalls.

I have no third party firewall software running on my LAN and I tried disabling the Windows Firewall on the server altogether, no luck.  Ubuntu is reporting it's firewall as disabled (as per the 1st post instructions).  If my windows computer were firewalling samba connections, android wouldn't be able to connect and I wouldn't be able to ever manually connect to the shares either.

Now, Ubuntu won't even manually connect.

Correction: Ubuntu will manually connect using IP address instead of Hostname.  After that is mounted, it'll mount properly by hostname as well (but I still can't browse to it under Windows Network).  If I unmount everything from the server, trying to connect by hostname fails again.  The error I get is:

Cannot display location "smb://phane@a64-3200/shared/"
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

The error pops up IMMEDIATELY after I attempt to connect, so I don't think it's an actual timeout.

FYI, the hostname for this computer is listed under hosts under my IP Cop router/firewall, so Linux can see it without using WINS, and I can ping using the hostname just fine.

---

### Post by dmizer on 2011-04-03
> **phane said:**
> FYI, the hostname for this computer is listed under hosts under my IP Cop router/firewall, so Linux can see it without using WINS, and I can ping using the hostname just fine.
From everything I've read, including the following excerpt from [the samba manual]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2580798"), you cannot use samba with DNS unless you have an AD controller. This means that even though you can ping by hostname as a result of a correctly working DNS server, you will still be unable to browse samba shares by name unless you use NetBIOS.
[quote=samba docs]Use of raw SMB over TCP/IP (No NetBIOS layer) can be done only with Active Directory domains. Samba is not an Active Directory domain controller: ergo, it is not possible to run Samba as a domain controller and at the same time not use NetBIOS. Where Samba is used as an Active Directory domain member server (DMS) it is possible to configure Samba to not use NetBIOS over TCP/IP. A Samba DMS can integrate fully into an Active Directory domain, however, if NetBIOS over TCP/IP is disabled, it is necessary to manually create appropriate DNS entries for the Samba DMS because they will not be automatically generated either by Samba, or by the ADS environment. [/quote]

---

### Post by phane on 2011-04-04
> **dmizer said:**
> From everything I've read, including the following excerpt from [the samba manual]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2580798"), you cannot use samba with DNS unless you have an AD controller. This means that even though you can ping by hostname as a result of a correctly working DNS server, you will still be unable to browse samba shares by name unless you use NetBIOS.

I've done it before... it was working before... as I said, it was (now) 3 weeks ago that it all stopped working.  I'm not sure if IP Cop functions as an AD controller, it is Linux and has a Hosts file in which my server is listed and my server has a fixed IP address.  Regardless, it should let me browse to it through Windows Network as it did even before I had IP Cop as a firewall and DNS/DHCP server.  Connecting to a samba share using hostname functionality isn't something I'm looking to accomplish as a goal, it's merely something I'm using to describe the issues I'm having in hopes of being able to browse to it.  I have several linux computers and several windows shares (including a printer) and doing symlinks to them all would be laborious to say the least.

---

### Post by jamesisin on 2011-04-04
It's probably your router.  Try rebooting your router.  Which firmware are you running there?

---

### Post by phane on 2011-04-04
> **jamesisin said:**
> It's probably your router.  Try rebooting your router.  Which firmware are you running there?

Facepalm.... :(

Not that I'm trying to stray people away, this is a solution I'd give to a lot of people myself, however I've mentioned a number of times that I'm running IP Cop as my router.  There is no firmware to download.  It's running on a 1ghz laptop with a broken LCD.  For the hell of it, since I can't remember rebooting it, I went ahead and did just that.  No result.

A tracert from windows shows that I go direct to the server without touching the firewall/router (iow I go through the switch as drawn previously), but traceroute in linux just times out... any idea if that's related?

---

### Post by jamesisin on 2011-04-04
That's normal behavior, typically.  I don't know specifically about IPCop, but sometimes these issues can be traced back to the router being finicky.  Any chance you can connect directly to the server via a cross-over cable or even a dumb hub?

---

### Post by phane on 2011-04-04
```
Internet <--> Ooma <--> IP Cop <--> Switch <--> LAN
                                       ^
                                       |
                                       v
                                     E3000 <--> WLAN
```

Already doing that.  I tried unplugging IP Cop from the switch to be certain, no real change.  I could connect manually using hostname this time (interesting, considering ping to hostname no longer works with IP Cop unplugged), but no other change.

---

### Post by jamesisin on 2011-04-04
You should probably post this as its own thread (complete with the items above discussed) so we can try to get you help from the wider community.  Link here so anyone interested can follow it.

---

### Post by llogg on 2011-04-04
> **gdea73 said:**
> wow, different problem
 I can access shares via IP address but I can't via machine name. I didn't change anything in my smb.conf and it was working 2 days ago ...This is my problem.  I have a Vista machine connected to a router that also has a Linux Mint machine connected to it.  A printer is connected to the Mint computer.  The Mint computer can access all the files I want from the Vista machine.  Vista can print to the machine connected to the Mint box.  Vista can access the Mint machine's files/folders via IP address or as a mapped network drive, but cannot recognize the Mint machine on the network.  It sees a device but only calls it "unknown device".  I've done all the steps on the first page.  Any further suggestions on how to resolve this?

---

### Post by MATilley on 2011-04-07
Adding to my investigation, looking into dmesg, I see the following every time that I attempt to list the windows share contents from the linux box:

```

CIFS VFS: Send error in FindClose = -9

```


I've been through every permutation of permissions and security on the windows machine, and nothing changes the share state. The only change I can make is using the 'noserverino' option in the mount syntax.

This is thoroughly frustrating.

---

### Post by MarkieB on 2011-04-12
no longer participating in ubuntuforums.org

---

### Post by LADmaticCA on 2011-04-28
I've got a bit to add. I was having share browsing issues too (failed to retrieve share list from server). I found my solution in adding the samba server, and any other machines in the network, to the /etc/hosts file of the client. IP then hostname:

example
192.168.1.xxx nattyMachine

I happened to come across this suggestion on a fedora forum, just thought it should be added to this howto. I have an all linux network, NFS works very well but I find samba faster at times.

---

### Post by sierra8804 on 2011-04-29
I have followed all the suggestions to the letter but I don't see the Samba server on the Microsoft Windows Network. I only see the other windows boxes. I can share files by using the Run [\\sambabox]("file://\\sambabox") or mapping the drive using [\\sambabox\share]("file://\\sambabox\share") but I would like to be able to see the samba box in the list.
Is it because the sambox is on a static IP of 65.x.x.x and the windows machines are on the 192.168.x.x network? How can I get around that problem?

---

### Post by seth3d on 2011-05-08
> **MATilley said:**
> This is thoroughly frustrating.

I'm with you, I'm having this same issue. The FindClose is a kernel error when listing folder contents. I found old references to this error here (not a fix for our issue I think):

[http://lists.samba.org/archive/linux-cifs-client/2004-February/000078.html](http://lists.samba.org/archive/linux-cifs-client/2004-February/000078.html)

And then of course I found your post.. I'm running linux-2.6.32-31 here. I don't know if downgrading would correct the issue, or if that would even be possible now.

Are you trying to mount from a Windows 7 box?

---

### Post by gordintoronto on 2011-05-08
> **seth3d said:**
> ...And then of course I found your post.. I'm running linux-2.6.32-31 here. I don't know if downgrading would correct the issue, or if that would even be possible now.


I'm using that kernel on my laptop. No problem sharing a folder, or accessing other Windows and Linux shares.

---

### Post by seth3d on 2011-05-08
> **gordintoronto said:**
> No problem sharing a folder, or accessing other Windows and Linux shares.

It's not the mounting that's the problem, it's accessing all of the files which is an issue. Other than files not being available it works perfectly. My issue is occurring in a folder with over 1,000 files in many sub-folders.

Try mounting a large file share, browse or list all of the directories with 'ls -laR', and then run the following to see if you are really *not* having any issues. 

```
grep FindClose /var/log/kern.log
```

If it comes back without anything you can proudly say you are awesome with much awesomeness and you don't know what our problem is.

---

### Post by seth3d on 2011-05-09
Update: I've upgrade to 10.10 Maverick with kernel 2.6.35-28 and I'm still getting the error.

```
May  9 12:17:03 ubuntu-desktop kernel: [  212.494035] CIFS VFS: Send error in [COLOR="Red"]FindClose[/COLOR] = -9
```

I'm currently upgrading to 11.04 to see if I can upgrade past the issue...

---

### Post by seth3d on 2011-05-09
Still getting the FindClose error with Ubuntu 11.04. 

To refresh on the issue, I'm mounting a rather large Windows 7 file share with CIFS. I have gone through the steps in the beginning of the post.

```

**media@ubuntu-desktop:~$ grep FindClose /var/log/kern.log**
(CLIP)
May  9 14:17:03 ubuntu-desktop kernel: [  578.128458] CIFS VFS: Send error in [COLOR="Red"]FindClose[/COLOR] = -9
**media@ubuntu-desktop:~$ cat /proc/version**
Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011
```

Any help?

---

### Post by seth3d on 2011-05-09
OK, I got a few more files to show up by removing various brackets and braces such as {}[](). I also replaced all spaces with underscores. I'm now wondering if there are hidden characters in some of the file names which would still be causing issues?

I've also split up the file share into several directories, this doesn't have any effect. I was hoping listing fewer files would help.

---

### Post by seth3d on 2011-05-09
I can truncate the file names and get a few more to show up. Rather if you prefer, more files are available with smaller file names. I'm counting the characters in the directories having the issue and am finding a character limit of about 690 characters. The second time I ran it is after I increased a file's name length and it dropped a file from the mount point.

```
**media@ubuntu-desktop:~$ ls /the/directory/mounted/to | wc -m**
689
**media@ubuntu-desktop:~$ ls /the/directory/mounted/to | wc -m**
684
```

Should I submit a bug report for this, and as a CIFS or kernel? I think I'm at the end of how much I can do, and compiling a debugging kernel isn't something I'm prepared to do.

---

### Post by seth3d on 2011-05-09
I opened a bug report for the CIFS Send error in FindClose issue here:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/780251](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/780251)

---

### Post by Genicode on 2011-05-10
Hello mate,

Look here:
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/09bd78bf-06c3-4c85-91f7-41bc12c647bb](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/09bd78bf-06c3-4c85-91f7-41bc12c647bb)

After uninstall Avast everything is ok.
I was trying to resolve this problem for last few days ;)

Best Regards.

---

### Post by seth3d on 2011-05-10
> **Genicode said:**
> Hello mate,

Look here:
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/09bd78bf-06c3-4c85-91f7-41bc12c647bb](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/09bd78bf-06c3-4c85-91f7-41bc12c647bb)

After uninstall Avast everything is ok.
I was trying to resolve this problem for last few days ;)

Best Regards.

Brilliant! It's working 100% for me now after uninstalling Avast. Many, many thanks for this, I've actually been looking at this issue for months.

Moving onward...

---

### Post by gordintoronto on 2011-05-10
> **seth3d said:**
> It's not the mounting that's the problem, it's accessing all of the files which is an issue. Other than files not being available it works perfectly. My issue is occurring in a folder with over 1,000 files in many sub-folders.

Try mounting a large file share, browse or list all of the directories with 'ls -laR', and then run the following to see if you are really *not* having any issues. 

```
grep FindClose /var/log/kern.log
```

If it comes back without anything you can proudly say you are awesome with much awesomeness and you don't know what our problem is.

I was glad to see that you got this resolved.

My original point was that blaming the kernel was inappropriate, since sharing and accessing shares worked perfectly for me with the same kernel.

I've never accessed a share from the Terminal. Where is it? I tested access to a share with 12,000 files in a couple of dozen folders using Nautilus, and everything worked properly, including running Properties, which required reading all the directories.

---

### Post by seth3d on 2011-05-10
> **gordintoronto said:**
> I was glad to see that you got this resolved.

My original point was that blaming the kernel was inappropriate, since sharing and accessing shares worked perfectly for me with the same kernel.

I've never accessed a share from the Terminal. Where is it? I tested access to a share with 12,000 files in a couple of dozen folders using Nautilus, and everything worked properly, including running Properties, which required reading all the directories.

I wasn't blaming the kernel, just the CIFS_VFS kernel mode driver. :-)

_My_ point was that your original post wasn't very helpful, and didn't contain any of the information you just posted. I'm sorry if I come across as snide. I sometimes have difficulty writing things when I'm frustrated, and my objective was to give tools to try to troubleshoot the issue. Want to learn how to capture network packets from a CIFS directory listing?

---

### Post by wlraider70 on 2011-05-11
I have a shared folder "common" that I want several users to have full access to. 

They can see the folder and the files, nut not access them at all.

---

### Post by gordintoronto on 2011-05-11
> **wlraider70 said:**
> I have a shared folder "common" that I want several users to have full access to. 

They can see the folder and the files, nut not access them at all.

Is it a Windows share? This thread is about Windows shares...

(If it's a Ubuntu share, did you click "guest access" when you created it?)

---

### Post by lyricmuse on 2011-05-14
Just wanted to give you a big "THANK YOU" for this information.  I've been pulling my hair out (what's left of it) over sharing in a mixed network.  This did the trick and I can see files between all my machines.

---

### Post by jhatashi on 2011-05-17
Thank you for the info, this thread was helpful.

What ended up being my main problem on 10.04 LTS was long hostnames.  My shares and server were not visible to any other machines on the network.  I was able to connect with \\ip\sharename but browsing for them was giving me nothing.  Even 'smbtree -N' on the machine I was trying to configure would not show its own shares.  Finally I noticed that my hostname was getting trucated in smbclient -L localhost.  So I changed it from jason-desktop-linux to desktop-linux and everything fell into place after that.

---

### Post by maverick280857 on 2011-06-03
I have a desktop (running Win 7) and a laptop (running Natty), both connected via a wireless network.

After following the steps outlined in post #1, I am able to access Linux shares from Win 7.

But I am not able to access Win 7 shares from Natty, although I do see the Win 7 system in 'Windows shares' in Nautilus. When I click on the Win-7 machine, I get this error message

```
**Unable to mount location**
Failed to retrieve share list from server
```

I don't have Windows Live Sign In assistant and have also disabled the antivirus on the Win 7 machine.

---

### Post by dmizer on 2011-06-05
> **maverick280857 said:**
> I have a desktop (running Win 7) and a laptop (running Natty), both connected via a wireless network.

After following the steps outlined in post #1, I am able to access Linux shares from Win 7.

But I am not able to access Win 7 shares from Natty, although I do see the Win 7 system in 'Windows shares' in Nautilus. When I click on the Win-7 machine, I get this error message

```
**Unable to mount location**
Failed to retrieve share list from server
```

I don't have Windows Live Sign In assistant and have also disabled the antivirus on the Win 7 machine.

Have you tried this yet? [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

---

### Post by maverick280857 on 2011-06-05
> **dmizer said:**
> Have you tried this yet? [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

Yeah. And I even disabled the antivirus software.

---

### Post by dmizer on 2011-06-05
> **maverick280857 said:**
> Yeah. And I even disabled the antivirus software.

Other possible causes include:
[LIST]
[*]File/directory names may be too long.
[*]Client and server have the same hostname. More here -> [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/338411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/338411)
[*]File names with unusual characters
[/LIST]

The problem with this error is that it's generic. There's no useful information provided as to what the real cause is, so it's extremely difficult to give solutions. You may find more information by looking in the logs at /var/log/

---

### Post by maverick280857 on 2011-06-06
Do you think this has to do with both systems being on a wireless network? I am able to access Windows shares from Ubuntu when both systems are on a wired network. But when on a wireless network, Ubuntu can't access Windows shares.

---

### Post by gordintoronto on 2011-06-06
Being on a wireless network should make no difference to file sharing.

---

### Post by dmizer on 2011-06-06
> **gordintoronto said:**
> Being on a wireless network should make no difference to file sharing.
Correct, this should make no difference, but I have certainly seen many people with this problem. The same computer can connect when wired, but not when wireless.

> **maverick280857 said:**
> Do you think this has to do with both systems being on a wireless network? I am able to access Windows shares from Ubuntu when both systems are on a wired network. But when on a wireless network, Ubuntu can't access Windows shares.
I have seen many people reporting this behavior before, wired works and wireless does not. Try checking to make sure that the firewall on the Ubuntu machines are not active when connected wirelessly.

---

### Post by moorsey on 2011-08-06
> **maverick280857 said:**
> I have a desktop (running Win 7) and a laptop (running Natty), both connected via a wireless network.

After following the steps outlined in post #1, I am able to access Linux shares from Win 7.

But I am not able to access Win 7 shares from Natty, although I do see the Win 7 system in 'Windows shares' in Nautilus. When I click on the Win-7 machine, I get this error message

```
**Unable to mount location**
Failed to retrieve share list from server
```

I don't have Windows Live Sign In assistant and have also disabled the antivirus on the Win 7 machine.

I've been battling this with my Win 7 machine and 3 Ubuntu machines.  This happens randomly where the Ubuntu machines cannot see Windows shares.  I find a reboot of the Win machine fixes it most times.  Either that or a change in wind direction etc etc

Very irritating, have tried everything online about the issue, more annoying is that it is random and doesn't happen all the time.

---

### Post by lucamanu on 2011-10-22
Hi all.
I tried to solve this problem for months now, without any success.
Here is the situation:

- I have a Ubuntu Machine, connected to internet via a wifi router (gigaset se551) which has a shared filespace storage. 
- The filespace on the router is available as a win share.
- I can access and fully manipulate the share both with windows machines and with my android smartphone (used Astro file manager). I assume therefore that the filespace can be normally accessed.
- My ubuntu machine does not manage to access the winshare. 
- I'm running 10.04.3, recently upgraded from 8.04.3 (Hardy Heron) because I thought this problem was a bug in Hardy Heron...

Symptoms:
- If I try to access with Nautilus (Places->Network->Windows Network) I get the classic "Unable to mount location - Failed to retrieve share list from server".
- If I type the IP address in nautilus/Location (smb://ipaddress/) I can see the two shares available on the filespace. If I double click to open any of them I get "Unable to mount location - Failed to retrieve share list from server"
- If I type in nautilus/Location: smb://ipaddress/sharename/ I get "Could not display "smb://ipaddress/sharename/ - Error: Failed to mount Windows share. Please select another viewer and try again".
- If I try Places->Connect to Server... and insert all data, a window pops up asking for the password, but I did not assign any password and the shares are unprotected (all users on the lan can access them). If I click enter without entering any password, I get "Cannot display location "smb://ipaddress/sharename/ - Error: Failed to mount Windows share"
- - If I type in firefox: smb://ipaddress/sharename/ I get a page showing the two partitions, but I cannot go any further.

I tried to follow all suggestions of the initial post of this thread. The ubuntu machine and the router share the same workgroup (it is called WORKGROUP - could this be a problem?).

I don't have a firewall active, this is my iptable:

> luca@luca-desktop:/etc/samba$ sudo iptables -L
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

This is smbtree:

> luca@luca-desktop:/etc/samba$ smbtree
Enter password: 
WORKGROUP
	\\SE551          		Samba 3.4.7
		\\SE551\IPC$           	Remote Inter Process Communication
		\\SE551\webserv        	Share Folder
		\\SE551\partition1     	partition1

Finally I attach the smb.conf. I tried two different ones: first I tried modifying the one which I inherited from the Hardy Heron (which was already creating problems). **[ATTACH]205179[/ATTACH] **
Then I downloaded a simpler one from the net and tried to use it, to no avail. **[ATTACH]205180[/ATTACH]**
I must highlight that the behaviour of the machine never changed.

---

### Post by ripon.nh on 2011-10-25
wins before dns makes Internet browsing slow. 

Best not to edit /etc/nsswitch.conf, instead in the file /etc/samba/smb.conf find and edit the line

**;   name resolve order = lmhosts host wins bcast**

to

[B]name resolve order = lmhosts wins bcast host

[/B]which only effect SMB browsing

---

### Post by lucamanu on 2011-10-25
@ripon, if you were referring to me, I tried your suggestion, but it did not have the slightest impact on my problem.
Thanks however.
L.

---

### Post by ripon.nh on 2011-10-26
> **lucamanu said:**
> @ripon, if you were referring to me, I tried your suggestion, but it did not have the slightest impact on my problem.
Thanks however.
L.

 Sorry, wasn't referring to you, commented on the original post. Regarding your issue, sounds like problem with nautilus file manager. Try installing Krusader (or Gnome Commander) file manager to see if you can mount with that. If not the problem could be the version of smbclient you are using.  Hope that helps.

---

### Post by lucamanu on 2011-10-29
Thanks Ripon. I installed Krusader, and when I connect to the server it actually sees the share, but when I try to open it, it replies with an error:
The file or folder "smb://192.168.2.1/sharename/ does not exist"
:confused:

---

### Post by Paddy Landau on 2011-10-31
@lucamanu:

** First**

Check that your Windows and Ubuntu computers do not have the same name.

*Ubuntu:* Look in [FONT=Fixedsys]/etc/hostname[/FONT] to see your computer name. (If you change it, you must also change it in [FONT=Fixedsys]/etc/hosts[/FONT], and reboot your computer. There's probably a GUI way to change the name, but I don't know it.)

*Windows:* Look in Control Panel > System > Computer name. While you are there, double-check that the workgroup name is indeed WORKGROUP (or, if you change it, also change it in [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] on your Ubuntu machine).

**Second**

Check that you have given permission to guests from your Windows share. I'm not entirely familiar with Windows any more, but here are the few bits I do know.

On your Windows computer:

[LIST]
[*]Control Panel > Network and Sharing Centre > Change advanced sharing settings:
[LIST]
[*]Turn on network discovery
[*]Turn on file and printer sharing
[*]Turn on sharing so anyone with network access can read and write files in the Public folders
[*]Use 128-bit encryption to help protect file sharing connections
[/LIST]
 
[*]Right-click your Public folder > Properties > Sharing > Share > Everyone > Read/Write
[/LIST]
You may have to reboot your Windows computer *and* reboot your Ubuntu computer (to ensure that caches are cleared).

**Third**

If that does not solve the problem, try the following. I cannot guarantee it will work, but it helped me.

On your Ubuntu computer:

[LIST]
[*]Back up your [FONT=Fixedsys]/etc/samba/smb.conf[/FONT]
[*]Take my version of [FONT=Fixedsys]smb.conf[/FONT] (attached).
[LIST]
[*]*If you have a shared folder on your Ubuntu machine (that Windows must be able to see):*
[LIST]
[*]Change [FONT=Fixedsys]YourUbuntuComputerName[/FONT] to your computer's name (i.e. [FONT=Fixedsys]/etc/hostname[/FONT]).
[*]Change [FONT=Fixedsys]/YourUbuntuPublicPath[/FONT] to your computer's shared folder, e.g. [FONT=Fixedsys]/public[/FONT]
[/LIST]
 
[*]*If you do **not** have a shared folder on your Ubuntu machine:*
[LIST]
[*]Remove (or comment out) the entire [FONT=Fixedsys][public][/FONT] section at the end of the file.
[/LIST]
 
[/LIST]
 
[*]Replace [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] with this modified version.
[/LIST]
Restart your Ubuntu computer to ensure Samba registers the new version. Let us know whether or not you can connect.

---

### Post by yellerKat on 2011-10-31
> **ripon.nh said:**
> wins before dns makes Internet browsing slow. 

Best not to edit /etc/nsswitch.conf, instead in the file /etc/samba/smb.conf find and edit the line

**;   name resolve order = lmhosts host wins bcast**

to

[B]name resolve order = lmhosts wins bcast host

[/B]which only effect SMB browsing

Hey Ripon thank you! I've been cursing my ISP for slow dns look up, then I implemented your advice and the difference in DNS lookup time is startling! :)

---

### Post by emil_donca on 2011-12-05
Hi!!

I really wanted to write about my experience.

I was getting "Unable to mount location: Failed to retrieve share list from server" when accessing XP box.

I followed all steps like 3 times, nothing worked. After reading 8 pages of replies I eventually stopped.



I took me a full day to try all sorts of things then I eventually gave up. In the evening I noticed also the XP box cannot be ping'ed and I came accross this thread: [http://www.tek-tips.com/viewthread.cfm?qid=920007](http://www.tek-tips.com/viewthread.cfm?qid=920007)  where everybody is perplexed for 3+ months that the ping wont work on a machine no matter what. Turns out the culprit was a CISCO VPN software that does some firewalling of its own. After removing it ping works fine AND ALL WINDOWS SHARES CAN BE BROWSED FROM NAUTILUS!! hooray

--hope this helps somebody,
Emil

---

### Post by l07 on 2011-12-31
I've tried the things suggested, but still cannot access xp from ubuntu. Help: [http://ubuntuforums.org/showthread.php?p=11576519#post11576519](http://ubuntuforums.org/showthread.php?p=11576519#post11576519).

---

### Post by juannm on 2012-01-10
In respect to the PROBLEM 3 - PART 2, as said in the tutorial:

> **dmizer said:**
> 
***Problem 3 - Part 2***
You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
```
sudo apt-get install winbind
```
Then, either restart networking or reboot.


But here [http://ubuntuforums.org/showthread.php?t=1873912](http://ubuntuforums.org/showthread.php?t=1873912)
bab1 points out that winbind is not needed if what we want is just netbios name resolution.

> **bab1 said:**
> 
You DO NOT need a WINS server with this solution nor do you need winbind (a utility to map Windows *user* accounts to Linux user accounts


So, is it actually needed of not?

---

### Post by Paddy Landau on 2012-01-11
> **juannm said:**
> So, is [winbind] actually needed [or] not?
Well, I have it installed by default on my machine. So, just install it; if it's not used, it'll do nothing, and if it's needed, it's there.

---

### Post by dmizer on 2012-01-15
> **juannm said:**
> In respect to the PROBLEM 3 - PART 2

But here [http://ubuntuforums.org/showthread.php?t=1873912](http://ubuntuforums.org/showthread.php?t=1873912)
bab1 points out that winbind is not needed if what we want is just netbios name resolution.

So, is it actually needed of not?

I think this solution would be fine if you wanted your Ubuntu machine to be reachable (via netbios name resolution) from other machines, but it could help for your Ubuntu machine to reach the other SAMBA servers on the network in some situations, particularly if your SAMBA servers do not include any Windows machines.

This would also be a solution if you had a Windows machine (with a winbind server) always turned on. It would also be a solution if the Windows machine was turned on before the Ubuntu machine.

So, in some situations, you do not need a winbind server but in other situations, you do need a winbind server. Furthermore, if you have a winbind server installed, it doesn't break the network so it doesn't really hurt anything to have it installed. Since this guide is an attempt to cover as many possible Windows networking pitfalls as possible, this guide includes installing and configuring a winbind server.

---

### Post by fasta6 on 2012-03-25
Maybe I missed it, but I didn't see anything is this thread about changing "wins support".  

sudo gedit /etc/samba/smb.conf

Look for this section:

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

"wins support" is probably set to "no".  Change it to what is shown above, save, close, restart samba.

---

### Post by mgmiller on 2012-03-25
> **fasta6 said:**
> Maybe I missed it, but I didn't see anything is this thread about changing "wins support".  

sudo gedit /etc/samba/smb.conf

Look for this section:

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

"wins support" is probably set to "no".  Change it to what is shown above, save, close, restart samba.

If you have a line starting with a hash mark (#) it won't matter what you change the rest of the line to, it won't execute.

Perhaps you meant to say:
Look for this section:

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
  wins support = yes

"wins support" is probably set to "no".  Change it to what is shown above, make sure you remove the "#" at the beginning of the line, save, close, restart samba.

---

### Post by Paddy Landau on 2012-03-26
And yet, my smb.conf does not mention wins support, which is (by default) set to No. Yet mine works.

---

### Post by teknorah on 2012-04-13
These parts fixed my problem: Unable to browse share on Ubuntu 10.04 LTS machine from Linux Mint 12.

Thanks!

> **dmizer said:**
> 
***Problem 2 - part 1***
Open this file for editing with the following command:
```
gksudo gedit /etc/samba/smb.conf
```

Scroll down to the section that looks like this:
```
 #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]WORKGROUP[/COLOR]
```

Change “[COLOR="Red"]WORKGROUP[/COLOR]” in “workgroup = [COLOR="Red"]WORKGROUP[/COLOR]” to match your Windows workgroup.

***Problem 2 - part 2***
It may also help to add netbios name = [COLOR="Red"]computer-name[/COLOR] just below "workgroup = WORKGROUP".

Your "[COLOR="Red"]computer-name[/COLOR]" can be anything, but common convention is to use the name you gave it when you installed Ubuntu (everything after the "@" symbol on the CLI prompt).

For example, here's my CLI prompt:
```
dmizer@[COLOR="Red"]shinkansen[/COLOR]:~$
```
And here's my smb.conf file:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = [COLOR="Red"]shinkansen[/COLOR]
```

Now, save the file by clicking on "File" > "save", close gedit, and restart samba with the following command (Pre Jaunty):
```
sudo /etc/init.d/samba restart
```
If, after running the above command, you see this error (Since Jaunty):
```
sudo: /etc/init.d/samba: command not found
```
Use the following command (or reboot) instead:
```
sudo service smbd restart
```

[CENTER]= = = = = = = = = = = = = = = = = = =[/CENTER]

[SIZE="4"]**Problem 3:**[/SIZE]
Ubuntu is unable to reliably browse Windows host names by default. Enabling this ability will also require a conf file edit.

[COLOR="Red"][B]---CAUTION---
If you are using Firestarter, uninstall it before making this edit. Firestarter may prevent the machine from booting after this change is made. Use GUFW instead.
---CAUTION---[/B]
[/COLOR]
***Problem 3 - Part 1***
Open /etc/nsswitch.conf for editing with the following command:
```
gksudo gedit /etc/nsswitch.conf
```
Find the line that looks something like:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
For this line, [order IS important](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15). You’ll need to add the “wins” option before dns, so the line reads like this:
```
 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Now, save the file by clicking on "File" > "save" and close gedit.

***Problem 3 - Part 2***
You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
```
sudo apt-get install winbind
```
Then, either restart networking or reboot.

---

### Post by dmizer on 2012-04-17
> **fasta6 said:**
> Maybe I missed it, but I didn't see anything is this thread about changing "wins support".  

sudo gedit /etc/samba/smb.conf

Look for this section:

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

"wins support" is probably set to "no".  Change it to what is shown above, save, close, restart samba.

This is a common mistake. Please refer to man smb.conf where it says:
```
       wins support (G)

           This boolean controls if the nmbd(8) process in Samba will act as a
           WINS server. [B]You should not set this to yes unless you have a
           multi-subnetted network and you wish a particular nmbd to be your
           WINS server[/B]. Note that you should NEVER set this to yes on more
           than one machine in your network.

           Default: wins support = no
```
In Lunux, the server (allowing other computers to reach yours) and client (allowing your computer to reach others) functions of samba are separate. For the most part, smb.conf handles the server part of samba while Windows browsing is a client function and is handled by mount and cifs, or related network tools included in Nautilus or [gigolo]("http://www.uvena.de/gigolo/") (GIO and GVfs).

With the exception of the "workgroup" and "netbios name" options in smb.conf (which aren't even necessary, just helpful), the smb.conf file has no effect on Linux ability to browse Windows networks.

---

### Post by Paddy Landau on 2012-04-20
> **dmizer said:**
> ... In Lunux, the server (allowing other computers to reach yours) and client (allowing your computer to reach others) functions of samba are separate...

... the smb.conf file has no effect on Linux ability to browse Windows networks.
dmizer, your comments are most helpful, and they clarify the situation, thank you.

I am curious, then, because I have one (minor) problem. The Windows and Ubuntu computers can access each other's public folders in read-write-create mode, with one exception: Ubuntu machines cannot *create* files or folders on Windows public folders. How do I solve that problem? (They are Windows 7 and Ubuntu 11.04, both fully updated.)

---

### Post by dmizer on 2012-04-21
> **Paddy Landau said:**
> dmizer, your comments are most helpful, and they clarify the situation, thank you.

I am curious, then, because I have one (minor) problem. The Windows and Ubuntu computers can access each other's public folders in read-write-create mode, with one exception: Ubuntu machines cannot *create* files or folders on Windows public folders. How do I solve that problem? (They are Windows 7 and Ubuntu 11.04, both fully updated.)

Adding your Ubuntu username and password to the Windows computer, and then including it in the allowed users for the public share should fix this problem.

---

### Post by Paddy Landau on 2012-04-22
> **dmizer said:**
> Adding your Ubuntu username and password to the Windows computer, and then including it in the allowed users for the public share should fix this problem.
Hmm, it's already that way. Never mind, for me it is not worth the effort. I'll wait until 12.04 is here, and if it still doesn't work I'll start a new thread.

Thank you for your time.

---

### Post by lwfitz on 2012-05-14
> **dmizer said:**
> Howto: Fix Windows share browsing issues



You rock! Thank you for this. Worked like a charm on crunchbang 10.

---

### Post by Brian Willian on 2012-07-31
thank you, solve my problem.

---

### Post by HotPlug on 2013-05-16
> **emil_donca said:**
> Hi!!
 Turns out the culprit was a CISCO VPN software that does some firewalling of its own. After removing it ping works fine AND ALL WINDOWS SHARES CAN BE BROWSED FROM NAUTILUS!! hooray

--hope this helps somebody,
Emil

Man, you saved the rest of my hairs from being pulled out in rage. I've spent 3 days tweaking samba and nsswitch without any success until I found your post. This stuped cisco anyconnect indeed somehow spoils windows shares browsing. '/etc/init.d/vpnagentd stop' resolved the issue.

Cheers, Emil.

---

### Post by DestructiveLabs on 2013-06-06
Thank you for this comprehensive guide! I have been combing the net for a few days trying to solve this problem. Every other guide wanted to only address your ***Problem 2.*** I would only get the error intermittently. So, obviously that wasn't the fix I needed and, for the life of me, I could not pin down the culprit. Turned out to be the Windows LIVE software that came with the Wife's laptop!! I uninstalled all LIVE components, restarted and **BAM! **Worked. :cool:

Running 12.04LTS on mine and Win7 on the Wife's laptop.

---

### Post by axismann on 2013-06-13
Correct me if I'm wrong but if you want to use wins in the nsswitch file, don't you need to have a wins server on the network?  This post doesn't mention that for what I could tell.  Maybe I over looked it.  Oops!  I did (Wins Support = Yes).

---

### Post by dmizer on 2013-07-01
> **axismann said:**
> Correct me if I'm wrong but if you want to use wins in the nsswitch file, don't you need to have a wins server on the network?  This post doesn't mention that for what I could tell.  Maybe I over looked it.  Oops!  I did (Wins Support = Yes).

In "Problem 3 - Part 2", my tutorial mentions that you need to install winbind for name resolution. Winbind is (among other things) a wins server. If you have a Windows machine on the network, then the Windows machine will have a wins server. There is a lot more to configuring a wins server than adding "Wins Support = yes" to the smb.conf file. You'll need to correctly configure nmbd and learn about "domain master", "local master", "local master browser", and "domain master browser", and how to identify and configure them. Otherwise your local Windows machines will wreak havoc on your NetBIOS name resolution.

To correctly configure nmbd for name browsing support, you'll need to do a lot of digging through here: [http://www.samba.org/samba/docs/man/manpages-3/nmbd.8.html](http://www.samba.org/samba/docs/man/manpages-3/nmbd.8.html)

And here:
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Otherwise, I suggest turning off "wins support" in smb.conf and using winbind instead, because it mostly works out of the box in the largest variety of networking situations.

See also my post here: [http://ubuntuforums.org/showthread.php?t=1169149&p=11612737#post11612737](http://ubuntuforums.org/showthread.php?t=1169149&p=11612737#post11612737)
And here: [http://ubuntuforums.org/showthread.php?t=1169149&p=11850323#post11850323](http://ubuntuforums.org/showthread.php?t=1169149&p=11850323#post11850323)

---

### Post by Ridgerunrbunny on 2013-07-05
Oh, come on it can't be this complicated!

---

### Post by gordintoronto on 2013-07-05
99% of the time it isn't!

---

### Post by dmizer on 2013-07-09
> **Ridgerunrbunny said:**
> Oh, come on it can't be this complicated!

It looks complicated because:
[LIST=1]
[*]It is an omnibus tutorial which was created to provide fixes for more than one common NetBIOS resolution problem.
[*]It's wordy because I took a lot of time explaining the "why" of the problems in hopes that people could find their own answers if mine did not fix their particular problem.
[*]It addresses problems and fixes that changed across several versions of Ubuntu, some of which are out of date but I no longer have the time, motivation, nor experience to maintain the original tutorial.
[/LIST]

---

### Post by leinardo on 2013-08-08
Is this tutorial supposed to work with Windows 8 and Ubuntu 13.04? Cause, I just tried it and it does not work.... Any ideas of what might be going wrong? I would post my smb.conf file, but it is the same as the default except for the changes that you have mentioned.

---

### Post by gordintoronto on 2013-08-09
"It does not work" doesn't give people anything to go on.

I set up a shared folder in Windows 8.1 Preview and tried to access it from Ubuntu 13.04, but I couldn't get past the password prompt. (Win 8.1 told me the password to use, no joy.)

Using Win 8.1 to access a share in Mint 13 worked the first time. I have never edited a configuration file or used the command line for anything share-related.

---

### Post by lynton2 on 2013-10-02
Hi dmizer and co,

I'm having real issues being able to browse to external USB disks that are mounted to my Asrock ION which is running XBMCbuntu.

I've followed all of the information in your guide to no avail, and was wondering if you might be able to point me in the right direction. I am a massive Linux newb, so apologies if I've made any simple errors.

I'm trying to access the USB disks from my Win7 machine. From that PC, I can see other shares that are enabled by default which are stored on the OS disk on the XBMCBuntu machine - just not the external disks. Here's the output from my smb.conf. My username on XBMCBuntu is "xbmc".

```
[global]
workgroup = WORKGROUP
server string = %h server (Samba, XBMC)
netbios name = XBMC
dns proxy = no
name resolve order = lmhosts wins bcast host
guest account = xbmc
guest ok = yes
load printers = no
show add printer wizard = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n $
pam password change = yes
map to guest = bad user
security = SHARE
wins support = yes
dfree command = /bin/dfree.sh
create mask = 644
directory mask = 755


[Movies]
path = /home/xbmc/Movies
comment = Video's and Movies Folder
writeable = yes
browseable = yes
guest ok = yes


[Music]
path = /home/xbmc/Music
comment = Music Folder
writeable = yes
browseable = yes
guest ok = yes


[TV Shows]
path = /home/xbmc/TV Shows
comment = TV Shows Folder
writeable = yes
browseable = yes
guest ok = yes


[Downloads]
path = /home/xbmc/Downloads
comment = Downloads Folder
writeable = yes
browseable = yes
guest ok = yes


[Pictures]
path = /home/xbmc/Pictures
comment = Pictures
writeable = yes
browseable = yes
guest ok = yes


[System]
path = /home/xbmc/.xbmc
comment = XBMC System Share
writeable = yes
browseable = yes
guest ok = yes


[External]
path = /media/xbmc/External
public = yes
only guest = yes
comment = External_Movies
writeable = yes
guest ok = yes
browseable = yes
force user = xbmc

```

Of the above shares, "External" is the one that doesn't work. The others all work fine. When trying to browse to "External" from my Win7 PC, I can see the directory, but when I try to open it I get "Windows cannot access \\XBMCBUNTU\External. You do not have permission to access \\XBMCBUNTU\External. Contact your network administrator to request access."

My .conf file has blown out a little through Googling for other fixes (like force user = xbmc, which a lot of people recommended).

Any advice would be very much appreciated. I'm coming from an OpenElec build, and I much prefer the flexibility of an "actual" Linux box like XBMCBuntu provides, so I'd love to stick with it!

Thanks!

Edit: I think I'm getting closer. It seems like XBMCBuntu doesn't have the right permissions to use the external disks properly? Here's the output from ls -l:

> xbmc@XBMC:~$ ls -l
total 108
drwxr-xr-x  6 xbmc xbmc  4096 Oct  2 11:59 couchpotato
drwxr-xr-x  6 xbmc xbmc  4096 Oct  2 12:20 CouchPotatoServer
drwx------  2 xbmc xbmc  4096 Oct  2 22:30 Desktop
drwxr-xr-x  3 xbmc xbmc  4096 Oct  2 00:26 Downloads
drwxr-xr-x  2 xbmc xbmc  4096 Oct  1 23:47 Movies
drwxr-xr-x  2 xbmc xbmc  4096 Oct  1 23:47 Music
drwxr-xr-x  2 xbmc xbmc  4096 Oct  1 23:47 Pictures
drwxr-xr-x 11 xbmc xbmc  4096 Oct  3 12:28 sickbeard
drwxr-xr-x  2 xbmc xbmc  4096 Oct  1 23:47 TV Shows
-rw-rw-r--  1 xbmc xbmc 24442 Oct  2 12:14 xbmc_crashlog-20131002_121408.log
-rw-rw-r--  1 xbmc xbmc 23924 Oct  2 12:28 xbmc_crashlog-20131002_122856.log
-rw-rw-r--  1 xbmc xbmc 24209 Oct  3 01:37 xbmc_crashlog-20131003_013700.log


Is that what the above suggests?

---

### Post by dmizer on 2013-10-03
Hello lynton2,

In order to share a drive, it has to appear in fstab. Meaning, you'll have to create a hard mount in /etc/fstab for your usb drive. Once you've done that, then you'll have the correct permissions to share the drive with samba.

Since you're new, it's a good idea for you to understand that there are two parts of Windows sharing on Linux. There is a client side for (which this tutoral addresses) and a server side (which you need help with).

CIFS is the file system that handles browsing Windows shares from other machines. It does not require any modification of your smb.conf file. Ubuntu -> Windows
smbd is your share server. It allows other computers to see files on your Linux computer. In order for other computers to see your files, you'll need to modify of your smb.conf file. Ubuntu <- Windows

This will be helpful in the future when troublshooting other issues that you may encounter when using Windows shares.

Finally, here is a tutorial for hard mounting your USB drive: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by lynton2 on 2013-10-03
Thanks, dmizer! I'll give that a crack tomorrow. I started to suspect it was a mounting issue, after applications that initially worked with directories on the USB drives started failing after a reboot. I'll check the tutorial you linked. Thanks again!

---

### Post by lynton2 on 2013-10-03
> **dmizer said:**
> Hello lynton2,

Finally, here is a tutorial for hard mounting your USB drive: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Perfect. Thanks dmizer; once I'd followed that and correctly mounted the drives it all came together. Thanks again.

---

### Post by 2CV67 on 2014-03-11
This Howto had a large number of very satisfied customers in 2009 - 2011.

Are the recommendations still valid in 2014?
For 13.10 - 12.04LTS - W7 - W8?

It would be helpful if this could be clarified in the first post, to avoid time-wasting, one way or the other.

If no longer valid, could you point to anything equivalent?

Thanks!

---

### Post by Paddy Landau on 2014-03-11
I personally have not had problems since going to Ubuntu 12.04 and Windows 7. I don't know if anyone else has problems.

---

### Post by dmizer on 2014-03-30
> **2CV67 said:**
> This Howto had a large number of very satisfied customers in 2009 - 2011.

Are the recommendations still valid in 2014?
For 13.10 - 12.04LTS - W7 - W8?

It would be helpful if this could be clarified in the first post, to avoid time-wasting, one way or the other.

If no longer valid, could you point to anything equivalent?

Thanks!

This howto addresses common problems people encounter with network configuration related to Windows share browsing. For the most part, the major points addressed here should be universal. A few of the terminal commands should be updated, but this can be circumvented by rebooting the machine.

This tutorial includes lots of information specific to Windows 7, including a blurb at the end about the tricky part of configuring Windows 7 shares in such a way that Ubuntu can see them. I have absolutely zero experience with Windows 8, and I don't have any plans to include it any time soon. I guess that's the biggest part missing from this tutorial. If someone wants to add information I'll be willing to spend some time updating the first post with more current information.

---

### Post by wsmith on 2014-04-21
> Problem 3 - Part 2
> You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:
> Code:

> sudo apt-get install winbind

As of Ubuntu 13, this has given me quite the fit. You also need to install the libnss_winbind package to make this work.

---

### Post by wendt-mark on 2014-05-21
Got a user on one of my 14.04 LTS machines who is having issues using  Nautilus\gvffs\smb to mount Windows shares.  Shares are being served by  Windows 2012 Server machines.

User's Windows domain account keeps getting locked out after first  successfully mounting a share, then either trying to open another share,  or when trying to open a sub-directory under an existing share mount.

I've logged into the machine under a different account, and don't seem  to have the same problem.  I can successfully open multiple shares and  multiple sub-directories without having my Windows domain account  locked.

Where or what should I be looking for on the Ubuntu machine that would cause a problem like this?

Thanks,
Marl

---


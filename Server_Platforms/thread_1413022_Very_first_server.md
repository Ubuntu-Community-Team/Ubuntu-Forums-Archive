---
title: "Very first server"
date: 2010-02-21
forum: Server Platforms
---

### Post by espressobeanie on 2010-02-21
Hi,

I'm building a personal file server out of old desktop hardware parts. I have everything I need, minus an understanding of how Ubuntu Server Edition works. Is there a gui to navigate around? or is it all command-line?

I'm wondering because I'm not sure how easy it would be for me to setup a program like Moblock.

---

### Post by stlsaint on 2010-02-22
Congrats on server. Well server edition DOES NOT come with an X environment. (GUI) It does have web based interfaces such as webmin for admin task and control of server. Most people just use ssh or vnc for server work. I use ssh which is great as it allows you to just setup the server and never have to go back to it with a keyboard/mouse/monitor. Just control remotely from client systems.

---

### Post by sicpsnake on 2010-02-22
Ubuntu Server is great. To get started with using it, that is if you are not comfortable with the command line, you can use "sudo apt-get install ubuntu-desktop --no-install-recommends"

Worked well for me. I eventually removed it all in place of DWM.

---

### Post by CharlesA on 2010-02-22
I originally had a GNOME GUI installed on my server, but now I just SSH in and configure it from there.

Installing a GUI would work. I usually use webmin for managing the box I have, but for the most part I think I just use SSH, since my server is configured how I want it to be.

---

### Post by espressobeanie on 2010-02-22
To be honest, all this remote admin server stuff makes me jittery. I know that hackers use remote connections to overtake computers, and I'd rather a gui so I can set everything up easily. I don't mind stripping down the gui when I have everything I want automatically running on it.

---

### Post by rizzeh on 2010-02-22
found a little cheat to bring up GUI program to my windows desktop via SSH so can still claim to use my server without desktop. Need Putty and Xming for that:
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://e.molioner.dk/guides/puttyx11](http://e.molioner.dk/guides/puttyx11)

If i could only find how to run X11 tunnel with screen? :)

---

### Post by Kiwi76 on 2010-02-22
> **espressobeanie said:**
> To be honest, all this remote admin server stuff makes me jittery. I know that hackers use remote connections to overtake computers, and I'd rather a gui so I can set everything up easily. I don't mind stripping down the gui when I have everything I want automatically running on it.

Remotely means to do it from another location (and PC). That's it. Just because hackers take control of PCs that way (and it's because it's the only way they have to), doesn't mean it's less secure, per se. In fact, if the server with be on your LAN, and you'll be controlling it from another PC on that same LAN, simply don't expose port 22 to the internet, and i believe you'll effectively be safe. The PC will still have port 22 open (to the rest of the LAN), but the firewall and/or router won't, so to the internet, it will be closed off completely. I do this. Only port 80 is exposed to the internet on my server. I log into it using Putty on my Windows workstation.

Now, if it's because you'd simply rather do it with a GUI and/or don't want to work with command line, then go for it. However, I dove in headfirst to command line, using this...

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

...and along with Google, I know enough, at least the basics, to keep it going. Of course, if anything new comes up, it's off to Google and/or here for me, but I understand the basics now.

---

### Post by CharlesA on 2010-02-22
What Kiwi76 said. Also, if you do set up SSH on the server, and don't expose it to the internet, you are fairly secure. If you do expose it to the internet, set up key-based logins and install something like fail2ban or denyhosts.

---

### Post by Iowan on 2010-02-22
[https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by kenada on 2010-02-22
I use the GUI on the Server, mainly cause I do a fair bit of file transfers to and from it. 
Its lazy I know but the drag and drop options I find a bit easier.

My server is basically for media so GUI is helpful when I want to run things Pyrenamer etc

---

### Post by absolver on 2010-06-02
Hi All,

This is also my very first server - Ubuntu or otherwise.  Installed 10.04 apparently successfully but on reboot, after seeing bios screen and messages, black screen and no response from keyboard.

Determined that it does have an IP - it pops up in Angry IP when I turn it on - but what do I use to access it over the network?  BTW I only installed the fileserver package - I mainly want to fill this older HP pavillion with hard drives and get rid of the NAS drives, for now at least.

The IP is "trusted" in Zone Alarm.  I have the username and password and don't think there's anything else I saw in the install that I needed to access it. 

So how do I log in to the server?  What comm program?

Thanks

---

### Post by tad1073 on 2010-06-02
ssh yourname@serveripaddress

---

### Post by absolver on 2010-06-02
Guess I didn't mention that the network is presently all XP boxes.  Most of the sources I found for SSH look to be for Linux.  Can you suggest an open source windows version?

Thanks

---

### Post by arrrghhh on 2010-06-02
> **absolver said:**
> Guess I didn't mention that the network is presently all XP boxes.  Most of the sources I found for SSH look to be for Linux.  Can you suggest an open source windows version?

Thanks

You mean an SSH client for Windows?  [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) is probably the 'standard' one that most people use because it's free.

There's also [KiTTY](http://lifehacker.com/5541871/kitty-adds-session-saving-portability-and-more-to-putty?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker%29&utm_content=Google+Feedfetcher) which just adds some nice features that the original PuTTY is missing.

[SecureCRT](http://www.vandyke.com/products/securecrt/) is pretty nice/powerful but it's not free.

---

### Post by absolver on 2010-06-05
Hi again,

Thanks for your help.  However there must be something pretty fundamental that I'm in the dark about.

I do get a ping response from the server so there's the good news.  Installed Putty on my XP laptop on the home network.   Entered the IP , used default port 22 and selected SSH as connection type.  Putty window opens with the IP in the title bar then a popup window saying "Network error: Connection refused"  Also tried username@ipaddress.  Same result.

So, still a black screen and no response from the keyboard.

Looked through the Putty doc and others but all seem to assume I know something I obviously don't.

Suggestions?

---

### Post by absolver on 2010-06-05
Curiouser and curiouser...

When I enclose the IP with these <> the error message sometimes changes to 
"Network error: Connection timed out" rather than refused.

Then any idea why I would get this in the Putty event log?

2010-06-05 16:41:43    Looking up host "<192.168.2.103>"
2010-06-05 16:41:43    Connecting to 92.242.144.1 port 22

The .103 is the IP address of the server

What is 92.242.144.1 port 22 that it appears to trying to connect to?  Is Putty "calling home?" It times out if I ping it.

---

### Post by Goodheart on 2010-06-06
Are you quite sure that .103 is the IP-address of your server? You mentioned earlier that it "got an ip-address" that sounds like it is getting one from a dhcp-server. For a server, a fixed ip-address is the better option.

What is 92.242.144.1 port 22 that it appears to trying to connect to

That looks like it is trying to connect to your outside ip-address, i.e. the one you get from your ISP.

---

### Post by PyrexKidd on 2010-06-06
92.242.144.1 is not pingable.

nmap times out.  (although it is still running in the background as I type this... maybe I'll find something by the time I done typing).

Here is the whois lookup.  
```

% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '92.242.128.0 - 92.242.159.255'

inetnum:        92.242.128.0 - 92.242.159.255
netname:        UK-BAREFRUIT-20071227
descr:          Barefruit Ltd.
country:        GB
org:            ORG-BL53-RIPE
admin-c:        PR42-RIPE
tech-c:         PR42-RIPE
status:         ALLOCATED PA

mnt-by:         RIPE-NCC-HM-MNT
mnt-lower:      CATALYST2-MNT
mnt-domains:    CATALYST2-MNT
mnt-routes:     CATALYST2-MNT
source:         RIPE # Filtered

organisation:   ORG-BL53-RIPE
org-name:       Barefruit Ltd.
org-type:       LIR
address:        Barefruit Ltd.
                26 Southampton Street
                London WC2E 7RS
                United Kingdom
phone:          +44 207 717 8675
fax-no:         +44 207 717 8759
admin-c:        PR42-RIPE
mnt-ref:        CATALYST2-MNT
mnt-ref:        RIPE-NCC-HM-MNT
mnt-by:         RIPE-NCC-HM-MNT
source:         RIPE # Filtered

```

This looks like a routed netblock for Barefruit Ltd.  Although this isn't the standard ARIN whois reply, so I could be wrong.

I loose the traceroute to that address at 208.84.49.26, although traceroute hasn't worked correctly since installing UD 10.04...

the difference between 192.168.0.10 and <192.168.0.10>, the latter is not an IP address.  putty doesn't recognize the "<>" thus the time out, AFIK.

What does the port scan from angryIP show when you scan that address?

> 
Determined that it does have an IP - it pops up in Angry IP when I turn it on - but what do I use to access it over the network? BTW I only installed the fileserver package - I mainly want to fill this older HP pavillion with hard drives and get rid of the NAS drives, for now at least.


you need to install openssh-setver to be able to open an ssh tunnel to your server.
```

sudo apt-get install openssh-server

```

ssh-server should start automatically, though you may need to open that port if you are running a firewall.

for ufw:
```

sudo ufw allow 22
---or---
sudo ufw allow ssh

```

> 
Re: Very first server
[quote]
Quote:
Originally Posted by espressobeanie  
To be honest, all this remote admin server stuff makes me jittery. I know that hackers use remote connections to overtake computers, and I'd rather a gui so I can set everything up easily. I don't mind stripping down the gui when I have everything I want automatically running on it.


Remotely means to do it from another location (and PC). That's it. Just because hackers take control of PCs that way (and it's because it's the only way they have to), doesn't mean it's less secure, per se. In fact, if the server with be on your LAN, and you'll be controlling it from another PC on that same LAN, simply don't expose port 22 to the internet, and i believe you'll effectively be safe. The PC will still have port 22 open (to the rest of the LAN), but the firewall and/or router won't, so to the internet, it will be closed off completely. I do this. Only port 80 is exposed to the internet on my server. I log into it using Putty on my Windows workstation.

Now, if it's because you'd simply rather do it with a GUI and/or don't want to work with command line, then go for it. However, I dove in headfirst to command line, using this...

[http://net.tutsplus.com/tutorials/ph...rver-for-free/](http://net.tutsplus.com/tutorials/ph...rver-for-free/)

...and along with Google, I know enough, at least the basics, to keep it going. Of course, if anything new comes up, it's off to Google and/or here for me, but I understand the basics now.
[/quote]

ssh tunneling is one of the most (IMHO THE most) secure methods to access a server/computer.  The encryption method that ssh uses is more secure and efficient that https.  unlike telnet, which transmits everything in plain text, the even initiation protocol is an encrypted handshake.

people tend to forget that it is possible to break into the physical location of the server and hack it directly that way.  often times this is easier that exploiting a remote security hole.

I'm not exactly sure of your goals/network topology but if you are that concerned about security you can always unplug the incoming internet connection.  I say this tung in cheek, but seriously, the only way to have a 100% secure system is to isolate it.  However, that being said, todays systems are very secure, as long as you have taken at least the standard security precautions you should be safe (should's a funny word.)

Accessing a server inside of a LAN most certainly does not expose that ssh tunnel to the outside wold.  run a trace route to that IP, you'll get only two hops.  pc --> router then router --> server IP.  (although the trace may show only the one hop.)

on windows xp from the command line run:
```

tracert 192.168.2.103

```

Are you still unable to log into the server via local terminal?

also I'd recommend nmap over angryip.  personal preference, I've used both and I find nmap faster and more configurable, not to mention the HUGE community following/support.


by the way the nmap came back on 92.242.144.1
```

sudo nmap -sS -sV -O -PI -PT -PN 92.242.144.1
Starting Nmap 5.00 ( http://nmap.org ) at 2010-06-06 00:56 MDT
Warning: Giving up on port early because retransmission cap hit.
Interesting ports on 92.242.144.1:
Not shown: 984 closed ports
PORT     STATE    SERVICE      VERSION
1/tcp    filtered tcpmux
33/tcp   filtered dsp
70/tcp   filtered gopher
79/tcp   filtered finger
80/tcp   open     http         Apache httpd
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
524/tcp  filtered ncp
636/tcp  filtered ldapssl
646/tcp  filtered ldp
667/tcp  filtered unknown
714/tcp  filtered unknown
800/tcp  filtered mdbs_daemon
992/tcp  filtered telnets
1022/tcp filtered unknown
Device type: general purpose|WAP
Running (JUST GUESSING) : Linux 2.6.X (90%), AVM embedded (86%), Netgear embedded (86%), Linksys embedded (86%)
Aggressive OS guesses: Linux 2.6.9 (90%), Linux 2.6.9 - 2.6.24 (90%), Linux 2.6.20 (Ubuntu 7.04 server, x86) (89%)

```

I'm kinda curious myself as to what this IP is.  Anyone have any thoughts?  I was unable to log on to this IP using my gopher browser, but I believe we can say this server is up and running.

you could try pinging the broadcast address of your network and see what responses you get.  ping 192.168.2.255 (0 is the network and 255 is the broadcast.) personally I like to make all the 1-99 addresses static and allow DHCP on 100-199 with 200-254 being reserved for and "special" devices.

---

### Post by absolver on 2010-06-06
1st many thanks to PyrexKidd and Goodheart.

Reinstalled 10.4 server w/ openssh-server pkg as well as Lamp Server and Samba file server and am now logged in via Putty.

As far as my "goals/network topology," - topology 1st.  For now and the near future, I will only access the server on my home network - a linksys router (for wireless) and a D-Link switch tacked on to accommodate a couple more boxes. I really don't need remote login so it's a low priority.  That may change as I become more comfortable with basic operation, much less security issues related to remote login.

Goals - I primarily - or at least initially - I want to fill the HP Pavillion with big cheap drives in "pairs" - one primary and 1 backup drive and get rid of these WD NAS drives I have now.  The Lampserver is for me to play with Joomla and other CMS in my, uh, spare time.

Now that I can login, I will stick another drive in the server and see if I can get the other computers to access it.  Anything to look out for?

I understand that a server is not a desktop but is command line through Putty or another SSH client the only way to access and configure these things?  I could dual boot another XP machine and install Ubuntu desktop on that if it would make management easier.

Thanks again

---

### Post by absolver on 2010-06-07
OK, Another day...

I can now login and I've installed an additional hard drive in the server box to be accessed by the other boxes on the network.  This is an NTFS drive that already has data on it that I want to keep so I guess the 1st question is...

Is there any destructive process that will occur in accessing/configuring that drive?  I'm assuming there isn't but thought I'd better ask.

I've been poring through the Ubuntu server documentation but can't quite find a comprehensible instruction on how to detect - much less mount, set permission and access that drive.

Another consideration - I have a workgroup - call it WGA - that the other boxes appear in plus the regular windows Workgroup which has nothing in it.  Once the server shows up on the network list - ie to map network drive - I assume I'll be able to add it to WGA like the other windows boxes? 

I presently have several windows boxes on the network but no Ubuntu boxes other than the  server.  For the purpose of getting this thing working, would having another Ubuntu box available speed/smooth the process?  Or given that it's all command line - from Terminal in Ubuntu or Putty on Windows - is there any difference at all?

TIA

---

### Post by PyrexKidd on 2010-06-07
> **absolver said:**
> OK, Another day...

I can now login and I've installed an additional hard drive in the  server box to be accessed by the other boxes on the network.  This is an  NTFS drive that already has data on it that I want to keep so I guess  the 1st question is...

Is there any destructive process that will occur in  accessing/configuring that drive?  I'm assuming there isn't but thought  I'd better ask.

I've been poring through the Ubuntu server documentation but can't quite  find a comprehensible instruction on how to detect - much less mount,  set permission and access that drive.

Another consideration - I have a workgroup - call it WGA - that the  other boxes appear in plus the regular windows Workgroup which has  nothing in it.  Once the server shows up on the network list - ie to map  network drive - I assume I'll be able to add it to WGA like the other  windows boxes? 

I presently have several windows boxes on the network but no Ubuntu  boxes other than the  server.  For the purpose of getting this thing  working, would having another Ubuntu box available speed/smooth the  process?  Or given that it's all command line - from Terminal in Ubuntu  or Putty on Windows - is there any difference at all?

TIA

To detect a drive:
```

sudo fsdisk -l

```
To mount a drive:
```

mount /path/to/drive /mount/point

```
this works with all Linux FS, however there are some FS that it is  necessary to specify the type of FS.

from ```
man mount
```
> 
For most types all the mount program has to do is issue a simple  mount(2) system call, and no detailed knowledge of the filesystem type  is  required.
              For  a  few  types however (like nfs, nfs4, cifs, smbfs,  ncpfs) ad hoc code is necessary. The nfs, nfs4, cifs, smbfs, and ncpfs  have a separate mount
              program. In order to make it possible to treat all types  in a uniform way, mount will execute the program  /sbin/mount.TYPE  (if   that  exists)  when
              called  with  type TYPE.  Since various versions of the  smbmount program have different calling conventions, /sbin/mount.smbfs  may have to be a shell
              script that sets up the desired call.



here is a good tutorial on mounting an internal drive, this will walk  you through editing the fstab file so you don't have to manually mount  the drive all the time.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

this is the Ubuntu community doc on installing/mounting new drives:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Not sure what exactly you mean by a "destructive process" for installing  the drive.  I'd recommend formatting the drive to an ext3 or ext4 type  FS.  Formatting the drive will definitely destroy any data on the HDD,  however, you don't necessarily NEED to format the drive if you already  have data on it. 

If you want a GUI 
```

sudo aptitude  install --no-install-recommends  ubuntu-desktop

```

personally I prefer the command line.  Once you get used to it I think  it is much more efficient.

webmin is also available 
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

As far as work groups...  I'm not to familiar, to my understanding you  should be able to add it as normal--but I'm not really a network guy.  

As far as installing ubuntu on one of your client machines... I think  you should do it.  Probably wont speed up the administration of the  server--But lets fight the good fight against winbolws.

Other than command line access to ssh utilities, I don't see any  advantages over using putty or kitty on your client machines.

---

### Post by expatCM on 2010-06-08
even if you do not follow it all, the server setup guide found at [this]("http://woodel.com") link may make for some good background reading for you.

---

### Post by Leppie on 2010-06-08
> **kenada said:**
> I use the GUI on the Server, mainly cause I do a fair bit of file transfers to and from it. 
Its lazy I know but the drag and drop options I find a bit easier.
you can use the ssh function in nautilus for this...

---

### Post by PyrexKidd on 2010-06-08
> **Leppie said:**
> you can use the ssh function in nautilus for this...

that's so cool!!!!!

---

### Post by absolver on 2010-06-09
Ahhh!

Nothing like a little "light reading!"

Thank you all.

---

### Post by SteveHillier on 2010-06-09
This thread seems to take a right angle turn after post 10 and I wanted to address the initial problem of using a GUI on a server system.
Whenever I have used Ubuntu as a server I have set it up with the Desktop version and just not included the desktop type software (such as Open Office) in the install.
I then set up Apache, php, MySQL as required.
I have not tried to use it as a domain server yet - but it is a project I want to achieve one day.
I currently have a fully working web server based on Ubuntu with OpenPanel over the top.  It does what I want it to do.
After all isn't what I have done what the server version is anyway?

---


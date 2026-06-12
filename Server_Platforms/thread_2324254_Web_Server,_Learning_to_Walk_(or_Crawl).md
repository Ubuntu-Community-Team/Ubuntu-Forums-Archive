---
title: "Web Server, Learning to Walk (or Crawl?)"
date: 2016-05-12
forum: Server Platforms
---

### Post by raequin on 2016-05-12
Would help me start off in the right direction to set up a server?  My background is that I've used Ubuntu Desktop for a few years, occasionally coming to this forum for help, but have 0.0 units of server experience.  My family owns a server PC and now I get to set up the software.  Something simple and low maintenance would be great because, while computing is fun I have a million other things to do.  Something like Amahi is attractive but I think that particular software is not right for me (see the list, below).  I'm happy that a new LTS version of Ubuntu has just been released.  Here are the few desired functions of this server:

[LIST]
[*]Logitech Media Server (we own a Squeezebox)
[*]Host web pages (just a personal website or two)
[*]Media streaming (videos, music, and pictures) --- my current aim is to use Plex and want both local and Internet access
[*]File management --- uploading/downloading files on local network and also some pain-free way of maintaining a relatively current backup of important files on an external HDD
[*]Read-only file explorer access for relatives to browse and download photos
[/LIST]

I'm guessing that it's possible for me to get all these things running by following various web tutorials and the like, but feel that this approach might be a little too haphazard and ... sub-optimal.  That is, I'm afraid of bumbling around and wasting time with duplicate efforts or, worse, leaving out some important security feature.  Can you help me get a clear picture of what's important, how to go about the process of becoming a server admin, and have a good overview of the system?  Advice, links, and book recommendations are all welcome.

---

### Post by ian-weisser on 2016-05-12
Bumbling around haphazardly only harms you if you don't take the time to learn what each step does and why each step exists.

Advice: Create a VM for each independent service (like web hosting), so a mistake doesn't accidentally take down all services.

Advice: Use SSH keys from the start. Take the time and learn how to use ssh properly. Never start with passwords, thinking "I'll change over to keys soon." You won't, and your server will be quickly compromised.

Advice: Keep a (paper) journal of what you did, when, why, and how. You will surely need to tear down and rebuild some VM or service, and those notes will save you a lot of frustration.

Advice: If you run an internet-facing server, you need *real* security habits. Habits like regularly checking logs, regularly checking your listening ports, regularly checking for unusual network activity, and regularly-checking the unattended-upgrades log for each VM. Else your compromised machine will, unbeknownst to you, become part of the problem.

---

### Post by raequin on 2016-05-13
Thanks a lot for the information!  It seems to me that I have nowhere near the time required for proficiency in setting up and maintaining a Linux server.  (My plan is to just use FreeNAS instead.)

---

### Post by mastablasta on 2016-05-13
Prepare to learn abotu BSD then. same advice from ian applies on BSD as well.

---

### Post by raequin on 2016-05-14
> advice from ian applies on BSD as well

If I abandoned the idea of hosting web pages could I forsake all the security habits he mentions?  All I would use the server for would be local storage and streaming plus maybe setting up a VPN and enabling Remote Access on Plex Media Server.  Is there really that much to be concerned with if I only

[LIST]
[*]Set up NFS
[*]Install Logitech Media Server (for local Squeezebox)
[*]Install Plex (and possibly enable Remote Access)
[*]Install Transmission
[*]Maybe create a VPN
[/LIST]

Maybe I should add wireless MAC filtering, but assuming nobody gets on our network would the server described above have any more security risks than an Ubuntu desktop computer?  What I'm getting at, is can this be a simple operation if I forget about opening a port for the server?

---

### Post by mastablasta on 2016-05-14
you will need security as soon as you open a port to internet (e.g. remote access etc). if you have a LAN server only then you would have less steps needed.

as soon as you open a port to internet server will be attacked. mostly by some chinese IP who are looking to get new "zombies".

if you will have remote access and you are logging in via web or SSH then you need strong a password (keys for SSH) and something like fail2ban to block repeated intruders and prevent brute force attacks. desktop doesn't have any ports opened by default. 

in other words if you plan an open door policy, you better have some guard set at the doors.

what i would like to know what part do you find overly complicated? it all mostly involves installing a few apps from repository and then editing their config files. 

example in **fail2ban** after install - you setup email where warning of intrusion will be sent (not necessary), time that repeated abuser get's banned and how many tries they have before they get banned. maybe also what port is being monitored if you set one different from defaults (e.g. apache has port 80 by default but oyu can set it at 9000). you then save the file, restart the service and you are done.

**SSH remote access **- you create a set of keys with a command, copy public key to server, try to connect with private key only. if it works, disable password connection and you are done.

in any case various advice given is valid for BSD as well. if you need a  GUI interface to help you administer the server there are a couple good  ones available on Linux. have a look at:
**Ajenti **- web admin panel.  can be installed on various distros. i like it as it has editor  available in browser to edit config file.s no need to do thing in  command line.
**Openmedia vault **- debian based, plenty of addons. if i am not mistaking also for easilly setting up virtual machines.
**Nethserver **- CentOS based, they work hard to make it as easy for the users as possible. Plenty options.
**ClearOS** - CentOS based, plenty of plugins available. but some you need to pay for. Otherwise easy to setup and use.

You can install these in virtualbox and see how they work for you. here is how you use virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
Obviously you will do a server or minimal install so install will look something like this (minus the windows manager install): [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
mostly you click next, next with occasional password input and username.

The VM advice - VM's are good and will make things easy for you as you plan to run mutiple services. however, it is still possible to keep services separated without them.

---

### Post by raequin on 2016-05-14
Thanks for your time.

> you will need security as soon as you open a port to internet

I think I will just start with an Ubuntu LAN server and see if that gets me all the functionality I want (except for web-page hosting).

> what i would like to know what part do you find overly complicated?

I don't imagine that any one part of the process is difficult but I just don't have a big-picture view and so can't see how all the individual tasks fit together and am afraid that I'd leave out some important security seting.  Also, this lack of an overview means I don't know where to start or if it even matters where I begin.  I'm not sure if I'm communicating this well enough.  The whole setup/admin process just seems so big ... I don't have a handle on it.  Is it okay just to break it down to individual services and tackle them independently or is it a knee-bone's-connected-to-the-thigh-bone kind of thing?

---

### Post by mastablasta on 2016-05-15
i would say use Zentyal if it was liek the old one but they shaved off so much fucntionality from it.

so i will say install openmediavault into virtualbox. connect to it form browser and explore what things you can set up. the demo on their website will provide with a few quick information. but the real thing is instal as aside from their official repository they have 3rd party plugins (OMV Extras) repository that really has plenty of features. OMV Extras: [http://omv-extras.org/simple/index.php?id=how-to-install-omv-extras-plugin](http://omv-extras.org/simple/index.php?id=how-to-install-omv-extras-plugin)

you will be able to do the mentioned things using clicks in GUI quite easilly.

after you set it up you can search for plugins you want to add or simply add other services you want manually in command line.

---

### Post by bob_jones2 on 2016-05-17
One big word.

[SIZE=3][FONT=arial black][SIZE=5]**[FONT=arial][SIZE=3]GIT[/SIZE][/FONT]**
[SIZE=2][FONT=arial]
Learn how to use it.  It won't be time wasted. It _*will*_ become your best-friend and at some point, it will probably become a sysadmin life-saver ![/FONT][/SIZE]
[/SIZE][/FONT][/SIZE]
Git repo on /etc for example.  Lovely way to track-changes on configs.  :D

P.S. Once you're done learning GIT, learn TMUX, it's almost as important as GIT !  If you don't know why TMUX is important, trust me, you'll find out soon enough !

---

### Post by bob_jones2 on 2016-05-17
> **ian-weisser said:**
> 
Advice: Use SSH keys from the start. Take the time and learn how to use ssh properly. Never start with passwords, thinking "I'll change over to keys soon." You won't, and your server will be quickly compromised.

Advice: If you run an internet-facing server, you need *real* security habits. Habits like regularly checking logs, regularly checking your listening ports, regularly checking for unusual network activity, and regularly-checking the unattended-upgrades log for each VM. Else your compromised machine will, unbeknownst to you, become part of the problem.

I also second these two excellent pieces of advice, infact those points are so important I'll put them in stronger terms : 

SSH with passwords is only for the lazy, and if you can't be bothered with security habits (or are one of those people who think "security can wait, let's just get this running ASAP") then you have no business running a server on today's internet !

  You can do SSH Key-based authentication on ALL modern operating systems,  INCLUDING those running on smartphones and tablets. So there's NO  excuse for not setting it up and turning off passwords.

Got the message ? :D

Bonus hint....Key things to say "no" to in your SSH config:

PasswordAuthentication no
ChallengeResponseAuthentication no
UseDNS no
PermitRootLogin no

You may also wish to RTFM for sshd_config on MACs,Ciphers,ClientAliveInterval, ClientAliveCountMax

---


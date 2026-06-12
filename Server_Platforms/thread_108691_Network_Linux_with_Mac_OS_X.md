---
title: "Network Linux with Mac OS X"
date: 2005-12-26
forum: Server Platforms
---

### Post by trihai44100 on 2005-12-26
Hi I would like to get Linux to do three tasks. I'm thinking of using Ubuntu for doing these things, but if another distribution would be easier, please tell me.

1.
I want to network a Linux machine to my other computers so I can use it to store files. My other computers are running OS X and Windows XP. I really only need to network it with the OS X computer, but XP would be a plus. I have no idea how to setup computer networks. All I'm looking for is the easiest way to be able to mount the Linux computer on my Powerbook to share files between the two. My Powerbook is connected to a wireless router if that matters.

2.
I don't want to run the Linux computer with a monitor, keyboard, etc. Is there a way that I can access it and manage it from my Powerbook? I've read about VNC and think that it would be a good way to accomplish this. So I think what I need to do is set up the computer so that it starts a VNC server on startup. When I've used Linux previously, a password needs to be entered to log in. I assume it can be set so that it automatically logs in without the password. But the other thing I'm worried about is that having it log in by itself may be insecure, but as I don't have a monitor/keyboard, how do enter the password when I turn the computer on?

3.
I want to know how to setup the Linux machine as an FTP server so that I can make user accounts and connect to it from other machines.

If anyone is able to help explain any of these topics to me or give me links in the right direction to accomplish these tasks completely or partially, please do so and thank you.

---

### Post by ingo on 2005-12-28
on 1: google "samba" - it is ideal for mixed networks, plenty of documentation, make sure you have samba server installed

on 2: sounds good, yes, but haven't managed to get it to work yet. If you make any progress, please let us know :)

on 3: if you are on an internal network samba will suffice. if you want to connect from the internet you will need apache. Again, google "apache" and similar to samba you will come across loads of info. make sure you have the package installed.

Have fun fiddling!

---

### Post by TopDog on 2006-01-01
Read the [www.UbuntuGuide.org](www.UbuntuGuide.org) on how to install Samba and ProFTPd.

Then if you want Samba to be competely open (no access-control), I just answered this in another tread, search the forum.

For remote control, you can use VNC (sudo apt-get vnc-server), but that is very slow, learn your way around BASH and install OpenSSH, then you can connect via SSH. Very practical and very fast!

See my attached picture with both Samba and SSH in action on my Mac.

---

### Post by xenonite on 2006-01-02
this should be what you want for the vnc server. for mac os x, I would reccomend "Chicken of the VNC"

[http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc](http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc)

---

### Post by moon2js on 2006-01-05
I've used guides to setup samba, but the ubuntu guide and the custimization guides aren't exactly very robust. They don't tell me what I'm doing so when things go wrong, I have no idea where to look.

I'm also trying to make an Ubuntu system into a samba server for a Mac OS X laptop (and possibly in the future an XP laptop). For the longest time, the Ubuntu samba system wouldn't show up in the Network finder (on the Mac). Now that it does, Finder becomes unresponsive whenever I try to connect to the ubuntu samba system and I have to force quit.

Actually, the ubuntu system never showed up on the Network finder until after my roommate's Win XP laptop entered the mix. I don't know why his computer, which doesn't do anything to the other computers on the network, somehow made the ubuntu machine show up on the network.

I also noticed that the router lists all the computers on the DHCP client table by host name (the Mac, the XP PC), but it doesn't list the Ubuntu system by hostname, only by IP address. Is this a factor in or symptom of why I can't find things on the network?

Under System / Administration / Networking and under the General tab, the only things I have to fiddle with are Hostname and Domain name (the latter of which I don't use because it's just a private LAN). On one of the [guides]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29"), they speak of a Windows networking section on this tab that I don't have.

I'm a bit clueless about Windows networking and I have never been able to get it right even when using Windows machines (maybe it's because I never have a copy of XP Pro). If Windows networking requires any kind of admin or name servers, I'd like the ubuntu machine to do that and not let everything rely on an XP laptop that occasionally enters the mix.

Also, does anyone know if there are any known issues with Tiger communicating with Samba/Linux? As far as I know, I thought Tiger was using samba.

---

### Post by deNoobius on 2006-01-05
cancel me

---

### Post by moon2js on 2006-01-07
Update for me:

I have one partition for Breezy and one for Hoary. I cannot for the life of me get my OSX to connect to the Breezy Samba. In fact, the Finder locksup and I have to force quit.

Hoary, however, works beautifully.

I would rather use Breezy for a number of reasons, but Hoary works and samba is a crucial function for this machine. Both were fresh installs and the exact same Samba installation as per guides. They are setup exactly the same on independent partitions, but one works, one doesn't.

I haven't tried using Windows, but I have a feeling that an XP client will work with both. Did I read somewhere that there is a problem with OSX and samba?

Anyone else experience this or have any advice?

---

### Post by TopDog on 2006-01-07
Come to think of it my server runs Hoary... I have a Breezy installed at work. I can check it out next week.

---

### Post by moon2js on 2006-01-11
According to [this older thread]("http://ubuntuforums.org/showthread.php?t=82039&highlight=mac+samba"):

[QUOTE=evil-boweevil]There is a problem with the version of samba included in Ubuntu.  You will not be able to connect to a shared folder from Tiger.  You need to upgrade it to 3.0.20.  I did that by adding a debian testing repository to aptitude and then upgraded samba to 3.0.20.  Works great now.  I'm not sure about PPC specific repositories though.[/QUOTE]

So, as I understand it, Breezy's samba doesn't play well with OS X's samba? I'm fully updated and it still doesn't work so is it safe to assume that this isn't security related and won't be fixed?

Can anyone explain to me how I update samba to work better with OS X clients without mucking around too much or breaking anything as I'm like a third-year newbie and I don't like to mess with things I don't understand.

To any OS X users looking at this thread, I've found that you can access the Ubuntu samba server by using the Finder's Connect to Server option (smb://IP_of_ubuntu_machine/username), but trying to connect using the Network Finder GUI will just lockup Finder.

So technically, I can access samba stuff on Breezy from a Mac and maybe I shouldn't be rocking the boat by trying to make it perfect. Maybe it's not worth updating samba since it essentially works although it's not as pretty as it should be.

---

### Post by i_am_socket on 2006-01-11
I just went through all this last week.

#1 don't use the ubuntu included samba package. in fact, use synaptic to remove samba and samba-common completely.

#2 go to samba.org and download the latest stable version (3.0.21a right now) of the debian binaries (samba & samba-common)

#3 sudo dpkg -i samba-common_etc
     sudo dpkg -i samba_etc

#4 sudo smbpasswd -a (insert local username here)

#5 go share your folders!

The included version of samba doesn't work with OS 10.4.x, it works fine with 10.3 and earlier though.  

Good luck with that.

---


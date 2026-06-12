---
title: "HOWTO: No nonsense networking on Thunar"
date: 2011-12-05
forum: Tutorials
---

### Post by N00b-un-2 on 2011-12-05
when I first tried out XFCE back in the 7.10/8.04 days, I liked it but the lack of native network browsing was a deal breaker for me.  Almost four years later, I've come back to XFCE and found that networking does work finally!

By networking, I mean Thunar now supports dynamic Samba share browsing.  Of course you could always install samba, nfs, sftp or any other file sharing utility, manually mount your shares and then browse to them, but that's not always very efficient and can be a huge road block for newbies, as it requires knowledge of how networking functions, while networking just plain works on Windows and OSX.

As of Xubuntu 11.10, getting samba configured is fairly simple, and doesn't even require Gigolo (I don't know why they included that particular piece of software in this release of Xubuntu instead of just including a functioning samba install)

**1. Install the necessary packages:**

```
sudo apt-get install samba smbfs smbclient fusesmb gvfs-backends
```

**2. Configure your /etc/samba/smb.conf**

There are an infinite number of ways to set up your smb.conf and for the uninitiated, it can be a daunting task.  But don't worry, I will break it down as simply as I can.

First off, it seems that Thunar is pretty picky about a couple of settings.  In order to browse networked shares, you must make sure this line is in the [global] section of your smb.conf

```
name resolve order = bcast host lmhosts wins

```

A similar line already exists in the default smb.conf which is commented out with a ';'.  You can choose to uncomment and edit that line or simply add a new one.

Then the next major order of business is to set up one or more shares.  Set them up like this and you can't go wrong:
```

[home-ryan]  ## This is what the share will be called when you browse to it.
comment = Ryan's Home  ## This line is optional
path = /home/ryan  ##  This line dictates where the share is on your computer.  
browseable = yes  ## Self explanatory...
guest ok = yes  ## Once again, self explanatory...
create mask = 0755  ## allows read/write access to new files created within the directory
directory mask = 0755 ## allows read and write of existing files

```

Beyond that, you just need to make sure that all of your computers exist in the same workgroup.  Although it's not 100% necessary, it's the standard practice for a reason.  To do so, add or edit a line in the [global] section of your smb.conf

```
 workgroup = MSHOME 
```

Where MSHOME is the default for Windows networks.  Change it to whatever you decide to call your workgroup.

so in conclusion, here is a very simple yet functional, complete smb.conf that will get file sharing up and running.  Just tweak it to suit your particular machine.

```

[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share
name resolve order = bcast host lmhosts wins

[home-user]
comment = User Home
path = /home/user
public = yes
writable = yes
create mask = 0755
directory mask = 0755

```

---

### Post by N00b-un-2 on 2011-12-08
if this helps anyone I'd really appreciate feedback.  This setup worked on all of my computers but I'd like to hear how well it faired for other people.

---

### Post by nothingspecial on 2011-12-08
Thread moved to Tutorials & Tips.

---

### Post by dmizer on 2011-12-08
Is it necessary to configure a functioning samba server to enable samba browsing in Thunar?

---

### Post by N00b-un-2 on 2011-12-08
> Is it necessary to configure a functioning samba server to enable samba browsing in Thunar? 

Perhaps not, but why wouldn't you want bi-directional file sharing?  I have never once even considered setting up Samba **without** setting up each machine as sever & client.  On my home network I like to be able to access any file from any computer. I realize that this may pose a potential security risk, which is why I set up samba to only share files in $HOME.  If I need to edit a system file on my server for example, that's what ssh is for.  But SMB makes for easy dynamic file sharing at the user level.
I suppose you could just omit adding any shares to the smb.conf and just configure the global section as per my instructions.

---

### Post by dmizer on 2011-12-08
> **N00b-un-2 said:**
> Perhaps not, but why wouldn't you want bi-directional file sharing?  I have never once even considered setting up Samba **without** setting up each machine as sever & client.  On my home network I like to be able to access any file from any computer. I realize that this may pose a potential security risk, which is why I set up samba to only share files in $HOME.  If I need to edit a system file on my server for example, that's what ssh is for.  But SMB makes for easy dynamic file sharing at the user level.
I suppose you could just omit adding any shares to the smb.conf and just configure the global section as per my instructions.
There are a number of good reasons for not configuring every machine on your network as a server. First and foremost, it cuts down on unnecessary LAN traffic since samba is very noisy. Lots of smb traffic reduces file server performance and increases transfer speeds. It's also easier to administrate the security of one server rather than 3 or 4. You won't get caught with your samba open when you take your laptop to a wifi hotspot.

With only a few machines, there's usually no problem but it is something to consider.

BTW, I've been looking forward to native samba client support in Thunnar for a long time as well, I'll have to take a look now.

---

### Post by N00b-un-2 on 2011-12-08
three of the four computers on my network are hard wired, the other being my netbook.  I don't trust wifi hotspots as far as I can throw them so typical practice is to tether to my Android phone when I need internet away from home.  My phone is capable of connecting to 3G and wifi at the same time and tether to my computer via USB without exposing any of my computer's files.
!!IF!! someone were to hack me over wifi, they'd get my phone instead of my computer, which aside from my vcards would be essentially useless if the hacker were even smart enough to figure out that they were talking to a phone and not a computer.  Not saying it's impossible, just extremely unlikely.

---

### Post by dmizer on 2011-12-08
Again, hacking is not the only issue with enabling multiple samba servers. But I'm not really talking about your network anyway. I'm responding to this:

> **N00b-un-2 said:**
> if this helps anyone I'd really appreciate feedback.  This setup worked on all of my computers but I'd like to hear how well it faired for other people.

You asked for feedback. Essentially, my feed back is this: If you're giving configuration advice to others, it's important to consider how things work on networks other than your own. That's why I asked if it was necessary to configure a full samba server in order to browse samba shares with Thunar.

Sorry for not making myself more clear previously. :(

---

### Post by Morbius1 on 2011-12-08
You're missing a step.

The remote guest does not have permissions to write to the share despite specifying so in smb.conf. Samba cannot override Linux file permissions and unless you do something it's sitting there at 755. The remote user can access but read only. I suppose you could leave it at 755 and then control what subdirectories allow write access by changing them to 777 but if you actually want to create a share that everyone can access with write abilities then you might want to add a line to your share definition:

> [home-user]
comment = User Home
path = /home/user
public = yes
writable = yes
**[COLOR=Blue]force user = user[/COLOR]**
**[COLOR=Blue]#[/COLOR]**create mask = 0755
**[COLOR=Blue]#[/COLOR]**directory mask = 0755You will need to do something like that anyway. 

If bob creates a share as defined the way you had it and betty was able to add a file it will save with owner = nobody. bob isn't nobody so he will have read access only to the file on his own machine. "force user = bob" will make the file added by betty save with bob as owner.

To be honest creating a share - a guest share to boot - of ones own home directory gives me the willies.:wink:

BTW: 

*The smbfs package is a dummy package. It points to the new package: cifs-utils.
* Gigolo is a samba client package not a samba server package and it has a remarkable ability to auto mount samba shares if you use it a certain way.

---

### Post by N00b-un-2 on 2011-12-08
I was using $HOME as an example.  typically, I'll actually point my shares to Videos, Music, Pictures, etc.  I was just using HOME as an example.  On a small home network, I don't see the harm

---

### Post by N00b-un-2 on 2011-12-09
I appreciate all the feedback everyone.  I'm always glad to hear suggestions for how to make things more secure.  I just hope that someone can use what I did as a starting point to get native networking in thunar up.

---

### Post by N00b-un-2 on 2011-12-11
as of this morning my computers are all giving me a 'Failed to open "Windows Network".' error when I try to browse samba shares in Thunar.  I just ran updates yesterday so once again, running updates has broken Samba.  What is with the constant cat and mouse game of getting samba working?
I can still use gigolo to manually mount the shares by typing in the IP address of the computer I'm trying to access.  Typing in the address directly in Thunar does not work though eg; smb://192.168.1.10.

A Vista laptop I'm working on for a friend can not see my Linux samba shares either.  any ideas here?  I'm about to say screw samba and just use sftp exclusively because I'm getting sick of it breaking all the damn time

---

### Post by Morbius1 on 2011-12-11
You seem to be having problems at opposite ends of the spectrum:
> A Vista laptop I'm working on for a friend can not see my Linux samba shares either.

You might want to check to see if nmbd is running:
```
sudo service nmbd status
```
If it's not running start it:
```
sudo service nmbd start
```

Also, Assuming you have already done the following:

(1) Check your hostname length by typing:
```
hostname
```If it's 15 characters or less you are good to go. If it's more than that then you can add a parameter to the [global] section of smb.conf:
```
netbios name = something
```[COLOR=Blue]*Just make sure "something" is 15 characters or less in length.*[/COLOR]

(2) Change the order of name resolution by adding another line to the global section:
```
name resolve order = bcast host lmhosts wins
```If you have to do either of the above restart some services:
```
sudo service smbd restart
sudo service nmbd restart
```

Wait a few minutes - seriously - minutes then run the following command and see if the samba client on your machine can see the samba server on your machine:
```
smbtree
```> Typing in the address directly in Thunar does not work though eg; smb://192.168.1.10.That's another problem entirely however and one I don't have an explanation for at the moment.

---

### Post by N00b-un-2 on 2011-12-11
Nmbd is running.  my resolve order is as you put it. No computer on my network has a hostname longer than 12 characters.  smbtree reports no feedback.
typing in ip addresses in thunar allows me to access the shares.  typing in the hostnames on the vista computer allows me to browse the shares on the Linux machines.  So it seems to me that the updates broke samba.  I'm going to try downgrading samba to an older version.

---

### Post by N00b-un-2 on 2011-12-11
I can now confirm, downgrading samba and its dependencies restores network browsing.  I'm locking my samba packages in synaptic and filing a bug against samba.

---

### Post by N00b-un-2 on 2011-12-12
interestingly it turns out that when I downgraded samba and its dependencies, the packages smbclient and libsmbclient were uninstalled.  Following the reboot, thunar network browsing of samba shares was working, so I suppose it is safe to say yes, it is necessary to set up samba server in order browse network shares in thunar.  That is unless of course, the functionality is being provided by gvfs backend.  At this point what I thought I understood about samba has all been thrown out the window, and I'm sick of messing with it every other update to get it working again.

---


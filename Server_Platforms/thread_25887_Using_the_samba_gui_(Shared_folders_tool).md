---
title: "Using the samba gui (Shared folders tool)"
date: 2005-04-11
forum: Server Platforms
---

### Post by paulfox on 2005-04-11
I've added a share to my samba conf, but when i browse to the network place and open my machine hostname, that place is empty.
I've checked the smb.conf file, and it does have the entry:

[mysharedfolder]
path = /home/paul/SharedDocs
comment = Pauls shared documents
available = yes
browseable = yes
public = yes
writable = no

and i've restarted the samba service, but still no luck.
the samba logs give me some errors about /etc/printcap not being read, but i don't think thats the reason for not enabling the share. 
is there anything else i need to do for this to work?

thanks for any help!
paul.

---

### Post by localzuk on 2005-04-11
[QUOTE=paulfox]I've added a share to my samba conf, but when i browse to the network place and open my machine hostname, that place is empty.
I've checked the smb.conf file, and it does have the entry:

[mysharedfolder]
path = /home/paul/SharedDocs
comment = Pauls shared documents
available = yes
browseable = yes
public = yes
writable = no

and i've restarted the samba service, but still no luck.
the samba logs give me some errors about /etc/printcap not being read, but i don't think thats the reason for not enabling the share. 
is there anything else i need to do for this to work?

thanks for any help!
paul.[/QUOTE]
 run 'testparm' as root and see if it turns up any errors.

---

### Post by paulfox on 2005-04-11
testparm gave me an error about my share having a description whcih is longer than 12 chars, i changed it and now it shows up.
thanks a lot for the tip! :)

---

### Post by troyDoogle7 on 2006-04-21
I think something should really be done about configuring samba through a program.  This command line stuff is junk!  

We can't expect it to take off when you have to explain to someone that to share files on their network they have to resort to this long procedure.  Kubuntu has a proper gui setup... why not ubuntu?

---

### Post by brentoboy on 2006-04-21
troy,

what is the name of the gui setup app in kubuntu?
certainly it could be added via synaptic and then used from ubuntu -- I did that with the printer config app when the gnome one wasnt measuring up for me.

---

### Post by stengah on 2006-04-22
My problem resembles Paul's i.e. I cannot access the shared folder on my Samba server. However, unfortunately I cannot resolve it as easily. 

1. I make sure the server is running by entering: 
sudo /etc/init.d/samba start
2. Afterwards I try to connect through my network client with nautilus (Places > Networks) from my Ubutu breezy OS on my laptop. 
3. I'm prompted for a user pw and and after logging I get a 'windows-network' icon. When clicking I get to a 'mshome' icon.
4. When I click the 'mshome' network icon I get the same error as Paul it seems i.e. 'The contents of the folder cannot be displayed.'

I've set up users on the server acc. to the guide link below the quote. I do get the option of accessing a MSHOME server, and as I run my login pw (acc. to the samba user setup) I gain access but a popup tells me that   

When I run testparm I don't get no errors. I've listed my smb.conf file sontents below:

> #======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[public]
    comment = Public Folder 
    path = /home/public 
    public = yes 
    writable = yes
    create mask = 0777 
    directory mask = 0777 
    force user = nobody 
    force group = nogroup

I'm new to ubuntu and I've searched the forums for an answer with no luck. I really don't know what to do. I've followed this guide when installing samba: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server")

I'm really turning desperate here due to my lack of insight - been spending the whole day trying to figure this out - any help would be really appreciated!!!

---

### Post by troyDoogle7 on 2006-04-22
Hey guys,
In Kubuntu there is a samba configuration in the system wizard.  I looked at my old server and it had kubuntu on it, which I used to set it up....which is why I thought there was a gui tool to do it.  (not in ubuntu though you need to mess around with the config files.

I posted a bug about it and would be great if you guys could lend your support:

[https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/40556](https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/40556)

Regarding the network share issue-- if you change the share security type from user to share (and remove the ";") from the beginning of the line, should sort it out!

eg 

security=share

Please help to encourage ubuntu to sort this mess of a system out so that noobs don't get fed up with the system.  Its a fundamental basic feature and a must have for most people with more than one computer(pretty much everyone nowadays!)

---

### Post by stengah on 2006-04-23
Troy: what line is it exactly that you are referring to?:confused:

---

### Post by troyDoogle7 on 2006-04-23
there is a line in smb.conf that says security=user, change it to security=share and delete the ";" before it(if its there)

---

### Post by stengah on 2006-04-23
Ahh.. okay. I've changed it... but when I (acc. to the guide from my link above) try to run the restart command I get this:

> mads@ubuntu-homeserver:~$ sudo testparm sudo /etc/init.d/samba restart
Load smb config files from sudo
params.c:OpenConfFile() - Unable to open configuration file "sudo":
        No such file or directory
Error loading services.
mads@ubuntu-homeserver:~$


Any ideas? 

EDIT: Arrrgh... sorry! It's two separte commands ofcourse... just the syntax got me a bit confused. I'll get back to you as to whether this solves the problem. testparm reported no errors... that's a start I guess...

---

### Post by stengah on 2006-04-23
This is *****d up. When I try to access from my laptop I now get to the Windowsnetwork icon - clicking it just gives me.... absolutely nothing, nada, zip! Previously I at least got the MSHOME folder...

I am really like ](*,)  right now!

EDIT: when I from my laptop client try dropping a file into the empty window I'm told that this file already exists and whether I'd like to replace it... and the wierd part is that IT DOESN'T MATTER WHICH FILE I GRAB. What a loop...

Have I missed out on something... anything??!??

---

### Post by troyDoogle7 on 2006-04-23
nope just try to use only one sudo!

sudo testparm /etc/init.d/samba restart

---

### Post by troyDoogle7 on 2006-04-23
I think we need to start advocating a better gui for samba

---

### Post by stengah on 2006-04-23
Yeah, but I'm passed that point.:( 

Have restarted the server successfully. But the problem persists as explained above. This is quite a mess... don't really know where to end or begin....

---

### Post by troyDoogle7 on 2006-04-23
you can try use the unc path to see the ubuntu
press start run 

\\ubuntu (if thats the name of your ubuntu computer
or 
\\ubuntu ip address eg \\192.168.0.4

do you have your firewall switched off?

---

### Post by stengah on 2006-04-23
Troy: Yeah... I did make a follow-up to the bugfile you linked to previusly in this thread as u suggested to support this issue. 

As the Samba server seems to be working fine I think it's the client side that is somewhat confusing... have I missed out on some essential configuration anywhere - be it the client or serverside...?

My client/server network is working fine - meaning it's not like there's any problems  in terms of connections as far as I can tell. I can ping those machines of mine... however I'm wondering whether this might be an issue to do with me running a network where the server IP changes?

I wonder if anybody have had similar issues... ??

---

### Post by stengah on 2006-04-23
I'm running only ubuntu - no windows machines! The reson I'm want to use Samba is that I intend to emulate Windows with vmware and use Samba as a bridge to share files...

---

### Post by stengah on 2006-04-23
Consequently, the client issue is within ubuntu.... however As far as my research has shown me it ought not being a problem sharing between linux machines using Samba - though I'm aware many advise NFS -  again, the reason why this is not relevant to me is the emulation thing mentioned above....

---

### Post by stengah on 2006-04-23
To answer your questions more specifcally:

1: I can ping the machines- however the server is given an IP (192.168.1.4/192.168.1.5) by the network router. Is this the problem maybe?
I cannot test anything on Windows as I'm not running Win.

2: I don't have a firewall on any of the machines.

---

### Post by brentoboy on 2006-04-26
I think troy is right.
We need to start advocating a better gui for samba.  I have yet to have a samba server setup for ubuntu without resorting to hit the config file, not even a basic: "just share this folder" type of setup.

A good samba gui could work like so:

first, select which "windows" you want to model:
Windows 95/98 - totally opened sharing, no user athentication
Windows NT/2000 - users must login
Windows domain server - users own their own files, and some users can access some shares... etc.

then it could ask:
what do you want to call this computer?
What is the workgroup / domain name?

the wizard would ask what folders you want to make available, and then some questions about printers etc.

finally, it would spit out a new smb.conf file, and restart smb

then it could offer to allow you to add/remove/edit samba users (or maybe this should be a different app altogether that gets launched after you create a new smb-conf)

after running the wizard, a windows box should be able to see the server and its shares without any more issues than they would have with a windows 2000 computer that they had selected to share a particular folder.

if it isnt that easy, then it isnt progress.
I really dont see why a clean python script couldnt do all those things with ease, but it would take some time to organize and design a really smooth logical step by step easy setup.

---

### Post by troyDoogle7 on 2006-04-26
@Brento boy: I couldn't agree with your more.  

Basically what Ubuntu needs, which I think you are alluding to is "Network Setup wizard" or even a network configuration window.  I don't see it as being a major problem to create.  Perhaps a Google Summer of code project candidate?

If there was anyway to move this forward or to bring it to the attention of relevant parties I would be happy to offer my support.   


Regarding sharing between ubuntu boxes- I can't help much as I only have one ubuntu box but apparently NFS is the way to go.   If it helps your ip addresses seem to be correct.

---

### Post by troyDoogle7 on 2006-04-26
Brento, I am putting your suggestion into the developer forum to see what they can come up with.  I would even be willing to contribute towards a bounty to see this done.  

Assuming that the upcoming network manager will not resolve this issue

---

### Post by Skerit on 2006-04-26
I just can't get my head around to why, WHYYYY, is there no "Add Samba User" dialog anywhere in ubuntu? Seems prety useless without it!

---

### Post by troyDoogle7 on 2006-04-26
Skerit, create a new thread and point us in the location--- eg post here if you would like an unbuntu network setup/config tool for samba. 

We need to start shouting louder than the crowd.

---

### Post by stengah on 2006-04-26
Yep! Please post a follow-up thread... as of right now we all seem to agree that the Samba GUI is somewhat a pitfall, so we need to point developer's attention to these issues for Ubuntu to gain wider appeal amongst networking 'human beings'... 

Personally setting up samba been nothing but trouble to me on the client side. It's up and running on my server configured to share with specified users, still this client GUI has gotten me nowhere near a share. ](*,)

Now, I certainly don't claim to be a walking knowledge lab in linux networking and chances are that I'm screwing myself here somehere along the line, but think it's sad for newbies trying to get things running - it just take some time to get there and sadly this reinforces the prejudice linux distros has to face in the real world where 80% of those regular humans out there want things working more or less out of the box.  

Anyway, s'ry for ranting! Make some noise for a better Samba GUI !!!:)

---

### Post by mci8406 on 2006-04-29
I too have had difficulty with samba.  I can edit the config files, but the fact of the matter is, I shouldnt have to for simple stuff.  The shares-admin in dapper allows for some very basic sharing, but is far from complete.

I'm thinking of working on a better samba tool as a SoC project.  I working on coming up with a list of needed/desired features and design specs.  Any suggestions would be appreciated.

---

### Post by troyDoogle7 on 2006-04-29
mci I will gladly help you draw up the specs.  I have started already. we can cross refernce.

---

### Post by mci8406 on 2006-04-29
That sounds good troy.  I found some specs on the wiki: [http://wiki.ubuntu.com/GUISambaConfigSpec]("http://wiki.ubuntu.com/GUISambaConfigSpec")

Here are some of the thoughts I had:
[LIST]
[*]Python + GTK for the interface
[*]Configure server/workstation Options
[LIST]
[*]hostname
[*]workgroup
[*]description
[*]advanced options
[LIST]
[*]master browser status
[*]other (theres quite a few advanced options that arent needed by everyone, but perhaps we should include the most common ones here)
[/LIST]
[*] (share) Security mode (maybe advanced option?)
[/LIST]
[*] Shares config
[LIST]
[*]path to share
[*]share name
[*]share description
[*]share security (opens as seperate dialog?)
[*]mount/exported shares
[/LIST]
[*]user account management
[/LIST]
I think that covers the features that most people need in a simple setup.
Nautilus seems to have decent samba client support (at least in dapper).  The browse list is empty for me, but if I type in the machine's name directly, it is accessible.  I haven't determined if that is a problem with the browsing interface in nautilus or with my system's config.  If anyone can tell me if it works, that would be great.

The idea of giving the user the option to select which version of windows (described in the wiki) they want samba to emulate is an interesting idea.  I dont think options described above should be replaced with it, but maybe allow for both?  Also, by giving that option some people may not necessarily pick the best option for their server; they may instead pick win95 emulation because they are used to that version or think they have to pick that to make it work with win95 clients.  Perhaps a better option might be to describe the user/share/domain options in detail, and give examples (i.e. share is like win95).

I'm not currently familar with the "usershare" support the wiki says is going to be in the new version of samba.  I was thinking that providing a mechanism to allow regular users to share directories that they own might be useful.  I also think that there should be an option for the sys. admin to enable/disable this option.

Any ideas or comments?

---

### Post by Ozitraveller on 2006-04-29
I was wonder whether this could be used to also configure other network share-able resources, i.e. printers? 

Just a thought.

---

### Post by chriscando on 2006-04-29
Stengah - if you want to share files between your host computer and your virtual machine (with vmware), just configure a shared file in vmware.  I'm assuming your going to run Windows from within Ubuntu.  If so you can do this by going to 'Edit virtual machine settings -> Options -> Shared folders'.  After this you can access your shared folders in Windows by going to \\.host\Shared Folders\

As for configuring samba, I wish it was as easy..

---

### Post by mci8406 on 2006-04-30
I thought about printers, but its not absolutely necessary, as samba can be configured (and is by default) to export all cups printers automatically.  I guess if you wanted to fine tune the access rights to the printer an interface to configure it explicitly in samba would be useful, but the printer would still probably exist in cups and would be accessible that way, so setting permissions in samba may not buy you an extra security.

---

### Post by troyDoogle7 on 2006-04-30
Hi guys since the initial discussion document has been put on the wiki, I thought it would be useful if we could discuss it here: [http://ubuntuforums.org/showthread.php?p=970170#post970170](http://ubuntuforums.org/showthread.php?p=970170#post970170)

so that all the feedback is in one place. 

I have added the link to the wiki.

---

### Post by troyDoogle7 on 2006-04-30
edit

---

### Post by stengah on 2006-04-30
Chris: thanks for the help. I'll try that.

Troy and mci: Great initiative. Please keep us informed on your progress! :)

---


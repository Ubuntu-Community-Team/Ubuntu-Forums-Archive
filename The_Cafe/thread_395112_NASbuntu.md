---
title: "NASbuntu"
date: 2007-03-27
forum: The Cafe
---

### Post by Darthbuntu on 2007-03-27
Hey all,

Dunno if this is the best place to post this, it is however just a thought.  Perhaps a brilliant group of Ubuntu junkies could make us up a form of NASbuntu?  I dont need all the goodies that go with Ubuntu Server Edition.  Just a simple NAS server will work.  Something easy on the hardware reqs, headless, light on resources.  Perhaps it will help us dig more of those old musty comps out of the garages and attics and closets and put them back into service?  Yes I know about FreeNAS,  I havent had much luck with it though as the performance isnt "there" for me,  file transfers are slow,  system sluggish sometimes.  In any case, its just a passing thought.....

---

### Post by SZF2001 on 2007-03-27
How about a NASAbuntu, with spaceships and aliens. That'll show 'em.

---

### Post by lyceum on 2007-03-27
> **SZF2001 said:**
> How about a NASAbuntu, with spaceships and aliens. That'll show 'em.

That sounds cool!

And isn't there already a server addition?

---

### Post by Darthbuntu on 2007-03-27
Yeah there is a server edition, I just thought something with a cool easy to use web interface for configs would be nice.  Very much like FreeNAS only ubuntu based.  :)

---

### Post by lyceum on 2007-03-27
> **Darthbuntu said:**
> Yeah there is a server edition, I just thought something with a cool easy to use web interface for configs would be nice.  Very much like FreeNAS only ubuntu based.  :)

That is cool. It maybe something to bring up with developers for Feisty +1

---

### Post by igadgetman on 2007-03-31
Thats exactly what I'm looking for at the moment. Running FreeNAS from an USB stick here, but having too much problems getting Feisty to do the FreeNAS thing. I need NFS for my TVIX and Freecom mediaplayer, but samba for my Windowsbox to map drives in the network. So I can unpack my mediafiles there and watch throughout the house on my TVIX 5000 and Freecom MG35 kit.

I want easy setup from extra SATA drives I want to put in this server. The ease of use of FreeNAS. But also a working GNOME/Beryl machine at the same time.

---

### Post by P86 on 2007-06-27
I'm getting slow performance out of FreeNAS as well. Has anyone tried OpenFiler? Looks a little intimidating to set up...

---

### Post by diskotek on 2007-06-27
> **SZF2001 said:**
> How about a NASAbuntu, with spaceships and aliens. That'll show 'em.
+1 :D

---

### Post by spockrock on 2007-06-27
why not use free nas, hopefully wihen free bsd hits, freenas will use the freebsd 7.0 kernel, which includes zfs....

---

### Post by P86 on 2007-06-28
Like we already stated, performance from FreeNAS is poor. A file copy that should only take a minute or two was taking me 15+ minutes. This could be a configuration error on my part, but I have heard other people having the same issue. Does anyone have any suggestions?

---

### Post by dca on 2007-06-28
Install 6.06LTS Server Ed and throw the webmin utility on top of that?

---

### Post by P86 on 2007-06-28
> **dca said:**
> Install 6.06LTS Server Ed and throw the webmin utility on top of that?

Thats a good suggestion, but definately overkill for what I am trying to accomplish. I need someting easy to setup and maintain.

---

### Post by P86 on 2007-06-29
Turns out FTP transfer speed is excellent. Its CIFS transfers that are slow. Any ideas?

---

### Post by devmnky on 2007-07-07
Why not do like dca said above and just throw on a simple install of 6.06LTS server or fiesty server, and then just use a simple samba share? They're both fairly easy to setup and maintain.

---

### Post by Callumgw on 2007-07-11
oh I wish.  I'm a Linux newb and have tried FreeNAs and SME Server, both weren't as good as I'd like.  So I thought I'd try Ubuntu 7.04 SE and "just chuck Samba" on it.  My home network is a simple windows workgroup without user authentication (ie no log-ons at each PC) and I'm have all sorts of funny things happen.  Like I create a folder on one windows PC and the other can't right to it (permissions issue), then go back to the first and seek to change the permissions, so de-select "read only" but when youcheck it again it's back on....and theres been other issues....so I'm not having much fun.....I haven't found an easy "how too" that worksso if one could be created that'd help heaps!.  I should note that some projects are underway ([www.ubuntuhomeserver.org](www.ubuntuhomeserver.org)), but there not going to be up and running for a little while (longer than I want).  So here's what I'd like:

some open folders (everyone, no log-in), mapped as drives
some restricted folders (groups and user access controlled)
No email control, 
no DNS, 
no domain controller, 
no apache for the www (maybe only local web pages)
back up facilities
ability to expand  disk space and maybe host NTFS
Web interface for management and users

Later i want to add:
P2P
media server

Here's what I reckon works so far...

Get latest Ubuntu server edition CD ([www.ubuntu.com](www.ubuntu.com))
Download ISO, burn to CD
Install Ubuntu (Server Edition 7.04) from CD and set up as "LAMP" server

login and get root priveledges
        *sudo bash*

Set up network address (if you don't want auto network config):
        Open /etc/network/interfaces
	*nano /etc/network/interfaces*
        Change:
                     # The primary network interface
                      auto eth0
                      iface eth0 inet dhcp
        to (adjust the addresses to suit your network config):
                    # The primary network interface
                     auto eth0
                     iface eth0 inet static
	     address 192.168.X.X
	     netmask 255.255.255.Z
	     gateway 192.168.X.Y
	     network 192.168.X.0
	     broadcast 192.168.X.255
Restart network
      */etc/init.d/networking restart*

Install ‘SSH’
     *apt-get install openssh-server*

RESTART SERVER (for network and ssh settings to take effect)
     *shutdown -r now*

Check for updates (this is more a best practice thing, from what i can tell). Edit  the /etc/apt/sources.list file
     nano /etc/apt/sources.list
comment out CD put a # infront of any

---

### Post by Callumgw on 2007-07-11
oh I wish.  I'm a Linux newb and have tried FreeNAs and SME Server, both weren't as good as I'd like.  So I thought I'd try Ubuntu 7.04 SE and "just chuck Samba" on it.  My home network is a simple windows workgroup without user authentication (ie no log-ons at each PC) and I'm have all sorts of funny things happen.  Like I create a folder on one windows PC and the other can't right to it (permissions issue), then go back to the first and seek to change the permissions, so de-select "read only" but when youcheck it again it's back on....and theres been other issues....so I'm not having much fun.....I haven't found an easy "how too" that worksso if one could be created that'd help heaps!.  I should note that some projects are underway ([www.ubuntuhomeserver.org](www.ubuntuhomeserver.org)), but there not going to be up and running for a little while (longer than I want).  So here's what I'd like:

some open folders (everyone, no log-in), mapped as drives
some restricted folders (groups and user access controlled)
printserving (printer connected to server and requested/shared by Windows machines)
No email control, 
no DNS, 
no domain controller, 
no apache for the www (maybe only local web pages)
back up facilities
ability to expand  disk space and maybe host NTFS
Web interface for management and users

Later i want to add:
P2P
media server

Here's what I reckon works so far...[anything in red and with ??? I'm unsure about]

Get latest Ubuntu server edition CD ([www.ubuntu.com](www.ubuntu.com))
Download ISO, burn to CD
Install Ubuntu (Server Edition 7.04) from CD and set up as "LAMP" server

login and get root priveledges
        *sudo bash*

Set up network address (if you don't want auto network config):
        Open /etc/network/interfaces
	*nano /etc/network/interfaces*
        Change:
                     # The primary network interface
                      auto eth0
                      iface eth0 inet dhcp
        to (adjust the addresses to suit your network config):
                    # The primary network interface
                     auto eth0
                     iface eth0 inet static
	     address 192.168.X.X
	     netmask 255.255.255.Z
	     gateway 192.168.X.Y
	     network 192.168.X.0
	     broadcast 192.168.X.255
Restart network
      */etc/init.d/networking restart*

Install &#8216;SSH&#8217;
     *apt-get install openssh-server*

RESTART SERVER (for network and ssh settings to take effect)
     *shutdown -r now*

Check for updates (this is more a best practice thing, from what i can tell). Edit  the /etc/apt/sources.list file
     *nano /etc/apt/sources.list*
comment out CD by putting a # infront of any line that starts:
        deb cdrom: [Ubuntu&#8230;&#8230;.
Add:
        deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
Run the update and upgrade:
    [I]apt-get update
    apt-get upgrade[/I]


[COLOR="Red"]???install quota???? apt-get install quota[/COLOR]

Install &#8216;SAMBA&#8217;
    *apt-get install samba samba-common*
    *[COLOR="red"]??????sudo apt-get install smbfs[/COLOR]*

[COLOR="red"]????Install SAMBA Client
    *apt-get install smbclient*[/COLOR]


Install &#8216;WEBMIN&#8217;
    *apt-get install webmin*

Install &#8216;USERMIN&#8217;: In Webmin / Webmin Menu / Usermin / Install

[COLOR="red"]?????? do I need OpenLDAP, or LDAP client, or JAVA JRE ????????

????? what is create mask = 0777 and directory mask = 0777 , what do other numbers mean????

??? Do I need CUPS ????

??? Anything else?????[/COLOR]

so any assitance greatly accepted, if you want to turn this into a wiki, great!

C

---

### Post by Callumgw on 2007-07-11
Last night I set up these two shares:

[public_RO]
  comment = Public Folder
  path = /test/public_RO
  public = yes
  writable = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[public_RR]
  comment = Public Folder
  path = /test/public_RR
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

The PC's needed to be logged in to MAP drives to them and then were able to function properly.  If the PC was shut down it again required a login to see them, even though they are both PUBLIC.  In the Samba File under the GLOBAL settings:
;  security = user

which I believe is commented out, so not effective [whats the default if security not set in the file?]. If this is changed to 
security = share

Or should I place a security declaration in each share?

C

---

### Post by P86 on 2007-07-13
Because this thread is in "Community Cafe" it may not be getting noticed by those who can help. You may want to try opening a new post in "Networking & Wireless".

Also, on a side note I would like to add that I resolved my FreeNAS issue. Turns out the file I was copying back and forth on the FreeNAS box was corrupt! Now that I have deleted that file, all is running well.

Callumgw, you may want to give FreeNAS another try. I followed the installation instructions at [http://www.howtoforge.com/network_attached_storage_with_freenas](http://www.howtoforge.com/network_attached_storage_with_freenas) and I had FreeNAS up and running in 15 minutes.

---


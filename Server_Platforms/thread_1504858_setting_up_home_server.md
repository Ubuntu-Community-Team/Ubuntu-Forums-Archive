---
title: "setting up home server"
date: 2010-06-08
forum: Server Platforms
---

### Post by terry_gardener on 2010-06-08
hello 

i am wanting to setup a file server,for backups from desktop and act like server for my xbmc media center. 

setup i would like.

ubuntu 10.04 LTS server.
openssh server 
samba 
and ability to add external storage USB-HDD 
dhcp is fine since i can setup the router to assign the same ip address to server all the time. 

do anyone know where i can find a how to guide for this, easy one since i have never down this before.

---

### Post by Neezer on 2010-06-08
How familiar are you with CLI? If you aren't comfortable with it, you might want to just install the desktop version and install openssh.

If you are comfortable with the command line, then just go with the server install. 

I know that I ran into problems with Mediatomb and my PS3 before I set my server to static IP. It is really easy to set up actually...


```

sudo nano /etc/network/interfaces

```


find where you eth0 is. It will look something like:

```

auto eth0
iface eth0 inet dhcp

```

That means you'll be in dhcp mode. To get to static mode replace the above with:

```

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

A few notes on the above configuration...It is wise to set the static address to something that is not in the range of the DHCP settings on your router. That way you are assured to not have any conflicts.

then do:
```

sudo /etc/init.d/networking restart

```

that will restart your networking and you should be good to go.

I know it is an extra step, but in the long run if you are going to have a server going, you can save a lot of headaches by setting it up as a static IP address.


I'm not familiar with SAMBA, but I just set up ssh with keys and use winscp from my windows machine to brows the files on my server. If you want to connect remotely just remember to setup key authentication. 

with either the server, or desktop install you should be able to plug in any usb drive for external storage. I have a 1TB external drive that I do backups to.

Hope this helped. Good luck and enjoy the trip!

---

### Post by arrrghhh on 2010-06-08
To configure Samba for your windows clients, I'd use Webmin.  Made Samba config easy peasy.

As for a streaming media server, I wasn't such a fan of Mediatomb.  I just couldn't get it to transcode files correctly, although if my PS3 played the file natively I never had an issue with Mediatomb.

So I use PS3MediaServer.  It works for the xBox as well, but unfortunately the xBox does not use a standard DLNA implementation, so there's not any that really support it... maybe TVersity or twonky, not sure.

---

### Post by Neezer on 2010-06-08
If you need assistance with the SSH config, this should help

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

after you set it up, check out the /var/log/auth.log after about 24 hours and you'll be amazed at the number of failed login attempts. You might want to change the port from the default of port 22 to something else. I like 2222.

It is security by obscurity and in no way does it replace have a very strong password (or better yet, a key), but it will reduce the number of unauthorized login attempts dramatically.

---

### Post by terry_gardener on 2010-06-08
with regard to the media server i dont need anything fancy just shared drives/folders and xbmc will read the shared folders and stream the file directly to the TV (HTPC think this is the term). 

i have setup ssh before and samba but using the desktop version as that is how i have it at the moment but would like server so my desktop doesn't have to be on when wanting to watch file on big tv.

so just need server with ssh and samba with shared folders and be able to automount and use external usb HDD. 

i am comfortable using the cli but no expert and i have changed config files before the aid of how to's

---

### Post by arrrghhh on 2010-06-08
You should be fine then.  Dig in, let us know if you have issues.

---

### Post by spynappels on 2010-06-10
> **terry_gardener said:**
> with regard to the media server i dont need anything fancy just shared drives/folders and xbmc will read the shared folders and stream the file directly to the TV (HTPC think this is the term). 


This will work, but I found that installing a DLNA server makes playback better, especially with high bitrate video. Have a look at miniDLNA for the DLNA streaming server, it is ultra easy to set up and try.

---

### Post by terry_gardener on 2010-06-10
setup server using the guide from the following site.

[http://www.badgerbait.net/linux/ubuntu-10-04-server-lucid-print-and-file-server-for-home-network]("http://www.badgerbait.net/linux/ubuntu-10-04-server-lucid-print-and-file-server-for-home-network")

everything seems to be working ok except for one thing i can only connect to it using ip address and unable to connect via hostname ie ubuntu-server so unable to browse using the nautilus-network and clicking ubuntu-server. i have to goto places-connect to server, select windows share and type in ip address and the folder i want to connect to, this way works fine. 

i have setup ufw the same as in the link also.

not really bothered about this but would be nice.

---

### Post by arrrghhh on 2010-06-10
So you want to use DNS?  You can either setup hosts files or use avahi...

---

### Post by terry_gardener on 2010-06-10
is it easy to setup the host files. 

does the server to be logged into a user to be able to access it. if so how do you autologin a user at boot up

---

### Post by arrrghhh on 2010-06-10
Most servers are configured to be 'userless' in the sense that all the services you want to be running DO NOT need a user to login.  That's how my server is - everything is in /etc/init.d so when my server is rebooted I don't have to do anything - all the services just come up on their own, without any user intervention.

Host files are very easy to setup.  Just depends on the client - if you find yourself setting up lots of machines with a custom hosts, it may be beneficial to look into running your own DNS server.  That way clients get the DNS info from DHCP, and all the stuff that you would normally have to put in a custom hosts file is polled automatically thru the DNS server.

I believe the hosts file in Ubuntu is just /etc/hosts, whether server or client.  In Windows it's in the c:\windows\system32\drivers\etc\hosts I believe.

---

### Post by terry_gardener on 2010-06-11
thanks for the replies, i initially thought that you needed to be logged in for it to work properly because i turned it on without monitor etc couldn't do anything but that was because it didn't boot properly. 

it is working fine now.

---


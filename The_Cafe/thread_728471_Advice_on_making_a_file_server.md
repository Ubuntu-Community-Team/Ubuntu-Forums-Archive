---
title: "Advice on making a file server"
date: 2008-03-18
forum: The Cafe
---

### Post by amazingtaters on 2008-03-18
So, my friend and I (I just recently got him to switch to Ubuntu via gentle prodding) want to set up a file server that we, and a select number of friends, can use while at school. Basically we want to build a box that will house a veritable cornucopia of files for our circle of friends to share. We all already share music and whatnot, but now the two of us want to streamline the process and make things more accessible and quicker. So, to get to the point, what OS would you all recommend for this endeavour. I was thinking of using Ubuntu Server, but figured I'd get some advice about whether there was something better to use. I'd like there to be a gui included, since neither of us are really hardcore into the terminal and are both relatively new (within the first year) to linux.

---

### Post by fedex1993 on 2008-03-18
Ubuntu server is okay i use it sometimes here and there but had always run into problems with permissions and what not. Right now i am working on getting my file server back up with a nice OS. I am thinking of using debian stable, centos, fedora, or openbsd. I still ahve yet to learn openbsd and centos, but use to debian and fedora. I still havnt figured out how to setup samba up correctly but i know NFS really well and how to setup. I would recommend using two to 101023010321 hard drives sort of hard to setup using one hard drive and also if you run it in raid and one ahrd drive fails plug it in and it saves in two places.

---

### Post by freebeer on 2008-03-18
Use the OS you're familiar with -- Ubuntu Desktop.  You can do all the sharing you want with that.  Or you can install Ubuntu Server, then add the desktop.

---

### Post by -gabe-noob- on 2008-03-18
an unrelated post:

Your avatar reminds me of a high school mascot in my area for a private school 

Come to think of it one of the kids who WENT their introduced me to Ubuntu heh...

---

### Post by Slingshot on 2008-03-19
I setup a web testing server using Clark connect running on a old 400mhz celeron with 194mb ram two 20gig HDD running in software raid. Was only meant to be used for a short time but its run so well i decide to leave it. CC has a simple web interface.

---

### Post by lespaul_rentals on 2008-03-19
Use vsftpd.  You can make an account for each friend and they can upload and share music on the FTP server.

---

### Post by igknighted on 2008-03-19
If this is accessible to the internet as a whole, look into an FTP server, not a file server.  If this is over a lan a file server would do nicely.

For FTP servers, vsftpd is my personal favorite, but proftpd is popular as well.

For file servers across the internet, you would likely have to have a VPN (virtual private network) setup as well.  I know this is possible, but I've never done it and couldn't begin to tell you how.

As for file servers across a local network... Samba is the easiest way to go.  Just set your server to use a workgroup that isn't otherwise in use, then it should be visible in your windows "network neighborhood" and "places -> network" or "smb://" in linux.

---

### Post by amazingtaters on 2008-03-19
It would be on a lan, the uni's network. We were contemplating doing FTP, especially so that we can give everyone an account and control access to the server. So, thanks for the suggestions, vsftpd sounds like something worth looking into.

---

### Post by lespaul_rentals on 2008-03-20
vsftpd is very easy to set up and a good learning experience at the same time.  It is the most simple and secure FTP server out there and will suit you perfectly.

So, basically, this is going to be a University darknet?  Be careful who you give access to, there are little birds who spread news very quickly around those parts.  ;)

---

### Post by notwen on 2008-03-20
If you're going w/ over the internet, I'd also recommend vsftp.  Over the LAN I would recommend NFS over Samba, but NFS would only work if both server and client are running the same OS.  I use NFS to stream video/audio to my laptop.  =]

[vsftpd setup guide]("http://ubuntuforums.org/showthread.php?t=518293")

---

### Post by amazingtaters on 2008-03-21
> **lespaul_rentals said:**
> vsftpd is very easy to set up and a good learning experience at the same time.  It is the most simple and secure FTP server out there and will suit you perfectly.

So, basically, this is going to be a University darknet?  Be careful who you give access to, there are little birds who spread news very quickly around those parts.  ;)

Yeah, our plan though is to put it up at random times, never the same time each week, and make everyone have passwords and whatnot to help control whois in on it.

---

### Post by lespaul_rentals on 2008-03-21
> **amazingtaters said:**
> Yeah, our plan though is to put it up at random times, never the same time each week, and make everyone have passwords and whatnot to help control whois in on it.

Okay, good idea.  I would also recommend that you make a Linux box to act as a router/firewall and set up all file servers behind it.  You should route all connections through the Linux box and only allow connections from trusted MAC addresses using iptables.  Also, you should block all outgoing protocols (by outgoing I mean from the darknet --> the WAN) other than FTP.  This will make it harder for people to probe the network and figure out what lies beyond.

If you're really paranoid, consider using SFTP.  It will encrypt all packets which means that passwords, file transfers...everything will be encrypted.  Another thing to think about is public keys; If you disable login and password and instead use RSA keys, it will make it harder for someone to bruteforce the logins.

---

### Post by amazingtaters on 2008-03-22
I would worry that much, but to be honest, no one I know on campus, including our tech people, would really know how to do that. Let's just say our IR dept. is a little behind...

---

### Post by kevdog on 2008-03-22
How about putting FreeNAS as the OS instead of Ubuntu -- thats what you want -- a network attached storage or file server.

---


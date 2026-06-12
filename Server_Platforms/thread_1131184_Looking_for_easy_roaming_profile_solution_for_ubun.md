---
title: "Looking for easy roaming profile solution for ubuntu"
date: 2009-04-20
forum: Server Platforms
---

### Post by whoop on 2009-04-20
Not sure where to post this but this looked like the best place for it.

I am wondering if there is an easy roaming profile solution for an all ubuntu (or all linux) local network.

I have read the Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller thread ([http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)) and I even got it up and running somewhere but it made me wonder, shouldn't this be a little bit easier/faster to setup? Aren't there solutions for this that are a little more prefab/ready-out-of-the-box.
The thread I mentioned above is one of the best ones out there and it's for version 7.10.
This feature seems very important to me to get (small) businesses running an all ubuntu (or linux) network.

So I seriously hope that I am missing something, and that someone can point me in the right direction.

---

### Post by whoop on 2009-04-24
Am I to believe that when I hear all the stories about schools, universities, government agencies, the military and businesses moving to linux the are not using roaming profiles or that they are using the Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller thread ([http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)) technique?

I find that hard to believe...

---

### Post by netztier on 2009-04-24
> **whoop said:**
> 
I am wondering if there is an easy roaming profile solution for an all ubuntu (or all linux) local network.


Well, the classic Unix-Style approach to "roaming profiles" is to have the user's home directories on a (typically NFS) file server, and they get mounted onto whichever machine the user logs in.

Since all user specific application configuration and all the default data directories reside in the home directory, you're set to go in no time. Problem: Laptops need some form of synchronisation between local homedirs and the ones on the server.

To use classic NFS, you'll need some mechanism to have UID and GID be identical for each on all systems across your domain - enter NIS (legacy) or LDAP.
 
And it might be advisable to have some form of control of what and which versions of software gets installed on the clients - sounds like a job for [Landscape]("http://www.canonical.com/projects/landscape").

As far as I know, Ubuntu offers no pre-bundled bolt-on package for your basic server installation - although I would consider it a good idea. Others have been thinking about it as well: [https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu)

And then there's even one or two Launchpad Blueprints about the ideas [https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-small-business-server-blueprint](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-small-business-server-blueprint) and [https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)

regards

Marc

---

### Post by capscrew on 2009-04-24
Roaming profiles is  Windows idea.  The solution **netztier** has provided is really all that is stable and available at this time.  For an out of the box solution look at [[COLOR="Green"]eBox[/COLOR]]("http://ebox-platform.com/") or [[COLOR="Blue"]Zivios[/COLOR]]("http://www.zivios.org/").  Neither of these are widely adopted yet.  

Two other sources of non-windows enterprise management are Sun (oops Oracle) and Novel (SUSE Linux).

**Edit:** Your observation about universities is sort of correct.  I for one have worked for a major university and we did configure all our own infrastructure services separately. We created our own scripts to automate some of the processes.  Originally it was NIS for centralized user management.  We later changed to LDAP.  We use NFS to manage over 5,000 user account home directories. Samba is a little lightweight for any large user base.

---

### Post by netztier on 2009-04-25
> **capscrew said:**
> For an out of the box solution look at [[COLOR="Green"]eBox[/COLOR]]("http://ebox-platform.com/") or [[COLOR="Blue"]Zivios[/COLOR]]("http://www.zivios.org/").

Univention's product range consisting of "Corporate Desktop", "Corporate Server" and "Groupware Server" might also be interesting: [http://www.univention.de/english.html](http://www.univention.de/english.html).  They're not based on Ubuntu but Debian, and the whole web page is - alas - only in German, it seems. :-/ Still, it might be worth a look and a download.

regards

Marc

---

### Post by HermanAB on 2009-04-25
Howdy,

The exact solution depends on how many roaming users you want to have.  If it is only a handful, then manually ensure that all users have the exact same username, password, UID and GID on all systems.  Then set up a NFS server on one machine and NFS mount all user home directories. 

For some NFS help, see this: [http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html) or do some Googling. It is very easy to get to work.

Once you have the manual method figure out, you can look at setting up a directory server, for cetralized control of user names, passwords and IDs.  You can then centrally manage tens of tousands of user accounts.  The way to do that is with NIS (RedHat Directory Server, Netscape Directory Server, Sun Yellow Pages, MS Active Directory - are all the same thing.).

If you want wizards to do all of the above in a few minutes at the click of a mouse, then you need to use Mandriva or Suse Linux.  If you want to do it the hard way in order to learn how it all really works, then Ubuntu is a good one, but it will keep you out of trouble for a week or two...

---

### Post by Meson on 2009-12-08
One piece that remains unanswered though, is how to efficiently handle situations where the NFS server is not available. This is important for roaming laptop users who might want their home directory cached on the system.

Of course there are security implications here, if multiple people log into the machine and have their data cached, pretty much anyone with physical access will be able to read/write all of the data. (Unless there is some sort of encryption layer...)

---

### Post by coutts99 on 2009-12-08
> **Meson said:**
> One piece that remains unanswered though, is how to efficiently handle situations where the NFS server is not available. This is important for roaming laptop users who might want their home directory cached on the system.

I sync /home/user to /local/home/user, /home/user gets NFS mounted to the users home directory when on the network. When not on the network, /home/user isn't mounted and is a just a symlink to /local/home/user.

Works for me.

---

### Post by BFG on 2010-01-05
I do this with autofs to load users' home directories.

The problem I get with this is if the NFS server reboots, all the clients hang.
I found it was also a good idea to have at least one user on each client with a local home folder.

---


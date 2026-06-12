---
title: "Setting up Samba Server"
date: 2009-03-24
forum: Server Platforms
---

### Post by matthewboh on 2009-03-24
I'm working with the local Boys and Girls Club, and they need a basic file sharing server.  What's the best way to go about this?  They really need some type of GUI to help manage the shares and groups.  Should I go ahead and install the entire LAMP stack then add Samba, LDAP and eBox or would it be easier to just use Webmin?  Any direction / help appreciated!

I'm fine with installing packages, can use the command line pretty well, but I'm looking for ease of use for the staff at the Boys and Girls Club - one guy is semi-techno savvy - the rest aren't.

---

### Post by bryanl on 2009-03-24
If all you need is shared data storage, look at getting a decent NAS.

If you are going to set up a dedicated box from existing parts, then [eBox](http://ebox-platform.com/) is probably a good bet. It's goal seems to be in line with your needs.

If you are going to share files on an existing machine, check the Add/Remove apps for [Gadmin](http://gadmintools.flippedweb.com/). 

If you want to build it yourself, then the server edition plus Lamp plus perhaps webmin might be a way to start but I think you'd have an easier time with eBox because that comes with everything you need and handles some of the interdependencies between services.

---

### Post by doogy2004 on 2009-03-24
FreeNAS is another good NAS option.

If you would like to use Ubuntu a good choice would be to install a desktop GUI and use the shared folders GUI for the users to create and maintain the shared folders on samba.

---

### Post by HermanAB on 2009-03-24
Unless your distribution has a good wizard for Samba (and Ubuntu doesn't) then it is actually easier to install Services for Unix (free download from Microsoft) on the Windows machines and use NFS as the server.

Soooo, unless you wish to switch to PCLinuxOS or Mandriva Linux, then you should seriously look at NFS, since it only needs ONE line of configuration, vs hundreds of lines for Samba.

[http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

Cheers,

Herman

---


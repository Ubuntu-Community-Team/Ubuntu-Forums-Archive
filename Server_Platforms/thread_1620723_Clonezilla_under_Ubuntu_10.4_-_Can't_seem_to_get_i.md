---
title: "Clonezilla under Ubuntu 10.4 - Can't seem to get it working..."
date: 2010-11-13
forum: Server Platforms
---

### Post by d_brennen on 2010-11-13
I'm something of a Linux noob I must say. I run a community centre and we've been donated 50 ex government PCs to use in basic computing classes. The machines are HP DC7600 CMT tower base units, all with Windows XP Pro license stickers and blank hard drives obviously. Would anyone be as kind as to help me set up a Ubuntu machine to clone Windows XP Pro onto a load of identical machines?

I could install all of them from disk and install drivers from pendrive but that would take forever! I like the idea of seting one up as I like it and cloning it across the LAN. Would save a massive amount of downloading updates for each client too.

So far I've followed this guide: [http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/](http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/)

I can only get as far as stating up the drbl service (if that is the correct term?) but the terminal says something along the lines of "unknown command"

So far I have one fully built base unit to use as the image, one running Ubuntu 10.4 and a 16 port switch (so I can clone 14 at a time?)

I would be very greatful if someone could break the instructions down to bite size noob chunks for me :P

---

### Post by CharlesA on 2010-11-13
If the machines are identical, with a different CoA on each I guess you could install XP on one machine and then clone it to the other machines, but you'd have to create a new SID and product key on each machine.

You can check the product key by using this: [http://www.microsoft.com/genuine/selfhelp/XPPkuinst.aspx](http://www.microsoft.com/genuine/selfhelp/XPPkuinst.aspx)

I always thought you needed a unique SID, but according to [this]("http://blogs.technet.com/b/markrussinovich/archive/2009/11/03/3291024.aspx"), that's not really needed.

I've not really done large deployments of machines using Windows, but I've heard of sysprep being used in that way.

I don't know the specifics of using sysprep other then you need a Windows Server based machine to do it with.

EDIT: [Here's some info]("http://technet.microsoft.com/en-us/library/bb457073.aspx") about sysprep.

---

### Post by d_brennen on 2010-11-15
> **CharlesA said:**
> If the machines are identical, with a different CoA on each I guess you could install XP on one machine and then clone it to the other machines, but you'd have to create a new SID and product key on each machine.
 
You can check the product key by using this: [http://www.microsoft.com/genuine/selfhelp/XPPkuinst.aspx](http://www.microsoft.com/genuine/selfhelp/XPPkuinst.aspx)
 
I always thought you needed a unique SID, but according to [this]("http://blogs.technet.com/b/markrussinovich/archive/2009/11/03/3291024.aspx"), that's not really needed.
 
I've not really done large deployments of machines using Windows, but I've heard of sysprep being used in that way.
 
I don't know the specifics of using sysprep other then you need a Windows Server based machine to do it with.
 
EDIT: [Here's some info]("http://technet.microsoft.com/en-us/library/bb457073.aspx") about sysprep.
 
Hi,
 
Thanks for the reply. I've used Sysprep in a Windows Server 2003 enviroment, and I'd rather not go there! I'd planned to use Microsoft's own Key Update Tool on each machine to keep the licensing right... Shame I just can't get Clonezilla to work in Multicast mode :( Might wipe the Ubuntu machine and start again if I get time tonight. This isn't even a paid job and it consumes all my time!
 
Plan B is to use the Conezilla Live CD to clone drives from one machine to the next ad nauseum. Still quicker than doing it the manual way

---

### Post by CharlesA on 2010-11-15
I just use a clonezilla livecd and either save/restore the image from a server (hurray for Samba) or just drag an external drive to each machine.

That would probably be the easiest way to do it.

---

### Post by d_brennen on 2010-11-15
> **CharlesA said:**
> I just use a clonezilla livecd and either save/restore the image from a server (hurray for Samba) or just drag an external drive to each machine.
 
That would probably be the easiest way to do it.
 
Hi Charles, I see, didn't know the Live cd alowed server functionallity. Will look into it

---

### Post by CharlesA on 2010-11-15
It'll let you store the image on a networked machine, it can use SSHFS, and Samba. NFS as well, but I am not 100% positive on it

---

### Post by d_brennen on 2010-11-15
> **CharlesA said:**
> It'll let you store the image on a networked machine, it can use SSHFS, and Samba. NFS as well, but I am not 100% positive on it

If I have a Ubuntu machine I can save an Image using the live cd from a prepared Windows box, via Samba, to the Ubuntu machine? 

Does Samba require any additional setup on Ubuntu? i.e. is the live cd Clonezilla likely to see that there is a Ubuntu machine on the local network running Samba? 

I'm guessing if I can manage to get a Ubuntu machine to host the image I can use Clonezilla live cds to pxe boot the rest of the bunch :)

Fun times ahead :P Sorry for all the questions Charles, probably trying to run before I can walk with Linux!

---

### Post by CharlesA on 2010-11-15
Only thing you'd have to set up would be a samba user and a share, the default smb.conf should work fine.

If you were going to do it that way, I'd go for using SSH instead, less config to do.

Doing it that way would mean you have the boot each one off a cd, since it's not a form of PXE booting.

---

### Post by d_brennen on 2010-11-15
> **CharlesA said:**
> Only thing you'd have to set up would be a samba user and a share, the default smb.conf should work fine.

If you were going to do it that way, I'd go for using SSH instead, less config to do.

Doing it that way would mean you have the boot each one off a cd, since it's not a form of PXE booting.

You're a legend. Now all I have to do is get it working...

TBH I'd love to just Linux them all and be done with it... But as is the way of the world we get funding to do classes based in Windows. Because the only way is the Microsoft way, of course :rolleyes::P

---

### Post by CharlesA on 2010-11-15
Best of luck. :)

---

### Post by elperrillo on 2010-12-06
Follow this article, it was done with Ubuntu 10.04

[http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/](http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/)


It worked for me and it is VERY complete, it even shows you how to create desktop shortcuts to start the server automatically in "multicasting" mode. 


Good Luck!

---


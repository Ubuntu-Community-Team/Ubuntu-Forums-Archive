---
title: "New program need access to port 69"
date: 2010-07-29
forum: Server Platforms
---

### Post by kfleten on 2010-07-29
I'm installing a new program wich requires access to port 69 on a server that already has tftpd installed. 
Is there a way of temporarily release port 69 for the new application, and afterwards switch between the two applications when needed ?

---

### Post by arrrghhh on 2010-07-29
> **kfleten said:**
> I'm installing a new program wich requires access to port 69 on a server that already has tftpd installed. 
Is there a way of temporarily release port 69 for the new application, and afterwards switch between the two applications when needed ?

Bad idea.  Why would this new application require access to a reserved port?  There's no way you can change the port on the new program?

---

### Post by kfleten on 2010-07-30
Beacause it has its own TFTP server built in, and this conflicts with the one previously installed. There is no option for disabling this during install (so installation fails). 
I have decided to only use the new one, and remove the old one - but: synaptic tells me tftpd* is not installed at all ? Wich other programs could possibly be using port 69 ? Is there any way of finding out wich program that uses specific ports ?

---

### Post by kfleten on 2010-07-30
Just found out that my problem is excatly the same as this:
[http://ubuntuforums.org/showthread.php?t=454848](http://ubuntuforums.org/showthread.php?t=454848)

I'm trying to install a Windows program with a tftp server in wine, and the installation fails because it says port 69 is in use - wich it is actually not if I ask netstat and lsof. How can I solve this ?

---

### Post by arrrghhh on 2010-07-30
> **kfleten said:**
> Just found out that my problem is excatly the same as this:
[http://ubuntuforums.org/showthread.php?t=454848](http://ubuntuforums.org/showthread.php?t=454848)

I'm trying to install a Windows program with a tftp server in wine, and the installation fails because it says port 69 is in use - wich it is actually not if I ask netstat and lsof. How can I solve this ?

Bleck.  I think you're not supposed to be in the server section for one.  What you're trying to do sounds like an atrocity...

Perhaps there's a limitation in WINE.  Can you install it in a VM?

---

### Post by kfleten on 2010-07-30
> **arrrghhh said:**
> Bleck.  I think you're not supposed to be in the server section for one.  What you're trying to do sounds like an atrocity...

Perhaps there's a limitation in WINE.  Can you install it in a VM?

Agree that this is the wrong section; I really *thaught* it was a server problem at first... Further investigation of the problem is now moved here: [http://ubuntuforums.org/showthread.php?t=1542487](http://ubuntuforums.org/showthread.php?t=1542487)

The windows executable is made for Win2003 server ONLY, and I dont have this available in any VM. Making such software work on ANY Linux platform is fare away from atrocity ;)

---

### Post by arrrghhh on 2010-07-30
Are you using that SolarWinds TFTP server?  Should I even ask why?  

SolarWinds... *shudders*

---

### Post by CharlesA on 2010-07-30
> **arrrghhh said:**
> Are you using that SolarWinds TFTP server?  Should I even ask why?  

SolarWinds... *shudders*

Ack!

If you can't get it working in WINE, why not just install another tftp server in a VM or something?

Not really sure why you'd use a tftp server either, ftp or sftp are better alternatives tbh.

---

### Post by arrrghhh on 2010-07-30
Well some things like PxE booting and transferring files to a Cisco router (just a couple of examples) require a TFTP server.

However, why you would be installing a SolarWinds TFTP server over something native is what is baffling me.

---

### Post by CharlesA on 2010-07-30
I've used tftp before, but I don't know why you'd use it outside of those applications.

I know I wouldn't have it running all the time.

---

### Post by arrrghhh on 2010-07-30
> **CharlesA said:**
> I've used tftp before, but I don't know why you'd use it outside of those applications.

I know I wouldn't have it running all the time.

Indeed.  I know I've only been forced to use TFTP in those two situations.  Can't think of any others where a TFTP server was useful/required.

---

### Post by kfleten on 2010-07-31
Lots of feedback here since yesterday - Very nice :-)
And now to the great unveiling of WHY I want this tftp server thing:
It's because I work with networking AND Linux professionaly. I use a lot of properitary Cisco software tools wich is only available for Windows, but I REFUSE to accept that I can not run any tool I like from my Ubuntu 10.04 laptop.
The special application I fight with in the moment is Cisco WCS. Its not primary a tftp server, but a tftp server is included.
Cisco WCS is available for two platforms ONLY: Windows 2003 server and Red Hat Linux Enterprise Server 5.X 32-bit. I do not intend to buy any of those. 2003 server can be emulated in wine ! I just need to get rid of that tftp failure...

---

### Post by CharlesA on 2010-07-31
Wow, that's a pain in the butt.

Could you try running a trial of Server 2003 x86 in a VM and do it that way?

---

### Post by kfleten on 2010-07-31
Probably - or preferably RedHat Enterprise server trial.
But that is just a temporarily solution. 

As stated in comment #6, since the solution might be a wine-issue, I moved this question to [http://ubuntuforums.org/showthread.php?t=1542487](http://ubuntuforums.org/showthread.php?t=1542487)

Last comment here is that I'm trying to make the .exe binary work with the setcap command:
sudo setcap cap_net_bind_service=69 WCS.exe

Unfortunately without any success yet...

---

### Post by CharlesA on 2010-07-31
I don't know what you can do. :(

The only thing I can suggest is to stop the linux tftp server that is running and try to see if the other one will run in Wine.

---

### Post by arrrghhh on 2010-07-31
I tftp IOS upgrades to all sorts of Cisco devices... any reason why you need this *special* tftp server?

Seems insane if  you ask me.  Never played with their wireless stuff tho.

---

### Post by kfleten on 2010-08-01
WCS is an exstensive management software suite for wireless networks. TFTP'ing firmware etc. to accesspoints is just a small part of it, wich I currently actually dont need at all. The problem is that I can not deselect this part during installation of the software suite...

---

### Post by arrrghhh on 2010-08-02
> **kfleten said:**
> The problem is that I can not deselect this part during installation of the software suite...

Ah... Have you tried it on a physical Win machine?  Perhaps WINE isn't playing nicely with the installer.

However, if the installer simply does not have the option perhaps talk to the manufacturer to see if you can download a special edition with the TFTP stuff removed...?

---


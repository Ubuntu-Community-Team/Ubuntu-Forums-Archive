---
title: "Samba Domain Controller"
date: 2011-04-13
forum: Server Platforms
---

### Post by Babyd3k on 2011-04-13
I have a small company network. It is mixed Win2k, WinXP home/pro, Vista, Win7, Linux environment of about 75 computers. Now we try to network this bouillabaisse with just windows workgroups because we are poor. Now the problem is this is just not working anymore. It never works right. Some computers can see others sometimes and not others. Some times a password that doesn't exist is demanded other times it isn't. A good and total mess. 

I am not allocated anything more then one broken server with no OS and no funds to fix this problem or I'd think about deploying an active directory setup which I am told solves all of my issues.

So my questions to the infinite knowledge of the forums is this.  

1. Will setting up what is listed as Samba NT4.0 style domain controller fixed these problems or at the very least a good chunk of them or is there something better I can make with linux that would solve my problem more efficiently? (Please omit ubuntu powered bomb to blow up this mess.) 

2. What sort of hardware is good for this? On a small network does this computer need allot of horse power if I set it up with a headless version of Ubuntu Server 10.04?

3. Does this add authentication to the network for network resources? 

Allot of time and Google hasn't really produced any results but I am freely willing to admit this maybe because I'm not sure what to ask.

Thanks in advance for everyone that helps.

---

### Post by HermanAB on 2011-04-13
Howdy,

Yes, if you install a WinNT style Active Directory server using Samba, then you will certainly have much less administrative trouble.  However, your WinXP Home machines won't work with that and Active Directory (in all its flavours) is not totally bug free either.

You will have much less trouble, if you reduce the sheer number of different versions of OS that you are running.  Try to change all  machines that don't absolutely need to run Windows to Linux and change the collection of Windows machines to one or two versions and things may become manageable again.

---

### Post by Babyd3k on 2011-04-13
Trust me if I could get all those random computers off the network I would have done it a long time ago. At least I have all the servers running Ubuntu, that's a small win. 

Now you said an NT style active directory set up. But according to Samaba they don't really have any of the features of ActiveDir just the domain controller. Is there a newer ver of samaba I'm not seeing or is it just a syntax thing.

Also, can anyone recommend a good howto on setting up a good samba directory server?

---

### Post by HermanAB on 2011-04-14
Howdy,

There are two types of Active Directory: The old NT style and the new 2003 style.  The old style is of course much simpler and the new style doesn't work with old versions of Windows and nothing works with Windows Home Edition.

Samba does the old NT style Active Directory, which is usually good enough.  There is a howto guide on the Samba web site.

So, you got to change the Windows Home Edition machines, whether you like it or not.  Try to put Linux on them.

With 75 machines, you will have endless trouble with viruses and malware.  The best control mechanism is to change your ethernet switches to Managed switches and enable Port to Port Security (port based VLANs), such that the Windows machines can only access the servers and printers and cannot access each other.  That will prevent malware from spreading through the whole company whenever someone installs a new smiley on their machine.

Also reconfigure the Windows XP machines so that each user has a separate admin account, to prevent the installation of malware.  These simple steps may restore some sanity to your network.

---

### Post by AmericanSkin on 2011-04-14
The easiest and most reliable option would be to run DCPROMO on a Windows server then install Likewise-Open on your Linux boxes, IMHO. 

(I prefer Linux over Windows on everything except DCs)

---

### Post by HermanAB on 2011-04-14
BTW, if you end up using MS Active Directory, there are a few tricks to keeping it working properly:
1. Install Windows server as a virtual machine on Linux.  Once you have it working, make a tar ball of the whole VM.
2. NEVER CHANGE OR MOVE ANY OBJECT!
3. Each time, before adding users or something, make a fresh tarball of the VM.  When it screws up (Not if - when!), untar the last working version.
4. NEVER CHANGE OR MOVE ANY OBJECT!
5. If you need to edit an object, for any reason whatsoever, make a new object and then delete the old object.
6. NEVER CHANGE OR MOVE ANY OBJECT!

Oh, did I mention that you must never change or move any object?

---

### Post by Vegan on 2011-04-14
XP home will connect fine to server 2000 and up using the old domain setup or the newer active directory.

SAMBA can be configured to integrate into Windows forest and it can act as a controller but you should use a Windows server to have proper management of policies etc.

I use SAMBA as a easy share for using the machines disk as a backup target when I am fixing machines.

---

### Post by brentini on 2011-04-15
[]("https://wiki.samba.org/index.php/Samba4")Check out ClearOS.

[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

Good luck and best regards,


Brentini

---


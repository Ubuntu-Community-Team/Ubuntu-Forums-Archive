---
title: "Samba to xp/vista; very slow"
date: 2007-10-07
forum: Server Platforms
---

### Post by Oki on 2007-10-07
Hi

I made a shared folder in Ubuntu, and Samba got installed. I can see the folder in windows xp and windows vista. I made username/password and it works fine from both. 

The problem is the speed, it is terrible slow, and I don't understand why. If I try to transfer the same file from windows to windows with msn, it will go much much faster. 

In vista I used it as a shared folder, in xp I mapped it as a drive. 

Do you have any advice why samba-windows dont go faster? And yes, no other applications where downloading when trying this.

---

### Post by HermanAB on 2007-10-07
Howdy,

There are various reasons for slow transfer speed.  You have to look at the protocol and see what is held up: DNS, WINS, Winbind, or SMB.  This can be daunting.

Firstly, run 'testparm' and look for syntax errors in your smb.conf, then use telnet to check whether all the required ports are open in your firewalls.

Here is an old guide: 
[http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

When all else fails, join the samba mailing list at samba.org.

'Hope that helps!

Herman

---

### Post by Oki on 2007-10-08
Hi, and thanks for your answer!

> then use telnet to check whether all the required ports are open in your firewalls.
Would it work if any of the needed was closed? I can send/receive, but it gos very slow.

I have searched with Google and can see that many others have the same problem; samba to vista gos slow. It looks like the latest version of Samba(3?), fix some problems(as I understand - caused by ms:mad:). How can I check witch version of Samba I have, and what version will come with latest Ubuntu? 

Thanks again :)

---

### Post by netlogic on 2007-10-08
Hi. Are you using smbfs or cifs?
Why don't you try with CIFS?

---

### Post by netlogic on 2007-10-08
I just remembered. Did you accidentally played with the TC settings in your firewall and limited the bandwidth?

---

### Post by Oki on 2007-10-08
Hi, and thanks for answering my post.

In the Shared Folders , under settings, I can see that I am using SMB(Windows networks). This is my first try with Ubuntu as server(or NAS), want to try it out before I try windows HS(I have only shared a folder from my main pc witch use Ubuntu, and tried with and without username/password). I have not changed the firewall settings(only installed the frontend for it). Right now it is so slow that it cant be used for music or movie:-/ 

I have read several others have problem with samba-vista, perhaps the upcoming update will fix it(?).

Is it possible to check if the firewall is making trouble?

Edit: SMB is the only option I get when sharing a folder from Nautilus/samba.

---

### Post by netlogic on 2007-10-08
are you mounting using cifs? everything is going cifs now. 
mount.cifs //sever/share1 /home/you/mnt/share1 -o username=you%password,uid=1000,gid=1000,debu
g=0,workgroup=yourdomainorworkgroup

---

### Post by netlogic on 2007-10-08
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
i don't know the detail of your setup, because you haven't described it to us, but if you are trying to setup a Linux Domain Samba file server, you should look at this doc. i believe the development for smbmount has slowed down. you should use cifs to mount. if you don't know what cifs does...
[http://www.samba.org/cifs/](http://www.samba.org/cifs/)

I hope it helps.

---

### Post by Oki on 2007-10-08
Lets start with a noob warning:confused:

I have Ubuntu on my main pc, and I want to try how well it works as a NAS(there are other pc in the house running xp and vista). If it works as I want I will build a new computer and install Ubuntu server on it, just to work on the LAN(to share data, be used as backup and so on). I also want to do more - but this is the first (baby) step. 

So I followed this guide; [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way)
 I have also made username/password for samba, and it works fine on xp/vista - but it is very slow.  I can transfer files faster with msn from xp-vista.  

Synaptic is telling me that samba and smbclient are installed(but not smbfs). But since I don't want to mount folders from windows I guess I don't need them.

---

### Post by netlogic on 2007-10-08
You must learn how to edit /etc/samba/smb.conf
If you spend a day reading the docs, you will understand. :)
I never recommend using the gnome samba share tool. 
If you don't have any desires to learn UNIX, download FREENAS at [http://www.freenas.org](http://www.freenas.org)
It is all web interface. It also has a nice auto-configuration.

---

### Post by Oki on 2007-10-08
FreeNAS is not recommended elsewhere since it is not stable(yet) for backups. FreeNAS is also using Samba to «speak» with Windows – so that would mean back to start. 

Reading about settings for one day, no thanks. Now I understand why WHS will sell! 

I am only hoping someone could give me any tip on what can be wrong with my settings, since it is so slow.

---

### Post by HermanAB on 2007-10-08
Samba is very complex.  It can be a client or a server for Windows 2000 and Windows 2003 domain controllers.  If you wish to use Samba, then you have to read the manual.

Otherwise, if you don't want to read the Samba manual, use NFS.  This is very easy to set up and Windows has support for NFS.

---

### Post by netlogic on 2007-10-08
> **Oki said:**
> FreeNAS is not recommended elsewhere since it is not stable(yet) for backups. FreeNAS is also using Samba to «speak» with Windows &#8211; so that would mean back to start. 

Reading about settings for one day, no thanks. Now I understand why WHS will sell! 

I am only hoping someone could give me any tip on what can be wrong with my settings, since it is so slow.

FreeBSD isn't stable for backup? hmm... That is the first I heard so far. Did you knew even MS used BSD flavor in the past?  Anyway, WHS might be a better option for you. I am sorry. I don't know what you want us to do. You want to drive, but you are saying your free car isn't good enough, so someone should drive it for you? We can't re-code your GNOME sharing tools for you to work exactly as you wanted. Maybe, you can join the Gnome forum and ask the developers. I don't think they hang out here. We are showing you a work around. You can do what you want by editing the configuration files and mount the drive using CIFS.  I don't know what answers you are seeking at this point. From what I know VISTA uses CIFS to mount.

---

### Post by Oki on 2007-10-08
> FreeBSD isn't stable for backup? hmm... That is the first I heard so far.  Personally I don't know, but I have read several different threads - both Danish and English, that version 0.6++ is not stable enough for important stuff(as backup). 

> You want to drive, but you are saying your **free** car isn't good enough
If you try and search with Google for "share folders with Ubuntu"(or in this forum) you will find a lot(with a big L) guides telling you that sharing folders from Ubuntu to Windows/Mac is easy and fast(thanks to samba). There is even video demos on the ubuntu screencast. I believed them, but understand its not realistic after all. 

> , so someone should drive it for you? 
Not at all. If you read my post (again?) you will see that I am only a user that have installed samba on Ubuntu, managed to share the folders with xp/vista, set up username and password; but don't get the speed that I need(and belived to get from different guides). There must be something wrong when it takes 20min ++ to transferee a file that only needs about 4min via msn on the same LAN. And this user is asking for advice; perhaps there is a well known mistake that caused this(?). Clearly, I am new to all this - so I made a shot and hoped for some help. 

> WHS might be a better option for you.
I guess so, I will try the trial version and see how it goes.

---

### Post by netlogic on 2007-10-08
> **Oki said:**
> 

If you try and search with Google for "share folders with Ubuntu"(or in this forum) you will find a lot(with a big L) guides telling you that sharing folders from Ubuntu to Windows/Mac is easy and fast(thanks to samba). There is even video demos on the ubuntu screencast. I believed them, but understand its not realistic after all. 

I guess so, I will try the trial version and see how it goes.

well, if you refused to use a text editor or terminal session, WSH is a better choice. it is almost impossible not to use them. If you want everything to be GUI, stick with Windows or OSX.  I doubt Solaris/Linux/BSD will ever be all GUI driven.

---

### Post by Oki on 2007-10-08
> well, if you refused to use a text editor or terminal session, WSH is a better choice. 
If your read my post (again?), you will learn that I have only said that sitting a hole day learning something I thought would be simple is not something I will do. 

> I doubt Solaris/Linux/BSD will ever be all GUI driven.
[http://www.ubuntuhomeserver.org/](http://www.ubuntuhomeserver.org/)

---

### Post by netlogic on 2007-10-08
hmm... you are a serious newbie with the hard edge, aren't you? listen... go install WSH. You will like it. I demoed, it is pretty darn easy.

---


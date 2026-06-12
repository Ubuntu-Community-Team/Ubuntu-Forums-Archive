---
title: "Samba 3, Windows 2003 ADS, Kerberos, and Brain Damage!"
date: 2005-06-07
forum: Server Platforms
---

### Post by Vache on 2005-06-07
I have a Windows 2003 server and an Ubuntu file server. Currently, all the clients (Windows XP) are in a workgroup configuration (read: non-domain). They have a username/pass to access the desktop and the Windows 2003 machine (SQL Server) in addition to a handfull of mapped drives on the Ubuntu file server that also needs a name and password - not only a linux account but a samba account as well. There are also a few shares on the Win2k3 server. As you can see, this is messy, insecure, and a pain in the rear to deal with.

What I want - cue the dreamy music! - is to migrate all the clients to the domain, make Samba be a member server in the domain - think ADS / Active Directory, and everything plays nice in a single sign on kind of way. I have experimented with kerberos + winbind + Samba 3 and I've only been able to get it to half work.

What I don't want is having to manage un/pw on both Windows and linux. I want winbind to do the work for me... So when a client logs on, he's automatically authenticated again Win2k3 and has access to the shares, plus netlogon scripts, etc.

Before I get a million "RTFM" responses, let me state that I have read just about everything I can get my hands on. I've read every configuration tutorial I could find and either it's not *exactly* what I want and not detailed enough to tell me how to tweak it, or it's what I want but it's using distro specific installs or setups (cough Red Hat cough).

FAXON-1.FAXON.LOCAL is the kerberos realm. I can join ADS using kinit, sync using winbind, but when I get to the point where I want to map drives onto the XP machine off the Samba machine, it dies an ugly death.

If someone could kindly show me the light, I would be very greatful :) I know I need krb5-user, winbind, and Samba. Do I need PAM at all? Anything specific I have to do on the Windows server side?

---

### Post by garyng on 2005-06-07
samba shouldn't be that distro specific.

All the samba setting is in /etc/samba/smb.conf.

You need to add winbind to /etc/nsswitch.conf and /etc/pam.d/* for authentication stuff.

Unfortunately, I don't have AD setup(I am gearing towards a samba only NT4 style domain) so don't know too much about that but as far as I know, you just give the right realm entry in smb.conf and that is all about it.

---

### Post by LordHunter317 on 2005-06-07
If your having a problem with a specific issue, you know, posting error messages and configuration is more useful than saying "it dies an ugly death".

Given what you've told me, I could think of a thousand things that could potentially be wrong.

---

### Post by Triton on 2005-06-28
[QUOTE=LordHunter317]If your having a problem with a specific issue, you know, posting error messages and configuration is more useful than saying "it dies an ugly death".

Given what you've told me, I could think of a thousand things that could potentially be wrong.[/QUOTE]

Well my problem is when I try to login with DOMAIN\user and password I get an invalid user.  I authenticate manually fine but when I log out and login again I get that error!

---

### Post by LordHunter317 on 2005-06-29
Exact commands you're running and their output would be helpful.  Also, are you running them on the XP box or the Linux box?  I'm assuming the XP box, are you running net use?  Did you accidently leave a connection as Guest or another use to the Samba box?  If so, that can cause authentication errors.

---

### Post by Triton on 2005-06-29
Here it goes...I have installed Kubuntu 5.04, Samba and all the other apps needed, including winbind.  I've been following the instruction on how to setup Samba as a domain member using winbind.  I get all the right results, connection and getend stuff.  I discovered that it all works fine for a terminal session based on configuring /etc/pam.d/login, but there is no clear instruction on how to setup for a graphical logon suchas kdm.  I guess i'm looking for those instructions.

 ](*,)

---

### Post by LordHunter317 on 2005-06-29
XDM/GDM/KDM use pam, just like login.  Setup their specific PAM configurations to use winbind and everything should work just fine, AFAIK.

On Debian and Ubuntu, you can edit the common-* files in /etc/pam.d to give more or less global support to winbind.

---

### Post by Gallows on 2005-07-08
Take a look at [this](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto)  Howto on the Wiki, and take a peep at [this](http://www.ubuntuforums.org/showthread.php?p=246644#post246644) thread.

I've just used the wiki HowTo to setup Hoary / Win2k3 AD authentication, works like a charm but you may need to download the Hoary Libkadm55 Deb as detailed in the referenced thread.

Works for both console and kdm access as Lord Hunter suggests they both use pam to authenticate users.

You' re going to have to join the XP machines to the domain and logon as a domain user to the XP box. Then map a drive and you *should* get access as configured in your shares and file permissions.  If not there is a whole host of info on this topic netwide... take a look [here](http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2540088) 
 in the official Samba HowTo's

Good luck!

---

### Post by MikeyXX on 2005-07-25
But is there a graphical version like perhaps YaST? To do the kerberos setup? I was going through that krb5.conf and it seems a little intimidating..unless I'm reading it wrong.

---

### Post by rpn on 2005-08-16
Using the info in Gallows post above in particular I found it fairly easy to get this Ubuntu Hoary box logging in using ADS. After a little fiddling to force the dependancies of Kerberos to install and this box to resolve the computer names on the network. Having pecked at this for a couple of years with several distros and attempted to make some use of the  excellent but huge Samba 3 book I am a happy bunny :) It needs to be said I've been around computers a long time but I'm not an expert and in Linux pretty much a newbie but have been fiddling in a modest way for several years - it can mean I miss something that is rather obvious to others :) 

Now for the bits that still have me puzzled, two really.

1. I have no problems browzing from the Win2K machine and XP clients and seeing files but opening an OO file from them the file opens read only. If I check the properties on this box the owner is correct and has write permission.

2. I can see the windows machines in file manager but if I try and browse them while logged in with an ADS login (and a 'normal' login)  I get a 'You do not have the permissions necessary to view the contents of "Windows Network: bendoran".' The Win2K box under AD/computers shows an entry for this box and the details seem correct.

Both apply with a regular user and the administrator ADS accounts.  

This is my home network to play with but I've got Linux boxes snuck into work in a minor way (DNS, DHCP, Apache) and I'd love to get this right to sneak into authentication and secured filesharing particularily on the peer-peer network but also the Win2k3 + Win2K served one.

Can anyone help with this? After a couple of evenings slog I suspect I'm into 'can't see the wood for the trees mode'!    :) 

Richard

---


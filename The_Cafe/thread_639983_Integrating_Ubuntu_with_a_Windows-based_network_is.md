---
title: "Integrating Ubuntu with a Windows-based network is harder than it should be"
date: 2007-12-13
forum: The Cafe
---

### Post by john_spiral on 2007-12-13
Found this article on the net, he seems to have a valid point.

[http://www.linux.com/feature/122681](http://www.linux.com/feature/122681)

How does Ubuntu compare with other distros when it comes to Windows integration?

John

---

### Post by boast on 2007-12-13
i think linux on a nix-based network is worse.

i hate having to mount every folder I want to use via NFS

---

### Post by LaRoza on 2007-12-13
Considering Windows is a closed source OS with hidden APIs and protocols, that Linux (Ubuntu) can network with it at all it amazing.

---

### Post by toupeiro on 2007-12-13
all my linux boxes have machine accounts in Active directory, and can authenticate from Active Directory.

I use AMD (Automounter Daemon) to manage my mount points, and run CIFS on the top for the windows permissions.


Absolutely seamless...  Maybe its in the approach?


I run RHEL at work , but what I do isn't proprietary to RHEL.

---

### Post by red_Marvin on 2007-12-13
> **boast said:**
> i think linux on a nix-based network is worse.

i hate having to mount every folder I want to use via NFS

I believe you can put nfs share mounting in /etc/fstab?

---

### Post by bash on 2007-12-13
At least authentication to an Active Directory domain is being worked for 8.04.

Link:
[https://blueprints.launchpad.net/ubuntu/+spec/windows-authentication-integration](https://blueprints.launchpad.net/ubuntu/+spec/windows-authentication-integration)

---

### Post by D-EJ915 on 2007-12-13
> **red_Marvin said:**
> I believe you can put nfs share mounting in /etc/fstab?
yes, you put nfs for the file system type, it's very easy.

---

### Post by boast on 2007-12-14
> **red_Marvin said:**
> I believe you can put nfs share mounting in /etc/fstab?

if the NFS server has exported folders all over the place, that will be a big big fstab. (and a lot of folders all over my computer too)

being one would not like to export the whole drive or /

---

### Post by HermanAB on 2007-12-14
The Ubuntu wizards are quite dreadful compared to for example Mandriva, so these "whatever is difficult on Linux articles", where the author only tried one old and dated version of Linux are just trolls really.

---

### Post by koenn on 2007-12-14
> **boast said:**
> if the NFS server has exported folders all over the place, that will be a big big fstab. (and a lot of folders all over my computer too)
 /
if the NFS server has exported folders all over the place, the guy who set it up didn't do his job very well, or is dealing with a complex situation where this was the only sollution. 

Same goes for Windows File sharing though : If a Windows file server hase shares all over the place, and you want a drive letter mapped to all of them, you'll have a long list just the same, and you risk running out of drive letters.

---

### Post by boast on 2007-12-14
If I could just shortcut them instead of mounting locally, it would not be so bad. (like smb)

---

### Post by koenn on 2007-12-14
> **john_spiral said:**
> Found this article on the net, he seems to have a valid point.
I don't think so. 
First, what LaRoza said : Considering Windows is a closed source OS with hidden APIs and protocols, that Linux (Ubuntu) can network with it at all is amazing. 

Second, the guy uses " lets try and see what happens" approach, but draws conclusions as if this was a well designed migration or Integration scenario. If n ICT environment is designed around a Windows Platform, anyhing that is not explicitly supported by Microsoft is going to have trouble integrating, "There's something wrong with this round peg, it doesn't fit neatly in any of these square holes".

Do people actually get paid for such sloppy work ?

---

### Post by koenn on 2007-12-14
> ---Quote (Originally by koenn)---
if the NFS server has exported folders all over the place, the guy who set it up didn't do his job very well,
---End Quote---
well, my FTP folder is /ftp/
my WWW server is /var/www/
my media server is /home/media
my different user shares are /home/user
etc,,,

If I could just shortcut them instead of mounting locally, it would not be so bad. (like smb)

*If you actually need to share / export all those*, what's so hard about making just 1 share and put all those directories in there. 
you would have to configure the respective daemons to look in the right place, and set security, but once that's done, you just have 1 share to maintain / mount / etc. 
That's what I meant earlier : let the design match the requirements.

---

### Post by boast on 2007-12-14
> **koenn said:**
> *If you actualle need to share / export all those*, what's so hard about making just 1 share and put al those directories in there. 
you would have to configure the respective daemons to look in the right place, and set security, but once that's done, you just have 1 share to maintain / mount / etc. 
That's what I meant earlier : let the design match the requirements.well i removed that from my post because the argument would go elsewhere. I'm trying to say--

with smb, I just have to put those folders for sharing, (or export them had it been nfs), and then I just browse to the computer and all the shared folders are shown.

with NFS, i have to mount each folder I wish to use. i can not connect to the server and just surf through all the folders.

Windows can both link folders and mount network drives, while linux can only mount network drives/folders

---

### Post by koenn on 2007-12-14
Well, as I explained it, you'd mount 1 folder to your local filesystem, and all your shares are accessible the same way local files are : you can access them from the command line or browse to them with a file browser. The only difference is that you don't need to remember drive letters, unc paths and local paths, and likewise for programs : paths in  configuration settings are uniform and transparant. You can even move stuff from one server to another without much fuss - 1 change in fstab would do. 

Compare that with the Windows way where you have "network" files that start with \\servername\sharename, local files that start with C:\ or D:\ or e:\, all the way up to Z:\,  and a trick to make network files look like local files ("network drives").. Move a file from one partition to another, or from one server to another, and you're of hunting for references to it all over your operating system. 

 I happen to prefer the Unix way of handling this. If you plan a bit, you actually don't need those shortcuts and "browse network neigborhood" features - so I'd consider them ugly workarounds for design flaws, rather that features.

---

### Post by boast on 2007-12-14
> **koenn said:**
>  so I'd consider them ugly workarounds for design flaws, rather that features.
like this?

> **koenn said:**
>  you'd mount 1 folder to your local filesystem,


not to mention NFS and writing permissions. horrible!

---

### Post by koenn on 2007-12-15
> **boast said:**
> like this?!
I don't see the point you're trying to make. You mount hard disks, removable media, ... too, don't you ? 
But let's drop this already, it's off topic, and I've said all I have to say.

---

### Post by john_spiral on 2007-12-15
It would be good to see Ubuntu "borrow" from work done in other distro's , it's open source after all?

The Ubuntu Hardy's '[_Improve Windows Client Integration_]("https://blueprints.launchpad.net/ubuntu/+spec/windows-authentication-integration")' blueprint looks a bit thin on the ground?

How about looking at work done by Novell's SUSE?

I don't get the argument that Windows is a closed system that's why it's not easy to ...........

If it was so closed how has Apple managed to get so much work done?

_[http://www.apple.com/itpro/articles/adintegration/](http://www.apple.com/itpro/articles/adintegration/)_

---

### Post by darkoptix on 2007-12-15
I find it the other way around, my ubuntu boxes network better using samba than my XP machines... weird...

---

### Post by koenn on 2007-12-15
> **john_spiral said:**
> 
I don't get the argument that Windows is a closed system that's why it's not easy to ...........

Compatibility with "Windows File Sharing" is implemented by SAMBA. 
You should read "How Samba was written" [http://www.samba.org/ftp/tridge/misc/french_cafe.txt](http://www.samba.org/ftp/tridge/misc/french_cafe.txt)
it explains just how closed Windows is, and how they managed to create something compatible anyway. It's a great story.

> **john_spiral said:**
> 
If it was so closed how has Apple managed to get so much work done?

Apple, like Linux and other unix-like systems, uses Samba for windows-compatible file sharing, and LDAP / Kerberos for Active Directory integration. You can do the same with any Linux system, although you may have to tweak and tune things a bit to get it right, and/or borrow ideas and code  from distributions that have their own LDAP implemantation. That's what Apple did. That's what anybody does to run a Linux file server in a Windows environment. And it works. 

What the OP article complains about are GUI details such as 'why doesn't Gnome show me the share "properties" dialog box with a "security" tab the same way windows does'. That's a Gnome / GUI issue, and in that field, distro's may still have some polishing to do.

---

### Post by Polygon on 2007-12-15
> **koenn said:**
> if the NFS server has exported folders all over the place, the guy who set it up didn't do his job very well, or is dealing with a complex situation where this was the only sollution. 

Same goes for Windows File sharing though : If a Windows file server hase shares all over the place, and you want a drive letter mapped to all of them, you'll have a long list just the same, and you risk running out of drive letters.


you wont run out of drive letters in windows. when you reach z:\ , you start going into double letters. AKA  

AA:\
BB:\

etc

---

### Post by koenn on 2007-12-15
never knew that, since what version do they have that ?

---

### Post by undine on 2007-12-15
> **john_spiral said:**
> Found this article on the net, he seems to have a valid point.

[http://www.linux.com/feature/122681](http://www.linux.com/feature/122681)

How does Ubuntu compare with other distros when it comes to Windows integration?

John

How does Windows compare when it comes to Linux integration?

---

### Post by john_spiral on 2007-12-15
> **undine said:**
> How does Windows compare when it comes to Linux integration?

Not very well, but then again how many offices are running Linux? 

Not many

Windows has only a limited need to integrate with other OSes it already dominates the operating system market. 

ask yourself this question:

Wouldn't Ubuntu see a much more rapid adoption rate if it was easier for a Ubuntu box to live in a Windows environment?

---

### Post by undine on 2007-12-15
> **john_spiral said:**
> Not very well, but then again how many offices are running Linux? 

Not many

Windows has only a limited need to integrate with other OSes it already dominates the operating system market. 

ask yourself this question:

Wouldn't Ubuntu see a much more rapid adoption rate if it was easier for a Ubuntu box to live in a Windows environment?

Maybe but so what?

---


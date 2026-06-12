---
title: "Ubuntu Hardening"
date: 2015-07-18
forum: Security
---

### Post by drm200 on 2015-07-18
I'm running 14.04 on my laptop from a flash drive.  Because of loading from flash drive, I've moved the /tmp and /dev/shm directories to memory (tmpfs) and have been running without any problems.

Recently, I've read that I should modify my fstab file by adding the nosuid, nodev and noexec switches to provide additional security and prevent some known exploits.

I've modified the two lines below in my fstab by adding nosuid, nodev and noexec


    tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1777 0 0
    tmpfs /dev/shm tmpfs defaults,noexec,nosuid,nodev 0 0

Is this good advice and worthwhile to make these changes (nosuid, nodev and noexec )?
Is there downside to the change?
Are there other directories that this should be applied to?

---

### Post by anon9815 on 2015-07-23
for normal users who are not being targeted by police/intelligence agency/state sponsored hackers Ubuntu is secure enough who are you attempting to defend against and how much time can you put into it?

---

### Post by drm200 on 2015-07-25
> **anon9815 said:**
> for normal users who are not being targeted by police/intelligence agency/state sponsored hackers Ubuntu is secure enough who are you attempting to defend against and how much time can you put into it?


I travel 300 days per year in China, Vietnam, Thailand, Indonesia, Laos and more.  I stay in hotels.  I do all my banking via the internet.   I do my work via the internet.

So, I am not a normal user.   And I have no idea who would be targeting me .... But, I feel at risk ... I have no corporate IT department behind me .... So I dedicate a significant amount of time thinking/trying to improve my risk profile.

My question about "nosuid, nodev and noexec" is a serious question.

---

### Post by HermanAB on 2015-07-25
Yes, it may be beneficial under some circumstances to set the ownership and modes like that.

You have a serious security problem.  I am glad that you are using Linux - that all by itself is a major security advantage already.

First of all, you have to encrypt the whole disk (and all removable media) with AES256, CBC, with SSIV and SHA256 (well, except /boot) and you should *never* suspend it - rather do a shutdown, since encryption only provides protection to data at rest.

Secondly, install KeepassX on your laptop machine (using a long passphrase) and ensure that every account you log into around the wild wide web has a unique, 12 character (or more) password, so that if any one account gets compromised, it won't spread like falling dominoes to all other accounts.

Finally, you should investigate the use of either AppArmor or SELinux for additional protection.

---

### Post by obake2 on 2015-07-26
If you want to harden and broaden your security, follow the following tips:

[https://ssd.eff.org/](https://ssd.eff.org/)

[https://www.privacytools.io](https://www.privacytools.io)

[http://prism-break.org/](http://prism-break.org/)

[http://www.fsf.org/](http://www.fsf.org/)

[https://trisquel.info/en/wiki/security](https://trisquel.info/en/wiki/security)

---

### Post by Lars Noodén on 2015-07-26
> **drm200 said:**
> My question about "nosuid, nodev and noexec" is a serious question.

Some systems follow the principle of W^X, or Write XOR eXecute.  That would mean that parts of the system that are writable cannot execute programs and vice versa.  In the context of file systems, it means that the partitions like /home /tmp or /var, if they are separate partitions, should be mounted noexec.  As an example, that would inhibit the browser from being able to launch a trojan.

Dividing your system up into partitions that are either read-only but executable or read-write but not executable takes planning and makes system administration less flexible.  But if you've had the same set up for a long time, you've probably already settled into patterns and won't need to drastically change the size of, say,  /usr

---

### Post by Skaperen on 2015-07-26
and do upgrades *only* while at home.

---

### Post by anon9815 on 2015-07-26
Never leave your laptop unattended  consider using full disk encryption  a grsecurity patched kernel because a kernel exploit can bypass most system security ([https://grsecurity.net](https://grsecurity.net)) browsing via the tor browser bundle to prevent targeted network attacks ([https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)) verify any downloaded software with GPG e.g. the grsecurity patches be careful about emails use a password manager remove flash if you dont really need it limit network services on your system to the bare minimum needed (you can use netstat and nmap to check this) and remove any unneeded software

---

### Post by drm200 on 2015-07-26
Many thanks for the responses .... it has given me some additional points to ponder ..... This is a summary of my current situation:

1. I am already using disk encryption at multiple levels.   I still use Truecrypt because the encrypted volumes work under Ubuntu and Windows.  I don't worry about a truecrypt back-door ... I have nothing to hide from the government.  All of my critical data is stored in a separate truecrypt container that is only opened as required ... 

2. I am already using Keepass ... and have different passwords for all accounts ..

3.  I use a VPN that has servers located in all the countries that I visit .... I may prefer to connect to a US or European server ... but in reality sometimes there is just limited bandwidth unless I connect to an in-country server.   VPN's are particularly troublesome in China in that one VPN server may work for one hour and then be blocked for the next week ... all I can do is keep trying different VPN servers until I can get a connection .. I primarily am using the VPN to lessen exposure to inhouse hotel attacks, and when in China to access my gmail (as it is routinely blocked).

4.  I've not found TOR reliable/workable in the countries I visit ... the bandwidth is just "not there" to even open up my gmail .... (I'm not worried about googles prying eyes) ... 

5.  I use a system wide hosts file to defend against malware sites.

6.  I use two browsers (Firefox and Chrome) ... both hardened with the different tweaks found on the internet ... I use these extensions only:  noscript on firefox and uBlock0, uMatrix, HTTPS Everywhere, & BitDefender traffic light extensions on both browsers.  Firefox is used only for banking/financial/email  ... The firefox browser has no Flash installed and I have blacklisted most known domains and then whitelisted the sites that I need to access.

7. I use the built in UFW firewall with just the basic setup ... block incoming and allow all outgoing.  I'm looking for a portable wifi repeater with built in hardware firewall that I can use in my hotel. Unfortunately, I've not found one where I'm travelling.  

8. I keep a backup of my encrypted data in a safety deposit box, and on Amazon AWS .... 

9. I keep the software up-to-date .... I only update thru a VPN with a connection to the U.S. ...  I worry that this is not particularly secure ... but I don't have a better option.

Comments welcome and appreciated.

---

### Post by drm200 on 2015-07-26
I've not given thought to the hardened kernal ...  Is this primarily for servers?  (my setup requires no server) ... 

I've also not given any thoughts to limiting network services (other than disable ipv6) ....  Currently, I use ethernet, wifi, bluetooth connections .... I will need to do some research to better understand what services might be disabled.

Verification of downloaded software .... I check/verify software that is manually downloaded but never have checked when downloading from the Ubuntu repositories ... as I've assumed that this is managed in the download process ....  Is there some risk here? (And I do try to only update thru a VPN connected to US servers).

[h=2]Re: Ubuntu Hardening[/h][COLOR=#000000][INDENT]Never leave your laptop unattended consider using full disk encryption a grsecurity patched kernel because a kernel exploit can bypass most system security ([https://grsecurity.net]("https://grsecurity.net/")) browsing via the tor browser bundle to prevent targeted network attacks ([https://www.torproject.org/download/...d-easy.html.en]("https://www.torproject.org/download/download-easy.html.en")) verify any downloaded software with GPG e.g. the grsecurity patches be careful about emails use a password manager remove flash if you dont really need it limit network services on your system to the bare minimum needed (you can use netstat and nmap to check this) and remove any unneeded software[/INDENT]
[/COLOR]

---

### Post by drm200 on 2015-07-26
> **Lars Noodén said:**
> Some systems follow the principle of W^X, or Write XOR eXecute.  That would mean that parts of the system that are writable cannot execute programs and vice versa.  In the context of file systems, it means that the partitions like /home /tmp or /var, if they are separate partitions, should be mounted noexec.  As an example, that would inhibit the browser from being able to launch a trojan.

Dividing your system up into partitions that are either read-only but executable or read-write but not executable takes planning and makes system administration less flexible.  But if you've had the same set up for a long time, you've probably already settled into patterns and won't need to drastically change the size of, say,  /usr


I've not heard of the W^X principle .... but it makes good sense to me.

At this point I've only applied the noexec to the /tmp and dev/shm directories.  I've not noticed any issues ... I think the next step is to apply noexec to the /home folder.   I'm relatively new to Linux/ubuntu ... When I look at the home directory, I see many folders associated with software ... But it looks like the content of the folders is for configuration/data.

I've let ubuntu always decide where to install the software ... and in almost all cases the installation was completed through the software repository.  Would you expect Ubuntu's default installation to allow me to use noexec on the home directory?

---

### Post by Lars Noodén on 2015-07-26
It should be configurations or data in /home but there is an optional ~/bin/ where you can have scripts or other executables.  If you have them, you would have to move them if you mount it noexec.  If you write scripts in your home directory you might notice something but when I've tried it, I've not run into other issues.

---

### Post by drm200 on 2015-07-27
> **Lars Noodén said:**
> It should be configurations or data in /home but there is an optional ~/bin/ where you can have scripts or other executables.  If you have them, you would have to move them if you mount it noexec.  If you write scripts in your home directory you might notice something but when I've tried it, I've not run into other issues.

During Ubuntu installation, I chose the option to encrypt my home directory.  There is no reference to my home directory in fstab.

If I issue the "mount" command, I get the following output relative to my home directory:

      gvfsd-fuse on /home/drm/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)

It isn't clear to me the next step that would add noexec to my home directory.

---

### Post by Lars Noodén on 2015-07-27
> **drm200 said:**
> During Ubuntu installation, I chose the option to encrypt my home directory.  There is no reference to my home directory in fstab.


The /home partition is a different matter from the individual home directories and encrypting the individual home directories.  The latter are usually within /home.  However it is possible that you do not have a separate /home partition.  If you did a generic installation, then it is the case that everything is lumped into a single partition, plus one for swap.  If you re-install you can make a separate /home partition if you partition manually.  There are guides about moving the /home directories to a separate partition but it is easiest to do during installation.

---

### Post by drm200 on 2015-07-27
> **Lars Noodén said:**
> The /home partition is a different matter from the individual home directories and encrypting the individual home directories.  The latter are usually within /home.  However it is possible that you do not have a separate /home partition.  If you did a generic installation, then it is the case that everything is lumped into a single partition, plus one for swap.  If you re-install you can make a separate /home partition if you partition manually.  There are guides about moving the /home directories to a separate partition but it is easiest to do during installation.

As I understand it, the individual home directories are in the /home/username directories.  In my case I have 3 directories under home:
        /home/user1
        /home/user2
        /home/.ecryptfs


The user1 and user2 directories contains the desktop, documents, downloads ... etc.    So I believe the user1 and user2 directories are the proper individual home directories..
I did not install a swap file purposely during installation.

 However,  there is still no reference to user1 or user2 in fstab.  So I don't know where to  go to modify their properties with noexec.  I thought that this line in fstab:

[COLOR=#000000]      gvfsd-fuse on /home/drm/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)

was the mounting of the home directory .... but I couldn't find a file that seemed to do this command.  The contents of the file .gvfs appears blank when I open it.[/COLOR]

---

### Post by Lars Noodén on 2015-07-27
Ok.  I was thinking that you might have set up a separate /home, that would have been in /etc/fstab  

The encrypted home directories are mounted using a wrapper shell script /usr/bin/ecryptfs-mount-private  That's as far as I've been able to figure out.  After some searching, I'm not finding any clues as to how to mount an encrypted home directory noexec.   The utility [mount.ecryptfs_private](http://manpages.ubuntu.com/manpages/trusty/en/man1/mount.ecryptfs_private.1.html) seems to be called from that.  An encrypted home directory unmounts with fusermount, so it seems to use FUSE.  Maybe adding additional mount options for an encrypted home is something for a separate thread.

---

### Post by drm200 on 2015-07-28
> **Lars Noodén said:**
> Ok.  I was thinking that you might have set up a separate /home, that would have been in /etc/fstab  

The encrypted home directories are mounted using a wrapper shell script /usr/bin/ecryptfs-mount-private  That's as far as I've been able to figure out.  After some searching, I'm not finding any clues as to how to mount an encrypted home directory noexec.   The utility [mount.ecryptfs_private]("http://manpages.ubuntu.com/manpages/trusty/en/man1/mount.ecryptfs_private.1.html") seems to be called from that.  An encrypted home directory unmounts with fusermount, so it seems to use FUSE.  Maybe adding additional mount options for an encrypted home is something for a separate thread.


Ok... your information has been very helpful.

thanks

---

### Post by HermanAB on 2015-07-28
OK, so you are doing OK.  Just shut the machine down when it is not in use.  Do not suspend it.

---


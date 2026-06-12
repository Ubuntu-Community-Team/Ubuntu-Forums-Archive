---
title: "Recently unable to mount Windows 2012 Server network drives"
date: 2020-08-30
forum: Server Platforms
---

### Post by linuxnoob87 on 2020-08-30
Up until about 7-10 days ago my fstab file in Ubuntu 18.04 was able to mount file shares from a  windows 2012 Server without any issues. Now the shares no longer mount; I get the error ```
mount error(5): Input/output error.
```



Interestingly enough, there are other shares being mapped in the same file from a Windows 2016 Server without any issues.


 I've confirmed that the windows account is **not** locked out; still experienced the same issue. I also tried mounting the drives with a different account and same behaviour. I am specifying ```
vers=2.1
``` in the fstab line.


 Has anyone seen this issue before? Where am I going wrong?

Thanks!

---

### Post by darkod on 2020-08-30
I haven't followed the topic but check which smb version is used on both ends and its compatibility. OS updates (especially on windows side) can limit which smb version can be used or blocked.

That might be a reason why it suddenly stops working.

And regardless if lower versions are supported, try to go as high as possible that could work in your scenario. I guess it offers more security and better result (in theory)...

PS. It looks obvious but people sometimes forget it. What do the logs say on both sides? There should be something in the logs if mounting is failing...

---

### Post by TheFu on 2020-08-30
Please show the full line, if you'd like help and the outout from **lsb_release -a**, so we know what release you are running.

How often is the ubuntu system patched?  Some defaults changed for samba about 6 months ago which broke connections to older Windows systems.  There are threads here about that. Also, MSFT has been changing some of their defaults for network shares the last year.  2 moving targets are hard to hit when there isn't any coordination between the teams.

---

### Post by linuxnoob87 on 2020-08-30
I've tried specifying version 3.0 in the config with the same issue. Completely with you on using the highest supported version.

Where would I be looking for the Ubuntu logs? Windows logs don't really show anything.

---

### Post by linuxnoob87 on 2020-08-30
Sorry about that; didn't know to post the full release info.


That info is:
> USER@PServer:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic


This system is patched (roughly) monthly.

Understandable about the two teams; what's weird is that nothing on my end has changed (other than patching both systems) and the Server 2016 still continues to work successfully (fingers crossed).

---

### Post by darkod on 2020-08-30
I suggest you try the mount command in terminal with high verbocity (something like -vvv) to show you more details as it tries to mount.

Also comparing Windows 2012 and 2016 does not always mean things should work identically. Patching is precisely what can "close down" what they consider vulnerabilties and they are not always identical across different OS versions.

---

### Post by linuxnoob87 on 2020-08-30
Ok, can you point me in the right direction as to what command I should be using (please)? 

Thanks!

---

### Post by Morbius1 on 2020-08-31
> **linuxnoob87 said:**
> Ok, can you point me in the right direction as to what command I should be using (please)? 

Thanks!
```
sudo mount -t cifs --verbose //server/share /mountpoint -o comma,separated,list,of,options
```

*Side note: The version of the Linux kernel in Ubuntu 18 automatically negotiates with the server for the best smb dialect to use between SMB2.1 and SMB3.X so the only reason you would need to specify a "vers" in the options list would be if the server can only speak SMB2.0 or less.*

---

### Post by linuxnoob87 on 2020-09-01
```
user@PServer:/mnt$ sudo mount -t cifs --verbose //HServer/HPics /mnt/HPhotos -o user=(Username),password=(Password)
mount.cifs kernel mount options: ip=172.16.249.101,unc=\\HServer\HPics,user=(Username),pass=********
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by wmcl on 2020-09-02
> **linuxnoob87 said:**
> ```
user@PServer:/mnt$ sudo mount -t cifs --verbose //HServer/HPics /mnt/HPhotos -o user=(Username),password=(Password)
mount.cifs kernel mount options: ip=172.16.249.101,unc=\\HServer\HPics,user=(Username),pass=********
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I am getting the same error message (different path, mountpoint and credentials, of course), dmesg gives me

```
[  137.556264] Status code returned 0xc000018d STATUS_TRUSTED_RELATIONSHIP_FAILURE
[  137.556274] CIFS VFS: Send error in SessSetup = -5
[  137.556330] CIFS VFS: cifs_mount failed w/return code = -5

```

I tried several different combinations of the mount options vers= and sec=, none of those attempts have worked so far.
Connecting to the shares using smbclient works from the same machine using the same credentials.

The last time I can confirm the mountpoints were working, the syslog entries

```

Status code returned 0xc000018d STATUS_TRUSTED_RELATIONSHIP_FAILURE
CIFS VFS: Send error in SessSetup = -5

```

were already occurring regularly, so I assume the only syslog entry definitely related to the problem must be

```

CIFS VFS: cifs_mount failed w/return code = -5

```

which started to appear after a reboot following the installation these updates:

```

Start-Date: 2020-08-28  06:47:46
[...]
Upgrade: libnss3:amd64 (2:3.35-2ubuntu2.11, 2:3.35-2ubuntu2.12)
[...]
Start-Date: 2020-08-31  16:03:45
Upgrade: libpam0g:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2), libpam-modules:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2), libsystemd0:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), libkmod2:amd64 (24-1ubuntu3.4, 24-1ubuntu3.5), udev:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), language-pack-de:amd64 (1:18.04+20190117, 1:18.04+20200702), libpam-runtime:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2), kmod:amd64 (24-1ubuntu3.4, 24-1ubuntu3.5), libudev1:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), apport:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17), python3-distupgrade:amd64 (1:18.04.37, 1:18.04.38), ubuntu-release-upgrader-core:amd64 (1:18.04.37, 1:18.04.38), python3-apport:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17), systemd-sysv:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), libpam-systemd:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), systemd:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), libpam-modules-bin:amd64 (1.1.8-3.6ubuntu2.18.04.1, 1.1.8-3.6ubuntu2.18.04.2), iproute2:amd64 (4.15.0-2ubuntu1.1, 4.15.0-2ubuntu1.2), bcache-tools:amd64 (1.0.8-2build1, 1.0.8-2ubuntu0.18.04.1), libnss-systemd:amd64 (237-3ubuntu10.41, 237-3ubuntu10.42), python3-problem-report:amd64 (2.20.9-0ubuntu7.16, 2.20.9-0ubuntu7.17), base-files:amd64 (10.1ubuntu2.8, 10.1ubuntu2.9)

```

---

### Post by linuxnoob87 on 2020-09-02
@wmcl

That date fits (roughly) the same time frame as when my network shares stopped mounting as well.

---

### Post by wmcl on 2020-09-03
I just restored my machine to the state it was in when the mount points were still working, but they didn't. Starting to suspect the Windows server as the source of the problem.

Edit:

The Windows Server(s) in question didn't have any related updates in the time frame, also, accessing the shares with smbclient instead of mounting them does work. The windows server(s) report a failed login when attempting to mount the shares.

---

### Post by darkod on 2020-09-03
How about creating new user on windows end and assign it permissions for the share, then try with these new credentials?

Although the failed login might relate to actually how the two machines talk between themselves rather than the credentials being wrong. In such case even new user wouldn't work.

---

### Post by wmcl on 2020-09-03
Managed to get my mount points working again after poking around a bit in the mount options.

Setting ```
sec=krb5
``` gave me a different error ("no such file or directory"), more research showed that this was caused by the package keyutils not being installed, fixed that by installing it.
```
sudo apt -y install keyutils
```
Then, after initializing Kerberos for the user I am mounting the shares as ```
sudo kinit username
``` the shares would mount again.

---

### Post by linuxnoob87 on 2020-09-03
@Wmcl

I follow you up to a point. I installed keyutils but then I'm not sure what you did after that.

Trying to get the shares to mount at boot via fstab

Edit: If I run ```
sudo kinit username
``` I get the error ```
sudo: kinit: command not found
```

---

### Post by wmcl on 2020-09-04
kinit is in the krb5-user package.

Unfortunately I've hit some more snags by now, the mount points got disconnected after some time, but I could remount them just fine after running the kinit command again. I'll need to figure out how to make the Kerberos authentication persistent.

---

### Post by linuxnoob87 on 2020-09-04
Darko:

Tried this and ran into the same issue.

---

### Post by darkod on 2020-09-05
I have no more ideas right now. You will have to search deeper into the logs and google the error messages you find there. If a mount is rejected there must be log entries on either side.

I have to say this is strange situation because in most cases users would insist on using Windows on workstation because of the GUI comfort but run linux on their server (which allows to save a lot on windows server license too). But in this case the server runs Windows and has CIFS shares in the network which are not as native to linux as NFS. And with Microsoft doing quite a lot of changes on their end too (sometimes patching vulnerabilities that have existed for decades) you would need a deeper investigation to find the issue.

Another thing not mentioned here is whether domain is used on Windows or not. I assume not but that would change things. I don't really see why kerberos would complain if there is no domain in place. But on the other hand, like I said, I have mostly used linux servers and windows clients, not the other way around.

---

### Post by linuxnoob87 on 2020-09-05
Darko,

It's a windows server on a windows domain but not joined to the domain (as it's always been).

This linux server was (and still is) my initial deployment of any sort of linux server; the reason for this is that I've been a windows sysadmin for many years and am more comfortable with windows.

Can you (please) point in the direction (on the linux side) as to what logs I need to look at? Is there another share type I can use on the windows server that interfaces better with linux?

---

### Post by darkod on 2020-09-05
Try the following and post the output here:
```
sudo mount -t cifs -vvv //HServer/HPics /mnt/HPhotos -o user=(Username),password=(Password),sec=ntlm
```

PS. Also check the last lines in /var/log/syslog for errors related to the cifs mount.

---

### Post by TheFu on 2020-09-05
> **linuxnoob87 said:**
> Can you (please) point in the direction (on the linux side) as to what logs I need to look at? Is there another share type I can use on the windows server that interfaces better with linux?

NFS, but I don't know about it being "better" when Windows is involved. userid mapping will need to be handled, which is usually a manual thing to setup IME.

NFS is server-to-server, not user-to-server.
Perhaps I missed whether Kerberos authentication was being used or not.

I'm just asking questions in hope that it may spawn ideas in others. I've never connected any Linux system to any Windows Server using file sharing.  

The closest was in the mid-1990s when we used NFS on Windows Server with thousands of Unix clients (machines and about 6K users) due to political reasons. Windows was a political choice due to some other MSFT agreements at that location.

---

### Post by darkod on 2020-09-05
If it was the other way around (windows is the client) I would say NFS too. Especially since recent versions of Windows now include NFS client by default.

But I am not sure if Windows can serve as NFS server and if it can be trusted for that role. It's worth exploring though.

---

### Post by TheFu on 2020-09-05
Windows Server used to have the Unix Services pak.  Thought that was discontinued.

We used 3rd party NFS tools, which were not cheap.

I've never gotten NFS working from WinXP, Vista, Win7 after multiple attempts.  That includes a Win7 Ultimate license (a gift from MSFT).  Windows Home has never included NFS, so if Win10 does, that's great, new and news.  There are free NFS clients that I've seen. They were all shareware to my knowledge or hadn't been maintained in 5+ yrs.  I'd love to be wrong. It wouldn't be the first time.

---

### Post by darkod on 2020-09-05
Yeah, I was speaking only about native tools, not third-party. The NFS Client comes as Windows feature now, and disabled. You only have to enable it.

Again, I'm not sure any of this helps if you want Window to be the one serving the share. CIFS/SMB still seems the only way to go for that.

---

### Post by TheFu on 2020-09-05
> **darkod said:**
>  CIFS/SMB still seems the only way to go for that.

Yep - 98% of the time, CIFS is the better answer when Windows is involved.

I had an issue connecting to Win7 (I don't have anything newer here) in my hacking lab. Made all sorts of changes and couldn't get Win7 to share anything.  Finally, on a weekly Linux meeting, I asked for help.  They asked, "have you tried turning it off and on again?"

Flashbacks to Roy and Moss ... 

It worked. How sad is that?

---

### Post by Morbius1 on 2020-09-05
This my be way off base but is it  all possible you enabled SMB encrypted transport at either the share level or the server level in your Win2012 server?

If you did specifying vers=2.1 will not work. Even if you told mount.cifs to force encrypted transport it will not work. It can only be done when using SMB3.

If you remove the vers=2.1 from your mount declaration it should go SMB3 by itself. If not specify vers=3.0 in your mount command.

---

### Post by linuxnoob87 on 2020-09-05
```
xxxx@PlexServer:/mnt$ sudo mount -t cifs -vvv //HServer/HPics /mnt/HPhotos -o user=(Username@domain.global),password=(Password),sec=ntlm 
[sudo] password for xxxx: (Password typed here)
mount.cifs kernel mount options: ip=172.16.249.101,unc=\\HServer\HPics,sec=ntlm,user=xxx@domain.global,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

/var/log/syslog:
```
Sep  5 22:41:38 PServer kernel: [558863.327821] No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 (or SMB2.1) specify vers=1.0 on mount.
Sep  5 22:41:38 PServer kernel: [558863.329183] CIFS VFS: Unable to select appropriate authentication method!
Sep  5 22:41:38 PServer kernel: [558863.329185] CIFS VFS: Send error in SessSetup = -22
Sep  5 22:41:38 PServer kernel: [558863.329908] CIFS VFS: cifs_mount failed w/return code = -22
```

---

### Post by linuxnoob87 on 2020-09-05
Here's my mount line in the fstab file:

```
//HServer/HPics /mnt/HPhotos cifs user=(domain user name),password=(password),iocharset=utf8,vers=3.0  0  0
```

Note that prior to 5 minutes ago the vers=3.0 was set to vers=2.1. Removing any reference to a version doesn't mount the drive either (using "sudo mount -a")

I know that putting the password directly in the fstab file is not great; this is a home environment where I'm not worried about passwords "leaking".

Thank you all for your help and assistance. What's weird (but I'm happy about) is that connectivity to Server 2016 is still working properly.

Edit: Interestingly enough I can mount the share via the GUI from my Linux Mint 20 (Ulyana base: Ubuntu 20.04 focal) laptop

---

### Post by darkod on 2020-09-06
First, make sure cifs-utils is installed. You can check that with:
```
apt-cache policy cifs-utils
```

Then, you said the server is not joined in a domain but for the credentials in mount you use a domain user???

Have you also tried creating local user on the server and use that one?

I am pretty sure this is because of something on the windows side, especially since you use domain user and maybe all you need to do is play with the sec= options. From the man page of mount.cifs:
```
none attempt to connection as a null user (no name)
krb5 Use Kerberos version 5 authentication
krb5i Use Kerberos authentication and forcibly enable packet signing
ntlm Use NTLM password hashing (default)
ntlmi Use NTLM password hashing and force packet signing
ntlmv2 Use NTLMv2 password hashing
ntlmv2i Use NTLMv2 password hashing and force packet signing
ntlmssp Use NTLMv2 password hashing encapsulated in Raw NTLMSSP message
ntlmsspi Use NTLMv2 password hashing encapsulated in Raw NTLMSSP message, and force packet signing
```

We are not in a position to judge what do you need for the domain user to authenticate successfully especially since you said the server is not joined to the domain but you use domain credentials for the share. That is how I understood it and I find it very strange.

If the server is not in a domain you would use local user.

---

### Post by TheFu on 2020-09-06
For not putting username and password into the fstab, use:
```
       credentials=filename
           specifies a file that contains a username and/or password and
           optionally the name of the workgroup. The format of the file is:

                         username=value
                         password=value
                         domain=value

           This is preferred over having passwords in plaintext in a shared
           file, such as /etc/fstab. [B]Be sure to protect any credentials file
           properly[/B].
```

---

### Post by LHammonds on 2020-09-06
My Linux servers are not joined to my Win2012 domain but they can connect via CIFS to a Windows share using domain credentials.  Here is what I have done:

Any Linux machine that connects to a Windows server, I install samba and cifs-utils:
```

sudo apt -y install samba cifs-utils

```

Then I create a file to hold the Windows/Domain credentials.
```

sudo touch /etc/cifspw
sudo chown root:root /etc/cifspw
sudo chmod 0600 /etc/cifspw

```

/etc/cifspw
```

username=linux
domain=abc
password=thepassword

```

I can manually connect using this command:
```

sudo mount -t cifs //srv-windoze/myshare /mnt/srv-windoze --options nouser,rw,nofail,noexec,credentials=/etc/cifspw

```

This procedure has worked for Ubuntu 10.04 through 20.04.  Over time, there have been various tweaks done to the options to accommodate changes in Windows such as the dropping of SMB 1 and such but there was always a solution to make it work.

LHammonds

---

### Post by linuxnoob87 on 2020-09-14
Here's the output of trying to install those tools:

```
cifs-utils:
  Installed: 2:6.8-1ubuntu1
  Candidate: 2:6.8-1ubuntu1
  Version table:
 *** 2:6.8-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:6.8-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

> Then, you said the server is not joined in a domain but for the credentials in mount you use a domain user???

Yes. It's been setup this way for at least 2-3 years now.

> Have you also tried creating local user on the server and use that one?

The server is running in a domain; the accounts are created at the domain level. 

> I am pretty sure this is because of something on the windows side,  especially since you use domain user and maybe all you need to do is  play with the sec= options. From the man page of mount.cifs:

Where would I add this? At the end of the line in my fstab?

> We are not in a position to judge what do you need for the domain user  to authenticate successfully especially since you said the server is not  joined to the domain but you use domain credentials for the share. That  is how I understood it and I find it very strange.

When I set the server up I had no idea it could be joined to a domain. Instead I found that using the domain creds would mount the share (and with my Server 2016 this method still works) Would this fix the issue (joining it to the domain)?

---

### Post by linuxnoob87 on 2020-09-14
Samba and cifs-utils are installed and up to date.

> Then I create a file to hold the Windows/Domain credentials.

I have different creds depending on the share; do I make a file for each set of creds?

Thanks!


Edit: Figured it couldn't hurt to try. I created a file called "/etc/cifspw1" and followed the directions. Ran the following command:

```
sudo mount -t cifs //HServer/HPics /mnt/HPhotos --options nouser,rw,nofail,noexec,credentials=/etc/cifspw1
```

and this was the output:

```
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Edit 2: Output of "dmesg":

```
[376803.285610] No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 (or SMB2.1) specify vers=1.0 on mount.
[376803.288104] Status code returned 0xc000018d STATUS_TRUSTED_RELATIONSHIP_FAILURE
[376803.288114] CIFS VFS: Send error in SessSetup = -5
[376803.288710] CIFS VFS: cifs_mount failed w/return code = -5

```

Edit 3: Made a new test folder in /mnt. Tried the command again with the 2012 share and it wouldn't mount. Tried the exact same command (with the same creds) to mount a share off the 2016 Server and it mounted without any issues.

---

### Post by TheFu on 2020-09-14
yes.  each mount can use different credentials=

---

### Post by linuxnoob87 on 2020-09-14
Thanks - see my edit to the post.

Short version: It didn't work.

---

### Post by linuxnoob87 on 2020-09-21
Ok, here's what I've done so far.

I stood up a new 2012 server without ANY updates. Shared out a folder for testing and I was able to mount it with the same commands as the other (non-working) 2012 servers.

My next step is to run updates and see if things break.

TL;DR - Unpatched "base" 2012 works fine.

---

### Post by linuxnoob87 on 2020-09-21
Update: Fresh install with all patches stops working. Will need to go through and figure out which patch it is.

---

### Post by darkod on 2020-09-22
Another approach would be to see if any option in the mount command can help you open a share even if Windows is fully patched. That's what I was talking about earlier, not sure if you understood that.

The man page of the mount command has all the various options for the sec= parameter which you can use for manual testing to mount the share. If any of them works, then you simply would modify the fstab line accordingly and see if it works that way.

That would allow you to have windows fully patched and ubuntu still to connect to the share.

---

### Post by linuxnoob87 on 2020-10-06
All,

I HATE that this is the answer (but it is) - I upgraded the  two servers running server 2012 to server 2019 and the issue is  resolved. I have no idea why as I did not make ANY config changed on the  linux side. My shares now successfully mount.

Good luck and God  speed to anyone else who reads this and winds up in the same boat - it  was easier in my small homelab to upgrade than to continue to try and  figure out why it wasn't working


EDIT: So, yeah. Rebooted and it stopped mounting the shares from the "old" 2012 server. Still no idea why this is working with the other server but happy that it is.

---

### Post by linuxnoob87 on 2020-10-07
Ok, ok. I THINK I've **finally** figured this out thanks to this post: [https://lists.samba.org/archive/samba-technical/2007-October/055861.html](https://lists.samba.org/archive/samba-technical/2007-October/055861.html)

In case the post is removed, here's the text (from 2007):
```
This last week I've gone even further down this rabbit hole, and found a
few more issues in authenticating local users to a domain which has a
user of the same name. 

 

First off, when passing WORKSTATION\user local credentials to a Windows
domain member (both Win2K and Win2K3) I haven't seen that server pass
them onto the DC for authentication.  Every time, the Windows server
recognizes that the workstation name given as the domain is not part of
any trusted domain it can authenticate against and immediately returns
STATUS_TRUSTED_RELATIONSHIP_FAILURE (Win2K) or STATUS_LOGON_FAILURE
(Win2K3) to the client.

 

Whereas Samba 3.0.24 converts the WORKSTATION to its domain and asks the
DC for credentials or with my following patch, leaves the WORKSTATION
name, but still asks the DC for credentials.
```

This got me thinking; the **only** difference between the servers is that one was/is a Domain Controller (DC) and the other was **not** a DC. I promoted the other server to a DC and the drives magically started working.

What got me here was this error message when running DMESG:
```
**STATUS_TRUSTED_RELATIONSHIP_FAILURE**


```

So, yeah. I'll et you all know if this actually fixes the issue.

---

### Post by LHammonds on 2020-10-07
Interesting.  My Linux servers were never part of the domain but were able to connect to Windows (2003/2008/2012) servers that were on a domain.  I never connected to a DC though (mainly because it is VERY bad practice to run file services on a DC).

It has been a while since I've connected to Windows though.  I switched over to Linux as my backup target and thus have been using NFS.  If I get some time, I will try to connect to a fully-patched Win2012 server.

LHammonds

---

### Post by linuxnoob87 on 2020-10-14
> Interesting.  My Linux servers were never part of the domain but were  able to connect to Windows (2003/2008/2012) servers that were on a  domain.

Same with all of mine; none of the servers were/are joined to the domain.

> I never connected to a DC though (mainly because it is VERY bad practice to run file services on a DC).

Agreed, which is why up until recently my two DCs were running server core and were **ONLY** DCs. No file shares. No nothing.

> If I get some time, I will try to connect to a fully-patched Win2012 server.

If it's Ubuntu core connecting to a Windows Server (it *seems* **any** version) it must be a DC otherwise it can't authenticate for the drive mounts. What's odd is that my laptop running the latest stable release of Mint mounts the shares just fine. 

Update on the issue: Rebooted the Ubuntu server **several** times and the shares continue to mount successfully.

---

### Post by LinuxNoob6 on 2021-05-24
[Deleted]

---


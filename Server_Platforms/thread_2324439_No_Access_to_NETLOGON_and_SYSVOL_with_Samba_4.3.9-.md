---
title: "No Access to NETLOGON and SYSVOL with Samba 4.3.9-Ubuntu on Ubuntu Server 16.04"
date: 2016-05-13
forum: Server Platforms
---

### Post by joebell on 2016-05-13
On my Linux box I am running the new Ubuntu Server 16.04 LTS 64-bit  (Xenial Xerus) operating system. A new big capacity hard drive has been added to it  lately, hence I wished to use the box as a File Server and Domain  Controller for Windows workstations, as well. To achieve the goal, this site was my guide - [http://blogging.dragon.org.uk/samba4...-ubuntu-14-04/]("http://blogging.dragon.org.uk/samba4-ad-dc-on-ubuntu-14-04/").  Everything seems to be OK except of after this command is issued:  smbclient //localhost/netlogon -UAdministrator -c 'ls'. 

Instead of  getting something like this:
------------------------------------------------------------
Enter Administrator's password: 
Domain=[BLACK] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
    .                                                  D                0   Sat May  9 12:20:08 2015
    ..                                               D         0  Sat May  9 12:20:14 2015
 
                                41773 blocks of size 262144. 27672 blocks available
------------------------------------------------------------
I can only see this error: NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*. As DNS Backend I am using BIND 9.10.3-P4-Ubuntu. The Samba version is Version 4.3.9-Ubuntu.

Commands kinit and klist are all working great. Even I can see the  shares in Windows, but no access to them although my workstation is joined into the domain and I am logged on as a domain admin. The Active Directory can be managed from workstation without any  troubles, too. Only the shares including sysvol and netlogon and all others I created cannot be  accessed at all. That's weird. 

I did install Samba4 as a DC many times before on Ubuntu Server 14.04.4 LTS. Everything  was always working great. Can someone explain what can be wrong in my configuration and  help to solve this unpleasant issue? Is it a bug of Samba 4.3.9-Ubuntu, or Ubuntu Server 16.04 LTS is the reason for this strange behavior?

---

### Post by peterp772000 on 2016-05-14
I'm using Samba 4.3.9 and I have exactly the same problem. I have Samba set up as an AD server and whilst the Windows client can see the directories, it won't allow me to access them. And when attempting to access any shared files from the server itself, I also get the NT_STATUS error message. I'm thinking it may be a bug. 

Perhaps we need to update our Samba version? Which would mean compiling it from source.

---

### Post by darkod on 2016-05-15
This is not strictly related to 16.04, but it might be related to a combination of kernel 4.4 and samba 4.3.9, or only to samba 4.3.9. I was able to reproduce that error message on 14.04 too. Here is what I did:
1. In vbox I installed 14.04.3 and then added the linux-generic-lts-xenial package which adds the latest kernel 4.4.0-22.
2. From the standard apt repository I installed samba which is 4.3.9 version (the 4.3.9 has been added to 14.04 LTS too few months ago, so now even 14.04 installs that samba version by default).
3. I provisioned a test domain and tried the smbclient right away, the error message showed up.

Now the next tests would be to try with 14.04.3 with default kernel of 3.19 and with 4.2 (by adding linux-generic-lts-wily I think it was). In all cases samba should be 4.3.9 and that can show if it is kernel related or not. After that a bug can be reported and see what the developers will say.

---

### Post by darkod on 2016-05-15
Hmmm, it looks to me like issue with samba 4.3.9 package. Here is what I get on basic 14.04.3 with kernel 3.19:
```
root@dc1:~# smbclient -L localhost -U%
session setup failed: NT_STATUS_OBJECT_NAME_NOT_FOUND
root@dc1:~# uname -a
Linux dc1 3.19.0-59-generic #65~14.04.1-Ubuntu SMP Tue Apr 19 18:57:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
root@dc1:~# samba -V
Version 4.3.9-Ubuntu
```

So, it doesn't look related to 16.04 or kernel version because I still haven't added kernels 4.2 or 4.4 to the testing 14.04. The error shows up even for kernel 3.19. Unless I did something wrong during testing but there isn't much room for mistake.

---

### Post by darkod on 2016-05-15
Searching for that error message on Launchpad it seems it was already reported as bug with samba 4.3.8:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573221](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573221)

According to that only adding winbind package solves it (probably better to reboot after adding it, instead of trying to restart all samba services). It doesn't say you need any special winbind config. I still haven't tried it in my test environment. I'll post later.

---

### Post by darkod on 2016-05-15
Yes, just adding winbind and rebooting seems to work:
```
darko@dc1:~$ smbclient -L dc1 -U administrator
Enter administrator's password:
Domain=[HOME] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]


        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        IPC$            IPC       IPC Service (Samba 4.3.9-Ubuntu)
Domain=[HOME] OS=[Windows 6.1] Server=[Samba 4.3.9-Ubuntu]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------
        WORKGROUP            DC1
```

This is still on 14.04 with kernel 3.19. I will try later with kernel 4.4 and with 16.04 with kernel 4.4.

---

### Post by darkod on 2016-05-15
It works on 16.04 with kernel 4.4 too. Only you need to add winbind and reboot. I'm not sure if that's a good fix for this bug but it seems obvious it's within samba and not ubuntu itself. Installing the winbind package is a quick and easy workaround. No need for any special configuration, at least not in my tests.

As they commented in that Launchpad bug report, this might be due to big differences between samba 4.3 and 4.1.

---

### Post by joebell on 2016-05-15
Darko,

Congratulations. You are making progress. I keep my fingers crossed. This is what I can share with you by now.

[LIST=1]
[*]winbind daeomon installed 
[*]box rebooted 
[*]testing commands issued:
[LIST]
[*]smbclient -L localhost -U% 
[*]smbclient //localhost/netlogon -UAdministrator -c 'ls' 
[*]smbclient -L dc1 -U administrator 
[/LIST]
  
[*]all of them working great 
[*]NETLOGON - can be open from workstations
[LIST]
[*]as Administrator, no objects can be created 
[/LIST]
  
[*]SYSYVOL - can be open from workstations
[LIST]
[*]as Administrator, the folder scripts cannot be open. Error: The Filename, directory name, or volume label syntax is incorrect. 
[/LIST]
  
[*]Assess to shares via Computer Manager from Windows 10 Workstation:
[LIST]
[*]Computer Selection through Active Directory: OK 
[*]click on Systems Tools - error: The procedure number is out of range(1745), proceeded with click on OK 
[*]Shared Folder double clicked: I can see all the shares - this is OK 
[*]right-click on NETLOGON, then Properties chosen: in a new window I can see that by default the User limit is set to 0. Why???? 
[*]trying to switch to Maximum allowed - error: The system encountered the following error while saving the properties of share netlogon: Error 1: Incorrect function. 
[/LIST]
  
[*]RESULT: I can open NETLOGON and SYSVOL, however no object can be created within them. Trying to adjust Folder permissions in Computer Management snap-in results in no success. 
[/LIST]

As you can see, the installation of winbind took the system just a step forward. However, this configuration of an AD DC cannot be applied atl all in aproduction environment. My Ubuntu Server 16.04 LTS Kernel is: 4.4.0-22-generic #39-Ubuntu. I do hope you will finally hit the nail and find out what is making all these troubles never seen before with previous versions of Samba and Ubuntu Server.

---

### Post by darkod on 2016-05-15
For me it allows creating/copying files in NETLOGON on the 16.04 DC with kernel 4.4 and samba 4.3.9. I didn't do anything special, just installed a test windows server 2016 vm, joined it to the domain (as member server, not as DC), logged in as domain admin and tried opening and writing to netlogon folder. It worked.

If you have more specific permission settings and limitations for your shares, you will have to look into it. By default, it is working as expected for me.

Also, be sure to go through your notes if you started changing things while trying to fix the samba error. You might have changed something that now affects writing to the shares.

---

### Post by burden50 on 2016-05-19
I am experiencing the same issue but installing winbind and setting my file system with the noatime flag lets me access the NETLOGON and sysvol. 

I still cannot manage any group policies using RSAT in Windows 10 it throws the error: System cannot find the file specified

I am trying to compile samba 4.3.3 from source on 16.04 and see if that fixes this issue.

It does seem that alot of samba functions are more complex to configure in the package that shipped with 16.04

---

### Post by freesbee on 2016-05-23
In my case it applies to **ANY samba share** (whatever privileges) when being accessed from the **[FONT=arial][COLOR=#FF0000]system context[/COLOR][/FONT]**. Maybe this could confuse when trying to figure out why NETLOGON and SYSVOL cannot be accessed properly.
I have been searching around for hours, and this seems to be the only place where an issue similar to mine is being discussed.
For a number of reasons I need the [COLOR=#ff0000]**system context**[/COLOR] to be able to access and read certain  public network shares. These shares are located on a samba server, and are public read to everyone.
Environment is [FONT=courier new]WORKGROUP[/FONT] (the issue appears not to be happening in a domain environment, but I cannot "certify" that in this moment).
Also the issue appears to be happening ONLY on samba shares (I have other "non-samba shares" working properly).
Samba server is a 4.3.9 on Ubuntu 14.04 x64, as a standalone server, simply publishing a few public read-only shares.

I can confirm that with [FONT=arial]**Samba 4.3.9**[/FONT] and **Ubuntu Kernel 3.13.0** the user "**[FONT=courier new]nt authority\system[/FONT]**" (the "**[COLOR=#ff0000]system context[/COLOR]**") cannot access these shares any more: in the image below the cmd window in [COLOR=#ff0000]RED[/COLOR] is the one executed as [FONT=courier new]System[/FONT], while the [COLOR=#ff8c00]YELLOW[/COLOR] one is being executed as any other user (on Win10 10586).
[ATTACH=CONFIG]269254[/ATTACH]
The same command executed under 2 different "contexts" gives different results.

I can also confirm that 2 months ago all this was working perfectly (under Win7, 8.x, 10, both 32 and 64 bit). Of course my [FONT=courier new]smb.conf[/FONT] file has not been changed since then.
Rolling back **Samba to 4.1.6** also does not fix the issue, but I can  confirm that 1 month ago (april 2016) this was working "as expected"  (system context could parse samba public shares). I am not able to roll back the ubuntu kernel to that one, that's unfortunately too much for me.

Now this issue in Win10 is quite critical for a couple of my implementations. I am in the condition of providing a quite good testing environment for such issues, even if I am still not at the level of implementing samba as AD controller.
Any suggestion would be very welcome.

---

### Post by darkod on 2016-05-23
If you suspect it's a kernel issue, and depending how many old kernels you kept, you can boot an older kernel.
Connect monitor and keyboard to the server (if it's headless) and reboot it. Be ready and on the grub menu hit the down arrow key ( by default you have only 3secs before it boots the default entry). Once you hit a button the time count stops. Select the Ubuntu Advanced entry which should list older kernels. Boot the one you want.

But I have standalone ubuntu 14.04 with samba 4.3.9 ( it upgraded about a month ago I think) and open to all public RW shares, and they work just fine. Of course, I haven't tried opening them as systen user...

---

### Post by freesbee on 2016-05-23
> **darkod said:**
> (...)
But I have standalone ubuntu 14.04 with samba 4.3.9 ( it upgraded about a month ago I think) and open to all public RW shares, and they work just fine. Of course, I haven't tried opening them as systen user...

...this is happening to me on 3 independent systems. If you have a moment to test it as system maybe you could clear me the doubt that it's not my configuration mistake.
It's very easy: unpack the PSTools ([https://technet.microsoft.com/en-us/sysinternals/psexec.aspx](https://technet.microsoft.com/en-us/sysinternals/psexec.aspx)) and in an elevated cmd run

[FONT=courier new]PSexec.exe -i -s cmd[/FONT]

that new cmd will be running as [FONT=courier new]**[COLOR=#FF0000]nt authority\system[/COLOR]**[/FONT]

Then simply DIR any of the samba shares and the problem should occur (it must be Win10, because Win7 works fine).

In the meantime I could boot into the 3.13.0-83.127 and there was no difference in the behaviour. I am not an ubuntu kernel expert, so I don't know when this one was the "current".
What I can confirm at the moment is that **Samba 4.1.6 + ubuntu kernel 3.13.0-83.127** give the problem. Thus it appear to be "samba related".
To be honest it appears to be related to some surrounding components of samba.

So I checked around the systems I have, and I can report the following:

Samba 4.1.6 + kernel 3.13.0-83.127: problem PERSISTS
Samba 4.1.6 + kernel 3.13.0-86.131: problem PERSISTS
Samba 4.3.9 + kernel 3.13.0-86.92: problem PERSISTS
Samba 4.3.9 + kernel 3.19.0-56.66: problem PERSISTS
Samba 4.3.9 + kernel 3.16.0-45.60: problem NOT PRESENT (but this environment is an AD DOMAIN no way for me to test WORKGROUP at the moment)

I am totally lost.

---

### Post by darkod on 2016-05-23
I get the same message as you, that the operation can't be performed.

But I'm still unsure if this is how windows and ubuntu/samba communicate with this system user. Can you use any users that you have created to do your tasks? That should work, right?

---

### Post by freesbee on 2016-05-23
> **darkod said:**
> I get the same message as you, that the operation can't be performed.

But I'm still unsure if this is how windows and ubuntu/samba communicate with this system user. Can you use any users that you have created to do your tasks? That should work, right?

Yes, it works, but it's not a practicable solution for me.
And I am quite sure that it is not an authentication problem (I tried to mount from system context with the /USER:fooo parameter, and that was also failing). When system context accesses a samba share, it is normally showing up as a user like [FONT=courier new]%COMPUTERNAME%$[/FONT] (the name of the computer plus a $ at the end) and that's it.

I need the share to be accessed by NTAuthority\SYSTEM because that is the user running the StartUP and ShutDOWN scripts in a Windows machine (at least starting from Win7). All my Windows machines are running those scripts to dynamically update some programs that are installed. If I loose that functionality I will loose a project that took me about 3,5 years to develop, which is currently maintaining about 85 workstations (Win7, 8.1 and 10) in different locations. The first 25 Win10 machines are in a DOMAIN, and for that reason I guess things are still working fine ( :???: not sure of course :???: ). As the first Win10 machine in a WORKGROUP came last Friday, I noticed that something was wrong. Initially I thought of a Win10 issue, but today I figured out that it is for sure NOT a Win10 issue.

My only workaround for the moment is to replicate the shares on a Windows server and let the scripts run over those shares, but it is not exactly my preferred solution because the synchronization happens on the linux machines.
Knowing where the problem is (samba version? ubuntu kernel?) would at least help me to understand how to handle the coming updates: right now it's a nightmare!!
Maybe if you could also post your "sambaversion + ubuntu kernel" combination that could help understanding were the problem could be?

---

### Post by freesbee on 2016-05-25
> **freesbee said:**
>  (...)
My only workaround for the moment is to replicate the shares on a Windows server and let the scripts run over those shares (...)

...unfortunately this is also not a practicable solution ](*,) because apparently there is no way for a windows server to expose a public share accessible from system context of OTHER members of the same WORKGROUP (this also explains why in the DOMAIN environment the problem is not present).
More info will follow...

---

### Post by freesbee on 2016-05-29
Over the weekend I saw a couple of samba updates coming, but no difference.
I tested also on Ubuntu 16.04 (kernel 4.4.0-22.40) and there is no difference in the behaviour.
I am 100% sure that 2 months ago this was working properly.
Shall I try to report it as a bug to samba community?

---

### Post by matthew138 on 2016-06-20
I'm also experiencing this issue. Installing Winbind gave me read/write access but I can't write folders (which means no new GPOs without using samba-tool first). I'm on Ubuntu 14.04.4 ( 4.2.0-38-generic kernel); Samba version 4.3.9.

I had thought it was an apparmor issue but even adding the sysvol directories to the samba abstraction didn't help.


I'll wait to see what happens.
:popcorn:

---

### Post by cartasegnals on 2016-08-11
Hi there, 

Perhaps its too late but had te same issue, but for i do not know what reason samme command worked using the domain name:


```
[xxx@xxxx user]$ smbclient -L localhost -U%
Connection to localhost failed (Error NT_STATUS_UNSUCCESSFUL)
[xxx@xxxx user]]$ smbclient -L domainName -U%
Domain=[DOMAINNAMEEXAMPLE] OS=[Windows 6.1] Server=[Samba 4.3.2]


    Sharename       Type      Comment
    ---------       ----      -------
    netlogon        Disk      
    sysvol          Disk      
    perfiles        Disk      
    scripts         Disk      
    IPC$            IPC       IPC Service (Samba 4.3.2)
Domain=[DOMAINNAMEEXAMPLE] OS=[Windows 6.1] Server=[Samba 4.3.2]

```

---

### Post by elliot-labs on 2016-10-06
I am writing in to confirm that the issue is still present in version 4.3.11 with ubuntu server 16.04.1 x64.

Installing winbind allowed me to join computers to the new domain, I can also create GPO.

---

### Post by rdratlos on 2017-01-18
I also had this problem using Samba version 4.3.11. With help of winbind I was able to access the shares (sysvol, netlogon), but only with read access even as administrator. From Windows 7 I was not able to read the secuity descriptor of the shares and the maximum allowed user option was reported to be 0. No chance to change this, either.

By chance I have found a solution to my problem. I hope it will help also others:

Please check the server services settings in your smb.conf file. After domain provisioning I had the old smb service instead of the s3fs service, which is required for SMB v3 protocol. After replacing smb by s3fs I was able to access the shares, their security descriptor and was able to manange and edit GPOs. Here are my updated smb.conf settings:

> 
server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, s3fs
    dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
    idmap_ldb:use rfc2307 = yes



I hope this helps. I do not know, if this is a bug within the Ubuntu scripts or if I have changed the server service settings to smb during my long lasting activities to fix this issue.

---


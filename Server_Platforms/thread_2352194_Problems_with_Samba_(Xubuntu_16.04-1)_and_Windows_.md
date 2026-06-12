---
title: "Problems with Samba (Xubuntu 16.04-1) and Windows 10"
date: 2017-02-10
forum: Server Platforms
---

### Post by jamesr on 2017-02-10
Good Morning except it is not a good morning see following.

I have 2 test file-servers using 16.06-1 (64bit) with the appropriate samba and both will not connect to W10 PC's. One (M) is clean build from scratch and the other (K) was a system  that had been upgraded from 14.04.
System K 14.04 => 16.04 had  working Samba connections. But I had to upgrade from 16.04-1 (32 bit) to 16.04-1 (64bit) because of problems with my archival software needing 64bit. but I cannot get W 10 to see or login the servers.

In fact, the 2 servers exhibit different symptoms so I believe that I have missed something in the setup. I have been using Samba for several years on several systems, with no real problems except getting used to the changes that Microsoft bring in with every new version. But I am probably not "seeing the wood for the trees" so I need some help.

I have checked directory permissions and ownership, the correct passwords, etc.

As I stated previously,, the 2 systems exhibit different symptons :-

System K I do not see at all in windows, no entry in the "make new network connections" wizard. I must be missing something or setting up something incorrectly.
System M I see M in the wizard but cannot connect.

On the MIcrosoft site, there are are a lot of questions about connection problems, Samba to W10 but they give information about activating the synchronisation bit but only for the Windows server software. 
I use master copies of smb.conf  as smb.conf.master and use testparm to generate smb.conf.

I have not attached any files of results but I will supply them when needed,and in order.  I just need to go through the fault finding, in order, with at least another set of eyes viewing the outputs. Possibly start with System K and then lead onto M.

Best Wishes 
Jim R

---

### Post by LHammonds on 2017-02-10
I have several 16.04.2 LTS Ubuntu Servers running and on each one I enable Samba so I can copy files to/from Windows 10/7/2008/2012 and have not had any issues.  Been running Linux servers since 10.04.

Are you trying to do authentication with them or just present guest-access shares?

I have documented how I setup samba here (section titled "Configure Ubuntu for File Sharing"): [Installing Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220)

If you need help configuring Windows so Linux can connect to it, I have that also documented further down on that page here: [Configure Windows as a Remote Mount Point](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220).

LHammonds

---

### Post by jamesr on 2017-02-10
Hi, 

Thanks for your reply, I normally have no problems as I stated before,  having used Ubuntu or more recently Xubuntu since before the days of Dapper i.e. 6.04. 

I have downloaded your blog and I will compare it with my notes.


As an additional comment, re fault finding, I can ping to all of the devices Linux to Windows and Windows to Linux.

Seeing your comment > : Configure Windows as a Remote Mount Point.
reminded me that I am still able to copy to and from the W10 PCs  from/to the 14.04 servers. The only combination that does not work Xubuntu 16.04-1 (amd64 i.e. 64bit) as a server whereas as all others are happily running. I know that you should not use GUI but it is helpful at times when fault finding, even though I normally use the CLI.

I also note that you said> 16.04.2 LTS Ubuntu Server so there may be difference between the Xubuntu and Ubuntu sites re the versions but these systems were both updated to latest on-line  version


Thanks again

---

### Post by LHammonds on 2017-02-10
Here are some versions about the Ubuntu Server 16.04.2 LTS that I'm running...maybe compare to yours:

```

#uname -a
Linux srv-mysql 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

```

#lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial

```

```

#samba --version
Version 4.3.11-Ubuntu

```

If you have UFW running, might want to do a "ufw status" to verify the right ports are open.

Example commands to enable samba file sharing connections:
```

ufw allow proto tcp to any port 135,139,445
ufw allow proto udp to any port 137,138

```

---

### Post by jamesr on 2017-02-12
Hi,

Thanks for the reply I had forgotten about the firewall, although I do not use it because the servers are always behind  firewalls but I wondered if 64bit installed it automatically.

Here is the information in order.
> :~$ uname -a
Linux mcgonagall2 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
mcg@mcgonagall2:~$ 
so I checked with sudo apt upgrade 71MB of additions. Updated using software updater.
Then reran your questions.
 > mcg@mcgonagall2:~$ root
[sudo] password for mcg:  
New alias definations
rm_script_aliases
Sub calls
temp aliases file has been loaded
call rm_script _aliases_2

root@mcgonagall2:~# uname -a
Linux mcgonagall2 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

root@mcgonagall2:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

root@mcgonagall2:~# samba --version
Version 4.3.11-Ubuntu
root@mcgonagall2:~# ufw status

Status: inactive
root@mcgonagall2:~# 


All as your system.

Although I did notice when doing other checks, that my alias smbtest='testparm -s /etc/samba/smb_mcg.conf.master > /etc/samba/smb.conf' seems to remove read only = no when it generates the smb.conf file so 
> root@mcgonagall2:~# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[allusers]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	workgroup = changed
	server string = %h server (Sam,Xub)
	interfaces = 127.0.0.0/8 eth0
	bind interfaces only = Yes
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare max shares = 30
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	directory mode = 0700
	browseable = No


[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes
	browseable = Yes


[allusers]
	comment = allusers access
	path = /shared/allusers
	create mask = 0755
	guest ok = Yes
	browseable = Yes

I also noted running
page 12 heading Configure Ubuntu for File sharing
 line 11 the test from the windows PC run \\192.168.123.83
generate the file explorer window but I could not copy anything into it. No Entry symbol.
used the cmd window
 to ping 192.168.123.83 all ok
 \\192.168.123.83 could not access
using the server name no access
back to run window no access ????

---

### Post by LHammonds on 2017-02-13
In the "Global" section, you have the following lines that mine does not (which is pretty-much default on mine):

```

    interfaces = 127.0.0.0/8 eth0
    bind interfaces only = Yes
    usershare max shares = 30
    comment = Home Directories
    valid users = %S
    read only = No
    create mask = 0700
    directory mask = 0700
    directory mode = 0700
    browseable = No

```

The most interesting are the "interfaces" and "bind" lines which seems like it is limiting samba to the local interface and not allowing it to work on the LAN/WAN.  Might be wrong in how it works since I have not added those entries before.

Regarding the not able to write files, you need to make sure folder permissions are set correctly on /shared/allusers

Example:
```

#ls -l /shared/
total 1
drwxrwxrwx 2 nobody nogroup 1024 Feb 10 08:07 allusers

```

---

### Post by Morbius1 on 2017-02-14
There is something else you might want to correct. At the bottom of the [global] section you have this:
> idmap config * : backend = tdb
	[COLOR=#0000cd][B]comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	directory mode = 0700
	browseable = No[/B][/COLOR]
The highlighted section is the remnants of a homes share except you have no section heading. You need to insert the [homes] section header so that it looks like this:
> [COLOR=#0000cd]**[homes]**[/COLOR]
[COLOR=#000000]comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	directory mode = 0700
	browseable = No[/COLOR]

If you don't then the "valid users =%S", create masks, "browseable = No", etc .. will be applied to all shares unless it's overridden further on since samba will include that as part of the [global] section.

---

### Post by jamesr on 2017-02-14
Hi LHammonds & Morbius1

Thanks for the replies, bur I will deal with them separately

Hi Lhammonds,
 with reference to your reply.
I had already compared to smb.conf.master files one from K and from M. I had mentioned previously one could be seen and the one I sent could not be seen by the network? The differences where the two lines that you  mentioned , I had already commented out and now I can  see  them on the network, therefore I agree with your they are not necessary in this case. 

I first checked with nmap/zenmap and I see all PC's on the network. Then I commented out the 2 offending lines ,ran testparm directly not using my alias, restarted smbd & nmbd  and I could see the PC's on smbtree. This, I assumed was a positive result but I now could see both on ""add network location" (W10), but I still received the error "access is denied" on the W10 PC. At least, they were both behaving in the same manner.I googled "access is denied & w10" and found a link to the Microsoft site about disabling SMBv2 and SMBv3 in Windows 7, but this can from  W10 link. As yet I have not had time to check this out.

Hi Moribus,

We last had contact re  with a problem  my alias smbtest='testparm -s /etc/samba/smb_mcg.conf.master >/etc/samba/smb.conf' when update changed the way one of the commands worked. This is  the current one, albeit that I seem to have problems now with new version but only with 16.04-1/2.. It still works correctly with 14.04.

Back to the current problem, I was not looking at the homes section so thanks for pointing that problem out to me. But that maybe related to my alias problem but I will check. I will not run the alias but the full line.

When googling for  "access is denied & w10",  I found link to one of your replies which suggested changes to the smb.conf.master to add  symlinks references, is that valid in this case or should I look the more closely at the Microsoft help reference 2696547.

To both thanks to both of you for the help. I will be away of business for a 3 days, so I will not be able to respond, I will see only on my tablet but not able to test on test servers.

Thanks Again and Best Wishes

---

### Post by Morbius1 on 2017-02-15
*** So I took an Ubuntu machine and added a share:
> [Test]
    path = /mnt/Test
    read only = No
    guest ok = Yes
*** Made /mnt/Test have permissions of 777

*** Then I added the one item from your [global] section to my own [global] section:
> valid users =%S

When I try to access the Linux box from WIn10 this was the response:
[ATTACH=CONFIG]273728[/ATTACH]
Take out the "valid users = %S" line and I am no longer prompted for credentials befor I can view the shares on the box and have access to the Test share.

So either:

** Remove the "valid users" line from the [global] section.
** Or add the [homes] section header back where it belongs.
** Or create a local linux user with the same name as the Win10 user and give it a samba password. If you make the samba password match the Windows login user's password access to your public share will be seamless.

[COLOR=#0000cd]*An additional fun fact concerning name resolution: Windows 10 has joined it's brothers and sisters ( Linux and macOS ) and can speak mDNS now so I can access my Linux box with this in Win10:*[/COLOR]
```
 \\vub-16041.local
```
[COLOR=#0000cd]*You can access a Win10 machine that way as well but you will need to add a firewall rule in Win10 to make it happen.*[/COLOR]

---

### Post by jamesr on 2017-02-20
Hi,

Thanks for the additional suggestions and apologies about the slow reply. This reply is just a short update to update the information.

After getting back from my business trip, I tried your suggestion 1 server M
> [Test]
path = /mnt/Test
read only = No
guest ok = Yes 
> Made /mnt/Test have permissions of 777 All of this I had done before but not with the permissions of 777 but, just case, I made made a typo I repeated by copy and paste your lines.
>  remove "valid users = %S"  done
Restarted samba twice 
method 1 my alias smbrestart3
no change still get a similar error as seem in your attachment.
method 2 ```
smbd restart
nmbd restart 
```
still no change

Returned to the problem later and repeated for Server K    SUCCESS I was able to see server plus directories
[ATTACH=CONFIG]273809[/ATTACH][ATTACH=CONFIG]273810[/ATTACH]
I will now be removing the Test link in smb.conf and trying again. I do not normally have ```
guest ok = yes
```in my server setups. I do not normally allow guests.
 But this a great advance forward. The only difference from my normal mode of setting up was that I did not use my aliases. I manually added your test setup on the end of my smb.conf instead of editing smb.conf.master and then using testparm as part of an alias to convert smb.conf.master to smb.conf.

More testing to follow.

---

### Post by jamesr on 2017-03-12
Hi Folks,

Sorry about the long delay but I have not been able to reply earlier. The problem is partially solved.

Morbius1 re your test directory, I see the directory but cannot write to it. so I shutdown the PCs K and M.

After returning and rebooting and could see my allusers (K) directory on one of W!0 pro PC, still could not it  see from the other PC. Checked logging to the account directly on K and could not login, re-entered the smbpassword so after a reboot, both W10 PCs could see the K /shared/allusers directory. So the problem with the second PC was an incorrect password and yet I thought that I had checked that before. 

Returned and repeated for M i.e. rebooted , lo and behold I could see the M /shared/allusers no change to the files. Again after a complete reboot but 2nd PC again could not see the M /allusers directory.  

Returned again Friday rebooted K & M Just to checkout the backup software would run successfully a partial success on M would not run as a cron task from root but running the script that I called in root cron manually.

While typing this reply I thought that I would check access from the other W10 Pro PC, it works!! so fully solved  but why I am not sure except for the need to reboot the system not just restart the services, another puzzle but it works.

I will not as yet mark it solved until I have checked of a couple of weeks.

To you both thanks for the help 

to LHammond I have some questions re your mediawiki and mysql/mariadb  tags in your signature. I know that  this is not the correct forum to ask these questions what forum would you suggest. 

Thanks again and Best Wishes
Jim

---


---
title: "Help with Win9x, OS/2, DOS, &amp; WfW access to SAMBA"
date: 2018-05-18
forum: Virtualisation
---

### Post by reidrik on 2018-05-18
Hello,

Here goes my first post to this group... I am using Lubuntu 17.10 virtualized on VMWare fusion running on my MacBook Pro. I am hoping to use the VM as a networking bridge to all of my old Macs and PC OSs so that they can share text files to the VM and edit existing text files. Good progress has been made on the Mac side with help from the Applefool article referenced in this [post]("https://68kmla.org/forums/index.php?/topic/46647-the-definitive-guide-to-connecting-your-se30/&do=findComment&comment=578951"). Netatalk 2.1.6 is running and various old Macs (SE/30, IIsi, G4 tower) running OS 6.0.8 to 9.2.2 can connect and share/edit files. Note, the Lubuntu VM and all machines referenced are ethernet connected via my old Hawking Technology Skyhawk wifi router.

I installed SAMBA on the VM with instructions in this [article]("https://www.howtogeek.com/176471/how-to-share-fiwww.howles-between-windows-and-linux/"). smbd -V reports Version 4.6.7-Ubuntu. With the smb.conf listed below, here is what works (access the VM, create and edits files):
[LIST]
[*]The MacBook Pro host can access the Lubuntu VM
[*]Windows XP works; this is a standalone PC
[*]The following are all OSs on a multi-OS PC
[LIST]
[*]Windows NT 3.51 Server works
[*]Windows NT 3.51 & 4.0 Workstation work
[*]Windows 2000 (not tried yet)
[*]Windows NT 4.0 Server (not tried yet)
[*]BE OS 5.0 (not tried yet)
[/LIST]
[/LIST]

Here are the OSs on the multi-OS PC that don't work and some comments...

DOS 6.2.2
[LIST]
[*]Attempting to net use x: \\Lubuntu-vm\tc fails with "access denied" after entering the correct password
[*]Note, when I do the lanman login at boot, I am asked if I want to create a password file and I have always said "N"
[/LIST]

Window for Workgroups v3.11 (I think this is the correct version)
[LIST]
[*]Sees \\LUBUNTU-VM when browsing MSHOME
[*]When attempting to map network drive to \\LUBUNTU-VM\TC
[*]"Access Denied" after correct password was entered
[/LIST]

Windows 95, 98, & ME

[LIST]
[*]Sees \\LUBUNTU-VM\IPC$ when browsing MSHOME (see Notes below RE printing...)
[*]When attempting to access \\LUBUNTU-VM\IPC$ "Access denied" after correct password
[*]When attempting to map network drive to \\LUBUNTU-VM\TC
[*]"Access Denied" after correct password was entered
[/LIST]

OS/2
[LIST]
[*]Sees \\LUBUNTU-VM it its network viewer thing
[*]I cannot connect to it from an OS/2 command prompt with "net use"
[*]I don't recall if it was Access Denied or if the machine could not be found
[*]I have not tried this OS again after adding "lm announce = yes" which was a tidbit found on the interweb
[/LIST]

Notes:
[LIST]
[*]DOS, WfW, Win9x, OS/2 all can successfully network and connect to the XP PC
[*]MSHOME is the workgroup on all of the OSs
[*]TC is both a user on the Lubuntu VM and has a SAMBA user
[*]All OSs use TC as the user on the machine
[*]I don't care about printing from these old OSs so the print-related entries have been removed
[*]Security is not a concern as this is a closed home network
[/LIST]

I have been Googling and poking through current and old Samba manual pages and below is my smb.conf 
I have seen references to hacking the Win9x registry for plain text passwords but that won't help the DOS side of the equation. THere was also some reference to setting "password level = 8" but I could not find details on this. 
I'd greatly appreciate any input on getting the above OSs on the multi-boot PC working.  

THx!!


```

tc@Lubuntu-VM:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    workgroup = MSHOME
    lm announce = Yes
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    server max protocol = NT1
    client lanman auth = Yes
    client NTLMv2 auth = No
    client plaintext auth = Yes
    lanman auth = Yes
    map to guest = Bad User
    ntlm auth = Yes
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb




[homes]
    comment = Home Directories
    browseable = No
    create mask = 0775
    directory mask = 0775
    read only = No
tc@Lubuntu-VM:~$ 



```

---

### Post by monkeybrain20122 on 2018-05-18
Are you running a museum? :o

---

### Post by reidrik on 2018-05-18
Funny that you mention that because that is the name of the multi-boot PC...Museum

---

### Post by reidrik on 2018-05-24
I found this very helpful post that described the Samba configuration needed to achieve what I was looking to do:

[https://www.lazybrowndog.net/freedos/virtualbox/?page_id=374](https://www.lazybrowndog.net/freedos/virtualbox/?page_id=374)

Posting the instructions here too:[INDENT]
[COLOR=#2B2B2B][FONT=Lato][FONT=inherit]1. Create a share[/FONT][/FONT][/COLOR]
[COLOR=#2B2B2B][FONT=Lato]Open a GNU/Linux terminal and type as root:
[/FONT][/COLOR]
mkdir /home/share

[COLOR=#2B2B2B][FONT=Lato]DOS will not login with a user name, so make the folder owned by &#8220;nobody&#8221;:
[/FONT][/COLOR]
chown nobody:nogroup /home/share

[COLOR=#2B2B2B][FONT=Lato]With &#8220;chmod&#8221; set the UNIX permissions for the directory recursively (-R) for all (a) to &#8220;read&#8221; (r), &#8220;write&#8221; (w) and special execute (X). The &#8220;X&#8221; makes only directories executable (able to open), but not files. So command as root:[/FONT][/COLOR]

chmod -R a+rwX /home/share[COLOR=#2B2B2B][FONT=Lato][FONT=inherit]2. Configure Samba[/FONT][/FONT][/COLOR]
[COLOR=#2B2B2B][FONT=Lato]
In our example we use a very simple smb.conf. DOS doesn&#8217;t use usernames and passwords to limit the access to files. Instead it allows or disallows access to shares. Now command as root:
[/FONT][/COLOR]
nano /etc/samba/smb.conf

[/INDENT]
```
[global]
   workgroup = WORKGROUP
   lanman auth = yes
   client lanman auth = yes
   bind interfaces only = No
   map to guest = Bad user
   mangle prefix = 6

[share]

   path = /home/share
   comment = simple share
   guest ok = yes
   guest only = yes
   public = yes
   browseable = yes
   writeable = yes    
   read only = no
   create mask = 0644
   directory mask = 0777
   delete readonly = Yes
   dos filemode = Yes
   ; I added the following for MacOSX: 
    veto files = /._*/.DS_Store/[INDENT][COLOR=#2B2B2B][FONT=monospace]  
[/FONT][/COLOR][/INDENT]

```[INDENT]
[COLOR=#2B2B2B][FONT=Lato]
Basically this means everybody is allowed to read and write to &#8220;/home/share&#8221;. Username and group are forced to be &#8220;nobody&#8221; and &#8220;no group&#8221;, so at least there is not much you can do with it.[/FONT][/COLOR]
[COLOR=#2B2B2B][FONT=Lato]In GNU/Linux restart samba:
[/FONT][/COLOR]
/etc/init.d/samba restart

[COLOR=#2B2B2B][FONT=Lato][FONT=inherit]3. Connect...[/FONT][/FONT][/COLOR]
[/INDENT]
[COLOR=#2B2B2B][FONT=Lato]

After following these instructions I have been able to connect with all of the OSs listed except for BEOS which I am not if I was ever able to connect to another machine from.







[/FONT][/COLOR]

---

### Post by wildmanne39 on 2018-05-24
*Thread moved to **Virtualisation for a more appropriate fit**.*

---


---
title: "Sharing between Virtual guest box to another Ubuntu PC"
date: 2010-11-07
forum: Virtualisation
---

### Post by onaridge on 2010-11-07
As I worked through this problem I realized it was in fact a virtualization problem so I repost here from Absolute Beginners thread.

I have a virtual installation of Lucid Lynx as guest on a Windows 7 laptop. My other computer has Lucid Lynx installed. When in Windows, on the laptop (with Lucid as guest) I can see all my shares on my Lucid computer. But my laptop does not see any shares on that computer. My Lucid PC sees the Windows shares on the laptop as well as another computer on a different workgroup but does not see any shares in Lucid on the laptop. I have shared the pertinent folders by right clicking them and selecting share with no passwords. 

I have this info from another source, I just don't know how to proceed:
The reason you aren't seeing the desktop shares from Ubuntu Linux in VirtualBox is because the default network configuration for VirtualBox (VBox) is to use a virtual network connection between guest and host. Therefore, the IP address ranges and net masks are different. This is resolved by binding the VBox guest NIC to the real NIC in your laptop. Having a laptop complicates the problem because....you can't bind the virtual NIC to a Wi-Fi connection, only an Ethernet connection. I imagine the former connection is the way you are trying to do it.

I eventually want to dump W7 on the laptop but can't until I can share files from my Lucid PC as I stream movies from there to my laptop. I do have Samba installed on both computers. Can anyone help?

---

### Post by P4man on 2010-11-07
I dont think you have to bind anything for file sharing to work in the way you want to. Default networking mode is NAT, and that should do if you want to connect to a  file server. It likely wont allow you to share files from the VM though, but as I understand that is not what you want.

I would try on the ubuntu guest to access the ubuntu file server by IP address. So just go to smb:\\192.168.x.y\ (or whatever the IP address of your server). If that doesnt work, double check your firewall settings in windows.

---

### Post by CharlesA on 2010-11-07
NAT works fine if you are only going to access stuff from another machine on the network from the guest, but not accessing stuff on the guest from another machine.

Try using the connect to server option and punch in the ip.

---

### Post by onaridge on 2010-11-07
Is the IP of file server the same as the IP of that computer and what exactly do you mean by go to smb:\\192.168.1.100?

---

### Post by CharlesA on 2010-11-07
> **onaridge said:**
> Is the IP of file server the same as the IP of that computer and what exactly do you mean by go to smb:\\192.168.1.100?

It would be whatever the ip of the machine you want to connect to is.

---

### Post by onaridge on 2010-11-07
Ok I wasn't sure which of the options (I know it isn't FTP) so I choose Windows share and can now see all the shares on my main computer but cannot mount any of them.

---

### Post by onaridge on 2010-11-07
scratch that I can open some folders and not others. I will have to check their properties and see if I can see anything different. Getting there!

---

### Post by onaridge on 2010-11-07
nope see nothing that distinguishes one folder from the other but I guess I can move whatever I need into those folders and share them that way.

---

### Post by P4man on 2010-11-07
are the ones you cant share on an ntfs partition by any chance? Have you check the file and folder permissions, or only the permission on the share? Are you sharing through samba or right click / folder sharing ?

---

### Post by onaridge on 2010-11-07
nope ext4.

I figured out that the folders I am successfully sharing are inside the home folder on a physically separate drive than the other two shares I can't see.  For the folders, the permissions as I right click on them are identical.

here is my set up: 1 160g drive has root, home and swap
2nd drive:  160g drive has storage 1,    share 1 is here
3rd drive: 500g drive has storage 2,    share 2 is here

So it looks like I need to give permissions to those 2 other drives...but how to do that?

Oh and yes, Samba was set up and used to make the home folder work (I did not set this up) and for the others that I can see in Windows, I shared them by right clicking on the folders.

---

### Post by P4man on 2010-11-07
You may not have those drives in your fstab, and so there might be a permission problem with the mountpoints. You could try fixing that or try this

```
gksudo gedit /etc/samba/smb.conf
```

under [global] add this line:
```
usershare owner only = false
```

restart samba (or reboot)
If that doesnt help, post the output of 
```
testparm -s
```

---

### Post by onaridge on 2010-11-07
It didn't work:

windy@windy-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
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
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[test]
    path = /home/windy/test
    valid users = windy
    read only = No
    guest ok = Yes
windy@windy-laptop:~$

---

### Post by onaridge on 2010-11-07
and this is from main PC
	path = /var/lib/samba/printers

[Shares1]
	comment = Storage 1 Share
	path = /storage1/shares1
	read list = loren
	write list = loren
	read only = No
	guest ok = Yes
	hosts allow = 192.168.1.
	case sensitive = Yes
	delete readonly = Yes

[Shares2]
	comment = Storage 1 Share
	path = /storage2/shares2
	read list = loren
	write list = loren
	read only = No
	guest ok = Yes
	hosts allow = 192.168.1.
	case sensitive = Yes
	delete readonly = Yes
loren@loren-linux1:~$

as an afterthought, am I using the right service type when I connect to the server via windows share? And the only field I fill out is the IP, nothing else.

---

### Post by P4man on 2010-11-09
You seem to have a mix of nautilus and samba file sharing. 
I have to admit that confuses the hell out of me, since both seem to have different syntax for essentially the same things. 

Just to make sure I understand your situation right; the shares on storage1 and 2 dont work from windows (dont even show up?), while a third share on your / drive that is not listed below, does work?  How did you create those shares? Am I right thinking you created the storage shares using samba and the other one by right clicking a folder and enabling sharing there?

---

### Post by onaridge on 2010-11-09
> **P4man said:**
> You seem to have a mix of nautilus and samba file sharing. 
I have to admit that confuses the hell out of me, since both seem to have different syntax for essentially the same things. 

Just to make sure I understand your situation right; the shares on storage1 and 2 dont work from windows (dont even show up?), while a third share on your / drive that is not listed below, does work?  How did you create those shares? Am I right thinking you created the storage shares using samba and the other one by right clicking a folder and enabling sharing there?

No this is the situation: the shares are all seen in windows on my laptop and can be opened etc. They were set up on my main by the guy that installed Ubuntu for me on what was a windows machine. He installed Samba. The root, home and swap are all on one hard drive. I added a few shares via Nautilus (right clicking and sharing). These can also be used by my Windows partition on the laptop. Only the shares in my home directory on the 1st hard drive can be seen from my Ubuntu install on the laptop. I had installed Samba and thought I added the correct setup. The storage shares are each on a different physical hard drive so I presume he never set them up for sharing. Since your last post I have set up a dual partition with Ubuntu 10.4 and Windows 7 side by side. The setup was smooth and successful and am having the same problem. Should I try Avahi? If I knew how to move this thread I would as it is no longer virtualization now. :-)

---


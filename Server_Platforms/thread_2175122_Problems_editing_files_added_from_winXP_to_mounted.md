---
title: "Problems editing files added from winXP to mounted drive &quot;using&quot; Samba"
date: 2013-09-17
forum: Server Platforms
---

### Post by pppaperboy2 on 2013-09-17
Absolute newbie to Ubuntu but decided to use an old machune as a server and followed this guide [http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu).
This used the desktop version so i could also try out Ubuntu as well as set up a media server.
The guide went well up to not being able to create a password using smbpasswd -a.
To cut a very long story short I beleive that I may have mounted a created partion (media) and set up share via nautilus and ended up giving 777 privilages on that drive but not initially using Samba.
Managed to use sudo gksu system-config-samba working (that's when i realised Samba was not sharing) but still can't get full permissions on the drive for all users.
However if I add a file from my winXP laptop the Ububtu server does not own the file ("nobody" does) and so the file is locked to read only.
I want to be able to read and write to all files on this drive to and from both the laptop and the Ububtu Unity desktop which has it's own partition.
After this I hope to add back in some security measures.
Hope this will help to short out my mess.
                        ```
Load smb config files from /etc/samba/smb.conf 

 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
 Processing section "[printers]" 
 Processing section "[print$]" 
 Processing section "[sda3]" 
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
     idmap config * : backend = tdb 
  
 [printers] 
     comment = All Printers 
     path = /var/spool/samba 
     create mask = 0700 
     printable = Yes 
     print ok = Yes 
     browseable = No 
  
 [print$] 
     comment = Printer Drivers 
     path = /var/lib/samba/printers 
  
 [sda3] 
     path = /media/sda3 
     read only = No 
     guest ok = Yes 

```

Thanks in advance.

---

### Post by Morbius1 on 2013-09-17
Force the guest user to appear to be you - the login user of the Ubuntu server. So let's say your Ubuntu login user name is morbius:
> [sda3] 
     path = /media/sda3 
     read only = No
     [COLOR=#0000cd]**force user = morbius**[/COLOR]
     guest ok = Yes
The guest user will be converted from "nobody" to "morbius" for everything that's done - add, delete, edit, ...

---

### Post by Morbius1 on 2013-09-17
Just noticed something about your original post:
> set up share via nautilus and ended up giving 777 privilages on that drive but not initially using Samba.... Managed to use sudo gksu system-config-samba working
You are using 2 different ways to create a samba share so if you are doing it to the same target folder you will have problems. The one you showed in smb.conf is one way but the one you created in Nautilus may conflict with this. Run the following command to find out if you are sharing it twice:
```
net usershare info --long
```

You can't add the "force user" line to the Nautilus share because it's not listed in smb.conf - you'd have to add it to the [global] section of smb.conf but then it would apply to all shares. The best thing to do if you double shared is remove one type of share or the other.

---

### Post by pppaperboy2 on 2013-09-18
net usershare info --long
[sda3]
path=/media/sda3
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

Sorry only saw your first post and did what you iniyially suggested.
The above is the result with the force guest added under [sda3]. 
As I said in the OP I worked out that I may be using two systems to share so that's when I thought it best to stop digging since I was in a hole.
Do I now need to "unshare" with nautilus and just use Samba?

---

### Post by Morbius1 on 2013-09-19
>  Do I now need to "unshare" with nautilus and just use Samba?                 
Just to make this clearer, you can create Samba shares 2 different ways in Linux:

[1] A Samba Usershare
This is created in Nautilus. It's share definition does not appear in smb.conf but it's still a Samba share. You can have a certain amount of control over this type of share in smb.conf but only at a global level affecting all shares. So if you remove the share you created using system-config-samba and only have the nautilus share then you need to add the force user to the [global] section of smb.conf - right under the workgroup line is where I usually put these types of things so it's easy to find.

A Usershare is easier to create and it automatically adjusts the Linux permissions on the folder being shared to accommodate the kind of share ( guest , writable, etc.. ) you are creating but it's limited to how complex a share you can create.

[2] A Samba Classic share
This is the type created by system-config-samba. It's share definition is in smb.conf. 

This method allows more control of the share by allowing more options - especially if you access smb.conf directly.

If you plan in the future to have more complex share requirements then I would remove ( "unshare" ) the share you created in Nautilus, add the "force user" to the share definition itself as I suggested in my first post, and then change permissions ( in this case ) to accommodate a guest accessible writable share:
```
sudo chmod 777 /media/sda3
```

Either way, the one thing you do not want to do is use both methods at the same time on the same target folder.

---

### Post by pppaperboy2 on 2013-09-20
Thank you Morbius for all your help.

Went into Nautilus and cancelled the share but can stil rename and delte files both ways. 

I have the file set up as a network drive and can see it on my computer but now it won't show up on my workgroup in network places. I assume this is because Samba is now doing all the work.

I was going to now add back in some security. Is the best way to do this by limiting IP addresses in samba or will this cause problems if I decide to access the drive over the internet.

Once again thank you. It's just a shame i can't give you some good rep.

---

### Post by Morbius1 on 2013-09-20
>  I was going to now add back in some security. Is the best way to do this  by limiting IP addresses in samba or will this cause problems if I  decide to access the drive over the internet.
You actually can limit access by ip address by adding an option that looks like this:
> allow hosts = 192.168.0.100 192.168.0.101
Where 192.168.0.100 and 101 are the ip addresses of the hosts that you want to allow access. 

You can also specify the netbios name but when working with Windows this is problematic - Samba with windows works a lot better with static ip addresses:
```
allow hosts = some-host-name1 some-host-name2
```

You can add that to the [global] section  - right under the workgroup line or you can do it on a per share basis:
> [sda3] 
     path = /media/sda3 
     read only = No
     force user = morbius
     [COLOR=#0000cd]allow hosts = 192.168.0.100 192.168.0.101 [/COLOR]
     guest ok = Yes


As for accessing a Samba share over the Internet it's generally not recommended and I for one have never attempted it.

---

### Post by pppaperboy2 on 2013-09-21
Thanks again. Was going to look up the IP address route this weekend but you've been a star and told me how to do it. Cheers

---


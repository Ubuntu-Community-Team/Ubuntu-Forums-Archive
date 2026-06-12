---
title: "Samba network drive permissions"
date: 2014-12-30
forum: Server Platforms
---

### Post by andrew184 on 2014-12-30
[B]I have a samba server that I setup but I am having trouble with permissions. I have a hard drive accessible by IP address (an apple timecapsule) which I have mounted to the directory "/mnt/timecapsule". 

I can connect to, and browse the drive with my windows machine but I cannot create new folders or write to the drive. In addition I can connect and browse the drive, but I cannot create new folders using "mkdir" as the user "pi" on my linux machine as the permission is denied.

 I have spent some time editing my samba .config file trying to resolve this permissions issue to no avail. Below are the relevant contents of my samba .config file: [/B]  



[global]
        server string = %h server
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
        force user = pi


[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0775
        directory mask = 0775


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


[Capsule]
        comment = Time capsule directory
        path = /mnt/timecapsule
        read only = No
        guest ok = Yes

[B]Thanks for any help. 
-FYI I am doing this with raspbain on a raspberry pi, however I believe the process is the same in ubuntu.[/B]

---

### Post by bab1 on 2014-12-30
> **andrew184 said:**
> I have a samba server that I setup but I am having trouble with permissions. I have a hard drive accessible by IP address (an apple timecapsule) which I have mounted to the directory "/mnt/timecapsule". 

How did you mount the partition and what protocol did you use?
> 

I can connect to, and browse the drive with my windows machine but I cannot create new folders or write to the drive. In addition I can connect and browse the drive, but I cannot create new folders using "mkdir" as the user "pi" on my linux machine as the permission is denied.

I have spent some time editing my samba .config file trying to resolve this permissions issue to no avail. Below are the relevant contents of my samba .config file: [/B]  

What are the permissions at the file level (Linux) of the directory that you are sharing ("/mnt/timecapsule)?

---

### Post by andrew184 on 2015-01-02
I mounted the drive using "sudo mount.cifs //10.0.1.1/Time\ Capsule /mnt/timecapsule -o password=passwd,sec=ntlm"

The permissions of the directory "/mnt/timecapsule" by using "ls -l" are as follows: 


pi@raspberrypi /mnt/timecapsule $ ls -l /mnt/timecapsule
total 0
drwxr-xr-x 2 root root 0 Apr 20  2014 temp&#8217;s MacBook.sparsebundle
drwxr-xr-x 2 root root 0 Dec 30 22:07 Backups


I see that the permissions are listed as "root" instead of as "pi", so I did "sudo chmod 1777 /mnt/timecapsule/" but when I did "ls -l /mnt/timecapsule/" again, it seems to be unchanged.

---

### Post by bab1 on 2015-01-02
> **andrew184 said:**
> I mounted the drive using "sudo mount.cifs //10.0.1.1/Time\ Capsule /mnt/timecapsule -o password=passwd,sec=ntlm"

The permissions of the directory "/mnt/timecapsule" by using "ls -l" are as follows: 


pi@raspberrypi /mnt/timecapsule $ ls -l /mnt/timecapsule
total 0
drwxr-xr-x 2 root root 0 Apr 20  2014 temp’s MacBook.sparsebundle
drwxr-xr-x 2 root root 0 Dec 30 22:07 Backups


I see that the permissions are listed as "root" instead of as "pi", so I did "sudo chmod 1777 /mnt/timecapsule/" but when I did "ls -l /mnt/timecapsule/" again, it seems to be unchanged.

That's because you need to specify the uid and gid when mounting the partition.  I'll bet it's a NTFS or FAT32 partition that doesn't understand Linux style permissions.  The permissions are ONLY set at mount time.  FYI the command should also be *mount -t cifs blah blah blah*.  See the man pages ```
man mount 

man mount.cifs
```
From the mount.cifs man pages```
It is usually invoked indirectly by the
       mount(8) command when using the "-t cifs" option. 
```

---

### Post by andrew184 on 2015-01-02
Thanks a ton, I got it working! :p

I ended up using:

```
sudo mount -t cifs //10.0.1.1/Time\ Capsule /mnt/timecapsule -o password=mypass,sec=ntlm,uid=1000,gid=1000
```

so now my ls -l looks like:

```
pi@raspberrypi / $ ls -l /mnt/timecapsule
total 0
drwxr-xr-x 2 pi pi 0 Apr 20  2014 temp’s MacBook.sparsebundle
drwxr-xr-x 2 pi pi 0 Jan  3 03:45 Backup
```


I kept thinking that the samba settings were what was giving me trouble, guess it was just how I was mounting it all along. 

Now I just have to figure out how to reformat this command and put it into fstab so the drive automounts.

---

### Post by bab1 on 2015-01-02
> **andrew184 said:**
> Thanks a ton, I got it working! :p

I ended up using:

```
sudo mount -t cifs //10.0.1.1/Time\ Capsule /mnt/timecapsule -o password=mypass,sec=ntlm,uid=1000,gid=1000
```
...

Now I just have to figure out how to reformat this command and put it into fstab so the drive automounts.

Nice work.  

All the answers are in the man pages for /etc/fstab. 
```
man fstab
```

Something like this should work:
```
 //10.0.1.1/Time\ Capsule   /mnt/timecapsule  cifs  password=mypass,sec=ntlm,uid=1000,gid=1000      0   0 
```

See this for some more info: [http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot]("http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot")

---

### Post by andrew184 on 2015-01-03
Ok, one last thing and all will be well;

when I try to "mount -a" it says this line in fstab is bad:

```
//10.0.1.1/Time\ Capsule /mnt/timecapsule cifs password=mypass,sec=ntlm,uid=1000,gid=1000  0  0
```

I keep messing with it, but I can't get the syntax right I think.

---

### Post by bab1 on 2015-01-03
What are the errors?  Maybe it doesn't like the space in "Time Capsule".

Edit: Try //WinFileServer/Share\040name /mount/point cifs blah blah

The difference is the \040 for the space instead of just \ and a space.

---

### Post by andrew184 on 2015-01-03
Ha! That was it, I forgot that you can have spaces in the file names when using mount in the command line, but fstab doesn't like them.

Thanks so much, I'm up and running now.

---

### Post by bab1 on 2015-01-03
> **andrew184 said:**
> Ha! That was it, I forgot that you can have spaces in the file names when using mount in the command line, but fstab doesn't like them.

Thanks so much, I'm up and running now.

Very good.  Glad you got it worked out. 

Please mark the thread SOLVED.  Use the thread tools at the top of the page to do that.

---


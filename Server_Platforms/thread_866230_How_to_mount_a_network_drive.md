---
title: "How to mount a network drive"
date: 2008-07-21
forum: Server Platforms
---

### Post by theonegod on 2008-07-21
I have a NAS (Buffalo Terastation) that I want to use to store backups. It has a path of say \\192.168.1.100\backup\production to the folder I want to use. 

My question is, from the terminal how to I access such a location and how can I mount it for easy access? I have never tried to access a shared network folder from a linux terminal before and found of course the I can not navigate to it via the UNC as I had hoped I would be able to. 

Can anyone help me figure out how to mount it and access it?

---

### Post by songshu on 2008-07-21
you would need to run a service on the server that allows connections over a specific protocol to that folder.

depending on your needs there are a lot of choices with different performance benefits. SMB, NFS

you could always use scp (secure copy) that uses ssh if you want to do it in a terminal.
it would be simple as:
scp -R /folder yournameatserver@192.168.1.0:/var/backup

---

### Post by Endwin on 2008-07-21
For the NAS I will assume it is being shared using microsoft protocols. For that we can use SMBFS.

First we need it installed on our system.

```
sudo aptitude install smbfs
```

After that a simple mount command will work 

```
sudo mount //server/directory /path/to/where/I/want/it
```

There are options in man mount.cifs that explain how to add in user name in passwords  pretty much just user=myusername password=mypassword added to the command before the source and destination. Some systems may want you to specify the file system type -t smbfs will need to be added.

If the NAS is sharing files another way, appletalk, NFS, etc. let me know and I will see if I can help.

---

### Post by FakeOutdoorsman on 2008-07-21
If you're using plain SSH, then SSHFS may be of interest.  I use it to mount a remote folder from a headless server.  I can interact with the remote files as if they were on my local machine which is useful when I need to edit with something other than vi, move files, etc.
```
sshfs frink@192.168.1.145:/var/www/tarkin/htdocs /media/tarkin
```
I'm also using a NAS that shares via Samba at the office that I connect to with:
```
sudo mount -t cifs -o iocharset=utf8,noperm,file_mode=0666,dir_mode=0777 //192.168.1.153/greasedscotsman /media/greasedscotsman/
```

---

### Post by ptreaster on 2008-07-30
> **Endwin said:**
> For the NAS I will assume it is being shared using microsoft protocols. For that we can use SMBFS.

First we need it installed on our system.

```
sudo aptitude install smbfs
```

After that a simple mount command will work 

```
sudo mount //server/directory /path/to/where/I/want/it
```

There are options in man mount.cifs that explain how to add in user name in passwords  pretty much just user=myusername password=mypassword added to the command before the source and destination. Some systems may want you to specify the file system type -t smbfs will need to be added.

If the NAS is sharing files another way, appletalk, NFS, etc. let me know and I will see if I can help.
Thanks for the pointer in mounting a networked drive. I have 8 stores that I keep updated and this will help me copy updates to the shared folder in each location. I had a Windows machine doing that with tasks, but I am doing away with that server with this Ubuntu Server. Does so much more!

If I wanted to put this all in a script file so it runs during the night, is there a way to put the sudo password in the command line?

---

### Post by recoding on 2008-09-15
If your still looking at this, please look at this post ([http://ubuntu-utah.ubuntuforums.org/showthread.php?t=642788]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=642788"))

In short it says:
>  Re: Mount Network Drive
Assuming your mount command works, here is what you need to add to /etc/fstab
```
//192.168.1.110/MyFiles /path/to/mount cifs username=adminz,password=passwordz
```

Save and Exit and type
```
sudo mount -a
```

to mount the filesystems configured in fstab. It should automount next time you reboot.


I tried this, and worked fine :)

---


---
title: "Ubuntu server problem (says samba's not installed but it is)"
date: 2012-07-10
forum: Server Platforms
---

### Post by benjimenez805 on 2012-07-10
Ok,

I just installed Ubuntu server 12.04 on my pentium 4 computer, the install went great and I only choose to install samba from the list of software. When I try the samba -v command it says that samba is not installed, but if I try to edit the conf file using vi /etc/samba/smb.conf  it works and the file comes up. ubuntu says I still have to install samba4 even though a version is already installed on the system. Why is this ? is this a bug? or is ubuntu dumb and can't see where my samba is installed :confused:

I found a file called samba in the /etc/ folder but I guess it's not the program. why would the smb.conf file be there is samba was not installed??? 

I tried to install samba4 as ubuntu said by using apt-get install samba4 . I got all kinds of errors.

I am signed in as root user.

install errors
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied

e:Sub-process /usr/bin/dpkg returned as error code (1)

unknown parameter encountered: "max log size"
ingnoring unknown parameter "max log size"
syslog
unix password sync
passwd program
pam password change
map to guest
usershare allow guests
guest ok
valid users
writable
valid users
 
all gave the same two erros as above. So now when I use the samba -v command these errors come up instead of the version number.

Now this is even funny now, I tried to install samba again, a different version and now when I try samba -v it tells me that thats not a valid command. Go figure. I didn't have this trouble with Ubuntu server version 7.10, I might just have to go back to it.

---

### Post by darkod on 2012-07-10
If you are sure you selected Samba, it should have been installed. Sometimes people hit Enter without using Space to select Samba or other roles, but I guess you know how to do it.

Also, samba and samba4 are different packages, I'm not sure in what stage samba4 is. I guess it should be final if you can install it with apt-get.

If you try apt-cache show <package> it says samba conflicts with samba4, so you might try purging both, and then installing the samba package.

sudo apt-get purge samba samba4
sudo apt-get install samba

I hope you are not serious about installing 7.04. If you do decide to go with an older version, I guess the best is 10.04 LTS server.

---

### Post by bab1 on 2012-07-10
> **benjimenez805 said:**
> Ok,

I just installed Ubuntu server 12.04 on my pentium 4 computer, the install went great and I only choose to install samba from the list of software. When I try the samba -v command it says that samba is not installed, but if I try to edit the conf file using vi /etc/samba/smb.conf  it works and the file comes up. ubuntu says I still have to install samba4 even though a version is already installed on the system. Why is this ? is this a bug? or is ubuntu dumb and can't see where my samba is installed :confused:

I found a file called samba in the /etc/ folder but I guess it's not the program. why would the smb.conf file be there is samba was not installed??? 

I tried to install samba4 as ubuntu said by using apt-get install samba4 . I got all kinds of errors.

I am signed in as root user.

install errors
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied

e:Sub-process /usr/bin/dpkg returned as error code (1)

unknown parameter encountered: "max log size"
ingnoring unknown parameter "max log size"
syslog
unix password sync
passwd program
pam password change
map to guest
usershare allow guests
guest ok
valid users
writable
valid users
 
all gave the same two erros as above. So now when I use the samba -v command these errors come up instead of the version number.

Now this is even funny now, I tried to install samba again, a different version and now when I try samba -v it tells me that thats not a valid command. Go figure. I didn't have this trouble with Ubuntu server version 7.10, I might just have to go back to it.

What are you trying to install/run?  Samba 3.6 (smbd) the stable Samba or Samba4 (samba) the experimental version.

For Samba3 use ```
smbd -V
```  For Samba4 I would expect this would work```
samba -v
```

I would remove everything and install Samba 3 (v3.6)

[COLOR="Blue"]Edit: Install from either ***aptitude*** or ***apt-get*** from the CLI[/COLOR]

---

### Post by bab1 on 2012-07-10
> **darkod said:**
> If you are sure you selected Samba, it should have been installed. Sometimes people hit Enter without using Space to select Samba or other roles, but I guess you know how to do it.

Also, samba and samba4 are different packages, I'm not sure in what stage samba4 is. I guess it should be final if you can install it with apt-get.

If you try apt-cache show <package> it says samba conflicts with samba4, so you might try purging both, and then installing the samba package.

sudo apt-get purge samba samba4
sudo apt-get install samba

I hope you are not serious about installing 7.04. If you do decide to go with an older version, I guess the best is 10.04 LTS server.

Samba 3.6 will successfully install on 12.04.  I have a samba 3.6.3 server running now.

---

### Post by benjimenez805 on 2012-07-11
hi guys thanks for the input, I didn't know how to purge or anything about purge so i just reinstalled my whole system and got another new error, now with grub, it it gives an error and puts me at a recover command line. I'm trying to re install again as I type this. If my install goes well I will try to install samba again.

yes I did make sure to press spacebar and put a little star next to samba during install, but when I typed samba -v at the command prompt i got the "not installed" message. So I'm trying it all over again. I hope it works this time. I just want a simple server I can share with my win computer for file sharing. I also want to run a home server and I was able to get Abyss web server up and running on 7.10, i want to use the latest Ubuntu server with Abyss (assuming Abyss will run on 12.04). So I'm going back in to try to get this server up and running.:P

---

### Post by benjimenez805 on 2012-07-11
ok i give up,

after a reinstall i still get a grub error and the server won't load. I tried using gparted to wipe the hard drive and reformat it, but after it formats it it says it can't read the drive!? I tried to format a swap partition and it said the same thing, can't read the partition! I give up. I'm gonna download another version of linux and try to save my computer and hard drive. Puppy linux here I come!

---

### Post by darkod on 2012-07-11
> **bab1 said:**
> Samba 3.6 will successfully install on 12.04.  I have a samba 3.6.3 server running now.

I never said it wouldn't. :)

I am just not familiar with the exact package name. I thought samba is the latest version before v4 (like 3.6 you mentioned). I might be wrong though.

So, the daemon (I guess it's called that) is called smbd but what is the actual package name you would use to install 3.6?

To the OP: Look at the posts from bab1. samba -v seems to be working only with the latest samba4. Since the server cd install 3.x I guess, the result of samba -v might actually say nothing, even though you do have it installed. That might have created the whole confusion to start with.

As for the grub error, I think sometimes during reinstall it might not install grub correctly, or it was installed onto another disk if you have more than one. So you might be trying to boot the broken grub from the first install and it clearly can't work now with the partition overwritten with the new install.

---

### Post by bab1 on 2012-07-11
> **darkod said:**
> I never said it wouldn't. :)

I am just not familiar with the exact package name. I thought samba is the latest version before v4 (like 3.6 you mentioned). I might be wrong though.

So, the daemon (I guess it's called that) is called smbd but what is the actual package name you would use to install 3.6?

The Samba **package** for 3.6 is called samba. You are correct the _daemon_ (process) is called *smbd*.  The Samba **package** for 4 is called Samba4 and the _daemon_ is called *samba*. > 

To the OP: Look at the posts from bab1. samba -v seems to be working only with the latest samba4. Since the server cd install 3.x I guess, the result of samba -v might actually say nothing, even though you do have it installed. That might have created the whole confusion to start with.
Yes this does cause problems for the new user.  The command is asking for the version number of the daemon.  If you installed Samba 3 it's *smbd* and if you install Samba 4 then it's *samba*.

---

### Post by darkod on 2012-07-11
> **bab1 said:**
> The Samba **package** for 3.6 is called samba. You are correct the _daemon_ (process) is called *smbd*.  The Samba **package** for 4 is called Samba4 and the _daemon_ is called *samba*. Yes this does cause problems for the new user.  The command is asking for the version number of the daemon.  If you installed Samba 3 it's *smbd* and if you install Samba 4 then it's *samba*.

So I was correct with apt-get install samba for 3.6. ;)

Thanks for the clarification. It seems the OP has left us though.

---

### Post by bab1 on 2012-07-11
> **darkod said:**
> So I was correct with apt-get install samba for 3.6. ;)
Yes, the package is samba for v3.> 

Thanks for the clarification. It seems the OP has left us though.
I think the OP has more serious install problems.  :-(

---

### Post by benjimenez805 on 2012-07-15
ok,

I wanted to give ubuntu one last try, so I downloaded 10.04 and installed it. During the install I chose the option to use the entire disk, but I didn't use the lvm option, because I'm not sure I need it. Again when I reboot grub does not show up or load ubuntu. What I figured out from using some grub commands is that grub for some reason does not recognize the file system. I'm not exactly sure what the default file system is for ubuntu 10.04 but grub does not like it.

I fan gparted to check out the file system and it could not recognize the file system either. There were two partions  and then two more partions which I think are some kind of virtual partions because they said that they were the same size as the first too, but I know that cant be because that would be double what the hard drive is. So I was able to delete all the partitions after some messing with gparted, then I was able to reformat the hard drive and install puppy linux successfully. 

I then wanted to try again with ubuntu 10.04, so i went through the install and after a reboot, grub once again said it could not read the file system. 

Am i missing something? when I install ubuntu server 7.10 it works fine, what changed in the later versions that does not like my hard drive? I wait for an "expert" to way in on my issue and maybe give me a fix solution. :(

---

### Post by benjimenez805 on 2012-07-15
Hi guys,

Just to test I went and downloaded Debian Linux which is what Ubuntu is based on. It pretty much has the same install screens as Ubunut except for software install options. It was able to install Grub correctly and my system booted fine. So the issue is with the Ubuntu installer, it does not like to be reinstalled for some reason. It seems to not know how to deal with a Grub that is already installed. But Debian is working for me, so I'll see how installing Samba goes.

---

### Post by darkod on 2012-07-15
If you think that only grub2 doesn't correctly overwrite the old grub2 (I get the same feeling sometimes), you can always reinstall only grub2 once the OS is installed.

On another note, one possible reason is hardware raid meta data remains on the disks. Many people have used hardware or fakeraid and then simply break the array and start using the disks without taking into account that meta data remains stay there even after formatting. Ubuntu detects this with the dmraid package and can make confusion whether you are installing on raid or not, because in raid the bootloader goes to different device.

---

### Post by benjimenez805 on 2012-07-15
ok,

i installed debian and this fixed the grub issue, I then re installed ubuntu 10 and this time grub worked. So next i installed samba4 which does not seem to be working correctly with the smb.conf file. So how do i delete samba4 so I can install and older version?

---

### Post by darkod on 2012-07-15
Purge samba4:
sudo apt-get remove --purge samba4

Install samba 3.x:
sudo apt-get install samba

---

### Post by benjimenez805 on 2012-07-15
I was able to remove samba4 and install just regual samba (i think 3). so now I just have to configure it to see my network. Then i'm off to try to install php. oh joooyy!

---

### Post by benjimenez805 on 2012-07-15
Hi,

After what felt like weeks, but was only a few days I am finally up and running with Samba correctly. I also was able to install my abyss web server. Everything is running smooth, I have allot to learn about samba and linux but it's a good challenge for me. I'm working now on installing and running php5 and then enabling sqlite support. You may see a post from me about that too. Thanks for the help & tips. :P

---


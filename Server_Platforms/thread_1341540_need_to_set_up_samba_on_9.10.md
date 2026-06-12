---
title: "need to set up samba on 9.10"
date: 2009-11-29
forum: Server Platforms
---

### Post by meomike2000 on 2009-11-29
i would like to set up a network share on this machine, ubuntu 9.10 desktop,
i think that samba might be the way to go for this as i would like to set this up so that:
1. it can be accessed from multiple machines, some will be linux machines and some will be windows xp and later machines.
2. i would also like to set it up so that each user will have storage on this machine that will be set just for that user, password protected.
3. also would like to have a folder that can be accessed by all users.
4. would like to use this as a location for the printer as well.

can somebody tell me if samba is the way to go and if so where can i find some config info to help me out.

thanks in advance mike

---

### Post by BkkBonanza on 2009-11-30
If you are using regular desktop install then I believe you just need to enable the Samba (smbd) file sharing and then use Nautilus to select suitable folders to share. File sharing used to be enabled in menu item Preferences, Startup Applications. I don't see it in mine now so either I removed it or they moved it recently. It may need to be installed via Synaptics as I'm not sure of it's default install status now.

For the printer enable cupsd. I have this enabled and working and just looking where that is - now it strikes me they have moved both of these recently because they aren't in Startup Apps any more. Oh well, I'm sure someone else will chime in with their new location.

---

### Post by meomike2000 on 2009-11-30
yes it is just a normal install of desktop 9.10. but i would love to get this share figured out.

i did notice that samba was already installed and when i go to the command line and use code:

```
sudo shares-admin
```

you can set the work group and it sets this inside the smb.conf file for the samba install.....

i have not found a way to get samba to start on machine startup, i have a folder that i have created on my desktop and i can access that from my ubuntu machine but not my windows machine, and i have to right click the folder and set share options to share every time i log on to the machine....

can anybody help with this......

thanks mike

---

### Post by Iowan on 2009-11-30
A few Sama links for you:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")

---

### Post by meomike2000 on 2009-11-30
thank you.....
i will be checking those out....

---

### Post by meomike2000 on 2009-11-30
question will this type of set up share with windows machines and linux machines?

will it allow the type of share set up that i wish for.....

Nautilus Integration

If you want to be able to share folders with nautilus (the file browser), install the nautilus-share package: 

```
sudo apt-get install nautilus-share
```

or should i set up the samba.....

opinions.....

thanks,
mike

---

### Post by meomike2000 on 2009-11-30
ok, after a little research i know for me that the samba set up will be the way to go if i can figure out how to get it in the start up program list....

---

### Post by cariboo on 2009-12-01
The samba servers starts automagically after installation, you should have to do anything. If you need to start Samba manually, open a terminal and type:

> sudo /etc/init.d/start

if that doesn't start samba, try:

```
sudo service samba start
```

---

### Post by BkkBonanza on 2009-12-01
Quote:
sudo /etc/init.d/start 

That doesn't look right - probably a typo.
I think you meant more like,

sudo /etc/init.d/smbd start

(although I don't recall offhand if it's smbd, sambad, or samba)

---

### Post by Iowan on 2009-12-01
> **BkkBonaza said:**
> (although I don't recall offhand if it's smbd, sambad, or samba)```
sudo /etc/init.d/samba start 
```

---

### Post by meomike2000 on 2009-12-06
will it start again automatically after a reboot.....

---

### Post by BkkBonanza on 2009-12-06
Generally, when it is installed properly it should start automatically on reboot. If it doesn't then something isn't right. There needs to be suitable links pointing to the /etc/init.d/samba for desired runlevels in /etc/rcX.d. Usually this is done for you. If you need to change it manually you should probably read "man update-rc.d". Althought this is not the preferred way I think it can be used to put in init links.

---

### Post by meomike2000 on 2009-12-06
thanks for all the help.....

---

### Post by Roasted on 2009-12-06
Also remember to set your file/folder permissions and ownership accordingly based on the way you want your setup to be.

For example, I have 5 or 6 shares on my system. I use my system as a backup server for the other users in the house. They back up to my system everyday at 3 am.

My setup is pretty simple. Ownership is me:user group with 770 permissions:

jason:curt 770
jason:tyler 770
jason:pam 770


Etc... then I have all users in 1 group called "Samba", and then the Samba group is assigned to a "Public" share.

Just throwing out some constructive ideas in case it's something you want to do.

Good luck!

---


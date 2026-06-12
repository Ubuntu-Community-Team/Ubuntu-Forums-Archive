---
title: "login issue due to space or ....."
date: 2008-10-06
forum: Server Platforms
---

### Post by nido4u on 2008-10-06
Hello everyone
here is nido
it is my first post. i m in deep trouble, i have a UBUNTU 8.4 server version with postfix ,courier imap and ISPConfig ,
it was running f9 from couple of months but yesterday when i checked it after 2 days off. it was stuck, i have restared it forecfully and there seems errors ..

kinit: name_to_dev_t (/dev/..........
kinit:trying to resumefrom (/dev/.......
kinit:no resume image, doing normal boot...

loading hardware drivers.....
( 67.762668)intel_rng : PWH not detected 

and many services like courier, mysql, postfix etc hav shown "segmentation fault"

in the end login screen appears but accpets no user and shows help options on any user instead of password prompt..


Plzz urgently help me in this issue ...
i wd be gr8ly thankfull.....

---

### Post by lykwydchykyn on 2008-10-06
First thing to do is reboot and at the boot prompt select "recovery mode".  when you get to the menu, select "drop to root shell".

Check the following:

 - free space on drives:
```

df -h

```

 - bad blocks on the hard drive:
```

badblocks -v /dev/sda

```

 - Check system log:
```

less /var/log/syslog
dmesg

```
 - If that doesn't turn anything up, you might want to boot the Ubuntu CD and run memtest.

---

### Post by nido4u on 2008-10-06
gr8 thanx for reply

when i goes to recovery mode it asks for root password in root shell
but rejects my entry as 'bad login'
can u plz guide the if there is some syntex issue ????

---

### Post by lykwydchykyn on 2008-10-06
Did you set a root password at some point?  I don't typically get prompted for a root password when I do this.  It'd be kind of useless if you did, seeing as root login is disabled by default in ubuntu.  

You may need to boot to a liveCD to sort this out.

---

### Post by nido4u on 2008-10-06
yes root is by default disabled in ubuntu server
i have manually enabled it set the password
and as per my memory i am typig same password

additionally  i have checked using Acronis disk director i have more than 100 Gb free space for ext3 partition , i have only 1 partition
and 15 Gb swap

now i m confused wts the mess ??????????

---

### Post by nido4u on 2008-10-06
yes root is by default disabled in ubuntu server
i have manually enabled it set the password
and as per my memory i am typig same password

additionally  i have checked using Acronis disk director i have more than 100 Gb free space for ext3 partition , i have only 1 partition
and 15 Gb swap

now i m confused wts the mess ??????????

---

### Post by cariboo on 2008-10-06
If you boot up normally can you log in as root? It might be an idea to boot from your LiveCD and fsck on your hard drive.

Jim

---

### Post by lykwydchykyn on 2008-10-06
If the disk isn't full my guess is either bad blocks on the disk or bad RAM.  Boot to an Ubuntu liveCD and run the tests I suggested.

---

### Post by nido4u on 2008-10-06
dear in normal boot up i cannot login with any user including root
when i enter user at login prompt , it shows login help and again prompt login:
:(

---

### Post by nido4u on 2008-10-07
Hello all
at last i am in recovery console
i have to reset my root password 
now when i check files have segmentation error they are looking fine

wt to do ?????

any suggestion plzzz

---

### Post by nido4u on 2008-10-07
i have found that there problem with permission on drive
all files with segmentation error have this on "chmod" command
when i tried to run " chmod -R a+rw * " in recovery console it again gives segmentation error

any clue......

---

### Post by lykwydchykyn on 2008-10-07
Did you run the tests I suggested?  Your posts are a little hard to understand.

---


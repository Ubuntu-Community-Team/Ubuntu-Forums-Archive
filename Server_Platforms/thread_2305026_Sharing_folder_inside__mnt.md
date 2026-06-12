---
title: "Sharing folder inside  mnt"
date: 2015-12-02
forum: Server Platforms
---

### Post by gardenair on 2015-12-02
hi,
     In my Ubuntu box i make a new partition i.e "mysahre" mount it  as for sharing files .Previously I make a folder in root and then access it. 

```
# mkdir home-share
```

assign the group 

```
# chown -R root:pdc /home-share
```

and then assign rights


```
# chmod -R 757 home-sare

```

Now I create the folder "home-share"  inside /mnt  

```
[COLOR=#666666][FONT=Arial]# mkdir /mnt/home-share[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]# mount /dev/sda6 /mnt/home-share
[/FONT][/COLOR]
```[COLOR=#666666][FONT=Arial]
the question is should I also give group ownership and permission to " mnt" folder to access "/home-share" i.e  "/mnt/home-share"

[/FONT][/COLOR]```
# chown -R root:pdc /mnt/home-share
# chmod -R 757 /mnt/home-sare
```

Please guide me,technically what is the correct way 

thanks

---

### Post by SeijiSensei on 2015-12-02
/mnt has read and execute permissions for everyone. You don't need to change it at all.
```

$ ls -l / | grep mnt
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt

```

---

### Post by gardenair on 2015-12-02
Thanks "[COLOR=#000000]SeijiSensei" for your reply.Well my query is should I mount the partition name (which is my share folder i.e office-share)  inside /mnt folder. Actually normally i keep the share folder in "/ " .
[/COLOR]
[COLOR=#000000]I am going to take a example.Suppose you are configuring samba server and create a share folder "office-share " ,it is good to keep this  folder in " /mnt " or you keep keep it in " / ".[/COLOR]
[COLOR=#000000]Technically and professionally which is the correct way ?
 [/COLOR]

---

### Post by Bucky Ball on 2015-12-03
In my opinion best to avoid keeping ANY personal data in /. If the OS breaks and you need to reinstall your data is on the partition you may not be able to access. Also makes backing up more straightforward (and if you have more than one OS installed it makes even more sense as you don't want to be accessing your data files from the root partition of another installed OS). 

Generally best to have a /home partition and keep personal data there or just use a /data partition and symlink to folders in there. The latter is ideal if you have more than one OS. They can all be symlinked to the same directories in the /data partition. No confusion, no doubling up, no redundancy.

---

### Post by gardenair on 2015-12-03
Thanks "[COLOR=#000000]Bucky Ball" for your reply.I have only single operating system .As you have mentioned that if the OS crash then i can not access ,For that purpose I keep the personal data in a separate partition.   Well from scratch i want to draw your attention. I have install Ubuntu,keep free space.I use fdisk command and create a new partition i.e "home-sahre"  i.e 140 GB for sharing files and folder for the users.[/COLOR]

```
# fdisk -l




   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200   83  Linux
/dev/sda2          616448    82536447    40960000   83  Linux
/dev/sda3        82536448   143976447    30720000   83  Linux
/dev/sda4       143976448   625141759   240582656    5  Extended
/dev/sda5       143978496   160362495     8192000   82  Linux swap / Solaris
/dev/sda6       160364544   453965823   146800640   83  Linux
```

I mount it

```
# mount /dev/sda6 /mnt/home-share

```

Now you can see my mounted partition.
```
# df -h
/dev/sda6       140G   33M  140G   1% /mnt/home-share

```


Now when i share the folder "home-share" the user will keep their files in that separate partition which is in my case "/dev/sda6".

Even If I use /home-share the user will keep his/her files in that separate partition (if i am correct) so why I make a symbolic link ?

In Samba configuration file .

```
[public]
comment = Public Stuff
path = /home-share      <-----------This is the [FONT=Arial][COLOR=#111111]symbolic link.The actual folder is located in /mnt/home-share [/COLOR][/FONT]
writable = yes
printable = no
write list =  +staff

```

Please let me know that in the "path" is it correct to give symbolic link in the path.

---

### Post by SeijiSensei on 2015-12-03
Just use the full path:
```
path = /mnt/home-share
```

---


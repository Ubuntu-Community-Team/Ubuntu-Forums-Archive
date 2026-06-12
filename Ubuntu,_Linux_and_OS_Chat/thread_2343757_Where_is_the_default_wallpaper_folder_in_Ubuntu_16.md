---
title: "Where is the default wallpaper folder in Ubuntu 16.04"
date: 2016-11-18
forum: Ubuntu, Linux and OS Chat
---

### Post by notso23 on 2016-11-18
There were no recent posts on this topic.
I would like to put all the wallpapers in the default one so I can just click on them as per the attachment.

I know that I can create a folder in Pictures and put them all there but I was just trying to use the default one. ;)
Thank you.

---

### Post by cariboo on 2016-11-18
The same place it is in other versions - /usr/share/backgrounds

---

### Post by notso23 on 2016-11-18
I can't find any of those folders?

---

### Post by Bashing-om on 2016-11-18
notso23l Hello;

For your reference:
> 
sysop@1404mini:~$ ls -al  /usr/share/backgrounds
total 12
drwxr-xr-x   3 root root 4096 May 19  2013 .
drwxr-xr-x 159 root root 4096 Oct 13 19:02 ..
drwxr-xr-x   2 root root 4096 Jan 28  2015 xfce

sysop@1404mini:~$ ls -al  /usr/share/backgrounds/xfce/
total 160
drwxr-xr-x 2 root root   4096 Jan 28  2015 .
drwxr-xr-x 3 root root   4096 May 19  2013 ..
-rw-r--r-- 1 root root 152462 Oct 28  2014 xfce-blue.jpg
sysop@1404mini:~$

my most simple xfce ; Wherein I follow the KISS principal .

[INDENT][INDENT]I like simple
[/INDENT][/INDENT]

---

### Post by notso23 on 2016-11-18
Sorry but I have no idea what that is.

---

### Post by Bashing-om on 2016-11-18
notso23; K

Just showing what cariboo pointed out.
That standard placement for the desktop files.

[INDENT][INDENT]standards are good
[/INDENT][/INDENT]

---

### Post by deadflowr on 2016-11-18
The wallpapers themselves are in the location mentioned.
However, for wallpapers to show up in the Appearance > Wallpapers setting , and not the Pictures setting, they also need to be listed in an .xml file.
Located at /usr/share/gnome-background-properties. 

So it's not a matter of moving pictures around, but is a tad bit more involved.

---

### Post by notso23 on 2016-11-19
ok thank you ... it's all beyond my knowledge at the moment but I may catchup one day soon :p

---

### Post by notso23 on 2016-11-20
Well I finally found the /usr/share/backgrounds in files, but now it says that I don't have permission to change the folder, as I am not the owner?

Any help for this little problem. :D

Sorry I didn't read [**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577") post properly so I will learn to do more. :o

---

### Post by notso23 on 2016-11-20
Sorry I didn't read [**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577") post properly so I will learn to do more. :o

---

### Post by cariboo on 2016-11-20
As all the files in /usr/share/backgrounds are owned by root, you need to escalate privileges by using sudo to do anything in that directory , for example to copy a file from your Pictures directory to the backgrounds directory on the command line you would use a command similar to this:

```
sudo cp ~/Pictures/Picture045.jpg /usr/share/backgrounds
```

---

### Post by notso23 on 2016-11-21
Thank you Cariboo for your help, and although I am on the bottom side of the learning curve, I did it. I moved it into the folder and it show up in the folder and has root permissions. But I now have to learn how to edit the .xml file in /usr/share/gnome-background-properties/ for it to be displayed in Appearance so I can use it.

I tried to edit with text editor but it wouldn't save because it has the root permission. I suppose it needs to be edited with sudo as well?

Well I found how to do it ... simple ... ```
sudo gedit
``` command and it saved and all is good ... This learning at my age is great :D

---


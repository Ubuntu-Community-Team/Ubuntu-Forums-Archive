---
title: "Samba, write permisions, sub directories, and epic battles"
date: 2010-11-17
forum: Server Platforms
---

### Post by yettiman2208 on 2010-11-17
So this has been a long time in the works. And might take a while to explain.

Essentially, I migrated from a Windows machine to a mac machine taking with me my usb external drive. I formatted it to the HFS+ format and used it for a while. I then decided it was time to learn the ways of the server. (I have been fooling with ubuntu desktop for a while)

So I took an old laptop, loaded up Ubuntu server 10.10 and then hooked up my ext harddrive via USB.

The goal was to create a home file server where I can access and dump to my ext, do time machine backups and share to my xbox360.

Well, needless to say, easier said than done. After many days of grueling battle with the server, mounting issues, HFS+ journalling issues, samba problems, and time machine problems I have almost defeated it.

I am at the point where I am running time machine backing up to the external drive over wifi (currently on first backup.....timeeee), with read access through samba to the entire drive. My problem is this, I have write access from the Mac (over wifi) to only the parent directory ( so in this case /media/WD) where I can put files, create folders etc. All subsequent sub directories (example /media/WD/Videos) I have only read access and no write access. 
excerpt from the smb.conf file. 

[WesternD]
path = media/WD  
writable = yes
public = yes
valid users = rhorie

I dont know if you need all the .conf file, if so, let me know. I didn't automatically post it all because it still has all the comments in it and that would be obscenely long.

On a side note, if I ssh into the box and cd into the /media/WD/Videos directory I have full write access, so that is what is leading me to believe that it is a Samba problem rather than a chmod/mounting issue. (even tho that was an epic war in itself.

Also, I am hesitant to mess around to much because I finally have Time Machine backing up to it wirelessly (through, I believe, a Samba access)

(I have also abandoned the ushare xbox360 attempt for now. I had it to a point where xbox was seeing the share, but then when I tried to connect to it, it made some claims about firewall and went no further, then I started messing and the whole shebang dissapeared, and I gave up (med school exams got in the way). But the xbox does still connect to the mac shares over wifi (which are accessing the ext. harddrive from the linux box.......... over wifi). This, naturally, is not ideal, and I am not sure it fully works, I havn't tried actually running a vid from this setup yet because its absurd.)


Please also note that I did all this with very little initial command line knowledge, so it was a project of mine to learn it and figure it out. I am just stumped, and google has lead me nowhere. (very steep learning curve btw, attempting to mount a readable/writeable HFS+ journaled usb HD through ssh from my mac, not to mention getting the infernal time machine to play nice)...... I'm a noob, so please explain directions/commands for me


Appreciate all and any aid,

sincerely,
a large yetti

---

### Post by s1nch4n on 2010-11-17
> **yettiman2208 said:**
> So this has been a long time in the works. And might take a while to explain.

Essentially, I migrated from a Windows machine to a mac machine taking with me my usb external drive. I formatted it to the HFS+ format and used it for a while. I then decided it was time to learn the ways of the server. (I have been fooling with ubuntu desktop for a while)

So I took an old laptop, loaded up Ubuntu server 10.10 and then hooked up my ext harddrive via USB.

The goal was to create a home file server where I can access and dump to my ext, do time machine backups and share to my xbox360.

Well, needless to say, easier said than done. After many days of grueling battle with the server, mounting issues, HFS+ journalling issues, samba problems, and time machine problems I have almost defeated it.

I am at the point where I am running time machine backing up to the external drive over wifi (currently on first backup.....timeeee), with read access through samba to the entire drive. My problem is this, I have write access from the Mac (over wifi) to only the parent directory ( so in this case /media/WD) where I can put files, create folders etc. All subsequent sub directories (example /media/WD/Videos) I have only read access and no write access. 
excerpt from the smb.conf file. 

[WesternD]
path = media/WD  
writable = yes
public = yes
valid users = rhorie

I dont know if you need all the .conf file, if so, let me know. I didn't automatically post it all because it still has all the comments in it and that would be obscenely long.

On a side note, if I ssh into the box and cd into the /media/WD/Videos directory I have full write access, so that is what is leading me to believe that it is a Samba problem rather than a chmod/mounting issue. (even tho that was an epic war in itself.

Also, I am hesitant to mess around to much because I finally have Time Machine backing up to it wirelessly (through, I believe, a Samba access)

(I have also abandoned the ushare xbox360 attempt for now. I had it to a point where xbox was seeing the share, but then when I tried to connect to it, it made some claims about firewall and went no further, then I started messing and the whole shebang dissapeared, and I gave up (med school exams got in the way). But the xbox does still connect to the mac shares over wifi (which are accessing the ext. harddrive from the linux box.......... over wifi). This, naturally, is not ideal, and I am not sure it fully works, I havn't tried actually running a vid from this setup yet because its absurd.)


Please also note that I did all this with very little initial command line knowledge, so it was a project of mine to learn it and figure it out. I am just stumped, and google has lead me nowhere. (very steep learning curve btw, attempting to mount a readable/writeable HFS+ journaled usb HD through ssh from my mac, not to mention getting the infernal time machine to play nice)...... I'm a noob, so please explain directions/commands for me


Appreciate all and any aid,

sincerely,
a large yettifirst.. make sure user 'rhorie' has read and write access to the path 'media/WD'...

maybe u can try this... 

```
chmod -R a+rw /media/WD
```

---

### Post by yettiman2208 on 2010-11-18
I did the chmod 777 for the drive.

When I logon directly to the box, either with ssh or at the actual machine, the user "rhorie" can write to all the disk no prob.

---

### Post by yettiman2208 on 2010-11-18
Also, in the .conf file I added the unix extensions = no line with no difference.

---

### Post by yettiman2208 on 2010-11-19
Please Change to Solved.

So I figured out that I had not -R when I chmod the directory.

Very simple mistake, but I figured it out eventually. For whatever reason the user "rhorie" has full access when loging on at the machine, but then when i logged on as rhorie through samba I did not have write access to sub directories.

So a simple chmod R fixed all that.

---


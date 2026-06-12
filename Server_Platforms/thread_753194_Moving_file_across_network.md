---
title: "Moving file across network ?"
date: 2008-04-12
forum: Server Platforms
---

### Post by dbrine on 2008-04-12
I have a 2 Ubuntu Servers with mulitple HDD's. I need to move files/ Directories from 1 server to another. How do I do this? I could do it from a windows PC but would take forever.

---

### Post by volkswagner on 2008-04-12
Use NFS.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

---

### Post by dbrine on 2008-04-12
I'm new to Ubuntu Server so pardon my newbie questions... but Do I need NFS? I have samba setup and just need to relocate several files/ directories from 1 server to another. I have used scp but it keeps the old files on the other HDD and I get permission denied for some files?

---

### Post by schiznik on 2008-04-12
assuming samba is setup correctly (which it is by the sounds of it), you should be able to use smbmount (manually or from /etc/fstab) to mount the shared folders. eg:```
smbmount //server/share /localdir -o username=user,password=pass,uid=500,gid=500
```Then you can mv the files as if they were all on a local machine.

Edit: No you dont NEED nfs - this is the unix/linux equivalent of samba (as used by windows). Stick to samba if you have windows machines, if its all mac/linux, I'd migrate to NFS.

---

### Post by hyper_ch on 2008-04-12
I'd use sshfs...

---

### Post by dbrine on 2008-04-12
I was unable to get the smbmount to work. Is there anything different I  have to do since I have to linux boxes? The files are on those boxes.

---

### Post by hyper_ch on 2008-04-12
see my post :)

---

### Post by dbrine on 2008-04-12
I can't seem to get sshfs to work either. Gives me "Bad mount point"? Can I use scp -r and overwrite all files?

---

### Post by hyper_ch on 2008-04-12
you first have to create the mount point...

---

### Post by dbrine on 2008-04-12
LOL... finally got sshfs to work I can see the mount now. How do I move (command) all the files/ directories to another folders?

---

### Post by hyper_ch on 2008-04-12
when you mounted it you can move/copy files accross the same way you do it normally...

use your file manager or command line... 

I'd either us Midnight commander (mc) or konqueror as they are two-pane resp. multi-pane programs... mc is command line based but gives a ncurses interface.

---

### Post by dbrine on 2008-04-12
I'm using the command line, No GUI server. I am moving them now. thanks for all the help. How do I force it to overwrite folders? files?

---

### Post by hyper_ch on 2008-04-12
would be the -f parameter with copying... probably also with moving.... in mc you should be able to select an option after the first collission to overwrite everything

---

### Post by dbrine on 2008-04-12
this is the command I used.

[HTML] mv -f music/* /media/HDD-500-3/music
[/HTML]
 
This is the error

[HTML]I get this mv: inter-device move failed: `music/U2-2004_-_How_To_Dismantle_An_Atomic_Bomb' to `/media/HDD-500-3/music/U2-2004_-_How_To_Dismantle_An_Atomic_Bomb'; unable to remove target: Is a directory[/HTML]

---

### Post by firecat53 on 2008-04-13
You could try:

rsync -av --delete music /media/HDD-500-3/

Then delete the original folder if you're just moving it.

Or if you don't have sshfs set up, you can do it directly over ssh with:

rsync -av --delete -e ssh username@{machine name or IP address} music /media/HDD-500-3

Good luck!
Scott

---


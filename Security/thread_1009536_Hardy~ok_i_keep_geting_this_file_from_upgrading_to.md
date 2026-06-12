---
title: "Hardy~ok i keep geting this file from upgrading to hardy from gutsy"
date: 2008-12-12
forum: Security
---

### Post by KEE on 2008-12-12
the file i keep getting is is a system 32 folder and i think its coming with my installation disc to hardy from gutsy. this is the third time in a week i have to run gutsy install disc to rewrite and delete my drive and hardy to reset it and start over. then i check gutsy this time and no system32 , ok good!. know last night i installed hardy and the system32 folder is still in trash after a 3rd install of hardy? and does only bad things like used up hdd space and take a way permissions on random occasions. Please Help i think i should give up here though I tried ervything i think from using nautilus to using codes like ```
rm system32
``````
sudo rm -rf ~/.local/share/Trash/files/system32
``` going to gutsy dics and delete through recoveryboot option using these```
mkdir /media/hda
mount /dev/hda1 /media/hda
cd /media/hda/home/USERNAME/.local/share/Trash/files/
ls
rm System32.exe 
``` ```
umount /media/hda
mount /dev/hdx /media/hda
``` to change /dev/hdx to the correct partition. then tried ```
cd /home/USERNAME/.local/share/Trash/files/
ls
rm System32.exe
```. and on a note everything starts going bad what i mention about permissions and hdd space once i start downloading limewire install from [http://www.limewire.com/download/download.php?version=l](http://www.limewire.com/download/download.php?version=l)  =/

---

### Post by cariboo on 2008-12-12
I would suggest you press Alt-F2 and type:

```
gksu nautilus
```

this will run nautilus as root, navigate to the trash folder and delete the file.

Jim

---

### Post by KEE on 2008-12-23
> **cariboo907 said:**
> I would suggest you press Alt-F2 and type:

```
gksu nautilus
```

this will run nautilus as root, navigate to the trash folder and delete the file.

Jim

alright, how do i get to trash? i could not find it in applications..been searching for a while. need help finding it

---

### Post by albinootje on 2008-12-23
> **KEE said:**
> alright, how do i get to trash? i could not find it in applications..been searching for a while. need help finding it

After 
```

gksu nautilus

```
You would browse to here (click first on "File System" at the left inside Nautilus, then "home") :

/home/your_user/.Trash/  and /home/your_user/.local/share/Trash/

Where "your_user" is the username that you normally use in Ubuntu.

---

### Post by KEE on 2008-12-23
cant use image options =/

---

### Post by KEE on 2008-12-23
> **albinootje said:**
> After 
```

gksu nautilus

```
You would browse to here (click first on "File System" at the left inside Nautilus, then "home") :

/home/your_user/.Trash/  and /home/your_user/.local/share/Trash/

Where "your_user" is the username that you normally use in Ubuntu.

nope [IMG]http://www.facebook.com/album.php?aid=2000935&l=2aefc&id=1090594698[/HTML]

---

### Post by KEE on 2008-12-23
need help!!!!!

---

### Post by cariboo on 2008-12-24
Use:

```
gksu nautilus
```

Then navigate to your home directory, see screenshot1, once in your home directory press Ctrl-h to reveal hidden files and folders, then navigate to ./local/share/Trash. You will see two folders in trash, delete them both.

Jim

---

### Post by KEE on 2008-12-24
> **cariboo907 said:**
> Use:

```
gksu nautilus
```

Then navigate to your home directory, see screenshot1, once in your home directory press Ctrl-h to reveal hidden files and folders, then navigate to ./local/share/Trash. You will see two folders in trash, delete them both.

Jim

yeah i know i have that directory also, but its not there! its only in trash here ill blow it up for you  ![http://www.facebook.com/album.php?aid=2000935&l=2aefc&id=1090594698](http://www.facebook.com/album.php?aid=2000935&l=2aefc&id=1090594698) Just to let you again that this file is still in trash after several re installations of gutsy/hardy and its still there. So i think thats its ubuntu thats giving  it to me or that ubuntu cant really install correctly so that all files are erased before installing =/ they should fix their installation process so that this doesnt happen XD

---

### Post by KEE on 2008-12-29
please help!

---

### Post by cariboo on 2008-12-29
Have you enabled the delete option in Nautilus? Go to  Edit-->Preferences-->Behavior  and select Include a Delete Command that bypasses Trash. Then navigate to your Trash folder and right-click and select delete.

Jim

---


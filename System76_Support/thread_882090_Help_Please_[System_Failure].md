---
title: "Help Please [System Failure]"
date: 2008-08-06
forum: System76 Support
---

### Post by Jonathan93 on 2008-08-06
Heey guys!

Now i rly need ur help

today i brought a new mouse ( mx518 ) and was gona fix some drivers
Link: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon)

I did like the instructions said, and then restarted the computer
And got some error :( said something about graphical failure in etc/X11/XORG.conf :| I backuped that file @ desktop but now i cant get to my desktop anymore =( Since im realy bad @ this terminal thing i need good descriptions, if u can help me
And btw i dont want options as format or somethin :( Since ive got no extended harddisk and ive got some important things @ the computer and cant loose them! "/

I realy dont know what to do and i hope u guys could help me!

If i didnt tell you enough, Ask me more! I want this to be fixed as soon as possible :)


Thanks in advance Jonathan

---

### Post by raul_ on 2008-08-06
It must be a typo in the /etc/X11/xorg.conf

double check all the changes you've made. If you can't find any errors, undo all changes, or create a new xorg.conf file

---

### Post by Jonathan93 on 2008-08-06
> **raul_ said:**
> It must be a typo in the /etc/X11/xorg.conf

double check all the changes you've made. If you can't find any errors, undo all changes, or create a new xorg.conf file


I cant cos im getting only to this weird system console mode..

---

### Post by raul_ on 2008-08-06
Don't panic! :p

You can still use the system.To edit your xorg.conf file, type

```

sudo nano /etc/X11/xorg.conf

```

Edit the text, and when you're done, quit (ctrl+X) and choose to save the file (Y)

You're gonna get used to it :)

---

### Post by Jonathan93 on 2008-08-06
Hm okey could u copy ur file for me? so i can see what i need to write? :P
I only deleted the "mouse" part and pasted the other part from the link.

---

### Post by gaussian on 2008-08-06
> **Jonathan93 said:**
> Heey guys!

Now i rly need ur help

today i brought a new mouse ( mx518 ) and was gona fix some drivers
Link: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Typhoon)

I did like the instructions said, and then restarted the computer
And got some error :( said something about graphical failure in etc/X11/XORG.conf :| I backuped that file @ desktop but now i cant get to my desktop anymore =( Since im realy bad @ this terminal thing i need good descriptions, if u can help me
And btw i dont want options as format or somethin :( Since ive got no extended harddisk and ive got some important things @ the computer and cant loose them! "/

I realy dont know what to do and i hope u guys could help me!

If i didnt tell you enough, Ask me more! I want this to be fixed as soon as possible :)


Thanks in advance Jonathan

If you backed up the xorg.conf file to your desktop, then you should be able to revert to earlier settings by doing

```

sudo cp /home/YOURUSERNAME/Desktop/xorg.conf /etc/X11/
sudo reboot

```

---

### Post by Jonathan93 on 2008-08-06
It says no such file or directory

But i know i pasted it into desktop, i remember that xorg wasnt the full name of the file btw. Could u check urs for me? :>
xorg is in the end but i remember that it was somethin befor xorg.

Im felling that im close to it now!

EDIT: Is there any comand that tells me all the file names @ my desktop or somethin?

---

### Post by thomasaaron on 2008-08-06
From the terminal enter these commands:

cd /home/<YOURUSERNAME>/Desktop
ls

This will list all files on your desktop. You should see your xorg.conf file in there.

Then:

sudo cp /home/YOURUSERNAME/Desktop/XORGBACKUPNAME /etc/X11
(Note: there is a space between ...NAME and /etc...)
sudo reboot

---

### Post by Jonathan93 on 2008-08-06
It dosnt show the files ust this text´is added to my terminal name "~/Desktop$" :S nothing else happens :(

Looks like this:

```
Jonte@Fristedt:~$ cd /home/jonte/Desktop
Jonte@Fristedt:~/Desktop$
```

---

### Post by raul_ on 2008-08-06
```

ls

```

---

### Post by thomasaaron on 2008-08-06
:popcorn:

You've got to follow *ALL* of the directions.

---

### Post by Jonathan93 on 2008-08-06
It works!! :DDD THANKS ALOT MATES! <33

---

### Post by phyzome on 2008-08-06
Now would be a great time to look up some of the more common commands:

ls
mv
cp
cd
rm (Careful with this one! It's permanent.)
touch
locate

And most importantly: man

You can look up how to use just about any command by typing "man" before it. Example: "man cd" would tell you about the "cd" command.

---


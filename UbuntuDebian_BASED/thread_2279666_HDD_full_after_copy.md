---
title: "HDD full after copy"
date: 2015-05-25
forum: Ubuntu/Debian BASED
---

### Post by p.callan on 2015-05-25
I think this is pretty easily solved I just dont know how.

I tried to upload a ton of files from an external HDD to my Dropbox. But the cache/ swap/ temp or whatever got full and then it stopped uploading. I'd like to clear this out (about 200gb) and in a second step, increase the swap space. (The entire HDD is 350gb but the swap is only 2,9gb and I keep zero of my own documents, downloads or other files on this HDD, which is the way I like it). I can't find where this blob of data is located beyond /dev/sda1.

Thanks for any help on this.



Elementary OS (Ubuntu 12.04)

---

### Post by nerdtron on 2015-05-25
> I tried to upload a ton of files from an external HDD to my Dropbox. But  the cache/ swap/ temp or whatever got full and then it stopped  uploading. I'd like to clear this out (about 200gb) 

I can't fully understand this. Can you elaborate? Which folder and partition got full and what files do you want to delete? It would be better if you  post the output of the following so that we can see your situation better.
```
lsblk
df -h 
```

> and in a second step, increase the swap space. (The entire HDD is 350gb  but the swap is only 2,9gb and I keep zero of my own documents,  downloads or other files on this HDD, which is the way I like it). I  can't find where this blob of data is located beyond /dev/sda1. 
You can't save directly on swap. (It's like the pagefile on windows and is used only the OS to cache something when your free RAM is low). 
And 2.9GB is already good.

---

### Post by p.callan on 2015-05-25
```
lsblkuser@X125:/$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0 295.4G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   2.8G  0 part [SWAP]
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/M
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part /media/INFOBANK003
sdd      8:48   1  58.6G  0 disk 
&#9492;&#9472;sdd1   8:49   1  58.6G  0 part /media/STG
user@X125:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       291G  [COLOR=#ff0000]**227G**[/COLOR]   50G  82% /
udev            1.4G  4.0K  1.4G   1% /dev
tmpfs           278M  888K  277M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G   23M  1.4G   2% /run/shm
/dev/sdb1       932G  253G  680G  28% /media/M
/dev/sdd1        59G   35G   25G  60% /media/STG
/dev/sdc1       932G  865G   68G  93% /media/INFOBANK003



```


I mean the data from the ext hdd lands on the computer's hdd before it is sent off to dropbox, right? 
The ONLY thing I have installed on the computer's hdd right now is the OS itself and it's certainly not 227GB :)
Sorry, I don't know why those nice columns aren't kept...

---

### Post by ajgreeny on 2015-05-25
You need to use code tags to keep the formatting (see my signature below form a how-to
Here's what it should look like, though I'm afraid I can't help with the real problem.
```
lsblkuser@X125:/$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0 295.4G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   2.8G  0 part [SWAP]
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/M
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part /media/INFOBANK003
sdd      8:48   1  58.6G  0 disk 
&#9492;&#9472;sdd1   8:49   1  58.6G  0 part /media/STG
user@X125:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       291G  [COLOR=#ff0000]**227G**[/COLOR]   50G  82% /
udev            1.4G  4.0K  1.4G   1% /dev
tmpfs           278M  888K  277M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G   23M  1.4G   2% /run/shm
/dev/sdb1       932G  253G  680G  28% /media/M
/dev/sdd1        59G   35G   25G  60% /media/STG
/dev/sdc1       932G  865G   68G  93% /media/INFOBANK003
```

---

### Post by p.callan on 2015-05-25
I didn't know my dropbox folder is a **local copy**. That's why the hdd is full.
Trying now to not mirror the distant dropbox folder as per [this page]("https://www.dropbox.com/en/help/4456") - "Selective sync". However, there is no dropbox icon to get to the preferences via. When I right-click Dropbox in the file explorer I get: Open, open in a new tab, open in new window, remove, rename. Nothing else. Clicking dropbox from applications menu does nothing. There is no White arrow for other apps in the menu bar. Moving on to do it via terminal:


> Linux Select which folders to sync on Linux

Click on the Dropbox icon from the menu bar. If you don't see the Dropbox icon, press the white up arrow to see all system tray icons.
Select Preferences.
Click the Account tab.
Click the Selective Sync button.
A window will appear with a list of all the top level folders in your Dropbox folder. The folders with a check next to them will be synced to your computer. Uncheck any folders that you don't need to sync to your computer's hard drive. When you're done, select OK. Any folders you deselected will be removed from your hard drive, but will still be available through the website and on any computers linked to your Dropbox account.

Use the Advanced View button to drill down into the folders in your Dropbox. Click on the arrow next to the folders in your Dropbox to drill down and check or uncheck folders deep within your Dropbox hierarchy.

From the command line

If you have the Dropbox command line instructions script, then all you need to do to add a folder to the Selective Sync "do not sync" list is enter the following command in your Terminal.

/path/to/dropbox.py exclude add ~/Dropbox/path/to/folder/
Simply substitute the /path/to/ to the actual paths to the CLI script and the folder or file, respectively.


> user@X125:/$ /Downloads/dropbox.py exclude add ~/Dropbox/
bash: /Downloads/dropbox.py: No such file or directory
user@X125:/$ /Downloads/dropbox.py exclude add ~/Dropbox/
bash: /Downloads/dropbox.py: No such file or directory
user@X125:/$ /Home/Downloads/dropbox.py exclude add ~/Dropbox/
bash: /Home/Downloads/dropbox.py: No such file or directory
user@X125:/$ /Home/Downloads/dropbox.py exclude add ~/Home//Dropbox/
bash: /Home/Downloads/dropbox.py: No such file or directory
Even though I am looking at it. *sigh*

> user@X125:/$ #!/bin/shuser@X125:/$ sleep 10 && dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start
Dropbox isn't responding!
Dropbox isn't responding!
Dropbox is already running!

](*,)](*,)](*,)

---

### Post by p.callan on 2015-05-25
Tried this:

> [FONT=Helvetica Neue]A quick fix I go into detail on [/FONT][my blog here]("http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/")[FONT=Helvetica Neue], but simply here:[/FONT]
[LIST=1]
[*]Kill dropbox, and restart it so it shows
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start

[*]Go to the settings in dropbox after it starts up and select to not start at startup.

[*]Go to system settings -> Applications, from the tab up top select "Startup" and add a command from the + button at the bottom left and there will be an input where you can enter in a command below and press enter to save:
env XDG_CURRENT_DESKTOP=Unity dropbox start ls
[/LIST]
[FONT=Helvetica Neue]Restart and you should be good to go.[/FONT]
And it freaking worked. Hail Mary.

---

### Post by howefield on 2015-06-22
Thread moved.

---


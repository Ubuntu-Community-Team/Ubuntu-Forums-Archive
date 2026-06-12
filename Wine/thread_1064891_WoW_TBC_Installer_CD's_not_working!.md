---
title: "WoW TBC Installer CD's not working!"
date: 2009-02-09
forum: Wine
---

### Post by draconastar on 2009-02-09
Alright.  So I'm trying to install WoW on Ubuntu 8.10, and it's not working out for me.  This is sad, because being able to play my Windows based games is about the last thing I'll need to switch over completely.  Allow me to explain.

After installing Wine (1.0.1, apparently), I started the process.  The first order of business was to edit my /etc/fstab to see hidden .exe files, which worked out fine.  I popped in the original WoW installer (which was the DVD, important) and the first part of the game installed.  Excellent.

When I popped in my BC Disk 1 and tried to run the installer, I got:
"No installer data could be found.  If this problem persists, please contact Blizzard Technical Support."

Now, I can see the installer.exe file on this disk.  I can *also* see the InstallerTome.mpq, but there's an interesting problem: the size of all the files put together on the CD is **1.2 MB**.  That doesn't sound right.  Sure enough, the installer tome's size is 50.3 KB, which is not nearly where it should be.  So I figured that maybe the CD is scratched or something like that, so I popped in CD 2 just to make sure.  And that's what kills me.  Install Tome 2 is *also* 50.3 KB, as well as the installer tome on every other install CD for BC.  The chances of having a scratch in the exact same spot on that number of CD's is unbelievably small, so that means I'm missing something.

I've looked around over several forums and have found no one with a similar problem.  Everyone's problem originally seems to be on finding the installer.exe in the first place, and then configuration issues afterwards.  Every guide always just says "pop the CD's in and install, it's that easy!".  I wish it was that easy for me.  :(

So I'm stuck.  Can anyone help?  Will I have to find a copy of the TBC DVD for some reason?  If advice given here is successful, will I encounter similar problems when trying to install WotLK?  Thanks!

****EDIT****

Almost forgot, when I try to run it in terminal, here's what it spits at me:
```
daren@daren-desktop:~$ wine /media/cdrom0/installer.exe
fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14a32a8
fixme:ole:OleCreateStaticFromData (not shown), stub!
```

---

### Post by Bios Element on 2009-02-09
Go to the Blizzard site and download the downloader and just use it. It'll make things much easier for you.

---

### Post by draconastar on 2009-02-09
Yes, I've considered that too.  But my connection has a download limit per 24 hour period, so that's out of the question.

However, I have managed to get it working so far, and I'll document what I've done so that it might help others with similar problems.

**First hurdle: _Original WoW Install_**

     This will give you problems because the installer.exe on the disc is a hidden file.  But the reason it's a problem is that it's a *Windows* hidden file, not a *Linux* hidden file.  Most people will tell you to simply mount the CD or DVD using the "unhide" option, but there's a more permanent and simpler way to accomplish this: editing your fstab file so that it automatically uses the unhide option.  After you unmount the CD or DVD (if you popped it in before doing this), open up a terminal window and use a text editor to open fstab:

```
sudo gedit /etc/fstab
```

Once the text editor opens, add the following line to the very bottom:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,unhide,noauto,exec 0 0
```

This makes it so all Windows hidden files mounted from that mount point will be shown, making your installer.exe accessible.  If you are mounting the CD from a different mount point, then change it accordingly.  

**Second Hurdle: _The Burning Crusade_**

     For an explanation why this is a hurdle, see the original post of this thread.  I don't know the reason for the problem and have still yet to figure it out, but after searching around a bit I came across an easy workaround for people who have a separate Windows partition or networked Windows machine.

     Once in Windows (somewhere), create a folder in which you will store the contents of your install CD.  Then, insert the CD or DVD.  If you have the 4 separate CD's, copy the entire contents of the first CD into the folder **then only the Installer Tomes from each following CD.**  If you have the DVD, then copy the entire contents into the folder.  

     If you are on a Windows partition and the destination install point is a Linux partition on the same drive, then hop back over to Linux and skip the following paragraph.

     If you are using a networked Windows machine, be careful.  If you have a strong, uninterrupted network connection, then you can simply point Wine to the remote installer.exe and install from there.  However, if your connection to the network hiccups at all during the install, you'll have to uninstall and start over, so I'd recommend copying the contents of the folder onto your Linux machine.  In Ubuntu, opening up a Nautilus window and typing "smb://<Name of your Windows Machine here>/" in the location box will show you all of the Windows shares on the specified Windows machine.

    From here, you should be able to navigate to the folder and use Wine to run the installer.exe.

    For those of you who don't have separate Windows machines / partitions, some people have said that just copying the contents of the CD onto their hard drives and trying it from there worked out, so this might be an option.

**Third Hurdle: _Wrath of the Lich King_**

    This comes with a few problems.  First and foremost, not being able to do anything.  You pop in the CD or DVD, open it up and attempt to run the installer.exe using Wine, but nothing happens.  No matter what you do, nothing happens.  **This is because you don't have permission to use the files on the CD/DVD.**  This, however, is an easily solvable problem.

     First you are going to have to copy the files from the CD's or DVD onto your hard drive as root.  **Note: if you are using multiple CD's, make sure you copy the entire contents of the first CD into whichever directory you have created *and only the installer tomes from each CD after***.  I'll help you through this one, as it's going to be pretty rough.  

     Create a folder on your Desktop called Wrath (for simplicity).  Insert the CD and open a terminal window, entering the following command:

```
sudo cp -r /media/cdrom0 /home/<user>/Desktop/Wrath
```

Obviously, make sure to insert your user name in place of <user>.

     This will copy the entire contents of the CD into the Wrath folder ***as root***, which is important.  If what you copied was the DVD, then it will take awhile (with no progress bar, so be patient), and you'll be done copying.  However, if that was only the first CD, then insert the next and copy the next Installer Tome in Wrath as root:

```
sudo cp /media/cdrom0/Installer\ Tome\ 2.mpq /home/<user>/Desktop/Wrath
```

     Do that for each CD, obviously putting in the correct Installer Tome number as you go along. 

     After you're done copying and have all of your installer tomes and your installer.exe, it's time to change ownership of the files to you, the user.  Go into Terminal and type:

```
sudo chown -R <user> /home/<user>/Desktop/Wrath
```

Again, making sure you insert your user name for each instance of <user>.

     After you're done claiming ownership over the files, you can navigate to the installer.exe and run it using Wine.

  
     The second problem some of you may encounter, depending on your Wine version, is the actual installer screen.  The user agreement screen won't allow you to hit "Agree" until it senses that you're at the bottom of the text.  However, this feature does not work correctly in Wine 1.0.1.  There are other very complicated ways to work around this, but the easiest way is to install the most recent version of Wine (1.1.14 for me).  Visit [www.winehq.com](www.winehq.com) to grab and install it.  Wine will ask you to download Gecko in order to display the HTML correctly, so just let it do it's thing and you should be golden.


     As a side note for those of you who have subsequent problems downloading patches using the Blizzard Downloader: the easiest way to solve this problem is to download the patch elsewhere and run it using Wine.  The best way I've found is to grab the appropriate "mega patch" from FilePlanet.  This updates you from wherever you are to whatever the most recent is.

Hope this helps some people!  I don't know how to rename this post or to put this particular post at the top of the thread, but I hope that people who need this can find it.  :D

---

### Post by roh8880 on 2009-05-14
Okay, I followed your tutorial to the letter and I still get

```
ghost@ghost:~/Desktop/wowfiles/lichwow_install$ wine Installer.exe
fixme:ole:OleCreateStaticFromData (not shown), stub!
```

and when I try to open it using wine I get the

> "No installer data could be found. If this problem persists, please contact Blizzard Technical Support."

What's next?

---

### Post by hikaricore on 2009-05-14
You obviously didn't follow the instructions when mounting the dvd.
Reread the guide and follow all the steps, not just the ones you want to.

---

### Post by roh8880 on 2009-05-14
OH YOUR GOD!!!!!

> **OrbJinzo said:**
> sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/ 

Make sure you have unmounted the drive first with umount. then run this it should get ya going.


I feel like a dumb bass now! I didn't unmount the dvd first!! 

This code works just fine!

---


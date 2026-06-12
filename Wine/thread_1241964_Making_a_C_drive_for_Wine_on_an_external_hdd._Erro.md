---
title: "Making a C:\ drive for Wine on an external hdd. Error message 'unable to accept...'"
date: 2009-08-16
forum: Wine
---

### Post by phantomjoker on 2009-08-16
I try and be as descriptive as i can with my titles so basically as written above i am trying to create a bigger drive to install programs to via Wine, due to the current C drive running out of room. I went into the settings and into the 'drivers' tab and created a new drive in my external hdd called E:\ ....

So i went to install the program and i browsed to the folder and it automatically brought up the drive E:\ rather than the folder name+destination. But when i clicked install i got an error saying 'Wine cannot accept this destination, please choose another drive.'

---

### Post by ajgreeny on 2009-08-16
I think the problem is that wine can only install programs into the hidden .wine folder in your /home folder.  If this new "drive" you made is not part of your /home, I don't think what you want is possible.

---

### Post by Paddy Landau on 2009-08-16
Have you considered moving some of your data to the external drive, so that Wine has more space?

Also, I would recommend [PlayOnLinux]("http://www.playonlinux.com/"), which is a sort of manager for Wine, making it very easy to install, run and uninstall Windows programs on Wine.

---

### Post by phantomjoker on 2009-08-17
thanks for the help. I didnt know files had to be in a perticualar folder, so that is probably the problem. 

I cant move any data, its bare bones as it is, so i really need a way to create another wine folder/drive

---

### Post by matthewbpt on 2009-08-17
What I did was create a symlink in the .wine folder in your home directory and pointed the symlink to the external source, that way wine thinks its storing the files in the home directory when they are actually on the external drive. First thing, move everything in /home/"your_user_name"/.wine/drive_c/ to the new folder you want this stuff to be in, lets say this is /media/external_drive/wine_drive_c/ , and delete /home/"your_user_name"/.wine/drive_c/ folder. Now the clever bit, make the link:

```
ln -s /your/new/drive_c/location/ /home/"your_user_name"/.wine/drive_c
```

In the case of my example I'd do

```
ln -s /media/external_drive/wine_drive_c/ /home/"your_user_name"/.wine/drive_c
```

Now wine will be using the folder in your home directory, but in raelity it will be storing everything in the external drive, clever! =D

Don't forget to change "your_user_name" for your actual username!

---

### Post by Paddy Landau on 2009-08-17
> **phantomjoker said:**
> I cant move any data, its bare bones as it is, so i really need a way to create another wine folder/drive
I've just been having a look at the Wine instructions ("man wine").

There is an environment variable, WINEPREFIX, that tells Wine where to look for the files.

So, experiment with this. (I've never done it, so I can't tell you whether it will work.)

[LIST=1]
[*]Close all Wine (Windows) programs, including [PlayOnLinux]("http://www.playonlinux.com/") if you have it.
[*]Move your [COLOR=Navy]~/.wine[/COLOR] folder to your external drive. For the sake of clarity, let's suppose your hard drive is mounted on [COLOR=Navy]/media/hd[/COLOR] and you call the new directory [COLOR=Navy]/wine[/COLOR]. The command would be as follows (obviously, change [COLOR=Navy]/media/hd[/COLOR] to whatever path your drive is mounted as): ```
mv ~/.wine /media/hd/wine
```
[*]Edit your [COLOR=Navy]~/.bashrc[/COLOR] file and add the following command at the bottom (again, change [COLOR=Navy]/media/hd[/COLOR] to the correct path): ```
export WINEPREFIX=/media/hd/wine
```
[*]Now run Wine. Does it work?
[/LIST]
Let us know.

[LIST]
[*]If it does work, great!
[*]If it doesn't work, don't despair, there's something else we can still try.
[/LIST]
And if you want to use PlayOnLinx (which I strongly recommend), then there's something we can try to move its directory, too.

---

### Post by Paddy Landau on 2009-08-17
> **matthewbpt said:**
> What I did was create a symlink in the .wine folder...
Ah, yes, Matthew's idea is probably far simpler than mine!

---

### Post by Moyamo on 2010-06-26
I have PlayOnLinux and Wine and both have separate c: drives how do i link the 2.

---

### Post by Paddy Landau on 2010-06-26
> **Moyamo said:**
> I have PlayOnLinux and Wine and both have separate c: drives how do i link the 2.
PlayOnLinux creates a separate C: drive for *every* separate prefix that it makes. For example, if you install three Windows programs in three different prefixes, each one will have its own C: drive and its own registry.

Thus, when they run, they are completely independent of each other.

That prevents the programs from interfering with each other or crashing each other.

It doesn't make sense to "link the two".

If you want two programs to share the same C: drive and registry in PlayOnLinux, then you want to install both of them in the *same* prefix.

So, don't install anything though Wine. Install always through PlayOnLinux.

---

### Post by Moyamo on 2010-06-26
What is a prefix ?

---

### Post by philinux on 2010-06-26
Moved to Wine forum.

---

### Post by Moyamo on 2010-06-26
What's a prefix?:confused:

---

### Post by Paddy Landau on 2010-06-26
> **Moyamo said:**
> What's a prefix?
When you install a Windows program with [PlayOnLinux]("http://www.playonlinux.com/"), it creates a "prefix" for it. A prefix is a place to install the Windows program, together with the C: drive and the registry.

For example, you may want to install Word, Excel and Quicken. You want Word and Excel to share the same location, but Quicken to go somewhere else.

You install Quicken in a prefix called (say) "Quicken", and Word and Excel in a prefix called (say) "Office".

The two prefixes, Quicken and Office, will be completely independent of each other, as though they were on different machines.

To uninstall Quicken, you simply instruct PlayOnLinux to delete the Quicken prefix. To uninstall both Word and Excel, you instruct PlayOnLinux to delete the Office prefix.

PlayOnLinux hides some of the complexity of Wine, making it easy to install and uninstall Windows programs.

---

### Post by Moyamo on 2010-06-26
Sorry for asking so many questions but now that i have PlayOnLinux can i remove wine.  It is taking up a few gigabytes on my hard drive

---

### Post by Paddy Landau on 2010-06-26
> **Moyamo said:**
> ... now that i have PlayOnLinux can i remove wine.
No, no, no.

PlayOnLinux isn't a replacement for Wine. It's a front-end to make using Wine simpler.

Wine will take up a lot of space. After all, it has to get Windows programs to run!

If you want to start Wine afresh, do the following -- but, warning, you will lose all the programs that you've already installed in Wine (you'll have to install them again):

[LIST]
[*]Delete the directory [FONT=Courier New].wine[/FONT] in your home directory.
[*]Delete the directory [FONT=Courier New].PlayOnLinux[/FONT] in your home directory.
[/LIST]
Do that, and Wine and PlayOnLinux will be reset to a fresh installation. You can then install through PlayOnLinux. I repeat, this will delete all your installed Windows programs (on Ubuntu, that is; it won't affect your Windows installation if you have a dual boot).

---

### Post by Paddy Landau on 2010-06-26
> **Moyamo said:**
> ... wine.  It is taking up a few gigabytes on my hard drive
Uh, double-take here. A few *Gigabytes*? :o

My *entire* Ubuntu installation, including all my extra installed programs, Wine and my Windows programs (but excluding data), takes a mere 5.3Gb. Are you sure that Wine is taking a few Gigabytes?

---

### Post by Moyamo on 2010-06-28
I thought it was but it was actually my Age Of Empires 3 installation

---


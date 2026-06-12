---
title: "need help with few things"
date: 2010-12-23
forum: Wine
---

### Post by ags84 on 2010-12-23
hey guys,

as i have mentioned in ur previous request, i am a  newbie to linux and have currently installed linux Mint 10 on my laptop. Dual boot with Windows 7 and Mint ( i have 1GB Nvidia Graphic  card installed)

i need help to configure a few things. they r as follows

1.   I also Windows 7 . it had a amazimg feature ie u can select a few  pictures and add them as wal paper for desktop back ground. it gets  changed at pre-set time. ubuntu had that feature as well.. but in mint, i  am not able to find it... pls help me find out where exactly i can set  it?

2. i have a Nokia Phone which used to help me to take backup  of my phone when i required. now, in Nokia's website, they havent  released their PC suite for linux. so is there a supplement for Nokia PC  suite or Nokia OVi suite?

3. I am a also a game freak... can certian games (windows based games) like GTA, NFS be installed here?

4. How to install new themes which can be downloaded from net? i mean, files in .7z format.

5. Can GHOST backup be done on linux mint?

thanks  guys, i hope u guys can help me out here. if these things can be done, i  need not reboot it into win7 when i need to use above mentioned  features.

kindly provide me steps to do so as i am very very new to linux. installed it this week( 3 days ago)

thanks once again.

---

### Post by inkrypted on 2010-12-23
Well I do know of a program called Wallpapoz to change your wallpaper like that for the gnome desktop.
[http://wallpapoz.akbarhome.com](http://wallpapoz.akbarhome.com)

I found this software for a friend of mine once with a Nokia phone and he said it really worked well called gnokii. I cannot vouch for this myself but you might check it out.
[http://www.gnokii.org](http://www.gnokii.org)

As for playing windows games on Linux Wine is all I can think of.
[http://www.winehq.org](http://www.winehq.org)

This post may help you alot with the themes.
[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

Remember you can search the forums and Google is your friend too.

Hope this helps.;)

---

### Post by SbKhaan1 on 2010-12-23
1. You mean a slideshow? I'm not very familiar with Mint, I wouldn't be able to tell you.

2. You could try running the program with WINE - [http://www.winehq.org/](http://www.winehq.org/)
    or .. ```
sudo apt-get install wine
```

3. Again, WINE can run most Windows apps/games.

4. You should be able to extract that onto your desktop, go into themes, click "Install" and then choose the theme pack.

---

### Post by inkrypted on 2010-12-23
Linux Mint is based on Debian and Ubuntu. 
[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

---

### Post by inkrypted on 2010-12-23
Yes with Clonezilla.
[http://clonezilla.org](http://clonezilla.org)

---

### Post by ags84 on 2010-12-23
> **inkrypted said:**
> Yes with Clonezilla.
[http://clonezilla.org](http://clonezilla.org)

can u pls tell me to which question is this applicable???

---

### Post by ags84 on 2010-12-23
> **SbKhaan1 said:**
> 1. You mean a slideshow? I'm not very familiar with Mint, I wouldn't be able to tell you.

2. You could try running the program with WINE - [http://www.winehq.org/](http://www.winehq.org/)
    or .. ```
sudo apt-get install wine
```3. Again, WINE can run most Windows apps/games.

4. You should be able to extract that onto your desktop, go into themes, click "Install" and then choose the theme pack.


wine is preinstalled in mint. but i am not able to run any exe file ( by double clicking as we normally do it windows) so i am not sure how to install exe files in linux

can u pls guide me?

wrt to themes, i tried as u said. but when i click on install linux is not recognising any files (in that extract) as themes file. hence i am not able to install it.

---

### Post by Elfy on 2010-12-23
First wine is not a panacea - it will not run most windows apps/games - or at least not well. Check the wine app database for info on specifics. [http://appdb.winehq.org/](http://appdb.winehq.org/)
> 
but i am not able to run any exe fileRight click the exe and make sure that it's allowed to execute on the permissions tab.

Linux is not to be thought of as a free way to run windows apps - that way lies disappointment.

---

### Post by inkrypted on 2010-12-23
Clonezilla is for question 5.

---

### Post by ags84 on 2010-12-29
> **inkrypted said:**
> Clonezilla is for question 5.


sorry for the late reply... i had some problems with net last few days...

clonezilla is not available in software package manager.... should i have to download it from elsewhere????

thanks

---

### Post by ags84 on 2010-12-29
> **forestpiskie said:**
> First wine is not a panacea - it will not run most windows apps/games - or at least not well. Check the wine app database for info on specifics. [http://appdb.winehq.org/](http://appdb.winehq.org/)
Right click the exe and make sure that it's allowed to execute on the permissions tab.

Linux is not to be thought of as a free way to run windows apps - that way lies disappointment.


this is error i get when i did as u mentioned
```

The file '/media/Windows Black XP/Documents and Settings/Admin/Desktop/Made Man.lnk' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

pls let me know how to solve this...

---

### Post by ags84 on 2011-01-02
guys....

i am still waitiing... pls help me

---

### Post by Elfy on 2011-01-02
> **ags84 said:**
> this is error i get when i did as u mentioned
```

The file '/media/Windows Black XP/Documents and Settings/Admin/Desktop/Made Man.lnk' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

pls let me know how to solve this...

> **ags84 said:**
> guys....

i am still waitiing... pls help me

That's a link on a windows desktop - you need the actual exe in linux to get it to run with wine.

---

### Post by ags84 on 2011-01-02
i have exe file... i get same error when i click in it..

it just says, it cannot be executed/

---

### Post by Elfy on 2011-01-02
I've already told you how to in one of the other posts, please read what people post.

At some point you are going to need to help yourself.

---

### Post by ags84 on 2011-01-02
> **forestpiskie said:**
> I've already told you how to in one of the other posts, please read what people post.

At some point you are going to need to help yourself.

i am extremely sorry.....

i forgot this
```

Right click the exe and make sure that it's allowed to execute on the permissions tab.
```

now i am able to install...

thanks for the information and i am ver sorry for the mistake i comitted. i hope u will forgive me for it.

i had asked for a application similar to nokia PC suite. i was suggested to use gnokii... but it ddint work...

can u pls suggest me a alternative?

---

### Post by Elfy on 2011-01-03
> **ags84 said:**
> can u pls suggest me a alternative?

Sorry I can't.

---


---
title: "How do I install extra truetype fonts"
date: 2016-05-06
forum: Ubuntu Studio
---

### Post by Alfred_Douglas on 2016-05-06
I've just moved from Windows to Ubuntu Studio 16.04. How do I install more truetype fonts? I have downloaded about 20 fonts and placed them in my Home folder, in a new subfolder that I've created, called MyFonts. How should I proceed from here.
Many thanks.
:confused:

---

### Post by Bashing-om on 2016-05-06
Alfred_Douglas; Hello.

We have a utility for that !
```

sudo apt update
sudo apt upgrade
sudo apt install ttf-mscorefonts-installer

```
When the EULA pops up use the space bar to page down, Tab to highlight "Ok", then Enter.

[INDENT]'buntu
[INDENT][INDENT]when it is hard, you are doing it wrong
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-05-06
And if you have other fonts not available in the mscorefonts package you can install them by doing the following:-

First make a system folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```
I am using myfonts as an example.
Next open a terminal in the folder where you have a bunch of custom fonts and run command
```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```
This will copy the truetype fonts to that folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.
Now that we have the fonts in the proper folder we need to install them in Ubuntu. Run command
```
sudo fc-cache -f -v
```
This will install the fonts so that both your applications like LibreOffice, and any other users including the system utilities can use them.

---

### Post by Alfred_Douglas on 2016-05-06
Many thanks for your swift responses!  I am writing about the history of alchemy and how it evolved into the science of chemistry, so I'm using a variety of strange ttf fonts - alchemical symbols, astrology glyphs, etc.  I now have them installed.

The MS core fonts would be useful too, but when I entered: 
apt install ttf-mscorefonts-installer

I got this response:
E: could not open lock file /var/lib/dpkg/lock - open (13:Permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/)  Are you root?

I have no idea what any of this means. As I entered my administrator password I assume that made me root.

---

### Post by Bashing-om on 2016-05-06
Alfred_Douglas; Hey ...

My bad .. to make a system change requites admin access . That access is 'sudo' .
the command " apt install ttf-mscorefonts-installer" is amended to be :
```

sudo apt install ttf-mscorefonts-installer

```

My apologies for my lapse of error checking.

[INDENT][INDENT]security, what makes 'buntu 'buntu
[/INDENT][/INDENT]

---

### Post by serfcx on 2016-05-07
It used to be the case that you could put any fonts you wanted in the .fonts folder in your home directory (Notice the .dot)
This is a hidden folder so when in your home folder "ctrl+h" will show hidden folders. If you dont have one create the folder and then download the font you want and place them in this folder.

---

### Post by Alfred_Douglas on 2016-05-07
Hi Bashing-om,

I've got the msttcorefonts installed by running the reinstallation:

sudo apt-get --reinstall install msttcorefonts

followed by:

sudo apt-get --reinstall install ttf-mscorefonts-installer

Many thanks,

Alfred

---

### Post by Alfred_Douglas on 2016-05-07
Hi serfcx,

This looks very handy. I've located the hidden .fonts folder in the home directory and I'll use your suggestion next time I download extra ttf fonts.

All the best,
Alfred

---

### Post by ajgreeny on 2016-05-07
> **serfcx said:**
> It used to be the case that you could put any fonts you wanted in the .fonts folder in your home directory (Notice the .dot)
This is a hidden folder so when in your home folder "ctrl+h" will show hidden folders. If you dont have one create the folder and then download the font you want and place them in this folder.
The possible disadvantage of adding fonts this way is that they will be visible and usable by that one user only, which could be a problem on a multi-user machine.  Installing in the manner I showed means all users can use all the fonts.

If you have only one user, then putting them in the ~/.fonts folder is absolutely fine.

---

### Post by marseille2 on 2016-06-04
Sort of on-topic, but more of an alternative if you like web design ... 

IMO ... one of the best FONT programs that ever happened to Ubuntu is [TypeCatcher]("http://www.omgubuntu.co.uk/2013/08/typecatcher-google-fonts-download-for-ubuntu")! It allows us to choose Google Fonts and install them without any hassle. It's sort of like [SkyFonts]("https://skyfonts.com/").

---


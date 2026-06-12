---
title: "Korean input with Nabi ****"
date: 2006-06-27
forum: Tutorials
---

### Post by mikwig on 2006-06-27
This is how to get Korean input working within Dapper - Gnome,
using nabi as the input method.

**Step 1**

you need to install the packages *nabi* and *im-switch*.
```
sudo apt-get install nabi im-switch
```

**Step 2**

You will need to setup the environment for gnome to use nabi.
Start by creating a file in your home directory named .gnomerc
```
gedit ~/.gnomerc
```

Copy and paste the following into the file.
```
export XMODIFIERS="@im=nabi"
export XIM_PROGRAM=/usr/bin/nabi
export GTK_IM_MODULE=xim
export QT_IM_MODULE=xim
nabi &
```

Save the file

**Step 3**

Tell im-switch to use nabi
```
im-switch -s nabi
```

Now restart the x-server by pressing {Ctrl}-{Alt}-{Backspace}

If you recieve and error (in Korean) or your nabi box is blank all of
the time then your locale setting needs to be changed to a korean 
locale or a utf-8 compatible one
eg. *en_AU.UTF-8*

The button to switch between English/Korean is {shift}-{Space}
You can select other buttons by right clicking the Nabi tray Icon 
selecting preferences and then the hangul tab followed by {+add}
I chose the evil windows button as my input switcher (take that ms)

---

### Post by parksobong on 2006-08-28
I followed your method and installed Nabi.

The Nabi icon shows up on the panel, and when I press shift + space the icon switches between Korean and English.

However, when I type, it still types in English.

What might be the problem?

Thanks in advance.

---

### Post by parksobong on 2006-08-29
The issue was solved when I uninstalled the Nabi package downloaded from the Ubuntu repository, and I installed the source tar.gz from nabi.kldp.org.

---

### Post by paker on 2007-01-09
Here is my experience.
I followed the first poster's instructions. All went well. I didn't need to download and extract the tar file like the previous poster.

My setup: ubuntu 6.10 amd64, Jan 9, 2007

EDIT: 10.04 is packaged with nabi 0.99.06. Korean fonts may break. Install 0.99.07 from [http://packages.debian.org/unstable/x11/nabi](http://packages.debian.org/unstable/x11/nabi). The debian package installs easily. Supports both Korean and Hanja.

---

### Post by GordSellar on 2007-02-17
The instructions worked perfectly well for me also. No idea what might be causing an error, but I'd reinstall everything and see. Also, if you're trying to type in a word processor and text isn't appearing, you might check that Korean fonts are installed/selected.

 &#54616;&#51648;&#47560;&#12596; &#50780;&#44536;&#47000; &#51060;&#49324;&#12615; &#54616;&#12596;  ugh... why isn't it handling 3-letter consonants? I'm annoyed now.

---

### Post by mikwig on 2008-02-03
> **GordSellar said:**
> 

 &#54616;&#51648;&#47560;&#12596; &#50780;&#44536;&#47000; &#51060;&#49324;&#12615; &#54616;&#12596;  ugh... why isn't it handling 3-letter consonants? I'm annoyed now.

You need to change between 2&#48520; and 3&#48520;.

I have switched back to scim again - in that it is stable again, and can also do Japanese.

---

### Post by Sef on 2008-08-13
This tutorial works for Hardy Heron as is.

---

### Post by paker on 2010-01-28
I have been using this method for years. Stills works with 9.10 32 bit.

---

### Post by geekboysf on 2010-02-11
It works,  but I would like to change the keys that switch languages.  It is default on Shift-Space which is tricky for my sloppy typing.  I don't get a tray icon for nabi and cannot figure out how to change the configuration.

---

### Post by paker on 2010-05-01
Now I have a problem. I switched to 10.4 on 2 machines. nabi works on one and doesn't on the other. I have yet to figure out why so.

---

### Post by mklinux on 2010-05-05
I am having the same problem. I updated both of my computers to 10.04 and on one of them (the hp laptop)nabi is still working, but on the other (LGx130 netbook w/10.04 UNR) it's not working. I tried reinstalling the files for nabi and uninstalling and reinstalling the language support as well. I don't like SCIM that much and I've had problems with it not recognizing 3 character syllabic blocks, but I'm willing to deal now...

Though I'd still like to keep nabi, cleaner and more efficient. Though as of now it doesn't work.

Any help at all would be much appreciated.

---

### Post by paker on 2010-05-06
Previously I reported nabi worked on one machine but didn't on the other. I was mistaken. Nabi doesn't work on neither of 10.4 machines. I am going back to 9.10. If anyone found solution, please share. Thanks.

PROBLEM SOLVED: Install new version of nabi outside Synaptic Package Manager. [http://packages.debian.org/unstable/x11/nabi](http://packages.debian.org/unstable/x11/nabi)

EDIT: The link now defaults to 0.99.9. It is not stable. Search for nabi, and you will get links to different versions. Select 0.99.7. June 8, 2011  10.04LTS

EDIT: Install nabi that comes with 10.04 first. This will put the language box in the upper task bar. If you install 0.99.7 directly, the language box will be outside the top task bar, very annoying.

---

### Post by dapfy on 2010-05-11
I have done a fresh german language Ubuntu 10.4 install on a Korean keyboard laptop.

I have tried all kinds of Korean input methods with uim, scim, nabi (with the .gnomerc proposed here previously) and ibus and I have never managed to enter a single Hangeul :(  All but scim gave me a gnome taskbarlet which was never any use.  When configuring the switch key they all recognized the hangul and hangul-hanja keys, but then the keys do nothing.  Same goes for other keys like shift-space or control-space.

Doesn't anybody have a clue?

On a not quite related topic I have put the Zeichenpalette (character chooser) into the top menu bar.  When hovering it gives me a (gibberish to laymen!) unicode char name and says it would insert that char.  But when I click it, it only copies it, so I can then insert it with middle-mouse or ctrl-v.  That's so cumbersome it's almost unusable!  There doesn't seem to be an option for direct insertion.

---

### Post by ryecomp on 2010-05-25
1. sudo apt-get install scim-hangul
2. system > administration > language > keyboard input method system to scim-bridge
3. sudo /etc/init.d/gdm restart 

solves similar problem.

---

### Post by paker on 2010-06-26
SOLUTION

Download nabi 0.99.7 deb package.
[http://packages.debian.org/unstable/x11/nabi](http://packages.debian.org/unstable/x11/nabi)

10.04 comes with nabi 0.99.6.

---

### Post by jdalt on 2010-12-13
For the Kubuntu people wondering if they can replace .gnomerc with .kderc -- in my experience that doesn't work. 

For Kubuntu I do the following (circa 10.10 Maverick):

1. Copy Batang, Dotum, and Gulim fonts from Korean windows install to /usr/share/fonts/windows-fonts (create the windows-fonts directory). Run fc-cache to refresh the font cache. You could probably also download these fonts from the interwebs.

2. Install the nabi package via your favored method. I prefer the trusty: sudo apt-get install nabi

3. Now instead of modifying/creating .kderc you should create a script in ~/.kde/env called something like nabi.sh with the following:

```
export LC_TYPE=en_US.UTF-8
export XMODIFIERS="@im=nabi"
export XIM_PROGRAM=/usr/bin/nabi
export GTK_IM_MODULE=xim
export QT_IM_MODULE=xim
nabi &
```

chmod +x nabi.sh and restart kdm and X. 

You might have to fool around with the dpkg-reconfigure locales, but I think simply specifying a UTF-8 based locale is good enough. Hope that clears up any confusion. If I put the contents of nabi.sh into .kderc then nabi would go to the system try but I would not be able change into hangul.

---

### Post by darkwolfalone on 2011-01-12
> **mikwig said:**
> You need to change between 2&#48520; and 3&#48520;.

I have switched back to scim again - in that it is stable again, and can also do Japanese.

I have the exact same problem. How do I switch from 2&#48520; to 3&#48520;?

---

### Post by paker on 2012-10-08
The OP instructions still work for 12.04 LTS.

---

### Post by paker on 2013-01-01
Same instructions work in 12.10.

---

### Post by paker on 2013-06-02
same procedure works for 13.04 64 bit

---

### Post by palmgrower on 2013-10-12
13.10

sudo apt-get install nabi
Lanugage Support > add Korean > change ibus to hangul (input method)
reboot

---


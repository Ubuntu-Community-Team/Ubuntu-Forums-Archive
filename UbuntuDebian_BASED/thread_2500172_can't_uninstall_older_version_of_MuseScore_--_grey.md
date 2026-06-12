---
title: "can't uninstall older version of MuseScore -- greyed out in &quot;Applications&quot; window"
date: 2024-08-24
forum: Ubuntu/Debian BASED
---

### Post by straitsfan on 2024-08-24
Hello.  It's been a while.  I'm using Elementary OS, and have different versions of MuseScore on it, including the most recent version, MuseScore Studio.  I want to uninstall the other 2 versions, MuseScore portable, and MuseScore 3.6.2, but when I click on "Applications" in the upper left of the screen the uninstall option is greyed out.  

Not sure how to uninstall them.  I think they may be causing problems with the latest version.  I went online to try to uninstall it from the command line but not sure what to do.   I used the sudo apt-get remove "Application name" but the command line said it couldn't find any app named MuseScore.

If it matters, I also noticed that these two versions do not appear in the list of installed apps in the App Center.  But I can open them and use them, which is strange.

Any help out there?

---

### Post by ajgreeny on 2024-08-25
How are those versions of musescore installed?
I use the downloaded appimage direct from the musescore website and have to create my own launcher for that as the system doesn't even know it's on the computer until I do so.
To uninstall an appimage you simply delete the downloaded appimage file.

Tell us in complete detail everything you can about how you installed musescore and we should be able to tell you how to uninstall it.

---

### Post by straitsfan on 2024-08-25
Honestly I don't know how they were installed -- it had been so long since I've used them.  They've got to be somewhere on my computer, but I wouldn't know where to look for them.  I can only guess and say that I installed them from the app center in elementary OS.  But I can't even be sure about that.

---

### Post by ajgreeny on 2024-08-25
We can get a few clues from the output of the following commands which you should run one by one and then copy back here the output using Code-tags please.
There is a How=to for Code-Tags below in my signature.
```
apt policy musescore
locate musescore
```

---

### Post by straitsfan on 2024-10-26
Sorry it's been a while.  Haven't been working on my machine in a bit.

For the apt policy command this is what I have:

```

apt policy musescore
musescore:
  Installed: (none)
  Candidate: (none)
  Version table:

```

The locate command put out A LOT.  You sure you want me to paste that here?

Now I can't uninstall my latest version of musescore, version 4.4.2  I have musescore 3.6.2 (from some time ago) and musescore portable as well, and those where the two that I want to uninstall.  But now, after working in the latest version, that uninstall option for 4.4.2 is also greyed out in the applications menu in Elementary OS.  

This is getting weird and frustrating

---

### Post by ajgreeny on 2024-10-27
OK. So you didn't install it using apt install or the apt policy command would have found it.

Let's see if you installed it in some way using command line by running command```
history | grep musescore
``` or if you got it as an appimage with ```
locate -i appimage
```and then another version of the previous locate command ```
locate musescore | grep $USER
```

---

### Post by straitsfan on 2024-10-27
okay -- here they are:

```

history | grep musescore
 1526  apt policy musescore
 1527  locate musescore
 1532  history | grep musescore

```

the locate -i musescore command is A LOT, unless I misunderstood the syntax.  am I supposed to say 'musescore' or should that be substituted with something else?

what is $USER in regards to the third command?  I assume it's me.  How do  find it?

---

### Post by ajgreeny on 2024-10-27
We're not getting very far so let's try once more with the output of command ```
locate -i appimage | grep -i musescore
``` which will tell us if you have the musescore appimage.

I have just realised that musescore is also available as a snap application (I do not use any snaps and keep my OS snap free!) so show us the output from command ```
snap list
```
If it is listed there you can use command ```
snap remove musescore
``` using the full name of the snap as listed in the previous output.

---

### Post by straitsfan on 2024-10-27
Thanks I'll try that.  I downloaded the appimage for the newest version and went online to learn how to make it executable, so that works now.  My apologies if I should have thought about that earlier.  I'll try your suggestions and get back to you.  Might be a bit, if that's okay.

---

### Post by straitsfan on 2024-11-04
Okay, here are the results:
locate -i appimage|grep musescore
/home/christopherlaurenzano/snap/musescore/228/.local/share/mime/application/vnd.appimage.xml
/home/christopherlaurenzano/snap/musescore/228/.local/share/mime/application/x-iso9660-appimage.xml

The appimage for the most current version, 4.4.3, is in my home folder as well, but it's not in the location above, so I'm guessing that at least one of the other versions are in the location stated above.

Here are the results of your other recommendation:

snap list
Name                Version             Rev    Tracking       Publisher   Notes
bare                1.0                 5      latest/stable  canonical&#10003;  base
core                16-2.61.4-20240607  17200  latest/stable  canonical&#10003;  core
core18              20240920            2846   latest/stable  canonical&#10003;  base
core20              20240911            2434   latest/stable  canonical&#10003;  base
gtk-common-themes   0.1-81-g442e511     1535   latest/stable  canonical&#10003;  -
gtk2-common-themes  0.1                 13     latest/stable  canonical&#10003;  -
[COLOR=#ff0000]musescore           3.6.2               228    latest/stable  musescore&#10003;  -[/COLOR]
snapd               2.63                21759  latest/stable  canonical&#10003;  snapd
vcard-studio        1.5.0               22     latest/stable  chronoscz   -

You can see here that version 3.6.2 is listed in this output.  I'm not sure if version 3.6.2 is what's in the location in my first output.  If it is, then there is also musescore portable 4.0 which is somewhere on my machine, and I'll need remove that as well.

So just to be sure I can just enter the snap remove muscore command to eliminate version 3.6.2, yes?

While I'm here, the current version that I'm using, 4.4.3, is in my home folder, but there's no icon/link that I can click on to open it, the kind that I could put in the dock.  I have to click on the appimage link in my home folder.  Is there any way that I can create an icon link that I could put in the dock?  If I click on the properties for this version, and choose which default program to open it with, (either musescore 3.6.2 or portable), it opens that version of musescore, and I can't use the score i've created with the newest version.

---

### Post by straitsfan on 2024-11-04
Okay -- got musescore 3.6.2 removed.  Thanks so much. 

Based on the locate command that you gave me I also tried this to find Musescore4 Portable and got this:

locate *portable
[COLOR=#0000ff]/home/christopherlaurenzano/.local/bin/mscore4portable
/home/christopherlaurenzano/.local/bin/musescore4portable[/COLOR]
/home/christopherlaurenzano/.local/share/flatpak/runtime/org.gnome.Platform/x86_64/45/547c38809093f20a153446421224c4d197bc8ce24d3c5cdd4bab978bbf9b3c83/files/lib/systemd/portable
/var/lib/flatpak/runtime/io.elementary.Platform/x86_64/7.3/d9fc7a37330ed6b142000e020f6c74eac5905daba9af1b70028a583dca8f03d4/files/lib/systemd/portable

I've highlighted in blue the files with musescore in them.  I'm assuming that the other files don't have anything to do with them, but I'm not sure.  Was wondering if you could let me know if I can use the "remove" command to eliminate those two files, and how to correctly enter it.  I don't want to remove files that I need.

---

### Post by ajgreeny on 2024-11-05
I've no idea about those portable versions but I suspect they may be flatpacks and those unmarked files in the list may be needed for those flatpack versions to run

Perhaps just move them to Trash rather than remove them completely; you can then restore them if needed.

I've never used flatpacks hence my lack of knowledge.

---

### Post by apkpin on 2024-11-13
[COLOR=#000000][INDENT]Honestly I don't know how they were installed -- it had been so long since I've used them. They've got to be somewhere on my computer, but I wouldn't know where to look for them. I can only guess and say that I installed them from the app center in [elementary OS]("https://www.apkpin.com/"). But I can't even be sure about that.[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by 1fallen on 2024-11-13
This will find them all:
```
[FONT=monospace][COLOR=#54FF54]**>**[/COLOR][COLOR=#000000] locate musescore[/COLOR]

```
This will narrow it down a bit:
```
[/FONT][FONT=monospace][COLOR=#000000]flatpak list|grep musescore[/COLOR]

```
When MuseScore gets updated via Flatpak it dumps an appimage in Downloads:
```
[/FONT][FONT=monospace][COLOR=#000000]ls Downloads [/COLOR]
[COLOR=#5454FF]**"1.All-DL's"**[/COLOR][COLOR=#000000]   [/COLOR][COLOR=#54FF54]**MuseScore-Studio-4.4.3.242971445-x86_64.AppImage**[/COLOR]
[COLOR=#000000] [/COLOR]
```
Seems rather silly to me due to this:
```
[/FONT][FONT=monospace][COLOR=#000000]locate -i appimage | grep -i musescore[/COLOR]

```
Nothing found.

[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]

[/FONT]

---


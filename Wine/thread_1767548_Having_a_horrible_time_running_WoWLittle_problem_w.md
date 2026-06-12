---
title: "Having a horrible time running WoW/Little problem wth WIne as well?"
date: 2011-05-25
forum: Wine
---

### Post by Super10.10 on 2011-05-25
Hello there folks, I am veryyyyy new to Ubuntu and linux in general, I've been a Windows guy for a long time. I'm not 100% sure if this is the correct section to post this in, but I did look around and this looks like it would fit here..sorry if it does not, I am also new to these forums, this would be my first post :guitar:. 
  I am running Ubuntu 10.10 legit and I just  recently finished installing WoW also legit off the blizzard/battle.net  site. I finished patching it is all up to date. When I went to install  it, it said it was going to my c:/program files like it always does and  should by default, I did not change it..now I need to get to the wow  directory and it is no where to be found. I looked in my wine c: drive  program files, all thats in there is a three folders, common files which  is empty, users, and IE. All three are useless in my situation. I  checked my home folder/username/ but nothing is in there..downloads  folder is empty, nothing in the documents or anything either. I then  checked my computer -- system file and didn't find anything..

   this is a problem for me. Also with wine, I have no .wine folder in my  home folder like I'm supposed to? I tried to configure wine so that it  would leave a directory behind in the home folder and nothing  happened...? I mean there's only so much configuring I can do? I  selected my windows in the app. tab even though I'm not using windows,  and I auto detected for drives, only thing that added in was h:  home/username and then I tried to configure the audio but it was already  on the right box and that's all anyone has said to configure..I really  would just like to play some wow so if you can help me through this  ridiculous nightmare, please do. thank you for your time.


                                      Also  if it means anything to anyone I have a folder in my Applications  section that says 'Windows Games' and has WoW in it and only wow..course  clicking it doesn't do anything lol..Sorry for the wall of text but I have been at this since saturday..I've pulled two all nighters trying to get this down already, heh. Thanks guys. :(

---

### Post by Sandlst on 2011-05-26
This probably belongs in the wine subforum, but I'll try to help you out some :)

Wine creates a windows file hierarchy in the .wine subfolder in your home directory.  Since it is hidden by default you will have to go to the view tab in the file browser and turn on "show hidden files." I would recommend running wow from a terminal to try to get meaningful error messages; you can do this by running ```
wine ~/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe
```From a terminal.

---

### Post by Super10.10 on 2011-05-26
Oh cool, well alright..now I see the .wine folder but still can't find the wow directory anywhere. I tried to run it from the terminal and got a very simple: 'wine: cannot find '/home/username/.wine/drive_c/Program Files/World of Warcraft/WoW.exe'  I mean it's gotta be somewhere lol..I did install it off the site and I have it all up to date etc..

Should I move this to the wine area, do I have to delete this thread first?

---

### Post by Sandlst on 2011-05-26
Hmmmm I have my wow copied on a usb drive, so I haven't run it from the default wine location in quite some time, I assume I must have misremembered the path.  So since you can see the .wine folder, what's inside it? Is it empty? Unless something major has changed in how wine works, your wow directory should be buried in there somewhere....if not I probably can't be of much help I'm afraid.

---

### Post by Super10.10 on 2011-05-26
Yeah I would love to do it that way but the PC I was using crashed completely and I have no windows on this pc :(. But yeah I'll go do some extensive digging then, but for now I'll let you know what's in there.. first is a folder dosdevices which lets me access my c: h: and z: wine c drive, home, 

  and my computer system file I believe, then there's drive_c which has program files, users, and a windows folder in it..windows has like system, command, fonts, system32, temp, winsxs, inf, help and a couple other things like IE, program files has common files and IE folder in it..common files is empty. then there's a system.reg, user.reg, userdef.reg, and .update-timestamp.

Did I maybe do something wrong?..all I've done so far is just install/patch it off the site and install wow off the software thing provided by ubuntu and configured it as much as I could?

---

### Post by Paddy Landau on 2011-05-26
Wine is not guaranteed to run all Windows programs (in fact, it's a bit of pot luck).

However:

I recommend that you do not install anything directly under Wine. Instead, install [PlayOnLinux]("apt:playonlinux").

PlayOnLinux is a front-end to Wine, hiding much of its complexity. It helps you to install each Windows program in its own "prefix" (i.e. independent area). This means that different Windows programs do not interfere with each other (unless you choose to install them in the same prefix), and uninstalling a program is lightning fast (PlayOnLinux simply deletes its prefix).

Once you have installed PlayOnLinx:

[LIST]
[*]Start PlayOnLinx.
[*]Press the big Install button.
[*]Start typing "world" into the search bar.
[*]Select "World of Warcraft" (I presume that's what WoW means).
[*]Press Apply.
[*]Follow the instructions.
[/LIST]
I have never used Wine directly; I find it too complicated. Every Windows program I have installed has been through PlayOnLinux. There are very few programs that PlayOnLinux recognises (WoW is one of them), but the others you can install using the button "Install a .pol package or an unsupported application".

Good luck.

---

### Post by Sandlst on 2011-05-26
Hmmm, have you tried searching (via places menu since you're using 10.10) for World of Warcraft?  If you can manage to get the search to find it, you should be able to see where it is located.  Once you know that, you can go ahead and drag it somewhere more convienent like your desktop or home folder.

---

### Post by Super10.10 on 2011-05-26
Well actually I did try to use playonlinux, I ran the install etc and it came to a point where it asked me if I am using 4, 5 cd's or one dvd..I didn't really know what to pick so I picked one, then it asked me something like are you sure it's patched or something and I didn't really have a choice but yes so I went for that and it finished..tried to open it up and nothing happens, I do something wrong? Like I said, I'm horribly nooby with anything ubuntu-related..

Yeah I searched 'world of warcraft' in my file system+username, should I search for it somewhere else? I think I'll try to install it via playonlinux again and see how that goes..any of you guys ever use crossover games to install/run it and such? How did that work?

---

### Post by cwwilson721 on 2011-05-26
Forget Play On Linux. You need NOTHING else to run WoW.

WoW is installed, by default, in the:
```
~/.wine/drive_c/Program Files/World of Warcraft
```folder.
("~" is a shortcut way of saying your home folder, i.e. /users/<username>)

To launch WoW successfully, first run (in a terminal) ```
winecfg
```This sets up the folder itself, and if needed, asks you to install Gecko (DO THIS)

Next, make sure you have your proprietary drivers installed from System > Administration > Additional Drivers

If you have an Intel chipset for video, good luck is all we can say. It might work, it probably won't, and even if it does, doing more than questing with all settings to lowest possible will still be slow. Forget Cities, 5mans, raids, etc.


Next, try to launch WoW with the following command (substitute your actual username for <USERNAME>):
```
env WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```
This tells wine to run in the '.wine' folder, to launch the WoW Launcher, and to run in opengl mode. 

You should be good to go after this.

Why not use Play On Linux (POL)? Because it just adds one more layer of complexity to an easy-to-run game. So why use it?

---

### Post by Super10.10 on 2011-05-26
Alright well I did the proprietary driver thing and it said none was in use..but I'm using an ATI video card, not intel. I tried to run those codes you gave me and got a simple 'directory not found/no such directory exists' which is the biggest problem I've been having, it's not in the .wine/c:/program files and I can't find the directory..but, it's installed..should I just try to install it again? It said it was going to c:/program files when I installed it like usual by default..

---


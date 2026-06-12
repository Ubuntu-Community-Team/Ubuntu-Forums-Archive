---
title: "Sidebar Icons-How to edit Properties?"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by emarkay on 2012-04-15
Have the CONKY one as a grey folder symbol with a Question Mark.  Pretty OK for an unknown, but I know what I have  I want one of those purdy picture thingies there that I gots' on my disk...

---

### Post by cariboo on 2012-04-16
Depending on where the .desktop files are located, either /usr/share/applications or ~/.local/share/applications, you can edit the files to your needs. I use this one to ssh into my server via a right-click.

```
[Desktop Entry]
Version=1.0
Name=Remote Servers
Comment=Login to my servers
Exec=gnome-terminal --disable-factory --sm-client-disable --class=remoteserver $
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=utilities-terminal
StartupNotify=true
StartupWMClass=RemoteServers
X-Ayatana-Desktop-Shortcuts=Server1;

[Server1 Shortcut Group]
Name=SSH into willy
Exec=gnome-terminal --disable-factory --sm-client-disable  --class=remoteserver$
TargetEnvironment=Unity
```

---

### Post by stinkeye on 2012-04-16
**@ emarkay** Not sure what you are trying to do, but to put an icon on the launcher for a personal script you can use alacarte.
```
sudo apt-get install alacarte 
```

eg
I have a script to toggle the sound output between the headphones and speakers.
Using alacarte I added a **new menu** called Scripts and then added a
**new item** with the command pointing to the script.
You can change the icon as shown in the pic.
You can use a downloaded icon by just browsing to it.

This will create  a .desktop file in **~/.local/share/applications**
which will be picked up in a dash search for applications.

You can then search in the dash and drag and drop to the launcher.

---

### Post by emarkay on 2012-04-16
All fine and good. But... 
Install CONKY and have it load at startup.

Note the question mark on the sinister side of the screen. Lame, eh?
Without hacking cracking or wailing. I want something more literal. 
Right click does not bring up options.

By default, how to correct this?

Say I have CONKY ands DONKEY and they both have "?" in their little picture icon.

You now see the fault inherent in the system?

So, how to fix this, or do I need to file another "bug" for a "feature"?

---

### Post by stinkeye on 2012-04-16
> **emarkay said:**
> All fine and good. But... 
Install CONKY and have it load at startup.

Note the question mark on the sinister side of the screen. Lame, eh?
Without hacking cracking or wailing. I want something more literal. 
Right click does not bring up options.

By default, how to correct this?

Say I have CONKY ands DONKEY and they both have "?" in their little picture icon.

You now see the fault inherent in the system?

So, how to fix this, or do I need to file another "bug" for a "feature"?
The queston mark is the fallback icon where there is no associated icon.
Edit the .desktop file to use a particular icon.
eg I have used a downloaded icon for the conky launcher.

---

### Post by zombifier25 on 2012-04-17
Yeah. Conky does not have any icons associated with it, so you need to add one yourself. If you want, you can contact the devs to add an icon. It's not Ubuntu's fault.

---

### Post by ranch hand on 2012-04-17
What it boils down to is that you have the choice of editing the config files or living with it.

Real computer users do not want to change the default.  Only elitist gurus do that sort of thing.

I suggest Xfce, preferably under Debian, but Xubuntu 12.04 is pretty nice.  

Xfce hasn't read the experts reports yet on usability so they still allow for customization.  Probably developed by elitist gurus.

---

### Post by Dngrsone on 2012-04-17
> **ranch hand said:**
> 
Real computer users do not want to change the default.  Only elitist gurus do that sort of thing.


[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]  *Who*'s being elitist?

To edit the .desktop file, you will likely have to open a terminal, type in the following:

```

gksudo gedit

```

and, using gedit (or substitute for what ever text editor of your choice you have installed), hit Open and surf to the location of the conky.desktop file, likely in /usr/share/applications and edit it to point to the icon of your choice.

For instance, for my Daily Firefox profile launcher, I have linked to a fixed location for my icon:

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/dngrsone/.icons/Daily.gif
Name[en_US]=Daily
Exec=firefox -no-remote -P Daily
Name=Daily
Icon=/home/dngrsone/.icons/Daily.gif

```

This code is legacy from a 11.04 install a year ago, so there may no longer be a need for two icon pointers, but the gist is there.

---

### Post by mc4man on 2012-04-17
it's likely a .gif isn't suitable for the launcher though haven't tried

---

### Post by Dngrsone on 2012-04-17
> **mc4man said:**
> it's likely a .gif isn't suitable for the launcher though haven't tried

.gif is fine, or you can use .png

---

### Post by mc4man on 2012-04-17
> **Dngrsone said:**
> .gif is fine, or you can use .png

Ok- then I'd try removing the one of the duplicate lines, probably the 1st one, - Icon[en_US]=

(Can you use a .gif & see animation in the launcher?

---

### Post by Dngrsone on 2012-04-17
> **mc4man said:**
> Ok- then I'd try removing the one of the duplicate lines, probably the 1st one, - Icon[en_US]=

(Can you use a .gif & see animation in the launcher?

It works fine for me the way it is.  Actually, now that I think about it, this was a Docky script... *that's* why I have two icon indicators there-- the first instance was for the launcher and the second is what Docky used.

I haven't tried an animated gif...

**Edit: No, animations don't work.  That is, you will have an icon, probably based off the first image of the animation, but it will not be aninimated.

---

### Post by stinkeye on 2012-04-18
> **Dngrsone said:**
> [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]  *Who*'s being elitist?


You might find he's being sarcastic.
It's quite common nowadays for people to interject their dislike of unity
into help threads instead of "The Community Cafe".
Even the OP uses such gems as "sinister side of the screen" to describe the unity launcher whereas I take the view that customization will most likely improve as the product develops.

---

### Post by Dngrsone on 2012-04-18
> **stinkeye said:**
> You might find he's being sarcastic.
It's quite common nowadays for people to interject their dislike of unity
into help threads instead of "The Community Cafe".
Even the OP uses such gems as "sinister side of the screen" to describe the unity launcher whereas I take the view that customization will most likely improve as the product develops.

Whatever.

Personally, I *like* the launcher, which is why, when I gave up 11.04 for a lost cause, I tried using Docky in 10.04.

Unfortunately, *that* was kind of a lost cause, as well.

I *am* hoping Unity will open up a little more as time goes by, otherwise I will have to start building up some hacking muscle...

---


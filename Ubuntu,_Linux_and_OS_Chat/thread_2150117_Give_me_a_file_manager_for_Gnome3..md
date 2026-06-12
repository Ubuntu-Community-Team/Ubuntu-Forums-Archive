---
title: "Give me a file manager for Gnome3."
date: 2013-05-31
forum: Ubuntu, Linux and OS Chat
---

### Post by DisappearingOak on 2013-05-31
I just wanted an editable path bar but Nautilus don't seem to have that feature and I had to go search Google finally to locate it in tweak tool. I just want a conveniently located Open as Root/sudo option in right click to every folder and file. I don't want to do gksudo nautilus everytime I need privileges for a folder. I want a split pane option. Maybe some nice views like Windows Explorer has like that preview pane with slideshow/theatre, large thumbhnails when I'm looking for images? Anything? The alternative file managers seem to be the 'Orthodox' type,. which are useful when working with multiple folders and files for quick move, copy, delete, permissions and other operations but how about a general use file manager to use also? Dolphin is not too good either. Do I need plugins or something? What file manager supports these types of plugins?

---

### Post by Frogs Hair on 2013-05-31
If using 13.04 [http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)

---

### Post by montag dp on 2013-05-31
You can switch to typing in the path by using CTRL+L, and then go back using ESC.  That way you don't need to change it in the tweak tool.  I could have sworn there was another way to do it as well, because I thought I had done it before, but I can't figure it out now.

About the other questions, I don't really know because I don't use Nautilus for that.  I'm more likely to use the terminal to modify root files, etc.

---

### Post by MadmanRB on 2013-05-31
[https://launchpad.net/~marlin-devs/+archive/marlin-daily](https://launchpad.net/~marlin-devs/+archive/marlin-daily)

just add the repo for your respective version
so if you are using Raring:
deb [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) raring main

---

### Post by monkeybrain2012 on 2013-05-31
> **montag dp said:**
> You can switch to typing in the path by using CTRL+L, and then go back using ESC.  That way you don't need to change it in the tweak tool.  I could have sworn there was another way to do it as well, because I thought I had done it before, but I can't figure it out now.

About the other questions, I don't really know because I don't use Nautilus for that.  I'm more likely to use the terminal to modify root files, etc.

The other way is to use dconf-editor. Install dconf-tools, then open the doconf-editor and navigate to org > gnome > nautilus > preferences and check the box "always-use-location-entry" 

Do it this way you can't switch back and forth on the fly, but I can't see why one would want to do that.

---

### Post by monkeybrain2012 on 2013-05-31
> **MadmanRB said:**
> [https://launchpad.net/~marlin-devs/+archive/marlin-daily](https://launchpad.net/~marlin-devs/+archive/marlin-daily)

just add the repo for your respective version
so if you are using Raring:
deb [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) raring main

Yeah but does it remove nautilus? If not you will have two file manager existing side by side which is confusing and may lead to problems because of which controls what and how paths are handled etc (I read that there are some issues like that with installing nemo in Ubuntu via ppa, I suppose Marlin would be similar) Frogs hair's solution seems to be cleaner.

---

### Post by MadmanRB on 2013-05-31
> **monkeybrain2012 said:**
> Yeah but does it remove nautilus? If not you will have two file manager existing side by side which is confusing and may lead to problems because of which controls what and how paths are handled etc (I read that there are some issues like that with installing nemo in Ubuntu via ppa, I suppose Marlin would be similar) Frogs hair's solution seems to be cleaner.

No that is nonsense, Marlin does not take the system hostage thus it will be fine.
The only harm Nemo does is due to it being tied to cinnamon, but marlin is its own thing thus not tied into the system or gnome in any way.

---

### Post by monkeybrain2012 on 2013-05-31
So it will duplicate a lot of Nautilus functions but cannot replace it? What I am asking is, if say you decide you want to use Marlin full time, is it possible to get rid of nautilus without breaking your desktop?

---

### Post by monkeybrain2012 on 2013-05-31
My issues with Files (new name for Nautilus) in 13.04 are the followings: 1: The "File" menu now appears in the top bar without any local menu, if remove global menu the File menu just disappears. So I am forced to use the global menu which is a pain. 2: The absent of F3 split window function, it is idiotic to remove this function. 3. There is a bug so that if you open an external partition and minimize it and then try to restore it by clicking at the icon on the Unity bar, it will open a new instance of Nautilus instead of restoring the already opened one (only happens with external devices or partitions)

The soluOS's patched version of Nautilus 3.4 (frog hairs' link) solves all these problems. It does it in a clean way (unlike nemo) by simply replacing the 13.04 version so there is no issue of duplication or having two competing file managers in the same system. I would have used it myself if I were not using the compiz performance enhancement ppa  There seems to be some strange interactions so that the patched version of Nautilus becomes sort of slow when using the compiz ppa.

---

### Post by monkeybrain2012 on 2013-05-31
> **MadmanRB said:**
> [https://launchpad.net/~marlin-devs/+archive/marlin-daily](https://launchpad.net/~marlin-devs/+archive/marlin-daily)

just add the repo for your respective version
so if you are using Raring:
deb [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) raring main

I just did to check it out. Maybe I am missing something, but I don't seem to figure out how to show the full path in the top bar, or if there is anything like F3 in nautilus 3.4 and before. Also, I have set marlin to be the default file manager, but if I try to open a file browser in any application it is still nautilus. Maybe need to do this [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

EDITED: Ok, googling some more it seems that marlin never supports f3 like split window function and while it allows typing in the top bar, it doesn't support showing the path to some directory you just open (thus not able to copy it) So it begs the question, what is the advantage of marlin except it is "light"? It seems it is even more stripped down than Nautilus and introduces unnecessary duplications since you can't really keep nautilus out of the picture anyway (marlin doesn't draw the desktop, for example)

---

### Post by MadmanRB on 2013-05-31
Marlin still has major functions over nautilus, like being able to change the wallpaper via the filemanager.
Marlin is intended to be a bit stipped down but with nautilus being stripped down too its looking better

---

### Post by monkeybrain2012 on 2013-05-31
> **MadmanRB said:**
> Marlin still has major functions over nautilus, like being able to change the wallpaper via the filemanager.
Marlin is intended to be a bit stipped down but with nautilus being stripped down too its looking better

Well I am not sure what is achieved by being able to change wallpaper via the file manager while I can just right click on the desktop or use the setting manager. :) I would rather have functions that are useful (split screen , use location entry,--thanks heaven it is still in Nautilus) rather than "looking better" if I have to pick one or the other. And coming back to this thread, OP asked not which file manager looks prettier, but which one has the function he needs (turned out Nautilus actually has that even not enabled by default) ;)

---

### Post by pissedoffdude on 2013-06-01
What exactly do you need to edit? It might be safer to edit via the command line so that you know for sure what you're doing, in case anything major might happen.  That said, last I checked pcmanfm supports root  editing by simply going to tools>edit in root.

---

### Post by Copper Bezel on 2013-06-01
The project began before Gnome started simplifying Nautilus into the cleaner (and arguably less functional) UI it uses now. As it is, there's a lot less to distinguish it from Nautilus. I believe that, like Nautilus, it only gives a text pathbar when you press Ctrl+L. It *does* at least display the full location in the breadcrumb bar regardless of the window size, which is an irritating oversight in Nautilus.

Marlin *does* offer a quicklist item for launching with gksu.

---

### Post by AgentZ86 on 2013-06-02
I don't understand this problem but you could just use gftp it's got a nice double pane and you can change permission there too right click and adjust clickety methods

you don't have to use the ftp part either just use it for file browser and move stuff around if you like

---

### Post by VanillaMozilla on 2013-06-06
> **DisappearingOak said:**
> I just wanted an editable path bar but Nautilus don't seem to have that feature....
Press <ctrl> l (lower case L).

It's hidden but it works.  There's also a configuration option if you can find the right config editor.

Not entirely what versions this applies to, but it worked in Precise.

EDIT:  Aw, gee, I see these answers have already been posted.  :)

---


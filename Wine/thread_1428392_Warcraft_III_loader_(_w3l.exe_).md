---
title: "Warcraft III loader ( w3l.exe )"
date: 2010-03-12
forum: Wine
---

### Post by reflexsa on 2010-03-12
Hi all,

Just to start off I am not very experienced with ubuntu.

I currently have Warcraft 3 frozen throne version 1.24d using a loader with exe name w3l.exe.

When I try and run the game I received the following error:

Could not start War3.exe! Make sure the loader is in your Warcraft III install directory.

The game was working before it was updated. The loader was also changed with the update as far as I know.

If I run it in windows it works perfectly.

Any ideas?

Thanks in advance for any help.

---

### Post by asdfoo on 2010-03-12
> **reflexsa said:**
> Hi all,

Just to start off I am not very experienced with ubuntu.

I currently have Warcraft 3 frozen throne version 1.24d using a loader with exe name w3l.exe.

When I try and run the game I received the following error:

Could not start War3.exe! Make sure the loader is in your Warcraft III install directory.

The game was working before it was updated. The loader was also changed with the update as far as I know.

If I run it in windows it works perfectly.

Any ideas?

Thanks in advance for any help.


a)  how are you starting the game?

You need to cd into the application directory and then run it.

b) Which version of Wine are you using?  If it's 1.0.1, try updating to 1.1.40 after you have confirmed a.

---

### Post by beastrace91 on 2010-03-12
What Wine version are you running? From personal experience I can say that you should always be using the latest beta with WC3 :)

Regards,
~Jeff

---

### Post by reflexsa on 2010-03-13
Hey guys,

Im not 100% sure how to check what version of wine I have, but if I open the Wine configuration from the applications menu and click on "About" it says Wine 1.0.

As for how I am running the game, I made a launcher on the desktop as suggested by a site I was on.

In the launcher command is the following:

wine "/home/kevin/.wine/drive_c/Program Files/Warcraft III/w3l.exe" -opengl

Hope this info helps

---

### Post by asdfoo on 2010-03-13
> **reflexsa said:**
> Hey guys,

Im not 100% sure how to check what version of wine I have, but if I open the Wine configuration from the applications menu and click on "About" it says Wine 1.0.

As for how I am running the game, I made a launcher on the desktop as suggested by a site I was on.

In the launcher command is the following:

wine "/home/kevin/.wine/drive_c/Program Files/Warcraft III/w3l.exe" -opengl

Hope this info helps


The site is wrong.
Your wine version is over a year old.  Update to 1.1.40.

You need to cd to the install directory first, before running the app.  A lot of programs are broken and think they will always be started within the same directory as their file.  Not all, but many are broken this way, and if you are intent on starting it otherwise it can only lead to problems.

---

### Post by reflexsa on 2010-03-13
Ah ok.

Right, how do I update my wine. The way I installed was, I refreshed the list in the package manager then searched for wine and told it too install that.

When you say "cd to the install directory" I am not sure what that means exactly. Sorry I am useless with ubuntu.

---

### Post by reflexsa on 2010-03-13
On another forum they say the following is causing the problem:

Out of date runtime libraries.

It makes sense as the problem they described there is pretty much the one I am having.
They said I should run the following:

$ mkdir winetricks
$ cd winetricks
$ wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
$ sh winetricks vcrun2005sp1 vcrun2005

Unfortunately I am not at home at the moment so I can't test it

---

### Post by dyltman on 2010-03-13
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) here you can download latest wine, just follow the guide.

also insteed of starting w3l.exe start war3.exe or Frozen Throne.exe if you have the expansion installed.

edit: here's the command for adding repositories wine, just type this in your terminal

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
```

and then afterwards go to synaptic and search for wine and pick the latest one.

---

### Post by reflexsa on 2010-03-14
Ok, so now warcraft opens using the loader.
But now when I try to log into battle.net as soon as I have put in my details and click the next button it crashes with FATAL ERROR!

Despite many searches for the problem. I have not fixed it yet
Many of them suggest compile wine myself. Me being useless can't seem to get it right.

Attached is an image of the error and the terminal text 

[IMG]http://img386.imageshack.us/img386/5223/screenshotgt.png[/IMG]

Hope this helps. :(

---


---
title: "Question about fronted of Wine(POL)"
date: 2009-06-21
forum: Wine
---

### Post by demontager on 2009-06-21
Halo,  have a question about PlayOnLinux, I need to run games from POL and check how it goes in terminal like in Wine or .log file like in cedega. Because I have  problems with running of some games and i want to trace a reason. How can i do that?
I run game from terminal with executing $playonlinux --run starter.exe, but it shows pop-up message indicating that program didn't installed(sorry, it in russian on screenshot). Why? If my game "Evil_Islands" installed in Playonlinux and I can run it freely from POL GUI? 
[http://www.megaupload.com/?d=M93OFCZL](http://www.megaupload.com/?d=M93OFCZL) 

And second, I saw "Debug Playonlinux" in POL GUI menu "Utilities" ( there also autostart, launch unofficial script, kill wineserver and manage wineversions), but how it works? Sorry i can't understand, I pressed it, but nothing happens.

---

### Post by ackanao on 2009-06-22
I think this is the simplest way to do what you want:

Go to "**/home/<YOUR_NAME>/.PlayOnLinux/configurations/installed**" folder and there you'll see the script for your game. Open the script in your text editor (gedit) and comment out this line:

```
export WINEDEBUG="-all"
```

it should look like this:
```
#export WINEDEBUG="-all"
```

Or if you want to turn on different "debug channels" for your game then put what you want instead of **"-all"**. Use "man wine" to see some explanations or take a look at "Wine User Guide":

[http://www.winehq.org/docs/wineusr-guide/x542]("http://www.winehq.org/docs/wineusr-guide/x542")

As for your other questions:

What version of POL do you use? In POL 3.5 under "Tools" menu there's:

**Manage wine versions** - it allows you to install any Wine version you want; Here you can choose which Wine version you want to use with different applications - For example: You can set Wine 1.1.16 for Office2007 and some other version of Wine for your Evil Islands game

**Kill wineserver process** - this will kill wineserver process

**Run a non-official script** - if you want to use your own POL script for installation of your application/game

**PlayOnLinux debugger** - launches xterm

**Autorun** - this will scan for your optical drives and mounted ISO's and then will start Installer for your application/game if it finds any.




Hope this helps...

---


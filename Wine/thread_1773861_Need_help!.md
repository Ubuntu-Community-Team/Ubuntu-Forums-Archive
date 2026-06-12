---
title: "Need help!"
date: 2011-06-02
forum: Wine
---

### Post by domoappo on 2011-06-02
So I just bought a PC game and it says I need either XP or Vista to run it. What do I need to do to get the game running? I heard of this thing called Wine that like lets people run things on Ubuntu as if it was Windows. Please keep in mind that I'm not very good/smart with computers.

Thanks!

---

### Post by ubudog on 2011-06-02
Welcome to Ubuntu!  Wine can be used to run many Windows games.  For running Windows games, it is usually used in combination with another great tool called PlayOnLinux.  You can download PlayOnLinux from here:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Just click on Ubuntu, and download the .deb file.  Open your Downloads directory, and double click the downloaded file.  The installation process is quite straightforward, and the Ubuntu Software Center will help you install it.  After that, go to Applications>Games>PlayOnLinux, and it will configure itself for you (it only does this once).  After all that is done, close PlayOnLinux.  Insert the Windows game CD.  Open PlayOnLinux again, click on Install, and search for your game.  Click on the correct game version, and proceed with the install wizard.  After it installs, your game should be accessible in Applications>Wine>Programs.  Hope that helps you!  Let me know if you have any questions.

---

### Post by domoappo on 2011-06-02
Okay I'm downloading it right now. I'll let you know how it goes. Thanks for the help ubudog. How can I help support you for Ubuntu Membership?

---

### Post by ubudog on 2011-06-02
> **domoappo said:**
> Okay I'm downloading it right now. I'll let you know how it goes. Thanks for the help ubudog. How can I help support you for Ubuntu Membership?

Cool, I hope it works for ya.  

You can support me by clicking the link "supporting" in my signature.  Then, just add a reply to the thread.  I really appreciate it!  :-)

---

### Post by domoappo on 2011-06-02
Mercenaries 2 isn't on the list... what do I do now?

---

### Post by mips on 2011-06-02
[http://wine.1045685.n5.nabble.com/Bug-21828-New-Unable-to-launch-Mercenaries-2-td1573858.html](http://wine.1045685.n5.nabble.com/Bug-21828-New-Unable-to-launch-Mercenaries-2-td1573858.html)

---

### Post by ubudog on 2011-06-02
> **domoappo said:**
> Mercenaries 2 isn't on the list... what do I do now?

Man... try this:
Open the CD using the file browser.  Right click on the setup.exe file, if there is one.  Sometimes it has a different filename.  Anyway, then click on "Open with Wine Windows Program Loader", and proceed through the installation wizard.  That may or may not work.  Good luck, and post back if it works or not!  :)

---

### Post by domoappo on 2011-06-02
Alright, I tried that and got this:

The file '/media/MERCS2_EN/EASetup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by ubudog on 2011-06-02
Ok, try this.

Right click Setup.exe, and select properties.  Then click on the Permissions tab.  Check the box that says "Allow executing file as a program".  Then try my previous post again.  :)

---

### Post by domoappo on 2011-06-02
I got this:

Sorry, could not change the permissions of "EASetup.exe": Error setting permissions: Read-only file system

---

### Post by ubudog on 2011-06-02
Are there any other setup files on there?  Perhaps a "Mercenaries2" executable file?

---

### Post by ubudog on 2011-06-02
In fact, could you please post the output of:
```
ls /media/MERCS2_EN
```
(run that command in a terminal)

---

### Post by domoappo on 2011-06-02
I tried the other .exe files and non would run. I tried to allow executing file as a program and It told me that option couldn't be changed. I punched that into the terminal and got this:

Autorun      d3d.log    EASetup.exe       _mercs2.ico  Precache.cab
autorun.dat  data       English1.cab      mercs2.ico   Redistributable
AutoRun.exe  Data0.cab  GDFBinary.dll     Mercs2.ini   Support
autorun.inf  DirectX    Mercenaries2.exe  Patches.cab

---

### Post by ubudog on 2011-06-02
Hmm... now punch this into the terminal:
```
cd /media/MERCS2_EN && wine Mercenaries2.exe
```

Post the output of all that.  Hope that works... let's see.

---

### Post by domoappo on 2011-06-02
This is what I got. Once again, thanks for the help ubudog!

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library binkw32.dll (which is needed by L"Z:\\media\\MERCS2_EN\\Mercenaries2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\MERCS2_EN\\Mercenaries2.exe" failed, status c0000135

---

### Post by ubudog on 2011-06-02
No problem, glad to help.

Try this command:
```
cd /media/MERCS2_EN && wine AutoRun.exe
```

And post the output of that.

---

### Post by domoappo on 2011-06-02
Okay I did that and it started to run, I went through some legal stuff and it asked me for the game code which I put in. However when I click on the Mercenaries 2 World in Flames icon on my desktop, the game doesn't start. But when I'm disconnected from the internet and I try to start it, it tells me I need to be connected to authenticate the game.

---

### Post by ubudog on 2011-06-03
Hmm... at least we got past that.  Try running the same AutoRun thing as before.  It may have a built in option to launch the game.

---

### Post by mips on 2011-06-03
> **ubudog said:**
> Ok, try this.

Right click Setup.exe, and select properties.  Then click on the Permissions tab.  Check the box that says "Allow executing file as a program".  Then try my previous post again.  :)

You cannot change permission on read-only media like cd/dvd.
You can however copy the entire content to your hard drive and then change the permissions.

---

### Post by ubudog on 2011-06-03
> **mips said:**
> You cannot change permission on read-only media like cd/dvd.
You can however copy the entire content to your hard drive and then change the permissions.

Yes, that could be a good option.

Try the following:
Make a directory in your home directory called "Mercenaries2" without the quotes.

Go to your CD using the File Browser, select everything, and copy it to the folder you created previously.  Then, go to that folder and change the permissions for Mercenaries2 (the executable).  Try double clicking on Mercenaries2.  It should run.  Let us know how it goes...

---

### Post by domoappo on 2011-06-04
It ran and Wine opened the little screen that starts up when you put a game in that offers you the option to play, it was basically the autoplay screen. I clicked play, the screen disappeared and nothing happened. Aside from this, I was curious as to how you get a game onto the list in playonlinux? Does somebody have to do something with the game or convert it to linux or something? Is there somebody I could ask to do this?

---

### Post by ubudog on 2011-06-04
Man, I'm sorry to tell you this... but according to Wine's App DB, Mercenaries 2 is just not supported.  What is the exact name of the game?  I'm afraid there are some things (like games), that just don't work on Linux, even with tools like Wine.  Do you still have a Windows install on your computer?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8226](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8226)

To answer your other question, I believe the developers and contributors of PlayOnLinux add games to their database.  

People don't convert games to Linux, there is just a tool called Wine that can run certain things by imitating a Windows environment.  (somebody please correct me if I am wrong)

Again, I'm really sorry I can't help you get the game working.

---

### Post by ubudog on 2011-06-05
If you have a Windows CD, you could install it into a virutal machine with VirtualBox, and run the game on there, without having to install Windows onto the computer.  Here is a screenshot of what something like that would look:

[http://farm4.static.flickr.com/3281/2568012677_6e6c0f8a1e.jpg](http://farm4.static.flickr.com/3281/2568012677_6e6c0f8a1e.jpg)

---


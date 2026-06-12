---
title: "How to build a desktop shortcut / multiple firefox profiles"
date: 2022-01-14
forum: Ubuntu/Debian BASED
---

### Post by frank105 on 2022-01-14
I feel close to my answer - but missing just a bit. 
Anyway - here it is:  I have Pop_OS 21.10 running on my laptop.  I want to add a "desktop icon" to launch a second Firefox profile for my wife when she uses my laptop.  I know "desktop icon" is sort of windows jargon - but I think you understand. 

So far I have a text file named Firefox.wife on my desktop.  In there is:

    firefox -p Wife

"Wife" matches the second profile I made in Firefox. I made the file "executable" in Nautilus/properties.  Double clicking it brings up a warning "Do you want to Run or display it's contents.  I have to click execute. 

Anyway - I just want to skip this step to make it simpler for her.  
Bonus points for adding the icon to the bottom launcher bar I think called "Favorites".  Currently I have an icon down there that opens my FF profile.  \

Thanks in advance,
Frank

---

### Post by Frogs Hair on 2022-01-14
This post could offer some suggestions. 

[https://askubuntu.com/questions/660147/how-can-i-use-two-firefox-profiles](https://askubuntu.com/questions/660147/how-can-i-use-two-firefox-profiles)

---

### Post by frank105 on 2022-01-14
Honestly - that is the thread I followed to get this far 

But I think it is old news when we get down to the area:
> Search for the line:

Actions=NewWindow;NewPrivateWindow;   and add new context menu action identifiers like this (example names,  but only used within the file, you won't see them anywhere else):


That didn't really seem to do anything.  But I may not have completely understood it.  But I did find a reference saying that everything changed after that version... but I didn't get an answer there either.  I know the command lines so I think I might be making this harder than it has to be.  

I think all I need to know is:  How do you turn a text file into an always understood to execute file?

Anyway - thanks a bunch for reaching out.

---

### Post by yancek on 2022-01-15
I'm not familiar with Pop OS but if you are using Nautilus/Gnome, the links below should help.  If you want a desktop icon, it does need a .desktop extension.  This is all expained in the links below. 

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

[https://fostips.com/app-icons-to-desktop-ubuntu-21-04/](https://fostips.com/app-icons-to-desktop-ubuntu-21-04/)

---

### Post by frank105 on 2022-01-16
> **yancek said:**
> 
[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)


Thanks - that was all I needed!!  

So yes - for anyone following me looking to do something similar in Pop_OS there are a few changes.  
For more help go to the links Yancek provided.  But in general it is really easy.
With your favorite text editor create a file named Firefox.desktop with the following lines:
```
#!/usr/bin/ xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/usr/bin/firefox -p Wife
Name=Firefox for Wife
Comment=Firefox
Icon=/usr/share/app-install/icons/firefox.png
```

So specifically my changes from the link are- 
Line 1 - You need to find the proper location in your system of xdg-open
Line 6 - Change to match the location of the executable.  If you don't know where it is - just type >which firefox  in the command line and it tells you.
Line 6 - So Firefox has switches to select profiles.  As I mentioned in my opening of the question - I already built the profile named Wife.  The "-p " switch is the select profile so just use the profile name you are trying to start.
Line 7 - Change this to whatever you like.  It is the text that shows up under the icon.
Line 8 - Unimportant
Line 9 - For bonus points - connect it to a good looking icon.  I just did a search for firefox.png and put the path in here.

After you build the file - then right click on the file on your desktop and select "Allow Launching".  

That (I think) should work for almost all Debian based distros. 

Thanks Yancek and everyone. 

Frank

---


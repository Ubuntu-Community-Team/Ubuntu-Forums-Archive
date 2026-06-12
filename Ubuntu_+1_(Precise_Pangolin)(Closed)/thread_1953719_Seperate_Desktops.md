---
title: "Seperate Desktops"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by crookiecookie on 2012-04-06
This is a work around to have as many desktops with their own desktop folders and icons as showen in the youtube link at a click of a button.

Youtube link  [http://youtu.be/ceg04_qpeeo](http://youtu.be/ceg04_qpeeo)

Now i have only been using ubuntu for about 1 month, been on windows all my life but needed a change :p

So i wont beable to give much support on this workaround because iam still getting my bearings around this system

This does not work with unity switch workspace but will get on to that later on.
Maybe some one who is clued up more then me on this system might beable to implement this into workspace.
In the mean time i will keep trying myself and keep you updated

I will be doing theese processes in steps. So lets go

1. Open home folder and make the screen fullsize.

2. On the toolbar at the top select view and click on view hidden files

3. Find a folder called .config and open it

Now i am using 6 desktops but you can have as many as you like just do all the processes the same for each desktop. I will be using this workaround for 6 in the next steps

4. Create 6 folders like this in .config

   desktop1
   desktop2
   desktop3
   desktop4
   desktop5
   desktop6

The reason i named them like this is so they are easy to find in .config

5. create a folder in .config like this

   launchers

6. copy the following file in .config

   user-dirs.dirs

7. paste the the file above in these folders in .config like so

   desktop1
   desktop2
   desktop3
   desktop4
   desktop5
   desktop6

8. Open desktop1

9. Open user-dirs.dirs in txt editor

10. find the following line

    XDG_DESKTOP_DIR="$HOME/Desktop"

11. Replace the following bit /Desktop" to what ever you want that desktop to be called like so

   /Hackingtosh"

12. Save

13. Do the same in all the desktop folders you created
    but make sure you dont have two of the same desktop names like

    /Hackingtosh" in desktop1
    /Hackingtosh" in desktop2
etc
They have to be diffrent in each folder.

14. Open the folder in .config called launchers

15. create 6 txt documents named

   desktop1
   desktop2
   desktop3
   desktop4
   desktop5
   desktop6

16. open document desktop 1

17. copy and paste the following script code inside

#!/bin/bash

gconftool-2-s-t bool/apps/nautilus/preferences/show_desktop false
cp /home/crookiecookie/.config/desktop1/user-dirs.dirs /home/crookiecookie/.config/
wmctrl -o 0,0
killall nautilus
sleep 0.01
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true; nautilus --no-default-window

# end script


18. Save

19. Do the same in each empty document but remember to change the following line

cp /home/crookiecookie/.config/desktop1/user-dirs.dirs /home/

to the desktop name like 

cp /home/crookiecookie/.config/desktop2/user-dirs.dirs /home/

cp /home/crookiecookie/.config/desktop3/user-dirs.dirs /home/
   
etc corresponding with each dektop no document you have open

20. You need to right click these documents and select all of the options on the permissions to allow execution so the files should be 777 permissions.

21. You have to install the following program from ubuntu software center

    Nautilus scripts manager

22 Copy all the documents ie: desktop1, desktop2 etc to the following folder

   /usr/share/nautilus-scripts

23. go to dash and type 

    nautilus script manager

24. Tick the box for all the desktop files like

    desktop1
    desktop2
    desktop3
    desktop4
    desktop5
    desktop6

25 Go to desktop and right click
   scroll on scripts on and select what desktop you want to use.

You can rename theese doing right click scroll on scripts and select scripts folder then simple rename to the desktop name you chose

Remember to open all desktop scripts so it creates the default folders in home.

Go to home now you can see your desktop names and Desktop, Desktop has all your old desktop items on them

Now you can simply change desktop at a simple right click of the desktop in scripts

Any files or folders now created will be saved only on that desktop loaded

Voila.

Now the only problem is i couldnt not implement this into workspace
it would be i deal that when you change workspace via switch it changes desktop too iam working on this but may take some time and proberly wont be able to do it
Maybe some one can help and implement it for us who knows

I have used a simple solution for this but its not the same
all i did say like i have hackingtosh, windows desktops
i have made it so my hackingtosh operating system only loads on workspace hackingtosh visa a versa for my windows operating system 
like showen in my video.

Hope this helps

They should make something like this workaround in thier Operating systems as standard but hay iam not a computer programmer so proberly dont what iam talking about.

---

### Post by cariboo on 2012-04-06
From that video, it looks like who ever made it is running a different instance of vbox in full-screen mode on each workspace. It's easy to do if you have a multi-core cpu and lots of ram.

BTW we don't support Hackintosh here, as it goes against Apples EULA about installing OSX on non-Apple branded hardware.

---

### Post by crookiecookie on 2012-04-06
This post is not about the other os system i just use them for diffrent programs like dreamweaver etc that was just an example 

Its about being able to switch to diffrent desktops with diffrent folders on them 

say like i have a buisness so i keep all buisness files and folders on seperate desktop called buisness

or i want a medie desktop i can  keep all media icons folders on that seperate desktop

and inter change between between the two as and when i need

Sorry i forgot to add in the originall post

THIS IS ABOUT DESKTOP ITEMS AND NOT OTHER OS
SO PLEASE DO NOT ASK ME HOW TO INSTALL THEM BECAUSE I WILL NOT ANSWER AS STATED IN POST ABOVE IT IS NOT ALLOWED BY APPLE

---


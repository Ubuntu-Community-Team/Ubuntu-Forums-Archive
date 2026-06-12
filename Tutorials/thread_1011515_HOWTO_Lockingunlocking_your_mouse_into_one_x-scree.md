---
title: "HOWTO: Locking/unlocking your mouse into one x-screen for dual-head users"
date: 2008-12-14
forum: Tutorials
---

### Post by Ng Oon-Ee on 2008-12-14
This HOWTO is specifically for users who want the following:-
a) A separate x-screen setup (TwinView/Xinerama users, this will not work for you).
b) Capability to allow the mouse to cross over from x-screen to x-screen.
c) Capability to DISallow the mouse to cross over from x-screen to x-screen.

The usage cases (that I can think of) are:-
a) playing full-screen games on one x-screen, so that the mouse does not escape the game into the other x-screen when edge-scrolling or rotating your FPS view
b) working on only one x-screen (perhaps while the other is just displaying output/your movie etc.)

In order to use this guide, you need to have already accomplished the following:-
a) A working separate x-screen setup (this HOWTO is not for such questions, there are much better HOWTOs around for that, with more qualified posters than myself).

So, on to the guide. Its really very simple, my references are these two links:-

[The Gentoo wiki's guide on Dual Monitors]("http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors")
[Homepage for MouseSwitch, the program we'll be using]("http://digamma.cs.unm.edu/trac.dmohr/wiki/MouseSwitchscreen")

So, firstly, download the latest version (0.3b as of this posting) from the second website above. Remember where you saved it. This is a tar.gz archive (if you're not familiar with them, they're sort of the same as zip files). Open your file manager and double-click on the file, extract the folder that it contains to your home directory. (If you're unsure of how to do this, click Extract, and select your home directory, which is normally the directory with your username, then click OK).

Next, you have to compile the program itself. First, you need the dependencies installed. For my install I only needed libXtst-dev, but others may need more, as I've been using my install for a while. Post here if there's any error messages in compiling. Anyway, to satisfy the dependencies, run in the terminal the following command:-

```
sudo apt-get install libXtst-dev
```

Once that's done, compile the program. It already has a makefile, so just change to the directory you extracted (the commands below show the default extraction directory) and run the 'make' command:-

```
cd ~/mouse-switchscreen-0.3b
make
```

If you have any errors at this part, it probably means you haven't fully satisfied the dependencies. Either google the errors to know which libraries you're missing or post here, I'll help you out.

Assuming there were no errors, browse to the folder above in your favourite file manager. There are two files you're interested in. One is an executable named mouse-switchscreen, another is a script named mouse-switchscreen.sh. Copy them into your home folder.

Now its time to test out your config. I'm assuming here that you have two monitors side-by-side. Now, go to the terminal and change directory to the folder containing the executable and script. Execute the script.

```
cd ~/
./mouse-switchscreen.sh
```

Now, move your mouse to the left-hand side of your left-most monitor. If it moves over to the right-hand side of your right-most monitor, the program is working as expected. Run the script again, as above, to kill the program.

Now, since the script is working, you should modify your xorg.conf so that your mouse cannot, by default, move between screens. First make a backup, then modify xorg.conf.

```
cd /etc/X11
sudo cp xorg.conf xorg_mouseswitch_backup.conf
sudo gedit xorg.conf
```

Inside xorg.conf you should see the following lines:-

```
...<some code>...
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
...<some other code>...
```

Your screen/layout names may differ, these are the default. Change the last line to

```
...<some code>...
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 2000 0
...<some other code>...
```

I set 2000 because my resolution is 1280 by 800. If you have a larger width resolution, please set the number 2000 to something larger than your resolution's width by at least 300-400. Alternatively, you can set the second digit to something much larger than your resolution height, no difference. All this does is 'break' the connection between your screens so the mouse cannot move between them.

Now, save the changes and restart X with Ctrl-Alt-Backspace. Remember to save all your work first! You should be brought back to login, and after that your system will not look different except you will not be able to move your mouse off any of the edges. That's fine. You have mouse-switchscreen to do this for you.

Now, before running the script again, edit it to your needs.

```
gedit ~/mouse-switchscreen.sh
```

After the 'ELSE', change the line from:-
```
./mouse-switchscreen >& $OUT &
```
to
```
~/mouse-switchscreen -l >& $OUT &
```

The important bits are changing the . to ~ (to directly call the executable) and -l which sets only the left edge of the first screen to be 'crossable'. You can use -r as well, if this is the opposite of what you want.

Then, add the script to a suitable keyboard shortcut. Run gconf-editor (just Alt-F2 and type 'gconf-editor' without the inverted commas), and browse to apps->metacity->keybinding_commands. Change one of the commands (I use command_1) to ~/mouse-switchscreen.sh. Then browse to apps->metacity->global_keybindings. Edit the shortcut key for the command you chose, since I'm using command_1, I edit run_command_1 to <Super>q. So, when you press the windows key (Super key) and Q at the same time, this will run the script. Running the script once activates your mouse being able to cross over, running it again deactivates cross over, locking your mouse in its screen.

Finally, most people would want the mouse to automatically be able to cross over when they logon. To do that, Go to the Preferences Menu->Sessions and click Add. The command should be ~/mouse-switchscreen.sh, the name and Comment is up to you.

That's about it. Advanced users will note that you can actually change the locations of the executable/script (I personally keep them in a separate folder), but I have not done so here, to minimize possible confusion. Hope it helps.


REMOVAL INSTRUCTIONS:

To remove all the changes, just delete the downloaded file, the directory you extracted it to, and the files created. The following deletes the created files (if you've followed this guide to the letter) but not the downloaded file or the extraction directory.

```
cd ~
rm mouse-switchscreen mouse-switchscreen.sh .mouse-switchscreen.out .mouse-switchscreen.pid
```

---

### Post by Sugi on 2009-06-27
Thank you for this HOWTO.  This helps with wine games and dual-monitor setups.

Sugi

---

### Post by wantime on 2010-05-26
Any idea of how to make a big screen "crossable" over BOTH horizontal (and vertical) edges in Xinerama?  Eg, move the mouse contiually around the screen circuit like the inside of a cylinder.

---

### Post by appleshampooid on 2011-12-02
I wanted to get this working on Ubuntu 11.10.

I downloaded the source but the default makefile wasn't working even after adjusting the lib path for my system, etc. It's been a while since I've complied a basic C program on Linux and it's pretty embarrassing that I couldn't figure out the problem, especially since I'm a software developer, haha (cries).

Anyway, I ditched the Makefile and was able to compile both programs successfully with just these commands:
```
gcc -Wall -o mouse-wrapscreen mouse-wrapscreen.c -lX11 
gcc -Wall -o mouse-switchscreen mouse-switchscreen.c -lX11
```
Probably a different version of the toolchain or something. Anyway, this worked on my 64bit installation of 11.10. Hope it saves someone else some time.
Cheers.

---


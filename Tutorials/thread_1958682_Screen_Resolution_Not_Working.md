---
title: "Screen Resolution Not Working"
date: 2012-04-14
forum: Tutorials
---

### Post by rhss6-2011 on 2012-04-14
Hi there - for everyone with issues regarding display resolutions (even if your computer is connected to a flatscreen...) I wrote this for a Debian Squeze forum and I hope you'll find it very helpful.
This is a ***VERY*** detailed guide so I hope that you don't mind a little reading...

---------------

Hello there,
I used to have a Laptop and after upgrading it in Linux the screen resolution wouldn't work anymore the way I wanted it (1200x800). After some research I found out how to more or less force the system to use the resolution I wanted, so here goes:

First of all -- use your terminal. Any terminal will do...

> USERNAME:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0 +   75.0  
   1280x800       60.0 +   75.0  
   1152x864       60.0 +   75.0  
   1280x768       59.9 +   74.9  
   1280x720       60.0 +
   1152x648       60.0 +
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)


Typing the command *xrandr* will tell you what you display is - in my case it's recognized as DFP2

Now Let's pretend you want a resolution of 1368x768

> USERNAME:~$ cvt 1360 768 60
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync


Using the command *cvt 1360 768 60* makes the terminal tell you what line you'll be adding to xrandr for a resolution of 1360 x 768 with a refresh rate of 60.
***NOTICE: You will want to copy the _"1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync_ into a text file or something as you will need it later...***

Now comes the fun part - telling xrandr to add the new mode to your display, and to use it:

----------------------------------------------

> USERNAME:~$ xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
USERNAME:~$ 

This adds the mode to xrandr and nothing else so we have to add it to your display configurations in order to use it:

> USERNAME:~$ xrandr --addmode DFP2 "1360x768_60.00"
USERNAME:~$

[b][i]NOTICE: The output of _DFP2_ is my personal monitor - you will have to replace that with your own!!!
Also notice, that there are no errors - if you have an error you'll have to change the resolution to something your system will recognize as a proper resolution format - I will add such formats at the bottom of this thread[/i][/b]

Now we need to force the monitor to use the desired resolution:

> USERNAME:~$ xrandr --output DFP2 --mode "1360x768_60.00"
USERNAME:~$

Now that your screen is using the resolution you want, we have one more step -- creating a start-up script. The next steps will:
1. Create a folder in your home directory in which we will place your personal script
2. We will use a text editor to create the script to change your resolution
3. From the script inside the folder we will tell Linux to automatically execute the script when you log in.

In the terminal:
> USERNAME:~$ mkdir /home/**YOUR-USER-NAME**/START-SCRIPTS
USERNAME:~$
[quote]USERNAME:~$ sudo gedit /home/**YOUR-USER-NAME**/START-SCRIPTS/resolution.sh
USERNAME:~$

[b][i]NOTICE: This will open up your text editor (Gedit in this case) with a new file called "resolution.sh"
Now just copy and paste the following text, or edit it as needed for your preferences[/i][/b]

> #!/bin/sh
#Edit the text file as you need it for your personal computer or use as is if you want the same resolution:
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync && xrandr --addmode DFP2 "1360x768_60.00" && xrandr --output DFP2 --mode "1360x768_60.00"
#Notice that you need to change the output DFP2 to whatever XRANDR recognizes as your display!!!

Now that we have the script we need to make it executable:

> USERNAME:~$ cd /home/**YOUR-USER-NAME**/START-SCRIPTS ; sudo chmod +x resolution.sh
USERNAME:~$[/quote]

Now, just go to your settings ---> Session and Startup ---> Application Autostart
And add the script just like you would any other application...


Resolution - Aspect ratio

720x480-----3:2
1152x768-----3:2
1280x854-----3:2
1440x960-----3:2
2880x1920----3:2

___________________

320x240-----4:3
640x480-----4:3
800x600-----4:3
1024x768-----4:3
1152x864-----4:3
1280x960-----4:3 
1400x1050-----4:3
1600x1200-----4:3
2048x1536-----4:3
3200x2400-----4:3
4000x3000-----4:3
6400x4800-----4:3 

___________________

800x480-----5:3
1280x768-----5:3

___________________

1280x1024-----5:4
2560x2048-----5:4
5120x4096-----5:4

___________________

852x480-----16:9
1280x720-----16:9
1365x768-----16:9
1600x900-----16:9
1920x1080-----16:9 

___________________

320x200-----16:10
640x400-----16:10
1280x800-----16:10
1440x900-----16:10
1680x1050-----16:10
1920x1200-----16:10
2560x1600-----16:10
3840x2400-----16:10
7680x4800-----16:10

___________________

2048x1080-----17:9

---

### Post by alf31 on 2012-04-16
> **rhss6-2011 said:**
> Hi there - for everyone with issues regarding display resolutions (even if your computer is connected to a flatscreen...) I wrote this for a Debian Squeze forum and I hope you'll find it very helpful.
This is a ***VERY*** detailed guide so I hope that you don't mind a little reading...

---------------

Hello there,
I used to have a Laptop and after upgrading it in Linux the screen resolution wouldn't work anymore the way I wanted it (1200x800). After some research I found out how to more or less force the system to use the resolution I wanted, so here goes:

First of all -- use your terminal. Any terminal will do...



Typing the command *xrandr* will tell you what you display is - in my case it's recognized as DFP2

Now Let's pretend you want a resolution of 1368x768



Using the command *cvt 1360 768 60* makes the terminal tell you what line you'll be adding to xrandr for a resolution of 1360 x 768 with a refresh rate of 60.
***NOTICE: You will want to copy the _"1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync_ into a text file or something as you will need it later...***

Now comes the fun part - telling xrandr to add the new mode to your display, and to use it:

----------------------------------------------



This adds the mode to xrandr and nothing else so we have to add it to your display configurations in order to use it:



[B][I]NOTICE: The output of _DFP2_ is my personal monitor - you will have to replace that with your own!!!
Also notice, that there are no errors - if you have an error you'll have to change the resolution to something your system will recognize as a proper resolution format - I will add such formats at the bottom of this thread[/I][/B]

Now we need to force the monitor to use the desired resolution:



Now that your screen is using the resolution you want, we have one more step -- creating a start-up script. The next steps will:
1. Create a folder in your home directory in which we will place your personal script
2. We will use a text editor to create the script to change your resolution
3. From the script inside the folder we will tell Linux to automatically execute the script when you log in.

In the terminal:


Now, just go to your settings ---> Session and Startup ---> Application Autostart
And add the script just like you would any other application...


Resolution - Aspect ratio

720x480-----3:2
1152x768-----3:2
1280x854-----3:2
1440x960-----3:2
2880x1920----3:2

___________________

320x240-----4:3
640x480-----4:3
800x600-----4:3
1024x768-----4:3
1152x864-----4:3
1280x960-----4:3 
1400x1050-----4:3
1600x1200-----4:3
2048x1536-----4:3
3200x2400-----4:3
4000x3000-----4:3
6400x4800-----4:3 

___________________

800x480-----5:3
1280x768-----5:3

___________________

1280x1024-----5:4
2560x2048-----5:4
5120x4096-----5:4

___________________

852x480-----16:9
1280x720-----16:9
1365x768-----16:9
1600x900-----16:9
1920x1080-----16:9 

___________________

320x200-----16:10
640x400-----16:10
1280x800-----16:10
1440x900-----16:10
1680x1050-----16:10
1920x1200-----16:10
2560x1600-----16:10
3840x2400-----16:10
7680x4800-----16:10

___________________

2048x1080-----17:9


great tutorials  :)

---

### Post by Kanna2412 on 2012-04-27
Hi, I followed your instructions above. When I add the text on "resolution.sh" file. The file is not saved saying the file doesn't exist. Please help me.

---

### Post by rhss6-2011 on 2012-04-27
Hello there Kanna,
I read your post and I am sorry for the delay. If you read my How-TO guide, I mention that you need to open the file in your preferred text editor/notepad which is in my case gedit...

When you (copy & paste) the text I give for the script, you then have to save it from your text editor of course. If you just close it your script won't be saved.

Assuming you did that... And the file was saved...
Typing any command in the terminal is case sensitive - so if you made a mistake in either your command, or in the saved file's name then it won't work...
Go to your terminal (and let's assume you followed my instructions to the letter...)

```
cd /home/**YOUR-USER-NAME**/START-SCRIPTS
ls -l
```

The last command will tell you what files are in the folder... Then (using your mouse) copy the file name and continue on...

---


---
title: "Help Installing Game with (2-4) CDs on Wine"
date: 2011-05-14
forum: Wine
---

### Post by TurtleKing on 2011-05-14
In order to narrow down the problem (on title), I decided to abandon my previous thread (Installing NFSMW & SWAT4) hopefully get more answers in reference to the problem rather than the game (I only had 1 person making suggestions in my previous thread which was odd until i read the title myself).

So to go into more detail about the problem, I am trying to install 2 games that bring more than 1 CD in order to install. Once I get the 1st CD to install I get a pop-up to insert insert disk 2 and click ok. However, when I try to eject (Right-Click on desktop CD Icon) the 1st CD I get a pop-up:
```
Volume is busy
One or more applications are keeping the volume busy.
(file icon)replaced@replaced:/media/NFSMW_DISC1
(terminal icon)replaced@replaced:/media/NFSMW_DISC1
*options: cancel & Unmount Anyway*
```When I click Unmount Anyway, the pop-up comes back up. The problem seems to be wine won't let go of the 1st CD. Does anybody know of a solution to this problem? In addition, is it possible to tell wine to look for it in a folder rather than the CD Tray?

Thanks in Advance.

---

### Post by insane_alien on 2011-05-14
paperclip in the manual release never fails

---

### Post by TurtleKing on 2011-05-14
> **insane_alien said:**
> paperclip in the manual release never fails
:confused:

Figured out a solution to overcome the 2CD pop-up:

We have to trick the game wizard into thinking our desktop is the cd tray. Set your mounted components to appear on your desktop. This can be done by Ubuntu Tweak/Desktop Icon Settings. If you don't have Ubuntu Tweak you can install it from the Ubuntu Software Center or whatever is the equivalent of Ubuntu Software Center for your distribution (Personally, I keep my on at all times, but it is up to you).

1. Insert your 1st CD into the CD tray (note: it should appear on the desktop (NFSMW_DISC1 or whatever your installing).

2. Create a folder with exactly the same name as the CD (I have not tested same name, but lets do it just to be safe).

3. Double click the 1st CD icon on your desktop (not the folder). You should have a window with all the stuff of CD-1 in it, hopefully. 

4. Copy and Paste everything in that window into the folder you just created on your desktop. Grab a paper or something to read while you wait (mine took 3 minutes).

5. Repeat step 1-4 with all other CDs needed to install the game you want.

6. Run Configure Wine which is located under application/Wine menu. The program can be from terminal as well with the following command:
```
winecfg &
```7. On Configure Wine look for the driver tab near the title bar, and click on it. Here look for D: under letter. If it is not there click on add button and it will usually have it ready, so click okay. Once you see D: listed click on it and click on the browse button next to the "path:" suggestion. Browse  through home/username/Desktop/CD1FolderName folder you created. and click  okay (don't open the folder as we want this to be where it looks). It  should list D: and the location of where your copy of CD1 folder is located. Click on apply button at the bottom of the window to save the settings.  Leave the window alone in the background for now.

8. Run a terminal (Application/Accessories Menu) and type (or copy and paste with your mouse) in the following commands, with each line meaning after you click enter for the previous one. Note edit your CD1FolderName with the actual CD1FolderName (don't just copy & paste this and hit enter, or I will give you such a pinch! :evil:) : 
```
cd Desktop
cd 1-CDFolderName:
```9.Look in here for an install.exe, AutoRun.exe, or Setup.exe  by using the folder you have on your desktop or after following the terminal command above type (don't be lazy):
```
ls
```10. Use the following command once you find that install.exe or whatever the program is  named (don't just  copy & paste this and hit enter, or I will give you such a pinch!):
```
wine Install.exe
```11. That should startup the wizard or game's installation program, and go fairly smoove till you come across the insert CD-2 pop-up. Here we go back to that Wine configuration window you had opened (don't close the game's installation program). We need to change the path of D: to the next copy folder of CD-2 you created. click on the browse button next to the "path:" suggestion. Browse  through home/username/Desktop/CD2FolderName folder you created. and click  okay (don't open the folder as we want this to be where it looks). It  should list D: and the location of where your copy of CD2 folder is located. Click on Apply button at the bottom of the window to save the settings.  Leave the window alone in the background for now.

12. Go back to the wizard you have running for your game (don't tell you closed it!?!) and click ok for that pop-up we got talking about inserting CD2. Now it should continue till the pop-up about CD3 (Or CD1 or finish. If finished, congratulations. And by the way, you owe your soul!:lol:). What is that?...you know what to do now?..Repeat step 11 and edit the path to the new copy of the CD folder it wants? Yes, How did you know?:-k

13. Hopefully, your installation should finish well and you will have an idea where to run the game from. Now, cross your fingers and hope that wine will take care of running the game without you needing to tweak it.[-o< If the game runs with the CD, simply switch the path of D: in Configure Wine to your CD1Folder in your desktop or switch it back to default which will make it look at the CD Tray. Don't pick install program again in the CD1Folder on your desktop (or CD1 from your CD tray) since we already did that step silly.;-)

Good Luck & Enjoy.

TurtleKing ):P

---

### Post by TurtleKing on 2011-05-14
Well first time it worked, 2nd time it wanted to start from actual CD1 in the CD Tray. Well, it is running now, so hopefully in the future we will finally get a native steam client on Linux to avoid all this mess.

---

### Post by BrandxG on 2012-07-24
I did everything ok until I got to the terminal step, over there when I have to type these commands I did the following:

I typed 	 	    cd Desktop  then I pressed enter 
 
afterwards i typed 
  	 	 	 	 	 	   cd 1-NBA LIVE2005_1:  which is the game I'm tring to install.

But it said " No such file or directory"

I would like you to help me please. 

Thank you so much for your help.

---

### Post by BrandxG on 2012-07-25
I did everything ok until I got to the terminal step, over there when I have to type these commands I did the following:

I typed 	 	    cd Desktop  then I pressed enter 
 
afterwards i typed 
  	 	 	 	 	 	   cd 1-NBA LIVE2005_1:  which is the game I'm tring to install.

But it said " No such file or directory"

I would like you to help me please. 

Thank you so much for your help

Please give me an example of how you would do it

---

### Post by BrandxG on 2012-07-25
Now I got to step 12 
over there after I set the location of second disc and click apply.
I go click the ok button on the insert disc 2 pop up but it doesn't  go on.

Do I have to go back to the terminal to make it work?

Please give me some more help I know you have already helped me with all this so thanks man:confused:

---


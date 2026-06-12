---
title: "Wine and WineTools"
date: 2005-12-13
forum: The Cafe
---

### Post by ndamix on 2005-12-13
Hello Ubuntu Community.

I'm a DB/Network administrator working with Windows products.  I found Ubuntu by chance and really enjoy working with it, in fact I may be a new convert.  

I wanted to post some notes I wrote this last week while attempting to load some Windows based software (Illustrator 9.0) on to Ubuntu.  After a few wrong turns and mis-steps I was able to make it work very good.  Anyway, any comments on my approach from more experienced users would be helpful.

.....The first pieces of software to install are Xdialog and Wine.  Open a Terminal window and enter the following code:

Switch to the root user:
**sudo –s** (at the prompt enter your password)

Open the sources.list file:
**nano /etc/apt/sources.list **

Edit the sources.list file by scrolling down and un-commenting the following lines: (Note that Linux uses the # symbol indicate a line of code is a comment.  To un-comment the line remove the # at the front of the line.) 
[B]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe[/B]

Next scroll down to the bottom of the file and add the following lines of code.
**# source for Wine**
[B]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ [/B](type ctrl x to exit the file and enter y when prompted to save the changes)

Install Xdialog and Wine:
[B]apt-get update
apt-get install xdialog
apt-get install wine[/B]

The above steps should install Xdialog and Wine.  You can leave the terminal window open because it will be used in later steps.

Install WineTools next.  To download the software open the web browser and navigate to [www.von-thadden.de/Joachim/WineTools/](www.von-thadden.de/Joachim/WineTools/).  Scroll down and find the link for the tar.gz file, click it and when prompted select the ‘save to file’ option.  You’ll notice that the winetool-0.9jo-ll.tar.gz folder has been created on the desktop.  To make the following steps easier rename the folder to winetools.tar.gz and move it off of the desktop to your home folder.  Select the terminal window now and enter the following code:

Unpack the compressed winetools folder:
**tar xvzf /home/*your user name*/winetools.tar.gz**

After unpacking you’ll notice that the winetools-0.9jo-ll folder is now in your home folder.  To make the next step easier rename the folder to winetools.

Move the folder to the correct directory:
**mv /home/*your user name*/winetools /usr/local/winetools**

Install shortcuts to the Winetools software:  (Note that in this case wt0.9jo is the name of the executable winetools file.  Verify that this file exists in the /usr/local/winetools directory.  If it is not the version that is in the folder change the line of code to reflect the correct version that is in the directory.)
[B]ln –sf /usr/local/winetools/wt0.9jo /usr/local/bin/wt
ln –sf /usr/local/winetools/findwine /usr/local/bin/findwine[/B]

Change from the root user back to your user identity in the terminal window:
**su *your user name***

Start WineTools to configure Wine:
**wt**  (The WineTools Main Menu will now open in a separate window.)

Configuring Wine with WineTools:
Select Base Setup from the main menu and do:
Create a fake Windows drive
Install True Type font Arial
Install Dcom98
Install Microsoft Foundation Classes
Install Internet Explorer 6.0
	Select Install Windows system software from the main menu and do:
		Install Windows Installer
		Install Visual Basic 6 runtime
		Install C++ runtime
		Install MDAC 2.8 and Jet SP8
		Install MSXLM 4.0 SP2 (Select customize option then install)
		Install Windows Script 5.6
		Install Common Controls 5.0
	Select Install Microsoft True Type Fonts from the main menu and do:
		Install all available fonts
	Select Install Tested Software from the main menu and do:
		Install Adobe Illustrator 9.0

---

### Post by curtis on 2005-12-13
Hi,
I always end up getting errors when trying to install IE.
It says that I am not connected to the internet, when I am.
It works fine in CxOffice, but I would prefer to use the latest version of WINE.
Thanks.

---

### Post by guano on 2006-02-14
Excellent!
I tried so many times to get Illustrator working under Cxoffice...

Now it is! Thanks man!

---

### Post by Mnemonicman on 2006-02-25
Excellent. Finally got Wine working. Thanks.

---


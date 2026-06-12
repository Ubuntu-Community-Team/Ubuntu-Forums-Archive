---
title: "How to install Canon LBP2900i printer in Ubuntu Mate"
date: 2014-11-11
forum: Tutorials
---

### Post by stevecook on 2014-11-11
The following is a tutorial on how to install the Canon LBP2900i printer in Ubuntu Mate 32 bit (for completeness, I should say, I am using an old Pentium D).
 
 I have split the tutorial into two parts. The first being sufficient to get the printer working easily at the start of each session by simply running a script after you log in. The second part shows how to run this script automatically at login. However, since running it automatically involves compromising the security of your system somewhat, you may choose to simply stop at the end of part 1. It's a matter of risk tolerance, I guess. For me, this is not an issue, but for you it may be.
 
_**  Part 1**_
 
 Download the following file. This is needed to make the printer driver work. If you don't download and install this file first, then the printer driver will not work.  
 
 "gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb"

 You can download it from:
 
 [http://packages.ubuntu.com/uk/lucid/all/gs-esp/download](http://packages.ubuntu.com/uk/lucid/all/gs-esp/download)
 
 If you double-click the downloaded file, it should automatically open in a deb installer. This will probably be the Software Centre.
 
 Once the above has been installed, download the printer driver from the link below:
 
 [https://github.com/raducotescu/CanonCAPTdriver/tarball/master](https://github.com/raducotescu/CanonCAPTdriver/tarball/master)
 
 It is in a zipped-up format called a "tar". Once downloaded, it should automatically open up in Engrampa archive manager (or, if you initially saved it instead, you can double click after it has downloaded and it will then open up in Engrampa). Extract the contents to your home folder.
 
 Once extracted, open a terminal. it will open in your home directory by default. If you type:
 
 **ls**
 
 you should se the "raducotescu-CanonCAPTdriver-c8ea9f9" directory there.
 
 Type:
 
 **cd raducotescu-CanonCAPTdriver-c8ea9f9**
 
 to go into the directory.
 
 If you type:
 
 **ls**
 
 you should see the following files:
 [B]
 canonLBP_install.sh
 canonLBP_uninstall.sh
 changelog
 DEBS
 LICENSE
 README[/B]
 
 Type:
 
 **sudo ./canonLBP_install.sh LBP2900**
 
 You will be prompted for your password (the same one you use to log into Ubuntu Mate). Type in your password and press the **Enter** key.
 
 Assuming all went well, above, the next step is getting the printer to work
 
 Assuming your printer is on, if you tried to print a document at this point, if would just hang in the print queue and would not print. This next step is what you need to do to make it actually work. It involves writing a bash script.
 
 You first need to open a text editor. In the Mate desktop, it's the "Pluma" editor. But any simple text editor will do.
 
 Once opened, paste the following code into it:
 
 [B]#!/bin/bash
 sudo modprobe usblp
 ls -l /dev/usb/lp0
 sudo -S lpadmin -x LBP2900-2
 sudo /etc/init.d/ccpd restart
 sudo /etc/init.d/cups restart[/B]
 
 This code is is essentially re-establishing a connection to the printer and restarting the "cups" printer software.
 
 Once you have pasted the code, save the file to your home folder as “reset-printer.sh”
 
 Then open up a terminal and type:
 
 **ls**
 
 You should see the file “reset-printer.sh” in the list of files and directories.
 
 Now type the following (followed by the "enter" key) to make the file executable:
 
 **sudo chmod +x reset-printer.sh**
 
 This script will be need to be used each time you start Ubuntu Mate to make your printer work.
 
 To do this, close the terminal and then navigate your way to your home folder. You will again see the “reset-printer.sh” file.
 
 Double-click the file. A dialogue box will appear asking how you want to run it.  
 
 Choose to “run in terminal”
 
 The terminal will appear and again prompt you for your sudo password (this is the same password you use to log into Ubuntu Mate) Type your password in and press the "Enter" key.
 
 At this point, your printer should now be working.
 
 You can test this by opening your word processor and typing something into it and then printing the document. At the print dialogue box, you may or may not see a second printer. I'm not sure why it is sometimes there and sometime not. But no matter, it is not set as the default and doesn't seem to affect anything. The one you are using is set to default and so you don't need to change anything. Just press the print button and it should work.
 
 I should note, very occasionally, the printer will still not play ball. If that happens, switch your printer off, wait a few seconds and switch back on again. Then run your script and you should find the printer works. If it still doesn't work, fully reboot your machine. When you log back in, re-run the script. At which point the printer will work. The above problem does not happen very often. But, I thought you should know it may do so occasionally and so let you know what you need to do in the eventuality.
 
 Notwithstanding the above qualifications, all other things being equal, the first thing you will need to do after you have logged onto Ubuntu Mate is to go to your home folder and double-click the “reset-printer.sh” file and then choose to run it in a terminal, type in your password, hit the enter key and you printer will be good to go for the rest of your session.

---

### Post by stevecook on 2014-11-11
_**Part 2**_

   This second part deals with automating the re-setting of the printer every time you re-boot your computer into Ubuntu Mate (incidentally, I think switching your printer off and on during a session will require a re-set as well. In which case you would need to re-employ the manual method described in section 1 of this tutorial using the “printer-reset.sh” file)

 There is a problem with running a script at start-up that includes the sudo command, Ordinarily, such commands require a user to enter their password. However, since we want this script to run at start-up, we won't have the opportunity to enter a password and so we need to employ a method whereby it is not required.  

 The following steps show how to first disable the sudo password prompt at a system wide level and then how to get the printer to re-set automatically at boot-up.

 Be warned, though. Disabling your sudo password in the following way requires that you edit a very important file called the “sudoer” file and if you screw up while you are editing it, you can knacker your entire system and you will have to re-write it. I know this because I have done precisely that myself on a previous occasion. Also, disabling the sudo password will be viewed by some as an unacceptable compromise of  system security. For me, as I stated earlier, this is not a problem. But, it's a matter of risk tolerance and you must make your own decision. In any event, you still need your password to log in to Ubuntu Mate.
 
 Firstly, you need to re-open your "reset-printer.sh" file and repeat the set of commands in there so that they run twice and also prefix them with a sleep command of 30 seconds. The reason for this has only been worked out by by me by trial and error. That is to say, I have found when I put the commands in only the once without a prefixed sleep command, half of the time the script does not work and half of the time it does. When I put the commands in twice alongside the sleep command, however, it seems to work every time. No other method of running the script at login has worked for me and, believe, me, I have tried them. What all of this suggests to me is that Mate can be a bit flakey in executing scripts at login and may skip some of the lines of code; thus rendering the script inoperable. By repeating the lines of code, this seems to give Mate the chance to pick it up on the second run if it didn't get it on the first. That's my hypothesis anyway. Irrespective, it does no harm and works. You new contents of your "printer-reset.sh" file should now look like this:
 
 [B]#!/bin/bash
 
 sleep 30
 
 sudo modprobe usblp
 ls -l /dev/usb/lp0
 sudo -S lpadmin -x LBP2900-2
 sudo /etc/init.d/ccpd restart
 sudo /etc/init.d/cups restart
 
 sudo modprobe usblp
 ls -l /dev/usb/lp0
 sudo -S lpadmin -x LBP2900-2
 sudo /etc/init.d/ccpd restart
 sudo /etc/init.d/cups restart[/B]
 
 Save and close the "reset-printer.sh" file.
 
 Open up a terminal. Type:
 
 **sudo visudo**
 
 and press the “Enter” key. After typing in your password at the prompt, press “Enter”. You will be taken into something called the “sudoer” file. Hold the down arrow key and you will see the cursor move to the bottom of the file. Paste the following line below all other lines (in order to paste using only the keyboard in a terminal, you need to press the CTRL/SHIFT/V keys simultaneously):
 
 **yourusername ALL=NOPASSWD: ALL**
 
 where “yourusername” should be replaced with your actual user-name (mine, for example, is “stephen”).
 
 You now need to save and close the file. To do this you need to:
 
 a) press CTRL and X
 b) You will be prompted to type Y or N in order to save or discard the modifications. You must type Type Y
 c) You will be given another prompt for the name that is given. Simply press the “Enter” key.
 
 You should now find you have dropped out of the sudoer file and are back at the normal terminal prompt. That's it, you can close the terminal at that point  
 
 Using your menu, go to  system/preferences/startup-applications. Click on the “Add” button. For the Command, press the "browse" button and navigate to your “printer-reset.sh” file and choose it. For the Description, simply write "reset the printer" (or whatever you want) in the box. Close the “add” dialogue box. You should now see this file listed as one of your start-up applications in the start-up-applications dialogue box. Close the start-up-applications dialogue box.
 
 That's it. From now on, every time you login to Ubuntu Mate, this file will will run automatically, you will not be prompted for your password in a terminal and your printer will be ready to use immediately.

---


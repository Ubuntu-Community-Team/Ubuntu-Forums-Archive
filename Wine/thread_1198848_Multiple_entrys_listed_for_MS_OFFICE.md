---
title: "Multiple entrys listed for MS OFFICE?"
date: 2009-06-28
forum: Wine
---

### Post by sandman3838 on 2009-06-28
Hello

I have been having an issue with Ms Office that I just installed.
If I select a DOC file and select OPEN WITH OTHER APPLICATION I have what is listed in the first screen shot &#8221; Ubuntu_Open Other App&#8221;.  There is multiple entries for all the Ms Office stuff. None of the MS Office items can be removed. 

Now if I go to the WINE menu and select &#8220;UNINSTALL WINE SOFTWARE&#8221; I get what is listed in the second screen shot &#8220;Wine Add-Remove&#8221;.  Again here, most of the entries can not be removed. 

Has anyone else see this?  This isn't normal is it? I know that they are both related!

On the plus side both OpenOffice and Ms office will open and I am trying to use OpenOffice more but there are some files that I really like to use with Ms Office.  But I just hate having all that loose file residue sitting out there.  To open a DOC file I either double click on the file or Right Click and select Open with &#8220;OpenOffice-PROGRAM&#8221; (Calc/Word) I can't select Ms Office Word or Excel.  For Ms Office I have to open Word and Excel first and select OPEN from the program.  Just not as handy.


**  Now the steps I did is as follows:

Uninstall Previous Versions Of Wine

For some odd reason, Office 2007 will not run on a version of Wine above 1.1.14. For that reason, if you currently have Wine installed, uninstall it by follow these steps:

   1. Open the terminal.
   2. Enter the following:

      sudo apt-get remove wine

   3. Remove the hidden Wine folder by entering the following into the terminal:

      rm -rf ~./wine



Install Wine

I&#8217;ll be using Wine 1.1.14 as I know it works.

   1. Open Firefox and navigate to the The WineHQ .deb Packages Archives and download Wine 1.1.14 for your system architecture.
   2. Install the .deb
   3. You will see a dialog box that reads: &#8220;An older version is available in the software channel.&#8221;
   4. Click the &#8220;Close&#8221; button.
   5. Click the &#8220;Install Package&#8221; button.
   6. Enter your password to install Wine.

Install Microsoft Office 2007

Now the fun part!

   1. Insert your Microsoft Office 2007 install disc into your computer&#8217;s CD-ROM drive.
   2. Look for the setup.exe executable.
   3. Right-click the installer and click &#8220;Open with other application&#8221;
   4. Choose Wine Windows Program Loader.
   5. Enter your serial number.
   6. Accept the User Agreement.
   7. Click the large &#8220;Install Now&#8221; button

If you click the Customize button, you can chose which components you want to install. You can also enter your name, initials and company name. This information will be embedded into every document that you create, just like in the PC version.

Install Winetricks

   1. Switch back to the terminal and enter the following:

      sudo wget [www.kegel.com/wine/winetricks](www.kegel.com/wine/winetricks)

   2. Once complete, enter this command:

      sudo apt-get install cabextract

   3. Enter the following:

      sh winetricks corefonts tahoma vcrun2005sp1 wsh56js

   4. Agree the Visual C++ license agreement.

   5. Click the &#8220;Yes&#8221; button to install Windows Script 5.6

Configure Wine

   1. Enter the following into the terminal:

      winecfg

   2. Switch to the Libraries tab
   3.  In the New override for libraries combo box, enter: riched20 and click the &#8220;Add&#8221; button
   4.  With riched20 highlighted, click the &#8220;Edit&#8221; button.
   5. Select the &#8220;Native (Windows)&#8221; radio button and click the &#8220;OK&#8221; button.
   6.  Enter usp10 into the New override for libraries combo box.
   7. Click the &#8220;OK&#8221; button to close the Wine configuration dialog box.

Test Microsoft Office 2007

All of the Microsoft Office applications should now have appeared in your application menu: Applications->Wine->Programs->Microsoft Office

---

### Post by jhoeijao on 2009-06-28
> **sandman3838 said:**
> Hello

I have been having an issue with Ms Office that I just installed.
If I select a DOC file and select OPEN WITH OTHER APPLICATION I have what is listed in the first screen shot &#8221; Ubuntu_Open Other App&#8221;.  There is multiple entries for all the Ms Office stuff. None of the MS Office items can be removed. 

Now if I go to the WINE menu and select &#8220;UNINSTALL WINE SOFTWARE&#8221; I get what is listed in the second screen shot &#8220;Wine Add-Remove&#8221;.  Again here, most of the entries can not be removed. 

Has anyone else see this?  This isn't normal is it? I know that they are both related!

On the plus side both OpenOffice and Ms office will open and I am trying to use OpenOffice more but there are some files that I really like to use with Ms Office.  But I just hate having all that loose file residue sitting out there.  To open a DOC file I either double click on the file or Right Click and select Open with &#8220;OpenOffice-PROGRAM&#8221; (Calc/Word) I can't select Ms Office Word or Excel.  For Ms Office I have to open Word and Excel first and select OPEN from the program.  Just not as handy.


**  Now the steps I did is as follows:

Uninstall Previous Versions Of Wine

For some odd reason, Office 2007 will not run on a version of Wine above 1.1.14. For that reason, if you currently have Wine installed, uninstall it by follow these steps:

   1. Open the terminal.
   2. Enter the following:

      sudo apt-get remove wine

   3. Remove the hidden Wine folder by entering the following into the terminal:

      rm -rf ~./wine



Install Wine

I&#8217;ll be using Wine 1.1.14 as I know it works.

   1. Open Firefox and navigate to the The WineHQ .deb Packages Archives and download Wine 1.1.14 for your system architecture.
   2. Install the .deb
   3. You will see a dialog box that reads: &#8220;An older version is available in the software channel.&#8221;
   4. Click the &#8220;Close&#8221; button.
   5. Click the &#8220;Install Package&#8221; button.
   6. Enter your password to install Wine.

Install Microsoft Office 2007

Now the fun part!

   1. Insert your Microsoft Office 2007 install disc into your computer&#8217;s CD-ROM drive.
   2. Look for the setup.exe executable.
   3. Right-click the installer and click &#8220;Open with other application&#8221;
   4. Choose Wine Windows Program Loader.
   5. Enter your serial number.
   6. Accept the User Agreement.
   7. Click the large &#8220;Install Now&#8221; button

If you click the Customize button, you can chose which components you want to install. You can also enter your name, initials and company name. This information will be embedded into every document that you create, just like in the PC version.

Install Winetricks

   1. Switch back to the terminal and enter the following:

      sudo wget [www.kegel.com/wine/winetricks]("http://www.kegel.com/wine/winetricks")

   2. Once complete, enter this command:

      sudo apt-get install cabextract

   3. Enter the following:

      sh winetricks corefonts tahoma vcrun2005sp1 wsh56js

   4. Agree the Visual C++ license agreement.

   5. Click the &#8220;Yes&#8221; button to install Windows Script 5.6

Configure Wine

   1. Enter the following into the terminal:

      winecfg

   2. Switch to the Libraries tab
   3.  In the New override for libraries combo box, enter: riched20 and click the &#8220;Add&#8221; button
   4.  With riched20 highlighted, click the &#8220;Edit&#8221; button.
   5. Select the &#8220;Native (Windows)&#8221; radio button and click the &#8220;OK&#8221; button.
   6.  Enter usp10 into the New override for libraries combo box.
   7. Click the &#8220;OK&#8221; button to close the Wine configuration dialog box.

Test Microsoft Office 2007

All of the Microsoft Office applications should now have appeared in your application menu: Applications->Wine->Programs->Microsoft Office

I think you are referring to this guide [http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/) similar to my guide here [http://ubuntuforums.org/showthread.php?t=1173365]("http://ubuntuforums.org/showthread.php?t=1173365&page=8") and I think I'm the first visitor who commented on that guide and I'm sure you are using wine 1.1.24 that causes multiple entries for Microsoft Office 2007.

Solution: You can downgrade your wine from 1.1.24 to 1.1.12 to 1.1.16 by uninstalling your wine using synaptic package manager or using your terminal and type ```
sudo apt-get remove wine
``` then delete your wine folder by typing ```
rm -rf ~/.wine
``` then download your desired wine version 1.1.12 to 1.1.16 here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) double click the file and install then follow your desired guide.

Note: Deleting wine folder means deleting all the programs installed using wine

---


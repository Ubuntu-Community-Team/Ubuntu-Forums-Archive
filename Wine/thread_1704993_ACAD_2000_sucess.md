---
title: "ACAD 2000 sucess"
date: 2011-03-11
forum: Wine
---

### Post by mark bower on 2011-03-11
ACAD 2000 under Wine 1.3 (1.3.15)
System:  32bit Celeron, Ubu 10.10, Linksys WRT 54G router, Laserjet4 printer, D-Link DP-301P print server on printer.  I am thrilled to have ACAD 2000 working and printing under WINE.  Following applicable steps, I also installed ACAD 2000 on a computer with 1.2 installed.

The following is combined from three posts and my own method.  Wine Doors is posted as being broken, but the script at the following link looks like a good alternative to my copying files in Step 10: 

[http://alxarch.wordpress.com/2008/04/20/autocad-2000-in-wine-howto/](http://alxarch.wordpress.com/2008/04/20/autocad-2000-in-wine-howto/)
also see winehq.org 

1.  Install printer/plotter in Ubuntu if you have not already done so.

2.  Download and install the following for latest WINE revision
	[I][B]sudo add-apt-repository ppa:ubuntu-wine/ppa
	sudo apt-get update
	sudo apt-get install wine1.3[/B]
[/I]
3.  Apps Menu>Other>Configure Wine, change Screen Resolution from 96 to 108dpi, then Apply>O.K.

4.  Apps Menu>Other>Winetricks, install the following 4 files either via Apps>WINE>Winetricks or at the cmd line:
	**sh winetricks corefonts mdac25 tahoma win98**

5.  In terminal at your home directory ~/, make a directory for ACAD 
	**mkdir acad**	

6.  In Nautilus, copy files from ACAD 2000 CD to the ~$ acad directory.

7.  Download the following service packs and update files from Autodesk (usa.autodesk.com, put file name into search).  With Nautilus copy the files to ~/acad directory.  
	acad2000spul.exe
	acad2000sp2ul.exe
	3dupdate.exe
	plotupdate.exe (used to update _setup.lib)

8.  Copy the above files to the ~/acad directory made per step 5.

9.  In the terminal, change directory to ~/acad and run the following two lines to install ACAD 2000 and updated plot drivers:
	**wine setup.exe** (select Typical installation)
	[B]wine plotupdate.exe
[/B]
10.  Step 9, ACAD 2000 install, makes a directory Autodesk Shared at .wine/drive_c/Program Files/Common Files/Autodesk Shared and places all the .dlls in that directory.  Using Nautilus, navigate to Autodesk Shared and copy all of the files in that directory to .wine/drive_c/windows/system32.

11.  Boot ACAD 2000

Notes for steps:

2.  Respond to pop-up "TrueType core fonts for the Web" EULA and accept if you can, else, close the window.  Wine installs at ~/.wine as a hidden directory and appears first as Apps>Other>Configure Wine.  Winetricks should show in Apps>Other>Winetricks.  Wine can also be installed with Syn Pkg Mgr, Wine 1.2 came with my Ubuntu 10.10.  If winetricks does not automatically install it can be installed from cmd line:
	wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)  or
	wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
If winetricks does not show in the Apps pull down menu, then use the cmd line as shown in step 4.

4.  WINE win98 emulation selected since ACAD installer baulks at winXP selection.

9.  You will get two VBA failed pop-ups during the ACAD installation; disregard and accept with the O.K. button.  If installing the service packs, make sure they are installed in order.  I only installed plotupdate.exe.  In my first attempt, I couldn't print until I installed plotupdate.exe;  in a second trial, printing worked prior to installing the update.  Plotupdate.exe updates the DRV and HELP folders in .wine/drive_c/Program Files/ACAD2000/.  The installation also creates a folder at .wine/drive_c/Program Files/Common Files/Autodesk Shared

10.  Not sure which dlls are critical to functioning, so copied them all

11.  I am not a sophisticated user.  I tested using only primitives in 2D, some modifications, eg "stretch", and a little text play; all worked just fine as well as printing via wireless network.

mark bower

---


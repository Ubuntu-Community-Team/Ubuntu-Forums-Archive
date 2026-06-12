---
title: "HP Web Jet Admin replacement for Linux"
date: 2007-12-19
forum: The Cafe
---

### Post by DouglasAWh on 2007-12-19
HP Web Jet Admin uses MS SQL Server, which not only do I not like, but it doesn't work on Linux, and it is SLOW on my work laptop.  Does anybody have a utility that will do what HP Web Jet Admin will do that has better performance for XP and/or as Linux functionality at all?  I think I tried HPWJA in WINE, but I can't remember exactly off the top of my head.  If I did....it didn't work!

Thanks!

---

### Post by BlackNinjaVirus on 2007-12-19
[http://localhost:631](http://localhost:631)

---

### Post by DouglasAWh on 2007-12-19
So an internal webpage goes and finds all the printers on your network?  I'm not on a Linux box at the moment, but when I've used CUPS before, it's been to install printers.  I don't need to install printers or drivers or anything like that, just administer them remotely.  We have a mixed printer environment with Xerox, HP and Dell (actually Xerox and Lexmark, I think), and HP Web Jet Admin handles all of them.

---

### Post by BlackNinjaVirus on 2007-12-19
Getting Started with CUPS
CUPS (the Common UNIX Printing System) is similar in many ways to the traditional System V LP subsystem. Many of the same commands (such as lp, lpadmin, cancel and so forth) are supported by both interfaces, though some may have a slightly different syntax.

Read this topic thoroughly to help you decide whether to move to CUPS from System V LP, and then to get started once you switch to CUPS. The CUPS documentation is available in the DocView Printing category.
Enabling CUPS

There are two options for enabling and administering CUPS:

    * if you want the default system printer to be a CUPS-managed printer, edit /etc/default/lpd and change the PRINT_SYSTEM value from ``SYSV'' to ``CUPS''.

      When you make this change, the SCOadmin Printer Manager is reconfigured to automatically launch the CUPS web-based administration tool.

    * if you want to use both CUPS and System V printing (lp):

          o use the SCOadmin Printer Manager to administer lp, as described in this topic.

          o use the CUPS web-based administration tool. To run this tool directly, launch a browser and specify the following URL:

            [http://localhost:631](http://localhost:631)

When you log into the CUPS administration tool, it assumes that you are the root user -- enter the root password.

Details on using the CUPS web-based administration tool are provided in the CUPS documentation. See the DocView Printing category.
Setting Up a Printer in CUPS

Setting up a printer correctly in CUPS depends on two critical choices: the printer device name and the printer driver. Most tasks can be performed using the CUPS graphical interface, but some will require the lpadmin(ADM) command.

Devices are selected from a drop-down list in the graphical interface that shows the make and model of the printer. The procedure below shows you how to use the lpadmin command to reset the device name as necessary.

CUPS provides its own generic printer drivers, that provide basic printing functionality. The following packages provide additional printer support, and should be installed along with CUPS:

    * The foomatic package provides dozens of PPD files for many printer makes and models.

    * The ESP Ghostscript package (gs) provides printer drivers.

    * The hpijs package includes the hpijs driver and PPD files driver for more than 200 Hewlett-Packard printer models, including DeskJet, OfficeJet, Photosmart, Business Inkjet and some LaserJet models. It also supports some non-HP printers.

    * The gimpprint package provides PPD files and the ijsgimpprint driver, which supports many Canon and Epson printers, as well as some Lexmark and Hewlett-Packard models. 

Your printer may work with more than one driver, but will probably work best with one of the available choices.

To set up a printer using the CUPS graphical administration interface:

   1. Start any browser and open [http://localhost:631](http://localhost:631).

   2. Select Administration from the menu at the top of the page. Enter the root login and password, and select OK.

   3. Select Add Printer from the Admin menu.

   4. Enter the printer name, and optional location and description. Select Continue.

   5. Choose the printer device from the drop-down box. The following is an example of the choices presented:

         AppSocket/HP JetDirect
         Internet Printing Protocol (ipp)
         Internet Printing Protocol (http)
         LPD/LPR Host or Printer
         Parallel Port #1
         Serial Port #1
         Serial Port #2
         USB Printer #1 (Printer Make/Model)

      Note that if no USB Printer is displayed, but you have one connected, you may need to restart the CUPS server in order for CUPS to recognize it. Make sure the printer is connected properly and is turned on. Then, open a console window and enter the following command (as root):

         /etc/init.d/cups restart

      Select the browser's Reload or Refresh menu command; the USB Printer should now be listed in the device choices.

      Choose the apporpriate device and select Continue.

   6. Select the printer manufacturer from the list displayed, or Generic.

   7. Choose the printer model from the list displayed, and select Continue. If the model of your printer is not listed, check the printer documentation to determine the nearest compatible model listed. Or, make no selection to go back to the previous list and try another manufacturer.

   8. The following message should be displayed:

         Printer printername has been added successfully.

      Select the printer name to go to the printer description.

   9. Check the printer details displayed. If something is incorrect, select the Modify Printer button to change the printer definition or driver. If the device URI is not correct, open a console window and type the following command (as root) to set the device URI appropriately:

         lpadmin -p printername -v deviceURI

      The deviceURI contains the type of interface and the device path. For example, for a parallel port printer, the device URI might be parallel:/dev/lp0. For a USB printer, it is recommended you use a device URI of usb:/dev/usb_prnt#. See usblp(HW) for USB device naming conventions.

      Once you have changed the printer definition as needed, select the browser Reload or Refresh menu command to check your changes.

  10. Test the printer:

         1. Select the Print Test Page menu command from the CUPS printer description page.

         2. Open a console window, and enter the following:

               man lpadmin | lp -d printername

            The above command should print the lpadmin(ADM) manual page on printer printername. 

      If the test page does not print, prints poorly, or printer performance is not optimal, select the Modify Printer menu command on the printer's description page to try another printer manufacturer or model. 

Printing from CUPS to a Windows Printer

This example configures an HP officejet v40 (USB) connected to a Windows XPPro (as printer queue HP) for printing from a system running CUPS.

   1. From Windows, select Start -> Settings -> Printers -> .

   2. Open the printer Properties box, and make sure that the printer is Shared. Select OK to close the Properties window.

   3. Select Start -> Control Panel -> Add or Remove Programs -> Add/Remove Windows Components -> .

   4. Enable the check box next to Other Network File and Print Services.

   5. Select Details. Make sure Print Services for UNIX is selected. Select OK and then Next.

   6. If the system needs to load Print Services for UNIX from the Windows CD, it will ask for the CD. Insert the Windows Installation CD into the CD drive and click OK. (Cancel the Installation Wizard if it appears.) Click Finish once the driver is loaded.

   7. Close the Add or Remove Programs window.

   8. Open Administrative Tools.

   9. Open Services.

  10. Look for "TCP/IP Print Services" in list. Select the entry to open the Properties window. Enable Automatic startup, and start now.

  11. Use the CUPS administrative interface on [http://localhost:631](http://localhost:631) to define "hp" as an lpd printer, using the raw interface.

  12. To print a text file to printer HP on Windows, enter a command like the following:

         lp -d hp textfile

      where textfile is the name of the text file. 

© 2005 The SCO Group, Inc. All rights reserved.
SCO OpenServer Release 6.0.0 -- 03 June 2005

---

### Post by Steveway on 2007-12-19
> **DouglasAWh said:**
> So an internal webpage goes and finds all the printers on your network?  I'm not on a Linux box at the moment, but when I've used CUPS before, it's been to install printers.  I don't need to install printers or drivers or anything like that, just administer them remotely.  We have a mixed printer environment with Xerox, HP and Dell (actually Xerox and Lexmark, I think), and HP Web Jet Admin handles all of them.

You should definitly try out what BNV posted.
I didn't now that before but it seems to pick up the printers and you can administer them.
That is a really nice feature, definitly a thumb up.

---

### Post by DouglasAWh on 2007-12-20
I still don't see how to give it an IP range and have it find all the printers in that IP range.  I do have an ubuntu box up and running at work again now, and I'm looking at CUPS.  As to the reason I didn't have a box yesterday...I killed X trying to use the new GUI for dual monitors...it's like the 4th time I've tried, thinking maybe there was an update...but nope.  The graphics card has just got to be incompatible...but that's another issue.

---


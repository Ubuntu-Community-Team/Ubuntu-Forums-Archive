---
title: "HOWTO: Install Lexmark Z55 printer"
date: 2008-05-22
forum: Tutorials
---

### Post by nick_h on 2008-05-22
This tutorial describes how to install a Lexmark Z55 printer on Hardy Heron.

By default the wrong driver is installed for the Z55 which causes the printer to squeal and fail to print.  A driver is available from the Lexmark website for Linux rpm distributions.

Most of the information for this howto came from the excellent thread - [HOWTO: Lexmark Printers](http://ubuntuforums.org/showthread.php?t=49714).

**[SIZE="4"]1. Download[/SIZE]**

Download the file CJLZ55LE-CUPS-1.0-1.TAR.GZ from the Drivers and Downloads section of the Lexmark website.  Select a Linux distribution such as Mandrake.

**[SIZE="4"]2. Uninstall the existing driver[/SIZE]**

System->Administration->Printing
Expand "Local Printers"
Click on "Lexmark_Z55" to select it
Press the "Delete" button and confirm with OK

**[SIZE="4"]3. Create directory[/SIZE]**

Create a directory to work in and move the downloaded file into this new directory.
```
mkdir lexmark
mv CJLZ55LE-CUPS-1.0-1.TAR.GZ lexmark
```

**[SIZE="4"]4. Extract rpm files from the download[/SIZE]**

```
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tgz
tar -xvzf install.tgz
```

**[SIZE="4"]5. Convert rpm files into deb packages[/SIZE]**

First install the alien package if you have not already done so.
```
sudo apt-get install alien
```
Now convert the files ignoring any warnings.
```
sudo alien lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien z55llpddk-2.0-2.i386.rpm
```
Save the deb files in a safe place.  For subsequent installations you can use these files.

**[SIZE="4"]6. Install the packages[/SIZE]**

The deb files can now be installed using any method you prefer.  To install from the command line type:
```
sudo dpkg -i z55llpddk_2.0-3_i386.deb
sudo dpkg -i lexmarkz55-cups_1.0-2_i386.deb
```

**[SIZE="4"]7. Unzip ppd file[/SIZE]**

```
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
```

**[SIZE="4"]8. Install the new driver[/SIZE]**

System->Administration->Printing
Press the "New Printer" button
Select "Lexmark Z55 USB #1"
Press "Forward"
Select "Provide PPD file"
Click on the file icon on the right hand side of the box below
Using the file picker select /usr/share/cups/model/Lexmark-Z55-lxz55cj-cups.ppd
Press "Forward"
Press "Apply"

---

### Post by hoisanjai on 2008-12-24
Well, the tutorial covers everything but everytime I type mv "the driver's name" it say it's not found. I need help, I am totally new to this linux thing I followed everything that was typed in the terminal but it keeps saying things cant be found. using 8.10

---

### Post by KMcCMedia on 2011-01-21
OK I had this working way back in Ubuntu 9, but it broke and I couldn't get it back when I upgraded to 10. I finally have it working in Ubuntu 11.04 - the Natty Narwhal.

Here's what I had to do:

- Follow the instructions through step 3.

- Right after putting "CJLZ55LE-CUPS-1.0-1.TAR.GZ" into the "lexmark" directory you just made, open the directory with your GUI browser, double click the file and extract the "CJLZ55LE-CUPS-1.0-1.TAR" file into the directory by dragging it. Next double click the "CJLZ55LE-CUPS-1.0-1.TAR" and extract the "lexmarkz55-CUPS-1.0-1.gz.sh" into the directory.

-Now when you continue with step 4 "Extract rpm files from the download", it will work.

Everything else goes pretty much like clockwork, except when you get to the installing printers part and choose new printer, the "provide PPD" part comes up before you can choose a printer. Don't attempt to look for the Lexmark Driver in the list, just paste the location of the file from the directions. It's OK! After you have provided the PPD, it will know what printer you are installing. 

In my case I am on a home wi-fi network with a windoze XP computer, which is sharing the printer, and I had no problem printing a test page, once the driver was loaded. Yay!

---

### Post by ub-khalid on 2011-08-08
Hello

Is this tip also applyable in the version 11.04 of Ubuntu?

---

### Post by roddehugo on 2011-10-05
I'd like to know if this tip is still applyable in ubuntu 11.04 ? Plus, when I try to print the test page it tells me : inactive - /usr/lib/cups/filter/rastorz55 failed.. What could I do ?

---

### Post by cesium62 on 2011-10-28
For the /usr/lib/cups/filter/rastorz55 error:

  cd /usr/lib/cups
  ls -altr

Verify that directories are searchable (they have the 'x' flag in three places), the files are executable, and the directories and files are owned by root.  For me, I somehow had ownership of some of the directories and files, but most were owned by 'root'.  To fix, I used:

  cd /usr/lib/cups
  sudo chown -R root:root .

This will change the owner and group to root for everything in the cups directory and below.

---


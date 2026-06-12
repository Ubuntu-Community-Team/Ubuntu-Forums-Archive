---
title: "HOW TO ... Brother MFC-J410W Printer ... U/Xubuntu 11.04 - 12.04"
date: 2012-04-18
forum: Tutorials
---

### Post by WinRiddance on 2012-04-18
More than likely any problems you've had with this printer have to do with the pre-checks on the Brother website since those are located in at least 3 different places. You'd think that doing the pre-checks for Ubuntu/Debian 64bit would cover everything ??? Not so because the Brother site, at least some parts of it, are not set up in a common sense manner (IMO) with all requirements in one neat little area. This tutorial will get your **MFC-J410W** printer working **with USB, step by step,** on your Xubuntu/Ubuntu 11.04 and 11.10 and 12.04 machine. This should probably work for Kubuntu too.
Network printing help is at the bottom !!!

First go to the Brother driver download page and **download both** the cupswrapper driver as well as the lpr driver deb files. Here's the link to the drivers, make sure you select the correct printer. It's easy to accidentally click the wrong link on that page.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

**Don't connect the printer yet,** but have it ready to be connected. Before you do anything else, note that [COLOR=DarkRed]**ia32-libs**[/COLOR] or [COLOR=DarkRed]**lib32stdc++**[/COLOR] is required to be installed. Open up the synaptic package manager, it should ask you for your user/login password. Search for ia32-libs and mark it for installation (over 200 MB of total data on my machine).

**Not familiar with Synaptic Package Manager ???** Search for an item in the searchbox at the top of the open Synaptic Package Manager window. When found, click on the item to select it, _then right click that item_ to mark it for installation. Click on APPLY at the bottom of the Synaptic window and that item will be installed.
[COLOR=DarkRed]**ia32-libs is what I installed**[/COLOR] since I noticed some dependency issues on my system when I checked the other (lib32stdc++) file first.

Now then, it's probably already installed, but just to be safe make sure that you have [COLOR=DarkRed]**sane-utils**[/COLOR] installed as well. Use synaptic to look for that too. When finished, go ahead and close the synaptic package manager. Awesome, now let's access that dreaded (kidding) terminal. Don't worry, this will be copy 'n' paste with a little bit of common sense. Once the terminal is open, issue this command (it's also part of the precheck requirements, your login PWD may be required):

```
sudo mkdir /var/spool/lpd
```Okay, at this point we need to gain access to the folder with the previously downloaded files. Assuming this to be the default "Downloads" folder in your home directory, enter this command in your open terminal (adjust as needed):

```
cd /home/yourusername/Downloads
```**Don't do anything else.** Go ahead and connect your printer to the USB port now before entering the following command in the terminal:

```
sudo dpkg -i --force-all mfcj410wlpr-1.1.3-1.i386.deb
```That was the installation of the LPR driver as required. Now let's install the cupswrapper driver with this command (the command takes awhile to complete):

```
sudo dpkg -i --force-all mfcj410wcupswrapper-1.1.3-1.i386.deb
```When you see this as the last line in the terminal again, the command has completed:
[COLOR=DarkRed]**yourusername@yourusername-more:/home/yourusername/Downloads$**[/COLOR]

At this point you **may** (depends on which *buntu version & type) have already received a status message on your screen, something like ... printer installed ...
**For network printer installatio**n ... you need your printer's IP, then follow instructions at the bottom of this link/page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

**If you're not** doing the network printer installation, let's check your USB connected printer now ....
Go to your main application menu (system) and open up the printing application, your printer should already be listed there. Now RIGHT CLICK on the printer model icon (should be MFC-J410W) and make sure that _ENABLED_ & _SHARED_ are checked. Also make sure that you check the line for _SET AS DEFAULT_

**Almost done** ... Right click the printer icon again and then select _PROPERTIES_ to open the printer functions. Under ... Tests & Maintenance ... click the print test page button. It should print. If so, you're finished. Yey, big clap on the back !!!

[COLOR=Navy]**In hindsight, some things to keep in mind ....**[/COLOR] The Linux kernel changed significantly within the past 6 months, Brother updated these drivers from another version in the past 6 months, and huge changes are taking place with the new 12.04 LTS (Long Term Support) upgrade of Ubuntu/Xubuntu. Any of those may be contributing factors that could explain why your MFC-J410W printer stopped working even though you had it working already earlier. If this tutorial worked for you, be sure to get rid of any downloaded files or instructions for this printer that are not current. It's one of the problems that I ran into ... using the newer drivers with my older instructions. To my knowledge this tutorial for this MFC-J410W is the most current & detailed tutorial.
Good luuck, and enjoy printing (again) ... :guitar:

[COLOR=DarkRed]**Update ... Very Important ... Read this too!**[/COLOR] If your version of Xubuntu is [COLOR=Black]**11.10**[/COLOR] and you finally got this printer working, _do not under any circumstances_ allow for any more updates from the update manager until you're ready to actually upgrade to another Xubuntu version such as 12.04 ... because my printer worked just fine until I let the Update Manager do its thing day before yesterday ... and now my printer is no longer working. Tried fresh install from scratch, no luck. Double, triple, and quadruple checked dependencies as well as re-installing the required ones, still no luck. Tried trouble shooting & network printing, still no luck. The rinter simply won't work at all anymore since the updates were installed. This problem should only exist with **Xubuntu 11.10**

.

---

### Post by WinRiddance on 2012-04-28
[COLOR=DarkRed]**Still having problems with this printer?**[/COLOR]
The following worked for me on another Ubuntu/Xubuntu computer:

Assuming that you've followed the steps from the initial thread, use the printer options in your system management to delete this printer. Now go ahead and reboot the printer. Don't do anything else printer related after logging back in. _Keep it connected and the cables in place_ though.

**Next use your file manager** to locate the cupswrapper driver from the Brother website, it's the same .deb file that you downloaded previously, probably entitled something like ... mfcj410wcupswrapper-1.1.3-1.i386.deb

_In your file manager, right click on this file_ and then choose the option for extracting the contents of the file. This will create another folder with the .deb package contents. When you're finished, open up the new folder. You should see two sub-folders, one entitled DEBIAN (ignore that one) and the other one entitled **opt**. That's the one that we're interested in ...

Open up every folder in opt _until you get to the end_ where you'll see a few files. One of these is the .ppd file that this printer uses. It's name is brother_mfcj410w_printer_en.ppd and you should copy this file (right click on it) to the root folder that you used to get here in the first place. The root folder is the ones with the two sub-folders DEBIAN and opt. Now place a copy of the .ppd file into that root folder. **Almost done now** ...

Now get back into your system printer settings ... there should be no printer since you deleted that previously. Click the "+" symbol to add a printer, let it search for a driver even though it won't find one. Next select a printer from a database, but then _click the button for providing a ppd file_ to the printer. Locate the ppd file that you just copied into that root folder a minute ago, then double click on that file.

Follow the prompts to the end, your printer should then work. I tried this with reboots as well and it still worked. That the final test for you ... printing a test page, rebooting the machine, and then printing an actual file on your computer. Good luck.

.

---

### Post by mushyhsum on 2013-03-18
I already installed it. It was extremely helpful. Thank you so much. (:
I am so happy now, I could die.

Mushy

---


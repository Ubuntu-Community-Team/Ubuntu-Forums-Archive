---
title: "HOW TO: Install and conficure Canon MX340 (Ubuntu Lucid 64 bit)"
date: 2010-06-26
forum: Tutorials
---

### Post by Cypher2 on 2010-06-26
Hello everyone!

Thought I'd share my success in installing and configuring my new MX340 printer on Lucid 64 bit.

As we all know or heard of, Canon does support linux .deb and .rpm driver packages but only for the 32 bit platforms.

I hearby declare that any thread claiming that the 32 bit modules installed on a 64 bit machine do not work is most probably a mishap on behalf of the user who tried installing without any clue of what he/she was doing.

After this, you will have full wireless functionnality and scanning capabilities :)

So here we go:

1 - Open you printer box, unwrap and set it up wherever you desire as long as it's in range of your network router/hub or wireless router/modem. Plug the power cord in and light it up.

2 - Go to this link 

[http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux)

and download the MX340 Series Printer drivers and ScanGear MP debian packages. You will notice that they are provided as tar.gz archives - once loaded, extract them to a working directory of your choice.

You will notice that upon extraction, the folder hierarchy is as follows for both archives: 

'FOLDER NAME' > packages|resources|install.sh

We will be working within the "packages" folder as it is the one containing the deb archives.

3 - Back to the printer: it should now be ON, and ready to be configured.

On the printer's button and configuration panel, press the MENU key 3 times until it displays the DEVICE SETTINGS menu. From now on, use the left and right arrows under the LCD display to navigate through all sub-menus that will follow.

3A - Press the right arrow once to select sub-menu LAN SETTINGS, press OK.

WLAN active/inactive - Press OK, switch status to active with arrow keys, Press OK.

You will now automatically exit back to the following sub-menu: WIRELESS LAN SETUP, press OK.

You are now on EASY SETUP option, press OK.

Your MX340 will now begin scanning for WLAN access points. It should show the strongest signal first, which would normally correspond to you modem/router. If not, use the arrows to cycle through the access point name entries until you find the desired name, press OK, confirm selection by pressing OK again.

If your router/modem is encrypted with a password (which it normally should), the printer will ask for it - enter it via the number input panel on the right, press OK. The LCD should Display "CONNECTING..." as a status message and it should not take more than 5 seconds to do so. Press OK to confirm status "CONNECTED".

3B - You now exit to sub-menu PRINT LAN DETAILS, skip it with right arrow to sub-menu OTHER SETTINGS, press OK.

You will now be on sub-sub-menu entry SET PRINTER NAME, Press OK.
I have set mine to simply show MX340, you can do so with the number entry pad as described earlier for the password entry, Press OK.

You are now on IPv4/V6 sub-sub-menu, Press OK. Select IPv4 with arrow buttons, press OK and confirm the AUTO SETUP option and interruption message by pressing OK again. Keep IPsec setting inactive by pressing OK. The status message should show "SETTING..."

You are now on WSD SETTING sub-sub-menu, press right arrow button to skip to ENTER SERVICE NAME, press OK. You can modify the service name to be shorter by erasing the hardware adress that follows the whole string for the service name to simply become Canon MX340 (the hardware address and hexadecimal tag will still be visible under the printer settings option upon setup in Ubuntu. Press OK to confirm entry.

You are now on LPR SERV. Advertising sub-sub-menu, press OK to enter and switch to ON, press OK to confirm.

You can now go back to the main LCD status menu by pressing the BACK button until reaching it.

YOUR PRINTER IS NOW FULLY CONFIGURED TO BE DETECTED BY UBUNTU VIA THE PRINTER SETTINGS MANAGER.

4 - Now, go back to your machine and enter the "packages" folder for the CNIJFILTER archive you've extracted earlier. Open a terminal window in that folder via right click menu (if you have the scripts already downloaded and set up in Nautilus, or you can simply use the good old "cd" command as follows:

"cd 'FOLDER NAME'/packages"

You can verify that you are indeed in the desired folder by the pressing "ls" and reading out the contents of the folder via the terminal.

4A - Now that we are in the desired folder, you will enter this command as follows and provide your superuser password when prompted by the terminal:

"sudo dpkg -i --force-all *.deb"

Do not worry about any error message that the terminal would display as it mostly refers to the architecture of the package being i386 and not amd64 - the packages will still extract and install perfectly fine.

THE FILTER AND DRIVER MODULES FOR THE MX 340 ARE NOW INSTALLED.

4B - Repeat step 4A, but this time you will use the "packages folder contained with the SCANGEARMP folder you've previously extracted.

THE SCANGEARMP SCANNING MODULE/APPLICATION IS NOW INSTALLED. (You can find it within /usr/bin/ as scangearmp).

5 - Close all your open windows and head to the "Printing" menu from System > Administration.

Press the ADD button (marked with a green cross icon), the "New Printer" window should now appear.

Press on the "[+] Network Printer" sub-menu, then press "Find Nework Printer", press the "Find and wait for the manager to finish scanning.

You should now see two entries for the MX340, the first one being the default printer module hardware address with the hexadecimal hardware ID, and the second the LPD entry with the printer's IP adress using DNS as backend to access the printer.

Click on the second entry (DNS with IP adress version) and press the forward button. The "Searching for drivers" window should appear and then pass directly to the "Describe Printer" dialog. 

If it did go as described, it means that the drivers were indeed successfully integrated to Ubuntu and that the system picked them up and configured the printer to use them.

Name you printer as you wish for it to appear within your system's dialogs. Press the "Apply" button to finalize.

If you wish, you can print the Ubuntu test page to make sure it does receive jobs.

The icon for the printer must not show any error status exclamation emblem ( /!\ ).

To access your printer via other remote systems and be able to print, press "Server" in the main window menu bar and go to "Settings". Check all first three options and apply, The printer should show up on the network browser of other machines and their respective printing dialogs within 30 seconds to a minute delay.

YOUR MX340 IS NOW READY TO PRINT ANY DOCUMENT FROM ANY LOCATION WITHIN YOUR NETWORK.

6 - We will now add a launcher/menu entry to be able to scan with the MX340 as the SANE library does not seem to recognize the scanner hardware for this model as of yet.

On your desktop, right-click and select "Create Launcher..."

Fill labels as follows:
_____________________________________________________________
Name: ScanGear MP
Command: scangearmp
Comment: Canon MP/MX Series scanning utility
_____________________________________________________________

You can set the scanner.svg icon to be used by simply clicking on the springy launcher icon and browsing to /usr/share/icons/gnome/scalable/devices and selecting scanner.svg Press OK when done, a launcher should now appear on your desktop.

If you prefer having a normal menu entry for it, you can set it up by right-clicking on the Ubuntu Applications panel icon and selecting "Edit Menus", navigate to "Graphics". Press the "New Item" button and follow the steps  previously described to create a custom launcher.


ENJOY!

---

### Post by josephhitt on 2010-07-06
Thanks for posting this and pointing out those drivers.  Not sure why Canon keeps them huddled away on the Asian site only.

Unfortunately it didn't quite work for me.  One difference was that I had to enter the printer IP manually (no big deal, just not sure why it didn't find it from scanning the subnet).  Then, things went smooth up until I tried printing the test page, last line in the error log is:

D [06/Jul/2010:20:40:13 -0400] cupsdAuthorize: No authentication data provided.

---

### Post by Cypher2 on 2010-07-07
My pleasure :), I love the Ubuntu community too much to hide this sort of happening from all of you!

Hmmm.. weird,

CUPS doesn't have much to do in the configuration other than hosting the printer on linux and via samba subnet to share with other computers...

The biggest load of the config is done through the printer itself...

did you reverify the IP version on the printer... it has to stay on IPv4, I can't really think of anything else at the moment, maybe reloading cups manually after config?

---

### Post by AndyCinDallas on 2010-07-12
This was extremely helpful to me, thank you :D

My printer died yesterday so I went to Best Buy and got this printer on sale - hey, for $80 I'm not complaining!

I followed your instructions on an older laptop with a 32-bit version of Ubuntu - 9.04 - and just for some feedback and maybe to help anyone else, this is the sequence for installation (on my system) after installing the drivers:

[IMG]http://img704.imageshack.us/img704/6450/screenshot1qi.png[/IMG]

[IMG]http://img203.imageshack.us/img203/7138/screenshot2d.png[/IMG]

[IMG]http://img155.imageshack.us/img155/6161/screenshot3kn.png[/IMG]

[IMG]http://img175.imageshack.us/img175/6060/screenshot4u.png[/IMG]

I'll be installing it on my main desktop machine (dualboot XP with Ubuntu 10.04) shortly.

---

### Post by Cypher2 on 2010-07-13
Great! ^_^

Glad to know it works well on other versions and architectures...

---

### Post by Archival Liaisons on 2010-07-31
Hi Cypher2, great "How To" it worked for me:D, Thanks,

p.s. Drivers now available on the European Site.

[http://software.canon-europe.com/products/0010835.asp]("http://software.canon-europe.com/products/0010835.asp")

---

### Post by treesurf on 2010-08-01
Thank you very much, that worked wonderfully for me. :)

---

### Post by cectom on 2010-10-09
cecilia@cecilia-desktop:~$ cd ./Desktop/downloads/
cecilia@cecilia-desktop:~/Desktop/downloads$ tar -xvf ./cnijfilter-mx340series-3.30-1-i386-deb.tar.gz
cnijfilter-mx340series-3.30-1-i386-deb/
cnijfilter-mx340series-3.30-1-i386-deb/packages/
cnijfilter-mx340series-3.30-1-i386-deb/packages/cnijfilter-mx340series_3.30-1_i386.deb
cnijfilter-mx340series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
cnijfilter-mx340series-3.30-1-i386-deb/resources/
cnijfilter-mx340series-3.30-1-i386-deb/resources/printer_zh_utf8.lc
cnijfilter-mx340series-3.30-1-i386-deb/resources/printer_ja_utf8.lc
cnijfilter-mx340series-3.30-1-i386-deb/resources/printer_fr_utf8.lc
cnijfilter-mx340series-3.30-1-i386-deb/install.sh
cecilia@cecilia-desktop:~/Desktop/downloads$ ls
cnijfilter-mx340series-3.30-1-i386-deb
cnijfilter-mx340series-3.30-1-i386-deb.tar.gz
scangearmp-mx340series-1.50-1-i386-deb
scangearmp-mx340series-1.50-1-i386-deb.tar.gz
cecilia@cecilia-desktop:~/Desktop/downloads$ cd ./cnijfilter-mx340series-3.30-1-i386-deb/
cecilia@cecilia-desktop:~/Desktop/downloads/cnijfilter-mx340series-3.30-1-i386-deb$ ls
install.sh  packages  resources
cecilia@cecilia-desktop:~/Desktop/downloads/cnijfilter-mx340series-3.30-1-i386-deb$ install.sh*  packages/  resources/
install.sh: command not found
cecilia@cecilia-desktop:~/Desktop/downloads/cnijfilter-mx340series-3.30-1-i386-deb$ 

ever thing work but when i get here it come up with command not found help please tom

---

### Post by AndyCinDallas on 2010-11-15
Use the dpkg command instead - here's what I did after unzipping (untarring, I guess) onto my Desktop:

[b]cd Desktop/

cd cnijfilter-mx340series-3.30-1-i386-deb/

cd packages/

sudo dpkg -i --force-all *.deb[/b]

---

### Post by mstormo on 2010-11-18
> **josephhitt said:**
> 
Unfortunately it didn't quite work for me.  One difference was that I had to enter the printer IP manually (no big deal, just not sure why it didn't find it from scanning the subnet).  Then, things went smooth up until I tried printing the test page, last line in the error log is:

D [06/Jul/2010:20:40:13 -0400] cupsdAuthorize: No authentication data provided.

I also got "Couldn't find any printers" when clicking the Find button. However, while I was entering the IP number in the find box, the two entries mentioned in the post above actually got populated in the list to the left in that dialog.
So, have some patience in that dialog, and they'll show up, I guess. :)

Thanks for this How To! Clean, nice and easy!

---

### Post by joslin on 2010-11-24
Works great!  Thanks so much, love the Ubuntu community precisely for posts like this.  Thanks.

---

### Post by ianb1469 on 2011-01-02
Thank you!

---

### Post by abelandlinux on 2011-01-25
Greatly useful post! Thank you.

---

### Post by rgorry on 2011-02-03
Great awesome post, thanks.

I followed all steps and done it smoothly with no problems. 1 thing though, I can't get it configured to print B/W only. It seems to be using the Color ink all the time, which is expensive.

How do I get it to print B/W only?

Thank you.

---

### Post by tybrownintn on 2011-02-12
> **Archival Liaisons said:**
> Hi Cypher2, great "How To" it worked for me:D, Thanks,

p.s. Drivers now available on the European Site.

[http://software.canon-europe.com/products/0010835.asp](http://software.canon-europe.com/products/0010835.asp)

I don't know if this is the case with the original link to the Asian site but the European site also includes html manuals with install instructions.  It is done in a terminal but uses an install.sh command with some prompts following to get the printer set up.  I found this to be very easy and recommend it.  Same with scanner, though I have not tested the scanning function.  Note that the scanner apparently only works via GIMP.

---

### Post by HouTex on 2011-02-17
I was able to get the scanner to work by following the initial post. I had to right click on the desktop and click "Creat Launcher" and then type the commands as instructed. However, the scanning utility is very limited. It does not provide for mulltipage documents--at least as far as I can tell. But thanks to the OPer for a very good tutorial.
 
[edit]  It does appear to allow for multi-page scanning.  It seems you have to use the document feeder for it to work.  It scans the pages automatically into a multi-page pdf (or other chosen format).

---

### Post by Bulkley on 2011-03-30
Sorry to resurrect this thread but I've hit a brick wall with this.  If we go to the following instruction from the original post we see this line:

> If your router/modem is encrypted with a password (which it normally should), the printer will ask for it - enter it via the number input panel on the right, press OK.The problem is that my router uses a 128 bit key with both letters and numbers and is coded something like a0:df:00:e7: etc.  There are 13 pairs in this key.  The Canon keypad has no ability to enter letters.  When I try to enter 'a' it inputs '2', etc.  The result is an error.  No mater how I try to compensate, it just errors.  Obviously, I don't understand something.  Does anyone know what I should be doing?  

BTW, I am using a Siemans Gigaset801 modem/router.  The Canon MX340 has no trouble finding it; I just can't make it log in.

---

### Post by AndyCinDallas on 2011-03-31
This works on 10.10 (Meerkat) 64-bit also.

However, after installing the drivers I couldn't find the printer, so I switched it off, fired it back up, waited 15 minutes (not deliberately, I was just playing with the dog) - and it was found.

Test-page printed just fine, too - yay! :)

---

### Post by Bulkley on 2011-04-01
I finally got the password in.  On the keypad, the * button is used to change from a number to a capital letter or a lower case letter.  Canon should have that in the instruction manual.  It's straight forward once you know, but figuring it out is a nightmare.  

Now to proceed with the rest of the instructions.

---

### Post by Bulkley on 2011-04-07
My MX340 is now printing.  After going around in circles for several days I went back to the printer and extended the WSD Timeout from 1 to 5 minutes.  That worked.   I had ignored WSD because I thought it was a purely Windows function.  Apparently not.  

If anyone else here is configuring by hand,   lpd://192.168.1.65/PASSTHRU  is what works with this printer.  The IP address came from the printer's Network Configuration Page which is generated by choosing  "sub-menu PRINT LAN DETAILS."

I am posting this because it might help someone else.  The instructions posted by [Cypher2]("http://ubuntuforums.org/member.php?u=933205") are good and I thank him for them.

---

### Post by caedocha on 2011-04-18
Hi, thx a lot for the post, it help me a lot to install my printer without any problem. 

Do you have any recommended utility for scanning ?

Thx


Caedocha.

---

### Post by raincityrunner on 2011-04-25
I followed the instructions and it works very well. Thank you!

---

### Post by wo251a on 2011-04-26
Cyber2 - thanks for the installation tip.  Clear and concise..!!  Awesome!

---

### Post by Carosweety on 2011-04-27
Thank you for your Tips

very useful information, Its helpful to solve my problems

Nice to meet you all.

---

### Post by corrytonapple on 2011-05-21
My printer is not on the list!  I am on Natty 11.04.

---

### Post by riskbreaker927 on 2011-05-31
Not working on Natty. I did this on Maverick and it worked, however, now I get the following:

```


$ sudo dpkg -i --force-all *.deb

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 143785 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace cnijfilter-mx340series:i386 3.30-1 (using cnijfilter-mx340series_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-mx340series:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: also configuring `cnijfilter-common:i386' (required by `cnijfilter-mx340series:i386')
dpkg: dependency problems prevent configuration of cnijfilter-mx340series:i386:
 cnijfilter-mx340series:i386 depends on libatk1.0-0 (>= 1.9.0).
 cnijfilter-mx340series:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-mx340series:i386 depends on libcairo2 (>= 1.0.2-2).
 cnijfilter-mx340series:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-mx340series:i386 depends on libfontconfig1 (>= 2.3.0).
 cnijfilter-mx340series:i386 depends on libglib2.0-0 (>= 2.10.0).
 cnijfilter-mx340series:i386 depends on libgtk2.0-0 (>= 2.8.0).
 cnijfilter-mx340series:i386 depends on libpango1.0-0 (>= 1.12.3).
 cnijfilter-mx340series:i386 depends on libpng12-0 (>= 1.2.8rel).
 cnijfilter-mx340series:i386 depends on libpopt0 (>= 1.7).
 cnijfilter-mx340series:i386 depends on libtiff4.
 cnijfilter-mx340series:i386 depends on libx11-6.
 cnijfilter-mx340series:i386 depends on libxcursor1 (>> 1.1.2).
 cnijfilter-mx340series:i386 depends on libxext6.
 cnijfilter-mx340series:i386 depends on libxfixes3.
 cnijfilter-mx340series:i386 depends on libxi6.
 cnijfilter-mx340series:i386 depends on libxinerama1.
 cnijfilter-mx340series:i386 depends on libxml2 (>= 2.6.24).
 cnijfilter-mx340series:i386 depends on libxrandr2.
 cnijfilter-mx340series:i386 depends on libxrender1.
dpkg: error processing cnijfilter-mx340series:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386
 cnijfilter-mx340series:i386
 cnijfilter-common:i386

```

Edit: it's because of this bug: [https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634](https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634)

---

### Post by strungoutfan78 on 2011-07-03
I'm following this thread as well as a couple others in addition to one I started at Debian User Forums regarding this printer.  Allow me to clarify I'm not running Ubuntu, rather Debian Squeeze amd64.  However, I was able to install the drivers by altering the install.sh script in the deb/packages folder to as discussed here:

[[COLOR="Navy"]http://forums.debian.net/viewtopic.php?f=5&t=66325&p=380094#p380094[/COLOR]]("http://forums.debian.net/viewtopic.php?f=5&t=66325&p=380094#p380094")

Unfortunately when running the printer setup and choosing Network it finds nothing.  I can't even manually enter the static IP address of the printer.  Something is wrong here and it just may be the slight difference between the driver architecture (Deb 32-bit for Ubuntu 9.10 vs my Debian 6.0.1 amd64).  

Hopefully the link I posted can help if anyone runs across the same issue.  Also maybe someone has run accross this and figured it out and could share?  Thanks.

---

### Post by glitch007 on 2011-07-20
> **rgorry said:**
> Great awesome post, thanks.

I followed all steps and done it smoothly with no problems. 1 thing though, I can't get it configured to print B/W only. It seems to be using the Color ink all the time, which is expensive.

How do I get it to print B/W only?

Thank you.

I've noticed this too.  I don't think there's a way to print in draft mode, grayscale.  The Canon drivers are minimal... but if anyone else knows, we'd be glad to hear how to print in draft mode to save ink.

Thanks for the instructions by the way.

---

### Post by DizzleLizzle on 2011-09-14
I accidentally launched Simple Scan and it caused scangearmp to stop working.  To get it working again, I needed to cycle the power on the printer.  Hopefully this will help someone.

---

### Post by aquibmir on 2011-10-13
Excellent!

I followed the instructions on 10.04 32-bit and everything works perfectly.

Thanks for the detailed post.

---

### Post by jfgencarnacao on 2011-10-16
Unfortunately this doesn't seem to work that well under Ubuntu 11.10. I have 3 computers running it, followed the instructions on them all. In 2 of them, I was able to install succesfully, the 3rd computer still doesn't find the printer.

However, in both those computers where I was able to install it, the system updater seems to regard those drivers as a problem and obligates me to remove them before being able to update the system/install software via apt-get.

Of course after removing the drivers, you won't be able to use the printer again. Trying to figure out a solution for this, but it goes way beyond my knowledge. Any ideas?

---

### Post by corrytonapple on 2011-10-16
> **jfgencarnacao said:**
> Unfortunately this doesn't seem to work that well under Ubuntu 11.10. I have 3 computers running it, followed the instructions on them all. In 2 of them, I was able to install succesfully, the 3rd computer still doesn't find the printer.

However, in both those computers where I was able to install it, the system updater seems to regard those drivers as a problem and obligates me to remove them before being able to update the system/install software via apt-get.

Of course after removing the drivers, you won't be able to use the printer again. Trying to figure out a solution for this, but it goes way beyond my knowledge. Any ideas?
I should try it again then since it works for you, maybe for me.  But my system is really messed up, so maybe not.  Such as I get samba errors every time I use apt-get.  I would just disregard those errors, as the job itself is probably getting done unless you are getting errors saying you cannot update because of those drivers.  But make sure that its still updating.  Just run it once then run it again and you'll see if any new packages are there.  If so, then you have issues with the system....

---

### Post by jfgencarnacao on 2011-10-18
It doesn't let me update at all, it tells me I have to remove those drivers first by doing apt-get update -f, and by doing it, it removes the drivers.

---

### Post by JohnHenry3 on 2011-10-25
I followed the instructions to a T and my 10.04 failed to find the printer. So I followed an earlier suggestion to try restarting. Lo and behold, upon rebooting my screen resolution is completely jacked down to 1024X768 from the proper 1920x1080. The proper resolution is not in the Display section and I'm back to trying to solve a problem that's been around for YEARS , as evidenced by threads dating to 2004.

It's $hit like this Ubuntu; try to get a printer working and end up borking something totally different.

---

### Post by jfgencarnacao on 2011-11-04
Anyone got this printer to work successfully in Oneiric so far?

---

### Post by corrytonapple on 2011-11-06
Nope, anyone else got it to work?

---

### Post by donalgodon on 2011-11-07
I might end up having to sell this device and move to something that IS functional. Any suggestions?

---

### Post by riskbreaker927 on 2011-11-16
Although this method did work for me in 64-bit Maverick and Natty, it is now broken in 11.10 (Oneiric.) This ironically seems to have to do with the fact that they are trying to make 32-bit packages work better with 64-bit installations.

Forcing the installation of the two canon packages (with either --force-all or --force-depends) seems to cause the following problems: ```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cnijfilter-common:i386 : Depends: libpopt0:i386 (>= 1.7) but it is not installed
 cnijfilter-mx340series:i386 : Depends: libatk1.0-0:i386 (>= 1.9.0) but it is not installed
                               Depends: libcairo2:i386 (>= 1.0.2-2) but it is not installed
                               Depends: libgtk2.0-0:i386 (>= 2.8.0) but it is not installed
                               Depends: libpango1.0-0:i386 (>= 1.12.3) but it is not installed
                               Depends: libpopt0:i386 (>= 1.7) but it is not installed
                               Depends: libxcursor1:i386 (> 1.1.2) but it is not installed
                               Depends: libxinerama1:i386 but it is not installed
                               Depends: libxml2:i386 (>= 2.6.24) but it is not installed
E: Unmet dependencies. Try using -f.

``` And the system remains broken until running apt-get -f install, which just removes the two canon packages.

There's gotta be a workaround. Maybe copying all the files installed by the packages out of, and back into their respective locations after removing the packages?

---

### Post by Docaltmed on 2011-11-22
If anyone is in gnome shell and trying to install this printer, you may get an error about "firewallD" not running, prohibiting you from adding the computer. 

To access the more familiar Ubuntu printer GUI from gnome shell, simply press Alt-F2 and type 

```
system-config-printer
```

on the command line. This will give you a printer GUI that will allow you to install this printer as outlined. It appears that "firewallD" is some RedHat package that isn't even packaged for Ubuntu, but the reference to it slipped through the cracks somehow.

More on this bug here:


[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985)

---

### Post by Docaltmed on 2011-11-22
There's a hack -- and it's a heckuva hack -- here:

[https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634](https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634)

Down near the bottom of the page, one person describes the process of going into the .deb file, making it think that it's an AMD64 file, and then rebuilding the deb.

I might give it a go when I'm not suffering from a head cold.

---

### Post by marseille on 2011-11-26
just bought a used Pixma MX340 for $25 USD this morning. So far so good -- got it up and running on Ubuntu LTS 10.04; AMD 64bit... already had _[ia32-libs]("http://packages.ubuntu.com/search?searchon=names&keywords=ia32-libs")_ (32-bit compatibility libraries) installed so maybe that helped.

Thank-you for your help :KS

---

### Post by bota87 on 2012-02-15
> **Docaltmed said:**
> There's a hack -- and it's a heckuva hack -- here:

[https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634](https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/767634)

Down near the bottom of the page, one person describes the process of going into the .deb file, making it think that it's an AMD64 file, and then rebuilding the deb.

I might give it a go when I'm not suffering from a head cold.

Thanks Docaltmed!

I modified the architecture of the package and now I can print and scan without any problems!

Driver to print
[http://dl.dropbox.com/u/1698395/driver%20mx340/cnijfilter-common_3.2.30-1_forced_amd64.deb]("http://dl.dropbox.com/u/1698395/driver%20mx340/cnijfilter-common_3.2.30-1_forced_amd64.deb")
[http://dl.dropbox.com/u/1698395/driver%20mx340/cnijfilter-mx340series_3.2.30-1_forced_amd64.deb]("http://dl.dropbox.com/u/1698395/driver%20mx340/cnijfilter-mx340series_3.2.30-1_forced_amd64.deb")

Driver to scan
[http://dl.dropbox.com/u/1698395/driver%20mx340/scangearmp-common_1.50-1_forced_amd64.deb]("http://dl.dropbox.com/u/1698395/driver%20mx340/scangearmp-common_1.50-1_forced_amd64.deb")
[http://dl.dropbox.com/u/1698395/driver%20mx340/scangearmp-mx340series_forced_amd64.deb]("http://dl.dropbox.com/u/1698395/driver%20mx340/scangearmp-mx340series_forced_amd64.deb")

---

### Post by rue1341 on 2012-02-25
For Ubuntu 11.10 64bit

Many thanks to Cypher2, bota87 and Marseille, I have finally got my MX340 to print by USB & wireless.

I my experience you need to:-

Set the printer up according to Cypher2's instructions (page 1)

Then use bota87's packages and Cypher2's method of installing them.

BUT first check you have "ia32-libs" and "ia32-libs-multiarch:i386" packages install on your system, it did not work for me without them.

Also it may help to re-boot.

One very happy man :P

---

### Post by bionicears on 2012-03-09
I followed what [rue1341]("http://ubuntuforums.org/member.php?u=606338") posted. And finally, after countless attempts of other suggestions, I could print with my Canon MX340 using Ubuntu 11.10.

Installing the printer on 10.04 LTS was painless. Installing the printer on 11.10 was just painful.

---

### Post by starcutter on 2012-03-29
Overall these instructions worked well for me too.  I'm currently running Ubuntu 11.10.  Installing the two Debian pkgs was a breeze.  The only thing different was that I had to manually enter in the IP of the printer for the search function to find it.  Other than that everything went great.

---

### Post by rue1341 on 2012-04-26
I had problems using the above with 12.04, the scanner worked fine but it would not print via USB. I solved this with the help of bug #701856 comment 20 by Yousry Abdallah 

(Remember to install "ia32-libs" via synaptic pakage manager first)

Solved. Driver requires libpop0 version 1.7 or higher, 1.6 installed on 12.04
Solution remove dependancy of this lib.

Download "MX340_Linux_Package.tar" from european canon site
extract "cnijfilter-mx340series-3.30-1-i386-deb"
Open terminal and cd to "packages" within the above .deb
Now...............
dpkg -x cnijfilter-common_3.30-1_i386.deb common
dpkg --control cnijfilter-common_3.30-1_i386.deb
vim DEBIAN/control
Now.............. remove the "Dependency: libc (..." line (could be "Depend")(move to line then press 'dd' this deletes the line then ESC  then ":x" (colon then x)   then Return to save and return to the terminal)
cp -a DEBIAN/ common/
dpkg -b common cnijfilter-common_3.30-1_i386.deb
dpkg --force-all -i cnijfilter-common_3.30-1_i386.deb
rm -rf common DEBIAN
this should have sorted out the dependancy issue
Now.............. install the other .deb "cnijfilter-mx340series_3.30-1_i386.deb" in the terminal
dpkg --force-all -i cnijfilter-mx340series_3.30-1_i386.deb

I did this with the printer on and attached via USB, it installed it self and worked.

---

### Post by corrytonapple on 2012-04-26
THE PRINTER WORKS!
I am just amazed.  Wow.  I was looking around through the settings, and I saw when I went to Colors (I'm in 12.04 BTW) that it saw the household printer.  Thinking "No way...." I went to printers, put it the printer's static IP address, and it saw it.  I stuck with the default connection method, and then it searched for drivers.  It failed, but it let me pick a driver from the list, and one of them was for the MX340!  I just printed the full color test page, and it works.  This is just awesome.

We have come a long way in two years

---

### Post by robgberg on 2012-07-21
I'm using Ubuntu 12.04 LTS 64 bit and attempted this install.  I received a dependency warning after running "sudo dpkg -i *deb" in the cnijfilter folder, something like libstc++6 >= 4.0.  The script completed but after installing the scangear packages and attempting to install the printer in the administrative utility, print test pages failed, and the test document is stopped in the print queue.  I can print to the printer via Windows, so the printer and the wireless connection is working.

Any ideas?

---

### Post by AndyCinDallas on 2013-06-21
I'm now on 12.04 LTS and this error showed up:

[IMG]http://i41.tinypic.com/2zrhq2g.png[/IMG]

As the pic shows, I've had to type **apt-get install -f** in the console - which ran a whole bunch of updates, so we'll see what happens.

---

### Post by chaoticpsyche2112 on 2014-04-01
THANK YOU! I have spent the last 3 hours trying to get my printer to work, and have drivien myself insane because it wouldn't. Thank you so much. While these instructions applied to MX340 it worked for MX450 as well, so I am completetly happy. Thank you!

I only had one small issue, the scanner part of the instructions didn't work for me. However, that could be because I'm running 13.10 but well, I'm not really picky right now, I'll keep trying but I'm just glad that I at least got the printer working. I feel like I accomplished something semi-impossible right now, so I'm feeling great, caffiene withdrawal and all! :D

---

### Post by AdhamG on 2014-04-12
[COLOR=#000000]Thank a lot, it's work for me[/COLOR]

---


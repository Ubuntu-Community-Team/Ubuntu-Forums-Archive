---
title: "Dropbox-options and tray missing."
date: 2015-06-02
forum: Ubuntu Studio
---

### Post by denungeherrholm on 2015-06-02
New Ubuntu-studio user here, pretty new to Linux at all(Using for a year or so). 

I installed Dropbox, and found that I didn't get any dropbox-icon in the system panel, and that there's no dropbox-options in Thunar when I right-click on dropbox-files. I understand this is because the dropbox application is geared towards Nautilus, not Thunar. 

I found a solution for Xubuntu, and tried to follow it: [http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html](http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html)

But I couldn't open any dropbox-daemon because the  "~/.dropbox-dist/dropboxd" file didn't exist( No .dropbox-dist folder and no dropboxd -file in the .dropbox folder). I tried to finish the installation still. No results. 

I then tried to install Nautilus, and no dropbox-options when I right-click dropbox-files still. 

I've tried uninstalling and reinstalling dropbox, but no luck. I've tried to figure out how to uninstall the Thunar-dropbox extension again, but haven't figured out how. 

Anyone know how to get full dropbox compatablity? I really need it, because I use dropbox a lot in my work-flow.

---

### Post by Nosphky on 2015-06-05
I had the problem of being unable to find the settings and system tray icon with dropbox around the beginning of this year.  The icon would appear some days and then disappear for a few weeks.  I contacted dropbox support who told me it was a known problem with their version of dropbax for linux.  Since then,  a later version (3.4.6) came out and the problem of disappearing tray icon exists no longer (at least for me on UbuntuStudio1404 and a Debian portable).  (I think they were on 3.4.8 yesterday)

I didn't have to change file manager - Thunar works.  I am somewhat perplexed by your statement that   "~/.dropbox-dist/dropboxd file didn't exist".   I didn't have that problem and dropbox was always working fine even though the icon was missing.

I have however sometimes had problems installing dropbox when I make a download from the website.  The way that always seems to work for me (and I just did it again on Debian jessie yesterday) is to go further down the dropbox downloads page, below the distro / architecture selection and use the scripts they show.

[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

for 32bit
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf - 
for 64 bit

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
Next, run the Dropbox daemon from the newly created .dropbox-dist folder.
~/.dropbox-dist/dropboxd

Hope this helps.

---

### Post by denungeherrholm on 2015-06-06
Wow! That seems to have done the trick! Thank you!

---

### Post by Kurt_Alan on 2015-06-07
> **denungeherrholm said:**
> New Ubuntu-studio user here, pretty new to Linux at all(Using for a year or so). 

I installed Dropbox, and found that I didn't get any dropbox-icon in the system panel, and that there's no dropbox-options in Thunar when I right-click on dropbox-files. I understand this is because the dropbox application is geared towards Nautilus, not Thunar. 

I found a solution for Xubuntu, and tried to follow it: [http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html](http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html)

But I couldn't open any dropbox-daemon because the  "~/.dropbox-dist/dropboxd" file didn't exist( No .dropbox-dist folder and no dropboxd -file in the .dropbox folder). I tried to finish the installation still. No results. 

I then tried to install Nautilus, and no dropbox-options when I right-click dropbox-files still. 

I've tried uninstalling and reinstalling dropbox, but no luck. I've tried to figure out how to uninstall the Thunar-dropbox extension again, but haven't figured out how. 

Anyone know how to get full dropbox compatablity? I really need it, because I use dropbox a lot in my work-flow.

The short answer to your question is that Dropbox does not support Xubuntu. But there MAY be a workaround (unsuccessful for me.) These two reports are the latest information I have. The first is from dropbox.com tech support. The second is from ditto bus escalated support:

ONE

Harley, May 7, 8:49 PM:
Hi Kurt!
Thanks for writing in. My name is Harley, and I'd be happy to assist you with this.
When new versions of the Dropbox desktop application are released, issues can arise on computers that use Linux because of the difficulty of testing the latest version on all of the distributions of Linux that exist.
For your computer with Xubuntu 14.04, I'm going to give you the steps to perform a complete uninstall of Dropbox, then install the latest stable release of our software. Hopefully this gives you full functionality again, but if you're still only able to access Dropbox through the command line then we have directions on how to manage selective sync settings in a headless environment here:[https://www.dropbox.com/en/](https://www.dropbox.com/en/).
First, make sure you save and quit ALL programs that access files in the Dropbox folder.
Depending on your OS and the package you used to perform the installation, you could have files in two different locations. I'm sending you instructions for both of the cases, so if some of the commands error out don't worry.
Run the following commands in your terminal:
&#8194;&#8194;&#8194;&#8194; dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox
After this, you can download version 3.4.6 of Dropbox at your command prompt. Depending on your system, you'll need either the 32-bit or 64-bit installer files.
32-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
64-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
Next, run the Dropbox daemon from the newly created .dropbox-dist folder to install the application:
~/.dropbox-dist/dropboxd
More installation and CLI information is also available here:
&#8194;&#8194;*[https://www.dropbox.com/](https://www.dropbox.com/)
After doing this, you should have a working version of Dropbox on your Linux system. But if this installation of Dropbox did not resolve your issue, please let me know so we can continue troubleshooting.
I hope this helps!
Have a wonderful day!
Harley

TWO

Frida, May 12, 2:21 PM:
Hi Kurt,
My colleague Harley escalated your request to me and I will be assisting you moving forward. My name is Frida and I'm a member of our team who specializes in desktop application issues.
After reviewing the issue you described, it appears that your specific desktop environment of Linux may not be supported by our desktop application. Xubuntu may be supported but you have to make sure that certain dependencies are installed. Please review the "For Advanced Users" section at the bottom of this article for detailed information about this:
[https://www.dropbox.com/en/](https://www.dropbox.com/en/)
You need to make sure that the dependencies are also updated along with the Dropbox desktop application - if you're unsure about this, please reach out to Xubuntu support directly.
I hope this is helpful - please let me know if you have any other questions.
Regards,
Frida


For our advanced users
Linux installer
Dropbox supports the following desktop environments:
Ubuntu (Unity) and GNOME Classic, full support using the package in our*installation page.
XFCE is supported if the corresponding Nautilus dependencies are installed.
GNOME shell natively displays the file overlays, but requires the extension TopIcons to get the application indicator (tray icon).
Dropbox uses*QT 5.3, and as such needs the following software to work on desktop environments:
GTK 2.12 or higher
GLib 2.22 or higher
Libnotify 0.4.4 or higher
Libappindicator 1.0
Nautilus 2.30.0 or higher
The Nautilus installer source code has been released under an MIT license, and people have reported building from source on different versions of Gentoo, Arch Linux, OpenSUSE, and Debian. 


These are the dependencies you need:

GTK 2.12+
Glib 2.22+
Libnotify 0.4.4+
Libappindicator 1.0
Nautilus 2.30.0+

Qt 5.3

IF YOU FIND SUCCESS WITH THE DEPENDENCIES LET ME KNOW!

---


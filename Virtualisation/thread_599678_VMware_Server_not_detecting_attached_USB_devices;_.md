---
title: "VMware Server not detecting attached USB devices; LPT port can't be added either..."
date: 2007-11-01
forum: Virtualisation
---

### Post by diablo75 on 2007-11-01
I am attempting to install a XEROX Documate 510 scanner on a Windows VM running inside of VMware Server. After attaching the device to the USB port on my PC, and then powering on the VM, no new device appears in the Removable Devices menu, where normally you would see a device and check it off to attach it to the VM.

Also, I'm wanting to install a printer on my LPT port. After adding it to my VM's profile, this error message appears on screen:

Parallel port "/dev/parport0" is used by another program (such as another instance of VMware Server) or driver (such as lp). Virtual device parallel0 will start disconnected.

How do I take care of these two problems?

---

### Post by jshanks on 2007-11-01
While I'm not absolutely sure, from the available documentation it seems that the LPT ports are not available to the virtual machine.

As a workaround, you can enable cups-lpd printing on the Linux side and sharing the printer and then installing Print Service for Unix on the Windows 2000 or XP side.

I've been planning on writing an Ubuntu how-to for this.  Maybe I'll get on it tonight.  :)

Anyway, the official cups documentation on linuxprinting.org does have a section that covers it pretty well.

---

### Post by diablo75 on 2007-11-01
> **jshanks said:**
> While I'm not absolutely sure, from the available documentation it seems that the LPT ports are not available to the virtual machine.

As a workaround, you can enable cups-lpd printing on the Linux side and sharing the printer and then installing Print Service for Unix on the Windows 2000 or XP side.

I've been planning on writing an Ubuntu how-to for this.  Maybe I'll get on it tonight.  :)

Anyway, the official cups documentation on linuxprinting.org does have a section that covers it pretty well.

Oh, that would be great if you wrote a howto!  Let me know if you do!

---

### Post by jshanks on 2007-11-01
lol, I just realized that I have no idea where to post HowTos.

So anyway, here's what I have so far.  It's been tested using VirtualBox with Gutsy and Windows XP and Windows 2000.  Maybe someone with VMware can add to it and let me know:

Printing to a Linux Local Printer from a Windows 2000 or XP Virtual Client.

Since virtual machines running on Ubuntu have become more popular, there seems to be a few issues that come up over and over.  One of them is printing from a virtual client to a local printer on the host.  Both Vmware and VirtualBox seem to have at least some difficulty sharing printers with the client.  Fortunately there's a relatively easy solution.  If seen it suggested that you might have to buy a network capable printer or install a Samba server on the host machine, and while that might fix the problem, it is in the case of the network printer, an unneeded expense and in the case of Samba (which I like very much) overkill for print services.

LPR/LPD print services to the rescue.

If you're running any modern Linux, chances are you already have Unix LPR/LPD print services installed.  In the case of a system with CUPS installed, all you have to do is share the printer and tell the Internet superserver inetd or xinetd to listen for print jobs.

Ubuntu 7.10 has no Internet Superserver installed by default.  For reasons unknown to me, but also just fine, the OpenBSD inetd Superserver seems to be the preferred choice.  To install the superserver, in a terminal window simply run:

sudo apt-get install openbsd-inetd

This will install the superserver and any related dependencies.

The next thing you will need to do is tell the superserver to listen for print jobs.  You can use any text editor to edit the inetd configuration file.  Here again, you will have to do this in a terminal windows at the command prompt:

 sudo gedit /etc/inetd.conf


Page down to the end of the file and add the following line:

printer stream tcp nowait lp /usr/lib/cups/daemon/cups-lpd cups-lpd -o document-format=application/octet-stream

Then save the file.

Now just one more thing to get the superserver up and running . . . start it:

sudo /etc/init.d/openbsd-inetd restart

if should respond with:

* Restarting internet superserver inetd                                 [ OK ]

If not, check the configuration file again and make sure it's exactly as above.

OK, now you're ready to configure you client.
Because Unix printing has been around so long, it's even supported by Windows.

The first thing you have to do on you Windows Virtual Client is to install “Print Services for Unix”.
To install Unix Print Services, go to the Control Panel, select Add and Remove Program, and then Select Add/Remove Windows Components in the left pane.  Now scroll the list down and check “Other Network File and Print Services”.  That's it for that.

Now you're ready to add the printer.  You do it basically the same was as you would add any printer for windows with one additional step; creating a new local LPD printer port.

Start the add printer wizard, and select “Local printer attached to this computer”  and NOT network printer.  Press next, Now instead of selecting LPT1:  (or any preconfigured port) select “Create a new port” then under Port Type select “LPR”.

Upon pressing next, you'll be presented with another fill in box asking for:

Name or address of server providing lpd:
This is either the IP address or the DNS name of the local computer host.

    -and-

Name of  print queue or printer on the server:
This is whatever you named the printer in the CUPS configuration.  This has to be exactly right, close gets you no points.

When you've entered the correct information, just press next and setup the printer with the appropriate windows drivers, just like always.  You should be able to print the test page with no problem.

---

### Post by diablo75 on 2007-11-02
> **jshanks said:**
>  Start the add printer wizard, and select &#8220;Local printer attached to this computer&#8221;  and NOT network printer.  Press next, Now instead of selecting LPT1:  (or any preconfigured port) select &#8220;Create a new port&#8221; then under Port Type select &#8220;LPR&#8221;.

Upon pressing next, you'll be presented with another fill in box asking for:

Name or address of server providing lpd:
[B]This is either the IP address or the DNS name of the local computer host.

    -and-

Name of  print queue or printer on the server:
This is whatever you named the printer in the CUPS configuration.  This has to be exactly right, close gets you no points.[/B]

When you've entered the correct information, just press next and setup the printer with the appropriate windows drivers, just like always.  You should be able to print the test page with no problem.

Can you add some extra detail about the part in bold?  How can I find out these numbers and names, and can you provide an example the address and name syntax please?

---

### Post by diablo75 on 2007-11-02
Also, while this work around may/will help with the inability to add an LPT port based printer to my Windows XP VM, it doesn't help with the USB problem I am having.  I've used VMware Server on several hosts before, and am familiar with how the Removable Devices menu is supposed to work.  It doesn't seem to be actively monitoring the USB ports on my PC to detect attached devices and acquire control of those devices from Linux upon request.

Any ideas?

---

### Post by jshanks on 2007-11-03
You're right, this won't help for the USB problem, just the printer problem.  However, if the USB device you need to attach to is a printer, this might indeed help.

I've had various problems with USB devices under VirtualBox as well.  That's what led me to just use LPR/LPD for printing.

---

### Post by jshanks on 2007-11-03
In the How-To, I plan on adding some screenshots to better explain where the information is entered.  I will attach a couple shots, so that you can see what my configuration looks like.

You will see in the Ubuntu Printer Configuration snapshot, the name of the printer in the left column.  This matches the name of the printer in the Windows XP port configuration.  The IP address in the Windows XP port configuration, is the IP address of the computer with the printer attached, and in this case the host of the virtual machine.

---

### Post by diablo75 on 2007-11-03
I'm connected to my computer via VNC and it would appear that I've gotten it to successfully print from Windows VM to Ubuntu (won't know till I get home tonight and look at the printer).  This is a pretty good solution to my original problem, though it is very dependent upon whether or not the printer is supported by Ubuntu and can be installed in cups without hassle.

Still, I would like to know how to properly add an LPT port to a VM.  And I really really want to know why VMware doesn't want to detect any USB device I attach.   I've tried an external hard drive, and external burner, and the scanner I mentioned above.  None of those items ever want to show up in the Removable Devices list....  :(

---

### Post by stell86 on 2007-11-03
> **diablo75 said:**
> Also, while this work around may/will help with the inability to add an LPT port based printer to my Windows XP VM, it doesn't help with the USB problem I am having
Any ideas?
[**[COLOR="Blue"]This[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=588225") worked for me to get my Scanner available in Gutsy.

The solution is given in the 1st post
Thanks to ashishgoel for that feedback

---

### Post by diablo75 on 2007-11-09
I managed to get things to print from Windows to Ubuntu using the above method of adding a Unix printing system to Windows then specifying an address.  But I have problems printing PDF's.  They take forever to print.  We seemed to be able to solve this problem by opening Printer configuration menu and click the tab Installed Options and put the total memory up to mirror the capacity of your printer. After doing this, my pdf docs print within two seconds. Before it would bottleneck and not print.  Now it seems to be doing it again....

---

### Post by jimshawnz on 2007-11-09
Yesterday I upgraded from 7.04 to 7.10 and then no USB devices appeared in my VMWare server sessions.

I fonud this thread and no answers so looked a bit deeper.

I noticed that there are no entries in /proc/bus/usb at all either so that may point at the reason. 

I did a search and found that I need to:
**mount -t usbfs none /proc/bus/usb**

That gave me /proc/bus/usb entries.

Restarting VMWare server gave me back my USB devices.

I am about to add an entry to fstab to have the mount happen automatically. Not sure why this changed in the upgrade.

Cheers

---

### Post by blazer34i on 2007-12-29
Thanks for the information, it worked great with Kubuntu 7.10!

---


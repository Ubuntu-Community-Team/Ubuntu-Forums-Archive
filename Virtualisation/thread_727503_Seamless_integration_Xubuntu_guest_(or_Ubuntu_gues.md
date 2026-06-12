---
title: "Seamless integration: Xubuntu guest (or Ubuntu guest) - Windows XP Pro Host"
date: 2008-03-17
forum: Virtualisation
---

### Post by H_out on 2008-03-17
This is a guide for seamlessly integrating a Xubuntu guest OS (or Ubuntu guest OS) into a Windows XP Pro host.

Here is a screenshot of the xfce4-panel running seamlessly in the upper left corner of my Windows host.
[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=62930&stc=1&d=1205801152[/IMG][/CENTER]


First, here are some comments about this guide.[INDENT]I've found a lot of guides on creating seamless integration for a Linux host and Windows guest, but hardly any the other way around. ** To be clear, this guide is for setting up an Ubuntu guest (or Xubuntu guest) running virtually through VirtualBox to be seamlessly integrated with a Windows XP host.**

In this guide, I refer to the Windows XP Pro SP2 host as the Windows host.  I refer to the virtual Ubuntu 7.10 or virtual Xubuntu 7.10 as the guest OS.

This guide is meant to integrate a guest OS locally.  This means that the Windows host and guest OS are running on the same physical machine.

I try to be really clear about tasks meant to be done on the Windows host OS or the guest OS.  Sorry if it's repetitive and/or obvious!

Here is the software you'll need to download and install.  Don't look for them yet, I'm just giving you a heads up.

Software for the Linux guest:
[INDENT]openssh-server (lets the guest OS act like a server; available in the Ubuntu repository)[/INDENT]

Software for the Windows host:
[INDENT]VirtualBox (runs the guest OS)
PuTTY  (runs commands on the guest OS)
Xming (allows seamless integration; forwards X windows)[/INDENT]
[/INDENT]


**_SET UP THE GUEST OS_**

On the Windows host, install VirtualBox.  My version was VirtualBox_1.5.6-1_Win_x86.msi.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Create a VM and install the guest OS.  I highly recommend Xubuntu over Ubuntu.  I tried both and found Xubuntu to be less buggy and lighter on my system.

Use "NAT" for the VM network settings.  Port forwarding will be used later.  I found that this was the simplest way to give the guest OS internet access.  I'm in a dorm room at a university and don't have much control over my network.

Boot the guest OS and install Guest Additions.  Installing Guest Additions on a Linux guest is less intuitive than on a Windows guest.  Here's how you do it:

Mount VBoxGuestAdditions.iso by going to "Devices" and "Install Guest Additions" in the VirtualBox menu.

Next, open a terminal in the guest OS.  Enter the command:
```
cd /media/cdrom
```Then enter the command:
```
sudo bash ./VBoxLinux*
```
Now you need openssh-server in order for the guest OS to act like a server.

Open a terminal in the guest OS.  Enter the command:
```
sudo apt-get install openssh-server
```You can also install openssh-server using Synaptic by searching for "openssh-server".  No need to run openssh-server or anything like that right now.

Don't enable automatic log in for the guest OS.  When running the guest OS as a server, you don't need it to log in.

I recommend enabling a sound to indicate when the guest OS is ready to log in.  Ubuntu has this by default but Xubuntu does not.


**_INSTALL PUTTY_**

On the Windows host, download PuTTY.  Get the Windows installer (it contains plink.exe and PuTTYgen.exe, which you'll need).
My version was putty-0.60-installer.exe.
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

PuTTY will let you connect to the guest OS and give you terminal access.  This is shown later in the guide.

Run the installer.  The setup is straightforward.  You don't have to run PuTTY right now, move on to installing Xming.


**_INSTALL XMING_**

On the Windows host, download Xming.  I got it from sourceforge.net.  The fonts package isn't necessary, but recommended.  These are the only two things you need--the other Xming downloads from sourceforge aren't necessary.
My versions were Xming-6-9-0-31-setup.exe and Xming-fonts-7-3-0-9-setup.exe.
[http://sourceforge.net/project/showfiles.php?group_id=156984&package_id=175377](http://sourceforge.net/project/showfiles.php?group_id=156984&package_id=175377)
[http://sourceforge.net/project/showfiles.php?group_id=156984&package_id=175482](http://sourceforge.net/project/showfiles.php?group_id=156984&package_id=175482)

Xming will let you run X windows on your Windows host.  Additionally, Xming lets you run applications with hidden command prompts (they don't show up on the screen or the taskbar at all).  This is great for seamless functionality!  I use Xming to run a headless server with hidden command prompt.  This means my guest OS runs in the background and doesn't show up in my Windows host taskbar.  I explain how to do this later in the guide.

Install Xming.  When prompted to "Select Components", keep the boxes checked and select the "Don't install an SSH client" button.

After installing, run the Xming shortcut created by the installer.  It should show up in your system tray.
[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=62924&stc=1&d=1205800785[/IMG][/CENTER]

Note that additional parameters are used in the desktop shortcut created by the installer.  View the shortcut properties to see that the target is:
[INDENT]"C:\Program Files\Xming\Xming.exe" :0 -clipboard -multiwindow[/INDENT]

Running the Xming.exe manually (i.e. by double-clicking the executable Xming.exe from the install directory) won't enable these parameters.  Use the shortcut.


**_PORT FORWARDING_**

The following steps will set up the Windows host port 2222 to communicate with the guest OS.

The guest OS doesn't have to be running.

On the Windows host, go to Start >> Run.

Run each of these commands, one at the time, in the order shown.  Replace [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]with the name of guest OS virtual machine.

```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort" 2222
```
```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort" 22
```
```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol" TCP
```

You should get a flash of a command prompt after each run.  Shut down the guest OS if it's running, and exit out of VirtualBox.

Here's how you can verify changes you've made to the virtual machine.
[INDENT]Start >> Run
cmd
cd c:\program files\innotek VirtualBox
VBoxManage.exe getextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]enumerate[/INDENT]

These commands can be undone.  Go to Start >> Run, then enter, one at a time, the following commands:
```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort"
```
```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort"
```
```
"C:\Program Files\innotek VirtualBox\VBoxManage.exe" setextradata [COLOR="DarkGreen"]**WindowsXubuntu **[/COLOR]"VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol"
```


**_PUTTY SETTINGS_**

Boot the guest OS and wait until it reaches the login screen.

On the Windows host, run PuTTY.exe.

Under "Host Name (or IP address)", enter
[INDENT]localhost[/INDENT]

Under "Port", enter
[INDENT]2222[/INDENT]

Under "Saved Sessions", enter a name (don't confuse this with the name of your VM.  This name is the saved PuTTY session, name it whatever you want.  My VM is named "**[COLOR="DarkGreen"]WindowsXubuntu[/COLOR]**" and my saved PuTTY session is named "**[COLOR="Orange"]Xubuntu[/COLOR]**"):
[INDENT]**[COLOR="Orange"]Xubuntu[/COLOR]**[/INDENT]

Under "Category", go to "Connection" and then "SSH" and then "X11" and check the box for "Enable X11 forwarding".

Under "Category", go to "Connection" and then "Data" and enter your guest OS user name for "Auto-login username".

Under "Category", go to "Session" and press the "Save" button to save the PuTTY session.

Press "Open".  The PuTTY terminal will come up and prompt you for your password.  Enter it.  You may receive a message about security--keep going, it will only ask you this once.

Now you have access to your guest OS via the PuTTY terminal.  Try running some applications that your guest OS has.

If your guest OS is Xubuntu, try entering:
[INDENT]mousepad
xfce4-terminal
xfce4-panel[/INDENT]

If your guest OS is Ubuntu, try entering:
[INDENT]gedit
gnome-terminal
gnome-panel[/INDENT]

With Xming and PuTTY, you can run single applications seamlessly!

I have xfce4-panel running in the upper left corner of the my Windows host.  It gives me complete access to my guest OS!
[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=62930&stc=1&d=1205801152[/IMG][/CENTER]


**_AUTOMATE THE PROCESS - SAVE A PUTTY SESSION_**

Now we have to make this whole process automatic.

On the Windows host, run PuTTYgen.exe (located in the same folder as PuTTY.exe).  Press "Generate" and move the mouse around in the blank area to generate randomness as instructed in the window.

Press "Save public key" and then "Save private key".  Save both keys in the same place.

If you're prompted for a passcode, just keep going, you can save the private key without it.

Under "Key" select all of the text and copy it to your clipboard.  The text begins with "ssh-rsa" and ends with a date like "20080316".

Run PuTTY.exe.  Load your previously saved session.  Mine was named "Xubuntu".

Under "Category", go to "Connection" and then "SSH" and then "Auth" and select "Browse".  Find the private key you saved.

Under "Category", go to "Session" and press the "Save" button to save the PuTTY session.

Boot the guest OS and navigate to ~/.ssh/

My full path was: /home/user/.ssh/

If it doesn't exist, create it.

In that folder (~/.ssh/) find the file, "authorized_keys2".  If it doesn't exist, create it.  It doesn't have a file extension.

At the end of the file, paste the the public key that you saved to your clipboard.  It should be one long line.  Save the file.

Log out of the guest OS.

On the Windows host, run PuTTY.exe.  Load your previously saved session.  Mine was named "Xubuntu".

Press "Open".  It should not prompt you for your password like it did before.


**_AUTOMATE THE PROCESS - XMING AND PLINK_**

You can use plink.exe (located in the same folder as PuTTY.exe) to create Windows shorcuts to guest OS applications.  

Windows host shortcuts to guest OS applications follow this format:
[INDENT][[COLOR="DarkRed"]**path to plink.exe including quotes**[/COLOR]] [[COLOR="Orange"]**your saved PuTTY session name**[/COLOR]] [[COLOR="Blue"]**a command to execute**[/COLOR]][/INDENT]

Here is an example of the "Target" for my Windows shortcut:
[INDENT][COLOR="DarkRed"]**"C:\Program Files\PuTTY\plink.exe"**[/COLOR] [COLOR="Orange"]**Xubuntu **[/COLOR][COLOR="Blue"]**mousepad**[/COLOR][/INDENT]

Also, you can run a command using Start >> Run using the same thing:
**[INDENT][COLOR="DarkRed"]"C:\Program Files\PuTTY\plink.exe"[/COLOR] [COLOR="Orange"]Xubuntu [/COLOR][COLOR="Blue"]mousepad[/COLOR][/INDENT]**

Again, remember that [COLOR="Orange"]**Xubuntu **[/COLOR]is the name of my saved PuTTY session, and NOT the name of my virtual machine, which was **[COLOR="DarkGreen"]WindowsXubuntu[/COLOR]**.

Everytime you run a plink.exe shortcut to start up an application, it runs through the whole PuTTY log in process.  It's actually pretty slow (5 or 10 seconds).  The fast and seamless way to run applications is to run a guest OS panel or terminal (gnome-panel and gnome-terminal for Ubuntu, xfce4-panel and xfce4-terminal for Xubuntu).  When you select an application using a panel or run a command in a terminal, the application starts up instantly.  That is the kind of functionality we're after!

Some minor pros and cons regarding plink.exe shortcuts and panels:
[INDENT]Although running plink.exe shortcuts is a little slow, it will allow you have only the applications you want to run show up as tasks in your Windows host taskbar.  When running a panel, the panel task will show up in your Windows host taskbar, and then additional tasks will come up as you run applications.[/INDENT]

This is a little picky, but can be important to achieving a real seamless setup, so I'll explain further.

[INDENT]Using plink.exe:
[INDENT]I'm running a headless server, but you wouldn't know it unless you viewed a list of my processes.  My Windows host taskbar is completely empty.
I want to run an Ubuntu application, and I double click a plink.exe shortcut on my desktop, wait 5 seconds, and then the task shows up in my taskbar.  My taskbar now has one task in it.[/INDENT]

Using a panel:
[INDENT]I'm running a headless server, and in my taskbar there is a task named "Xfce Panel" even though the panel is hidden in the upper left corner of my screen.
I open up the panel to run an application, it starts instantly, and a new task shows up my taskbar.
I haven't found a way to hide the Xfce panel task from the Windows taskbar...[/INDENT][/INDENT]


Now we can set up Xming.exe and Xmingrc to hide command windows and organize some shortcuts.

The system tray icon for Xming has a customizable right-click menu.  The right-click menu is defined by a file named "Xmingrc".  It's NOT located in the installation folder.

On the Windows host, navigate to
C:\Documents and Settings\[[COLOR="Indigo"]**YOUR WINDOWS USERNAME**[/COLOR]]\

For me, the folder is:
C:\Documents and Settings\[COLOR="Indigo"]**User**[/COLOR]\

In this folder, find the file "Xmingrc".  If it doesn't exist, create it.  It doesn't have a file extension.

There is an example Xmingrc file located in the folder where Xming.exe is located.  Mine is at:
[INDENT]C:\Program Files\Xming\example_Xmingrc[/INDENT]

For additional details on how to edit the Xmingrc file, view the manual at:
    [http://www.straightrunning.com/XmingNotes/xmingrc.php](http://www.straightrunning.com/XmingNotes/xmingrc.php)

Here is my Xmingrc file:  [LINK]("http://ubuntuforums.org/attachment.php?attachmentid=62932&stc=1&d=1205801529")

I had to the edit the file using Wordpad and not notepad because of some formatting issues.

I'm not going to go through all the details of editing Xmingrc.  Here is the important part of my Xmingrc file:

```
MENU systray {
	Xubuntu		exec "C:\Program Files\innotek VirtualBox\VBoxVRDP.exe -startvm WindowsXubuntu"
	Panel		exec "C:\Program Files\PuTTY\plink.exe Xubuntu xfce4-panel & xfce-mcs-manager"
	Separator
	"Reload Xmingrc"	RELOAD
}
```

The "exec" command allows you to run applications with a hidden command prompt.  The command prompt doesn't show up on the screen or the Windows taskbar.  This means you can run a headless guest OS that's completely hidden.  This is important because Windows XP doesn't give you much control over tasks displayed in the taskbar.  (Side note: hiding tasks in Ubuntu/Xubuntu is much simpler.  You can use Compiz's "Window Rules" to hide particular windows from the taskbar/tasklist.)

I had problems with the xfce4-panel graphics.  For some reason, the xfce-mcs-manager doesn't start up correctly, so I combined the two commands with the "&" symbol.

After editing Xmingrc, I restart Xming.exe.  Right-click the system tray icon to access the custom menu defined by the Xmingrc file.  If it doesn't show up, you made an error in the Xmingrc file.  I recommnd copying and editing the example_Xmingrc file provided by the Xming installation.

Here is how I use Xming:
[INDENT]I added Xming to my registry so it starts up when I boot my Windows host.  Make sure to include the extra parameters! (":0 -clipboard -multiwindow")

After booting up my Windows host, I right-click the Xming system tray icon.  The custom menu made by editing Xmingrc should be visible.[/INDENT]
[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=62925&stc=1&d=1205800785[/IMG][/CENTER]
[INDENT]I select "Xubuntu", which runs my headless server.  It boots the guest OS in about 40 seconds, and runs in the background completely hidden (no task in taskbar and nothing on the screen).

I right-click the Xming system tray icon again and select "Panel".  I can do this BEFORE the guest OS even finishes starting up!  Once the guest OS finishes booting, the xfce4-panel kicks in (and shows up in my task bar).

I use the xfce4-panel to access the guest OS and run applications.[/INDENT]


[SIZE="5"]**SEAMLESS AT LAST!**[/SIZE]


Some quirks about my setup:
[INDENT]I can't figure out a way to use Xming to run both Xubuntu and Panel commands automatically when I start up my Windows host.

I can add VBoxVRDP.exe to the registry, and run it automatically that way, but I get that ugly command prompt in my taskbar.

So, the problem is that I need Xming's "exec" command in order to hide the command prompt, but I can't use Xming to run "exec" commands at start up.  The Xming.exe doesn't accept "exec" as an option.  It seems that the only way to use "exec" is through the right-click menu from the system tray.  If anyone figures out how to run "exec" commands another way, please let me know!

Since the headless server doesn't have a command prompt or task in the taskbar, it's weird to shut down.  To shut down the guest OS cleanly, I go into the xfce4-panel and run a terminal.  I use the command "sudo halt" to shut down the guest OS.

The font size is weird.  I think it has something to do with a dpi setting, but I fixed it the lazy way by increasing the font size.[/INDENT]


**_REVERTING CHANGES_**

[INDENT]On the Windows host, use the PuTTY and Xming uninstall programs or go into the Control Panel and use "Add or Remove Programs".

See the section of the guide on port forwarding to undo the port forwarding commands.

Use Synaptic in the guest OS to uninstall openssh-server.

On the Windows host, delete the "Xmingrc" file if you created one.

On the guest OS, delete the "~/.ssh/authorized_keys2" file if you created one.

If you added Xming to your Windows registry to run it on bootup, delete that registry entry.[/INDENT]


**_CLOSING COMMENTS_**

[INDENT]If someone could describe (and hopefully alleviate) any security concerns regarding this setup, please post and I'll integrate it into the guide with proper credits.

Post problems you have with following the guide--I'll try to update it as needed.[/INDENT]

---

### Post by HermanAB on 2008-03-18
Neat write-up.  I like Xming and PuTTY for ad-hoc stuff.

However, if you wish to make things completely automated so that you just click an icon on the Windows desktop and transparently launch a program on Ubuntu, then you would probably find it easier to use Cygwin with OpenSSH.  This way, you can write a simple little batch file and make a shortcut to it.

---

### Post by billydzuy on 2008-04-02
thank you for this awesome guide!! it works for ubuntu 7.10 too

---

### Post by atcronos on 2008-04-02
Most of this guide can also be used to do seamless on MacOS, it seams to work a lot better than it does on Windows.

---

### Post by mrmooge88 on 2008-04-30
Neat guide, I can't wait to get it to work on my pc. I am having a little trouble though.
Host: Microsoft Vista
Guest: Ubuntu 7.04
Virtualbox version 1.5.6

the emulator keeps crashing when the guest OS is loading, just before the login screen. Any ideas on the cause.

The few times that I've gotten the whole thing to load when I am trying to connect to the guest through PuTTY it says
"Network error: Connection refused"
The guide doesn't state much on how to set up the server on the guest, or is it ready to go as soon as it is installed?

Who knows this might just be vista being dumb. Thank you for the help.

---

### Post by ftmmyers on 2008-05-01
I'm having problems with this guide also...

Host:  Windows XP Pro
Guest:  Ubuntu 8.04
VirtualBox 1.5.6

Guest loads up fine to login screen, but when I try to open the connection with Putty (.60), I get an error:

"Server unexpectedly closed network connection"

Any ideas?  I'm actually guessing that it's just not yet supported for Ubuntu 8.04, but I'm too lazy to right off reinstall with a lower version of Ubuntu...........  ;-)

Thanks in advance!

---

### Post by itsjareds on 2008-10-09
Great tut :D

My only two questions now are:

1. How can I change the theme? It isn't showing my default Human theme.

2. How do I start up a Gnome session, by that I mean, how can I make Ubuntu start up seamlessly through Windows, as if that was a different monitor?

---

### Post by topry on 2009-01-15
I've been using this method with great success, but noticed that when using the PLINK 'exec' command, a single instance of plink.exe will always remain in the process list and never terminates (short of task killling it or logging out). Subsequent executions will load another instance that does unload upon termination of the X-windowed app, but that initial instance always remains in the process list.

While not a huge issue on a single standalone PC, I use this under Windows Terminal server with 50 odd clients, so the resource hit adds up quickly.

If I use execd and manually close the cmd window, the process does of course terminate - so it appears be something with the exec implementation.

Does anyone have a solution to this?

---

### Post by topry on 2009-01-15
Quick followup to above post (since editing ability has timed out). It appears this issue with the plink process is unique to FireFox. I can run xcalc (and other apps) and plink terminates normally when the xwindow is closed, but running FireFox causes it to stay in the list. I have tried it with and without passing the '&' on the commandline after FireFox. Neither Opera nor any of the OpenOffice appear to have this issue - so far just FireFox.

I have tried terminating FireFox via menu and close button, same results.

I have also tried creating a .Net application using system.diagnostics.process with the same results, so its nothing unique to the XMing exec command perse.

---

### Post by bodhi.zazen on 2009-04-27
Just a little FYI ;)

Although this is an outstanding tutorial, there is an alternate "Portable Ubuntu". It uses Colinux and is much lighter weight then VirtualBox (the Ubuntu guest uses 256 Mb RAM) and, IMO, it runs fast.

Xming is included.

See my blog for some details, as well as the portable ubuntu home page.

[http://blog.bodhizazen.net/linux/portable-ubuntu-for-windows/](http://blog.bodhizazen.net/linux/portable-ubuntu-for-windows/)

---


---
title: "running Virtualbox from the icon"
date: 2013-04-20
forum: Virtualisation
---

### Post by dlrose on 2013-04-20
I have installed and run virtualbox from a term window using sudo. I want my wife to start using my Sys76 machine but she doesn't like using term windows.

I setup a VB icon, but it launches a new VB setup.  I want to have it start the VB I have already setup and run.

I tried to setup and have it use my previous VDI disk , but it does not see it.

Did I miss something

Thanks

Darrell

---

### Post by DuckHook on 2013-04-20
It is possible that you've made things more complicated than they need to be. There is no need to run VirtualBox from a terminal using sudo and it is actually unwise and insecure to do so. Never use sudo for anything except system administration tasks. Are you doing this because you cannot launch it from the graphical VirtualBox Manager under your own account? If so, this is likely due to the fact that you did not add yourself (or your wife) to the vboxusers group (VirtualBox will only work for members of this group). To add yourself, do:```
sudo usermod -a -G vboxusers username
```where "username" is your username. If your wife logs on under her own username, you will need to repeat this step for her as well (while running in your account, not hers).

Once you've added yourself to the vboxusers group, you will be able to launch any virtual machine you like directly from the graphical VirtualBox Manager.

Creating an desktop icon is rather more complicated. It requires you to invoke the command line version of VirtualBox manager with the desired virtual machine as an argument. Let's leave that to step 2. Let's solve the immediate issue first and get you launching easily and securely. Let us know how it goes.

---

### Post by dlrose on 2013-04-20
Thane you for the information. I ran the sudo command you said and rebooted the system and I get the same GUI that asks me to create a new VB.

With out being in sudo, the command line gave me a bunch of warnings

dlrose@dlrose-Gazelle-Professional:~$ virtualbox
Warning: program compiled against libxml 209 using older 208
Warning: program compiled against libxml 209 using older 208
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28 
dlrose@dlrose-Gazelle-Professional:~$ 

When I start my VB in sudo the way I thought was right, the VB manager opens with the GUI to start my VB session

What did I miss ?

Thanks

Darrell

---

### Post by deadflowr on 2013-04-20
```
virtualbox --startvm name-of-exiting-vm
```

To create a desktop file

> [Desktop Entry]
Name = Whatever it'll be called
Exec = virtualbox --startvm vmname
Type = Application
Icon = what icon you'll be using
Terminal = false

Save it as a .desktop extension into your hidden folder > .local/share/applications in the home folder.
Or, with root, save it to the /usr/share/applications folder for use system wide, instead per users session.

There are more options to run a virtualbox use
```
virtualbox --help 
```
to see.

---

### Post by DuckHook on 2013-04-20
You are not starting virtualbox from the command line with enough parameters, so it doesn't know what you want it to do. Your code:```
virtualbox
```will just start the graphical manager. If you want it to start your actual virtual machine, then you must also tell it what virtual machine you want it to run. If your VM is called "ExAmPlE", then, as deadflowr states:```
virtualbox --startvm ExAmPlE
```...remember, case matters. The name must be precisely that of your VM.

@deadflowr

For some reason, when used in a desktop file, at least in my install, the switch prefix (--) must be left out for VBox to recognize the command, i.e.```
Exec = virtualbox startvm ExAmPlE
```and not:```
Exec = virtualbox --startvm ExAmPlE
```Don't know why. Would love to have some guru clue me in.

@OP

Setting up a desktop launcher involves some arcane twists. When you are ready, we can give you step-by-step instructions to get you set up. Just get it launching from the terminal first.

---

### Post by DuckHook on 2013-04-20
You cannot launch your VM by creating a Linux link to the *virtualbox* app. Such a link will just launch VirtualBox Manager and not your VM. To launch a VM, you must create a desktop launcher. However, do **NOT** create a desktop launcher until you get the VM to launch properly from the command line. Otherwise, it just won't work and will confuse you further.

Once you successfully launch your VM from the command line, to create a desktop launcher, do these steps:

1. Open gedit and press <Ctrl>+<n> to create a new document.
2. Copy the following text into the blank document:```
[Desktop Entry]
Name=ExAmPlE
Comment= This is the VM running ExAmPlE
Exec=vboxmanage startvm ExAmPlE
Icon=virtualbox
Terminal=false
Type=Application
StartupNotify=true
```
3. Save the document to your desktop with the name:```
ExAmPlE.desktop
```
4. A file should now pop up on your desktop called: ExAmPlE.desktop but it won't yet run. To make it executable, we must set the file execute bit. The command line method is faster but more arcane and difficult for new users to remember, so instead,
5. Open nautilus.
6. Right click on your new file and select "properties".
7. In the dialogue box, click the "permissions" tab.
8. Click the "Execute" checkbox to "Allow executing file as a program"
9. Close the dialogue box.
10. Your icon should have changed from the generic file graphic into the VirtualBox graphic.

You should now be able to launch your ExAmPlE VM by using the icon. Obviously, change the term *ExAmPlE* to the actual name of your VM. If you wish to change the graphic, you must change the label in the "Icon=virtualbox" line of the desktop script to the name of the icon you want. Again, as deadflowr says, if you want the VM to be available to all users and not just visible on your desktop, then you must either move or copy the ExAmPlE.desktop file into:```
/usr/share/applications
```If doing so, it is a good idea to change ownership of the file to root. All users will then be able to see it on Ubuntu's Dash.

---

### Post by deadflowr on 2013-04-20
@Duckhook, for me, removing the -- makes it just open the main virtualbox page.
The -- prefix, for me, launches the actual VM I want to run.
So beats me as well.

But to the OP, just read the man pages 

```
man virtualbox
```

Then create launchers after.
Launchers only need three things, a name, a command(exec), and a type. Everything else is optional.

---

### Post by DuckHook on 2013-04-21
> **deadflowr said:**
> @Duckhook, for me, removing the -- makes it just open the main virtualbox page.
The -- prefix, for me, launches the actual VM I want to run.
So beats me as well.

...another one of Linux's quirks that drives users to distraction. So, for OP:

Try .desktop file with both the switch prefix (--) and without, and go with what works for you.

---

### Post by wildmanne39 on 2013-04-21
*Thread moved to **Virtualisation**.*

---

### Post by CharlesA on 2013-04-21
Just a note: VMs in Virtualbox are ***user specific*** if you created a VM after launching virtualbox with sudo, it would be in /root/VirtualBox VMs, and inaccessible to anyone but root.

Why did you use sudo to launch virtualbox in the first place? If it's because of those warnings, they are safe to ignore.

---

### Post by DuckHook on 2013-04-21
> **CharlesA said:**
> Just a note: VMs in Virtualbox are ***user specific*** if you created a VM after launching virtualbox with sudo, it would be in /root/VirtualBox VMs, and inaccessible to anyone but root.

Why did you use sudo to launch virtualbox in the first place? If it's because of those warnings, they are safe to ignore.

Would it be okay for OP to simply *mv* the whole *VirtualBox VMs* directory from /root to /home/username followed by *chown*?

---

### Post by CharlesA on 2013-04-21
> **DuckHook said:**
> Would it be okay for OP to simply *mv* the whole *VirtualBox VMs* directory from /root to /home/username followed by *chown*?

It should work, but they will probably have to change the paths to the VDI in one of the files in .VirtualBox/VirtualBox.xml

```
 <MachineEntry uuid="some super long number" src="/path/to/VM/VM.vbox"/>
```

I did that when I wanted to move my VMs so they run under a different user. It might be easier to just export the VM and import it as the correct user.

---

### Post by DuckHook on 2013-04-21
> **CharlesA said:**
> It might be easier to just export the VM and import it as the correct user.

When I did that, Windows will detect the changed BIOS and nerf activation on the imported VM thus burning up the key.

---


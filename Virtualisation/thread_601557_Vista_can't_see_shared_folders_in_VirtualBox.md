---
title: "Vista can't see shared folders in VirtualBox"
date: 2007-11-03
forum: Virtualisation
---

### Post by rustalot on 2007-11-03
For some reason, my shared folders aren't showing up in Vista. I read the manual and everything. WHen I couldn't find the icon in the gui, I opened cmd.exe or whatever the windows command line is called, and did 'net use x: \\vboxsvr\vmshare' and it gave me System error 67: The network name cannot be found.

---

### Post by koenn on 2007-11-03
try replacing vboxsvr with its ip address (either in net use ... or in a GUI file browser address bar) & see if that works.

---

### Post by Delvien on 2007-11-04
Map it as a network drive under My Computer, much easier than cmd

---

### Post by rustalot on 2007-11-06
I can't do either, because I don't know the ip addr that vboxsvr is using, and I can't do it in the GUI because it doesn't show up.

---

### Post by Delvien on 2007-11-07
For mounting a network drive in Vista :

[http://www.vista4beginners.com/Map-Network-Drive](http://www.vista4beginners.com/Map-Network-Drive)


Or.

[http://windowshelp.microsoft.com/Windows/en-US/Help/909d569b-ed98-4176-9f7c-6eed5201ba441033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/909d569b-ed98-4176-9f7c-6eed5201ba441033.mspx)

---

### Post by cjreid on 2007-11-07
Sorry  but I must be missing something here

I have tried using the windows gui with no luck and using net use with no luck either.

I have a ubuntu host and a vista guest.

Has anyone got this to work.

Chris

:confused:

---

### Post by rustalot on 2007-11-07
My issue isn't that I don't know how or have trouble mapping network drives, it's that the Virtualbox shares aren't /on/ the network. I don't know if it's a Vista-specific issue, but because my OEM Vista Home Premium won't activate (after all, what do the commoners need virtualization for? :P), I'm going to be installing a new VM running XP pro, and I'll see if the issue persists.

---

### Post by rustalot on 2007-11-09
After making a new VM that runs WinXP, I found that the issue is probably Vista-specific, because it works fine in XP.

---

### Post by bitumen on 2007-12-05
try creating share folder on ubuntu with samba and then mapping the vista network shared folders to that after the network is operational

---

### Post by ridius on 2008-01-14
This is actually a permissions problem related to Vista's ACL... check out [http://www.virtualbox.org/ticket/799](http://www.virtualbox.org/ticket/799).

If you go to Start -> All Programs -> Accessories then right click on Command Prompt and choose run as Administrator, you'll be able to mount the share. Unfortunately, the regular user won't be able to see the share so you'll have to do everything through the Admin Command Prompt.

---

### Post by -random on 2008-04-08
> **ridius said:**
> This is actually a permissions problem related to Vista's ACL... check out [http://www.virtualbox.org/ticket/799](http://www.virtualbox.org/ticket/799).

If you go to Start -> All Programs -> Accessories then right click on Command Prompt and choose run as Administrator, you'll be able to mount the share. Unfortunately, the regular user won't be able to see the share so you'll have to do everything through the Admin Command Prompt.

that helped ! i can access the files now, a but how do a eye start 'explorer x:' with admin privelages?

edit: somehow it showed in my 'my computer' @ the sidebar when i mounted another cd.. so i'm ok, til i get another blue-screen and have 2 restart it :P lol

---

### Post by kholddagger on 2008-04-21
After reading and trying (to no avail) all solutions on the internet, I, a lucky beginner, found my own solution to this problem.

I originally had a lot of difficulty getting my network connection to work. After following the instructions straight from the manual, I got it to work, though I couldn't tell why it worked.

In Devices->Network Adapters-> , I had two adapters. Originally I only had Adapter 0 and I had no internet connection. By following the steps, I added a second Adapter. This Adapter 1 seemed to cause it to work. However, even if I unmounted it, the internet would still work. If I unmounted Adapter 0, the internet would stop working.

Now, under the conditions of having Adapter 0 working and Adapter 1 disabled (though still set up in the settings) I was able to open Computer then press <Alt> to make the bar appear so that I could go Tools->Map Network Drive... and then map \\vboxsvr\folder as my Z:\ drive.

My setup:
Host - Ubuntu 7.10
Guest - Vista Home Premium
Wireless Card - Broadcom 43xx chipset family

If you have any more questions about my VirtualBox setup please ask and if you have an explanation as to why this process worked please tell me!

---

### Post by kholddagger on 2008-04-22
In addition, I have noticed that it is very finicky and will ONLY work after I have opened cmd as an administrator and run the 'net use' line, though it returns an error message. I have tried multiple times, and it seems that this step is necessary to get the Shared Folder to be available to map.

Again, if anyone can explain this, please feel free.

---

### Post by justtech on 2008-04-29
I have no issues at all sharing a network folder with VirtualBox (Vista) and my Ubuntu.  I have installed the latest Guest Additions (Devices --> Install Guest Additions). Then I went into Users under the control panel.. went to my username, and then turned "user account control" off.  Reboot.  Open up "My Computer".. Right click on "Drive C:" and click on "Map Network Drive".  The setup that I have was "\\vboxsvr\Clients".  Just remember that before you do this that you set up a Shared Folder in VirtualBox by going to "Devices --> Shared Folders.."  Hope this helps if anyone else is needing to use Vista for anything but don't want to dual boot... (Great for troubleshooting other peoples problems without having to drive out to their location to be able to SEE what is happening).  If this doesn't work for you, let me know and maybe I can help some more.

---

### Post by trspencer on 2008-05-21
This worked perfectly...thanks.

---

### Post by justtech on 2008-05-22
> **trspencer said:**
> This worked perfectly...thanks.

NP... Glad I could help out at least one person... a "Google" more to go to repay this forum for all the help I've received.

---

### Post by ldi38 on 2008-07-01
Hello
i find the solution to access shared folder on virtual box with vista guest without turn off UAC :

In the control panel, network manage, you must activate share public folders.

I'm not sure of microsoft english terms because i have a french version.

That's all, you can use cmd with net use x: \\vboxsvr\nameshared

IvaN.

---

### Post by ofer1353 on 2008-07-24
thanks aton justtech...

---

### Post by justtech on 2008-07-24
not a problem at all... glad to help.

---

### Post by Jim_in_Germany on 2008-07-26
I had the same issue in XP. (Guest:XP, host: Hardy 8.04)
Unless I first logged on as admin I could not see virtualboxes shared folders.
After I had logged on as admin, accessed "My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders", then everything was fine and I could access shared folders as a normal user too.

I solved this by making a batch file to mount the share, containing the line:

net use x: \\vboxsvr\sharename 

(where sharename is obviously the name of the shared folder - "Files" in my case).

I then logged on as admin and added this file to be run when xp started (Start - All Programs - Accessories - System Tools -Scheduled Tasks)

That sorted things out for me. Hope it helps someone else.

---

### Post by ahumin on 2008-11-10
It seems there are multiple causes for this issue.

For me it was the fact that my vista account (an admin account) in the virtual machine had no password set. Setting even a one-letter password allowed the share to be automatically connected properly at logon as you'd expect.

I used the graphical "map network drive" wizard, available in the Tools menu of any explorer window. You can use any drive letter, like S: for shared.

---

### Post by steve19137 on 2009-12-04
i realize that this a very old thread, but i know that you can login (with vista) as the admin from the login screen. i suppose that this would allow a certain amount of stability and consistency in accessing the shared folders. i have tired that and it works.

---


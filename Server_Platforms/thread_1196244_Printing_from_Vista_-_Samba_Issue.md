---
title: "Printing from Vista - Samba Issue??"
date: 2009-06-24
forum: Server Platforms
---

### Post by freddo__1 on 2009-06-24
[LEFT][FONT=Arial][SIZE=3]I've done a bit of a search and can find people with the same problem or similar problems, but nobody seems to have a definitive solution, or one that works in my case.[/SIZE][/FONT][/LEFT]
 
[LEFT][FONT=Arial][SIZE=3]I'm having issues printing to a HP Printer connected to an Ubuntu machine from a Vista machine via the network.[/SIZE][/FONT][/LEFT]
 
[LEFT][FONT=Arial][SIZE=3]I can see the printer, add it, vista says the drivers aren't on the server, so i tried using the proper HP driver for my printer, which installs fine, and i can print a test page perfectly, but if i try to look at the job queue the status up the top says "Access Denied, unable to connect". And if i try to print from an App in vista, the print job goes through from the app, the print queue icon pops up in the taskbar, but says 0 jobs, and if you double click on it to open it, nothing happens!![/SIZE][/FONT][/LEFT]
 
[LEFT][SIZE=3][FONT=Arial]I read in another thread about using a generic driver, and tried to go down that path, but i don't have the Microsoft Colour Printer in generic, or Microsoft. I do have a MS Publisher Colour Printer in Generic, which i tried, but no luck with that.[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Arial]Is there a setting in the Samba conf file that i need to change?? do i need to set browsable = yes or something in the [print$] section?? [/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Arial]I would try and mess with some settings, but don't have the SU password for the machine its on right now...[/FONT][/SIZE][/LEFT]

---

### Post by Vegan on 2009-06-24
You will need the passwords to be able to modify the /etc/samba/smb.conf file to fix the problems.

---


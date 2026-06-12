---
title: "WINE Terminal Services configuration"
date: 2008-10-03
forum: Server Platforms
---

### Post by larsmith on 2008-10-03
I have a situation in which I need to allow multiple users to connect via a "terminal services" type connection by which they can run a windows program ( [www.frazer.biz](www.frazer.biz) ) using WINE.

The Frazer program does NOT modify system registry nor does it drop DLL files in any folder other than it's own home folder.

I will have several copies of the Frazer program installed on the server, one copy for each of my customers.  Each customer will have up to 10 employees who'll need to access their employer's copy of the Frazer program.

I'm wondering if 1) there's some terminal-services type application available for Linux whereby people can log into the server, to run the Frazer program.  Since the Frazer program is a windows-based app, we'll need to run it under WINE ... and I'm wondering if it's possible to have a per-user WINE config file, unique to each user OR group-based WINE config files which apply to groups.

---

### Post by nitecon on 2008-10-04
A very basic suggestion would be to use VNC to connect to the linux box, and create users etc for each of the customers, so that they can log into their own account.  Under each account there should be a hidden folder .wine inside that folder should be your drive_c etc.  Just copy and run your program from there.  Basically just make a shortcut to the program with the ~ switch on the desktop.  

For instance the desktop shortcut should look like wine ~/.wine/ProgramFolder/Program.exe

Test it first and let me know kind of interested in how this would work out.

---


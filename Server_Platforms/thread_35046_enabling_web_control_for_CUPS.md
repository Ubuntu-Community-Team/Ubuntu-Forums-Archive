---
title: "enabling web control for CUPS?"
date: 2005-05-17
forum: Server Platforms
---

### Post by dannysauer on 2005-05-17
So, I had some problems with my last print server machine, and need to set a new one up.  I installed Ubuntu as a server, and added the relevant cupsys packages.  After I made the necessary changes to /etc/cupsd.conf, the main page still says that administrative commands are disabled, and that I should use gnome.  Now, I have no intention of installing a full graphical desktop on this machine just to maintain the printers, and that would not work well in this environment anyway.  I need to grant several users the ability to start/stop some or all printers, and to cancel print jobs from their Windows or Mac OS desktop.  Having them do something like VNC in to another machine (or ssh in and run command-line stuff) is not gonna cut it.

Is there a configuration change somewhere that I'm missing, wherein I can enable the admin controls, or do I have to build cups myself to get rid of some patching evil?  I know that Ubuntu is billed as a desktop OS, but given the presence of a "server" install option, it seems reasonable for me to think I could use it as a server... :)

---

### Post by harryc on 2005-05-17
Just change the /etc/cups/cupsd.conf and set the daemon user to root: Put "User root" in the file. Then restart cupsys.

---

### Post by dannysauer on 2005-05-17
While access to this machine is firewalled, and I trust the users to some degree, it seems like a somewhat bad idea to change the daemon to run as root.  Is that just so it can use PAM (for /etc/passwd - PAM to get to LDAP is fine without root), or is there a bigger permission reason?

---

### Post by harryc on 2005-05-17
The Ubuntu developers have disabled administrative commands in CUPs for security reasons. I agree that the proposed solution is not optimal (or secure), but it's the only one that I am aware of. Perhaps others can give you some ideas. You may end up installing it yourself. Good luck.

---

### Post by fakier on 2006-01-30
No need to let cups run as root: (by head, so you may tune it a bit)

1. Just edit cupsd.conf to your needs. (Don't change the user/group it runs as, to root but leave/set them as their default values: lp/lpadmin. Nor change the systemgroup to something else as lpadmin). Change the access stuff so you can reach the cups server from other systems from which you want to administer cups. (Oops, **lp/lpadmin** is for Debian (my server is Debian) Ubuntu uses **cupsys/lpadmin**)

2a. Add yourselft to the lpadmin group
      # sudo adduser <username> lpadmin

2b. Add the cup**sys** 'user' to the shadow group.     (sorry, cupsys instead of cups)
     So you can assign your own printernames via the webpage on port 631, no need to use gnome-printer-admin or however that is called. [(expl.)]("http://dramor.blogspot.com/2004/12/todays-stupid-trick-on-ubuntu.html")
      # sudo adduser cup**sys** shadow

3. Change all the html pages in '/usr/share/cups/doc-root' and remove the line(s) saying it's 'protected from remote login' (or whatever it was sayin). Or leave it when the warning message doesn't bother you.
To find them:
      # find /usr/share/cups/doc-root -type f -exec grep -l "<part of message>" {} \;

4. Restart cups (if you made changes to cupsd.conf, which you should)

Done. Now you can reach the webbased configuration from another host and login with your account. ([http://server:631)](http://server:631)).

---

### Post by zappa86 on 2006-01-30
What I did was make a printer group for me. as root I ran:
```
lppasswd -g lpadmin -a myname
```
then made an account
then when I went to the control panel it worked.
ALSO!!!! If you want to access it from another computer you will need to open up your cupsd.conf file (located in /etc/cups/) and make sure to listen on the IP that is your computer (not just the 127.0.0.1, but keep that one)
Then under access make sure to put:
```
Allow From *
```
that way you can see it from anywere.

---


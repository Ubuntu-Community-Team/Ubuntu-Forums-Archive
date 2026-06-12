---
title: "rkhunter log"
date: 2013-03-16
forum: Security
---

### Post by Luddite Savant on 2013-03-16
I've just installed rkhunter & run it (under ubuntu 12.10). All looks to be ok apart from a few possible issues I'll list below. 
Reason I'm posting it I ran rkhunter in terminal & got its output, but it is saving the log to /var/log/rkhunter.log 
When I try to open this (graphically) in a text editor I get the message:

> 
Could not open the file /var/log/rkhunter.log.
You do not have the permissions necessary to open the file.

Can someone let me know how I can set the permissions on the created log file so that I'm able to access the log report?

Also in the results from rkhunter I got > 
/usr/bin/unhide.rb                                       [ Warning ]


I gather from other posts this is nothing to worry about, if so how do I whitelist it so it doesn't come up in future?

Also I got:
> 
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]


Is this anything to be concerned about?

Thanks

---

### Post by Soul-Sing on 2013-03-16
No. :)

---

### Post by maglinu on 2013-03-16
We all get that output.

To see the log use gksudo gedit.

---


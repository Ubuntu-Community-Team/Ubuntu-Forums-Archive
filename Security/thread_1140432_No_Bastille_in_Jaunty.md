---
title: "No Bastille in Jaunty?"
date: 2009-04-27
forum: Security
---

### Post by Silvr2008 on 2009-04-27
When I try to run Bastille I get:

ERROR:   'DB5.0' is not a supported operating system.
         Valid operating system versions are as follows:
         'DB2.2' 'DB3.0' 'DB3.1' 'DB4.0' 'RH6.0' 
         'RH6.1' 'RH6.2' 'RH7.0' 'RH7.1' 'RH7.2' 
         'RH7.3' 'RH8.0' 'RH9' 'MN6.0' 'MN6.1' 
         'MN7.0' 'MN7.1' 'MN7.2' 'MN8.0' 'MN8.1' 
         'MN8.2' 'HP-UX11.00' 'HP-UX11.11' 'HP-UX11.22' 'HP-UX11.23' 
         'SE7.2' 'SE7.3' 'SE8.0' 'TB7.0' 'OSX10.2.0' 
         'OSX10.2.1' 'OSX10.2.2' 'OSX10.2.3' 'OSX10.2.4' 
ERROR:   Invalid argument list:
         Usage: bastille [ -b | -c | -r | -x [ --os version ] ]
         -b : use a saved config file to apply changes
              directly to system
         -c : use the Curses (non-X11) TUI
         -r : revert all Bastille changes to-date
         -x : use the Perl/Tk (X11) GUI
         --os version : ask all questions for the given operating system
                        version.  e.g. --os RH6.0

I don't think that I got that error in Hardy. I got it from the repos too.

---

### Post by stryder144 on 2009-05-02
This is the same error message that I received today, as well.  I'm going to do some more research and post what I find later.

---

### Post by alchi on 2009-07-18
Have the same problem. Any solution?

---

### Post by grayn0de on 2009-07-21
Have you tried the most current stable 'Lenny' package? 

[http://packages.debian.org/search?keywords=bastille](http://packages.debian.org/search?keywords=bastille)

---

### Post by rookcifer on 2009-07-21
You can change /etc/debian_version to "4.0" and it will allow Bastille to run.  However, this is a very hackish workaround and I personally wouldn't do it.

Really, if you are running a desktop box, Bastille is not necessary.  Besides, you can do all of the hardening that Bastille provides manually.

---


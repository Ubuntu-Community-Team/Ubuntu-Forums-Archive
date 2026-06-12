---
title: "Online Ubuntu Services"
date: 2008-04-04
forum: Ubuntu Brainstorm
---

### Post by jda1701 on 2008-04-04
Overview:
Provide the following services to Ubuntu users via a SSO method such as OpenID:

Hardware Submission
Configuration Settings per application
Bookmarks (Firefox, Konqueror, Epiphany, etc)
Bug Submissions
Brainstorm Ideas

Details:
Implement a web frontend (i.e. online.ubuntu.com) Ubuntu users can login to.  This website will be able to store the user's computer profile(s).
A computer profile should consist of the hardware (using an application like Fedora's Smolt, or hwdb) including proprietary drivers, Ubuntu version (Kubuntu 7.10, Ubuntu 8.04, etc), and common software settings (Firefox, Pidgin, Mythtv, etc).  Software settings could consist of Bookmarks, Settings, Plugins used, preferred background wallpaper, etc.

The website should also store and link any Bug Reports the user submits via the Apport utility.  This should be linked to the hardware profile and user.  Crash logs, kernel settings, core dumps, backtraces, etc should be stored here as well for proper linking to the bug report.  If possible, bug resolution should be linked back to the user's bug report so they can see if their submission has been fixed.  The frontend for the user should follow the same guidelines as Launchpad currently does by suggesting other bugs that have already been submitted, to cut down on clutter and duplicates.  

The website should also link to Brainstorm and other Ubuntu sites that the user belongs to.

The use of OpenID and/or an Ubuntu Single Sign On service for all services would be an added benefit.  Users would no longer need separate accounts for Brainstorm (QA), Forums, and Launchpad.

Finally, a graphical application should ship with all flavors of Ubuntu that integrates jockey, apport, hwdb (or Smolt, etc) and any other gui frontends already in use to facilitate easy submission to the website.  This application should allow the selection and synchronization of software settings and hardware profiles (in the case of an upgrade, etc) manually by the user, or allow the user to automatically set synchronization settings per application.  

Privacy Note:
As some users would prefer not to submit personal information such as this online due to privacy concerns, make the feature opt-in during Installation.  Allow the user to choose whether or not to use the online service, provide a way to sign up for the service, or login to the service for a server->client synchonization during install.  

Please post comments, as I will be refining this idea for a proper submission to Ubuntu developers over the next few weeks.

This is copied from a brainstorm idea.
[[IMG]http://brainstorm.ubuntu.com/idea/6410/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/6410/)

---

### Post by skiwithpete on 2008-04-06
This is a better version of a suggestion I made
[http://ubuntuforums.org/showthread.php?t=732230](http://ubuntuforums.org/showthread.php?t=732230)

I'd like to be able to login to a website, and it knows all my settings.  That way everything is transferable, and all my computers appear to work in the same way.

Cool,

P

---

### Post by smartboyathome on 2008-04-06
This can already be done. Copy the .* folders to your usb drive, and then copy them to your new folder.

---

### Post by jda1701 on 2008-04-06
While its true you can simply copy all your .* directories from /home/username, does the average user know how to a) show these directories in a file manager and b) know which files from these .* directories to copy.

Example:  Pidgin stores its configuration and log files in ~/.purple, not ~/.pidgin.

By simply copying the ~/.* folders you also risk file structure changes between version of ubuntu.  By parsing the configuration files and saving individual settings online, and by knowing how each version of a configuration file is structured from release to release, you can more easily import these settings across versions and releases.

---

### Post by skiwithpete on 2008-04-11
What I'm saying is that if you insert a USB drive, say with the ~/.* folders in it, Ubuntu recognizes you've done so and will ask if you'd like to login to your settings.  

Of course, this would be even more convenient if you could log into a website (like foxmarks - bookmark synchronizer for Firefox) and that would import all your settings.

---

### Post by gnomeuser on 2008-04-12
Maybe look at the GNOME Online Desktop and smolt (both from the Fedora camp but valid upstream projects with good traction) for the infrastructure for this. No need to duplicate efforts and this way everybody benefits not just Ubuntu.

---


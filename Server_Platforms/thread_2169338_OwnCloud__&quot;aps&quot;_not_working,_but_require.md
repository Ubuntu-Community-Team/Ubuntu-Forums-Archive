---
title: "OwnCloud : &quot;aps&quot; not working, but required for LDAP integration"
date: 2013-08-21
forum: Server Platforms
---

### Post by koenn on 2013-08-21
I''ve installed Owncloud  on Ubuntu server 12.04, using 
this page the for preps and config checking : [http://doc.owncloud.org/server/4.5/admin_manual/installation.html#manual-installation](http://doc.owncloud.org/server/4.5/admin_manual/installation.html#manual-installation)
and installing with apt-get cfr [http://software.opensuse.org/download.html?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download.html?project=isv:ownCloud:community&package=owncloud)

It works : I went through the initial web-based config flawlessly and am now looking at a (i think)  working owncloud in my browser

Next, I want LDAP / Active Directory integration to manage authentication 
Accoyding to the documentation, I can configure that in Settings -> Apps
However, Settings -> Apps just shows me a list of "apps" but I can't seem to do anything there ; I can't enable, disable or configure any app, including the one I need, de "LDAP auth backend" app.

I've searche around, but the solutions I found online boil down to
- clear your bowser cache and try again  - did that, didn't help
- "it's not an owncloud issue, it has to do with your (server, php, apache, ...) configuration".  -- fine by me, but not really helpful

I tried fixing it by changing ownership on the owncloud directories and files to www-data. No effect that i could see
I looked for clues in apache access and error log, but saw nothing that gave me hint about what to do or where to look next.


Help ?

---

### Post by kpothi on 2013-08-24
> **koenn said:**
> Accoyding to the documentation, I can configure that in Settings -> Apps
However, Settings -> Apps just shows me a list of "apps" but I can't seem to do anything there ; I can't enable, disable or configure any app, including the one I need, de "LDAP auth backend" app.


Did you click the application? Once you click (single-click) it, it will show the details of the application on the right side of the list and will also show a button named "Enable" (or "Disable", depending on the current status of the application). I use a slightly older version of ownCloud (5.0.9), at the moment. So, things may have changed in the latest version (5.0.10).

---

### Post by koenn on 2013-08-24
oh, I clicked the apps allright. I also looked at the page source to see where the links go to and try to trigger something to work from there. No go. 

Meanwhile, I sorta figured it out :
I used the 'apt-get' method to install owncloud, which uses repos on OpenSuse's Build Services. Turns out the packages in those repos are horribly out of date : they contain a version 3 of owncloud while the current is 5. Also, the packager tried to split up the owncloud php files over several directories to keep sensitive data out of the webroot, which is a standard Debian/Ubuntu way of doing things and the main reason I prefer packages over tarbals even for  LAMP/web applications. But, apart from lagging behind in versions, I suspect this move didn't really work in this particular case and causes permission problems or broken path references in the php code.

The download page also offers .deb packages for download + install with dpkg  (in stead of repo + apt-get) : these are more recent (v5) but they have some weird dependencies (eg they depend on sqlite even if you'd choose to use mysql as db backend + they have all sort of -dev dependencies that the tarbal install doesn't seem to need), plus they install the entire application in /var/www anyway just as you would do when you do a manual install, so there's hardly any reason to prefer those .debs over a manual install.

Ah, sloppy mantenance and inaccurate documentation ... I've fired people for less ... :-)

In the end, I just started over from scratch and did a 'manual' installation - that one works, including the LDAP authentication I was after.

---

### Post by kpothi on 2013-08-24
Thanks for sharing what worked for you and I'm glad you were able to sort it out. It's true that the documentation in ownCloud is very inadequate at the moment.

Since, you fixed it, please consider marking it as [solved](http://ubuntuforums.org/showthread.php?t=2151638), when you get a chance.

---


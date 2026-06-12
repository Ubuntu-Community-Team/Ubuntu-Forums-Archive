---
title: "Why not ubuntu-server-desktop package?"
date: 2006-09-07
forum: Server Platforms
---

### Post by pressureman on 2006-09-07
If you've got an Ubuntu server that needs GNOME for running GUI server management tools (like LDAP Administration Tool, LAT), or some commercial application that requires GTK, you basically have two choices:

- install ubuntu-desktop, and download around 400MB of packages, including things like OpenOffice.org, games, multimedia apps etc

- manually install xserver-xorg, GDM, various xfonts packages, GNOME panel, GNOME applets etc the list goes on...

Why not have a meta package like ubuntu-desktop, but without the apps that are unlikely to be needed on a server? Just a bare bones GNOME install, with system utils, monitoring apps, and perhaps evince for viewing PDF manuals.

---

### Post by az on 2006-09-07
> **pressureman said:**
> If you've got an Ubuntu server that needs GNOME for running GUI server management tools (like LDAP Administration Tool, LAT), or some commercial application that requires GTK, you basically have two choices:

- install ubuntu-desktop, and download around 400MB of packages, including things like OpenOffice.org, games, multimedia apps etc

- manually install xserver-xorg, GDM, various xfonts packages, GNOME panel, GNOME applets etc the list goes on...

Why not have a meta package like ubuntu-desktop, but without the apps that are unlikely to be needed on a server? Just a bare bones GNOME install, with system utils, monitoring apps, and perhaps evince for viewing PDF manuals.


There are a lot of LDAP configuration tools available that do not use X.

Regarding the apps you mention, if any of those apps were properly packaged for Ubuntu, you would just have to install them and their dependencies would take care of bringing in the other needed bits.  You would be able to install them and run them.  So is there really a need for a meta package to overcome the shortcomings of those third-party applications?

You do not need to run them locally, either.  You can just install the application and the associated libraries as well as Xorg-client and you then can run them remotely.  No need to run an X server on the webserver for that.

---

### Post by Macchi on 2006-09-07
> There are a lot of LDAP configuration tools available that do not use X.
Which LDAP configuration tools would you recommend?


Regarding the ubuntu-desktop I would like to learn how to customize meta-packages for at least two reasons:

A) The Cups-server was somewhat difficult to configure manually on my Ubuntu printer and file server. The web interface did not facilitate the process. After spemding a couple of hours to investigate what was wrong I just got tired and installed the (whole) ubuntu-desktop. Then I could very easily setup all printers in a couple of minutes. Maintenance is also easyer, but I am sad for having to live with gnome on the server.

B) I use Ubuntu in professional environments and thus would like to have a meta-package called "ubuntu-business-desktop" that focus on professional applications like office, messaging and multimedia, but suppresses games.

---

### Post by pressureman on 2006-09-07
> **azz said:**
> Regarding the apps you mention, if any of those apps were properly packaged for Ubuntu, you would just have to install them and their dependencies would take care of bringing in the other needed bits.  You would be able to install them and run them.  So is there really a need for a meta package to overcome the shortcomings of those third-party applications?

I would have thought that to be the case, so I tried installing something fairly pivotal to GNOME - gnome-about. Package dependencies were going to pull in several other GNOME packages, but not xserver-xorg and co.

> **azz said:**
> You do not need to run them locally, either.  You can just install the application and the associated libraries as well as Xorg-client and you then can run them remotely.  No need to run an X server on the webserver for that.

I realise that, and most of the time I run headless servers with no X. In fact, most of the time I run Debian on servers. The company I'm working for at present is a very Windows-centric company, and as such are not big fans of CLI. Having a basic GUI on a Linux server gives them warm fuzzies ;-)

At the end of the day, we've really got to make the customer happy. If they don't the features they want in brand X, they'll simply go with brand Y.

---


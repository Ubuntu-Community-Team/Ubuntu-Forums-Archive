---
title: "How to determine default server?"
date: 2009-09-01
forum: Server Platforms
---

### Post by bcw on 2009-09-01
Hi,

I'm hoping people in this forum might know about this off the top of their heads...

I'm designing an application that will use a browser for its UI, but doesn't need to connect to a remote server.  It probably needs a server for some of it's features, but that will be on the user's own system, serving their private data.

I can pick one and package it into the dependencies, but what if they have already installed one?  How do I know, how do I install my new app components to whatever they might have installed (Tomcat, Apache, etc.) - perhaps without knowing it because it was part of some other application they decided they wanted.

I'd like to avoid collisions, and unsophisticated users (hopefully) will want to use my application.  What approach can deal with this?

Thanks in advance for any discussion.

Regards,
Bret

---

### Post by drave on 2009-09-01
hmm! you could 'netstat -lt' and then grep for :80 or :httpd or whatever UNIQUE signature a listening server will show, or dpkg -l and look for apache/tomcat or whatever there signature is etc

that will tell you whethere something is installed and running

can your app be so general purpose that it hooks in with whatever is found? how many different web servers are there? make it work with Tomcat/Apache and anything else is an error. put in on port 81

---

### Post by Bachstelze on 2009-09-01
You can specify several alternative dependencies for a packages by using a | symbol. For example, here's the debian/control file for [kpackagekit]("http://packages.ubuntu.com/jaunty/kpackagekit"), look at the "Depends:" line.

```
Source: kpackagekit
Section: kde
Priority: extra
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
XSBC-Original-Maintainer: Sebastian Heinlein <glatzor@ubuntu.com>
Build-Depends: cdbs, debhelper (>= 7), cmake, quilt, libpackagekit-qt-dev (>= 0.3.14-0ubuntu3), kdelibs5-dev
Standards-Version: 3.8.0
Homepage: http://www.packagekit.org

Package: kpackagekit
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, policykit-kde | policykit-gnome, software-properties-kde, packagekit (>= 0.3.14-0ubuntu3)
Description: KDE package management tool using PackageKit
 PackageKit allows to perform simple software management tasks over a DBus
 interface  e.g. refreshing the cache, updating, installing and removing
 software packages or searching for multimedia codecs and file handlers.
 .
 This package provides a package manager and a update notifier.

```

---

### Post by denver on 2009-09-01
It also depends a bit on what kind of technollogies you are planning to use (PHP, Python, Ruby, PERL, etc).

If its just static content, you can junst start a simple http server as part of your application on some random non privileged port (above 1024). Transmission torrent client has a webUI and an integrated webserver to serve the files. Ktorrent is another app that has a WebUI. You can take a look at those to get a clue on how to move forward.

Goodt luck!

---


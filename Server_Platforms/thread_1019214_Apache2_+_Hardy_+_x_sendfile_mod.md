---
title: "Apache2 + Hardy + x sendfile mod"
date: 2008-12-22
forum: Server Platforms
---

### Post by delahappy on 2008-12-22
I have been trying to figure out how to install this mod on Ubuntu.  Can anyone point me to a good resource?  I have tried installing it most recently with "aptitude install libapache2-mod-xsendfile" but when I try to enable it I get an error.  I used this to enable:

XSendFile on
XSendFileAllowAbove on

Any help would be greatly appreciated.

---

### Post by hackeron on 2009-05-07
> **delahappy said:**
> I have been trying to figure out how to install this mod on Ubuntu.  Can anyone point me to a good resource?  I have tried installing it most recently with "aptitude install libapache2-mod-xsendfile" but when I try to enable it I get an error.  I used this to enable:

XSendFile on
XSendFileAllowAbove on

Any help would be greatly appreciated.

apt-cache search xsendfile doesn't show anything. Did you manage to install it? -- I'm on Jaunty.

---

### Post by hpadrick on 2009-08-25
Install the apache dev headers:

**$> sudo apt-get install apache2-prefork-dev**

This will install apxs2 needed to compile the module.

You can compile the module as outlined here: [http://tn123.ath.cx/mod_xsendfile/](http://tn123.ath.cx/mod_xsendfile/)

It will fail with an error pertaining to httpd.conf; just igone it.

All that you need to do from here is add the module in the mods-available folder.

[B]$> cd /etc/apache2/mods-available

$> sudo nano -w xsendfile.load[/B]

copy and paste the following line into the editor:

LoadModule xsendfile_module /usr/lib/apache2/modules/mod_xsendfile.so

save the file.

[B]$> sudo a2enmod xsendfile

$> sudo /etc/init.d/apache2 restart[/B]

That should be it.

---


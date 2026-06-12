---
title: "two factor authentication GDM login"
date: 2008-10-28
forum: Security
---

### Post by rosv on 2008-10-28
Hi,
Would it be possible to use two factor authentication, such as RSA secure ID, at the GDM login for Ubuntu. Can GDM can be configured to handle a RADIUS access challenge message after authenticating successfully with a user name and password.

Thanx

---

### Post by Sarmacid on 2008-10-28
I have managed to set up Ubuntu to authenticate through a radius server on ssh, so my guess is that it would be possible, not sure how it would go tho.

---

### Post by rosv on 2008-10-28
Cool,
I've managed to do this with sshd so it should be possible to do it with GDM as well.

Right now I'm using a radius request from the GDM pam module :

cat /etc/pam.d/gdm
#%PAM-1.0
auth       sufficient   /lib/security/pam_radius_auth.so
..............

I'm able to get the RADIUS challenge delivered to my token device, but there's no text input field for it in the GDM. I guess that's the big problem here......

---

### Post by rosv on 2009-03-26
I've solved it!

The trick is to enable Gnome smartcard login.

This is what I did:
* Download and install quest-gdm and gdm-plugins from [http://rc.quest.com/topics/gdm/](http://rc.quest.com/topics/gdm/)
The two packages are only provided in RPM format. However, converting them to deb using alien will work just fine.

* Install radius client: sudo apt-get install libpam-radius-auth

* Edit radius config file /etc/pam_radius_auth.conf:
# server[ :port ]	shared_secret      timeout (s)
yourradisuserver yoursharedsecret 30


* Configure GDM to use the radius pam by editing /etc/pam.d/gdm. At the very top, add the following line:
auth       sufficient   /lib/security/pam_radius_auth.so

The configuration is now complete. When you login using GDM. You should be promted for your usernamne and password as usual. 
In addition to that, you will recieve an additional promt for some type of two factor authentication. 

The example above expects the user to respond to an access challenge sent by a radius server such as FreeRADIUS or the Mideye RADIUS server.


Read more about the PAM radius module, and it's configuration options, at [http://freeradius.org/pam_radius_auth/USAGE](http://freeradius.org/pam_radius_auth/USAGE)

Note! You may need to configure /etc/gdm/gdm.conf to provide the absolute path to the libpromptpkcs11.so module. Just read the documentation on [http://rc.quest.com/topics/gdm/](http://rc.quest.com/topics/gdm/) and you'll figure how to do it.

---


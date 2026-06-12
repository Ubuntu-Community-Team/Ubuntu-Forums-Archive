---
title: "Setup a Enterprise file and print server"
date: 2008-10-04
forum: Server Platforms
---

### Post by speedgrind on 2008-10-04
Interested to know if anyone has a good solution for setting up a Enterprise file and print server? Please give me a link to the complete documentation.

---

### Post by windependence on 2008-10-04
[http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server)

-Tim

---

### Post by speedgrind on 2008-10-04
Thanks. But what is the different between Ebox and my current Webmin setup? Is Webmin already a complete server configuration? I would like to have an environment like what Windows Active Directory has. All user will have to authenticate to domain/server then only they can use the resources. They will need to have the rights in order to access the file specified by administrator. They will be also be category into groups. Please advise.

---

### Post by cariboo on 2008-10-04
Ebox is still a work in progress as far as I can tell, every  time I have a look at it the have added new features. I would stick with webmin if you are alresdy familiar weith it.

Jim

---

### Post by speedgrind on 2008-10-05
Does this means that Webmin is more powerful that Ebox and that Webmin alone is enough for what is required to configure and monitor a server? By the way, does anyone has any idea how to setup a VPN connection with server?

---

### Post by Drezard on 2008-10-05
Google "openVPN" for the VPN connection. 

In regards to Ebox or Webmin, its a matter of opinion. Its which one you are more comfortable with. And last but not least, yes webmin should be fine for monitoring a server. I guess it depends all on what you wish to 'monitor'. If I was you I would also set up SSH access, just incase all goes to hell and you need to get shell access to the server.

Daniel

---

### Post by lykwydchykyn on 2008-10-05
Instead of connecting to cups directly, you can publish the cups printers via samba to make use of users/groups permissions.

Other solutions involve ldap or nis, but samba is pretty easy to get going with.

---

### Post by speedgrind on 2008-10-06
What is the different between SAMBA, NIS and LDAP? Are they doing the same thing like what Microsoft Active Directory do? What makes them different?

---

### Post by lykwydchykyn on 2008-10-06
They share *some* of the functionality of Active Directory, basically:

 - NIS is a fairly old directory services implementation, you can use it for centralized authentication for things.  It's mostly deprecated because it's not terribly secure, but some people still use it in special situations.

 - LDAP is a very generic directory server.  Active Directory and Novell eDirectory are both based on LDAP with lots of special configurations and templates and so forth.  In Linux you can install OpenLDAP, an open source implementation of LDAP.  It's fairly generic and "roll your own", though, so if you're expecting lots of wizards and templates and policies and so forth OpenLDAP will disappoint.

 - SAMBA is usually thought of as a file sharing format, but actually it's an attempt to reimplement the entire Microsoft networking stack.  It's currently capable of emulating a pre-win2k Microsoft NT Domain, and can be integrated into Active Directory.  

I suggested these because it sounds like you want your file and print server to have centralized user logins and permissions on things.  In order to do this, you ideally want some kind of directory service so that you can associate users and groups with network resources.  These three things allow you to do this.  Of the three, I'd say samba is probably the easiest to get going, and pretty popular.

---

### Post by speedgrind on 2008-10-07
Yes. I do agree with you. But I, myself have been using Novell eDirectory and would like to have some implementation with this kind. What is the different between LDAP and openLDAP? Does anyone know if there are solution for Ubuntu which is similar to Novell eDirectory?

---

### Post by lykwydchykyn on 2008-10-07
LDAP is a generic standard for directory services, openLDAP is a free implementation of it.

I'd like something like that too, but so far as I can tell it doesn't exist, at least not for free or without a lot of setup.  You can also check out Fedora directory services or one of the many front-ends for openLDAP, but I have yet to find an integrated solution like eDirectory or Active Directory.

---


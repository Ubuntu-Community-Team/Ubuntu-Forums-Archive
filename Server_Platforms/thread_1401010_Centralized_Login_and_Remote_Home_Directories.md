---
title: "Centralized Login and Remote Home Directories"
date: 2010-02-07
forum: Server Platforms
---

### Post by cldfzn on 2010-02-07
In my desire to learn, mess around and set up something useful on my home network, I'm looking for something that can do centralized login and remote home directories.  When someone in my family logs in to a computer, windows or linux based, I want them to be able to use their credentials, then have their remote drive mounted and ready for use.  I've looked over ldap solutions, attempted to set up an OpenLDAP server and realized I have no idea what was going on.  Is an ldap implementation the proper way to go for my desired solution or am I barking up the wrong tree?  I've just now set up OpenDS on a VM for testing but I need to do some research there.  Any ideas, suggestions, howto's, all will be welcomed.

---

### Post by HermanAB on 2010-02-07
Howdy,

Since you mention Windows, you don't have much choice in the matter.  Go to the Samba web site and read up on their Win2000 compatible Active Directory server.

---

### Post by Vegan on 2010-02-07
Windows 2000 is EOL. Samba has been updated however.

---

### Post by senor_smile on 2010-02-08
> **cldfzn said:**
> In my desire to learn, mess around and set up something useful on my home network, I'm looking for something that can do centralized login and remote home directories.  When someone in my family logs in to a computer, windows or linux based, I want them to be able to use their credentials, then have their remote drive mounted and ready for use.  I've looked over ldap solutions, attempted to set up an OpenLDAP server and realized I have no idea what was going on.  Is an ldap implementation the proper way to go for my desired solution or am I barking up the wrong tree?  I've just now set up OpenDS on a VM for testing but I need to do some research there.  Any ideas, suggestions, howto's, all will be welcomed.

I would recommend using ebox.  It takes care of the openldap set up and makes setting up a windows directory server a piece of cake. I have used it a few times already.  Make sure to use the stable 1.2 version, as the newer betas definitely have problems, in my experience.

---

### Post by cldfzn on 2010-02-08
eBox looks quite nice, thank you the suggestion.  I'm still going to end up trying to figure out how to connect my boxes to an opends/openldap server for the fun of it.  So if anyone has any nice howto's or anything that would be nice. Thank you

---

### Post by cldfzn on 2010-02-08
After trying out eBox, I'm not terribly impressed.  I've got a working bind/dhcp ddns setup going and eBox seems to struggle doing even that.  The simplified ldap setup seems nice although I see no options for setting up automount through its gui, which defeats the purpose.  If I'm missing point it out, and any other suggestions would be nice.  For the time being I'm thinking about attempting to set up ldap since I only have one windows computer.

---

### Post by senor_smile on 2010-02-08
> **cldfzn said:**
> After trying out eBox, I'm not terribly impressed.  I've got a working bind/dhcp ddns setup going and eBox seems to struggle doing even that.  The simplified ldap setup seems nice although I see no options for setting up automount through its gui, which defeats the purpose.  If I'm missing point it out, and any other suggestions would be nice.  For the time being I'm thinking about attempting to set up ldap since I only have one windows computer.

The automount of network shares would be taken care of by putting a logon.bat file under the netlogon folder.  I remember seeing a full tutorial for setting up a working pdc using ebox on howtoforge.com.  I will post the link later when I'm not on the cell.

---

### Post by bryanshook on 2010-02-09
I've been looking into this today as well.  The best results for Windows single sign-on is Samba 4 which is still in development.  Apparently it functions.  Could be something interesting to try.  Definitely not for the faint of heart.

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

---


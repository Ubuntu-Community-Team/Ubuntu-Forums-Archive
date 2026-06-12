---
title: "&quot;Sharing&quot; folders from non-PDC Ubuntu box"
date: 2010-11-21
forum: Server Platforms
---

### Post by biscuit314 on 2010-11-21
I have several computers, some Ubuntu and some Windows. I have an Ubuntu machine acting as PDC (Samba + OpenLDAP). 
 
When I create a Samba share on the PDC, everyone can see it, whether accessing it from a Windows box or an Ubuntu box.
 
Any share created on a Windows box is similarly accessible to anyone.
 
My problem is: for any Ubuntu to Ubuntu file transfers I've been using SSH. I've not needed to share folders from a non-PDC Ubuntu to Windows until now.
 
I presume I have to install Samba on the non-PDC Ubuntu box and create samba shares. My attempts to allow Domain Users access to these shares have not been successful. To my shame I went setting happy - setting this, changing that... At one time I was able to "net view" to the Ubuntu box from Windows and see the share. Any attempts though to connect to that share failed on permissions. 
 
Is there a guide which will help me figure out how to open a samba share on Ubuntu box B when Ubuntu box A is a PDC, such shares accessible to Windows machines who are part of A's PDC (and users created in the PDC's LDAP)?

---

### Post by Ryan Dwyer on 2010-11-21
If I understand you correctly, you want the non-PDC server to authenticate login requests from Samba clients using the PDC.

You need to set security = domain in smb.conf and join the non-PDC server to the domain.

Read the section titled "SECURITY = DOMAIN" here for more info:
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#security](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#security)

---

### Post by biscuit314 on 2010-11-21
Yes, you understood correctly (I shouldn't post tech questions past my bedtime)
 
Short version:  It now works.
 
Long version...
But I didn't do anything that should have worked!
 
In preparation to use your advice I thought it best to uninstall/reinstall samba.  When I apt-get --purge samba, I was surprised the smb.conf file was still there.
 
Oh well, I reinstalled samba, a message appeared offering me a set of choices to deal with the existing smb.conf.  I selected "use package installer's version" thinking it would overwrite my debris.
 
When I opened the smb.conf file to set security=domain I was surprised by what I found:  the workgroup was already set to my domain name, and my previously created share was there too.  Gone was a bunch of crap I was experimenting with.
 
I made the change but before restarting samba I tried connecting to that share.  And it worked!  
 
On the PDC I see that the computer account was created.  This must've happened during my poking around with some webmin settings.
 
So reinstalling worked, but I'm not sure why.  For now I'm going to move on to other things, but for future reading I have noted **Ryan Dwyer**'s link plus the following
 
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[http://www.linuxforums.org/forum/servers/114983-connecting-domain-controlled-samba.html](http://www.linuxforums.org/forum/servers/114983-connecting-domain-controlled-samba.html)

---


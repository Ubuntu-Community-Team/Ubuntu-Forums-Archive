---
title: "Web-based Sever Management Tool"
date: 2011-10-29
forum: Server Platforms
---

### Post by jmacgowan on 2011-10-29
I am interesting in writing a web-based server management tool, but I'm not sure which language would be best(PHP vs Perl).  Here is a basic list of features that I need:

1.  Change Network interface settings (ability to pick static or dynamic, and set each)
2.  Enable/Disable DHCP and set simple parameters (IP and scope)
3.  Manage users and user permissions
4.  Set up restrictions on SAMBA shares
5.  Modify Preset firewall rules (Meaning hardcoded switching of allow SSH, deny FTP etc)

I realize that webmin exists (and I use it quite a bit myself), but unfortunately it doesn't meet my needs.  Specifically the part about easily managing user permissions on SAMBA shares. (I realize that you can in fact use webmin for this, but the end-users I am developing this for find the process to confusing)

Just in case anyone is familiar with it, what I am going for is something similar to the Toshiba SG20's web interface.

So, down to the question.  Should I write this in PHP or Perl?  While I have plenty of experience with PHP, I have read that running system commands with elevated privileges can be a pain.

Would learning/using Perl make changing the system settings I need to change any easier?  Or is it just as much of a pain?

***Please note that this management tool will not be used to administer the box remotely.  It is purely for local users to be able to easily change settings if they need to.

Thank you for your input!

---

### Post by volkswagner on 2011-10-29
Take a look at [ClearOS]("http://www.clearfoundation.com/Software/overview.html").  The WebInterface works well and has all the features you mention (not 100% sure on the ip address change).

---

### Post by jmacgowan on 2011-10-29
Wow... ClearOS just might be the answer!  Thank you!

---

### Post by volkswagner on 2011-10-30
I guess I should have also mentioned[ Zentya]("http://www.zentyal.com/")l I believe it is Ubuntu based, although it is not easily recognized as such.  I tried it in a VM briefly, but it seemed t use more overhead.  I did not see any obvious way to install without a GUI.

---


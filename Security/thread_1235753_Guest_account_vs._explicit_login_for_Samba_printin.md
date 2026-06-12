---
title: "Guest account vs. explicit login for Samba printing"
date: 2009-08-09
forum: Security
---

### Post by ladasky on 2009-08-09
Hi folks,
 
I just succeeded in making file and print sharing work on my home network!  \\:D/
 
However, it occurred to me that one of the things I did to make it work is a potential security risk.  I'd like to ask you folks whether, and how, I should change it.
 
Here's the situation: I've configured my Ubuntu 8.04 desktop to share a printer and some files, using Samba server.  One of the client machines is my wife's Mac OS X laptop, which leaves the house on a regular basis.
 
I don't mind requiring the user of the laptop to enter a user name and password manually, in order to access file sharing.  I'm the only person who would need to do that.  However, when it comes to printing, I would prefer that my wife did not have to bug me every time she wants to print.  I want her to be able to just send the job to the print server with a single click.
 
For the moment, my wife's machine has been granted the keys to the city.  It connects this way:
 
```
smb://user:password@server/printer_name
```
 
The problem I have with this is that there is currently a clear-text copy of my server's user name and password on her laptop, which roams.  That doesn't sound safe.

I see vague references to guest accounts in the Ubuntu docs.  Should I use one?  Can I grant printing access through a guest account?
 
Under System > Administration > Users and Groups I found the provisions to add accounts, and the various privileges you can grant a user, .  But I don't see "use shared printers" explicitly listed among those privileges, which makes me think that I'm missing something important.  "Manage printers" may or may not be the same thing.  Ubuntu defaults to denying that option, while granting what seem to be more obscure privileges such as "Use audio devices" and "Monitor system logs."
 
Thanks for any help!

---

### Post by ladasky on 2009-08-12
Sorry to do this, but...
 
[SIZE="3"]**< bump >**[/SIZE]
 
If I don't get a reply here, I guess I'll try General Help next.

---


---
title: "Ubuntu: Domain Controller, Active Directory, &amp; Group Policy"
date: 2006-12-26
forum: Server Platforms
---

### Post by XP1 on 2006-12-26
Is it possible to have a Domain Controller, Active Directory, & Group Policy all under Ubuntu?

Should I download Ubuntu or Ubuntu Server?

Would I have roaming profiles?

I want to have a Ubuntu Domain Controller and Windows XP clients connecting to it with Windows Group Policy applied.

I've heard of Samba but I'm not really sure what it can do. If I install Samba, will it allow me to do those things?

---

### Post by Brazen on 2006-12-26
I would suggest using Ubuntu Server.  It will not give you a gui, but for a server, going gui-less has many advantages and you'll be thankful you got comfortable with the command line.  I think the Ubuntu docs have some good starter information on Using the gui-less Ubuntu Server.

Samba is indeed the application you will want to go with.  Samba provides three things: a domain controller, a file server, and a print server.  You use 1, 2, or all 3 of these roles on one server.  If you search for 'Samba PDC', either in the Ubuntu wiki or out on the web with Google, you should find some information to get you started.

Also, you will not exactly have Active Directory.  Active Directory is, to put it simply, what Microsoft calls their domain controller software, so essentially you will be using Samba instead of Active Directory (there is more to Active Directory than this, but that's the basic idea).  As for group policy, I'm not exactly sure how Samba works with Group Policies.  I think it can do some group policy functions, and then there are add in software packages that can add more of the group policy-like features to Samba.

---

### Post by jonathan.lees on 2006-12-26
Another option is to set up OpenLDAP on Ubuntu and have the XP clients authenticate against that. You will have to have local group policies. I'm not sure about roaming roaming profiles, aren't they created by the workstation and then placed on a share?

Here's a link to a book that covers this topic pretty well: [http://www.amazon.co.uk/Linux-Windows-World-Roderick-Smith/dp/0596007582/sr=11-1/qid=1167147944/ref=sr_11_1/026-4942181-9866068](http://www.amazon.co.uk/Linux-Windows-World-Roderick-Smith/dp/0596007582/sr=11-1/qid=1167147944/ref=sr_11_1/026-4942181-9866068)

Also here's a link for a howto Samba as a Domain controller, it's for Breezy 5.10 and Samba but should map to current versions.
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

OpenLDAP is another story though...

Jonathan

---

### Post by Brazen on 2006-12-26
You can do roaming profiles with Samba.  I have no idea where the setting is for that though, cuz I prefer to just redirect the My Documents folder instead.

---

### Post by XP1 on 2006-12-26
Ok, thanks for the replies. I'll give Samba a try.

---


---
title: "Ubuntu for Small Businesses"
date: 2007-06-27
forum: Server Platforms
---

### Post by Alterax on 2007-06-27
I'm getting ready to do my first custom spinoff of Ubuntu, geared toward small businesses, much like Microsoft's Small Business Server.

Here's what I'll be using for it:
Ubuntu (Desktop version, only because of a GUI for less-skilled site administrators)
Citadel (Groupware service comparable to Exchange)
SugarCRM OpenSource version (Customer Relationship Management Database)
Alfresco (for building internal sites, kind of like MS Sharepoint)

Any ideas on other things that small businesses may need?  Also, any recommendations on programs that can help by generating customer bills, etcetera?  If I can get this going right, I can throw it into an .iso for any of you that want to use it.

--Alterax

---

### Post by Soarer on 2007-06-27
Webmin for server admin?
Firewall (I like Shorewall)?
Proxy (like Squid)?
Wiki (maybe Alfresco covers it?)
Automated backups?

Some of these are included as standard of course...

---

### Post by Alterax on 2007-06-27
None of that would be difficult to build in.  Thanks for the pointers!

--Alterax

---

### Post by ckempo on 2007-06-27
Post back how you get on. Am sure I'm not the only one here who would be interested in this.

---

### Post by HalcónMaltés on 2007-06-27
I'm myself up to a similar task. I'd love to see you blogging your way in. :D

---

### Post by dthacker on 2007-06-27
I like tikiwiki for a multi-function wiki tool.  YMMV of course.

---

### Post by amlucent23 on 2007-06-27
you may want to throw in some sort of gui LDAP config program.. I have no suggestions about which program or even if it exists but admins like "AD users and computers".. for small/medium businesses that want AD or something similar.

Also a thought, you may want to include FreeNX server in the install since you are supplying a DE. You could just leave it with VNC, but its dog slow and a admin will spend most of his life remoting into that box. Then he will say he doesn't like it because it isn't as fast as RDP.

---

### Post by az on 2007-06-27
> **Soarer said:**
> Webmin for server admin?


Webmin would have to work for it to be used.  It is horribly broken.

> **Alterax said:**
> I'm getting ready to do my first custom spinoff of Ubuntu, geared toward small businesses, much like Microsoft's Small Business Server.


Check out SOHObuntu.

[https://wiki.ubuntu.com/UbuntuEasyBusinessServer/](https://wiki.ubuntu.com/UbuntuEasyBusinessServer/)
[https://launchpad.net/sohobuntu/](https://launchpad.net/sohobuntu/)

It's a google summer of code project, too.

---

### Post by chris.zeman on 2007-06-27
> Webmin would have to work for it to be used. It is horribly broken.

It is? Mine works great! I install the minimal version and only the modules I need.

Chris

---

### Post by Alterax on 2007-06-27
Looks like the SOHO distro beat me to the punch.  Love it.  So maybe I should look into working with them instead.

--Alterax

---

### Post by Shibby73 on 2007-10-06
I am a big fan of FOS... and Linux especially Ubuntu... I am a long-time Windows user.

I think you ought to check out:
[www.firstclass.com](www.firstclass.com)

Firstclass is a superior business/collaborative solution that unifies many feature rich abilities and runs on any operating system.  The unified office idea is really cool too... essentially a firstclass server can handle voicemail, fax, e-mail, and paging, in one place as well as online content and collaborative work spaces that are accessible from anywhere with rich shared tools (conferences, chat, calendars, file, messaging, etc).  The internal structure is highly secure to groups of users and to the individual user, permiting users to even self-administer their own work environments with customizable permissions to other users.  A monkey can do it.... it was originally designed for K-12 educational environments so kids can do it too.

Microsoft and Sharepoint in particular is hurting Firstclass.

Why reinvent the wheel... make things that work with Firstclass and add to or complement its functional abilities.

IF you want to see Firstclass in action or see what it is like inside as a user let me know.
I can get you a user license for a period of time on my server.

I applaud your work effort here... we all need more smart people like you working on things that are useful to everyone and bring freedoms such as the ability to work from any OS.
My server is professionally maintained and backed up daily.

[www.stansgnosticus.net](www.stansgnosticus.net)


-Steve (Shibby73)

:)

---


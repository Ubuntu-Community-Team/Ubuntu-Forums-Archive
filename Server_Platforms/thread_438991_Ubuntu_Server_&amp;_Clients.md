---
title: "Ubuntu Server &amp; Clients"
date: 2007-05-10
forum: Server Platforms
---

### Post by truth on 2007-05-10
Hi everyone, i am a System Admin. of a small company with about 60-100 Client/End-Users & about 9-12 Application/Data Servers.   My boss had me  install and test Windows Vista & Windows Longhorn Server, My expeirence with these OS's  amounted to CRAP!! i mean serously crap, Vista & Longhorn offer no real improvement in my opinion other than a Fancy little GUI that some people seem to like, but I HATE along with the Icon Theme. Anyway enough about Windows "CRAP" Vista/Longhorn.     if i was looking at Ubuntu to replace Client Computers that doesnt seem like too much of a promblem, but what does seem like a promblem is   how do i replace something like Active Directory?  this is the Core of Windows Network OS. How can i get something similar in Ubuntu, where i can control Client Configurations, Access & Rights.  

Also. . .why does Ubuntu Server only have a command line?  

Isn't it much much easier to manage a server through a GUI? well i guess im use to the Microsoft Windows Server way, but i like it and its easy on the Admin. and still have the option of using the CMD when needed!

im looking forward to your response Thx you!

---

### Post by baastie on 2007-05-10
Hi,

hmm, maybe not the reply you are looking for, but why don't you have a look
at the Novell Open Workgroup  Suite ( OWS ) for linux.

It contains, SuSE SLES 10, Novell eDirectory ( your Active Directory replacement ), GroupWise 7 ( your Exchange replacement ), Novell SLED 10 ( Novell SuSE Linux Desktop ), ZENworks 7 ( complete management tool voor Linux & Windows desktops and more ) and Open Office Novell Edition ( enhancements on vbs scrips, startup time etc ). And the pricing in comparision to MS is a joke.

If you would like to have it on Ubuntu, than you could have a look at Openldap and Samba. But if you search the posts in this forum there is a lot of disagreement on this, in terms of calling it a AD replacement.

There is however a cool zimlet extension to the Zimbra messaging suite ( [www.zimbra.com](www.zimbra.com) ) which runs on Ubuntu which can give u a GUI for using Samba userbase togehter with the Zimbra LDAP userbase.
So you still have one point of management. 

The Zimbra suite comes in a opensource option or if you would like a paid version.

Cheers,

---

### Post by Aberrix on 2007-05-10
There are some good AD replacements for linux out there, I can seem to recall any of the names off the top of my head. I know from what I've heard the commercial products might offer better results than the open source ones. The one I heard great things about started with a 'Z'... I really wish I could remember the name, I am sorry.

**EDIT:** yeah, 'Zimbra' that is it!

As far as the command line, you don't need a GUI. I've never had a GUI on any of my linux servers, never needed them. Plus they just take up more resources, once you learn to use the command line (it takes some learning) you'll find it more productive than a GUI. but if you still need a gui, its just a simple matter of doing a 'sudo apt-get install desktop' and BAM! you have yourself a GUI.

---


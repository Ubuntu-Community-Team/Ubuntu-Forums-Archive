---
title: "Ubuntu security update blocks bind sockets tcp-ports 0...1023"
date: 2014-01-22
forum: Security
---

### Post by nosp4m on 2014-01-22
[COLOR=#333333][FONT=Ubuntu]Hi all,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]does anybody know a solution for this:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We have several ubuntu servers for two years now and the automatic installation of security updates is enabled. There was never a problem with the updates. Besides the servers work like a charm. But there was a security update that came on 01/03/2014. With this update the server application IBM Domino does not start several services anymore. These services (http, smtp, ldap...)try to bind sockets to the tcp-ports in the range of 0 ... 1023. I now found out that this is not possible if the software does not run as root([http://www-01.ibm.com/support/docview.wss?uid=swg21097534](http://www-01.ibm.com/support/docview.wss?uid=swg21097534) ). The last two years this was not a problem. There is a tool within the domino server called bindsock that did this job(change from normal user to root and bind the sockets). But this does not work anymore. And there seems to be no way to diagnose this problem for a normal user ([https://bbs.archlinux.org/viewtopic.php?pid=1356197](https://bbs.archlinux.org/viewtopic.php?pid=1356197) ).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]So here come my questions:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]What is the cause of the problem that it is not possible for the IBM Domino server to bind sockets?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]When there is now no workaround for the problem will there probably be a further update that will correct this problem?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I love Ubuntu and it would break my heart if I should search for another linux distribution. :([/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Please help me.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thank you for any hint in advance.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Regards[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Andreas[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]PS: The version of ubuntu is 12.04.03 LTS...[/FONT][/COLOR]

---

### Post by TheFu on 2014-01-22
The 2nd link says that the kernel issue has been fixed in Ubuntu. Have you patched recently?
Exactly which kernel is the issue inside? Is a newer version available?

[http://www-10.lotus.com/ldd/ndseforum.nsf/xpTopicThread.xsp?documentId=485F5F092833BCBE85257C33006AC7A3](http://www-10.lotus.com/ldd/ndseforum.nsf/xpTopicThread.xsp?documentId=485F5F092833BCBE85257C33006AC7A3) says the fixed kernel has been released already.

---

### Post by nosp4m on 2014-01-22
Oh, there was an update on this thread in the arch linux forum. I didn't see this. Thank you. 

There wasn't a kernel update since 01/03/2014. It is the kernel version 3.2.0-58, the kernel version 3.2.0-57 is working perfectly.

---


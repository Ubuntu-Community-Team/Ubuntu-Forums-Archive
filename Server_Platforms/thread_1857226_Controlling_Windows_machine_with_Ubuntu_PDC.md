---
title: "Controlling Windows machine with Ubuntu PDC"
date: 2011-10-09
forum: Server Platforms
---

### Post by maverickaddicted on 2011-10-09
I have 12 Windows machines, 10 Ubuntu machines. I have configured one Samba PDC on Ubuntu 11.04 server edition. Now, I want to control all of my Windows and Ubuntu machines, right from my PDC, such as installing softwares, running virus scans, configuring users, running updates, etc.
Is there any way I can do that?

---

### Post by papibe on 2011-10-10
You can ssh to the Ubuntu machines. A command line connection can give you all the tools you need for most admin tasks.

As for Windows, if they are 'Professional' or above versions, you can use the application called 'Terminal Server Client' to connect graphically.

Just some ideas. Does that helps?
Regards.

---

### Post by maverickaddicted on 2011-10-12
Thank You for your idea. I am already using VNC Viewer, but it is like a remote desktop connection. I want something, which will help in monitoring purpose as well without disturbing the users.

---

### Post by maverickaddicted on 2011-10-24
Is there any other way to deploy updates to all machines?

---

### Post by newbie-user on 2011-10-24
I'm not sure that you can fully administer Windows clients from an Ubuntu server.  I've never seen any documentation on pushing Windows updates from an Ubuntu server.  I believe that functionality is gained only from Windows servers.

[http://social.technet.microsoft.com/Forums/en-AU/winserverwsus/thread/ea9162c8-920e-4c2b-86a7-a86f73d6ef06](http://social.technet.microsoft.com/Forums/en-AU/winserverwsus/thread/ea9162c8-920e-4c2b-86a7-a86f73d6ef06)

---


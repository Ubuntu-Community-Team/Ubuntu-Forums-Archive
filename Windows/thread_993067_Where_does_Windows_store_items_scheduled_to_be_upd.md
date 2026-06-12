---
title: "Where does Windows store items scheduled to be updated?"
date: 2008-11-25
forum: Windows
---

### Post by DouglasAWh on 2008-11-25
I have a situation where every time I reboot a machine it loses a certain functionality. This functionality is hardware support for the primary use of the machine, but I really don't think that's worth getting into. If I do a system restore, that functionality returns, but then the next reboot causes the problem. I feel like it's likely the machine is getting reset to update on next reboot. This machine should never have to be rebooted, but occasionally there are weird errors that force a reboot. We have two other machines with the exact same set up and function (as far as we can tell) that do not have this problem.

---

### Post by Coreigh on 2008-11-25
There is a tool available from Microsoft developed by System Internals call autoruns.
[http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx]("http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx")

It will find and identify anything that is scheduled to run at startup and login time.

In addition it may not be something that runs at startup but *fails* to run that you need to solve. You said it is some type of hardware functionality so maybe a driver is not getting loaded or a service is not configured to start at boot time. Try to identify what it is that runs when you do your restore and set it to run at system start.

---

### Post by bmathis on 2008-11-27
msconfig will list everything. Go to Start > Run > msconfig and click on the Startup tab.

---

### Post by DouglasAWh on 2008-11-27
no, msconfig does not list what I am talking about.  msconfig only lists services and programs to run at boot.  I am talking about when the updates have already been downloaded and "installed" but they don't really get installed until the next boot.  

Just to give perspective on my question, 90% of what I do at work is Windows support, so in general I know what I'm talking about when it comes to Windows. My point is not to be snooty, it's just to draw attention to the fact that this is a very specific and unusual use-case.

---


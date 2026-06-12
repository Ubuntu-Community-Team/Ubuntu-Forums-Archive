---
title: "Remotely Accessing a Computer in Order to Perform Operations in the Background"
date: 2015-05-13
forum: Ubuntu, Linux and OS Chat
---

### Post by professor_universe on 2015-05-13
I'm doing some work on a couple of computers at an office that are running Windows 7. Unfortunately, both computers that I will be working on will be occupied while I'm performing the work, and I cannot work on them after hours due to the sensitivity of the information on the machines. Therefore, I am trying to find a way to work on them without interfering with the users. I would use Windows RDC, but that would interfere with their work since I would just be taking over their pc remotely.

So I was wondering if anyone had ideas on ways I could remotely access the computers on this network and be able to perform the scans and such that I need to without disturbing those users? I run a few different operating systems (e.g., Windows 8.1, 10, Ubuntu 12.04, and 14.04 beta). Any suggestions would be greatly appreciated.

---

### Post by ian-weisser on 2015-05-13
'doing some work' covers a lot of territory.
What do you need to accomplish that cannot be done through ordinary ssh?

---

### Post by professor_universe on 2015-05-14
Sure, that was quite vague. I'm doing some much needed cleanup on these computers, so I will need to be able to download programs (e.g., malwarebytes, adwcleaner, ccleaner, etc.) and run scans with these utilities. I'll also need to be able to examine the file system, processes, start up applications, etc.; and also be able to view and delete programs.

Can this be accomplished through ssh? I'm usually able to work on computers directly, so I have little experience with ssh, but if you think it'll work I'm not computer illiterate so I should be able to figure it out.

---

### Post by ian-weisser on 2015-05-14
So...you're going to run these Windows applications on Windows systems? I'm still confused - how is Ubuntu related to this?

I suspect that whomever is prohibiting you from doing the work after hours will need to make an exception to their policy.
Systems that both 'need to be cleaned out' but also 'contains sensitive information' and does not seem like a good combination.

---

### Post by QIII on 2015-05-14
To do much of what you are talking about on Windows 7, you would likely need desktop access.  Unfortunately, none of the Windows 7 products allow for concurrent user desktop connections.  That takes a server product.

The EULA provides for concurrent connections only for file services, IIS, internet connection sharing and telephony.

That is, you could add, delete and move files, but you can't get to the GUI desktop utilities for installing/uninstalling software.  If you know how to do that from cmd, you might still be in a gray area.

Ubuntu is related to this because there are near-native RDP Utilities like remmina and proprietary software like NoMachine that allow one to create a remote desktop to interact with a Windows machine.  That's how I interact with my Windows machine at home.  However, the proscription against multiple concurrent logins still applies.  One user logged in, one desktop.

---


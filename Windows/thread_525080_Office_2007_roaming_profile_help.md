---
title: "Office 2007 roaming profile help"
date: 2007-08-13
forum: Windows
---

### Post by adampyre on 2007-08-13
Hello,

I feel awkward asking a Windows question here, but this forum has been so extremely helpful with Ubuntu I thought I'd give it a shot.....

We are running into a problem at work with Office 2007 and the QAT (Quick Access Toolbar). With our setup, everyone logs into a Citrix server farm via a Win Term with a roaming profile. Well, if a user makes a change to the Quick Access Toolbar in any of the office programs and they log out and log back in, it reverts to it's default settings. We've narrowed it down to that Office uses a ".QAT " file to store this customization and it saves it on the persons session to a folder chain in their local settings folder. The problem is, the local settings folder doesn't copy back to the permanent profile for the user. I have created a script that does this but for security purposes we don't want to view this script as a long term fix.

In short, does anyone know where in the registry, if there is a place, I would be able to change where Office saves the .QAT config file?

Thanks.

- Adam

---

### Post by Pumm4 on 2007-08-30
Try this ...

C:\Documents and Settings\<your ID here>\Local Settings\Application Data\Microsoft\Office

...or Start > Search for *.QAT

---


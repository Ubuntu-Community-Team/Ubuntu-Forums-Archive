---
title: "Eclipse Error - Security Component?"
date: 2008-04-28
forum: Security
---

### Post by TMcKSmith on 2008-04-28
When I start Eclipse (3.3) and select a Workspace it gives me this message:

Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

I looked this up and only found one solution:

create

/home/thomass/.mozilla/eclipse

directory


This did not work for me. Has anyone else run into this problem?

---

### Post by rwales on 2008-04-29
I had exactly this problem when trying to run Eclipse 3.3.2 64bit on Hardy 64bit.

Essentially, the solution described here: [http://gdub.wordpress.com/2008/04/27/eclipse-security-component-errors/]("http://gdub.wordpress.com/2008/04/27/eclipse-security-component-errors/") worked for me.

I executed ```
mkdir ~/.mozilla/eclipse
``` then gave the new eclipse directory full permissions ```
chmod 777 ~/.mozilla/eclipse
``` and now eclipse runs fine.

No idea why eclipse needs a directory here. Any ideas anyone?

---

### Post by chalk-t on 2008-05-01
"No idea why eclipse needs a directory here. Any ideas anyone?"

I saw the XUL runner hidden somewhere in the distribution. Thats a possible cause, at least.

---

### Post by Patrik Granlöv on 2008-05-29
I got the same error message when I installed CollabNet Desktop ([http://www.collab.net/products/integrations/cdee/getit.html](http://www.collab.net/products/integrations/cdee/getit.html)) from Help.

Creating the directory solved my problem also.

/Patrik

---

### Post by dmjones500 on 2010-01-18
I suspect the error could be caused by running Eclipse under sudo on the first invocation.

I had a [FONT="monospace"]~/.mozilla/eclipse[/FONT] directory owned by root.  Once I changed ownership to myself, it worked fine.

A reboot of Eclipse is required once you have altered the permissions.

---


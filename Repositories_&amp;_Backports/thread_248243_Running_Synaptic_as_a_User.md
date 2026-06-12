---
title: "Running Synaptic as a User"
date: 2006-08-31
forum: Repositories &amp; Backports
---

### Post by PerXes on 2006-08-31
Is it possible to run synaptic from a desktop user account?  I try "sudo synaptic" in a terminal, but nothing happens.  However, if I just type "synaptic" it opens synaptic in read-only mode.  Do I have to switch to an administrative account every time I want to install software?

---

### Post by bikeboy on 2006-08-31
> **PerXes said:**
> Is it possible to run synaptic from a desktop user account?  I try "sudo synaptic" in a terminal, but nothing happens.  However, if I just type "synaptic" it opens synaptic in read-only mode.  Do I have to switch to an administrative account every time I want to install software?

Yes you should be admin every time you go to install software from synaptic. From the terminal try```
gksudo synaptic
``` rather than plain sudo. You should always do this when opening a graphical app as root.

When you go to System > Admin > Synaptic, it should ask for your password anyway.

---

### Post by PerXes on 2006-08-31
That's another thing, Synaptic isn't in System->Admin.  I thought perhaps it isn't supposed to be since I'm logged in as a user..is it supposed to be there no matter what kind of account I'm logged in as?

---

### Post by PerXes on 2006-08-31
I tried gksudo, and I got the following error after I entered my password:

The underlying authorization mechanism (sudo) does not allow you to run this program.

---

### Post by bikeboy on 2006-09-01
Ok another question for you. Are you logged in as the user you created when you did the install?

If you created another new user and are using that account, it won't have admin rights enabled and won't be able to use sudo, that would explain why your commands don't work.

The original user you created isn't like Windows' admin user in that it's not running with full rights. But that user (original one) can gain those full rights by using sudo or gksudo. It's also possible to allow your new user to gain the sudo ability if you want.

So let us know which situation you're in and I'll try to suggest the solution.

---

### Post by PerXes on 2006-09-01
OK, that explains it then.  I created a new user because I thought the user I created at installation was an administrator and I didn't want to be logged in as an admin.  Thanks for the  help.

---

### Post by brim4brim on 2006-09-01
Yeah the suer you created at install was an administrator but you have user rights until you need administrator rights at which times you'll be asked for a password to make you an administor temporarily.

---


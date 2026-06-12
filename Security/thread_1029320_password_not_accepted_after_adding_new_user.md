---
title: "password not accepted after adding new user"
date: 2009-01-03
forum: Security
---

### Post by davechapel on 2009-01-03
I have just added a new user with administrator privilege and now nobody can get admin access when asked for a password. For example when I check for updates and it asks for a password the following message is given:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '54525955' '--update-at-startup' as user root.

I am running Ubuntu 8.04 and keep it updated. Everything worked OK until I added a new user.
Also tried rebooting but no change.

basically I seem to have lost all root access

Update:
In a command window the root-access password seems OK (sudo) but any graphical request fails: e.g. if I click on a "UNLOCK" box in the User Settings window I get the error "Could not authenticate - An unexpected error has occurred" and under the User Privileges property the "Administer the system" box is unchecked.

Is this a re-install Linux problem (shades of MS) or is there a command line trick?


Can anyone help please?

Dave

---

### Post by teddks on 2009-01-03
There's probably a solution. How did you add a new user?

---

### Post by davechapel on 2009-01-04
I had made the mistake of adding a new user called   admin

I have now found that this is a common error - Ubuntu should warn people when they try this.

The solution was to add my name to the group called admin in recovery mode.

Problem now solved.

Dave

---


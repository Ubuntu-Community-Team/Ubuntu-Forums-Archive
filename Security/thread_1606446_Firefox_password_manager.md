---
title: "Firefox password manager"
date: 2010-10-26
forum: Security
---

### Post by dogdo on 2010-10-26
Im looking for a firefox addon to remember some passwords i enter all the time like-my gmail account and some online forums. Ideally a well known one that is free and opensource. 

First off are these password managers secure? i seem to recall a recent story concerning the default firefox manager being hacked into not displaying 'remember password for this site' messages but in reality it was logging and sending passwords to a unknown third party. 

Secondly Is there anything security wise specific to password managers i should know about?

---

### Post by OpSecShellshock on 2010-10-26
> **dogdo said:**
> Im looking for a firefox addon to remember some passwords i enter all the time like-my gmail account and some online forums. Ideally a well known one that is free and opensource. 

First off are these password managers secure? i seem to recall a recent story concerning the default firefox manager being hacked into not displaying 'remember password for this site' messages but in reality it was logging and sending passwords to a unknown third party. 

Secondly Is there anything security wise specific to password managers i should know about?

The thing with disabling the "remember" option and sending the info to a third party happened due to a malicious extension. People who were affected had to install it themselves from the add-on page (and Mozilla has since changed the way they approve add-ons). The saved password utility included with Firefox is basically fine, assuming you're just using it locally rather than synchronizing it across multiple machines.

---

### Post by lovinglinux on 2010-10-26
Setup a master password and don't install extensions that are not approved by Mozilla. All your passwords will be encrypted like any other password manager.

There are [several extensions for managing passwords]("https://addons.mozilla.org/en-US/firefox/search/?q=password&cat=all&lver=any&pid=1&sort=&pp=20&lup=&advanced="), but most of them store data on a server.

---

### Post by emarkay on 2010-10-27
IMHO, nothing that "autocompletes" is secure - never.

Text files and "cut-n-paste" the data are a stopgap, as are Post-It notes stuck to the monitor...

---


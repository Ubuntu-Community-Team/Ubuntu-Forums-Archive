---
title: "Virutal Box"
date: 2019-05-01
forum: Virtualisation
---

### Post by gordie692 on 2019-05-01
Hey guys running 18.04 love it changed the customization to cinnamon and a little MS XP look but overall great job guys on the OS everything works on my laptop to printer so bye bye windows the problem I have I installed virutal box and keep getting error I only want 1 OS on as primary and a couple in virutal but can't get it to work anybody else getting errors on virutal box

---

### Post by cruzer001 on 2019-05-01
Please post the errors you are getting.

---

### Post by gordie692 on 2019-05-01
The virtual machine 'Fedora' has terminated unexpectedly during startup with exit code 1 (0x1).


[TABLE]
[TR]
[TD]Result Code: 
[/TD]
[TD][FONT=monospace]NS_ERROR_FAILURE (0x80004005)[/FONT]
[/TD]
[/TR]
[TR]
[TD]Component: 
[/TD]
[TD]MachineWrap
[/TD]
[/TR]
[TR]
[TD]Interface: 
[/TD]
[TD]IMachine {5047460a-265d-4538-b23e-ddba5fb84976}
[/TD]
[/TR]
[/TABLE]

---

### Post by DuckHook on 2019-05-01
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by cruzer001 on 2019-05-01
I do not recall if I have encountered that error code, but /vboxconfig has come up in a search.  Here is one example:

[https://askubuntu.com/a/1131716](https://askubuntu.com/a/1131716)

from this search:
[https://www.google.com/search?q=NS_ERROR_FAILURE+%280x80004005%29&ie=utf-8&oe=utf-8&client=firefox-b-1-e](https://www.google.com/search?q=NS_ERROR_FAILURE+%280x80004005%29&ie=utf-8&oe=utf-8&client=firefox-b-1-e)

Myself, I am running vBox 6.0 (downloaded from their site) on 18.04 and working well for me.  What are you running?

---

### Post by DuckHook on 2019-05-01
[LIST=1]
[*]How did you install vbox? From repos or from vbox site?
[*]What version of vbox are you running? Post results of:```
vboxmanage --version
```
[*]Are you in vboxusers group? Post results of:```
id
```
[*]If vboxusers is not listed, do:```
sudo usermod -a -G vboxusers $USER
```
[*]logout&#8594;login
[*]Check again with:```
id
```
[*]Try launching vbox again.
[/LIST]

---


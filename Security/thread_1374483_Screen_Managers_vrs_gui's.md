---
title: "Screen Managers vrs gui's"
date: 2010-01-06
forum: Security
---

### Post by jmsgz on 2010-01-06
1.) "generally speaking" Are systems w/screen managers (vfwm, blackbox etc) more secure than those using  gui's such as gnome or kde even through both use "X" 2.)i am asking because i am at a knowledge level between gui's and the command line. i understand that the most secure systems are those without gui's such as general server enviornments or desktops/workstations without gui's.at all.  my priority is security over ease of use. 3.) if the diff is large then the command line is it., on the flip side can a gui such as gnome or kde be made as secure as a system without?

---

### Post by x33a on 2010-01-06
afaik, gui doesn't bring about any insecurity. servers are console based because they are usually headless (i.e. without a monitor) and so running a gui is a waste of resources.

you can make any system as secure as you want.

---

### Post by jmsgz on 2010-01-06
"Generally speaking" are unix/linux systems (desktop, servers or workstations) running screen managers (vfwm,blackbox) under "X" more secure than those systems running gui's (kde, gnome) under "X" ???

if yes 
can a screen manager system be made as secure as a command line system??
if so point me to some reading!

if no! and security is my main concern then what tools will aid the desktop/workstation or server systems user/administrator life easier? 
point me to some reading!

thanks in advance

---

### Post by jmsgz on 2010-01-06
have you read any e-letters from the developers of openbsd to the x developers regarding kernal corruption involving the video cards memory etc, where its indicated that systems running x are susceptible to various types of attacks!

---

### Post by bodhi.zazen on 2010-01-06
> **jmsgz said:**
> 1.) "generally speaking" Are systems w/screen managers (vfwm, blackbox etc) more secure than those using  gui's such as gnome or kde even through both use "X" 2.)i am asking because i am at a knowledge level between gui's and the command line. i understand that the most secure systems are those without gui's such as general server enviornments or desktops/workstations without gui's.at all.  my priority is security over ease of use. 3.) if the diff is large then the command line is it., on the flip side can a gui such as gnome or kde be made as secure as a system without?

In general, the less applications the less potential vulnerabilities.

So a server with no X is more secure then one with a light weight window manager is more secure then gnome is more secure then ubuntu-desktop.

In reality, these vulnerabilities are probably minimal and not something I would worry about *too* much when considering remote attacks, with physical access, well with physical access it does not matter.

The types of applications that are potentially dangerous are not necessarily window managers, it is server apps such as FTP, ssh, VNC and any network application such as firefox.

---

### Post by cariboo on 2010-01-07
Please don't create multiple threads on the same subject. I have merged your two threads.

---


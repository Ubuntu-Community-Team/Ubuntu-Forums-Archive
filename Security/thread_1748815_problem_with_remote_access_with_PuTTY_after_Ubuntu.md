---
title: "problem with remote access with PuTTY after Ubuntu 11.04 installation"
date: 2011-05-04
forum: Security
---

### Post by upadhyayanm on 2011-05-04
[COLOR=black][FONT=Verdana]I had remote connection to my computer with Ubuntu 10.X through Xming/PuTTy without any problem. However, after installing Ubuntu 11.04 there seems to be some setup problem. When I open a PuTTy session I get the terminal prompt "login as:" OK but when I enter the username I get the message[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Access denied[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Using keyboard-interactive authentication [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](I assume it takes this alternative root for authentication because I did check the relevant box in PuTTy configuration [Attempt "keyboard-interactive" auth-SSH-2][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]And then prompts[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Password:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Here when I put me password I get the connection OK.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Not sure why it says "Access denied" when I start the session. Not a big problem though as I still can login. However, it will be good if I could get rid of this annoying "Access denied" message.[/FONT][/COLOR]

---

### Post by spynappels on 2011-05-04
It looks like it is trying to use public key authentication first and when this does not work it drops to using passwords.

Do you have public key authentication set up?

---

### Post by upadhyayanm on 2011-05-06
Thank you for the reply and suggestion. I did manage to stop the "Access denied" message by unticking (unchecking) one of the options in PuTTY configuration for controlling the SSH authentication- [Attempt GSSAPI auth (SSH-2] :)

---


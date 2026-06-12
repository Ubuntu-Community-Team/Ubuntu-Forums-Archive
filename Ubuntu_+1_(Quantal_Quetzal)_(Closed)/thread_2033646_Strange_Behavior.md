---
title: "Strange Behavior"
date: 2012-07-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by miguelpires on 2012-07-26
Hello, 
I've 3 strange behaviors in my Tosshiba A660 (my test machine), that come from 11.04 to 12.10:
1º. When I boot the system alts for a long time (maybe 1 to 2 minutes) in the login screen without let you enter your password, because he is whayting for the background image to shoo up.
2º. Then, when i finally enter the password, the system loads to the UI but first show me the Nvidia picture, then load everything normally.
3º. When the system goo to shutdown the monitor because I'm not doing anything on the PC, first he puts the screen with a white color and then (+- 10s) he puts the screen black.

anyone notice this behaviors, and how can I trace the thing?
Tk for reading and sorry for my bad english
Miguel

---

### Post by dino99 on 2012-07-26
1 see your logs, xsession-eerror first, and be sure that your grahic driver is well activated.

2 - deactivate nvidia splash in the bios

3 - again see the logs

---

### Post by miguelpires on 2012-07-26
> **dino99 said:**
> 1 see your logs, xsession-eerror first, and be sure that your grahic driver is well activated.

2 - deactivate nvidia splash in the bios

3 - again see the logs

Thank's for the replay. 

I'm going to try to see something in the logs

Regards
Miguel

---


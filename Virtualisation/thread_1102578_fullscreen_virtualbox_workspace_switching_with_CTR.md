---
title: "fullscreen virtualbox workspace switching with CTRL + ALT"
date: 2009-03-21
forum: Virtualisation
---

### Post by mattie01 on 2009-03-21
Hi everyone,
I have been following this guide 
```
http://ubuntuforums.org/showthread.php?t=433359
```
to get virtualbox installed and working,(this guide is for the seamless integration which isn't what I want achieve though) what I want to be able
to do is, have virtualbox running full screen on its on work space (say work space2) and be able to switch between them by using the CTRL + ALT and a right or left arrow.

while following the guide above I have left out the parts that tell me to alter the windows registry for the no desktop.

i can get virtualbox running fullscreen in the second work space by either  opening it open normally "from applications -> system tools -> virtual box"
or by doing the headless virtual box thing mentioned in the guide and rdp'ing to it.(i can't get it to auto open on workspace2 if I click on a short cut in workspace 1 but this is a different issue and not my main concern.)

with each of these setups I can CTRL + ALT rightarrow into the fullscreen virtualbox session/workspace and use windows XP(needed for my VPN into the office damn watchguard vpn) normally but when i try to CTRL + ALT leftarrow out of the workspace it does nothing. 

this may seem a strange request but it is the idea setup for myself,as i'm still moving from windows to ubuntu, it is handy being able to revert into windows with just 3 quick button presses. do what i want or vpn into the office, then back in ubuntu. is the best of both worlds for me.


Nodoubt i'm missing something really simple. but i just hope you guys can help.

thanks in advance.

---

### Post by JKyleOKC on 2009-03-21
To go from the virtual machine back to the other workspace, first press the right-hand control key to release the keyboard; the CTRL+ALT should then work as you expect. I'm assuming that you haven't changed the "host key" setting from the default of right-CTRL...

---

### Post by mattie01 on 2009-03-22
Thank you very much for this I swear I tried this. before posting. but it is working now. 

thank you very much for your quick reply.

---


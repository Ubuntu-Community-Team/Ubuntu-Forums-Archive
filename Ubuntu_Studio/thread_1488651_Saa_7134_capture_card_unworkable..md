---
title: "Saa 7134 capture card unworkable."
date: 2010-05-20
forum: Ubuntu Studio
---

### Post by pdlethbridge on 2010-05-20
I have tried many things to get this card to work like it does in 9.04. The following info I used from your site to get it working with tvtime.

sudo nano /etc/modprobe.d/saa7134        hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev       enter
alias chr-major-81-0 saa7134      enter
options saa7134 card=42 tuner=43 oss=1       enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.

This did not work in 9.10 or 10.04LTS. Is there something else I need to try besides going to a different kernel? (*Which I don't have the foggiest idea how to do )

---


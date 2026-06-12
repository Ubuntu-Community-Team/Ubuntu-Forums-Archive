---
title: "Unity much Slow in VirtualBox than 12.04"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by oly on 2012-09-12
Anyone experience this it is significantly slower at bringing up the side bar and unity dash, i have 12.04 and 12.10 installed 12.04 is using unity 2d so i am wondering if its due to this option being dropped ?

Any tips to get better performance from the interface on 12.10 or are there known problems ?

Not the virtual machine does not have true 3d option available so that is likely part of the cause but its a very significant drop in performance.

---

### Post by mips on 2012-09-12
I think you answered your own question.

---

### Post by oly on 2012-09-12
I guess i did, but as 3d is not required i would have still expected similar performance, perhaps i will try turning 3d acceleration of and see if it works faster :p

---

### Post by fjgaude on 2012-09-12
Ubuntu now uses llvmpipe and the CPU to render 2D, instead of the driver that uses the video board. I wonder if there will be any improvements as time goes on with that llvmpipe?

---

### Post by funicorn on 2012-09-17
type 'nvidia-settings Exec=nvidia-settings --assign="SyncToVBlank=0" in the terminal and press Enter.

This will close 'Sync to VBlank' of opengl, and virtualbox should run more smoothly.

---


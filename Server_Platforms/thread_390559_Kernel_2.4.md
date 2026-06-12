---
title: "Kernel 2.4"
date: 2007-03-22
forum: Server Platforms
---

### Post by Andu on 2007-03-22
So, I have Ubuntu 6.06 installed, using the 2.6 kernel, and i need to downgrade it to the 2.4 version. 
I have installed the 2.4 kernel using synaptic and it is telling me that is it is successfully installed. Then i log in as root, to update grub (using the command 'update grub')
However grub does not find the 2.4 kernel. 

I need to have this 2.4 kernel installed quite urgently. Have i done something wrong?
And is there another way of going around this?

I am ready to install another version of Ubuntu from scratch, but they all seem to run the 2.4 kernel. Is there anywhere i can find an  Ubuntu downloadable image using a 2.4 kernel?

---

### Post by Rizado on 2007-03-22
You should tell us why you need to downgrade to the 2.4 kernel incase it's not necessary at all. 

Anyway I remember it beeing a hassle upgrading to 2.6 as there were lots of things that changed. Can't imagine it beeing any easier downgrading.

---

### Post by Andu on 2007-03-22
I have to run a program (pertaining to memory dumps: dev/mem) that was coded in the 2.4 kernel.
Since many things have changed and the program contains things closely related to the pure kernel structure (such as the memory adress for kernel mode pages etc), it won't run properly on 2.6.

---


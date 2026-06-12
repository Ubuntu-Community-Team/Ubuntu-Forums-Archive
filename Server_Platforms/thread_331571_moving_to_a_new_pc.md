---
title: "moving to a new pc"
date: 2007-01-04
forum: Server Platforms
---

### Post by bugboy on 2007-01-04
Hello all.

I have set up a wonderfull lamp server which is running great. I have a gui on it so i can use some tools over a vnc server. 

Now i've got my hands on a new pc and was wondering how can i clone this system over to it with minimal fuss. Baring in mind that once the new machine is set up all the bits and bobs from the older one will be used in the newer one.

I did try just moving the hard drive over (just to see what happens) but when i did it threw an error up about the gui.

I need to keep all the files on the old hard drive and the apache set up and mysql set up.

Has anyone else done this if so any advice would be great.

If this is in the wrong forum please forgive me. But as its a server question i thought it would suit.

Cheers

---

### Post by teaker1s on 2007-01-04
no doubt someone will come up with a more complete answer
1)make sure you have correct kernel and headers for processor installed in new system.
2) to reconfigure display may need to boot in recovery mode and 
sudo dpkg-reconfigure xserver-xorg

in theory unless you have tweaked config files for certain hardware you should be good to go-server wise I know nothing but this would be a general hard disc swap procedure if this isn't what your looking for my appologies :confused:

---

### Post by bugboy on 2007-01-05
i was wondering about just doing a hard drive swap. 

That makes sense what you said.

I was thinking about using a bigger drive for this part could i just clone that system over to it and bang the bigger drive into the new set up and then do the reconfigure?

---

### Post by bugboy on 2007-01-05
it works to a certain degree. But i'll have to set up the the network interface again as its not being picked up.

---


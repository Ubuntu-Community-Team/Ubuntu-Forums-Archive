---
title: "need help fixing dirty raid 5 array"
date: 2009-12-20
forum: Server Platforms
---

### Post by twidget on 2009-12-20
background:
i seem to have managed to fry the raid 5 array that my home folder lives on.basically i had a disk go bad and i decided it would be a good idea to check for broken SATA cables by swapping out the drive cables one at a time and then starting the server to see if the missing drive showed up.Mistake! this worked fine up until the last drive but now the OS reads the array as dirty.
 I don't mind losing the data in my home folder so much since i backed up everything on the array before i started fiddling. normally I would just re install at this point but I can't get at my subversion repo on the OS array in order to back it up. when I boot i get an file check error and then it spits me out into the root account. Ubuntu no longer recognizes my username.
I'm assuming that this is because i have no home folder anymore. 

so here are my questions: Is there anyway i can clean my 2 disk raid5 array up enough to make it usable again for enough time to download my repo onto another computer? 
if not then i assume the next best option would be to kill the array, then rebuild it, and finally to create a folder named my username.or would i have to use adduser? If i go this rout I would like to go to raid 6. will that make any difference? how hard is it going to be to pull this off?

---


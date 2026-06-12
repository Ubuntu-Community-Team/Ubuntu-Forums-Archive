---
title: "My last 2 Ubuntu days"
date: 2006-11-17
forum: Testimonials &amp; Experiences
---

### Post by pichalsi on 2006-11-17
Well, this isnt really gonna be about me moving to Ubuntu... In past i tried Red Hat (4 or so years ago) and this summer after i got my laptop without windows i decided do use Ubuntu... It worked well, but yesterday, eh... all worked like it should have had ,but i made a few fatal mistakes :)

I wanted to copy my mp3 collection to my MicroSD to play in my smartphone... so i put it in card reader, started copying but after a while the speed went down from like 5MB/s to 16kb or so... So i plugged the card out of reader in hope that nothing can happen and it probably got damaged which i didnt know before... So i put it back and tried to delete stuff but it said there were errors and so on. so i was gonna try fsck... i typed sudo fsck without any arguments thinking i dont know what (it was nearly midnight). Fsck asked me something even in UPPERCASE but i ignored it and pressed Enter. It printed some message but i didnt care again... i went on but i found out my filesystem was out... there was nothing in /, or anywhere else, i rebooted, grub didnt start so i put my dapper cd and noticed my root partition with all my work for school was wrong. so i went to sleep thinking ill have to redo everything again... anyway in the morning today i ran fsck again on the partition, it worked somehow but my /home with work was not there. fortunately i found it in /lost+found using grep (i only needed like 3 files in C and one in LaTeX).

Now im writing from livecd preparing to install tommorow and gonna reclaim (complain? idk if that is the right word i got it from dictionary :)) the memory card, hopefully they replace it :) 

Conclusion?:) Love the LiveCD ! i think this wouldnt happen in windowz but if so i think i would be able to do anything... i previously had kubuntu but now, looking on this im thinking what to install, i like the kde apps (amarok, k3b, superkaramba and kate for C programming :) ) but the desktop is better here. if you have some tips feel free to post :twisted:  i hope its not too long to read and that i wont ever make mistakes like this :???:

---

### Post by hoagie on 2006-11-17
You can always install the kde applications in gnome. You'll just have to add some extra packages too. But don't worry synaptic will do all the work and install by its own the deepndecies(kde libraries).

---


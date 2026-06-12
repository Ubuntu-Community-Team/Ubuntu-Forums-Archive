---
title: "A question about server"
date: 2010-02-12
forum: Server Platforms
---

### Post by babyboss on 2010-02-12
I created a website that allow people freely upload films to the site and it also allow other visitors to watch the film at the same time. Now I am using VPS hosting. There are many people successfully uploaded their films and there are also people complain about they can't upload the films properly. What can I do to reduce the complains. I used drupal's flash video module for all videos stuff. The module itself shouldn't have any problems, otherwise, no one would even upload any films. The fact is there are a lot of people can upload the films successfully. Would increase the bandwidth reduce the complains?

Thank you.

---

### Post by ikehack on 2010-02-15
Well there are a couple things you want to step back and look at, one of which you said. Bandwidth can always be an issue, especially with what you're doing. With users uploading and watching videos at the same time, this may be cumbersome to your bandwidth. Depending on how large these files are that are being sent, retrieved, and accessed simultaneously will dramatically effect performance for some users who are trying to access or send files when multiple uploads (that may be large in size) taking place at the same time. Following me?

The second aspect you want to take a look at is the hardware in your server. For the application your using your web server for, you want speed as far as your processor, NIC cards, hard disks and RAM's is just always a given. I don't know what type of network you're running this server on, maybe a gigabit network? If you're running it on a something less than gigabit, this can effect performance. 

With visitors constantly sending, retrieving and accessing small to large video files from the disks in your server, speed as far as your hard disks is something to also look into. If your disks are spinning at standard 7200RPM's that's going to yield some slower performance. If you were to use disks with 10,000+ RPMs, you might has less of an issue with that. 

RAM.. simply put, it'll help? I can't really think of a valid reason for RAM. 

The processor is a big one though. With all these files being, again: sent, retrieved, and accessed a beefier processor will increase performance.

I've given all I could think of. Hope this helps!

---


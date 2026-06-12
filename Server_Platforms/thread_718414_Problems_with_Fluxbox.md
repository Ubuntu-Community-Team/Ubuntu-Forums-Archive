---
title: "Problems with Fluxbox"
date: 2008-03-08
forum: Server Platforms
---

### Post by hey2222 on 2008-03-08
Well, installed ubuntu server tonight so I could learn how to bring up servies and such manually(You know learning experience), I'm fairly new to the server side of doing things  and still dependent on a gui; I have a lot questions.

I did this first(well after updates):
sudo aptitude install xorg

then:
sudo aptitude install fluxbox fluxconf; like it has it in the guide here
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Now my questions, i couldn't start fluxbox with "startfluxbox" says:
"Error: Couldn't connect to XServer"
When i do startx it works. Does the command startfluxbox not exist anymore?

When I'm at fluxbox left and right click don't work but middle button does and i have no icons. Do I have to set the icons manually, and if so how?

---

### Post by hey2222 on 2008-03-08
HA! sorry for the double post. I'm such a scatter brain why didnt i search the forums. Shame on me.

For others:
[http://ubuntuforums.org/showthread.php?t=718010](http://ubuntuforums.org/showthread.php?t=718010)

---

### Post by RedSquirrel on 2008-03-08
I would advise you to stay away from fluxconf. It's old, buggy, and might cause some headaches. See the Links & Information section in the tutorial in my signature for some help in getting used to Fluxbox.

For desktop icons, you could try idesk or rox-filer.

---


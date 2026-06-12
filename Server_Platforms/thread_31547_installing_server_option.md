---
title: "installing server option"
date: 2005-05-03
forum: Server Platforms
---

### Post by jayd36108 on 2005-05-03
hi,

linux no0b here.

i'm installing the server option on ubuntu and at restart it goes into a dos-like prompt screen.

how do i get it to start up like it does when i install the default version?

---

### Post by Ashtray on 2005-05-03
You need to install X-server try the command startx

If it doesn't work, search forum on how to install X and Gnome/kde

---

### Post by dataw0lf on 2005-05-03
That's one of the major features of the 'server' selection; e.g., you don't have the overhead on your server that comes with a X server and windows manager.  Running a GUI on a server isn't a good idea: it hogs resources that could be much better spent elsewhere, introduces more variables involving security, and adds a level of abstraction to your control of the server.

---

### Post by Ashtray on 2005-05-03
//offtopic

He's asking HOWTO....

 :-#

---

### Post by jayd36108 on 2005-05-03
well should i just re-intsall and hit default at setup rather than server? wuld that be better for me?

---

### Post by Ashtray on 2005-05-03
You can install packages you need, just from command line if you want to..

But for you as a self-titled NooB, i would do the reinstall... No-Offense dude, i started out couple years ago wondering what i should do in this DOS box...


 :razz:

---

### Post by jayd36108 on 2005-05-03
no offense taken, i'm just trying to sort through and get the right info i need
i just want to use ubuntu to as a website server to host my 4 sites and host audio.

---

### Post by crane on 2005-05-03
You could do a default install and then install the apache2 software and what everelse you needed or (and I'm not real familiar witht the server install ) you could just sudo apt-get install ubuntu-desktop I would think to install the desktop on the server.

I remember when I first installed a server i felt more comfortable being able to use gui text editers and such. I would suggest this if you want the gui on for checking and configing. (yes I know all the more advanced users are saying there is no gui config for some of the server software) But learn how to turn it off. loggin. startx do what you need to do the kill the x server to save resources.
Just a thought.

Good luck!!

---

### Post by az on 2005-05-03
[QUOTE=jayd36108]well should i just re-intsall and hit default at setup rather than server? wuld that be better for me?[/QUOTE]


No, just install ubuntu-desktop

sudo apt-get install ubuntu-desktop

---

### Post by jayd36108 on 2005-05-03
thanks

---

### Post by s0c0 on 2005-05-03
If you want a gui desktop w/o the high resource consumption I would go with blackbox or fluxbox.  This way you can still use firefox and other gui applications.

---

### Post by jayd36108 on 2005-05-03
what's the sudo command for those?

i am already installing the desktop as i type, not too concerned about resources cause i am only using the server box for updating websites once i get it up and going.

---


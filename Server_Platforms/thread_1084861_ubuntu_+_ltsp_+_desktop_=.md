---
title: "ubuntu + ltsp + desktop =???"
date: 2009-03-02
forum: Server Platforms
---

### Post by andrea000 on 2009-03-02
Hello all,

Here is my problem i have set up a linux terminal server but i had to install the GUI on the server so i would have a desktop
on the clients.I need a desktop to come up on the clients but i do not need one on the server.is there a way to do this?i have looked at ebox but that is just a way of managing the network
any help please  :confused:

---

### Post by lykwydchykyn on 2009-03-02
You need the GUI installed, but from my testing it doesn't need to be running.  You can set gdm not to load on startup, and that should keep the server at the CLI.

Just run this on the server:
```

sudo update-rc.d -f gdm remove
sudo update-rc.d -f gdm stop 2 3 4 5 .

```

I think that's right, anyway.  see if that does it.

---

### Post by andrea000 on 2009-03-03
> **lykwydchykyn said:**
> You need the GUI installed, but from my testing it doesn't need to be running.  You can set gdm not to load on startup, and that should keep the server at the CLI.

Just run this on the server:
```

sudo update-rc.d -f gdm remove
sudo update-rc.d -f gdm stop 2 3 4 5 .

```

I think that's right, anyway.  see if that does it.

Ok so all i needed to do was install the GUI not have it running all the time i have mine set to run all the time ok i am going to try this running a gui all the time is a big over kill and it
is eating up my system resources.

Thank you so much

XOXOXO

Andrea

---


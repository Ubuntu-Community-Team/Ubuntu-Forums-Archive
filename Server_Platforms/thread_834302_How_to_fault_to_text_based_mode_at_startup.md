---
title: "How to fault to text based mode at startup"
date: 2008-06-19
forum: Server Platforms
---

### Post by Evmax318 on 2008-06-19
I'm using Ubuntu 8.04 server edition onto a virtual machine. I then installed the Ubuntu Desktop Gnome GUI, it defaults to the GUI when I boot up the virtual machine, how do I get it to default to the text mode like it was before I installed the GUI?  (note: I still want the GUI installed, I just want to see the text first)


...and if I was able to get it to default to the text mode, what would the command be to launch the GUI?

---

### Post by HermanAB on 2008-06-19
See /etc/inittab about ten lines down.

---

### Post by Evmax318 on 2008-06-19
that file does not seem to exist. I just can't find it

---

### Post by lavajumper on 2008-06-19
This works for me:

In /etc/rc2.d are a bunch of sym-links to startup-shutdown scripts in /etc/init.d, look for the gdm or kdm sym-links. The S,K, and numbers are used to control startup and shutdown sequence. If it starts with an 'S' it means "Start this process when you enter this run-level" if it starts with a 'K' it means "Kill this process when you enter this run-level" So when it enters run-level 2 (rc2.d,the ubuntu default) it starts with S00alphabetical and moves down the line to S99zalphabetical, running each script down the line.


no gui boot on my system: (be root)
 ```

  cd /etc/rc2.d
  mv S23gdm K23gdm

```

(The S23 will probably be different on yours, ie S15gdm)

Starting and stopping gui from command line:
```

  sudo /etc/init.d/gdm stop
  sudo /etc/init.d/gdm start

```

notes:
-If you use kubuntu, replace gdm with kdm
-I rename the links to 'K's so that I can easily adjust them and I read somewhere that it makes update-manager a bit happier, but I have safely deleted some w/o ill effect.

Sorry so short, but I'm on the way out the door.

Good Luck

---


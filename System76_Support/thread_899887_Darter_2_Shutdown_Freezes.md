---
title: "Darter 2 Shutdown Freezes"
date: 2008-08-24
forum: System76 Support
---

### Post by gaussian on 2008-08-24
Just wanted to share something: My Darter 2 sometimes (may 1/3 of the times) does not shut down cleanly (it goes through the shutdown script but freezes just before it should power off or reboot). I think I have located the problem to hda-snd-intel module, which should be removed before shutdown. This is in 64-bit Gutsy, but I would be interested to hear if anyone else is experiencing this in any other configuration.

My fix:
Put the following script to /etc/init.d/darterownscript

```

#!/bin/bash
case $1 in
 stop)
 rmmod snd-hda-intel
 ;;
 *)
esac

```

make it executable
```

sudo chmod +x /etc/init.d/darterownscript

```

and make symlink to it 
```

sudo ln -s /etc/init.d/darterownscript /etc/rc0.d/K60darterownscript

```

All this is shamelessly modified/stolen from Wiki page on how to get Asus EEE 901 work with Ubuntu (looks complicated, I am waiting for Ubuntu ultraportables from Dell and hopefully from System 76 before making a purchase). I have not have freeze-ups ever since (it has been four days now, several reboots because I have been playing with Intrepid). Feel free to test this.

---

### Post by williumbillium on 2008-08-25
I experience this too.  I'm running Gutsy 64 bit on the Daru2 also. I don't reboot very often so I haven't been able to pinpoint the situation that causes the hang but I'm starting to think that it only hangs after suspending.  

I just tried rebooting 3 times after reading this post and it hung on both reboots after I suspended but it rebooted fine when I hadn't suspended.

Thanks for sharing the script though, I'll try it out and see what happens.

EDIT:  Having made the updates to the shutdown scripts, I tried rebooting (after suspending) and it hung.  I'm wondering if you haven't suspended because you are using intrepid and that's why you haven't been having any problems?

---

### Post by gaussian on 2008-08-25
> **williumbillium said:**
> I experience this too.  I'm running Gutsy 64 bit on the Daru2 also. I don't reboot very often so I haven't been able to pinpoint the situation that causes the hang but I'm starting to think that it only hangs after suspending.  

I just tried rebooting 3 times after reading this post and it hung on both reboots after I suspended but it rebooted fine when I hadn't suspended.

Thanks for sharing the script though, I'll try it out and see what happens.

EDIT:  Having made the updates to the shutdown scripts, I tried rebooting (after suspending) and it hung.  I'm wondering if you haven't suspended because you are using intrepid and that's why you haven't been having any problems?

I Can confirm that you are right and I am wrong :) The problem seems to be unaffected by snd-hda-intel and has everything to do with suspending, I tried suspending and the reboot hung tried after that. Well, back to the drawing board.

---


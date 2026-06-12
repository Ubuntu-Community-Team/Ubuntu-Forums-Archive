---
title: "Ratel Reboots when I shut down"
date: 2007-05-23
forum: System76 Support
---

### Post by Paulr-55 on 2007-05-23
My new Ratel box keeps rebooting after I select shutdown.

Any ideas what could cause that?

---

### Post by thomasaaron on 2007-05-23
Wow! I've not heard of that one before!
I did a bit of googling and found nothing similar.

My first question (and I apologize in advance for it) is: Are you sure you're pressing the correct button?

My second question is: What happens if you press Restart? Does it shutdown?


Until we get this figured out, here is a workaround:
From a terminal, you can restart by typing:  sudo reboot
Or you can shutdown by typing: sudo shutdown now

---

### Post by Paulr-55 on 2007-05-23
It has done this 3 times (it's not every time) and it is the shut down button I hit.

When I hit restart, the system goes down and I note that the power button remains lit and it immediately reboots.

When the problem happened, I chose shut down - the system went down and the power button light was off - and in about 3 seconds it powered back up.

It hasn't done this since early this morning. I will post back if it does it again.

I know -- weird.

---

### Post by Paulr-55 on 2007-05-25
Ok, it did it again just now. Machine was running overnite and I shut down to go to work. Started back up on its own as I described above. I suspect when I shut it down again in a minute it will stay shut down - that has been the behavior.

Can I write a shut-down script and hang it on a launcher icon or something? Or could this be a hardware glitch? I guess I should start shutting down from the command line and see if it occurs again.

It's not a crisis -- just very curious behavior.

---

### Post by Paulr-55 on 2007-05-25
Ok. Shutdown from the command line doesn't shut down at all. It prints some messages and leaves me in a root terminal.

```
shutdown -r now
```

restarts the machine, but it won't shut down from that root terminal. It just puts me back in that terminal -- is there maybe a buggy script somewhere.

I am off to work and will be unable to respond until this evening.

Thanks

---

### Post by thomasaaron on 2007-05-25
That's curious.

Definitely sounds like a buggy script somewhere.

Try this:

Go to System > Preferences > Power Management
Click on the General tab.
In the pull-down, select Shut Down

Then see if your power button will allow it to shut down properly.

If not, we'll get it straightened out after the (Memorial Day) weekend.

Best,
Tom

---

### Post by Paulr-55 on 2007-05-25
I'll try that tonight and get back with you after the weekend. Have a good one. -Paul

---

### Post by Paulr-55 on 2007-05-29
Tom - I have tried nail down exactly when and how this is happening. I configured the power button to shut down as you suggested and it behaves the same as the terminal command, it leaves me in a full screen text terminal as root.

I noticed on 2 occasions that cutting the power to my outboard USB drive (appeared to) cause the machine to start back up. I have unplugged and replugged everything and have not seen the error for several days so there's nothing left to do for now.

That aside - I love the new box. It is very fast and for once I did not have to edit xorg.config to get my widescreen Acer to work.

Thanks, Paul

---


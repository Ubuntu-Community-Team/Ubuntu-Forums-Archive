---
title: "Resuming with Beryl after a Hibernate/Suspend"
date: 2007-06-29
forum: System76 Support
---

### Post by aay on 2007-06-29
The recent System76 driver release fixes most (maybe all) of the problems I was having resuming from suspension and hibernation with my Gazelle Pro.

I had one problem left which I really didn't consider a System76 problem.

It was impossible to recover X after resuming from suspension or hibernation if I closed down with Beryl running.  One solution to this is simply to turn off Beryl before hibernating/suspending, but sometimes you forget and you end up losing any work you might have open.

I did some searching around and I found a solution that seems to fix this problem pretty well.

I got the solution below from [this page]("http://forum.beryl-project.org/viewtopic.php?f=39&t=47&view=previous") on the beryl forums.

Here's the solution.

> 

To kill Beryl on suspend, paste this into a text file as root:

```
#!/bin/sh
if pidof beryl > /dev/null; then
  WASBERYLRUNNING=1
  killall beryl-manager; killall beryl; killall emerald
fi

```

Save as /etc/acpi/suspend.d/06-kill-beryl.sh and chmod 755.

To start Beryl on resume if it was running, paste this into a text file as root:

```
#!/bin/sh

if [ x"$WASBERYLRUNNING" = x"1" ]; then
  for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
      export DISPLAY=":$displaynum"
      su $user -c "(sleep 1; beryl-manager &)"
    fi
  done
fi

```


Save as /etc/acpi/resume.d/97-restart-beryl.sh and chmod 755.

That's it. You can now safely suspend or hibernate without Beryl interfering.

Again, I suggest you have the latest System76 driver (currently 2.0.5) before doing this.

Carl and Tom, maybe this could be rolled into a future version of the driver especially when Gutsy comes out and has Beryl (Compiz-Fusion) turned on by default for systems that can support it.

Adam

---

### Post by aay on 2007-06-29
One more thing.

There is only one problem with the above mentioned method of resuming from suspend/hibernate and keeping Beryl going.

I have to restart beryl-manager manually after resuming.  This is no problem since you can just go to Applications/System Tools/Beryl Manager.

It would be nice to know how to automate this however if anyone knows how.  It looks like the resume script tries to restart it, but it doesn't seem to work.

Anyway, this method still gets you back into your X session without crashing everything.

Adam

---

### Post by pkwan on 2007-07-11
Make sure you have make the script executive for all users.

---


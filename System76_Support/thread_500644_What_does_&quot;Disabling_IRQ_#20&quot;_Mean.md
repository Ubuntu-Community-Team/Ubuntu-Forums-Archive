---
title: "What does &quot;Disabling IRQ #20&quot; Mean?"
date: 2007-07-14
forum: System76 Support
---

### Post by Paulr-55 on 2007-07-14
I've gotten this message twice now while in a bash session:

```
Message from syslogd@arrowroot at Sat Jul 14 05:46:41 2007 ...
arrowroot kernel: [ 1320.618768] Disabling IRQ #20
```

dmesg | tail:

```
[ 1320.618710]  [<c0105b75>] do_IRQ+0x45/0x80
[ 1320.618715]  [<c0104233>] common_interrupt+0x23/0x30
[ 1320.618723]  [<c01012b6>] mwait_idle_with_hints+0x46/0x60
[ 1320.618729]  [<c0101409>] cpu_idle+0x49/0xd0
[ 1320.618734]  [<c03d97f5>] start_kernel+0x365/0x420
[ 1320.618740]  [<c03d9230>] unknown_bootoption+0x0/0x260
[ 1320.618748]  =======================
[ 1320.618750] handlers:
[ 1320.618751] [<f888af10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 1320.618768] Disabling IRQ #20
```

This is on a Ratel under Feisty. I have a LaCie USB HD mounted at startup, and was running Firefox, Terminal, and Gedit.

Is this something to worry about? What's it mean?

Thanks for any insights.

Paul

---

### Post by greg_g on 2007-07-14
I don't know but I get it also.

I also have a Ratel with an external Harddrive connected. That could be it, but I have no idea.  I also have firefox, a terminal, and gedit running a lot of the time too ;) So it could be anything.


So far I haven't seen any system issues when it says that (like the harddrive not working) so I haven't worried about it.

You aren't alone, but if you figure it out, post back here.

greg

---

### Post by Paulr-55 on 2007-07-14
Thanks, I did some googling and didn't find anything that seemed relevant (or that I could understand. :-)

I guess it begs the question, why would linux disable an IRQ?

I will post back if I do figure anything out.

---

### Post by Paulr-55 on 2007-07-14
Greg-G, btw do you have Palm sync daemon running?

---

### Post by greg_g on 2007-07-14
I do not have the palm service running

---

### Post by greg_g on 2007-08-26
So, I am still getting this message in my terminal.  I just haven't noticed very much because I don't have terminals open for very long.  But now I am using irssi (a command line IRC client).  When this message is displayed it completely screws with irssi.

I did a bit more sluething today, and found a new bug on the kernel bug tracker:
[http://bugzilla.kernel.org/show_bug.cgi?id=8841](http://bugzilla.kernel.org/show_bug.cgi?id=8841)

posted bug in launchpad:
[https://bugs.launchpad.net/system76/+bug/134956](https://bugs.launchpad.net/system76/+bug/134956)

greg

---

### Post by thomasaaron on 2007-08-27
I did some research on it, and there is speculation that it relates to via chipsets, bios, etc...

It definitely seems to be kernel related, and the fix will probably end up coming down from Ubuntu eventually.

For now, it might be a good idea to see if there is another irc client that doesn't get screwed up by it.

---

### Post by greg_g on 2007-08-27
Yeah, thanks Tom.

It doesn't COMPLETELY screw with irssi, I found that all I have to do is resize (redraw) the window and all is good.

greg

---


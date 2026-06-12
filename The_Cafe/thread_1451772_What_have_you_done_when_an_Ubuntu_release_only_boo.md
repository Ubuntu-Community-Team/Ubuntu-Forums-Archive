---
title: "What have you done when an Ubuntu release only boots with an old kernel?"
date: 2010-04-11
forum: The Cafe
---

### Post by Irihapeti on 2010-04-11
I have an installation of Lucid which will only boot with the Karmic kernel. Bug report exists and it may get fixed, but I'm assuming at this point that it won't - at least, not in time for release.

I'd like to know if anyone else has had this kind of situation, and what they've done about it.

Options, as I see them, are to:

[LIST]
[*]keep using older kernels - but gets tricky when you are dealing with a long-term release

[*]compile a kernel (no luck with that so far)

[*]skip the release altogether and hope the next one behaves better

[*]go to another distro altogether

[*]and an option that's too awful (and expensive) to contemplate. :)
[/LIST]

So, who has any experience of this situation? What did you do?

---

### Post by gletob on 2010-04-11
I used to have that problem with Grub Legacy (Grub 1?).  Usually I'd fix it by copying the non automatic stuff from the menu.lst file and delete it.  Make a new one, add non automatic back.

Are you running Grub Legacy or Grub 2?

---

### Post by Irihapeti on 2010-04-11
OK, looks like I didn't make myself clear enough. I'll try again.

The problem is that the Lucid kernel actually doesn't work for me. So I have had to use the Karmic kernel for the thing to boot at all.

I'm using grub legacy, because Hardy is the main OS on this machine, but I doubt that this is what's causing the problem.

---

### Post by gletob on 2010-04-11
Oops I'm sorry, it my mistake as for what happening with your machine, and kernel I'm probably of no help.:P

Just out of curiosity what's your machines setup?

---

### Post by cariboo on 2010-04-11
What is it about the Lucid kernel that doesn't work for you? What type of errors are you getting? 

The last time I had a kernel problem, I reported a bug, and had one of the kernel devs email me about the problem with a day, and the issue was resolved fairly quickly. This was during the Jaunty testing cycle.

When creating a bug report, add as much info as you possibly can, file the bug using "ubuntu-bug kernel-2.6.32-19-generic #28".

---

### Post by Irihapeti on 2010-04-11
Cariboo:
See bug 499399 in Launchpad. I've had this problem since just before Christmas. I've recently discovered someone else has one that's very similar.

I've been asked by someone on the kernel team for further details, as has the filer of the second bug. I've provided them, of course. Is there something else I could/should be doing as well (that won't make me sound like a whiner :) )?

The purpose of this thread is to find out what others have done as a plan B in case this doesn't get fixed.

---

### Post by Khakilang on 2010-04-11
I would wait for the stable version release. I believe by that time most of the bugs has been fix.

---

### Post by cariboo on 2010-04-11
I've read the bug report, there seems to be a lot of missing information. Can you still boot to a console login prompt? If you can login, can you get a network connection by running:

```
sudo dhclient
```

at the prompt, if that is successful, you should be able to run ubuntu-bug against the kernel. This should give the devs some log files to look at, they are located in /var/crash.

With the way Ubuntu now boots, it's tough to see what is happening without resorting to some grub2-foo to see what the error messages are.

---

### Post by Irihapeti on 2010-04-11
@cariboo907

No, I can't login at all. If I try "recovery mode" it gets to the recovery screen and then the keyboard locks up totally. If I do a normal boot (minus the "quiet splash"), it gets to the point where ureadahead terminates, sometimes with an indication that the partitions have been mounted, and then the keyboard locks up totally. That's why I've not been able to provide any further information, which I know is frustrating to everyone.

If I make it boot to busybox, then keyboard works, but as soon as I exit busybox, it locks up.

---

### Post by ssam on 2010-04-11
have you tried installing any of the mainline kernels
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by bash on 2010-04-11
Btw wouldn't this be better suited in the Lucid Lynx discussion forum?

---

### Post by Irihapeti on 2010-04-11
> **ssam said:**
> have you tried installing any of the mainline kernels
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Yes, I've tried several of them. None of them have made any difference, unfortunately.

---

### Post by handy on 2010-04-11
I'm running kernel .34-rc3 on Arch & it is behaving beautifully. It might be worth a try?

---

### Post by undecim on 2010-04-11
manually edit grub.cfg to boot the old kernel. As soon as there is a kernel update, the change gets overwritten to use the new, possibly bootable kernel.

---


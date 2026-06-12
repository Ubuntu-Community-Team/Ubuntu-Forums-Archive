---
title: "gazp6 intermittently fails to resume from suspend"
date: 2012-01-23
forum: System76 Support
---

### Post by jschall1 on 2012-01-23
Every few suspends, my gazp6 hangs at a black screen with about 100 pixels of graphical corruption at the top (usually solid blue, or sometimes a message saying "irq 19: nobody cared (try booting with the "irqpoll" option)," which I think is unrelated - it comes up on boot, as well - I think it's just some garbage from video memory.)

ctrl-alt-sysrq R-E-I-S-U-B does not shut the system down, which I think means the kernel has crashed.

I'm using kubuntu, but I will probably install ubuntu and test with it for a bit - I can usually reproduce the problem in less than a minute of suspending and resuming. I can also possibly swap hard drives with my mother's laptop, an identical gazp6, to see if it's a hardware issue.

Anyway, there was nothing obvious in syslog or Xorg log. Anything else I should look for?

---

### Post by isantop on 2012-01-23
It will be interesting to see your results from testing with the other hard drive and in Ubuntu. I'm not sure this isn't a software issue localized to your installation.

Also, are you using Suspend (Suspend to RAM) or Hibernate (Suspend to Disk)? In theory, either should work fine, but suspend (to RAM) is definitely a cleaner process and generally better supported at the software level.

---

### Post by jschall1 on 2012-01-23
> **isantop said:**
> It will be interesting to see your results from testing with the other hard drive and in Ubuntu. I'm not sure this isn't a software issue localized to your installation.

Also, are you using Suspend (Suspend to RAM) or Hibernate (Suspend to Disk)? In theory, either should work fine, but suspend (to RAM) is definitely a cleaner process and generally better supported at the software level.

Using suspend to RAM.
It doesn't go away if I reinstall kubuntu, I have done so twice.

---

### Post by Ruebel82 on 2012-01-23
I am also getting that same message, and have the same model of computer (gazp6).  I haven't installed kubuntu though, and this message has been here since I got the computer as far as I can remember.

-Chase

---

### Post by jschall1 on 2012-01-23
Yeah, the message shows up on both of these gazp6s.

Haven't swapped drives yet.

---

### Post by isantop on 2012-01-24
That particular message is a red herring, and does show up on all of our systems. It's not indicative of a problem.

---

### Post by jschall1 on 2012-01-26
Oddly enough, I haven't had this issue again. Must have grabbed an update that fixed it at some point.

---

### Post by isantop on 2012-01-26
That's an excellent guess and a strong probability. The benefits of open source strike again!

---

### Post by dodo3773 on 2012-01-29
For future reference the magic sysrq key has to be enabled before you use it with reisub (not sure if you already did that just saying). Also, maybe in the future you could try the suggestion from the error message "try booting with the "irqpoll" option". irqpoll is a kernel option you can put in grub (not everyone has had a lot of luck with that option again just pointing it out). Glad you got your problem fixed.

---

### Post by isantop on 2012-01-30
> **dodo3773 said:**
> For future reference the magic sysrq key has to be enabled before you use it with reisub (not sure if you already did that just saying). Also, maybe in the future you could try the suggestion from the error message "try booting with the "irqpoll" option". irqpoll is a kernel option you can put in grub (not everyone has had a lot of luck with that option again just pointing it out). Glad you got your problem fixed.

They're enabled by default in Ubuntu, and we certainly try to keep from having to make changes to the OS that deep. That's the case here; we don't disable it, so it's enabled on all of our systems.

---

### Post by Tristan Schmelcher on 2012-02-12
FYI, I also get the irq 19 message on my serp7 and I have found that it is a problem with the IEEE 1394 controller (firewire). I filed a bug at [https://bugs.launchpad.net/system76/+bug/931208](https://bugs.launchpad.net/system76/+bug/931208).

In my case though, the message happens 100% of the time and the machine never hangs. So you are probably right that it is unrelated to your problem.

---

### Post by HunkirDowne on 2012-02-12
> **jschall1 said:**
> ctrl-alt-sysrq R-E-I-S-U-B does not shut the system down, which I think means the kernel has crashed.

Is order of the keys pressed important?  I learned this as R-S-E-I-U-B with the mnemonic, "Raising Skinny Elephants Is Utterly Boring".

---

### Post by isantop on 2012-02-13
They are. Specifically, what this does is:

R - Puts the keyboard into Raw mode
E - Sends a SIGTERM to all processes (asks them to quit)
I - Sends a SIGKILL to all processes (Forces them closed manually)
S - Re-syncs the information on the hard disk, to finish writing data.
U - Re-mounts the root partition as read-only
B - Reboots the system.

You want the E before the I, and they should both come before the S so that data is synced after the processes are closed. That way, nothing can try to write any more data to the drive.

---

### Post by jschall1 on 2012-02-15
> **isantop said:**
> They are. Specifically, what this does is:

R - Puts the keyboard into Raw mode
E - Sends a SIGTERM to all processes (asks them to quit)
I - Sends a SIGKILL to all processes (Forces them closed manually)
S - Re-syncs the information on the hard disk, to finish writing data.
U - Re-mounts the root partition as read-only
B - Reboots the system.

You want the E before the I, and they should both come before the S so that data is synced after the processes are closed. That way, nothing can try to write any more data to the drive.
Do you know if it is important to wait for the sync/unmount to go through before rebooting, or does the sync/unmount block until it finishes?

---

### Post by isantop on 2012-02-16
It *is* important to wait for S-B to finish before proceeding. That said, in most cases, the terminal will come up and tell you when each step is complete. In addition, these steps rarely take longer than a fraction of a second, and even if there's still any doubt, my rule of thumb is to watch the HDD indicator light, and only proceed once it's stopped flashing.

---

### Post by jschall1 on 2012-02-16
> **isantop said:**
> It *is* important to wait for S-B to finish before proceeding. That said, in most cases, the terminal will come up and tell you when each step is complete. In addition, these steps rarely take longer than a fraction of a second, and even if there's still any doubt, my rule of thumb is to watch the HDD indicator light, and only proceed once it's stopped flashing.

In my experience, usually it's the damn nvidia drivers that are at fault for freezing the system and it is impossible to switch to a tty and no terminal appears.
Watching the HDD activity light is probably the best way to go, then...

---

### Post by runny6play on 2012-02-17
It's worth mentioning I have the same issue on a new gazp6 but I get a blank screen and a cursor instead... It also doesnt happen every time.. Sometimes it works other times it doesn't

---

### Post by jschall1 on 2012-02-17
> **runny6play said:**
> It's worth mentioning I have the same issue on a new gazp6 but I get a blank screen and a cursor instead... It also doesnt happen every time.. Sometimes it works other times it doesn't

It's been a while since I've had this issue. You might try updating from ppa:ubuntu-x-swat/x-updates (official x updates ppa), which will get you the nvidia 295.20 drivers.

Apart from that, not certain... If it persists I would talk to system76 about warranty.

---


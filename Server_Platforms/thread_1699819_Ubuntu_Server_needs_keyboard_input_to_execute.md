---
title: "Ubuntu Server needs keyboard input to execute"
date: 2011-03-04
forum: Server Platforms
---

### Post by bayners123 on 2011-03-04
Hi all!
I've been trying to set up a server for my LAN but am running into a weird problem: any commands that I execute will only run while I'm holding any key on the keyboard. I seem to get 1-2s of time after a key press, after which the process just pauses and sits there until I press another key. This is obviously not ideal for what is meant to be an unattended server! Any ideas? 
I'm running a default Ubuntu Server install with nothing except Sun's Java added to it. 

Thanks!

---

### Post by volkswagner on 2011-03-04
Can you ssh into the server?

---

### Post by bayners123 on 2011-03-04
> **volkswagner said:**
> Can you ssh into the server?

I haven't tried: at the moment I've got a keyboard and monitor attached but I want to get rid of them eventually.

---

### Post by garfonzo on 2011-03-04
What about changing the BIOS setting so that the keyboard does not need to be plugged in for the system to boot up? 

I have not had the problem you are describing (which is bizarre!), but perhaps this BIOS setting may help.

---

### Post by bayners123 on 2011-03-04
Booting up isn't the problem: everything works as expected before I get into linux. I've got grub set up to boot straight into Ubuntu as it is. The problem starts once the server is going; after I log in any commands just hang there. There's no error message and they just resume again as soon as I hold a key. 
I'm not sure if it affects processes running as services in the background before I log in. I'll set sshd to run and try connecting to it from another computer.

---

### Post by papibe on 2011-03-04
Have you tried another keyboard?
Regards.

---

### Post by dtfinch on 2011-03-04
Does booting with the nolapic_timer kernel option make any difference?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822)

---

### Post by bayners123 on 2011-03-17
Sorry about the slow reply and thanks for all the help! dtfinch, your solution worked like a charm. I'd assumed that I was doing something wrong so didn't think to look in the bugs.

---


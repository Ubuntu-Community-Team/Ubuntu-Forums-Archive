---
title: "Skype install failed, now computer won't boot"
date: 2016-10-13
forum: Ubuntu/Debian BASED
---

### Post by veddox on 2016-10-13
Hey everyone,

I am currently facing the weirdest problem I have so far encountered on Linux. Some time ago I set up my sister's laptop with elementaryOS 0.3 (basically Ubuntu 14.04 with a different DE). Yesterday she asked me to install Skype, so I downloaded the relevant package from skype.com (Skype for Ubuntu 12.04 multiarch was the newest Ubuntu package available). I opened the downloaded package with the Software Center, but it refused to install, citing a missing dependency. To get a more detailed error message, I then tried installing the skype package using dpkg in terminal, which gave me a list of missing dependencies.

At this point I noticed that the installation must have already gone part way, because there was an entry for Skype in the desktop launcher. Clicking on this didn't do anything though, and attempting to run 'skype' from terminal simply gave the error message '/usr/bin/skype does not exist' (even though there was *some* kind of file there). Anyway, I went back to the missing dependencies and tried to install them manually with apt-get. However, nothing would install as apt told me that my packages were 'in an inconsistent state' (or something like that, I don't remember the precise wording). The error message did suggest I run ```
apt-get -f install
``` to fix the problem. This I did, and was suddenly faced with a surprisingly long apt operation in progress. I started to get worried when I read a line that said 'removing elementary-desktop'. After the operation finished, I noticed that somehow, about half the user programs had disappeared from the launcher (Firefox had gone, though Thunderbird was still there, etc.). Also, the currently open windows were failing to respond. Thinking the computer had hung itself up, I rebooted. Or tried to, at least, because once the computer had shut down, it wouldn't start again...

So here's the current situation: I cannot boot eOS. Grub runs fine and takes me on to the Plymouth boot splash, but no further. I've used the 'advanced options' boot in grub to get into recovery mode. Running the dpkg option there doesn't seem to do anything. Dropping me into a root shell kinda works, except it tells me I'm on a read-only file system so I can really only have a look around. Booting from the recovery mode shows that boot hangs at 'Starting CUPS printing spooler/server'.

Fortunately, I still had an old version of Mint installed on the same laptop, and that still works. I booted it and tried to chroot into the eOS partition, but that failed with the error message ```
chroot: failed to run command 'bin/bash': Exec format error
``` Trying to run bash (or any other program in the /bin folder of the eOS partition) failed with ```
bash: bin/bash: cannot execute binary file
```

So I'm kinda stumped right now, the only thing I can think of is a reinstall of eOS. (All user data is safe, that was on a different partition.) But before I commit to wiping the current install, I wanted to ask around if anybody here has any ideas of a) what the heck is going on and b) how to fix it? I much appreciate any replies :-)

---

### Post by howefield on 2016-10-13
Thread moved to "*Ubuntu/Debian BASED*" forum.

---

### Post by veddox on 2016-10-13
Thanks for moving it, I wasn't aware of that subforum. Unfortunately, elementaryOS doesn't have it's own support forum that I could have posted to, and as it's very similar to Ubuntu under the hood, I thought I would just try and bring the issue up here...

---

### Post by howefield on 2016-10-13
You are more than welcome to bring the issue up here, but as non Ubuntu the thread goes here.

For info, there are unofficial [support forums]("https://elementaryforums.com/index.php") for elementary as well as the more official [stack exchange]("https://elementaryos.stackexchange.com/").

---

### Post by veddox on 2016-10-13
Ah, great, I hadn't seen the unofficial forums yet. The style of the question didn't really seem appropriate for stack exchange.

---


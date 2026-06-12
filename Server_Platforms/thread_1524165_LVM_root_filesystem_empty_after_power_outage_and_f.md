---
title: "LVM root filesystem empty after power outage and fsck?"
date: 2010-07-04
forum: Server Platforms
---

### Post by prolixalias on 2010-07-04
Hello. Please help.
 
Ran into something I don't understand today... My co-worker discovered an Ubuntu 9.10 Server 64-bit box we support was down. He went into the datacenter and found it powered off. Another box in that same set of power outlets was also off. There was some kind of power failure/glitch - yet to be determined.
 
Anyway, he powered up both (same hardware, same OS) boxes... Both had an issue booting, ran fsck, one came up. The other did not.
 
The one that failed to boot, he tells me, complained about:
 
  dev didn't exist
  sys didn't exist
  proc didn't exist
 
[COLOR=black]So, I stepped him through booting to the Karmic CD, chosing "Recover" and got to a command prompt. Output from lvdisplay was encouraging. We used 'vgchange -ay' then mounted it up under /mnt.[/COLOR]
 
The only item was "lost+found" somehow! Are we out of luck? Any suggestions or tips? Getting nervous.
 
Many thanks!

---

### Post by modmadmike on 2010-08-23
> **prolixalias said:**
> Hello. Please help.
 
Ran into something I don't understand today... My co-worker discovered an Ubuntu 9.10 Server 64-bit box we support was down. He went into the datacenter and found it powered off. Another box in that same set of power outlets was also off. There was some kind of power failure/glitch - yet to be determined.
 
Anyway, he powered up both (same hardware, same OS) boxes... Both had an issue booting, ran fsck, one came up. The other did not.
 
The one that failed to boot, he tells me, complained about:
 
  dev didn't exist
  sys didn't exist
  proc didn't exist
 
[COLOR=black]So, I stepped him through booting to the Karmic CD, chosing "Recover" and got to a command prompt. Output from lvdisplay was encouraging. We used 'vgchange -ay' then mounted it up under /mnt.[/COLOR]
 
The only item was "lost+found" somehow! Are we out of luck? Any suggestions or tips? Getting nervous.
 
Many thanks!
A
I had the same problem on a workstation system... as it turned out a SMART status proved one of the physical volumes had Bad sectors that were yet to be relocated... I was forced to zero fill each of the physical volumes :(

---


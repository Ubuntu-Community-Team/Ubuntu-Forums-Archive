---
title: "How to delete local traces?"
date: 2010-12-14
forum: Security
---

### Post by mehmeh12 on 2010-12-14
I want to scan some documents in paper form from my scanner onto a encrypted usb key. I will not be copying any files to the local hard drive. I assume that doing this will however make logs of what happened on my local computer? if i delete the logs and then delete the logs again using bleachbit will these traces be unrecoverable? 

or would i be better off using a live cd of some sort and bypassing the entire local system altogether?

---

### Post by CharlesA on 2010-12-14
I don't think there are any logs that record that sort of thing.

If you are concerned about it, just use a livecd.

---

### Post by The Cog on 2010-12-14
Given that I don't know what temporary files are created by the scanner, I would be inclined to use a live CD. Also, use the command **sudo swapoff -a** before scanning to prevent it using the swap space and leaving traces on there.

---

### Post by mehmeh12 on 2010-12-14
ok so the consensus is that a live cd would be best. Just to clarify a live cd does not leave any traces on the host machine yes? 

which distro would be best for privacy? i have ubuntu 10.04 and 10.10 live cds lying around-would these be ok? 

On another note while on the installed system if i read and open files like those png files ive made with the scanner does the host system make logs of this?

---

### Post by CharlesA on 2010-12-14
It might be listed somewhere if you opened them, but the only thing that would be shown would be the filenames.

If you turn swap off and use a livecd, you'll be fine.

---


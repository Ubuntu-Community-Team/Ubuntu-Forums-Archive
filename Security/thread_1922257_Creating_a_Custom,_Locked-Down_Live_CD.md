---
title: "Creating a Custom, Locked-Down Live CD"
date: 2012-02-08
forum: Security
---

### Post by toseethefruit on 2012-02-08
Hello everyone,

I'm not sure whether I've posted in the correct place, but I'd be very grateful for any help you might be willing to offer to me.

I have a question I've been trying to solve with very little success. I have a friend who is running a research project with some new (and as-yet untrained) Research Assistants. The data that they are working with are video interviews, and the research program is requiring her to do everything she can to make sure that those videos can't be copied (and, e.g., posted to YouTube) by any of the Research Assistants. It's not possible to force the Research Assistants to do all of their work in a central location, unfortunately.

I found Ubuntu Privacy Remix ([https://www.privacy-cd.org/en/tutorials/build-your-own-cd](https://www.privacy-cd.org/en/tutorials/build-your-own-cd)), which disables networking and makes all removable media mount noexec. I'm wondering whether I might do something similar, but disable all removable media (so that the Research Assistant could not burn a CD or mount a USB drive), and retain networking but somehow use IPTables to block all network connections except those to a single address, where my friend could host an SSH server and keep all of the data (and allow the Research Assistants to save their edits, using "Connect to Server" in Nautilus). Thus, the only way in or out of the LiveCD would be through this one network connection, which preferably would require an RSA key).

Would anyone be willing to point me in the right direction for figuring out how to disable all external device mounting in the script at the above page? I've done a lot of searching and can't even figure out how to do it in a full install of Ubuntu. If I may ask, as well, is there a way to modify the above script to use IPTables and install a RSA key? I know how to do these in a full install (and could perhaps use RemasterSys to create a LiveCD from that), but don't know how to do it in the context of a bash script.

I'm very grateful for your help. Thank you very much!

My best,
J.L.

---

### Post by WthIteh on 2012-02-08
> **toseethefruit said:**
> It's not possible to force the Research Assistants to do all of their work in a central location, unfortunately.
So how it may be possible to force them to boot your specially created live CD at all?
They can boot using another system and then look in your created CD to find anything.

Put in other words, you either give them videos on the CD or on a server. If videos be put on the CD, they could copy it by booting another OS. If videos be put on the server, they could download it from another computer (independent from your CD). If you require them to have a RSA key (burned on CD) to work with server, they can first copy that RSA key from another OS and then use it for connecting to server.

---

### Post by toseethefruit on 2012-02-08
Hmm, good point, WthIteh. Just getting that feedback helps a lot -- I think that I may need to take a step back and re-assess the approach I was considering. Thank you!

---

### Post by C.S.Cameron on 2012-02-08
What if the videos were located in an encrypted home folder?

---

### Post by WthIteh on 2012-02-09
> **C.S.Cameron said:**
> What if the videos were located in an encrypted home folder?
It just adds another step for decrypting the home folder. The live CD must have a method for decrypting home folder (usual way is to either ask a passphrase or use user login passphrase). In either way, they now the passphrase too. So they can decrypt home folder using another live CD (installing lucks, etc.).

There is a general rule which says: "Everyone with *physical access* to a machine can break in independent of security measures".

---

### Post by OpSecShellshock on 2012-02-09
If these assistants need to be able to view or otherwise use/manipulate the video files, then due to the nature of how things work there will always be a clear copy on their computers at some point. The best solution here is probably more contractual than technical.

---


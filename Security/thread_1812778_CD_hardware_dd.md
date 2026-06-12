---
title: "CD hardware dd?"
date: 2011-07-26
forum: Security
---

### Post by fela on 2011-07-26
Hi

How can I dump the contents of an encrypted CD so that I have an .iso file with each bit mapping to the pits on the CD? I tried dd and the encryption broke, so it obviously didn't do a pit-for-pit copy.

Thanks

---

### Post by psusi on 2011-07-26
Do you mean an encrypted dvd?  Because CDs don't support hardware encryption.

---

### Post by doas777 on 2011-07-26
there are a number of tricks that cd distributors can use to make disks hard to rip, including throwing errors (that the decoder is supposed to know to ignore), skipping blocks, etc.

---

### Post by HermanAB on 2011-07-27
Use dd, ddrecover, cat or k3b:
# dd if=/dev/cdrom of=filename.iso
# cat /dev/cdrom > filename.iso

---

### Post by fela on 2011-07-27
Hi

Well it's a Seaclear charts CD, don't know if that rings any bells.

I tried ```
dd if=/dev/cdrom of=file.iso
```, but upon mounting that using Virtual Clonedrive under windows it threw an error saying 'encrypted CD/DVD not found'.

You're right, it is a DVD not a CD :P

I wonder if using cat instead of dd would have a different effect - I'll try that next ;)

---

### Post by psusi on 2011-07-27
If the DVD is encrypted, then dd should fail with with a bunch of errors, but this is usually only the case on videos.  Copy protection BS is another matter entirely where they intentionally insert errors into the disk that are automatically corrected when read with dd.

The best thing to do is refuse to pay for such crippleware.

---

### Post by fela on 2011-07-27
Hmm, well the thing is I didn't pay for it - it was supposed to be a favour for someone, as their computer doesn't have a CD drive. However it's looking like they made it pretty impossible to copy :(

---

### Post by psusi on 2011-07-28
Can this "virtual clonedrive" mount a cue+raw image?  If so then using cdrdao to rip it that way might help.  Some copy protection schemes embed data in the subchannels that you can only get in raw mode, but that doesn't give you an iso.

---

### Post by fela on 2011-07-31
I'm not sure, but I've since given up on trying to crack it as I'm pretty sure the validation has something to do with the hardware ID of the CD (or something along those lines). :(

---


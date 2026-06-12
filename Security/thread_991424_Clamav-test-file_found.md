---
title: "Clamav-test-file found"
date: 2008-11-23
forum: Security
---

### Post by josephellengar on 2008-11-23
I did a clamscan and clamav gave the above error as I virus for a bunch of files.  They were just tarballs of clamav.  Should I worry about this, or is this a false positive or something?  I have attached two of the files.  Thanks!

---

### Post by cariboo on 2008-11-23
Those are both Windows executeables. Are they part of the clamav installation? Where did they come from?

To find out if they are part of the clamav package go to System-->Administration-->Synaptic Package Manager, and search for clamav, when synaptic finds it highlight the package then click the properties  button and select installed files. If the files are part of the package they will be in the listing.

If they aren't a part of the clamav package you can safely delete them.

Jim

---

### Post by josephellengar on 2008-11-23
> **cariboo907 said:**
> Those are both Windows executeables. Are they part of the clamav installation? Where did they come from?

To find out if they are part of the clamav package go to System-->Administration-->Synaptic Package Manager, and search for clamav, when synaptic finds it highlight the package then click the properties  button and select installed files. If the files are part of the package they will be in the listing.

If they aren't a part of the clamav package you can safely delete them.

Jim

Ok, thanks.

---


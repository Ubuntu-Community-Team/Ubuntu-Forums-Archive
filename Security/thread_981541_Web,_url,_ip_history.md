---
title: "Web, url, ip history"
date: 2008-11-13
forum: Security
---

### Post by camrant on 2008-11-13
Wondering if linux stores or logs web, url, outgoing ip addresses, by default?  Outside of what your browser stores itself in its history function.  Are there forensic tools that if used can recover this data or the history of the browser program even if deleted.  What can be done to remove history so that such programs cannot recover.

---

### Post by cariboo on 2008-11-13
Destroy the hard drive. A big hammer (min 8lb) does a good job. :)

Jim

---

### Post by randy78 on 2008-11-13
Jim is right, you will have to destroy the hard-drive, but you'd better use thermite or grind the platters down to dust... Data recovery companies such as OnTrack have pulled data from drives that have been ran through chipping machines, among other disasters.
Granted, this is VERY, VERY expensive, and may only be used in cases of national security, but most of the time a software program like Encase is more than enough to gather enough evidence for a conviction.

Your best bet is to use full disk encryption with a long, random passphrase.

Otherwise, use a LiveCD

---

### Post by baeksu on 2008-11-13
> **camrant said:**
> Wondering if linux stores or logs web, url, outgoing ip addresses, by default?  Outside of what your browser stores itself in its history function.  Are there forensic tools that if used can recover this data or the history of the browser program even if deleted.  What can be done to remove history so that such programs cannot recover.
If you use a regular setup, i.e. you didn't set up squid or other proxies, there won't be any records of these things outside of what the browser (or other programs you used) stores.

Though if you have set up iptables to restrict outbound connections, and have it logging denied attempts, you might find something in the iptables logs.

If you didn't specifically set up any of the above stuff, you have nothing to worry about.

Just deleting the files from the browser history won't overwrite the sectors on the disk, however. If you want to make sure those things are not recoverable, you need to erase the disk, and use something that will write zeroes over each sector at least once. You can achieve this with the "shred" command, just follow [these instructions](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html).

---

### Post by Kinstonian on 2008-11-14
> **camrant said:**
> Wondering if linux stores or logs web, url, outgoing ip addresses, by default?  Outside of what your browser stores itself in its history function.Nope.

> Are there forensic tools that if used can recover this data or the history of the browser program even if deleted.  Yes, there will probably be trace evidence when you clear your browser's history.  When you delete data, it's not really deleted and is still on the drive until it is overwritten.  Contrary to popular belief, you only need to overwrite data once before it is unrecoverable.  The laboratory attacks that people refer to no longer work on modern day drives.  Governments still require multiple overwrites just in case someone once again finds a similar way to recover data.

> What can be done to remove history so that such programs cannot recover.

Don't think in terms of removing data from the hard drive (which is difficult), think in terms of preventing the data from ever being on the hard drive.  If you boot to a Live CD like Knoppix, all the evidence will be contained to memory.  Just make sure you boot by typing **knoppix noswap** if you're using knoppix to prevent it from using the swap partition on the hard drive.

Encryption is another option, but still isn't as safe as preventing the data from being written to disk in the first place.

---

### Post by mssever on 2008-11-15
> **baeksu said:**
> If you want to make sure those things are not recoverable, you need to erase the disk, and use something that will write zeroes over each sector at least once. You can achieve this with the "shred" command, just follow [these instructions](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html).

Note that shred isn't guaranteed to work if used on a journalling filesystem, such as ext3 (Ubuntu's default) or NTFS because the journal often interferes with shred. You can, however, shred the entire partition by passing in the device name. According to the US Defense Department, you need at least seven passes to be effective.

---

### Post by randy78 on 2008-11-15
> **mssever said:**
> Note that shred isn't guaranteed to work if used on a journalling filesystem, such as ext3 (Ubuntu's default) or NTFS because the journal often interferes with shred. You can, however, shred the entire partition by passing in the device name. According to the US Defense Department, you need at least seven passes to be effective.

Check here: [http://16systems.com/zero/index.html](http://16systems.com/zero/index.html)

One pass is enough, plain and simple.

I've never, ever heard of a case where any reasonable amount of data was recovered from any type of formatted disk after a data wipe was performed.
If you can prove otherwise, I'd love to see the results.

---

### Post by mssever on 2008-11-15
> **randy78 said:**
> Check here: [http://16systems.com/zero/index.html](http://16systems.com/zero/index.html)

One pass is enough, plain and simple.

I've never, ever heard of a case where any reasonable amount of data was recovered from any type of formatted disk after a data wipe was performed.
If you can prove otherwise, I'd love to see the results.

I've heard that it's sometimes possible to deduce what was on a drive before it was zeroed because the magnetized bits aren't always set precisely. Whether that's true or not I don't know, since I'm no expert. I also don't know whether the claim in the link you gave is true. I do know, however, that the DoD standard is (or at least was--I haven't kept up) for seven passes with random data. I don't know whether it's based on reality or paranoia.

---

### Post by randy78 on 2008-11-15
From: [http://en.wikipedia.org/wiki/Data_remanence#Feasibility_of_recovering_overwritten_data]("http://en.wikipedia.org/wiki/Data_remanence#Feasibility_of_recovering_overwritten_data")

"Feasibility of recovering overwritten data

Peter Gutmann investigated data recovery from nominally overwritten media in the mid-1990s. He suggested magnetic force microscopy may be able to recover such data, and developed specific patterns, for specific drive technologies, designed to counter such.[2] These patterns have come to be known as the Gutmann method.

Daniel Feenberg, an economist at the private National Bureau of Economic Research, claims that the chances of overwritten data being recovered from a modern hard drive amount to "urban legend".[3] Daniel Feensberg also points to the interesting fact, that the "18 minute gap" Rosemary Woods created on the tape of Nixon discussing the Watergate breakin, has not been recovered. A easy task compared to recovery of a modern high density digital signal.

As of Nov 2007, the DoD considers overwriting acceptable for clearing magnetic media, but not as a sanitization method. Only degaussing or physical destruction is acceptable for the latter.[4]

On the other hand, according to the 2006 NIST Special Publication 800-88 (p. 7): "Studies have shown that most of today’s media can be effectively cleared by one overwrite" and "for ATA disk drives manufactured after 2001 (over 15 GB) the terms clearing and purging have converged."

---

### Post by camrant on 2008-11-18
Would using Squid then be the most effective way to monitor network traffic for a small network?  What kind of information can be gathered?  Does squid intercept data passing through it

---

### Post by Kinstonian on 2008-11-18
You could not only get the data you asked about in your original post, but you would have the benefits of a proxy firewall as well if you used Squid.

If you are really serious about monitoring, you could purchase a passive tap like something from [Net Optics](http://www.netoptics.com/) and connect an Ubuntu Server or FreeBSD server to it so you can run common Network Security Monitoring tools.  See the [NSMWiki](http://nsmwiki.org/Main_Page) for details on NSM.

---


---
title: "Technical question about DMA, reading data off hard drive, multithreading"
date: 2015-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by flyingsliverfin on 2015-08-11
Hi all!
The question is relatively technical, but is almost a simple yes/no answer.
Here we go:

I have some program (written in say Java) in which I want to process a huge amount of data off the hard drive as quickly as possible. I have to read the data off of the drive in pieces (doesn't fit in memory). The basic approach is to send a read command, which fills an array, and then process it, then write the data out elsewhere; repeat as long as needed.
What I want to know is if the 'read' command consumes CPU cycles while the hard drive fills the array of data I need. That is, is the CPU simply blocking while waiting for completion, or actively involved? I'm asking because I'm thinking of trying to speed up my program by keeping the disk as busy as possible all the time by putting a load of read/write requests in a queue that get processed in a thread specific to the file operations. Meanwhile, the another thread can do all the relevant processing of data that is already available.

In short, does the CPU "hand off" the read or write operation to some hardware subsystem or not?
 I can imagine this would be the case because of things like DMA, but I'm not sure. I could also reason that this varies OS by OS, or even by which system call is used - in which case, is there a normal behavior on linux?
Relevant literature might be of interest to me as well!

Thank you

---

### Post by col48 on 2015-08-12
I don't know the answer, but I could imagine that you could easily get into a mess in a high-level language (which I think Java is...).
I can envisage that a specific hardware/software configuration could behave perfectly compatibly with a piece of code but a small tweak to one or the other could make the synchrony between hardware and software fall down, especially if using multi-threading.  This looks like a case for a bit of low-level code to me, if you can find someone to write it.

Good luck!

---


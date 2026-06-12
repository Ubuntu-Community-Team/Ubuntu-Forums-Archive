---
title: "rsync - asymmetrical system demands?"
date: 2008-02-19
forum: Server Platforms
---

### Post by jmidgley on 2008-02-19
Hi

I was pointed to rsync as the solution to my backup needs. After much googling, I have now got it running with rsync --daemon on my ubuntu machine and "rsync -vae 'ssh -p [portnum]' john@server:/dir_there/stuff /dir_here". This command is run on an NSLU2, which is a pretty minimal NAS box modified to run Linux accessibly.

My question - as I understand it, I can either run the daemon on the box with the data and pull it from other, or run the daemon on the box *without* the data and push it from where the data is. (Finally, the question: ) which will be less work for the NSLU2? Does the daemon use less resources than the command line rsync?

Cheers
John

---

### Post by MJN on 2008-02-19
The best way to answer that is probably to try it!

Howcome you're using the daemon at all, and not just an rysnc client at either end of an SSH connection?

Mathew

---

### Post by astrotech226 on 2008-02-19
What I like to do is run the rsync command on the more important (or busier) server and run it using "nice".  That way, it helps limit how much CPU time is spent on the sync.

And like MJN, I don't typically use the daemon.

---

### Post by jmidgley on 2008-02-20
[Patrick's voice from Spongebob] ...Uhhhhhhhh....

I thought you had to run the daemon at one end or the other. I must have misread the destructions.

What I'm hoping to get to is a cron job that can run an rsync command occasionally. Would I need to somehow synchronise commands to run at the same time?

Back to the Howtos for me...

Cheers
John

---

### Post by MJN on 2008-02-20
I think it's a common mistake to make - so don't feel too bad!

You only need rsync *installed* at both ends. Then, when you run rsync at one end (and the source/destination is remote i.e. user@host:/path/) then it'll open a SSH shell (via standard port 22 unless told otherwise) at the remote end and invoke rsync on that machine. Hence, no need for a daemon sat there listening!

Mathew

---


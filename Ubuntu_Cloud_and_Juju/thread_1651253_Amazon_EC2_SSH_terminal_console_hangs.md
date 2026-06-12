---
title: "Amazon EC2 SSH terminal console hangs"
date: 2010-12-22
forum: Ubuntu Cloud and Juju
---

### Post by photonymous on 2010-12-22
Preface: I have Googled around on this problem, but I'm a bit of a newb, and perhaps don't know the right search terms....

I've just created a new Amazon EC2 instance using a public Ubuntu image (10.10). (I'm using 10.04 locally).

When I SSH into my running instance, I can kindof navigate around OK, but when I try to do anything that requires dumping a bunch of characters to the console window, the console totally hangs (locks up). Ctrl+C doesn't work.

For instance, I can't do a directory listing if the directory contains too much stuff, and I can't cat a file if the file's too big. However, I can redirect the output of such a command to a file, and the file gets created correctly. Here's a command that consistently hangs the terminal:

> ls /proc/

Why is it hanging when I try to output more than, say, 1000 characters to the console window? 

Much thanks to anyone who can help!!

---

### Post by kim0 on 2010-12-23
interesting! can you check if there's packet loss to your instance. Try pinging it like 

ping -c 30 <public-ip-of-instance>

---

### Post by photonymous on 2010-12-23
Thanks for the assistance! So, I did what you suggested, but sadly, I think we're up against non-deterministic software... my least favorite kind.

The external ping results caused my local terminal to lockup, requiring a (successful) ^C:

 > ping ec2-184-73-45-29.compute-1.amazonaws.com 
PING ec2-184-73-45-29.compute-1.amazonaws.com (184.73.45.29) 56(84) bytes of data.
^C
--- ec2-184-73-45-29.compute-1.amazonaws.com ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7002ms
 > 

However, the previous symptom has gone away! I can now do something as crazy as a recursive directory listing starting at "/" with no problems at all. What the heck?!?!  Well, I guess I don't care if I can't ping it, so long as I can SSH in and play around without fear of a lockup.

If you have any thoughts on what the problem might be, in case the symptom rears its head again, please feel free to share your thoughts. Regardless, thanks for the help.

Cheers,
 - Erik

---


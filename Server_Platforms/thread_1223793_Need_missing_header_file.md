---
title: "Need missing header file"
date: 2009-07-26
forum: Server Platforms
---

### Post by Malcrow on 2009-07-26
I search all over but I can't seem to find the answer.

I am trying to build a program for school and it calls for mkdev.h

My install does not seem to have this.  

I did apt-get install build-essentials

Any other suggestions?

---

### Post by aesis05401 on 2009-07-26
Hello Malcrow. 

Did the assignment come with some prerequisites - like a list of library versions to target?  If so, you may need to have the exact library version in order to find package names matching. 

I hope someone will correct me if I am wrong on this, but mkdev headers are not on deb systems because mknod is used instead.  If you want to create a device manually you should be using mknod to actually create the special file.  udev is the system that handles on the fly device mounting/unmounting etc..

There are some hits for mkdev.h on gnu.org, but only in reference to autoconf checking to see if mkdev is actually present and holding some parameter values. 

That makes me think we are dealing with a deprecated lib.  I see refs to 'MAKEDEV' over on lkml, but I also see that referred to as a macro.

Anyone have better advice for our studious young friend?

---

### Post by aesis05401 on 2009-07-26
Now it occurs to me - are you supposed to be in a traditional Unix environment for this homework?

If so, I might be able to point you in a better direction.

---

### Post by Malcrow on 2009-07-27
> **aesis05401 said:**
> Now it occurs to me - are you supposed to be in a traditional Unix environment for this homework?

If so, I might be able to point you in a better direction.

Yeah I have been doing my work on ubuntu and then using scp to send it to unix to double check it is all still working properly.

I did send my files back to the unix server and everything is working.

If you have some ideas I would be glad to hear them I prefer to do my work on my server.

Thanks for answering my post.

---


---
title: "xen 3.1 nvidia problem"
date: 2007-12-26
forum: Virtualisation
---

### Post by perfecxion on 2007-12-26
having some trouble with Xen. It just doesn't want to load nvidia drivers. I've looked all over the net and now very confused. Some people say you can patch the nvidia modules to make it work others say you just can't do it. but either way this is what i have done:

1. made the nvidia modules work with kernel 2.6.22-14-generic. The was i did this is get the installation script from nvidia.com and get the kernel source for 2.6.22 then compile it and it worked. 

2. I log into xen and it doesn't load the modules so i decide to look for the kernel source for 2.6.22-14-xen. and there is none. so i go to plan B.

3. I download some package that say linux-restricted-modules-2.6.22-14-xen. That didn't work. So then I go to my last step.

4. I start looking on the net and says uses these patches and it should work. Sorry I don't have the links to them but I see this post also talks about patches [http://ubuntuforums.org/showthread.php?t=292971](http://ubuntuforums.org/showthread.php?t=292971)
and that didn't work. so then i just started downloading a whole bunch a stuff and hoped that worked and it didn't.

well that's everything i've done up to now i hope that's enough info for some of you to help me.

o btw i'm using xen 3.1 not 3.0. I've seen a whole bunch of stuff for 3.0. I tried some of that too but didn't work either.

---


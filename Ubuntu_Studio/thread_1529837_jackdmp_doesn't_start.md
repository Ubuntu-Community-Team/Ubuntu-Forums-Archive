---
title: "jackdmp doesn't start"
date: 2010-07-12
forum: Ubuntu Studio
---

### Post by GhostofJohnToad on 2010-07-12
So I have heard that running jackdmp can increase efficiency with multiprocessors.  I see it is an option and tried to set it using qjackctl and it fails.  I have a dual processor and it fails with just "Could not start Jack. Sorry."  running as jackd everything runs fine.  

just trying to make sure I have everything optimized as much as possible, on my system and was curious about the option.  if it's not a big gain I'm not going to fret it.

---

### Post by cchhrriiss121212 on 2010-07-13
I had this problem when trying out jack2, what you need to do is install it without having regular jack installed, otherwise jack2 will try to use the original settings.
If you are getting good latency/stability now then I think it would be a minimal upgrade.

---

### Post by GhostofJohnToad on 2010-07-13
Thanks chris.  Shouldn't there still be a way to change the settings without uninstalling the "regular" jack?

---

### Post by Pablo_F on 2010-07-13
Hi, 

Afaik, jackdmp, or jackmp in general, is nowadays known as jack2. You can check your jackd version by typing in a terminal:

jackd --version

 If the version number begins with a 0, then you have jack1 (the original jack)

On the other hand, even if you had installed jack2 (version number beginning with a 1) you shouldn't use "jackdmp" in qjackctl, just jackd [1]. 

This is, there is a unique command for both branches of jack. The confusion comes because qjackctl has some options, like jackdmp or jackstart, which are deprecated but nobody has swept away yet from the configuration file.

EDIT: Jack1 and Jack2 are incompatible, you install one or the other but not both at the same time. I think falktx's ppa has jack2. 

[1]: For jack2,"jackd -S", this is synchronous mode, seems to work better. 

They know better here:

[www.http://jackaudio.org](www.http://jackaudio.org)

---

### Post by GhostofJohnToad on 2010-07-13
well using: ```
 jackd -S 
``` in the server line worked great. 

It seems my cpu usage has gone down a slight bit and I am not getting the odd xrun that I did before.  I twas very infrequent before but now it's more solid.  

Thanks for the tip!

---


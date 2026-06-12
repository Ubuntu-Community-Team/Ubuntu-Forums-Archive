---
title: "Running Swami Soundfont Editor in Ubuntu Studio 11.04"
date: 2011-07-31
forum: Ubuntu Studio
---

### Post by mwinthrop on 2011-07-31
Hi - I am new to Ubuntu Studio having installed it as a dual boot capability on my Dell 1555 computer about 3 weeks ago.  This is my first experience with Linux and so far I like it.  I have had some successes using Ubuntu Studio.  In the last 3 weeks, I have figured out how to use Jack at least well enough to make Pianoteq (Linux version), QSynth, Rosegarden, and Ardour work on my computer.  I have also been successful in connecting my midi keyboard to my computer and it is working well with Pianoteq through Jack.
 
I have installed Swami on my machine using the Ubuntu Software Center and when I try to run it, it  says it is starting up in the panel bar, but then it just disappears and  does not run.  Note I started Jack before running Swami.  I have searched on Google and in the Ubuntu forum and  can't seem to find anything similar to the problem I have, though maybe I missed the answer somewhere.  In my searching, I was inspired to try to run Swami in a terminal window, so I tried that next.  I received the following text:

libswami-Message: Loading plugins from /usr/lib/swami
libswami-Message: Loaded 4 plugins
JackActivationCount::Signal value = 0 ref = 3
JackActivationCount::Signal value = 0 ref = 3
JackActivationCount::Signal value = 0 ref = 3

(swami:2759): libInstPatch-CRITICAL **: ipatch_type_get_valist: assertion `type != 0' failed
Segmentation fault

Could anyone help me understand what is going wrong and what I ought to do to fix this?  Thanks much.

---

### Post by Pablo_F on 2011-07-31
Are you running the 64 bit US? See [https://bugs.launchpad.net/ubuntu/+source/swami/+bug/810569](https://bugs.launchpad.net/ubuntu/+source/swami/+bug/810569)

---

### Post by mwinthrop on 2011-07-31
I am running the 64 bit US.  Thanks Pablo_F for pointing out the bug report.  I did not see it when I searched the web.  I have added my comments to the bug report and I am hoping it will be easy to fix.  That answers my question - I will keep an eye out for an update.

---


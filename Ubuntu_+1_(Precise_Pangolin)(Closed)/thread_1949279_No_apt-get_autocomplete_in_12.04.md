---
title: "No apt-get autocomplete in 12.04?"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clegends on 2012-03-29
This is weird, and I haven't run across this problem before. While the Ubuntu Software Centre is improving by leaps and bounds, it's still too slow, buly, and resource hungry for my liking. Currently though in the latest build of 12.04, apt-get seems borked. I can no longer use the handy 'autocomplete' function. I.e., running:
```
 sudo apt-get install unison 
```
And hitting "Tab", should give me a list of all the possible unison packages I can install. This no longer works. Can anyone help me troubleshoot this, or have I found a bug? Cheers.

---

### Post by Space_Balls on 2012-03-30
```
alex@apollo: ~
$ _ apt-get install unison                                            [8:42:08]
unison             unison2.27.57-gtk  unison2.32.52-gtk                   
unison2.27.57      unison2.32.52      unison-gtk 

```
works for me.

Does bash completion work for all the other commands? If the following bash code is in your .bashrc or .profile
```

if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```
and bash-completion is installed, it should work

---

### Post by clegends on 2012-03-30
Thanks for that, you pointed me in the right direction. Working fine now. I had actually deleted my .bashrc, .profile, and .bash_logout files... due to having reinstalled 12.04 over my 11.10 instllation, using the same /home paritition. Ended up borking the install, as the configuratioin was different. Rather than sorting out the problems, I decided to erase all my non-data holding files and folders, including those mentioned above. I just assumed that on first login they would be recreated. Well, most were, but not the .bash files apparently.

I created another user (admin, though I doubt that is necessary) and copied those missing files across. Thanks heaps, soooo nice to have a working apt command line working again. The Ubuntu Software Centre doesn't do it for me. 

Cheers.

---


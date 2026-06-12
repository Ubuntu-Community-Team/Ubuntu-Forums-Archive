---
title: "ltsp installation"
date: 2005-01-31
forum: Server Platforms
---

### Post by hyspah on 2005-01-31
hello 

i manage to download the ltsp 4.1-0. iso 
i the mounted it on /mnt/ltsp 

after installing ltsp-utils-0.10.tgz

i did this: sudo apt-get install libwww-perl to get ltspadmin working...

now ltspadmin now works...

after invorking sudo ltspadmin, i gave my ltsp 4.1-0. iso's path as file:///mnt/ltsp

i had this error message after selecting Install/Update LTSP Packages within ltspadmin:


 [ ]                                  0   Not installed Use of uninitialized value in hash element at /usr/sbin/ltspadmin line 651.
leave this screen by pressing 'Q', the components will be installed.   'H'-HelpUse of uninitialized value in hash element at /usr/sbin/ltspadmin line 651.
Use of uninitialized value in division (/) at /usr/sbin/ltspadmin line 672.
Use of uninitialized value in sprintf at /usr/sbin/ltspadmin line 672.

i went into /usr/sbin/ltspadmin to find out what was wrong but i could not understand the codes especially the line 651 and 672 which looks like this::

 return($self->{hash}->{$aComponents[$idx-1]}); (line 651)
 return(sprintf($fmt, $sel, $comp->{name}, (line 672)

and to be frank i can't just figure out what i should  replace the {hash} and {sprintf} with as stated in the error message i have posted above.

any one with an idea.

Joe Zicarelli.... if you happen to be a member of the mailling list i will like to hear from you, since i am following you tutorial

thanks.
 :!:  :!:  :!:

---

### Post by DagaZ on 2005-02-02
Which version of Ubuntu are you running Warty or Hoary? I have successfully installed LTSP on Warty. Not that this statement helps you in any way, but at least now you know it is possible to get it to work.  ;-)

---


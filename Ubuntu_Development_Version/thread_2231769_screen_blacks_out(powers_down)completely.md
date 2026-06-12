---
title: "screen blacks out(powers down)completely"
date: 2014-06-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-06-27
Running Utopic,  fully updated (non Unity8). I was researching a processor and went to this site:

[http://www.overclock3d.net/reviews/cpu_mainboard/amd_athlon_ii_x2_250_processor_review/1](http://www.overclock3d.net/reviews/cpu_mainboard/amd_athlon_ii_x2_250_processor_review/1)

After about 2 minutes of reading, the screen went blank . Could not recover. had to reboot. All other pages still loaded. No problem.

*note* Although this install does n


---

edit

Wow .. the above was saved and I didn't even save it. I am writing this from another install on the same PC. It had nothing to do with the web page. Just sort of like a random blackout.  I was trying to make a point that this install was not an original unity8-next install but a standard unity7 install.

  if it was a hack .. then .. nice hack :)lol

---

### Post by grahammechanical on 2014-06-27
> [COLOR=#000000][FONT=Verdana]In June of this year, AMD launched it's budget/mainstream line of processors named Athlon II. Asleep already?[/FONT][/COLOR]

My screen blacked out as I was watching top. I had fallen asleep. :) That web page uses a lot of CPU cycles. Need to overclock just to view the page. :)

Regards.

---

### Post by ventrical on 2014-06-28
:)

What I mean to say is that there is a serious bug (or java script perhaps) that has borked my install. And I have no idea what it is. One possible indicator is that there was an apport warning that came in with yesterday's updates but those  bug reports tell us nothing as they are contained.

---

### Post by ventrical on 2014-06-28
Some program called /powerd

Here it is.

 I'll send the bug report.

---

### Post by ventrical on 2014-06-28
Here is bug .

[https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1335395](https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1335395)

---

### Post by ventrical on 2014-06-28
powerd is for phones. This is an interfection from unity8 convergence process and obviously what is causing monitor power-downs.

[https://wiki.ubuntu.com/powerd](https://wiki.ubuntu.com/powerd)


Regards..

---

### Post by ventrical on 2014-06-28
No reboot required. You can just hit the power button and then all shutdown/restart options will come on screen and you can click x to continue your session.

---

### Post by grahammechanical on 2014-06-28
I am not getting that bug. I am now getting

colord-sane crashed with SIGABRT in-assert-fail-base

Regards.

---

### Post by ventrical on 2014-06-28
I also got this unity8 bug when running it from terminal:

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1335404](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1335404)


 and I just want to be clear that the current Utopic install in question was an original rolling release from Saucy that I had added the Unity8 from the repos. This activity just started from yesterdays updates of unity8 and mir rack.

 I am also getting this:

> 

                        Thank you for your report!
 However, processing it in order to get sufficient information for the
developers failed (it does not generate a useful symbolic stack trace). This
might be caused by some outdated packages which were installed on your system
at the time of the report:
 no debug symbol package found for powerd
 Please upgrade your system to the latest package versions. If you still
encounter the crash, please file a new report.
 Thank you for your understanding, and sorry for the inconvenience!

              
                                                [TABLE="class: bug-activity"]
[TR]
[TD="align: right"]         **tags**:       [/TD]
       [TD]         removed: need-amd64-retrace       [/TD]
[/TR]
[/TABLE]




and it sort of adds insult to injury.

:)

 regards..

---

### Post by ventrical on 2014-06-28
I went to :

/ect/init/powerd.conf and edited all the lines out with the expectation that it would be a temp workaround but no luck. screen still blanking/powering down after about a minute.

```

#author "Michael Frey <michael.frey@canonical.com>"

#start on started dbus and android

#respawn

#env ANDROID_ROOT=/system
#uncomment the line below to enable debugging
#env POWERD_DEBUG=1

#exec /usr/bin/powerd


```

---

### Post by ventrical on 2014-06-28
I was hacking around a bit in system settings and yet another bug reared up:

[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335432](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335432)

---

### Post by ventrical on 2014-07-05
Ok . here is the powerd bug.

[https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1338021](https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1338021)


 I assume that it is this that is causing screen powerdowns.

---

### Post by ventrical on 2014-07-05
This issue appears to be solved after recent update/upgrade.

---


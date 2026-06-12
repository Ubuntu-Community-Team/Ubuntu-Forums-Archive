---
title: "Daru2 hibernates irregularly"
date: 2008-11-03
forum: System76 Support
---

### Post by j.c.sackett on 2008-11-03
My laptop (a daru2) is periodically failing to hibernate. The screen goes black (though it is still backlit) and it sounds like the fan kicks up, but it doesn't hibernate, even if I wait for about 15 minutes or more.

I've mucked about with some of the settings, but I can't seem to change it, and I can't say I'm doing it with any real idea of what I'm doing.

Any help?

(Sorry to post two problems in one day, but today is the day they've both become noteworthy in their bothersomeness).

---

### Post by thomasaaron on 2008-11-03
Intermittent problems can be tricky to pinpoint.

Is there any common denominator? A particular program that might be opened up when it fails?

Run these two commands from a terminal immediately AFTER a failed resume:

cat /var/log/messages > ~/Desktop/messages.txt
cat /var/log/syslog > ~/Desktop/syslog.txt

These will create log files on your desktop that you can attach to this thread. Perhaps that will help us isolate the problem.

---

### Post by j.c.sackett on 2008-11-03
Well, if it helps, it more often fails then not. I can't seem to find a common thread, but I'll watch it, and post back here with those msgs after the next failure.

Thanks.

---

### Post by thomasaaron on 2008-11-03
OK. One other thing. Are you using 64-bit Ubuntu?

---

### Post by j.c.sackett on 2008-11-04
No, 32 bit Intrepid. The problem has been observed on 32 bit Hardy as well.

---

### Post by thomasaaron on 2008-11-04
We've gotten reports that hibernate works fine with 64-bit Intrepid (and Hardy). That was one of the main reasons we switched to 64-bit.

---

### Post by gaussian on 2008-11-04
I highly recommend that you install uswsusp package and try the s2disk command. It has always worked much better for me than regular hibernate. If it works fine I can give you pointers how to change the GUI to use s2disk.

---

### Post by j.c.sackett on 2008-11-04
> **thomasaaron said:**
> We've gotten reports that hibernate works fine with 64-bit Intrepid (and Hardy). That was one of the main reasons we switched to 64-bit.

Does 64-bit have full support now? Flash, etc? I was under the impression that there were still a number of applications and tools that did not work under 64bit.

---

### Post by thomasaaron on 2008-11-04
Everything works.

There are still some Flash sites that don't work well (or at all), such as comedycentral.com. This appears to be a nspluginwrapper issue. Youtube, cnn.com, etc... all work fine.

The gcc java plugin for firefox is about... 90% where it needs to be.

Other than that, it's a splendid OS.

---

### Post by laserline on 2008-11-06
> **gaussian said:**
> I highly recommend that you install uswsusp package and try the s2disk command. It has always worked much better for me than regular hibernate. If it works fine I can give you pointers how to change the GUI to use s2disk.

Hi,

Can you please post how-to change the GUI to s2disk ?

Thanks,
Idan.

---

### Post by gaussian on 2008-11-06
> **laserline said:**
> Hi,

Can you please post how-to change the GUI to s2disk ?

Thanks,
Idan.

I have never been able to found a better way to do this, so this scores fairly high points in the ugly hack scale.

Steps:
```

sudo -s
cd /usr/lib/hal/scripts/linux/
cp hal-system-power-hibernate-linux /somesafebackupplace
gedit hal-system-power-hibernate-linux

```

Now you want to look for a segment of code that looks like this (this is from a Hardy installation):
```

if [ -x /usr/sbin/pm-hibernate ] ; then
	/usr/sbin/pm-hibernate $QUIRKS
	RET=$?
else
	unsupported
fi

```

Change that to:
```

#if [ -x /usr/sbin/pm-hibernate ] ; then
#	/usr/sbin/pm-hibernate $QUIRKS
#	RET=$?
#else
#	unsupported
#fi

/sbin/s2disk
RET=$?

```

Let me know if this works for you.Try running the script first and see if it gives you errors.

---

### Post by werewolves on 2008-11-13
I am experiencing the same issue on a fresh install of Ubuntu Intrepid 64bit (Daru2).  I installed fresh from CD.  Installed the latest System76 driver.  Hibernate worked fine on Hardy 32bit, but suspend never did. Now hibernate works about every other time.  Same symptoms (blank screen, fan running high, never hibernates).  Suspend still doesn't work.

I will experiment with this s2disk option.

---

### Post by PatrickVogeli on 2008-11-13
the correct way to hibernate using uswsusp is editing the file /usr/lib/pm-utils/defaults and there edit the line # SLEEP_MODULE="kernel" to SLEEP_MODULE="uswsusp"

hope it helps

---

### Post by gaussian on 2008-11-13
> **PatrickVogeli said:**
> the correct way to hibernate using uswsusp is editing the file /usr/lib/pm-utils/defaults and there edit the line # SLEEP_MODULE="kernel" to SLEEP_MODULE="uswsusp"

hope it helps

After some research on the issue I think the really, really proper place to change this is in /etc/pm/config.d/00sleep_module. This changes the set value for the system, not the default value. Both should work ok.

---

### Post by werewolves on 2008-11-13
Does uswsusp help with the Suspend issues as well as the Hibernate?  I am not familiar with it.

Thanks

EDIT: Looks like it does.  Anyone tried it on a Daru2?

---

### Post by gaussian on 2008-11-13
> **werewolves said:**
> Does uswsusp help with the Suspend issues as well as the Hibernate?  I am not familiar with it.

Thanks

EDIT: Looks like it does.  Anyone tried it on a Daru2?

Yes, I have. Many times. And at least last time I tried it did not help. Notice also that the Ubuntu Uswsusp does not include s2ram (suspend program), you'll need to compile the program  yourself (or find a .deb somewhere outside the official repos). See discussion here for angry comments about this exclusion [https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238) :popcorn:

---

### Post by werewolves on 2008-11-14
> **gaussian said:**
> After some research on the issue I think the really, really proper place to change this is in /etc/pm/config.d/00sleep_module. This changes the set value for the system, not the default value. Both should work ok.

This worked great for me.  Thank you.

---


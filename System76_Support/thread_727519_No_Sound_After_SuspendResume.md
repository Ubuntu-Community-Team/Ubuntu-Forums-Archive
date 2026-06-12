---
title: "No Sound After Suspend/Resume"
date: 2008-03-17
forum: System76 Support
---

### Post by DBO on 2008-03-17
I know that technically, System76 does not support Hardy yet, but I was forced to upgrade due to technical constraints with my job (yeah, I know thats backwards).  Still I was hoping that i could get some insight into why my Gazp5 does not have sound after a suspend/resume.

If I kill pulseaudio after suspend/resume gnome-power-manager flips out and eats all my ram.  I can unload the alsa modules with /etc/init.d/alsasound stop.  But starting that again did not cause them to load until I manually aliased snd_hda_intel to snd-card-0.

Hopefully together we can fix this issue before Hardy's release =)

---

### Post by DBO on 2008-03-18
As a workaround I have placed the following script in /usr/lib/pm-utils/sleep.d

```
#!/bin/bash

aconnect=/usr/bin/aconnect

restore_hack()
{
        if [ -d /proc/asound/dev ]; then
                fuser -k /proc/asound/dev/* >/dev/null 2>&1
        fi

        if [ -d /dev/snd ]; then
                fuser -k /dev/snd/* >/dev/null 2>&1
        fi

        if [ -f /proc/asound/seq/clients -a -x $aconnect ]; then
                $aconnect --removeall
        fi

        sleep 3;

        modprobe -r snd_hda_intel
        modprobe snd_hda_intel

	LOGGED_USER=`who | awk '/tty/ {print $1}'`


	su $LOGGED_USER -c "pulseaudio --log-target=syslog -D --high-priority" &
}

case "$1" in
	thaw|resume)
		restore_hack
		;;
	*)
		;;
esac

exit $?
```

---

### Post by thomasaaron on 2008-03-18
It is because The Gazelle needs a model option inserted in the alsa-base file. 

Try inserting...
options snd-hda-intel model=toshiba
...at the very end of /etc/modprobe.d/alsa-base.

Then restart your computer. If sound still doesn't work, you will probably need to compile ALSA 1.0.15rc3 (but that probably won't be necessary).

Refer to the numerous screenshots on the following thread for setting up your sound controls.
[http://ubuntuforums.org/showthread.php?t=712172](http://ubuntuforums.org/showthread.php?t=712172)

---

### Post by DBO on 2008-03-18
Thank you!  That worked!  You wouldn't happen to know why they iwl3945 does not associate with wireless b networks would you?

---

### Post by thomasaaron on 2008-03-18
I'm not exactly sure. I think it is just a very limited driver with less features than the ipw driver. However, it also has less negative side-effects at the moment. That may be changing in Hardy.

---

### Post by DBO on 2008-03-19
I should have mentioned it actually worked with iwl3945 with the -5 kernel.  -7 broke it, but I am not sure how.

---

### Post by gbinal on 2008-05-06
Hmmm.... Just fyi, I had the same problem on my Serval Performance since upgrading to Hardy.  I'll try to give these workarounds a try.

Thanks for the help Thomasaaron - this is just one of the reasons why I'm incredibly happy I went with system76.

---

### Post by thomasaaron on 2008-05-06
Hi, guys.

This forum has now been archived, and we are not checking them as often.
The new Ubuntu/System76 forum is here.

[http://ubuntuforums.org/forumdisplay.php?f=341](http://ubuntuforums.org/forumdisplay.php?f=341)

---

### Post by karlakompiles on 2008-05-23
> **thomasaaron said:**
> It is because The Gazelle needs a model option inserted in the alsa-base file. 

Try inserting...
options snd-hda-intel model=toshiba
...at the very end of /etc/modprobe.d/alsa-base.

Then restart your computer. If sound still doesn't work, you will probably need to compile ALSA 1.0.15rc3 (but that probably won't be necessary).


I know this may be an old forum/issue, but this completely solved the problem I was having.  Thank you!

---


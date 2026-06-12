---
title: "Can your system go into suspend mode and wake up?"
date: 2005-10-16
forum: The Cafe
---

### Post by Adam Lee on 2005-10-16
Hello there : ) I've been using linux for a couple of months now and I've tried a few of wellknown distros.

Some are better than the others but all of them have failed to put my system in to suspend mode.

I have an ATI card and whenever I get my 3d working, the system would not wake up from or go into suspend. 

So I was wondering if any one of you successfully configured your system. 

Suspend mode is something I really need but unfortunately my only solution for now is sticking with Windows XP.

---

### Post by John.Michael.Kane on 2005-10-17
Since you list no system spec's or which version of Ubuntu your using, i can only answer with a link on fix'es [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles)

---

### Post by somuchfortheafter on 2005-10-17
it can get suspended but waking it up is a bitch

---

### Post by woodb on 2005-10-17
I had to change my /etc/acpi/lid.sh script to include "echo mem > /sys/power/state" for it to work.  It now looks something like:

>snip<
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            . /usr/share/acpi-support/screenblank
        fi
    done
    echo mem > /sys/power/state
else
    for x in /tmp/.X11-unix/*; do
>snip<

Obviously you need to restart acpi for this to be read (sudo /etc/init.d/acpid restart).  

Your milage may vary.

---


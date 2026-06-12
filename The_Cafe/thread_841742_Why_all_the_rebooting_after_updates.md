---
title: "Why all the rebooting after updates?"
date: 2008-06-26
forum: The Cafe
---

### Post by picopir8 on 2008-06-26
Ubuntu has traditionally been pretty good about updates being applied w/o the need of a reboot.  However, most of the updates I have received since installing Hardy have required a reboot before they take effect.  Whats up with that?  I am not one of those people who takes pride in their uptime counter, but it seems like I cant make it a single day anymore before ubuntu wants to reboot.  I just hope rebooting after an update becomes a common event that we can expect to continue in the future.

---

### Post by acelin on 2008-06-26
> **picopir8 said:**
> I just hope rebooting after an update becomes a common event that we can expect to continue in the future.

What?

---

### Post by lisati on 2008-06-26
> **acelin said:**
> What?

+1: typo?

---

### Post by bubba_169 on 2008-06-26
Usually you only have to reboot after a kernel upgrade! This is so you can reload into the new kernel to get the benefits immediately - If your box is running fine you don't usually need to reboot straight away...

---

### Post by cardinals_fan on 2008-06-26
I don't use Ubuntu, but even if I did I wouldn't care.  I turn off my box every night :)

---

### Post by kk0sse54 on 2008-06-26
> **cardinals_fan said:**
> I don't use Ubuntu, but even if I did I wouldn't care.  I turn off my box every night :)

same here,
> I just hope rebooting after an update becomes a common event that we can expect to continue in the future.
what updates are making you reboot?

---

### Post by Barrucadu on 2008-06-26
You should never need to reboot except for a kernel upgrade. In fact, not even for that if you use kexec to load the new one.
I also turn my computers off at night and compiled my own kernel which I'm unlikely to upgrade any time soon, so I don't need to reboot.

---

### Post by monstermudder78 on 2008-06-26
> **picopir8 said:**
> Ubuntu has traditionally been pretty good about updates being applied w/o the need of a reboot.  However, most of the updates I have received since installing Hardy have required a reboot before they take effect.  Whats up with that?  I am not one of those people who takes pride in their uptime counter, but it seems like I cant make it a single day anymore before ubuntu wants to reboot.  I just hope rebooting after an update becomes a common event that we can expect to continue in the future.

I'm with you, the last 2 days in a row have required a reboot!

---

### Post by wrtpeeps on 2008-06-26
The reboot needed icon just appeared for me. :)

---

### Post by paul101 on 2008-06-26
you dont have to reboot your pc, reboot when you want to... nobody controls your computer.

---

### Post by lunarcloud on 2008-06-26
Normally, it appears when installing new kernel modules, such as the nvidia/fglrx drivers.

---

### Post by Superkoop on 2008-06-26
Well the reason why it needs to reboot is because some of the things you updated are at a low enough level, that in order to reap the benefits of them, you need to restart that program. 
It's like when you updated Firefox,for example, you had to restart it to start using the new version. 
So the same applies here, when you update something at a low enough level, you need to restart that to start using the updates, and the simplest way to resart it is to reboot. 

The reason for the updates recently have been that lower level programs have been getting updated.
You only need to restart the computer if that particluar program, is something you want to use right away, if you don't care for the most recent, and it's not bothering anything, by all means, don't reboot right away.

---

### Post by zachtib on 2008-06-26
i've noticed this recently as well, ubuntu wanting to restart after just about any update.  I've just started ignoring it unless it actually was kernel related

---

### Post by starcannon on 2008-06-26
yeah I had to reboot twice since I put hardy on... not to worried about it here. Like others have said its only when low level updates happen, and really its to be a bit expected on a new release, the alternative is to do it the way another company does, and release outdated security updates that require 2 or 3 reboots for each update once a week, and then release a 250mb service pack every couple of years that in turn requires more of the outdated security updates causing 2 or 3 reboots each...

I guess now that I look at it, rebooting twice in the last couple months isn't bad ;)

---

### Post by FFighter on 2008-06-26
> you dont have to reboot your pc, reboot when you want to... nobody controls your computer.

Unless you use Windows :D

Sorry, couldn't resist the opportunity.

---

### Post by dizee on 2008-06-26
It only happens because of kernel updates or x updates. of course with an x update you just have to logout. and there are ways to have the kernel update without a reboot too. either way much much better than windows. the old versions were the worst, windows 98 made you reboot for installing and uninstalling anything, torturous.

it's happened a lot in hardy because the kernel has been updated four times by my count.

---

### Post by monstermudder78 on 2008-06-27
I would like to add that while I do understand that I am the one who makes the decision to reboot or not reboot, those damn blue arrows in the notification area drive me crazy.  Why isn't there an option to hide them? Or is there?

---

### Post by kevdog on 2008-06-27
Remember when Ubuntu used to claim as one of its merits that you didn't have to reboot like Windows with updates .... kind of came back and bit them in the a$$ didn't it?  If you don't really need to reboot (just like in Windows you don't really need to reboot -- the system will keep functioning), then get rid of any notification that would suggest otherwise on the taskbar.   Kind of like a warning, reboot now! -- but really this is only a suggestion because you know you don't really have too!

---

### Post by shadylookin on 2008-06-27
There's been a lot of kernel updates for hardy(moreso than I ever remember having before). If you want to use the new kernel then you have to reboot otherwise you can just ignore it. There is supposedly a way around it, but rebooting has never been that much of a hassle for me.

---

### Post by acelin on 2008-06-27
> **cardinals_fan said:**
> I don't use Ubuntu, but even if I did I wouldn't care.  I turn off my box every night :)
Then why do you ever stick your nose into what the default theme for Ubuntu should be?

---

### Post by smartboyathome on 2008-06-27
> **shadylookin said:**
> There's been a lot of kernel updates for hardy(moreso than I ever remember having before). If you want to use the new kernel then you have to reboot otherwise you can just ignore it. There is supposedly a way around it, but rebooting has never been that much of a hassle for me.

Not "supposedly a way", but an actual way around it. Just install kexec-tools, and then run this script:
```
#!/bin/sh

grub_conf() {
    STRING="# $1="
    grep "^$STRING" /boot/grub/menu.lst | sed "s|$STRING||g"
}

KERNEL=`find /boot/ -name 'vmlinuz-*' | sort -n -r | head -n 1`
INITRD=`echo $KERNEL | sed -e 's/vmlinuz/initrd.img/g'`
#KOPTS="`grub_conf kopt` `grub_conf defoptions`"
## New KOPTS method contributed by hyperair
KOPTS=`grep $KERNEL /boot/grub/menu.lst | head -n 1 | sed -e 's|^kernel.*'${KERNEL}'\s*||'`

ACTION="kexec -l $KERNEL --append=\"$KOPTS\" --initrd=$INITRD"

case "$1" in
    -n|-s)
        echo $ACTION
    ;;
    *)
        $ACTION
    ;;
esac
```
It will load your new kernel without rebooting, thus making your computer run longer. :D

---


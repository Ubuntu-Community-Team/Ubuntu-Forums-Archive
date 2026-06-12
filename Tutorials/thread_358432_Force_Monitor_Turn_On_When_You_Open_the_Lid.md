---
title: "Force Monitor Turn On When You Open the Lid"
date: 2007-02-10
forum: Tutorials
---

### Post by Darwin Award Winner on 2007-02-10
Compatibility: I run Ubuntu 6.10 Edgy, but this howto is likely to work with any sane ACPI setup.

For the trivial fix, skip to the PROCEDURE section. If you want to understand what's going on, read on.

RATIONALE: If you run Ubuntu on a laptop, and your monitor turns off when you close the lid but *doesn't* turn back on when you open it, this is for you (skip to the next paragraph). If you have the opposite problem (viz. monitor fails to turn off on closed lid), a slight modification of the script might help you. If you don't have either problem, this guide still might be useful for you. It is likely that gnome-power-manager does the unblanking for you. If there is a problem with it, or if you happen not to be logged in, or if you're at a virtual terminal instead of in X when you open the lid, your monitor might fail to turn on. This howto makes the monitor *always* turn on when the lid opens, as long as the ACPI daemon is running (which, in general, it should be). No dependence on gnome-power-manager or any other tool. 

BACKGROUND: First, we have to understand a little about what happens when the computer detects that the lid has been opened or closed. Basically, the configuration of the ACPI daemon tells it to execute the file [FONT="Lucida Console"]/etc/acpi/lid.sh[/FONT] whenever the lid is either opened or closed. This is a bash script that does the following, in order:
[LIST=1]
[*]Executes the file /etc/acpi/local/lid.sh.pre if it exists and is executable.
[*]Checks if a policy manager (that would be gnome-power-manager, or whatever the KDE tool is). If it detects one, it exits and goes no further.
[*]Checks if the lid was opened or closed.
[*]Takes the appropriate actions, depending on whether the lid was opened or closed.
[*]Executes the file /etc/acpi/local/lid.sh.post if it exists and is executable.
[/LIST]

PROBLEM: Ok, that sounds good. But there is a problem, at least for me, and apparently for many other Dell laptop owners, and maybe others. The problem is that in addition to this, *something*, I'm not sure what, always blanks the screen, even if the ACPI daemon is not running! But this something does *not unblank* the screen. So the screen is always guaranteed to be blanked, even if neither ACPI nor gnome-power-manager nor anything else tells it to blank, but it will not be unblanked unless it is explicitly instructed to. (And obviously, moving the mouse, typing, restarting X, etc. have no effect, or else it wouldn't be a problem.)

SOLUTION: So, the solution? If the screen always insists on blanking when it's closed, then we have to always insist that it unblanks when it opens. As you can see from the list above, the only place we can put something to always have it execute on lid open is in the file /etc/acpi/local/lid.sh.pre. After that, if gnome-power-manager is running, the script will exit, so things after that are not guaranteed to always run. So...

PROCEDURE: 
Install vbetool:
```
sudo apt-get install vbetool # should already be installed, but just in case
```
Make the script:
```
sudo mkdir -p /etc/acpi/local/
sudo gedit /etc/acpi/local/lid.sh.pre
```
Put this in /etc/acpi/local/lid.sh.pre:
```
#!/bin/sh
grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    # lid is open; turn the screen on
    vbetool dpms on
fi
```

If you have the opposite problem, put *this* in /etc/acpi/local/lid.sh.pre: 
Note, I haven't tested this, since I don't have this problem. The only difference is the else clause, though.
```
#!/bin/sh
# always turn on screen on open lid, regardless of policy or anything
grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    # lid is open; turn the screen on
    vbetool dpms on
else
    # lid is closed; turn the screen off
    vbetool dpms off
fi
```
And finally, make it executable:
```
sudo chmod +x /etc/acpi/local/lid.sh.pre
```

And that should do it. Whether your're logged in, logged out, on a console, whetever, as long as the ACPI daemon is running, the screen should turn on when the lid opens.

TROUBLESHOOTING: I learned all of this by logging into my laptop from another computer via ssh and watching various logfiles, trying various commands, etc. This was very helpful, as I didn't have to deal with the laptop's own monitor deactivating. If you have ssh set up, using it like this is very useful for sorting out all manner of power-management issues. Running "vbetool dpms [on/off]" over ssh should work, so this also gives you a way to manually unblank the monitor if it gets stuck blank.

Please let me know if you find this helpful, or if you have any questions.

---

### Post by twoseids on 2007-02-14
Dude, you rock! My dang black screen after closing the lid, which forces me to manually power off my computer, has been one of those things that really bugged me about Ubuntu.

But this fix worked! I only read far enough to know that this applied to me, then skipped right to the code.

Thanks for this great service you've performed for us Dell Ubuntu users!

---

### Post by Ivar Nahsesamar on 2007-02-16
No, this solution doesn't help. It did not work for me. I have a T42 with a Radeon Mobility 9000.

---

### Post by Pablasso on 2007-02-17
worked on a Dell Inspiron 6000 with the 915GM Intel integrated graphics, i was having this problem since the update to edgy

thanks man, i really appreciate the explanation, i didn't even knew the existence of vbetool

---

### Post by Darwin Award Winner on 2007-02-20
> **Ivar Nahsesamar said:**
> No, this solution doesn't help. It did not work for me. I have a T42 with a Radeon Mobility 9000.
I believe there is a program called radeontool that implements the same functionality for ati cards. Try "man radeontool"

---

### Post by warewolf55 on 2007-02-28
I must be missing something else. On a brand new install of 6.10 I get

> grep: /proc/acpi/button/lid/*/state: No such file or directory

Also the script fails due to permissions if I run it as a user. If I type > sudo vbetool dpms on before I close the lid and hit enter afterwards, it comes right up with no problems. Is there an alternate location for the lid state somewhere?

---

### Post by Darwin Award Winner on 2007-02-28
I believe that fails to qualify as a "sane ACPI setup," as mentioned in the requirements. You should make sure that ACPI is working correctly on your laptop. That's beyond the scope of this tutorial, but I'm sure there's a howto on it somewhere. As for the permissions problem, the ACPI daemon will run it with administrator permissions, so no sudo is required in the script.

---

### Post by H.E. Pennypacker on 2007-03-09
My brothers and sisters, the answer has come down from Heaven.  This solved my &*!@!#$ problem!

I've waged a war on this problem for so long, I can't begin to tell you how happy I am.  This is exactly what I needed.  It turns off the backlight, keeps the computer on to leave all downloads and processes going, AND asks me for my password upon return.  Could I ask for more?!  No, with the exception of fries and a drink....make that pink lemonade.  J'IEP!

Oh yeah, I have a Dell Inspiron 2200.

---

### Post by Darwin Award Winner on 2007-03-09
Yes, that's why I chose the lid.pre spproach rather than simply replacing the script.

---

### Post by IamAcoconut on 2007-03-09
What if I just want the monitor turned off after a certain period of inactivity, without closing the lid (which works fine for me)?
This...```
sleep 5 && xset +dpms && xset s off off && xset dpms 0 0 0 && xset dpms force off
```doesn't work. After a few seconds the screen is back on, though black.

---

### Post by kuukie on 2007-03-19
Thank you for all the effort DAW.

What I'd really like to know is what this *something* is that messes around with power/display management. Maybe somebody could contact an Ubuntu developer about this?

Aside from that, I **don't **think it's a good idea to close the lid at all (unless the laptop is completely off and has cooled down for a few minutes). I (almost completely) closed my lid once over night and that badly warped the display for a day or so. I suppose that would've been permanent if the lid had been closed entirely

---

### Post by Darwin Award Winner on 2007-03-20
I assume that there is some sort of hardware switch in Dell laptops that always turns off the monitor when the lid is closed.* The interesting thing is that "xset dpms ..." does not seem to be able to undo this effect. Only vbetool can turn the monitor back on.

IamAcoconut - All the major desktop environments have ways of setting the monitor to turn off after an idle time, I believe. If not, you can try a Google search for "(your desktop environment) monitor backlight".


*Edit: Part of my reason for believing this is that the monitor still turns off when the lid is closed, even if the ACPI daemon is disabled with 'sudo /etc/init.d/acpid stop'.

---

### Post by LucasCosta on 2007-03-20
Thank you so much! I've been trying to solve this since I started using Edgy... the fact that I couldnt close the laptop lid was really bothering me! Thanks again... very good job!
oh, and I also think that you should notify ubuntu developpers about that...

---

### Post by Darwin Award Winner on 2007-03-29
By the way, I decided to test the behavior of the monitor switch when no power-management daemon is running. In order to do this, I booted the computer and stopped the countdown at the boot loader screen, and then tested closing and opening the monitor. Since no operating system had been booted yet, there couldn't be any software power management running (unless GRUB has some sort of power management I'm not aware of). In this case, closing the lid turned the monitor off, and opening the lid turned it back on. Same thing at the console (no X). Presumably, MS couldn't be bothered to support this in their OS, so Dell was forced to implement it in firmware. Or something.
Anyway, I think that what causes the problem is that when the lid is closed, first the Dell firmware turns off the monitor, then Gnome Power manager, or some utility, uses Xorg's DMPS to deactivate the already deactivated monitor, and this causes it to get "stuck" off in such a way that neither one can turn it back on. But vbetool can. 
A possible solution might be to disable DPMS, but then the monitor would never turn off when idle. Maybe turning off DPMS when the lid is closed? Can DPMS be toggled without restarting X?

---

### Post by haricharan on 2007-03-30
perfect..that works absolutely fine on mine....

---

### Post by H.E. Pennypacker on 2007-05-02
> Maybe somebody could contact an Ubuntu developer about this?

If it has not already been reported, I'll do so.

> Aside from that, I don't think it's a good idea to close the lid at all (unless the laptop is completely off and has cooled down for a few minutes). I (almost completely) closed my lid once over night and that badly warped the display for a day or so. I suppose that would've been permanent if the lid had been closed entirely


I always close the lid when I walk away.  It's better to have the lid closed, because that reduces the dust build up.  

By the way, I am well aware of a screen becoming damaged.  My backlight once gave out, and that was certainly not pleasant.  I had to buy an entirely new laptop, because finding a new backlight was not working out.  This happened before I switched to Ubuntu.

---

### Post by Darwin Award Winner on 2007-05-02
This problem is partially solved in Feisty. If you never close the screen except when you're logged in to a graphical X session, and if you don't close the screen while using the automatic sleep inhibitor applet, then you should just have to tell Gnome Power Manager to blank the screen/suspend/whatever when the lid is closed (just set anything other than "Do Nothing"). If you use that applet, or if you use the console on occasion, or if you ever close the lid while at the login screen, then your screen will get stuck blank. So, all in all, not a full fix.

I looked at the acpi script that controls the monitor when the lid is opened/closed. As mentioned in the howto, if it sees a power manager (Gnome or KDE), then it just exits. Otherwise, it will blank and unblank the screen *only if you are currently logged in to X and viewing the X server*. If no X server is running, if no one is logged into X (i.e. at the login screen), or if you are logged in to X but currently viewing a different virtual terminal, the acpi script will do nothing. On a normal laptop, this would mean that the monitor just stays on. But if you're having this problem, then your monitor will turn off and stay off.

The problem with the sleep inhibitor applet arises like this: If you have set Gnome Power Manager to sleep on lid close, then obviously it won't try to blank/unblank the screen. That's normally ok, because the laptop will blank/unblank its screen in the process of sleeping/waking (incidentally, if your screen gets stick blanked, going in and out of sleep mode should bring it back on). But now, if you use the sleep inhibitor applet, GPMan won't sleep, but it also won't blank/unblank the screen. It will do nothing! Boom, blank screen.

So, to conclude, there are two problems:
[LIST=1]
[*]Both the lid acpi script and Gnome Power Manager only work when a user is logged into an X server on the active VT.
[*]Gnome Power Manager cannot always be counted upon to unblank the screen when the lid is opened.
[/LIST]
I can think of a way to fix the first one. Here's some pseudocode for the logic of a correct acpi script:
```

if active VT is running an X server:
    if active VT is running a power manager:
        do nothing; let the power manager handle it
    else:
        use xset to blank/unblank the screen of the X server
    endif

else:
    use vbetool to blank/unblank, because X isn't running
endif

```

As for the second problem one, the only good solution I can think of would be a special option that tells GPMan to always unblank on lid open. It could be labeled something like "Enable fix for blank screen bug" or something like that.

But for now, the only surefire solution is to always unconditionally force the screen to come back on.

---

### Post by mibdv6 on 2007-06-01
Just wanted to say thanks!

This worked great!

---

### Post by H.E. Pennypacker on 2007-06-26
> **Darwin Award Winner said:**
> This problem is partially solved in Feisty. If you never close the screen except when you're logged in to a graphical X session, and if you don't close the screen while using the automatic sleep inhibitor applet, then you should just have to tell Gnome Power Manager to blank the screen/suspend/whatever when the lid is closed (just set anything other than "Do Nothing"). If you use that applet, or if you use the console on occasion, or if you ever close the lid while at the login screen, then your screen will get stuck blank. So, all in all, not a full fix.

I can't believe it, but you're actually right.  This problem has partially been solved under Feisty.  All I had to do was select "Blank screen" from Power Management, and when I raised the lid, screen turned back on.  Awesome.

Did you report this problem, already?

Thanks again.

---

### Post by joeashcraft on 2007-06-27
Thanks. I had the problem of my screen not turning off when I closed the lid, and now it turns off, and turns right back on thanks to you.
I'm using an Inspiron 6400

---

### Post by axm on 2007-11-10
Good solution. Would have expected to work stuff like that out of the box when buying a machine with preinstalled ubuntu (lock screen instead of "do nothing" was the default and worked though). 

I am still sometimes experiencing this misbehaviour when closing the lid, then unplugging the power cable, then opening the lid. I cannot reproduce that relyably yet (thought I could, added some debugging logs, assured lid.sh.pre is executed, added some more logs if open status is recognised correctly, wont reproduce anymore for now).

Anybody experiencing the same?

---

### Post by IamAcoconut on 2007-11-10
Which Ubuntu do you use?
**Edited: **The problem somewhat remains in Gutsy. I can close the lid, the monitor turns off, than turns back on when I open it, but it will not - never ever - go off if the lid remains open. It'll just go blank, when it is supposed to shut down.

---

### Post by Darwin Award Winner on 2007-11-10
In general, it doesn't happen. But there are specific cases where it does. And if it happens even once, and you don't happen to have an open terminal where you can type the necessary command, then you have to restart. Rather than count on never encountering these specific cases, I'd rather just leave it enabled. 

Like I said, since apparently the Dell hardware always ensures that the monitor turns off when the lid is closed, the only solution is a 100% guarantee that it will come on again when opened.

---

### Post by axm on 2007-11-11
Still on Feisty, and will postpone Gutsy for couple of days more. But I I will wait till then to try and provoke it again.

> In general, it doesn't happen. But there are specific cases where it does.

..and that again makes me think that gutsy will fix only what I have done now anyway. But lets see.

Thanks.

PS:
Just for wrapup, I have been on Gutsy for a couple of weeks and had the glitch (close lid, unplug power, open lid, stays black) yesterday the first time again. The close/open states of the lid were recognised and the script ran as expected. Unlike on Feisty, another close/open resolved that problem, so I really can live with that.

---

### Post by galatians on 2009-12-06
Thanks for the fix. The fix works for me in 9.10.

This is what I put in /etc/acpi/local/lid.sh.pre

```
#!/bin/sh
if grep -q open /proc/acpi/button/lid/LID/state
  then /usr/sbin/vbetool dpms on
  else /usr/sbin/vbetool dpms off
fi
```

The only downside is that you have to remove that file if you want to use the gnome configuration tool to enable suspend/hibernate on lid close.

The gnome power utility needs to be fixed to use vbetool I guess.

---

### Post by aaronLund on 2011-08-30
Can anyone tweak this script to not kill the external monitor as well?

Thanks!

---


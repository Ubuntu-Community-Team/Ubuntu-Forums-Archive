---
title: "Set screen to turn off after time. Command line not desktop."
date: 2020-09-01
forum: Server Platforms
---

### Post by Raymond Day on 2020-09-01
Installed Ubuntu server 20.04.1 on a EVOO tablet. it works real good on it.

But the screen stay on all the time. Can I set a timer like for 5 minutes if no keyboard the screen will turn off.

It's a tablet and there is no way to just turn the screen off without turning off the whole tablet.

It had Windows 10 on it I just DD backed that up before installing Ubuntu server.

Found out this command will do it but with time it goes away.

```
echo -e "\033[9;1]" > /dev/tty1
```

That will turn the screen off in 1 minute with not keyboard use. But like I said it will not stay. I have to type it back in avery few days.

Change the 9:1 to like 9:5 and it will turn the screen off in 5 minutes.

-Raymond Day

---

### Post by Raymond Day on 2020-09-02
Looking on the web a long time for a answer and [3 months ago ask about the same thing here]("https://askubuntu.com/questions/1244358/ubuntu-20-04-server-turn-off-screen"):

So I don't think any one will know here either.

Guess have to make like a cron job so that command gets done about 1 time a day. Then it my stay.

Or maybe I can open this up and install a switch on it to turn off the built in LCD screen. Not sure.

-Raymond Day

---

### Post by ameinild on 2020-09-04
I think your best bet is to use either screen or tmux - both are terminal multiplexers. Both programs offers the ability to set a screensaver in the console, as well as other cool features. 
I'm not aware how you set a screensaver in a "raw" bash terminal, but I use tmux myself.

---

### Post by Doug S on 2020-09-07
A few years ago, the screen used to default to turning off after a few minutes. Now it defaults to staying on all the time. To restore the original behavior, you can add a timeout to your grub command line. Example (7.5 minutes, and I have other stuff on the line also):

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 [COLOR="#FF0000"]consoleblank=450[/COLOR] intel_pstate=passive msr.allow_writes=on cpuidle.governor=teo"
```

[The relevant bug report]("https://bugs.launchpad.net/ubuntu/+source/kbd/+bug/869017").

---

### Post by Raymond Day on 2020-09-09
Just made a file name "screen-blank" in /etc/cron.daily/ that has just this in that file:

**echo -e "\033[9;1]" > /dev/tty1**

Will see if I can get the grub one to work.

So I added this to /etc/default/grub

[B]# Turn screen off after 60 sec. of no use.
GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=60"
[/B]

Then ran the update-grub command.

After a reboot will see if it works.

Will post back if it works.

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2020-09-09
It did not work waited about 10 minutes and the screen never went off. Got Ubuntu 20.04.1 LTS server on it now.

Did I do the Grub command wrong some how?

-Raymond DAy

---

### Post by Raymond Day on 2020-09-09
There is a command to show if it's working I did this:

```
root@rayday-tablet:~# grep consoleblank /boot/grub/grub.cfg
        linux   /vmlinuz-5.4.0-47-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  [COLOR="#FF0000"]consoleblank[/COLOR]=60
                linux   /vmlinuz-5.4.0-47-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  [COLOR="#FF0000"]consoleblank[/COLOR]=60
                linux   /vmlinuz-5.4.0-45-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro [COLOR="#FF0000"] consoleblank[/COLOR]=60
root@rayday-tablet:~#
```

Should it show 3 of them? Maybe that is what is wrong. It is does like 60x60x60 that would be a long time before it does it. Not sure.

-Raymond Day

---

### Post by Doug S on 2020-09-09
> **Raymond Day said:**
> So I added this to /etc/default/grub

# Turn screen off after 60 sec. of no use.
GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=60"


Then ran the update-grub command.
After a reboot will see if it works.O.K. sounds right.

> **Raymond Day said:**
> Did I do the Grub command wrong some how?
It looks O.K. to me.

> **Raymond Day said:**
> There is a command to show if it's working I did this:

Code:

```
root@rayday-tablet:~# grep consoleblank /boot/grub/grub.cfg
        linux   /vmlinuz-5.4.0-47-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  consoleblank=60
                linux   /vmlinuz-5.4.0-47-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  consoleblank=60
                linux   /vmlinuz-5.4.0-45-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  consoleblank=60
root@rayday-tablet:~#
```

Should it show 3 of them? Maybe that is what is wrong. It is does like 60x60x60 that would be a long time before it does it. Not sure.
I think it should be 1 per kernel, plus 1 repeated for the default kernel. I get a bit different, but think it is a red herring. I have 30 kernels installed at the moment, so won't show all:

 ```
linux   [COLOR="#FF0000"]/boot[/COLOR]/vmlinuz-5.4.0-42-generic root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro  ipv6.disable=1 [COLOR="#FF0000"]consoleblank=450[/COLOR] intel_pstate=passive msr.allow_writes=on cpuidle.governor=teo
```what does your kernel command line show? here is mine:

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.9.0-rc4-stock root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro ipv6.disable=1 [COLOR="#FF0000"]consoleblank=450[/COLOR] intel_pstate=passive msr.allow_writes=on cpuidle.governor=teo
```

---


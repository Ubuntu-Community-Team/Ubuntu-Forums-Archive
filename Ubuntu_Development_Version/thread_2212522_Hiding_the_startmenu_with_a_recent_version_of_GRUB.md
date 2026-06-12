---
title: "Hiding the startmenu with a recent version of GRUB"
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-03-21
I'm having Ubuntu and Windows XP installed resulting that GRUB (grub-pc 2.02~beta2-7) does always show for 10 seconds a startmenu on booting. I have made already a look into the wiki and searched with Google how I can disable the startmenu but I can't find a solution that works. Here is my /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="elevator=cfq"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_GFXPAYLOAD_LINUX=1680x1050-24
GRUB_TIMEOUT_STYLE=hidden

```


After executing update-grub and rebooting the system I'm still seeing the startmenu for 10 seconds. Has anybody an idea how to solve this?

---

### Post by mc4man on 2014-03-21
It seems to treat 0 as 10 though 1 is treated as 1
(you could try 0.0 though no clue if that's recommended though will work..

Edit: maybe take a look at lines 35 -37 in /etc/grub.d/30_os-prober, sp

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
By "start menu" do you mean the grub menu that lets you choose which operating system you want to boot? Why would you want to "disable" it leaving you with no easy way to choose which OS to boot from? Perhaps I don't understand what it is you want to do. Maybe you could describe exactly what you want to happen when you boot. If you just want it to default to one of the OSs you have installed faster than 10 seconds but still give you an opportunity to boot from the other one without extraordinary difficulty you only need to set a shorter interval, one second for example, not disable it.

I see you have the timeout set to 0. I'd have to do "man grub" or some web searching to swear to it but I would have thought that would make grub start the boot of the default instantly after the menu loaded since I believe (again I'd have to check to swear to it) a negative number is what you use to get an indefinite delay until you make an explicit choice. In any case, I'd try commenting out```
GRUB_TIMEOUT_STYLE=hidden
```by prepending a "#" so it looked like this:```
#GRUB_TIMEOUT_STYLE=hidden
``` instead, on the reasoning that the more information you hide, the harder it is to figure out what is going on.

Did you remember to```
sudo update-grub
```not just```
update-grub
```?

P.S. I see Mac4man has tested the definition of "0" and posted while I was sloooooowly typing. Kudos to him.

---

### Post by grahammechanical on 2014-03-21
There is another command that is often needed in my experience. After running sudo update-grub we should also run

```
sudo grub-install /dev/sda
```

If we have only only hard disk (sda) and we want Grub to be installed in the MBR of sda. If we want it installed into the MBR of a second or third drive then it would be /dev/sdb or /dev/sdc.

I find that this commands often fixes with problem where we have updated the Grub configuration files but not change is noticeable in the Grub menu.

Regards.

---

### Post by craig10x on 2014-03-22
I started getting this too, after i upgraded from 13.10 to 14.04 in more recent times (about 2 months ago i think)...i only use ubuntu (no dual boot) and like the original poster here, on initially boot up, that purple grub screen appears (the one that you would normally on get if you dual booted and needed to make a selection) of course, i have no selection to make, but i was wondering if everyone gets this now (even if they don't dual boot) or is it some kind of bug we are having?

I am planning on re-upgrading my 14.04 when 14.04 final gets released (using the iso installer) or as it would call it re-install and bring your data and programs over with it...hope that that will knock it out...wasn't really anxious myself to "play" with grub...

Of course, if the original poster is dual booting (i kind of get that impression) then he is supposed to be getting that screen...how else would you be able to make a selection?
That is normal...my getting it (since i am not dual booting) is not...

---

### Post by grahammechanical on 2014-03-22
If it is now default to reveal the Grub menu even if Ubuntu is the only OS, then there should be a simple way to change the time out without needing to manually edit a configuration file. gksu is not installed by default. The developers clearly think that ordinary users should not be messing with system configuration files. And they have a point. So, I am starting to think that I need to study Grub Customizer again if I am to give advice on making these changes. I used to use it in the past. I get by without it now. But it is a good tool.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

Regards.

---

### Post by craig10x on 2014-03-22
@grahammechanical: thanks...yeah, i didn't want to mess with the file...i guess what i will do is wait until i re-install 14.04 final and see if it still sets it up grub screen appearance as default...if it does, then, as you said, it probably means that it's the way the set it up now...then, i could always lower the amount of time it stays on the screen (changing the time out)...;)

---

### Post by Mateusz Stachowski on 2014-03-22
OP if you don't want to see GRUB menu then you have to set GRUB_TIMEOUT to 0 like you did and add this line:

```
GRUB_TIMEOUT_STYLE=hidden
```

This will hide the GRUB menu entirely and will boot immediately the default system. If you ever want to use other boot entries then simply press and hold **left Shift** until you see the GRUB menu.

Also look at the top of /etc/default/grub file you have there:

> # For full documentation of the options in this file, see:
#   **info -f grub -n 'Simple configuration'**

This command will give you more informations about GRUB config options.

---

### Post by Mateusz Stachowski on 2014-03-23
Disregard my previous post in regards to GRUB_TIMEOUT_STYLE as you already have it set and also it isn't really needed you can comment it out or even delete as suggested by Dreamer Fithp Apprentice.

The only thing that's really needed for not seeing GRUB menu is GRUB_TIMEOUT set to 0 and then updating grub.

```
sudo update-grub
```

> **mc4man said:**
> It seems to treat 0 as 10 though 1 is treated as 1
(you could try 0.0 though no clue if that's recommended though will work..

Edit: maybe take a look at lines 35 -37 in /etc/grub.d/30_os-prober, sp

That is not what says official documentation check it out with this command:

```
info -f grub -n 'Simple configuration'
```

> 'GRUB_TIMEOUT'     Boot the default entry this many seconds after the menu is
     displayed, unless a key is pressed.  The default is '5'.  Set to
     '0' to boot immediately without displaying the menu, or to '-1' to
     wait indefinitely.


     If 'GRUB_TIMEOUT_STYLE' is set to 'countdown' or 'hidden', the
     timeout is instead counted before the menu is displayed.




---

### Post by Sworddragon on 2014-03-23
> **mc4man said:**
> It seems to treat 0 as 10 though 1 is treated as 1
(you could try 0.0 though no clue if that's recommended though will work..

Edit: maybe take a look at lines 35 -37 in /etc/grub.d/30_os-prober, sp

30_os-prober was indeed the cause. If the timeout was set to 0 it has set it to 10. But setting GRUB_HIDDEN_TIMEOUT to 0.0 does successfully hide the menu (0.0 seems to be kept as a float and not converted to an int so the condition in 30_os-prober is not triggering anymore).


> **Dreamer Fithp Apprentice said:**
> Why would you want to "disable" it leaving you with no easy way to choose which OS to boot from?

> **craig10x said:**
> Of course, if the original poster is dual booting (i kind of get that impression) then he is supposed to be getting that screen...how else would you be able to make a selection?

The idea is to boot up instantly with the default operating system to speed up the booting process without pressing enter but leaving the opportunity to summon the grub menu on holding shift on booting. But after I could test this now the menu does not appear if I'm holding shift on booting.

---

### Post by craig10x on 2014-03-23
@Sworddragon: i get what you mean now...makes sense...so, then if the time is set to 0 then the grub menu doesn't appear at all and yet, if you wanted/needed to access it, you would just have to hit shift when the system starts booting up?

Also: can someone tell me the easiest way to change the time out number on the grub menu?

---

### Post by Sworddragon on 2014-03-23
> **craig10x said:**
> @Sworddragon: i get what you mean now...makes sense...so, then if the time is set to 0 then the grub menu doesn't appear at all and yet, if you wanted/needed to access it, you would just have to hit shift when the system starts booting up?

Yes, this is what I'm trying to achieve.


> **craig10x said:**
> Also: can someone tell me the easiest way to change the time out number on the grub menu?

On testing this a little more from a default /etc/default/grub just add the line GRUB_TIMEOUT_STYLE=hidden (alternatively commenting out GRUB_HIDDEN_TIMEOUT=0 seems to work too) and set GRUB_TIMEOUT to 0 (or 0.0 if you have for example os-prober installed that sets the timeout to 10 if it is 0 (and 0.0 is not 0 in this case)). This will successfully boot the default operating system without showing the boot menu even on a dual-booting system. But there is still one thing that is not working: Keeping left shift or right shift pressed while booting will successfully show "GRUB loading." but the boot menu is then not displayed. I'm not sure if this is a bug or if I still have to configure something.

---

### Post by craig10x on 2014-03-24
Thanks for the update on that...hope you are able to figure it out... :D

---

### Post by Sworddragon on 2014-03-31
After some more testing I couldn't figure out how to solve this. On looking at the GRUB bugtracker I have found a related report and posted into it: [http://savannah.gnu.org/bugs/?40853](http://savannah.gnu.org/bugs/?40853)

---


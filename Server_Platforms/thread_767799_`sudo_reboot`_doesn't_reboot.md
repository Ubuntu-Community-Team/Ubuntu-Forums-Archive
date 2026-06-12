---
title: "`sudo reboot` doesn't reboot"
date: 2008-04-25
forum: Server Platforms
---

### Post by mat087 on 2008-04-25
Hi,

I'm running Ubuntu 6.06.2 on my server. Every time I do `sudo reboot`, everything is shutting down, I can see "Will now reboot", but it doesn't reboot. 

However the computer doesn't seems completely powered off. A led is turned on. In order to complete the reboot, I need to hold the "power" button for 5 seconds, then push it again to boot the computer.

I've passed each option of the BIOS one by one, but nothing seems related to my problem. (Maybe I missed it....)

Here is the output when I try to reboot :

```
Apr 25 22:19:30 jogger shutdown[4499]: shutting down for system reboot
Apr 25 22:19:30 jogger init: Switching to runlevel: 6
Apr 25 22:19:32 jogger mysqld[3647]: 080425 22:19:32 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 25 22:19:32 jogger mysqld[3647]: 
Apr 25 22:19:32 jogger mysqld[3647]: 080425 22:19:32  InnoDB: Starting shutdown...
Apr 25 22:19:35 jogger mysqld[3647]: 080425 22:19:35  InnoDB: Shutdown completed; log sequence number 0 43655
Apr 25 22:19:35 jogger mysqld[3647]: 080425 22:19:35 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 25 22:19:35 jogger mysqld[3647]: 
Apr 25 22:19:35 jogger mysqld_safe[4588]: ended
Apr 25 22:19:38 jogger kernel: Kernel logging (proc) stopped.
Apr 25 22:19:38 jogger kernel: Kernel log daemon terminating.
Apr 25 22:19:38 jogger exiting on signal 15

```


Any hint where I can search to find the problem ?


Thanks,
Mathieu

---

### Post by lsmobrian on 2008-04-26
I know it doesn't really answer the reboot command problem, and it might even be aliased, so this might be pointless to try, but does
```
sudo shutdown -r now
```
have the same result.  I have had similar problems w/ reboots/shutdowns on my laptop running hardy, but I'm away from it right now

---

### Post by mat087 on 2008-04-26
> **lsmobrian said:**
> I know it doesn't really answer the reboot command problem, and it might even be aliased, so this might be pointless to try, but does
```
sudo shutdown -r now
```
have the same result.  I have had similar problems w/ reboots/shutdowns on my laptop running hardy, but I'm away from it right now

Same problem with `sudo shutdown -r now`.

---

### Post by frankos44 on 2008-04-26
Has this computer always done this?

Try looking at power management in the BIOS.

Also try upgrading the server to latest release.

---

### Post by brokenshadows on 2008-06-20
I'm having the same issue.  I'm running the current release of Ubuntu Server (8.04 that I downloaded less than a week ago)...the 'sudo shutdown -r now' command begins the shutdown process but the system hangs after:

*Will now restart
[  73.409331] Restarting system.

I don't see anything in my BIOS that might be related, although I did try flashing to the newest version to try and fix this issue...

It's a bit frustrating because I can't do much remotely if any time I need to reboot, it hangs...

Update: the halt command works just fine...

SOLVED: I turned the Dual Core option in my BIOS to Off

---

### Post by mbeach on 2008-06-22
could be related to the "reboot=b" issue.

comment 8 at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/115011](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/115011)

---

### Post by _6i on 2009-06-14
i have just the same problem with my box running ubuntu desktop 9.04
i log in through ssh, then when i try to 'sudo reboot', first everything seems fine - i get the usual "i will now restart" stuff from the machine but it never starts again

BUT what is different in my case, i used to reboot it this way - through ssh - and it WORKED, but a week ago it started to "stuck" in the reboot sequence

this is a bit frustrating, because i have to administer the poor thing, but i'm 400 km away, so the go-there-push-the-button method is not so reassuring, because i have to wait, until someone get there...and i usually administer this one during nights..

when i got someone there, i was told that the box is acting like turned off (monitor -no signal from graphics card, i got dropped from ssh during the shutdown sequence), but all the fans were running (and probably the leds were on too..)
then a had my man push the power button, and the box started booting, like it was actually off...yeah, probably it forgot to turn the fans off... :-/

so, i have no idea what is going on, nether can i check it out on the spot..
i would really appreciate some advice - particularly, if it can be done through ssh..
thx beforehand to anyone who tries..

---

### Post by _6i on 2009-06-14
around the time it happened, i was just updating packages, installed gdesklets (box uses gnome) and played with X forwarding through ssh
could any of those invoke the problem at hand?

i tried to 'sudo reboot' when someone was logged in - no problem before, stuck now - and to first log out the user, then reboot - same. stuck.

anyone? any idea?

---

### Post by _6i on 2009-06-14
in the meanwhile, i read through the linked bugreports and the box has MSI or ASUS motherboard - none of the mentioned vendors - and their problems seemed constant, but my machine just started to act wierd..

---

### Post by lisati on 2009-06-14
I am aware of some users reporting a hang on shutdown or restart that is somehow connected with wifi cards, but can't recall a suitable link at the moment.....

---

### Post by arstanj on 2009-06-15
I think you should see what process is blocking reboot. Sometimes some process will have to shutdown properly before your machine can do a reboot. So I'd suggest to see ps ax results. Then kill those process and try rebooting again.

Also, from my own experience I know there are times when hdds fails due to read only access.

If all of those wont help here's how you can trigger reboot:

   1. echo 1 > /proc/sys/kernel/sysrq
   2. echo b > /proc/sysrq-trigger

[URL="http://bit.ly/s1zqi"]
http://bit.ly/s1zqi[/URL]

---

### Post by _6i on 2009-06-15
thanks for the fast replies

as for the wifi card, don't bother, no such thing in my box.. just a 10/100 old Realtek RTL 8029 AS and an onboard gigabit ethernet card, one of which is connected to the internet through a router (my vote would be on the 10/100)

as for the "debugging" attempt, thanks, i should try that, but it certainly won't be easy doing it remotely.. :)
..and i can proceed only when someone's around and can spare the time, to push the button and read the screen for me :DDD
wish me luck :D

---

### Post by v3xtra on 2009-06-15
Do you by any chance have an IDE HDD attached?  Or are you using SATA?

I believe there was something that was happening to IDE hard drives that prevented reboots / halts.  The operating system would unmount the filesystem before the computer would be able to shut down, and it would just hang there.  I would try and search for the topic that has a solution, it is a script that keeps the HDD mounted until shutdown or something to that nature, and if that is the case, it is definitely worth a try.  It does the same thing on my box, but it ends up shutting down fine, and I just feel it is somewhat specific with how it happens!

---

### Post by _6i on 2009-06-15
i had a little "user-time" on my hands, so i managed to try out some things

as a first step, i purged gdesklets (that was what i installed, around the time, the problems started) than done autoremove and tried the simple 'sudo reboot' (and i had someone watching the screen for me :) )
-> shutdown went ok, but when starting up, the system couldn't boot (like if grub were never there - no-bootable-disk type error in bios)
(probably this was the case before, and i wasn't really surprised, it happened again, because even if it was gdesklets which caused the problem, it could have stayed loaded or in the memory etc., however before trying to reboot, i logged off all users)
 then after simply turning off and on the box, ubuntu booted correctly

then after boot (the login screnn was running), BEFORE anyone logged in, i tried 'sudo reboot' again
-> reboot ok

then after boot i let my man log in to an account, which was not used for some time (it was never used while gdesklets was installed), then after the desktop was loaded and before starting any app manually another 'sudo reboot' came
-> reboot ok

then let my man to log in to the most used user account (this was always logged in to, when i tried to reboot and the problem showed - even if i logged it out first; usually the account was locked with firefox or sometimes skype running, so nobody was working with it during the reboot attempt), but right after the desktop gui was loaded and again, before starting anything manually, i tried to reboot
->  reboot ok

than my man had to go, so that's it for today..
but it seams, either it was something with gdesklets (or one of its dependencies), or maybe something that the heavily used account started (that would be interesting, because it almost always runs only firefox and skype)

well, i'll try to figure out, what caused the problem, when somebody will be there again
in the meanwhile any suggestion or idea is welcome..

---

### Post by _6i on 2009-06-15
> **v3xtra said:**
> Do you by any chance have an IDE HDD attached?  Or are you using SATA?

I believe there was something that was happening to IDE hard drives that prevented reboots / halts.  The operating system would unmount the filesystem before the computer would be able to shut down, and it would just hang there.  I would try and search for the topic that has a solution, it is a script that keeps the HDD mounted until shutdown or something to that nature, and if that is the case, it is definitely worth a try.  It does the same thing on my box, but it ends up shutting down fine, and I just feel it is somewhat specific with how it happens!

hmm, according to my trial this could have been the case, however iirc i have just one SATA HDD there
but why did it reboot correctly when it did then?..
..and what caused the problem in the first place?..

---

### Post by Endolith on 2009-11-13
Mine normally reboots fine, but now I send it "sudo reboot now" and it says "The system is going down for reboot NOW!" and then just continues on doing whatever it was doing.  I keep typing it over and over and it still doesn't do anything.

This did work though:

```
sudo su
echo 1 > /proc/sys/kernel/sysrq
echo b > /proc/sysrq-trigger
```

---

### Post by jeb800e on 2009-11-13
Have you tried the REISUB technique?

Hold down on Alt + SysRq and slowly, and one at a time, press "R", then "E", then "I", "S", and "U", and "B". This will not FORCE the system to do an emergency restart, but will instead (should) safely restart your system.
Search it up online to learn more!

Also, have you tried updating your system? If you haven't, that should be a major help!

---

### Post by Endolith on 2009-11-13
> **jeb800e said:**
> Have you tried the REISUB technique?

Hold down on Alt + SysRq and slowly, and one at a time, press "R", then "E", then "I", "S", and "U", and "B". This will not FORCE the system to do an emergency restart, but will instead (should) safely restart your system

That doesn't work if you're not in front of the computer.  :)  I think the commands I listed do the same thing, tough.

---

### Post by mandza on 2011-06-06
i have same problem,
sudo reboot and sudo halt -f now dont work (they dont reboot)
but sudo halt -p is shutting down my pc

---

### Post by CharlesA on 2011-06-06
> **mandza said:**
> i have same problem,
sudo reboot and sudo halt -f now dont work (they dont reboot)
but sudo halt -p is shutting down my pc
Make a new thread as this one is over 3 years old.

---


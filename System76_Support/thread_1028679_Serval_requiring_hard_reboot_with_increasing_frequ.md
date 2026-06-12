---
title: "Serval requiring hard reboot with increasing frequency"
date: 2009-01-02
forum: System76 Support
---

### Post by VOLKOV9 on 2009-01-02
I've been using a Serval for about half a year now, and until recently was very pleased with it.  For the last month or so (since upgrading to Intrepid), however, it has been jamming with increasing frequency.  By jamming, I mean that the computer becomes completely unresponsive, and the little blue caps and scroll lock lights blink synchronously.  The only thing I can do at such a point is a hard reboot.  I've had lots of little theories about what's causing it - something misfiring in the graphics card, overheating, power surges, something malicious running through Wine - but none of these seems to consistently explain it - it happens sometimes every twenty minutes, sometimes it goes a day without it; it happens sometimes when I'm running the entire processor and sometimes when I'm not doing anything and the frozen screen shows the processor wasn't running at more than a few percent.

The frequency is not consistent, but generally seems to be increasing.

Could someone point me in the right direction?  It's crippling an otherwise powerful computer.

PS: If this is unrelated, then ignore it and I'll post another thread about it, but I'm including it in case it's another symptom of the same thing: Since upgrading to Intrepid (and installing the System76 driver), the wireless card occasionally ceases working (but thinks it's still working), and physically toggling it on and off then reactivating networking via the network manager repairs it.  This problem was non-existent in Hardy.

---

### Post by thomasaaron on 2009-01-02
They could be related. That's a kernel panic. Please go to a terminal and run this command...

sudo apt-get --reinstall install linux-backports-modules-intrepid

...and see if that fixes it.

---

### Post by VOLKOV9 on 2009-01-03
Done.

Well, it's only been a day or so, but so far the "panics" seem to have ceased - so thanks for that.  However, since reinstalling that, it shut down fine the first time, but now every time I try to shut down, it skips the usplash and the text alerts me that it's failed to kill the avahi-daemon, to "kill all remaining processes", and to unmount (device busy).  then it says "* Will now halt" and hangs.

That said, the intermittent wireless hiccups are still present, except now NetworkManager doesn't react when I tell it to deactivate wireless or networking, so my only recourse is a reboot, which has the problem outlined above.

Thanks again for the help.

---

### Post by thomasaaron on 2009-01-05
Thanks, please note the time on your computer before attempting a shutdown. Then, after the hang, reboot and run these commands:

cat /var/log/messages > ~/Desktop/messages.txt
cat /var/log/syslog > ~/Desktop/syslog.txt


Attach the files these commands create on your Desktop to this thread. Also, let me know the aforementioned time.

---

### Post by VOLKOV9 on 2009-01-10
OK.  There are no longer shutdown problems.  I don't know what the problem was, but it's gone.  However, the internet still cuts out sometimes, and there doesn't seem to be a consistent explanation as to why.  I don't know if it helps, but once after it happened, I ran the commands you said, and here are the outputs (shaved down to be small enough to attach).  It happened around 19:06.

---

### Post by glacialfury on 2009-01-10
> **thomasaaron said:**
> They could be related. That's a kernel panic. Please go to a terminal and run this command...

sudo apt-get --reinstall install linux-backports-modules-intrepid

...and see if that fixes it.

Volvo, I had this exact problem on my Serval after upgrading (the flashing blue lights requiring hard reboot).  Running the above command, as Tom suggested to me in my thread, did indeed fix that problem.

This is just to give you hope for the future :-)

---

### Post by VOLKOV9 on 2009-01-18
Just clarifying: by 'the internet cuts out,' I mean that the wireless does one of a few things:
[LIST]
[*]Thinks it's still connected but cannot access anything
[*]Actually disconnects and can no longer see any networks
[*]Stays connected, but the bandwidth is being clogged by something.
[/LIST]

Occasionally, the first bullet, after several minutes, goes to the second bullet.

Never had this problem before Ibex.  After Ibex, I could disable and reenable networking, and that would fix it.  After performing the above fix for kernel panics, that solution rarely works, and a full reboot is required.  Rarely, when first booting up, the wireless card can't find networks.

The problem seems somewhat more frequent with my university network than my home network.

This is kind of similar to this issue: [http://ubuntuforums.org/showthread.php?t=1004431&highlight=bandwidth&page=2](http://ubuntuforums.org/showthread.php?t=1004431&highlight=bandwidth&page=2)

The text files above are from an instance of the first bullet; I have a screenshot of the third bullet, but can't upload it b/c I'm currently experiencing the third bullet; I'll upload it when I can.

---

### Post by VOLKOV9 on 2009-04-30
I was kind of hoping that Jaunty would magically fix this (as it seems that Intrepid caused it), but alas, it remains.  It *might* have less frequency, but that might just be small sample size noise so far.  I've now had this problem for more than one release.  Any ideas?

---

### Post by thomasaaron on 2009-05-01
I've seen a similar problem on university networks in the past. Does it occur primarily during downloads? If so, it could be on the university's end.

Really, the key thing we need to know is: Does it only happen on the university network, or does it happen on your home network/other network as well?

Also, *immediately* after a it drops the connection, go to System > Administration > System76 Driver > Support > Create and attach the logs.tar file created in your home dir.

---

### Post by PatrickVogeli on 2009-05-01
Maybe you could try the following: 

sudo -s 
echo "options iwl3945 disable_hw_scan=1" >> /etc/modprobe.d/iwl3945.conf

and then reboot? I've seen kernel panics as the ones you describe (flashing lights) in Jaunty, and they're fixed with that.

If it doesn't help, you can revert simply by doing sudo rm -rf /etc/modprobe.d/iwl3945.conf

hope it helps!

---


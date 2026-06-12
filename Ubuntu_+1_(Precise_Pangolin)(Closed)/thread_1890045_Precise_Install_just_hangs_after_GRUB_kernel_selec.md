---
title: "Precise Install just hangs after GRUB kernel selection"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by OGpmpdog on 2011-12-02
Happy Holidays all.

I tried to install Precise over an existing partition.

This is a simple partition setup:
sda = GRUB bootloader
sda1 = Natty (last ditch effort to hang on to Grub 2 :)

extended
sda7 = used to be Oneiric - now a hanging Precise bummer
sda5 = Swap
sda2 - Home

The partition is recognized in GRUB (obviously) and I checked in Gparted, and partition says "Precise Development".

Everything seemed OK but after choosing the kernel in GRUB, my laptop (T61) just hangs while Plymouth performs system checks.

startx doesnt work, as Nvidia is not recognized yet.
CTRL/ALT/F7 doesnt work.

Thought I had a corrupted download but the Live USB works perfectly.

HELP!!  Thanks ahead of time

---

### Post by ventrical on 2011-12-02
When you are installing and you choose "somethng else" don't forget to ,format, choose ext4 and then "/" without the quotes.
Regards,ventrical

---

### Post by OGpmpdog on 2011-12-02
> **ventrical said:**
> When you are installing and you choose "somethng else" don't forget to ,format, choose ext4 and then "/" without the quotes.
Regards,ventrical

Hi and thank you for responding :)

Yes, I assigned the ext4 file system, clicked the format box, and mounted root (/)

I'm actually looking for some alternatives to try to access the GUI.

Thanks again.

---

### Post by paul_in_london on 2011-12-02
> **OGpmpdog said:**
> Hi and thank you for responding :)

Yes, I assigned the ext4 file system, clicked the format box, and mounted root (/)

I'm actually looking for some alternatives to try to access the GUI.

Thanks again.

See if you can boot into recovery mode, choose netroot from the menu that comes up if you can get that far and check for updates. Look at this thread for ways to disable plymouth (assuming you can at least get to a root prompt):

[http://ubuntuforums.org/showthread.php?t=1886633](http://ubuntuforums.org/showthread.php?t=1886633)

EDIT: I created the following files in /etc/init:

```
paul@precise-64:~$ ls -la /etc/init/plymouth*over*
-rw-r--r-- 1 root root 7 Dec  1 01:23 /etc/init/plymouth-log.override
-rw-r--r-- 1 root root 7 Dec  1 01:23 /etc/init/plymouth.override
-rw-r--r-- 1 root root 7 Dec  1 01:23 /etc/init/plymouth-splash.override
-rw-r--r-- 1 root root 7 Dec  1 01:23 /etc/init/plymouth-stop.override
-rw-r--r-- 1 root root 7 Dec  1 01:23 /etc/init/plymouth-upstart-bridge.override
paul@precise-64:~$
```

each containing the string "manual".

Example:

```
paul@precise-64:~$ cat  /etc/init/plymouth.override
manual
paul@precise-64:~$
```

---

### Post by drs305 on 2011-12-02
I installed within the past 24 hours. Of course there are lots of reasons it might hang. If you have an older nvidia card:

With my gs7600 card, the boot continued to hang at various boot messages. In my case, I had to boot to the recovery mode, purge nvidia* and reinstall nvidia-current. After doing this my system booted correctly.

Here is my post about it if you think this might be your situation:
[http://ubuntuforums.org/showthread.php?t=1889658]("http://ubuntuforums.org/showthread.php?t=1889658")

---

### Post by OGpmpdog on 2011-12-02
Hi folks and thanks again for your responses, especially to the gentleman who helped me disable plymouth.

I was able to boot into recovery kernel, and even managed some updates and upgrades.

I installed synaptic, and tried to run from command line.
Got an error message saying something like 'unable to draw'

I could not access nvidia or "repair broken packages" repositories.

I didnt want to purge nvidia* - I might not be able to reinstall.

Thoughts?

P.S. I'm borderline clueless diagnosing and fixing Ubuntu graphics issues. Please bear with me.

---

### Post by drs305 on 2011-12-02
> **OGpmpdog said:**
> 
I didnt want to purge nvidia* - I might not be able to reinstall.


That's fine. We never want you to do something you aren't comfortable with. Someone may come up with a different way of doing things.

For me, the 'nomodeset' option didn't work, but you could press 'e' at the Grub menu to enter the Grub editing mode. Cursor to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'. Then CTRL-x to boot. This edit is non-persistent, but perhaps you will be able to get to the Desktop where you can reinstall your video drivers.

---

### Post by lolpenguin on 2011-12-02
I installed Oneiric and changed /etc/apt/sources.list and have no problems? Why not try that?

---

### Post by paul_in_london on 2011-12-02
> **OGpmpdog said:**
> Hi folks and thanks again for your responses, especially to the gentleman who helped me disable plymouth.

I was able to boot into recovery kernel, and even managed some updates and upgrades.

I installed synaptic, and tried to run from command line.
Got an error message saying something like 'unable to draw'

I could not access nvidia or "repair broken packages" repositories.

I didnt want to purge nvidia* - I might not be able to reinstall.

Thoughts?

P.S. I'm borderline clueless diagnosing and fixing Ubuntu graphics issues. Please bear with me.

So you still can't boot to the GUI (desktop)? What is it you tried to do from the command line? nvidia-current is in the proprietary drivers repository. Boot back into recovery mode and try this:

```
sudo aptitude reinstall nvidia-current
```

You may get an error to the effect that it can't be reinstalled - which in your case could be because you don't actually have it installed. If that first command fails, try

```
sudo aptitude install nvidia-current
```

instead.

If you can get to the GUI you can enable additional repositories using synaptic ("Settings -> Repositories" and tick everything then update/upgrade again). Otherwise we can give you command line alternatives. :)

---

### Post by OGpmpdog on 2011-12-05
Hi all, me again :)

A Big shout-out to the community for taking time to help.  I learned a few things about GRUB and nomodeset.

I considered all recommendations. I ended up just editing the source lists(duhhhhhh!!)to reflect oneiric repositories.

It took almost 2 hours - and upgrade to Precise was successful!

My graphics card in my T61 is ancient and doesnt get along with GRUB and X.

I recently built a Sandy Bridge PC. The Precise install took all of 25 minutes.

Now, I'm gonna try to install Lucid on Sandy Bridge/1155 chipset.:lolflag:

This thread will be marked as SOLVED.

Happy Holidays.

---

### Post by irv on 2011-12-06
Even though this tread is marked "solved", I woul like to add that I had a problem with 12.04 hanging after installing, but my problem was different.
I found that if you select install restricted extras when intalling there is a problem with some file that does not let the OS load after installing.
I filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/899608]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/899608") but there was a bug report that was for the same reason: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/850264]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/850264")
The fix was that I installed with out the restricted extras. After I got everything running and booting, I installed the Ubuntu restricted extras and everything worked.

---


---
title: "Virtual Box breaks ALL my mouse function"
date: 2010-10-14
forum: Virtualisation
---

### Post by phubert28 on 2010-10-14
64 bit Ubuntu 10.10

I just fired up VirtualBox (new version since 10.10) and it immobilized my MOUSE - PERIOD.

The mouse wouldn't function in the VirtualBox WinXP OR in Ubuntu when I bring up VirtualBox & start XP.

---

### Post by CharlesA on 2010-10-14
Is mouse integration enabled?

---

### Post by phubert28 on 2010-10-14
Well, it was working perfectly BEFORE 10.10 -and- the VirtualBox upgrade I installed today - didn't TRY to use it BEFORE that upgrade.

I assume it HAD been set - was once familiar with it in the professional versions of VMWare server editions.  Looking for such a setting now, I don't see it.

BUT, when I looked for a setting just now, I didn't find one (not to say it doesn't exist, I just couldn't FIND it!)

---

### Post by CharlesA on 2010-10-14
The mouse integration is a feature of the guest additions.

Does it only cause the mouse to stop working after you start a VM, or after you start VBox?

---

### Post by phubert28 on 2010-10-14
After I start my XP session. NO problem just starting VBox.

But when I hit "start" bye bye mouse 100% - I had to do a hard power down to get out of it.

Do you know of any key combination that is SUPPOSED to unlock the mouse.

I had guest additions installed, but perhaps the update to VBox interfered with that? That is, that the guest additions for the old version might be incompatible with the new?

Of course that would imply I'd have to install a NEW XP VM under the new version... ugh.

**

An earlier problem: after upgrading from 10.4 to 10.10, Update Manager's "Install" won't work - any place to post BUGS???

---

### Post by CharlesA on 2010-10-14
Hit right Ctrl to get focus back to the host.

You can just install the new guest additions over the old ones.

---

### Post by phubert28 on 2010-10-14
Yes, I tried Right Ctrl - zip. FIRST thing I tried. Then I just began to play with keys!!! Esc, Ctrl-Alt-Del - whatever. (desperation)

---

### Post by phubert28 on 2010-10-14
Now, if I need the guest RUNNING, then I CAN'T install ANYTHING in that guest since I HAVE no function - I don't think it was ONLY the mouse that was frozen out.

---

### Post by CharlesA on 2010-10-14
What you could do is purge virtualbox and then reinstall it and see if the same thing happens.

```
sudo apt-get purge virtualbox-3.2
```

```
sudo apt-get install virtualbox-3.2
```

If that doesn't work, then try creating a new VM and booting a livecd or something inside and see if the mouse and keyboard do the same thing.

---

### Post by phubert28 on 2010-10-14
Probably good suggestions - would that mean ALSO reinstalling my VM????

But a bit more information:

The mouse FUNCTIONS apparently are FINE (tho I can't break out of XP into Ubuntu), bit the mouse ICON doesn't move.

Tested a bit with right click & such AND noticed that the USB pointer indicator in VBox was showing activity when I moved the mouse, clicked on a button or used the scroll wheel.

---

### Post by CharlesA on 2010-10-14
Nah, you shouldn't have to reinstall the VM. the virtual hard drive would still be there.

Do you happen to have desktop effects enabled? Just wondering.

---

### Post by phubert28 on 2010-10-14
Forgive me, "desktop effects"??

---

### Post by CharlesA on 2010-10-15
Compiz or whatever it's called. The fancy stuff. :P

---

### Post by phubert28 on 2010-10-15
No, don't waste time with the fancy stuff.

The VBox removal/reinstall didn't help.

---

### Post by phubert28 on 2010-10-15
However, there SEEMS to be a "python" process running I didn't see in 10.4 - sucking up quite a lot of CPU - doesn't seem to come back after I kill it.

---

### Post by gradinaruvasile on 2010-10-15
There is a [bug in virtualbox]("http://www.virtualbox.org/ticket/4529")  that affects newer kernels (2.6.35+) it seems.
Open a terminal and type

sudo service vboxdrv restart

Then

dmesg

see the latest lines - sometimes there is an error that states that the vboxdrv  module cannot disable the [NMI watchdog]("http://x86vmm.blogspot.com/2005/10/linux-nmis-on-intel-64-bit-hardware.html").

This issue happened to me in Debian. It is more pronounced (happens more often) with the 2.6.35 kernel. The fix is to reload the service until dmrsg does not show that error.

---

### Post by phubert28 on 2010-10-15
5367.285506] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
[ 5424.336381] vboxdrv: **Trying to deactivate the NMI watchdog permanently...**
[ 5424.336385] vboxdrv: Successfully done.
[ 5424.336386] vboxdrv: Found 2 processor cores.
[ 5424.336709] VBoxDrv: dbg - g_abExecMemory=ffffffffa0f8fd60
[ 5424.336722] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x6e0
[ 5424.337137] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 5424.337139] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
[ 5452.276541] vboxdrv:** Trying to deactivate the NMI watchdog permanently...**
[ 5452.276544] vboxdrv:** Warning: 2.6.31+ kernel detected. Most likely the hardware performance**
[ 5452.276545] vboxdrv: **counter framework which can generate NMIs is active. You have to prevent**
[ 5452.276546] vboxdrv: **the usage of hardware performance counters by**
[ 5452.276547] vboxdrv: ***  echo 2 > /proc/sys/kernel/perf_counter_paranoid***

Is that along the lines of the problem?

Tried the suggested command with the following result:

[ 5452.277614] vboxdrv: Successfully loaded version 3.2.10 (interface 0x00140001).
paul@Aragorn:~$ echo 2 > /proc/sys/kernel/perf_counter_paranoid
bash: /proc/sys/kernel/perf_counter_paranoid: **No such file or directory**
paul@Aragorn:~$

---

### Post by phubert28 on 2010-10-15
Any idea why 10.10 presents this cpu-hungry python process where 10.4 did not???

---

### Post by gradinaruvasile on 2010-10-15
Something like that. The issue is that sometimes the module loads ok sometimes throws this error. I had the mouse (and some times keyboard too) control loss even if i virtualbox did not run.

@phubert28:

If you kill that process, do you have any functionality loss?

Open a terminal, type 

top

copy the process PID (first row on the left), press q to close top then type:

ps ax | grep <PID>

Where <PID> is the number you copied before. This way you can see the full command.

---

### Post by phubert28 on 2010-10-15
So far it seems to always encounter the error.

I guess I just don't mess with Windows for now tho there's SOME software I can ONLY use there.

Thanks much for the insight, however!

---

### Post by gradinaruvasile on 2010-10-15
> **phubert28 said:**
> So far it seems to always encounter the error.

I guess I just don't mess with Windows for now tho there's SOME software I can ONLY use there.

Thanks much for the insight, however!

You can try the following:

sudo rmmod vboxnetadp vboxnetflt vboxdrv

then:

sudo modprobe vboxdrv

See if the dmesg output is the same. As i said before i had the mouse issue even i did not run virtualbox, only the modules were loaded (which they do automatically at startup). So an idea would be unloading the modules (service vboxdrv stop) when not needed.

---

### Post by phubert28 on 2010-10-15
Thanks, [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640"), I'll try that - getting a bit late this side of the world, tho! :-)

---

### Post by phubert28 on 2010-10-15
?? "modprove" - "command not found"

Or is that "modprobe"?

Still gets the NMI messages

---

### Post by gradinaruvasile on 2010-10-15
Oops, my bad... Yes it is modprobe. I got a clean loading at the second-third loading usually on Debian.
Also you can try rebuilding the kernel modules for virtualbox:

sudo /etc/init.d/vboxdrv setup

---

### Post by phubert28 on 2010-10-15
Common typo ... I Googled and found more info, anyway.

In the meantime, Update Manager still won't respond to a click on "Install Updates" so I'm doing it manually...

---

### Post by phubert28 on 2010-10-15
Now I found THIS message from dmesg interesting, tho the echo redirect didn't find the directory or file:

You have to prevent the usage of hardware performance counters by
  echo 2 > /proc/sys/kernel/perf_counter_paranoid

(this is after running the VBox kernel modules rebuild you suggested)

---

### Post by gradinaruvasile on 2010-10-18
Well now with the 2.6.32-25 kernel upgrade on Debian i had to recompile twice the voxdrv modules in order to get the "MNI watchdog succesfully disabled" message, unloading/reloading did not help (did it about 10-15 times).

---

### Post by phubert28 on 2010-10-18
Fun. Never tried compiling UNIX stuff from source (naturally did LOTS of that with my own programs on RCA ... :-D )

---


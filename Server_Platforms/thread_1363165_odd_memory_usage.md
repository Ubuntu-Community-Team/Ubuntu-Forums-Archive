---
title: "odd memory usage"
date: 2009-12-24
forum: Server Platforms
---

### Post by lavinog on 2009-12-24
I have a personal server that I just updated to karmic from jaunty.

I started noticing abnormal memory usage at startup.
free would report that the used memory (+/- buffers/cache) would be around 270M...at one point it was over 500M  (this is a wind pc so 1g is the max mem)
I removed pretty much all services (apache, dns, mysql...etc) and each reboot would start with about 270M used.
After rebooting one last time, it is down to its normal value (28M)

Between each reboot I was removing another package to see if I can figure out what package was causing it.  I am thinking this might have something to do with the boot profiler.  I noticed anytime I removed a package, apt would display a message about a re-profile will occur at next boot.  The next boot would yield a high memory usage, and the following boot would be fine.  What is the proper way to trigger a re-profile with ureadahead?  Is it still the kernel option?

Before anyone mentions that used memory is good memory, I am not talking about cache usage.

---

### Post by HighCommander540 on 2009-12-24
> **lavinog said:**
> I have a personal server that I just updated to karmic from jaunty.

I started noticing abnormal memory usage at startup.
free would report that the used memory (+/- buffers/cache) would be around 270M...at one point it was over 500M  (this is a wind pc so 1g is the max mem)
I removed pretty much all services (apache, dns, mysql...etc) and each reboot would start with about 270M used.
After rebooting one last time, it is down to its normal value (28M)

Between each reboot I was removing another package to see if I can figure out what package was causing it.  I am thinking this might have something to do with the boot profiler.  I noticed anytime I removed a package, apt would display a message about a re-profile will occur at next boot.  The next boot would yield a high memory usage, and the following boot would be fine.  What is the proper way to trigger a re-profile with ureadahead?  Is it still the kernel option?

Before anyone mentions that used memory is good memory, I am not talking about cache usage.

So you were using this much memory at start-up or after a period of time?

---

### Post by lavinog on 2009-12-24
Ok this does seem like a bug.

Here is my initial memory (using free -m):
```

             total       used       free     shared    buffers     cached
Mem:           994         85        909          0         24         34
-/+ buffers/cache:         **25**        968
Swap:          572          0        572

```

Then I delete /var/lib/ureadahead/pack and reboot
This is the memory usage after the reboot:
```

             total       used       free     shared    buffers     cached
Mem:           994        319        674          0          4         34
-/+ buffers/cache:        **280**        713
Swap:          572          0        572

```

Then I reboot again, leaving /var/lib/ureadahead/pack alone:
```

             total       used       free     shared    buffers     cached
Mem:           994         86        908          0         25         34
-/+ buffers/cache:         **26**        968
Swap:          572          0        572

```

It appears that ureadahead does not release the memory it uses.
I wonder if this is related to these bugs:
[buffer overflow in values.c](https://bugs.launchpad.net/ureadahead/+bug/485194)
[When trying to profile on a system with 512MB -- get a kernel OOM](https://bugs.launchpad.net/ureadahead/+bug/491943)
[after deleting pack file, first boot is fast, subsequent boots are slow](https://bugs.launchpad.net/ureadahead/+bug/491956)

So it looks like to maximize your server performance, you need to reboot twice after applying certain updates.

---

### Post by lavinog on 2009-12-24
I just verified this behavior with lucid desktop in a vm:
```

-----------------
Thu Dec 24 02:57:58 CST 2009
             total       used       free     shared    buffers     cached
Mem:           997        299        698          0         33        113
-/+ buffers/cache:        152        845
Swap:          321          0        321
-----------------
Thu Dec 24 02:59:18 CST 2009
             total       used       free     shared    buffers     cached
Mem:           997        400        597          0         17        101
-/+ buffers/cache:        280        717
Swap:          321          0        321
-----------------
Thu Dec 24 03:00:44 CST 2009
             total       used       free     shared    buffers     cached
Mem:           997        298        699          0         33        112
-/+ buffers/cache:        152        845
Swap:          321          0        321

```

---

### Post by lavinog on 2010-01-05
I am noticing that when I set ureadahead to reprofile on next boot, there tends to be some graphical issues such as xorg might segfault, or the login screen hangs.
Maybe ureadahead is the cause of the stability issues in karmic.

---

### Post by lavinog on 2010-01-05
bug report:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by HighCommander540 on 2010-01-05
> **lavinog said:**
> bug report:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

Good man.

---

### Post by lavinog on 2010-05-10
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715):
[quote=Petar from bug report]
[quote=lavinog]
I am sure it is taken seriously. The dev is likely tending to more important issues at the moment.
The issue isn't a security issue, and it doesn't seem to cause any data loss.
[/quote]
lavinog you sound like one of the creators of Windows Vista. :) I'm sorry, but as a long time Linux user, I'm somehow spoiled by the idea/reassurance that my OS is not eating parts of my RAM if there are no objective reasons for it do so. I agree that security issues and data loss problems are extremely important, but fixing a loss of 250MB of RAM is equally important for me.
[/quote]
You have already mentioned that uninstalling ureadahead did not address the lost ram.  It also sounded as if the lost ram happened on every boot...if this is correct, the ureadahead bug is not the cause.
I agree that swapping with 2g of ram is not normal, and I would be happy to offer assistance with finding the cause.  If you already started a thread for your issue, can you give me a link to it?

---

### Post by lavinog on 2010-05-10
For those that want a immediate fix for the issue, I have written a init script to clear the trace buffer after the pack files are created.

To install this script:
```

gksu gedit /etc/init/ureadahead-cleaner.conf

```

paste the following code:
```

# ureadahead-cleaner - free tracing buffer after a ureadahead profile
# 
# This is only intended as a hack workaround for bug: 501715
# https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715
# "Kernel trace buffer should be cleared and size restored after profiling" 
#
# For more info, see this thread: http://ubuntuforums.org/showthread.php?t=1363165

description	"free tracing buffer"

start on (stopped ureadahead 
	  and stopped ureadahead-other)

task

script

  if [ "$(cat /sys/kernel/debug/tracing/buffer_size_kb)" -eq "128000" ]
  then

    # Wait up to five mins for pack file to be generated
    for delayloop in {1..300}
    do

         [[ -e /var/lib/ureadahead/pack ]] && break

         sleep 1

    done

    # if pack file exists, trace file should no longer be needed.

    # reduce the trace buffer
    echo 1 > /sys/kernel/debug/tracing/buffer_size_kb

  fi

end script

```
Save, then close gedit.

Now when you reboot, if ureadahead does a trace, it will wait until a pack file is written (I don't know if the wait is really needed, but added it just to be safe.)  It will then set the tracebuffer to 1kb from 128Mb

Let me know if it worked for you.

Another solution is to recompile ureadahead, but for some users, this might be a better fix for now.

If you do use this script, make sure you subscribe to the bug report so that when the bug is fixed, you can remove the script.

---

### Post by RossNM on 2010-05-20
I followed the directions and installed your script and rebooted, and my base memory usage on login went from 480+MB  to around 250.  Thanks, this was bugging me.

---


---
title: "Edgy on Wild Dog crashes hard when starting update manager"
date: 2006-11-10
forum: System76 Support
---

### Post by lord trousers on 2006-11-10
I don't want to test this too much right now, as I'm running quite a long simulation - so I've only tried it twice. But both times, when clicking the update manager icon, I got the update manager window *very* briefly, and then the machine shut down hard. Click - off.

I'll check it out again - running update-manager from the command line, etc. - when I can spare the time.

---

### Post by crichell on 2006-11-10
If the machine crashes when you run updated manager again post a snippet of the kernel messages at the time of the crash.  --We haven't seen this happen (yet :))

---

### Post by lord trousers on 2006-11-10
Well, the machine is *off* after it happens, so that's rather difficult. Would they be in a log somewhere?

---

### Post by lord trousers on 2006-11-10
New information: it only happens when I click the panel icon, but not when I start update-manager from a terminal session.

So where's that log I'm supposed to check?

---

### Post by crichell on 2006-11-11
the log is at /var/log/messages

there is a time stamp so we can look at what is happening directly before the crash.

---

### Post by lord trousers on 2006-11-11
I clicked on the update-manager panel icon at about 16:58. Here's /var/log/messages around then:

```

Nov 10 16:13:11 localhost -- MARK --
Nov 10 16:33:11 localhost -- MARK --
Nov 10 16:53:11 localhost -- MARK --
Nov 10 16:58:56 localhost syslogd 1.4.1#18ubuntu6: restart.
Nov 10 16:58:56 localhost kernel: Inspecting /boot/System.map-2.6.17-10-generic
Nov 10 16:58:56 localhost kernel: Loaded 22825 symbols from /boot/System.map-2.6.17-10-generic.

```

It looks like nothing gets logged at all.

---

### Post by lord trousers on 2006-11-11
kern.log shows similar symptoms - nothing, that is - and so does Xorg.0.log.old.

---

### Post by crichell on 2006-11-11
No it doesn't look very helpful.  I'll start searching around for this one.  Have you guys upgraded other Wild Dog's?  It it happening on any of the others?

---

### Post by lord trousers on 2006-11-12
One hasn't been unpacked, and the other two are running Windows XP. I haven't heard any reports of strange shutdowns on those.

I may try replacing the NVidia Xorg driver.

---

### Post by Skia_42 on 2006-11-17
> **lord trousers said:**
> New information: it only happens when I click the panel icon, but not when I start update-manager from a terminal session.

So where's that log I'm supposed to check?

So the update-manager opens in the command line but not with the panel icon? Check to make sure the panel icon is running the same command as the one you put into the command line.

---

### Post by lord trousers on 2006-11-19
How do I do that? The only way I know of is to click on it and check the process list, but that's not an option right now.

---

### Post by crichell on 2006-11-19
I'm using the nvidia package in the repositories and can't re-create the problem on our test systems - nor is there much info out there when I'm searching.

did you upgrade with this command:

```
gksu "update-manager -c"
```

---


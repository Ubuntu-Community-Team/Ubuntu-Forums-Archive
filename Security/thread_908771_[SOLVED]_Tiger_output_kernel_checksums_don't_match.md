---
title: "[SOLVED] Tiger output: kernel checksums don't match?"
date: 2008-09-02
forum: Security
---

### Post by doas777 on 2008-09-02
Hello all,

I've just run tiger security scanner, and checked out the log file. Most of it is pretty innocuous or Hardy-specific, but there are a few failures that concern me.

These messages seem to say that the kernel(s) i have installed does not match the checksums:

```

# Checking md5sums of installed files

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.pcimap' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.dep' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.ieee1394map' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.usbmap' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.isapnpmap' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.seriomap' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.alias' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-16-generic/modules.symbols' checksum differs from installed package 'linux-image-2.6.24-16-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.pcimap' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.dep' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.ieee1394map' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.usbmap' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.isapnpmap' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.seriomap' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.alias' checksum differs from installed package 'linux-image-2.6.24-19-generic'.

# FAIL [lin005f]Installed file `/lib/modules/2.6.24-19-generic/modules.symbols' checksum differs from installed package 'linux-image-2.6.24-19-generic'. 

```

I also notice these messages:

```

#

# Checking device permissions...

# FAIL [dev002f]/dev/log has world permissions

# FAIL [dev002f]/dev/nvidia0 has world permissions

# FAIL [dev002f]/dev/nvidiactl has world permissions 

```

so does anyone have any ideas on what to do about this (or is it a non-issue)? I would like to be able to clear up the world permissions issue if nothing else. Also if someone else could replicate these same messages, I would feel much better about it.

I've attached my tiger log in it's entirety. Any help would be much appreciated.

Thanks Folks!

---

### Post by doas777 on 2008-09-05
bump

---

### Post by Midnightsun on 2008-09-09
I can confirm I am receiving the same messages about kernel checksums after running tiger.

Is this something I should worry about?

---

### Post by doas777 on 2008-09-09
> **Midnightsun said:**
> I can confirm I am receiving the same messages about kernel checksums after running tiger.

Is this something I should worry about?


I wish I could say no, but I am quite reassured that someone is able to confirm the messages. the checksum failure indicates that the module may have been tampered with.

I've been operating under the assumption that it's a system specific false-positive, as I have no real reason to believe that my system has been rooted. but then again, if it's a decent kit, I wouldn't ever know it was there. 

if we can find another willing person to run tiger on a system with 2.6.24.19, we can probably call it solved.

Thanks for responding. you are most likely safe, and I feel a little better about it. 

have fun,
Franklin

---

### Post by cariboo on 2008-09-09
I get the same message on a fresh clean installation of Intrepid Alpha5, I also get the message on my server running hardy, so I would say it is safe to ignore it.

Jim

---

### Post by doas777 on 2008-09-09
> **cariboo907 said:**
> I get the same message on a fresh clean installation of Intrepid Alpha5, I also get the message on my server running hardy, so I would say it is safe to ignore it.

Jim

Excelent! Thanks all! I shall mark this as solved.

---


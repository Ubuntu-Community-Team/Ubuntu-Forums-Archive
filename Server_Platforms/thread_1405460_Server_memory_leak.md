---
title: "Server memory leak?"
date: 2010-02-12
forum: Server Platforms
---

### Post by humphreybc on 2010-02-12
Hi everyone,

Have a look here: [http://humphreybc.homeip.net/phpsysinfo](http://humphreybc.homeip.net/phpsysinfo)

That's my server that I'm running. You'll notice the physical memory is already at 97% but the uptime is only 20 hours.

I've noticed that when the server is uploading or downloading, the memory usage increases but never goes back down until I reboot it. Which isn't ideal.

Suggestions? Thanks a lot!

---

### Post by KiLaHuRtZ on 2010-02-12
Most of it is likely to be cached and not physically used.  This is actually a plus as compared to Windows.  If you quit a certain program and re-open, the second time around it will start quicker.  I would not worry, if a new program needs memory, the kernel will flush some out of cache for the new program to use.  To be sure, run this command.

```
free -om
```

This will display memory statistics in MB's.  You will get an output like this.

```
             total       used       free     shared    buffers     cached
Mem:          [COLOR="Blue"]3965[/COLOR]       [COLOR="Red"]3278[/COLOR]        [COLOR="Green"]687[/COLOR]          0        [COLOR="Purple"]196[/COLOR]       [COLOR="Orange"]2170[/COLOR]
Swap:         7632          0       7632
```

The blue is total system memory.
The red is total used memory.
The green is total free memory.
The purple is total buffered memory.
The orange is total cached memory.

To know what is physically in use, subtract the cached (orange) & buffered (purple) value from the used (red) value.

In this case, only 912 MB is physically in use.

---

### Post by humphreybc on 2010-02-12
I get:

```

benjamin@benjamin-server:~$ free -om
             total       used       free     shared    buffers     cached
Mem:           497        467         29          0         56        318
Swap:          956          0        956

```

Also, htop says that I'm only using 92 / 497mb of memory.

---

### Post by KiLaHuRtZ on 2010-02-12
Subtract your buffers...

467 &#8722; 318 &#8722; 56 = 93

---

### Post by humphreybc on 2010-02-12
Cool so it's nothing to panic about :P

Thanks for your replies :)

---

### Post by KiLaHuRtZ on 2010-02-12
You got it!  I forgot about the buffers in my first post, sorry. :(  Now that you know how it works, drop the "o".

```
 free -m
```

Gives you a new line.  That particular line is the memory used/free minus/plus the buffers+cached memory.  In short, it does the math for you. :)

```
             total       used       free     shared    buffers     cached
Mem:          3965       3287        678          0        197       2172
-/+ buffers/cache:        [COLOR="Red"]917[/COLOR]       [COLOR="Green"]3048[/COLOR]
Swap:         7632          0       7632
```

Red is used.
Green is free.

---


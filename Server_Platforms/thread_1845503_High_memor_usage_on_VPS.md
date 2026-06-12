---
title: "High memor usage on VPS"
date: 2011-09-17
forum: Server Platforms
---

### Post by e_torano on 2011-09-17
I'm currently setting up an Ubuntu based VPS for somebody. They want to use Apache + ubuntu whereas I usually tend to use nginx + centOS.

I've got the current setup so far: Apache (from repos) + PHP-FPM + mysql (optimised a little bit - not perfectly, tips would be great) + webmin.

When I checked the memory usage, it was way high. I stopped the webmin service and that brought it down a bit, but the usage seems high compared to what I'm used to with my usual setup.

**VPS stats:**

```

Dedicated memory: 512mb
Burst Memory: 1024mb

```

**Top output:**

```

top - 09:55:26 up 13:26,  0 users,  load average: 0.00, 0.00, 0.00
Tasks:  13 total,   1 running,  12 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1048576k total,   725252k used,   323324k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1313 mysql     17   0  158m  22m 6944 S    0  2.2   0:00.17 mysqld
 1497 www-data  15   0  130m 5804 2348 S    0  0.6   0:00.00 php5-fpm
 1496 root      18   0  129m 4644 1372 S    0  0.4   0:00.18 php5-fpm
 3408 root      18   0 80048 3124 1568 S    0  0.3   0:00.00 apache2
 3414 www-data  20   0  350m 2692  904 S    0  0.3   0:00.00 apache2
 3412 www-data  21   0  350m 2688  900 S    0  0.3   0:00.00 apache2
 3411 www-data  18   0 79780 2092  564 S    0  0.2   0:00.00 apache2
 3410 www-data  18   0 79780 2068  540 S    0  0.2   0:00.00 apache2
 3357 root      15   0 17872 1932 1448 S    0  0.2   0:00.00 bash
    1 root      15   0 23320 1560 1272 S    0  0.1   0:00.44 init
 3477 root      15   0 19096 1308 1064 R    0  0.1   0:00.00 top
 1128 root      15   0 49268 1092  544 S    0  0.1   0:00.02 sshd
 3356 root      15   0 11228  352  224 S    0  0.0   0:00.00 vzctl


```

(as you can see, mysql is the highest - though it is lower than it was before)

**free -lm output**

```

             total       used       free     shared    buffers     cached
Mem:          1024        707        316          0          0          0
Low:          1024        707        316
High:            0          0          0
-/+ buffers/cache:        707        316
Swap:            0          0          0


```








Any help bringing the usage down would be greatly appreciated. The guaranteed memory is only 512mb, so using 707mb isn't ideal at all...

---

### Post by e_torano on 2011-09-17
I finally managed to bring the memory usage down to about 181MB so that should be alright for now.

I am, however, now facing an issue with SSH where I can only log in with the console account provided by the VPS host. Annoying.

---


---
title: "Blank page after upgrade"
date: 2016-08-06
forum: Server Platforms
---

### Post by Will_Moonen on 2016-08-06
Hi Everyone,

I'm a bit puzzled - after upgrading from Ubuntu 14.04.4 LTS to 16.04.1 LTS, all Wordpress websites running on that server are just showing a single white page; even a one-liner of php script showing the system versions is just presenting a white page with the appropriate favicon icon.

However, I also tried a plane html file; which shows as expected.

With 14.04.4 everything worked fine.

The error.log of Apache shows:
```
[Sat Aug 06 17:33:30.319668 2016] [mpm_prefork:notice] [pid 3502] AH00163: Apache/2.4.18 (Ubuntu) PHP/7.0.8-0ubuntu0.16.04.2 OpenSSL/1.0.2g-fips configured -- resuming normal operations
```
Which seems ok to me.

There is also an FPM-log that states "ready to accept connections"; no errors or warnings.

Also, after enabling debug mode, the error.log states that whatever request I'm trying, it is granted; no errors or warnings here.

Anyone an idea where to continue looking for this?
I have run out of options here - just don't know where to look and what to look for.


Thanks - Will

---

### Post by howefield on 2016-08-06
Thread moved to the "*Server Platforms*" forum.

---

### Post by Vegan on 2016-08-06
I use wordpress and backup my work daily, not sure why but updates break everything in sight

---

### Post by Graham_Willis on 2016-08-08
@Will_Moonen: check access log of Apache and tell us what the response code of PHP pages is. You're saying that there're neither errors nor warnings in PHP error log - should it be understood that it's just empty (since upgrade)? Have you checked if after you open a PHP-based page a PHP process starts at all? Have you tried to manually run the PHP interpreter that is invoked by Apache on a one-liner script and check if it returns any output and if this output is as desired? Have you tried phpinfo script?

---


---
title: "Zend Optimizer Problem - not decoding files"
date: 2008-09-11
forum: Server Platforms
---

### Post by four2theizz0 on 2008-09-11
Hello,

I have a little problem with Zend Optimizer.  I will start off by saying I am running Hardy 64 bit and am runnign Xen, and this problem is on one of the instances, if that matters
I also have a dreamhost account that does everything perfectly and want to know what they have that I do not. 

Basically I am installing some software that is Zend encoded.  I am able to run this fine on the dreamhost server.  There are a couple cron jobs that run some php scripts that are encoded.  I noticed they werent running on my server and tried to run them manually...ie php -q cron.php
And it just outputs the garbled code that is in the file and that is it. 

Also, Here is the excerpt from my phpinfo()

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies
    with Zend Extension Manager v1.2.2, Copyright (c) 2003-2007, by Zend Technologies
    with Zend Optimizer v3.3.3, Copyright (c) 1998-2007, by Zend Technologies

Oddly enough, here is the output of php -v
PHP 5.2.6 (cli) (built: Sep 11 2008 17:23:39)
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies


notice it doesnt say optimizer, if that is a problem
Anywho, I have also custom compiled php with Thread-Safety disabled as suggested by others.

I really hope it is just something stupid that I have overlooked, any help would be appreciated and let me know if you need anymore info.

Thanks!

---


---
title: "RABBIT / Apache start error - undefined symbol: amqp_error_string2"
date: 2014-06-25
forum: Server Platforms
---

### Post by rob67 on 2014-06-25
Hi

I am running Ubuntu 14.04 and am trying to install Rabbit AMQP.

Upon restart of apache service, the error log reports:

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/amqp.so' - /usr/lib/php5/20121212/amqp.so: undefined symbol: amqp_error_string2 in Unknown on line 0
```

And the Rabbit lib doesn't work.

On a restart of apache, it repeats this exact line 3 times in error log.

I am at a loss where to even start debugging. Any pointers, most appreciated, and just shout if you need any more info / other results.

Thanks

More info:

[TABLE]
[TR]
[TD="class: votecell"]          
              
[/TD]
              [TD="class: postcell"]                  I followed this: [https://github.com/pdezwart/php-amqp/issues/87](https://github.com/pdezwart/php-amqp/issues/87)
  And...
  locate librabbitmq.so
  returns:
  /usr/lib/librabbitmq.so.0
/usr/lib/librabbitmq.so.0.0.0
  ls -al librabb* returns:
  /usr/lib/librabbitmq.so.0 -> librabbitmq.so.0.0.0  (root / root)
librabbitmq.so.0.0.0 (root / root)
  In /user/local/lib there is also:
  librabbitmq.so -> /usr/lib/librabbitmq.so.0 (root / root)
  Permissions are root/root and 755 on all.
  Any help, most appreciated.


[/TD]
[/TR]
[/TABLE]

---

### Post by lisati on 2014-06-25
*Thread moved to **Server Platforms**.*

---


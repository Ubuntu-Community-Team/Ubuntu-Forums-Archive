---
title: "apache2 undefined symbol"
date: 2009-10-30
forum: Server Platforms
---

### Post by Shark4126 on 2009-10-30
I've just upgraded from 9.04 to 9.10 Desktop. Everything went smoothly, but now Apache2 won't start. I use Apache on this desktop for web dev. After an /etc/init.d/apache2 start, I get:

 /usr/sbin/apache2: symbol lookup error: /usr/sbin/apache2: undefined symbol: apr_atomic_xchgptr

I've reinstalled libapr1, libapr1-dbg, libaprutil1, libaprutil1-dbg, libaprutil1-ldap, libapreq2, and libaprtuil1-dbd-mysql (ldap and mysql libs just for fun) but to no avail. What am I missing?

---

### Post by Shark4126 on 2009-10-30
Well, after the panic faded, running ldd found an issue with novell conferencing (which I had installed for work, but regretted ever since). After removing that, problem solved. Please disregard.

---

### Post by patobasalo on 2010-05-12
> **Shark4126 said:**
> Well, after the panic faded, running ldd found an issue with novell conferencing (which I had installed for work, but regretted ever since). After removing that, problem solved. Please disregard.

How did you resolve it??
Can you explain it, please...

Thanks

---

### Post by raelga on 2010-12-17
Hi!

I fix it removing manually the old libraries that I have on /usr/local/lib and apache2 remains using that ones:

```
root@posido:/home/rgarcia# cp -up /usr/local/lib/libapr* libapr/
root@posido:/home/rgarcia# rm -i /usr/local/lib/libapr*
rm: remove regular file `/usr/local/lib/libapr-1.a'? y
rm: remove regular file `/usr/local/lib/libapr-1.la'? y
rm: remove symbolic link `/usr/local/lib/libapr-1.so'? y
rm: remove symbolic link `/usr/local/lib/libapr-1.so.0'? y
rm: remove regular file `/usr/local/lib/libapr-1.so.0.2.12'? y
rm: remove regular file `/usr/local/lib/libaprutil-1.a'? y
rm: remove regular file `/usr/local/lib/libaprutil-1.la'? y
rm: remove symbolic link `/usr/local/lib/libaprutil-1.so'? y
rm: remove symbolic link `/usr/local/lib/libaprutil-1.so.0'? y
rm: remove regular file `/usr/local/lib/libaprutil-1.so.0.2.12'? y
```

and then reinstall the last version using the aptitude:

```
root@posido:/home/rgarcia# aptitude install libaprutil1 libaprutil1-dev libapr1 libapr1-dev
```

and **It works!** :D

```
root@posido:/home/rgarcia# /etc/init.d/apache2 start
 * Starting web server apache2                                                               [ OK ]
```


If it doesn't work, check that you are using the correct apr libraries with ldd

```
root@posido:/home/rgarcia# ldd /usr/sbin/apache2
	linux-vdso.so.1 =>  (0x00007fffe4123000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007f3a303b2000)
	libaprutil-1.so.0 => **/usr/lib/libaprutil-1.so.0 **(0x00007f3a3018f000)
	libapr-1.so.0 => **/usr/lib/libapr-1.so.0 **(0x00007f3a2ff59000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f3a2fd3c000)
	libc.so.6 => /lib/libc.so.6 (0x00007f3a2f9b9000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00007f3a2f7b3000)
	librt.so.1 => /lib/librt.so.1 (0x00007f3a2f5ab000)
	libcrypt.so.1 => /lib/libcrypt.so.1 (0x00007f3a2f372000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f3a2f16d000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00007f3a2ef44000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f3a3087d000)
```



I hope it helps.

---


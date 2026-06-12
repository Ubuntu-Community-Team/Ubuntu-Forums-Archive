---
title: "Snort fatal error during restart"
date: 2009-07-16
forum: Security
---

### Post by ihai on 2009-07-16
Hi guys;

Ive just installed and configured snort from [http://ubuntuforums.org/showthread.php?p=5786356#post5786356](http://ubuntuforums.org/showthread.php?p=5786356#post5786356)

When Im trying to restart snort with ***/etc/init.d/snort restart*** ; I got the following error :

 [SIZE=2][COLOR=Red]command not found[/COLOR][/SIZE]

Besides when Im doing :

 ***/usr/local/bin/snort -c /etc/snort/snort.conf***

I got the follwing error message :

[SIZE=2][COLOR=Red]Loading dynamic detection library /usr/local/lib/snort_dynamicrules/bad-traffic.so... ERROR: Failed to load /usr/local/lib/snort_dynamicrules/bad-traffic.so: /usr/local/lib/snort_dynamicrules/bad-traffic.so: cannot open shared object file: No such file or directory[/COLOR][/SIZE]

????
What do Ineed to do; its the first time that Im installing Snort.

thx

---

### Post by bodhi.zazen on 2009-07-16
First, since you compiled snort from source you will not have an init script, thus /etc/init.d/snort does not exist.

Second, you mentioned re-starting snort, meaning snort is already running ?

---

### Post by ihai on 2009-07-19
The bug is the tutorial is only for snort 2.83 and Ive installed snort 3.0 ...

I need to install 2.83

---

### Post by The Tronyx on 2009-07-19
> **ihai said:**
> The bug is the tutorial is only for snort 2.83 and Ive installed snort 3.0 ...

I need to install 2.83

The bug looks to be due to the fact that you compiled snort from source which is not what the tutorial stickied in this section covers.  However, this is not to say that this isn't going to work.

The error you are seeing is indicating that the shared object the binary was compiled against cannot be found.  This is likely due to the fact that during compilation, something didn't necessarily go as planned.  If you find the shared object (.so) and see where it's looking for these objects, you can likely get this working.

If I had to guess, the shared objects built with snort are in the source directory, probably under libs?

Try the below.

```

ldd /usr/local/bin/snort

```
 This will print out a bunch of stuff.  Please paste that stuff here.

Additionally, please run sudo updatedb then 'locate bad-traffic | grep .so"

You can see that the program is failing at "/usr/local/lib/snort_dynamicrules/" and then looks for the .so file in /usr/local/lib/snort_dynamicrules/.  I am guessing the shared objects it wants are going alphabetically, bad-rules being first.  Once you fixed the bad-rules error, you will run into the next shared object it cannot locate.  Once you find the shared object file(s) in their original location, you could just try doing
```

mkdir /usr/local/lib/snort_dynamicrules/
cp /original/pathto/snort/shared/objects/*.so /usr/local/lib/snort_dynamicrules/

```

---

### Post by ikt on 2009-09-15
> **The Tronyx said:**
> The bug looks to be due to the fact that you compiled snort from source which is not what the tutorial stickied in this section covers.  However, this is not to say that this isn't going to work.

The error you are seeing is indicating that the shared object the binary was compiled against cannot be found.  This is likely due to the fact that during compilation, something didn't necessarily go as planned.  If you find the shared object (.so) and see where it's looking for these objects, you can likely get this working.

If I had to guess, the shared objects built with snort are in the source directory, probably under libs?

Try the below.

```

ldd /usr/local/bin/snort

```
 This will print out a bunch of stuff.  Please paste that stuff here.



	linux-gate.so.1 =>  (0xb7fd4000)
	libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb7dea000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7dd1000)
	libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d9e000)
	libz.so.1 => /lib/libz.so.1 (0xb7d88000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb7d56000)
	libpcap.so.0.8 => /usr/lib/libpcap.so.0.8 (0xb7d25000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7cff000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7ce6000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ce1000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b7e000)
	/lib/ld-linux.so.2 (0xb7fd5000)



> 
Additionally, please run sudo updatedb then 'locate bad-traffic | grep .so"

You can see that the program is failing at "/usr/local/lib/snort_dynamicrules/" and then looks for the .so file in /usr/local/lib/snort_dynamicrules/.  I am guessing the shared objects it wants are going alphabetically, bad-rules being first.  Once you fixed the bad-rules error, you will run into the next shared object it cannot locate.  Once you find the shared object file(s) in their original location, you could just try doing
```

mkdir /usr/local/lib/snort_dynamicrules/
cp /original/pathto/snort/shared/objects/*.so /usr/local/lib/snort_dynamicrules/

```


/usr/src/snort-2.8.4.1/so_rules/bad-traffic.rules
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-4.6/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-4.6/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-5.0/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-5.0/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-5.0/x86-64/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/CentOS-5.0/x86-64/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Debian-Lenny/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Debian-Lenny/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-5/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-5/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-9/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-9/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-9/x86-64/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FC-9/x86-64/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FreeBSD-6.3/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FreeBSD-6.3/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FreeBSD-7.0/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/FreeBSD-7.0/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/RHEL-5.0/x86-64/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/RHEL-5.0/x86-64/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Ubuntu-6.01.1/i386/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Ubuntu-6.01.1/i386/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Ubuntu-8.04/x86-64/2.8.4/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/precompiled/Ubuntu-8.04/x86-64/2.8.4.1/bad-traffic.so
/usr/src/snort-2.8.4.1/so_rules/src/bad-traffic_ddns-any-update.c
/usr/src/snort-2.8.4.1/so_rules/src/bad-traffic_libspf2-txt-record.c
/usr/src/snort-2.8.4.1/so_rules/src/bad-traffic_linux-icmp-handling-dos.c
/usr/src/snort-2.8.4.1/so_rules/src/bad-traffic_pgm-nak-overflow.c


which one to copy?

running 9.04 server.

---


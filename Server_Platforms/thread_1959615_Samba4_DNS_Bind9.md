---
title: "Samba4 DNS Bind9"
date: 2012-04-16
forum: Server Platforms
---

### Post by Jean8888 on 2012-04-16
I am running ubuntu server 11.10 64-bits

I have to do a mock test, Samba 4 alpha18 domain controller.

So I folow the WIKI HowTo: [http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO) (I'm at step 8 )

# apt-get install bind9

Add samba name.conf to bind9 configuration
# nano /etc/bind/named.conf.local

I must add the configuration file of samba dns, so the line:
include "/usr/local/samba/private/named.conf";    --(when adding this line that Bind9 will not start)

bind9 refuses to start because of Apparmor.
So to give permission:
nano /etc/apparmor.d/usr.sbin.named
Add :
## for samba4
/usr/local/samba/private/** rw,   
/usr/local/samba/private/dns/* rw,

#etc/init.d/apparmor reload
also
#apparmor_parser -r /etc/apparmor.d/usr.sbin.named

bind1.9.7 and bind1.9.9 don't start

Thanks

---

### Post by Jean8888 on 2012-04-16
There are errors in the log so I added theses path to
/etc/apparmor.d/usr.sbin.named:

/usr/local/samba/lib/bind9/** rwkix,
/var/run/bind/run/named/** rw,

But I got these errors in the logs (when I tried to start bind)

Apr 16 14:07:35 test-samba named[26897]: dlz_dlopen failed to open library '/usr/local/samba/lib/bind9/dlz_bind9.so' - /usr/local/samba/lib/bind9/dlz_bind9.so: failed to map segment from shared object: Permission denied

Apr 16 14:07:35 test-samba kernel: [268930.718987] type=1400 audit(1334578055.872:222): apparmor="DENIED" operation="file_mmap" parent=26896 profile="/usr/sbin/named" name="/usr/local/samba/lib/bind9/dlz_bind9.so" pid=26898 comm="named" requested_mask="m" denied_mask="m" fsuid=107 ouid=0

It seem that apparmor denied the access, don't know why.

---

### Post by Jean8888 on 2012-04-17
Finally I make Bind9 working I post the solution:

I got this error in syslog:
15:14:49 test-samba named[27586]: dlz_dlopen: incorrect version 1 should be 2 in '/usr/local/samba/lib/bind9/dlz_bind9.so'

This error come from the sources files.


# cd /usr/local/samba-4.0.0alpha18/
Change this in the source file dlz_minimal.h
# nano source4/dns_server/dlz_minimal.h
Change :
  define DLZ_DLOPEN_VERSION 1
for :
  define DLZ_DLOPEN_VERSION 2
And reinstall, 
# ./configure.developer --with-ldap |make |make install

---


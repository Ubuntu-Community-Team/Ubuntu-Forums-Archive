---
title: "proftpd problem"
date: 2011-10-29
forum: Server Platforms
---

### Post by daninin on 2011-10-29
hello, my proftpd gui cannot start the sharing access.
here is there error code:
>  - mod_tls/2.4.2: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
 - mod_sftp/0.9.7: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
 - mod_tls_memcache/0.1: notice: unable to register 'memcache' SSL session cache: Memcache support not enabled
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 68 of '/etc/proftpd/proftpd.conf'


I dont know what to do.. i checked and i cant get access to "gadmin-proftpd" to check. i tried throught the console but it didn't help. :confused:

---

### Post by vasile002 on 2011-10-29
the proftpd package you installed was compiled with another openssl package, you need to either upgrade your openssl package to the version your proftpd requires or recompile proftpd with your existing openssl package

as for the memcache error, you need to enable memcache support in proftpd

---

### Post by daninin on 2011-10-29
> **vasile002 said:**
> the proftpd package you installed was compiled with another openssl package, you need to either upgrade your openssl package to the version your proftpd requires or recompile proftpd with your existing openssl package

as for the memcache error, you need to enable memcache support in proftpd

Alright, got it a little but how do i do that? I just started to use this. and i want to create a social FTP with me and my friends(ports will be opened later)
if you can give me a tutorial on how to do that stuff. thanks, if not can you explane a little how to do that?

---

### Post by Lars Noodén on 2011-10-29
Are you sure you really want [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)?  It's a lot of work to set up and maintain and is insecure.  If you have SSH installed then you already have SFTP up and running.  It's secure and as easy to use and easier to maintain.  There are SFTP clients built into Nautilus, Dolphin and FileZilla and so on.

---

### Post by iansane on 2012-05-08
Could someone please tell the steps to enable memcache in proftpd?

I'm looking at the proftpd documentation and it tells how to compile but since this is a ubuntu package not compiled from source, how and where would one go about enabling memcache?

Thank you

---

### Post by bdbais on 2012-06-07
> **iansane said:**
> Could someone please tell the steps to enable memcache in proftpd?

I'm looking at the proftpd documentation and it tells how to compile but  since this is a ubuntu package not compiled from source, how and where  would one go about enabling memcache?

Thank you

I found this article about enabling memcache:

[http://www.proftpd.org/docs/contrib/mod_tls_memcache.html](http://www.proftpd.org/docs/contrib/mod_tls_memcache.html)

it said to setup your proftpd.conf withi these modifications:

```
  
<IfModule mod_memcache.c>     
      MemcacheEngine on    
      MemcacheServers <YOUR SERVERS WITH MEMCACHE ACTIVE>

# Example: MemcacheServers 1.2.3.4:11211 1.2.3.5:22422

 </IfModule>    

<IfModule mod_tls.c>    
 ...     
 <IfModule mod_tls_memcache.c>
       TLSSessionCache memcache:
     </IfModule>
   </IfModule>


```

but you must have proftpd with memcache compiled ( I suppose yes because your problem asking for enabling )

I'm trying this solution but question is, do you really need it?

on this doc: [http://www.proftpd.org/docs/RELEASE_NOTES-1.3.4rc3](http://www.proftpd.org/docs/RELEASE_NOTES-1.3.4rc3)  I found:
 mod_tls_memcache        The mod_tls_memcache module uses the new mod_memcache/memcached support       in ProFTPD to use memcached servers for caching SSL session information.       This can be useful, especially when clusters of proftpd servers are       in used, or for preserving SSL session caches across proftpd restarts.       See doc/contrib/mod_tls_memcache.html for more details on this module. 
So if you want to preserve session after a restart of your proftpd you can use this option.
:popcorn:

I removed this feature for la single proftpd service.

Online documentation I'm using is: [http://www.proftpd.org/docs/modules/mod_memcache.html](http://www.proftpd.org/docs/modules/mod_memcache.html)

bye

---

### Post by fare31key on 2012-07-05
Just uncomment the line contains

LoadModule mod_tls_memcache.c
->
## UNCOMMENT LoadModule mod_tls_memcache.c

in /etc/proftpd/modules.conf

---


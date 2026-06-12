---
title: "DNS (BIND) problems"
date: 2008-10-14
forum: Server Platforms
---

### Post by Vegan on 2008-10-14
I have a bunch of nameservers in the resolv.conf and when I use ping everything works fine.

when I use dig though I get a parse error. Thoughts?

---

### Post by koenn on 2008-10-15
post an example of your dig command

---

### Post by Vegan on 2008-10-19
user@ubuntu:~$ dig ubuntu.com
dig: parse of /etc/resolv.conf failed
igreen@ubuntu:~$

here is my resolv.conf

domain contract-developer.dyndns.biz
nameserver 0.0.0.0
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 204.11.126.131
nameserver 208.185.179.218

---

### Post by koenn on 2008-10-19
does it get better if you leave out nameserver 0.0.0.0 ?

---

### Post by Vegan on 2008-11-13
Unfortunately it failed to help, any other ideas?

---

### Post by MJN on 2008-11-13
Try recreating resolv.conf from scratch. Completely new file, manually created.
 
I'm thinking there might be a weird control character in there. Also ensure there's a new line at the end of the file - some files can get picky at this (hosts file being the classic favourite).
 
Mathew

---

### Post by koenn on 2008-11-13
can't see anything wrong with the resolv.conf you posted ...

---

### Post by Vegan on 2008-11-13
Found a few NL in the file, snipped them out. Removed the blank line too.

dig still complained.

Wonder if BIND needs some work.

---

### Post by inphektion on 2008-11-13
if you add
search contract-developer.dyndns.biz
does it help?

---

### Post by Vegan on 2008-11-13
still getting a stupid parse error. Go figgure?

domain contract-developer.dyndns.biz
search contract-developer.dyndns.biz
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 204.11.126.131
nameserver 208.185.179.218

---

### Post by MJN on 2008-11-14
> **Vegan said:**
> Found a few NL in the file, snipped them out. Removed the blank line too.I said recreate the file _from scratch_.
 
Delete the one you've got (back it up if you prefer) then create a brand new file with just the line **nameserver 64.59.160.13** and see if that is any different.
 
Sure, it might not help but in the absence of any other ideas it's surely got to be worth a shot.
 
Mathew

---

### Post by koenn on 2008-11-14
> **MJN said:**
> I said recreate the file _from scratch_.
 
Delete the one you've got (back it up if you prefer) then create a brand new file with just the line **nameserver 64.59.160.13** and see if that is any different.
 
Sure, it might not help but in the absence of any other ideas it's surely got to be worth a shot.
 
Mathew
I agree.
As there is nothing visibly wrong with the file, yet dig complains it cant parse (i.e. read it and interpret the content) it, it's not unlikely there's some invisible (control-, non-printable-) character getting in the way, or some other sort of corruption. Starting from scratch with just a few lines is a good idea : either it solves the issue, or it will exclude a probable cause and thus help to diagnose further.

> **Vegan said:**
> 
Wonder if BIND needs some work.
Bind doesn't read from /etc/resolve.conf, and the error you get is not coming from bind. I'd say don't touch bind just yet.

---

### Post by bab1 on 2008-11-14
Careful consideration of: ```
man resolv.conf
``` reveals > **The  resolver is a set of routines in the C library **that provide access
       to the Internet Domain Name System (DNS).  The  resolver  configuration
       file  contains  information  that  is read by the resolver routines the
       first time they are invoked by a process.

as far as the parse error, the following might be relevant:> The different configuration options are:

       **[COLOR="Red"]nameserver[/COLOR]** -- Name server IP address
              Internet  address  (in  dot  notation) of a name server that the
              resolver  should  query.   Up  to  MAXNS   (currently   3,   see
              <resolv.h>)  name  servers  may  be listed, one per keyword. 

---

### Post by Vegan on 2008-11-21
I am going to try minimizing the search to my local DNS hosts, and see if that works better. BIND has the root tables if needed.

:guitar:

---

### Post by JDiss on 2008-11-22
> **Vegan said:**
> I am going to try minimizing the search to my local DNS hosts, and see if that works better. BIND has the root tables if needed.


Unless resolv.conf is pointed to your BIND server, you're just throwing electrons at something that isn't doing anything.

The nameservers in resolve.conf will be queried, meaning that you're hitting their [BIND|*] servers.  As one poster has pointed out, usually more than 3 nameserver entries is useless.

Personally my own resolve.conf has
nameserver 127.0.0.1 - for bind locally.
nameserver 192.168.0.1 - gateway for my router to do upstream requests.

My local BIND has a bunch of references to my local domains for development purposes, or punts the request.

---


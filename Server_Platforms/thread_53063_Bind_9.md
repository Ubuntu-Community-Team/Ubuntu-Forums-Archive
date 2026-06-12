---
title: "Bind 9"
date: 2005-07-30
forum: Server Platforms
---

### Post by soon82 on 2005-07-30
I had running samba server on my existing ubuntu....

Now i would like to add another services, which is DNS server....

I had install the bind 9... but i don't know how to configure it.. as well.. 

So I need yours help...

---

### Post by LordHunter317 on 2005-07-30
[QUOTE=soon82]I had running samba server on my existing ubuntu....

Now i would like to add another services, which is DNS server....

I had install the bind 9... but i don't know how to configure it.. as well.. 

So I need yours help...[/QUOTE]
 Read the DNS-HOWTO.

---

### Post by h4rdwire on 2005-08-02
[QUOTE=soon82]I had running samba server on my existing ubuntu....

Now i would like to add another services, which is DNS server....

I had install the bind 9... but i don't know how to configure it.. as well.. 

So I need yours help...[/QUOTE]

what he said .. RTFM it should be pretty much the same, i'm used to RH but i'm betting theres still the same named.conf and a need for the forward and reverse lookup files

---

### Post by tonym on 2005-08-08
Have a look at webmin. It has a reasonably nice GUI for managing BIND.

---

### Post by soon82 on 2005-08-19
[QUOTE=h4rdwire]what he said .. RTFM it should be pretty much the same, i'm used to RH but i'm betting theres still the same named.conf and a need for the forward and reverse lookup files[/QUOTE]


Excuse me, Can you send me your bind configuration files for me do some reference..

I had try to looking at DNS HOWTO... may be i misunderstood...about the configuration.


Thank you...

---

### Post by Velox Letum on 2005-08-20
Which part exactly are you having trouble with? The config? I'll scare up a named.conf.

---

### Post by LordHunter317 on 2005-08-21
I'm goign to be blunt, because this is how critical DNS is.

If you cannot understand the DNS howto or properly ask questions about what you don't understand, you shouldn't be running DNS.  At all.

---


---
title: "OpenVPN Access Server 64bit/32bit Amd/Intel"
date: 2009-04-14
forum: Server Platforms
---

### Post by primaxx on 2009-04-14
Hello,

I find OpenVPN quite tricky to configure, but today I saw that they have come up with a new product, namely [OpenVPN Access Server]("http://beta.openvpn.net/") (still in beta).

This is exactly what I need, but will it work?

I have Ubuntu 8.04 32bit on Intel-processors and OpenVPN only offer the software for amd64bit.

My first thougt is of course that this will not work, but am I wrong? Asked more general: Is it possible to run progams written for 64bit on 32bit computers?
Another thing: Is it so big difference between Amd 64bit and Intel 64bit that there have to be different versions of software?

Thank you for any answer! :)

Yet another thing, I don't have physical access to the machine I want to install OpenVPN on right now, and I don't remember if the processors are 32bit or 64bit (I believe they are 32bit)
-Can you tell, from the information given below, if my processors are 32bit or 64bit? (If they are 64bit, I consider to install the 64bit-version of Ubuntu...)

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU            2160  @ 1.80GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3602.31
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU            2160  @ 1.80GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3599.99
clflush size	: 64

```

---

### Post by MystaMax on 2009-04-30
I'm somewhat in the same boat as you. I'm also trying to figure out if this product works for me. There isn't much info on their site.

I know there are 32-bit packages that allow you to run 32-bit software on 64-bit architecture (I use to run 32-bit java in 64-bit). But, I don't think it works the other way around; at least I haven't seen it personally.

you can type:

```
 uname -a 
```

that'll tell you what you need to know. Here is mine:

```
  Linux fiasco 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux 
```

The **i686** lets you know that I'm running 32-bit. On Ubuntu 64-bit, you'll see:

```
 Linux fiasco 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 x86_64 GNU/Linux 
```

Hope that helps?

Did you end up finding anything else about openvpn?

---

### Post by lucanuscervus on 2009-05-13
Hi,

I found that they have packages for different architectures. I have downloaded a rpm for 64 bits and covert it to .deb using alien.
The server starts and I'm able to log through the web interface but now I'm facing a different problem:

```
process started and then immediately exited: ['Wed May 13 20:56:21 2009 failed to find GID for group nobody']
service failed to start or returned error status
``` 

I have looked for logs in /var/log but I couldn't find anything. Also, I'm unable to find out where the openvpn.conf is placed

---

### Post by acain on 2009-05-16
Good to hear of your interest in OpenVPN Access Server.

The "failed to find GID for group nobody" issue was resolved in
the second beta release, published on Friday (yesterday).  So I would
encourage you to give that version a whirl.  You can download it
from the same place:
   [http://beta.openvpn.net/index.php/access-server/download-openvpn-as.html](http://beta.openvpn.net/index.php/access-server/download-openvpn-as.html)

As far as the 32/64-bit question.... the current release
is only for 64-bit platforms, though there should be 32-bit versions
also released in the near future.  And though there is an "amd" in
the package name, it should work on both Intel and AMD platforms
(running a 64-bit OS).

   Adam Cain
   OpenVPN Technologies, Inc.

---

### Post by stephandej on 2009-05-29
Hello adam,

I am also looking at your access server as an alternative to configure vpn connection to home. When I quickly scan to scan through the package list it seems you mainly setup your own python tree. Why are you not depending on the existing packages for this? Are there actually architecture specific components to your installation (as opposed to only python scripts) other than python and some libaries? Wouldn't depending on existing packages not make it possible to create a architecture independent package?

Another question as I am planning this to use to connect to home from worklan, which is behind http proxy. I am interested on the deployed client. Is this using the openvpn gui for windows? I wonder if I can easily change proxy servers, in using the client pc in several locations?

thanks and keep up the good work.
stephan

---


---
title: "OpenVPN: Assertion failed at crypto.c:168"
date: 2008-06-30
forum: Server Platforms
---

### Post by NiRuWU on 2008-06-30
I´ve a problem using OpenVPN with your Webmin Module.

Server configuration:
Ubunto 8.04
Webmin 1.420
OpenVPN version 2.0_rc16
OpenSSL version 0.9.7e

Client configuration:
Windows Vista SP1
OpenVPN 2.1_rc7
OpenVPN GUI v1.0.3


First of all I fixed the problem with the VPN vreating script:
I removed the "-W" from create_vpn.cgi to get the WebminModule vreating new vpn servers.
After that I set up the CA, client and cerver certificates, the VPN-Server

Now I get the following server error while connecting (the error apears at all encrypting options):
Mon Jun 30 9:45:35 2008 xxx.xxx.xxx.xxx:40033 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Jun 30 9:45:35 2008 xxx.xxx.xxx.xxx:40033 [host1] Peer Connection Initiated with xxx.xxx.xxx.xxx:40033
Mon Jun 30 9:45:46 2008 host1/xxx.xxx.xxx.xxx:40033 Assertion failed at crypto.c:168
Mon Jun 30 9:45:46 2008 host1/xxx.xxx.xxx.xxx:40033 Exiting

The client error:
Mon Jun 30 11:45:50 2008 us=46000 [0] ev=0x000000e8 rwflags=0x0001 arg=0x0045d658
Mon Jun 30 11:45:50 2008 us=46000 [1] ev=0x000003d8 rwflags=0x0001 arg=0x0045d650
Mon Jun 30 11:45:50 2008 us=46000 NOTE: --mute triggered...
Mon Jun 30 11:45:52 2008 us=406000 17 variation(s) on previous 20 message(s) suppressed by --mute
Mon Jun 30 11:45:52 2008 us=406000 Assertion failed at crypto.c:168
Mon Jun 30 11:45:52 2008 us=406000 Exiting
Mon Jun 30 11:45:52 2008 us=406000 Closing Win32 semaphore 'openvpn_netcmd'

I´ve googled this error without any solution, there is only one russian having the same problem.

Can anybody help me out of that problem?
What kind of error is it:
Client or Server?

Thanks in advance,
Nils

---

### Post by mvillarejo on 2008-10-19
Hi mate, I'm having the same problem I thought the problem was releated with my windows vista, but I already try with windows XP and same result...did you find out a solution for this?

Regards,
MV

---

### Post by NiRuWU on 2008-10-20
Hi MV,

try to change the cipher.
We are using
OpenVPN version 2.0_rc16, OpenSSL version 0.9.7e

... this is not the newest version of openvpn, so you can´t use the newest ciphers.

We solved the problem by using:
AES-256 CBC-256

I hope I was able to help you.

---

### Post by mvillarejo on 2008-10-20
hi, thanks for the quick response: 

version I've got is the same:

OpenVPN version 2.0_rc16, OpenSSL version 0.9.7e

I tried with the same cypher you told me... but no luck.

do i need to renew the certs?

thanks

btw, here there is the end of the log when it finish.

Mon Oct 20 14:15:36 2008 us=250000 NOTE: --mute triggered...
Mon Oct 20 14:15:38 2008 us=625000 25 variation(s) on previous 20 message(s) suppressed by --mute
Mon Oct 20 14:15:38 2008 us=625000 Assertion failed at crypto.c:162
Mon Oct 20 14:15:38 2008 us=625000 Exiting
Mon Oct 20 14:15:38 2008 us=625000 Closing Win32 semaphore 'openvpn_netcmd'

---

### Post by mvillarejo on 2008-10-20
Hi mate! it works! using your algorithm and rexporting staff, it worked! :)

Thanks for your help.
MV

---

### Post by lolotux on 2009-02-18
Hi
Thank's for the hit !

Bye

---

### Post by BillyBob2 on 2010-09-10
Thank you guys, this works!

by the way I switched to AES-128-CBC 128 bit (fixed)
and it works as well :-)

---


---
title: "Error when using passwd."
date: 2009-11-20
forum: Server Platforms
---

### Post by mroski on 2009-11-20
HI, I've been receiving Authentication errors (POP3) when trying to download mail, I use dovecot.

Then I tried to login through SSH with the same user and the screen (putty) closed.

So I tried to change the user passwd and found the following error:
```
sudo passwd lorenagiudice
*** glibc detected *** passwd: free(): invalid pointer: 0x08b719d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x17aff1]
/lib/tls/i686/cmov/libc.so.6[0x17c6f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x17f79d]
/lib/security/pam_smbpass.so[0x52cd53]
/lib/security/pam_smbpass.so(pdb_getsampwnam+0x33)[0x50c6b3]
/lib/security/pam_smbpass.so(pam_sm_chauthtok+0x1ca)[0x48b44a]
/lib/libpam.so.0[0x97a3ad]
/lib/libpam.so.0(pam_chauthtok+0x113)[0x97e663]
passwd[0x804c0ad]
passwd[0x804b883]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126b56]
passwd[0x8049d51]
======= Memory map: ========
00110000-0024e000 r-xp 00000000 fc:00 262480     /lib/tls/i686/cmov/libc-2.10.1.so
0024e000-00250000 r--p 0013e000 fc:00 262480     /lib/tls/i686/cmov/libc-2.10.1.so
00250000-00251000 rw-p 00140000 fc:00 262480     /lib/tls/i686/cmov/libc-2.10.1.so
00251000-00254000 rw-p 00000000 00:00 0
00254000-00267000 r-xp 00000000 fc:00 262486     /lib/tls/i686/cmov/libnsl-2.10.1.so
00267000-00268000 r--p 00012000 fc:00 262486     /lib/tls/i686/cmov/libnsl-2.10.1.so
00268000-00269000 rw-p 00013000 fc:00 262486     /lib/tls/i686/cmov/libnsl-2.10.1.so
00269000-0026b000 rw-p 00000000 00:00 0
0026b000-0026c000 r-xp 00000000 fc:00 1048631    /lib/security/pam_deny.so
0026c000-0026d000 r--p 00000000 fc:00 1048631    /lib/security/pam_deny.so
0026d000-0026e000 rw-p 00001000 fc:00 1048631    /lib/security/pam_deny.so
0026e000-0027b000 r-xp 00000000 fc:00 132308     /usr/lib/liblber-2.4.so.2.5.1
0027b000-0027c000 r--p 0000c000 fc:00 132308     /usr/lib/liblber-2.4.so.2.5.1
0027c000-0027d000 rw-p 0000d000 fc:00 132308     /usr/lib/liblber-2.4.so.2.5.1
0027d000-00280000 r-xp 00000000 fc:00 429        /lib/libgpg-error.so.0.4.0
00280000-00281000 r--p 00002000 fc:00 429        /lib/libgpg-error.so.0.4.0
00281000-00282000 rw-p 00003000 fc:00 429        /lib/libgpg-error.so.0.4.0
00282000-00284000 r-xp 00000000 fc:00 917814     /usr/lib/gconv/IBM850.so
00284000-00285000 r--p 00001000 fc:00 917814     /usr/lib/gconv/IBM850.so
00285000-00286000 rw-p 00002000 fc:00 917814     /usr/lib/gconv/IBM850.so
00288000-00291000 r-xp 00000000 fc:00 262491     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00291000-00292000 r--p 00008000 fc:00 262491     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00292000-00293000 rw-p 00009000 fc:00 262491     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
00293000-002ab000 r-xp 00000000 fc:00 131909     /usr/lib/libsasl2.so.2.0.23
002ab000-002ac000 r--p 00017000 fc:00 131909     /usr/lib/libsasl2.so.2.0.23
002ac000-002ad000 rw-p 00018000 fc:00 131909     /usr/lib/libsasl2.so.2.0.23
002ad000-002c1000 r-xp 00000000 fc:00 340        /lib/libz.so.1.2.3.3
002c1000-002c2000 r--p 00013000 fc:00 340        /lib/libz.so.1.2.3.3
002c2000-002c3000 rw-p 00014000 fc:00 340        /lib/libz.so.1.2.3.3
002c3000-002df000 r-xp 00000000 fc:00 216        /lib/libgcc_s.so.1
002df000-002e0000 r--p 0001b000 fc:00 216        /lib/libgcc_s.so.1
002e0000-002e1000 rw-p 0001c000 fc:00 216        /lib/libgcc_s.so.1
0030f000-0032a000 r-xp 00000000 fc:00 351        /lib/ld-2.10.1.so
0032a000-0032b000 r--p 0001a000 fc:00 351        /lib/ld-2.10.1.so
0032b000-0032c000 rw-p 0001b000 fc:00 351        /lib/ld-2.10.1.so
0032c000-003cf000 r-xp 00000000 fc:00 132065     /usr/lib/libgnutls.so.26.14.10
003cf000-003d3000 r--p 000a2000 fc:00 132065     /usr/lib/libgnutls.so.26.14.10
003d3000-003d4000 rw-p 000a6000 fc:00 132065     /usr/lib/libgnutls.so.26.14.10
003dc000-003e5000 r-xp 00000000 fc:00 135765     /usr/lib/libtalloc.so.1.4.0
003e5000-003e6000 r--p 00008000 fc:00 135765     /usr/lib/libtalloc.so.1.4.0
003e6000-003e7000 rw-p 00009000 fc:00 135765     /usr/lib/libtalloc.so.1.4.0
0042b000-00434000 r-xp 00000000 fc:00 262482     /lib/tls/i686/cmov/libcrypt-2.10.1.so
00434000-00435000 r--p 00008000 fc:00 262482     /lib/tls/i686/cmov/libcrypt-2.10.1.so
00435000-00436000 rw-p 00009000 fc:00 262482     /lib/tls/i686/cmov/libcrypt-2.10.1.so
00436000-0045d000 rw-p 00000000 00:00 0
0045d000-005ce000 r-xp 00000000 fc:00 1049541    /lib/security/pam_smbpass.so
005ce000-005d1000 r--p 00171000 fc:00 1049541    /lib/security/pam_smbpass.so
005d1000-005d6000 rw-p 00174000 fc:00 1049541    /lib/security/pam_smbpass.so
005d6000-005d7000 rw-p 00000000 00:00 0
005ff000-00600000 r-xp 00000000 fc:00 1048764    /lib/security/pam_permit.so
00600000-00601000 r--p 00000000 fc:00 1048764    /lib/security/pam_permit.so
00601000-00602000 rw-p 00001000 fc:00 1048764    /lib/security/pam_permit.so
00602000-0067b000 r-xp 00000000 fc:00 427        /lib/libgcrypt.so.11.5.2
0067b000-0067c000 r--p 00078000 fc:00 427        /lib/libgcrypt.so.11.5.2
0067c000-0067e000 rw-p 00079000 fc:00 427        /lib/libgcrypt.so.11.5.2
00685000-0068b000 r-xp 00000000 fc:00 262487     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
0068b000-0068c000 r--p 00005000 fc:00 262487     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
0068c000-0068d000 rw-p 00006000 fc:00 262487     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
006cd000-006dd000 r-xp 00000000 fc:00 262495     /lib/tls/i686/cmov/libresolv-2.10.1.so
006dd000-006de000 r--p 00010000 fc:00 262495     /lib/tls/i686/cmov/libresolv-2.10.1.so
006de000-006df000 rw-p 00011000 fc:00 262495     /lib/tls/i686/cmov/libresolv-2.10.1.so
006df000-006e1000 rw-p 00000000 00:00 0
00754000-00769000 r-xp 00000000 fc:00 262494     /lib/tls/i686/cmov/libpthread-2.10.1.so
00769000-0076a000 r--p 00014000 fc:00 262494     /lib/tls/i686/cmov/libpthread-2.10.1.so
0076a000-0076b000 rw-p 00015000 fc:00 262494     /lib/tls/i686/cmov/libpthread-2.10.1.so
0076b000-0076d000 rw-p 00000000 00:00 0
00798000-007b1000 r-xp 00000000 fc:00 219        /lib/libselinux.so.1
007b1000-007b2000 r--p 00018000 fc:00 219        /lib/libselinux.so.1
007b2000-007b3000 rw-p 00019000 fc:00 219        /lib/libselinux.so.1
0087a000-0088a000 r-xp 00000000 fc:00 132349     /usr/lib/libtasn1.so.3.1.5
0088a000-0088b000 r--p 0000f000 fc:00 132349     /usr/lib/libtasn1.so.3.1.5
0088b000-0088c000 rw-p 00010000 fc:00 132349     /usr/lib/libtasn1.so.3.1.5
00978000-00983000 r-xp 00000000 fc:00 230        /lib/libpam.so.0.82.1
00983000-00984000 r--p 0000a000 fc:00 230        /lib/libpam.so.0.82.1
00984000-00985000 rw-p 0000b000 fc:00 230        /lib/libpam.so.0.82.1
009bd000-009bf000 r-xp 00000000 fc:00 262483     /lib/tls/i686/cmov/libdl-2.10.1.so
009bf000-009c0000 r--p 00001000 fc:00 262483     /lib/tls/i686/cmov/libdl-2.10.1.so
009c0000-009c1000 rw-p 00002000 fc:00 262483     /lib/tls/i686/cmov/libdl-2.10.1.so
00acb000-00acd000 r-xp 00000000 fc:00 231        /lib/libpam_misc.so.0.82.0
00acd000-00ace000 r--p 00001000 fc:00 231        /lib/libpam_misc.so.0.82.0
00ace000-00acf000 rw-p 00002000 fc:00 231        /lib/libpam_misc.so.0.82.0Cancelado

```



I have tried to userdel the user and then create it again with no success, server was restarted and I have tried other various things but still with the same problem.




Any ideas?
Thanks !

---

### Post by mroski on 2009-11-21
Where could I get some help?

---

### Post by mroski on 2009-11-22
Anyone can help me?

---

### Post by mroski on 2009-11-23
Hi

---

### Post by Denbert on 2009-11-23
> **mroski said:**
> HI, I've been receiving Authentication errors (POP3) when trying to download mail, I use dovecot.

Then I tried to login through SSH with the same user and the screen (putty) closed.



Try telnet to check credentials:

```
telnet pop.example.com pop3
```

---

### Post by mroski on 2009-11-23
HI,


Thank you very much for answering.
When I do that Dovecot responds "OK Dovecot ready".

Please note that I have almost 15 other users that have everything working OK and If I try to do passwd with any of those I can get to change their password.

Isn't this really weird?
The user doesn't even have access to commands on the server, it is just an email adress.

---

### Post by Denbert on 2009-11-24
> **mroski said:**
> 
The user doesn't even have access to commands on the server, it is just an email adress.

Like an Alias?

---

### Post by mroski on 2009-11-25
HI Denbert,

It's actually a user, I created it by doing "useradd myuser" but what I tried to mean is that the account is just used for email in a remote computer using Mozilla Thunderbird.
The user is a non-experienced user and I can assure this problem wasn't generated by that person.

---

### Post by Denbert on 2009-11-25
> **mroski said:**
> HI Denbert,

It's actually a user, I created it by doing "useradd myuser" but what I tried to mean is that the account is just used for email in a remote computer using Mozilla Thunderbird..

Ok

Try to make a new test user, read this new users mail via thunderbird - Try IMAP protocol.

Then try to change this new users passwd and see if it still works in thunderbird!

---

### Post by mroski on 2009-11-26
I've already tried that and it works fine and couldn't find any issues.

---

### Post by mroski on 2009-11-27
Any other ideas?

Thanks!

---

### Post by mroski on 2009-11-28
.

---

### Post by Denbert on 2009-11-29
> **mroski said:**
> .
Which Linux Distro are you working on?

Please send the output from this command:
```
# uname -a
```

---

### Post by mroski on 2009-11-29
Ubuntu Server 9.

uname -a response:
> Linux ASEOPLUS-SRV3 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux



I really appreciate yout help, this is giving me a really hard time.

---

### Post by Denbert on 2009-11-29
> **mroski said:**
> 
I really appreciate yout help, this is giving me a really hard time.

Please clear out something for me.

When you deleted the user, did you remove the users home dir?

```
userdel -r user
```

You have accepted to delete the user, therefore the users mail must haven been downloaded via pop.

You can create a new working user. Why don't you just give the original user a new username, eg. user2. and setup his Thunderbird for this new account?

I'm not familiar with dovecot, but I'm willing to learn \\:D/

---

### Post by mroski on 2009-11-29
I tried to remove the user's home folder but the mail folders weren't deleted because they weren't owned by the user. Then I deleted them manually.

Why I haven't created a new user, just because I thought this could be solved somehow.

About dovecot, I'm not an expert too, I installed this server using manuals from Internet and it was fun and a good learning opportunity.



So you think this can not be solved?

---


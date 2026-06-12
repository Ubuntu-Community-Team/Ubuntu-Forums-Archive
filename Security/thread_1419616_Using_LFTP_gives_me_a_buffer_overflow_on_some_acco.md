---
title: "Using LFTP gives me a buffer overflow on some accounts"
date: 2010-03-02
forum: Security
---

### Post by mokachoka on 2010-03-02
I have a number of accounts i connect to on my FTP server using LFTP. When i try and connect to **one** of my clients and issue an LS command it comes back with this below....
 
*** buffer overflow detected ***: lftp terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7fbc07ba12c7]
/lib/libc.so.6[0x7fbc07b9f170]
/lib/libc.so.6[0x7fbc07b9e519]
/lib/libc.so.6(_IO_default_xsputn+0x96)[0x7fbc07b18426]
/lib/libc.so.6(_IO_vfprintf+0x152b)[0x7fbc07ae8ecb]
/lib/libc.so.6(__vsprintf_chk+0x99)[0x7fbc07b9e5b9]
/lib/libc.so.6(__sprintf_chk+0x80)[0x7fbc07b9e500]
lftp[0x4419a7]
lftp[0x48eb4d]
lftp[0x48ee97]
lftp[0x48fbcd]
lftp[0x42f293]
lftp[0x40bb8d]
lftp[0x40851a]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fbc07ac05a6]
lftp[0x407ae9]
 
**(PLUS MORE)...**
 
It then disconnects me from the server. 
 
Using SFTP instead of LFTP allows me to make a connection but i need these connections to be scripted and automated so SFTP for me is not an option. Im also curious as to why LFTP is failing like this.
 
Does anyone know what the problem could be? I have been searching google for an answer but all i could find is you should update LFTP to the newest version which i have already done.

---

### Post by Bachstelze on 2010-03-02
Probably a bug in LFTP. Nothing you can do besides reporting it to the developers and waiting for a fix.

---

### Post by mokachoka on 2010-03-08
:( 
 
Can anyone confirm that this is infact a bug with LFTP? I cannot seem to find anything using google that confirms the buffer overflow issue is a bug.
 
The only other thing i can think of is that i have installed lftp incorrectly? 
 
Am i right in thinking installing LFTP using apt-get will install it with all the correct libraries that allow it to connect to sftp and ftps servers?

---

### Post by gmargo on 2010-03-08
What is the software running on the server?

---

### Post by mokachoka on 2010-03-12
Im now using psftp, works fine :P;):D

---


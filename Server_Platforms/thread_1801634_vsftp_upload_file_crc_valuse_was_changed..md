---
title: "vsftp upload file crc valuse was changed."
date: 2011-07-10
forum: Server Platforms
---

### Post by hyuk48 on 2011-07-10
hi guys~
 
I have some problem with vsftpd.
 
When I upload some files from "ubuntu client" to "red hat server" througt vsftpd,
 
Bytes are same, but **somtimes** the **CRC values** of "orig files and uploaded files" was 
 
changed. 
 
also the contents of files was changed.
 
This problem does not happen all the time.
 
When I checked hex values of two files,  there were some replaced values.
 
-----------------------------------------------------------------------------------------------
diff orin_hex_test uploaded_hex_test 
 
1c1
< 0x00000000: 31 32 33 34 2c 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 1234,1,1,1,1,1,1
---
> 0x00000000: [COLOR=red]0a[/COLOR] 32 33 34 2c 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 .234,1,1,1,1,1,1

92c92
< 0x000005b0: 31 32 33 34 2c 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 1234,1,1,1,1,1,1
---
> 0x000005b0: 31 32 33 34 [COLOR=red]0a[/COLOR] 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 1234.1,1,1,1,1,1

183c183
< 0x00000b60: 31 2c 31 2c 31 2c 31 2c - 31 2c 31 2c 31 2c 31 2c 1,1,1,1,1,1,1,1,
---
> 0x00000b60: 31 2c 31 2c 31 2c 31 2c - [COLOR=red]0a[/COLOR] 2c 31 2c 31 2c 31 2c 1,1,1,1,.,1,1,1,

274c274
< 0x00001110: 2c 31 2c 31 2c 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 ,1,1,1,1,1,1,1,1
---
> 0x00001110: 2c 31 2c 31 2c 31 2c 31 - 2c 31 2c 31 [COLOR=red]0a[/COLOR] 31 2c 31 ,1,1,1,1,1,1.1,1

366c366
< 0x000016d0: 31 2c 31 2c 31 2c 31 0a - 0a 31 32 33 34 2c 31 2c 1,1,1,1..1234,1,
---
> 0x000016d0: [COLOR=red]0a[/COLOR] 2c 31 2c 31 2c 31 0a - 0a 31 32 33 34 2c 31 2c .,1,1,1..1234,1,

457c457
< 0x00001c80: 31 32 33 34 2c 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 1234,1,1,1,1,1,1
---
> 0x00001c80: 31 32 33 34 [COLOR=red]0a[/COLOR] 31 2c 31 - 2c 31 2c 31 2c 31 2c 31 1234.1,1,1,1,1,1

--------------------------------------------------------------------------------------------------
And when I test on same platfrom ( upload file from ubuntu clinet to ubuntu server or 
 
redhat clinet to redhat server), it looks good. there was no problem. so I think the 
 
configration was good. ( also I did test binary and ascii mode)
 
 
what is the problem? pleas help me~
 
thanks for reading.:)

---


---
title: "Youtube's 'highly trained monkey' attack."
date: 2016-06-22
forum: Security
---

### Post by ventrical on 2016-06-22
Anybody else seeing this. I got it thismorning when I tried to open a new youtube tab.

---

### Post by Habitual on 2016-06-22
Custom 500 page. I've seen it, not today.

---

### Post by ventrical on 2016-06-22
Thanks for reply. I think it is some kind of javascript spam.

Regards..

---

### Post by Habitual on 2016-06-22
> **ventrical said:**
> Thanks for reply. I think it is some kind of javascript spam.

Regards..

**It is not spam**. and it's not javascript. It is a custom 500 error message that they wrote.
No conspiracy. No tinfoil hat needed.
[https://httpd.apache.org/docs/2.2/custom-error.html](https://httpd.apache.org/docs/2.2/custom-error.html)

Try decaf.

---

### Post by ventrical on 2016-06-22
> **Habitual said:**
> **It is not spam**. and it's not javascript. It is a custom 500 error message that they wrote.
No conspiracy. No tinfoil hat needed.
[https://httpd.apache.org/docs/2.2/custom-error.html](https://httpd.apache.org/docs/2.2/custom-error.html)

Try decaf.

I don't drink coffee.

... and there was a script that directed to that page.

..soooo script plus custom page equals spam..

They ? ;)

regards...

---

### Post by c0n7r4 on 2016-06-22
it looks like base64 encoded data. Malware can be obfuscated using base64 to hide what its really doing. Screenshots **should** will not be able to launch . I just decoded a little bit of the beginning of the  data; this is what it contains 
```
 00000000  FC                cld
00000001  58                pop eax
00000002  43                inc ebx
00000003  BC64968BB7        mov esp,0xb78b9664
00000008  AD                lodsd
00000009  B37F              mov bl,0x7f
0000000B  B973488E3B        mov ecx,0x3b8e4873
00000010  25FC833482        and eax,0x823483fc

``` this very much smells of executable code. They want you to email google malware, if im not mistaken.

---

### Post by ventrical on 2016-06-22
It came right up after I opened a tab and clicked youtube on my bookmarks list. My malware guard has been off the past few months. Fixed that today. There is not too much in the way of Linux malware realtime guards. AVG worked ok but COMODO works better. I used to work  behind the scenes for EMSIsoft and betatest their behavioural program, Mamutu. It would be sort of nice to have something like that for ubuntu or linux.  It is rare that I get any malicious activity on an ubuntu install. This has to be a first.

Edit: Just in case nobody seen the screenshot .. this happened in fully updated firefox on Ubuntu Trusty 14.04.

regards..

---

### Post by Habitual on 2016-06-22
Even a broke watch is right twice-a-day.

Newbies are hilarious.

---

### Post by ventrical on 2016-06-22
> **c0n7r4 said:**
> this very much smells of executable code. They want you to email google malware, if im not mistaken.

Mea cupla.  I had allowed firefox and flashplugin updates sit for a while plus I have about 60 tabs open at any one time :)

regards..

---


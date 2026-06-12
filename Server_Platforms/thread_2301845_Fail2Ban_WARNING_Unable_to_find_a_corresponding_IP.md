---
title: "Fail2Ban WARNING Unable to find a corresponding IP address for ::1"
date: 2015-11-05
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-05
Hello

I really dont know what happens but fail2ban start to give this warnings

```
2015-11-05 21:52:27,034 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,036 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,038 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,040 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,042 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,044 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,045 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,050 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,053 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,077 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,079 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,080 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,081 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,082 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,084 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,086 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,087 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,090 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,095 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,139 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,141 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,142 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,144 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,145 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,147 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,171 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,260 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,274 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,289 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,303 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,304 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,305 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,306 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,307 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,325 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,326 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,327 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,328 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,329 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,416 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported
2015-11-05 21:52:27,431 fail2ban.filter : WARNING Unable to find a corresponding IP address for ::1: [Errno -9] Address family for hostname not supported

```

---

### Post by Habitual on 2015-11-05
"fail2ban does not support ipv6" says [https://www.howtoforge.com/community/threads/fail2ban-error.70848/](https://www.howtoforge.com/community/threads/fail2ban-error.70848/)

Until it does, it's a Warning, ignore it? Or disable ipv6?
I believe it is the localhost that fail2ban is running on.

---

### Post by rhandy2 on 2015-11-06
Many Thanks!!!

I broken my brain searching for that answer.

---

### Post by Habitual on 2015-11-06
Well, if you're happy, then I'm happy you're happy with that answer. ):P

you could possibly add
```
ignoreregex =  <HOST> .* "::1:"
``` to the filter causing the Warning.
Should say in /var/log/fail2ban.log.

My Regular Expression.fu blows, so this line may not be 100% correct.

---

### Post by rhandy2 on 2015-11-06
Thanks again.

I upgrade ubuntu server to 15.10 and fail2toban to 0.9.3-1. 
And warning disapear.

---

### Post by Habitual on 2015-11-06
Good stuff! Glad it worked out.

---


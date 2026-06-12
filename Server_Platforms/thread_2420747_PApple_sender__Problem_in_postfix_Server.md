---
title: "PApple sender  Problem in postfix Server"
date: 2019-06-10
forum: Server Platforms
---

### Post by secooonder on 2019-06-10
[COLOR=#000000][FONT=arial]Hello
i  installed have postfix[/FONT][/COLOR][COLOR=#000000][FONT=arial], Dovecot and mysql setup my server on Ubuntu Server 16.04  two year ago.But  apple client can not send to mail.

Postfix Log is ;
[/FONT][/COLOR]```
Jun 10 10:47:49 mail postfix/cleanup[14687]: 75A11741672: reject: header Content-Type:** image/gif;??**name=blocked.gif;??[COLOR=#ff0000]x-apple-part-url[/COLOR]="15591970625cef75860c75e494621810@example.com" from unknown[1.1.1.1]; from=<bob@example.com> to=<tony@example.com> proto=ESMTP helo=<[192.168.1.10]>: 5.7.1 message content rejected
Jun 10 10:47:49 mail postfix/cleanup[14687]: 75A11741672: reject: header Content-Type: **image/jpeg;??**name=image1.jpg;??[COLOR=#ff0000]x-apple-part-url[/COLOR]="15591970625cef75860c75e494621810@example.com" from unknown[2.2.2.2]; from=<terry@example.com> to=<kate@example.com> proto=ESMTP helo=<[192.168.1.11]>: 5.7.1 message content rejected
Jun 10 10:47:49 mail postfix/cleanup[14687]: 75A11741672: reject: header Content-Type: **image/png;??**name=graphics1;??[COLOR=#ff0000]x-apple-part-url[/COLOR]="15591970625cef75860c75e494621810@example.com" from unknown[3.3.3.3]; from=<terry@example.com> to=<def@example.com> proto=ESMTP helo=<[192.168.1.12]>: 5.7.1 message content rejected

```[COLOR=#000000][FONT=arial]

[/FONT][/COLOR]i only gave 3 examples.But  i took an same error  "x-apple-part-url".

mime_header_checks conf is ;
root@mail:/etc/postfix# more mime_header_checks

> /name=[^>]*\.(bat|com|docm|exe|jar|rar|7z|gzip|tar|dll|vbs|zip|scr|xlt|reg|ps|cmd|bin|pif|src|mov|avi|mpg|r00|mpeg|ogg|mpe|qt|wma|wmv|rm|mp4)/ REJECT


No gif,no jpeg and no png ?

header_checks conf is ;
root@mail:/etc/postfix# more header_checks
> 
/^Received:                      /                IGNORE
/^User-Agent:                  /             IGNORE
/^X-Mailer:                      /                 IGNORE
/^X-Originating-IP:           /      IGNORE
/^x-cr-[a-z]*:                  /             IGNORE
/^Thread-Index:              /         IGNORE




[FONT=arial]i took an error at apple senders.
Can you help Me ?
Thank you very much for your help[/FONT]

---


---
title: "acl REDIRECT but in black list mode"
date: 2014-01-17
forum: Security
---

### Post by urbain2 on 2014-01-17
Hi. I use SQUID as a proxy, and here is the way I have set <[FONT=book antiqua]squid.conf[/FONT]> to establish URL redirection to [COLOR=#006400]web_server [/COLOR]for special [COLOR=#0000ff]processing :
[/COLOR]

[INDENT][FONT=trebuchet ms]acl _REDIRECT_ dstdomain "/home/urbain.egis/[COLOR=#ff0000]**redirec**[/COLOR]**t**[COLOR=#FF0000].txt[/COLOR]"[/FONT][/INDENT]
[INDENT][FONT=trebuchet ms]deny_info [http://[COLOR=#006400]web_server](http://[COLOR=#006400]web_server)[/COLOR]/[COLOR=#0000ff]processing[/COLOR]?website=%u all[/FONT][/INDENT]
[INDENT][FONT=trebuchet ms]http_reply_access deny _REDIRECT_ all[/FONT][/INDENT]

However, [COLOR=#FF0000]**redirec**[/COLOR][COLOR=#ff0000]**t**.txt [/COLOR]contains a WHITE LIST of URLs. I would like to manage a BLACK LIST approach: by default, where every URL would
be authorized to be _REDIRECT_ -ed (apart from a particular range of URLs included in [COLOR=#FF0000]**redirec**[/COLOR][COLOR=#FF0000]**t**.txt[/COLOR]). Thanks in advance.

---


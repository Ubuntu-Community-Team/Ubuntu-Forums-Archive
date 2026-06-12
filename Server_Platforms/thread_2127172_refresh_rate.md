---
title: "refresh rate"
date: 2013-03-19
forum: Server Platforms
---

### Post by kanjah on 2013-03-19
hi mates, am currently using squid3 3.1.20 64 bit on ubuntu server 12tty 64 bit, i have a problem with my refresh rate, which prevents squid3 to start, here's a sample code that am using

```
[COLOR=#000000][FONT=georgia]refresh_pattern -i \.(gif|png|jpg|jpeg|ico|bmp|tiff|webp|bif|gif\?|png\?|jpg\?|jpeg\?|ico\?|bmp\?|tiff\?|webp\?|bif\?)$ 36000 90% 100000 override-expire reload-into-ims ignore-reload[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern \.(swf|swf\?|js|js\?|wav|css|css\?|class|dat|zsci)$ 36000 90% 100000 override-expire reload-into-ims[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern -i \.(bin|deb|rpm|exe|zip|tar|tgz|ram|rar|bin|ppt|doc|docx|tiff|pdf|uxx|gz|xls|xlsx|psd|crl|msi|dll|dll\?|crx|enc|skl|arc)$ 36000 90% 100000 override-expire override-lastmod reload-into-ims ignore-reload[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern -i \.(xml)$ 0 90% 100000[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern -i \.(json|json\?)$ 1440 90% 5760 override-expire reload-into-ims[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern -i (/cgi-bin/|\?) 0 0% 0[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern ^ftp: 5440 90% 10080[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern ^gopher: 1440 0% 1440[/FONT][/COLOR]
[COLOR=#000000][FONT=georgia]refresh_pattern -i . 0 90% 5760[/FONT][/COLOR]
```

 any advice for me?

---


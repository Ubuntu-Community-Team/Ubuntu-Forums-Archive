---
title: "regex -i"
date: 2013-03-14
forum: Server Platforms
---

### Post by kanjah on 2013-03-14
[FONT=Arial, sans-serif][COLOR=#000000]hi mates, am currently running squid 3.1.20, 64 bit on hpz800 as  transparent. All is well except the server doesn't block any address that i have specified, here'z my sample code[/COLOR][/FONT]

[COLOR=#000000][FONT=Arial]acl bad_site url_regex -i torrentz torrents torrent[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]acl black_list dstdomain "/etc/squid3/list_dir.txt"[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]http_access deny bad_site[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]http_access denyblack_list[/FONT][/COLOR]

i have specified three web sites, being .redtube.com
                                                    .torrentz.eu
                                                    .thepiratebay.se 
running the tail -f /var/log/squid3/access.log, i see the three running. I have tried to change the file list_dir to black_list but to no avail, [COLOR=#000000][FONT=Arial]ave also used squidGuard, configured the sites in squidGuard.conf, but to no avail[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]any advice?[/FONT][/COLOR]

---

### Post by schragge on 2013-03-14
Missing space?
> **kanjah said:**
> http_access deny[highlight][COLOR=#ffd700]_[/COLOR][/highlight]black_list

---

### Post by kanjah on 2013-03-14
i have, that was a typo

---

### Post by schragge on 2013-03-14
Will it work if you write domain names directly instead of including them from file?
```
acl black_list dstdomain .redtube.com .torrentz.eu .thepiratebay.se
```

---

### Post by kanjah on 2013-03-14
i did, but it still displays the same.....it allows access

---


---
title: "Squid not blocking specific word in url"
date: 2021-08-29
forum: Server Platforms
---

### Post by kashifmax on 2021-08-29
[SIZE=3][FONT=-apple-system]I am using this acl in "squid.conf" to block the website containing the word "samsung".
[/FONT]
```
[FONT=-apple-system]acl denykey url_regex -i  /etc/squid/deny-keywords.squid
http_access deny denykey[/FONT]

```

[FONT=-apple-system]In file ```
deny-keywords.squid
samsung
```
[/FONT]
[FONT=-apple-system][https://www.samsung.com]("https://www.samsung.com/") is blocked[/FONT]
[FONT=-apple-system]but[/FONT]
[FONT=-apple-system][https://www.amazon.com/samsung/s?k=samsung](https://www.amazon.com/samsung/s?k=samsung) can be accessed and I think any site can be accessed after any domain.[/FONT]
[FONT=-apple-system]
What rule needs to be added to check whole url or to block the site containing the word "samsung"!
Note: Using proxy settings in browsers.[/FONT]
[FONT=-apple-system]Thanks[/FONT][/SIZE]

---


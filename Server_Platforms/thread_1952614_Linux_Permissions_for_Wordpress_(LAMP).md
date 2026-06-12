---
title: "Linux Permissions for Wordpress (LAMP)"
date: 2012-04-04
forum: Server Platforms
---

### Post by tts5 on 2012-04-04
[FONT=Arial][SIZE=3]I'm trying to configure a Linux server with secure permissions in /var/www. I've read that you shouldn't add your user account to the www-data group for various reasons. Instead, it's best (I'm told) to create a separate developer's group.[/SIZE][/FONT]
[SIZE=3] [/SIZE]
[FONT=Arial][SIZE=3]Here's what I came up with:[/SIZE][/FONT]
[SIZE=3] [/SIZE]
[FONT=Arial][SIZE=3]```
group add developers
```[/SIZE][/FONT]
[FONT=Arial][SIZE=3]```
usermod -a -G developers my_account
```[/SIZE][/FONT]
[FONT=Arial][SIZE=3]```
chown -R root:developers /var/www
```[/SIZE][/FONT]
[FONT=Arial][SIZE=3]```
find /var/www/ -type d -exec chmod 2775 {} \;
```[/SIZE][/FONT]
[FONT=Arial][SIZE=3]```
find /var/www/ -type f -exec chmod 664 {} \;
```[/SIZE][/FONT]
[SIZE=3] [/SIZE]
[FONT=Arial][SIZE=3]Finally, I'd set the default umask to:[/SIZE][/FONT]
[SIZE=3] [/SIZE]
[FONT=Arial][SIZE=3]```
umask 002
```[/SIZE][/FONT]
[SIZE=3] [/SIZE]
[FONT=Arial][SIZE=3]Questions:[/SIZE][/FONT]
[FONT=Arial][SIZE=3](a). Is this reasonably secure? (b). Is any of this redundant? (c). Does this setup require any change of the default umask? If so, to what?[/SIZE][/FONT]

---


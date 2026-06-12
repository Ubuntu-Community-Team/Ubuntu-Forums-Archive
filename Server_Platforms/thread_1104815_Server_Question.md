---
title: "Server Question"
date: 2009-03-24
forum: Server Platforms
---

### Post by id3379 on 2009-03-24
I just set up Ubuntu Server, not really that great with the terminal, but i was wondering if there's anything i can make my server do that show's it constantly scrolling through code, (for looks sake)

I had some ideas, maybe set it up as a web or FTP server and have the logs displayed to the screen in real-time.

I have no idea how i would do this though, maybe someone has a better idea?

Thanks.

---

### Post by id3379 on 2009-03-24
something like this [http://micrux.net/?p=66](http://micrux.net/?p=66)

except server doesn't have x

---

### Post by Anthon on 2009-03-24
(as root)
tail -f /var/log/messages > /dev/tty1

---

### Post by id3379 on 2009-03-24
Thanks, that works great !

---

### Post by BkkBonanza on 2009-03-24
Ya, also try: tcpdump
That will spew packet info continuously down the screen and look real tech-nerdy.

---


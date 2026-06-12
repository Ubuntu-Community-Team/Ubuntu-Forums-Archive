---
title: "irssi encoding"
date: 2021-09-10
forum: Server Platforms
---

### Post by hko2 on 2021-09-10
Hello,

My friend got his own IRC Server and it's set so users to have encoding ISO-89951 to connect, to the SSL Server.

I only get 'SSL Handshake error".. keep reading. 

I can connect to other ssl servers so it's not any openssl problem.

The problem is the encoding... i &#55358;&#56596; recall something to write &#55357;&#56541; in "screen irssi encoding ISO-89951' << Something!

Does anyone know or understand my problem? Whole server is ISO-89951.

Now we have reduce the issue to only:
" How to use screen irssi with another encoding"?
beacuse utf-8 is standard.

I've looked "screen --help". there's nothing.
In irssi I've "/set term_charset ISO-89951" so irssi isn't the problem.

Would really appreciate help here.. If you need anything from me just say it.

<snip>

---

### Post by coffeecat on 2021-09-10
Support, not chat.

*Thread moved to **Server Platforms**.*

@hko2:

[list=1][*]Please specify the operating system and release version running on the server.
[*]I've removed the last few lines from your post. This is a volunteer forum. Enticements are not needed and might cause offence with some members. [/list]

---

### Post by hko2 on 2021-09-10
> **coffeecat said:**
> Support, not chat.

*Thread moved to **Server Platforms**.*

@hko2:

Ok, now I saw the mail and a link &#128279; to this thread. 

Here you've my specs. 
Do you need anymore? Thats's no probs
_______________________________________________
xn@localhost:~$ uname -a
Linux localhost 4.19.113-perf-gaa66018ccb9c #1 SMP PREEMPT Fri Aug 20 00:19:22 CST 2021 aarch64 aarch64 aarch64 GNU/Linux
_______________________________________________

Best Regards, 

// hko


[list=1][*]Please specify the operating system and release version running on the server.
[*]I've removed the last few lines from your post. This is a volunteer forum. Enticements are not needed and might cause offence with some members. [/list].

---

### Post by hko2 on 2021-11-09
bump!

No-one knows how to start **irssi** in screen with other encode then 'UTF-8'?
I know it's possible beacuse I've done it long time ago but I just can't remember the line.. "*screen irssi -? encoding=ISO-89951"* SOMETHING.

I'm using Kali Linux and I can connect to other SSL SERVERS with in irssi command "[I]/connect -ssl example.server <port>. So it's not an ssl problem.
This specific server runs fully on encode ISO-89951 wich is a must to even connect to it.

I appreciate all kind of help

Best Regards,

// hko

---

### Post by LHammonds on 2021-11-10
Looking at "man screen" I see multiple references for encoding but only for setting "to" utf8.  Not setting to anything else.

Are you sure it was screen and not some other screen manager like tmux, byobu, dtach, mtm, wemux, abduco or zellij?

LHammonds

---

### Post by hko2 on 2021-12-03
Yes I'm sure it was screen I was using.
It was something like
$ screen irssi encoding="ISO-8859-15"

Something like that I'm sure. it's a way to make the server "unreachable" as must.
I get "SSL HANDSHAKE ERROR"

// hko

---

### Post by LHammonds on 2021-12-04
Here are links to related documents that might help you in the direction you want to go:

[https://irssi.org/documentation/settings/](https://irssi.org/documentation/settings/)

[https://quadpoint.org/articles/irssi/#utf-8-in-irssi-and-screen](https://quadpoint.org/articles/irssi/#utf-8-in-irssi-and-screen)

[http://www.iovene.com/posts/2007/03/the-ultimate-guide-for-utf-8-in-irssi-and-gnuscreen/](http://www.iovene.com/posts/2007/03/the-ultimate-guide-for-utf-8-in-irssi-and-gnuscreen/)

LHammonds

---

### Post by The Cog on 2021-12-04
There doesn't seem to be an ISO 89951 standard. And ISO 8995-1 is a standard for indoor illumination and lighting.

---


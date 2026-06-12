---
title: "Transmission Command line operations"
date: 2014-02-12
forum: Server Platforms
---

### Post by divxclub on 2014-02-12
Hi guys, I am trying to understand this client. I am using optware under ddwrt. Linux/3.5.7.13 and I am using transmission-daemon client with Transmission Remote app on windows to control all functions.

Here is the question. I see transmission-daemon in process tree in SSH and what if I don't want to use any kind of remote solutions, is it possible to fully control it from terminal and look at all activity ? Because I kinda don't understand the whole concept. Like I said I see already transmission-daemon working in background, how I can actually go and see what is going on because if I start transmission-daemon it's starting another process and then I see 2 transmission-daemon in process (htop) tree. So what exactly happening I starting 2 clients that use same torrents currently seeding/leeching or what. Basically I want to control add / delete / edit / change torrents from ssh with possibly some kind of gui. (GUI I mean let's say top vs htop, you know you can actually press buttons and move arrows).

Here are programs associated with transmission currently installed.

transmission-cli - 2.82-2
transmission-daemon - 2.82-2
transmission-remote - 2.82-2
transmission-web - 2.82-2

Thanks guys, I just need may be a command list with may examples on how to let's say add torrent file and stuff because I am sure it's possible and may be very easy I just finish installing this optware on router and my brains are just melting from all this codes.

Thank you !

---

### Post by ian-weisser on 2014-02-14
transmission-cli is well documented.
See [B]man transmission-cli
[/B]
Example to add a torrent: $ transmission-cli /path/to/foo.torrent

---


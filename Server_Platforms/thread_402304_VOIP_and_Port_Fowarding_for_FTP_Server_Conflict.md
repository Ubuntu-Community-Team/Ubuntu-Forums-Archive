---
title: "VOIP and Port Fowarding for FTP Server Conflict"
date: 2007-04-05
forum: Server Platforms
---

### Post by tbuss on 2007-04-05
Not sure if this is the right place to post this particular problem, so I apologize in advance.
The reason I'm posting here is because I had to close port forwarding on ports 20 and 21 to resolve the problem. So I had to choose between [COLOR="Red"]Vonage[/COLOR] service or my [COLOR="Red"]FTP server.[/COLOR]

I was having a problem with my voip service, no connection while logged into Ubuntu. I have a dual boot pc running windows and Ubuntu. When I'm logged into windows my Vonage service works as advertised, when logged into Ubuntu, no connection.  **The only way for me to use Vonage while logged into Ubuntu was to physically disconnect the PC from the router, then I would get a dial tone.**

To correct the problem I disabled port forwarding on ports 20 and 21, afterwards I was able to make calls using Vonage while logged into Ubuntu and connected to the router. But now I'm  confused about my FTP server config; I've seen other threads where folks have used port 1980. Not sure if this would make a difference.
**I guess I have a couple questions:**

How do I setup my PC so that I can have both: viop and ftp server.?
Why was it possible to use Vonage in windows with port fowarding enabled on ports 20 and 21 but not possible in Ubuntu?
Would a DMZ for the ATA resolve this issue; not sure how secure that would be.


Any advice would be greatly appreciated.

---


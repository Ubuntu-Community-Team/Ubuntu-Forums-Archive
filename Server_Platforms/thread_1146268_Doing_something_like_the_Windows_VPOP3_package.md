---
title: "Doing something like the Windows VPOP3 package"
date: 2009-05-02
forum: Server Platforms
---

### Post by cliveb on 2009-05-02
I'm planning on replacing the Windows 2000 household server with an Ubuntu machine. One issue I have is trying to replicate the functionality of a package called VPOP3 that I currently run on the Win2K box.

What this package does is connect to multiple external POP3 servers and store the retrieved mail in mailboxes within itself. Then the various users around the house (using an email client on their Windows PCs, eg. Outlook Express) retrieve their personal mail from the VPOP3 server rather than directly from the various external sources. It also acts as the SMTP server for the house - mail to be sent first goes into an output queue within VPOP3 and is delivered the next time it connects.

I think what I need to replicate this facility will involve a combination of a POP3 mail retriever (Fetchmail, Retchmail or similar?) and a POP3 server (Solid, Dovecot or similar?). But I'm by no means well-versed in the various terminology used by these packages to describe what they do, so I may well have misunderstood. It's possible there might be a single Debian/Ubuntu package out there that will do everything VPOP3 does and I haven't found it.

I am aware that some people have reported that VPOP3 will run inside a Windows emulator in Linux, but the whole point of this exercise is to get away from Windows, so I'm not interested in that route.

Can anyone offer some guidance? If nothing else, just knowing which package(s) are required would get me past my present state of having no idea which ones I should investigate.

---

### Post by ian dobson on 2009-05-02
Hi,

Have a look at xmail ([www.xmailserver,org](www.xmailserver,org)). It's a complete mail server with a POP3 and SMTP server/client and a simple coniguration system using text files.

I'm not sure if there's a apt package for it but the manual installation/compile isn't that hard.

Regards
Ian Dobson

---

### Post by cliveb on 2009-05-03
> **ian dobson said:**
> Have a look at xmail ([www.xmailserver.org](www.xmailserver.org)). It's a complete mail server with a POP3 and SMTP server/client and a simple coniguration system using text files.
Thanks for the pointer. I've taken a brief look at the Xmail documentation and reckon it'll take a while to figure it out, but at least I now have a place to start.

---


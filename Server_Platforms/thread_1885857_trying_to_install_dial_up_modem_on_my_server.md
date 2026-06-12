---
title: "trying to install dial up modem on my server"
date: 2011-11-24
forum: Server Platforms
---

### Post by kustomjs on 2011-11-24
Hi Guys
I am using Conexant dial up modem on ubuntu 10.04.3 lts with Linux 2.6.32-35-generic on i686 and I need some help on trying to set this up.

Thanks

---

### Post by kustomjs on 2011-11-24
anybody?

---

### Post by Irihapeti on 2011-11-25
You may find some useful information at [http://www.linuxant.com]("http://www.linuxant.com")

They make Linux drivers for Conexant modems. I ran one successfully for about 18 months, but that was a while ago and I don't remember much about the install process.

---

### Post by SeijiSensei on 2011-11-25
Inbound or outbound?  Are you asking about this specific modem, or are you looking for help handling PPP connections to an ISP or from remote dialup clients to you?  Providing a dialup shell server?  

For PPP, I'd start with the [HOWTO]("http://tldp.org/HOWTO/PPP-HOWTO/").

For inbound connections, your best choice is [mgetty](http://mgetty.greenie.net/doc/mgetty_toc.html).

---


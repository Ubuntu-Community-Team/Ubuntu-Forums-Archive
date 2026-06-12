---
title: "Is a DNS Server Needed in this case?"
date: 2010-06-19
forum: Server Platforms
---

### Post by Taurian on 2010-06-19
Hi!

I'm just starting to delve into DNS with my ubuntu server. Here's my question:

I have all my domains hosted at godaddy, and the A Records pointed at my new dedicated ubuntu server. It solved the problem in the short term as godaddy also hosts my mail.

Now I want to bring all that home. Is it really necessary? Are they any issues with just using Godaddy as my paid DNS to save the headache?

Thanks!

-T

---

### Post by cariboo on 2010-06-20
No you don't need to setup a DNS server, you're paying godaddy for the service, so you might as well use it.

---

### Post by terazen on 2010-06-21
I agree with cariboo907.  Stick with GoDaddy to save yourself the trouble until the point where the web interface doesn't do what you need.  They are keeping a good internet connection and reliable backups so the only reason to change would be if you run into a problem that the web interface can't solve.

---

### Post by BobVila on 2010-06-22
Another 2c here. Don't get in the business of hosting your own DNS. There's the 'you're already paying for it' argument, but on top of that, there's availability... What happens if your connection to the internet goes down? A DNS blackhole is a bit more dire than a standard 404 until you get reconnected.

---


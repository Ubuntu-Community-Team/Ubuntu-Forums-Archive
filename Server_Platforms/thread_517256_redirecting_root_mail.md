---
title: "redirecting root mail"
date: 2007-08-04
forum: Server Platforms
---

### Post by IcarusR on 2007-08-04
I have a daper server running Samba & Slimserver with f-Prot for virus scanning.
I would like to set it up to send all root messages (error & report mail) to my mail box @ my ISP so I can collect it when I collect my emails. I have a domain.
I do not wish to set up a full blown mail server, just send these messages.
Can someone please point me in the right direction.

Thanks

---

### Post by agds on 2007-08-04
I haven't done anything like this on my own machines, but on my university's server you can add a .forward file to your home directory&#8212;or in this case I suppose to /root.  The file consists of a single line, the address to which you want mail forwarded.  Multiple forwarding addresses, one per line, might be supported too.  I haven't been able to find any documentation for this, so it might be specific to a particular mail server.

---

### Post by IcarusR on 2007-08-04
Thanks for your reply agds.
 Just done some reserch, which I should have done before posting, & found out how to do it.

---

### Post by agds on 2007-08-04
You might want to post a link here, for anyone with a similar question who comes upon this thread.

---


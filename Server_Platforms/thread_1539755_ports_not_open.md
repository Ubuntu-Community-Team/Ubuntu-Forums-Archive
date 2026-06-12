---
title: "ports not open?"
date: 2010-07-26
forum: Server Platforms
---

### Post by darksidedude on 2010-07-26
hello all, I have hopefully an easy question

I am having trouble getting ports to open, on the router that the server is connected to it is set to DMZ, so everything passing through the router should go to the server right? but when I use a port checker none of the ports that I need to be open are. so my question is does ubuntu have a built in firewall that no one told me about? or something that would block me from having the ports open?

cheers

---

### Post by wojox on 2010-07-26
It does have a built in firewall ip tables / ufw but it's not on by default.

DMZ is not good. do you have the ability to Port Forward on your router?

What port are you looking to open?

---

### Post by darksidedude on 2010-07-26
I do have the ability to port forward on the router, I need ports 3306, 8129,8092 open

if it doesn't work while its in DMZ mode would forwarding those ports yield a different result? doesn't DMZ open ever single port known to man on the server?

---

### Post by wojox on 2010-07-26
> **darksidedude said:**
> I do have the ability to port forward on the router, I need ports 3306, 8129,8092 open

if it doesn't work while its in DMZ mode would forwarding those ports yield a different result? doesn't DMZ open ever single port known to man on the server?

No [DMZ]("http://en.wikipedia.org/wiki/DMZ_%28computing%29")

Try Port forwarding those ports and turn off DMZ.

---


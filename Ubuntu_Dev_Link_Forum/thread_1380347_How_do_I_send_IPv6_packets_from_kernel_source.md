---
title: "How do I send IPv6 packets from kernel source"
date: 2010-01-13
forum: Ubuntu Dev Link Forum
---

### Post by KarlIvan on 2010-01-13
I'm attempting to send packets from the Unix Kernel, and I can't seem to figure out exactly what I'm doing. I've been looking over the source for the past couple days, and have determined the structs and functions I should be concerned with (I believe either do_ipv6_setsockopt, ipv6_setsockopt...not really sure though, both of them seem to release the socket when they're done, and im not sure thats the best use of resources...because one function calls the other, so what the top function does, they both do. so maybe datagram_send_ctl function?)

If I knew how to send a packet, then that might help me enough to do what I want, but in any case:
I want to create my own destination option for the extension headers, and when a packet leaves the host, the destination header will be inserted into the header. I'm pretty sure I know what to do there, from looking at the source: I have to create my own struct that conforms with the generic destination option extension header so I can cast it as the generic when I pass it into the function that crafts the packet, and then generate the condition on which it does so. Then create the identifier for the extension header I am creating so that can be passed in to use to figure out what to do with the packet when it gets to the functions listed above. Problem being, if I don't know where the packet is created, I don't really know how to test that theory. I know how to do exactly what I want in binary, but unfortunately the kernel source is much more convoluted than that, and written in a language I am not entirely familiar with...to make matters worse, I am not entirely comfortable with my knowledge of networking.

So bottom line is: where in the source (or how, from outside the kernel do I call these functions) do I make calls to these functions, so I can send out packets with my new destination options?

---


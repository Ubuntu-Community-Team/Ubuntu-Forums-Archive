---
title: "Securing vino"
date: 2017-09-05
forum: Server Platforms
---

### Post by chris6672 on 2017-09-05
Hi

Apologies if this is not the right place to post this question, but I want to check something.

My dad lives 200 miles from me. He likes the Internet, but has asked me basically the same questions about once a month since some time in the nineties. I've decided to set up a remote desktop so I can help more easily.

We have two machines running Lubuntu. His machine has vino installed, and I can connect via SSH to his machine and view his desktop on my laptop.

I'm not worried if it's on his local network, but I want to be able to securely connect from my computer at home. So I took these steps to secure SSH:


[LIST]
[*]disabled root login
[*]set a nonstandard port for SSH.
[*]set a firewall rule that only allows access from my (static) IP address at home
[*]disabled protocol 1
[*]disabled passwords, and set public/private keys for access
[/LIST]

Have I missed anything before I set up port forwarding on his router, and expose him to the rest of the world? Is SSH enough, or should I set up a VPN as well? I don't want to be paranoid or do extra work, but I don't want him vulnerable.

Thanks in advance, and apologies if I've asked in the wrong part of the forum.

---

### Post by wildmanne39 on 2017-09-05
*Thread moved to **Server Platforms for a better fit**.*

---


---
title: "Beginner question: Setting up authenticated SMTP relay"
date: 2010-06-15
forum: Server Platforms
---

### Post by Bakmeel on 2010-06-15
Hello,

I am new to the Ubuntu Community and just starting to build my Ubuntu 10.04 Server. I am a novice in Ubuntu, though maybe not a full n00b any more :)

I travel around a lot with my laptop, (also Ubuntu 10.04). However, my ISP does not allow me to send email via their SMTP when I am not in their IP range.

Since I have this little server I am building, I thought it would be nice if I could have my own SMTP relay. The objectives would be simple:
- I do not need a mailbox or POP server (yet).
- I wish to send email from any place in the world. I can not use a filter on IP ranges or local networks only.
- If my server could do this, I just configure Evolution on my laptop to send mail to my home IP address, using some sort of authentication and/or security/encryption (whichever is easy to implement).
- My server then just forwards my mail to my ISP. Since the server is inside the IP range, it can be handled as usual.

I have been digging through several howto's and the ubuntu server guide, searching some forums etc. Even while I don't fully grasp the things explained, I can't get the idea that one of those is "Just what I need".

So, some help is appreciated. Even still, if there is some other service outside my own that can do this (a public SMTP relay maybe?) I would also be happy to consider as long as it is safe and does not "eavesdrop" on my messages.

Thanks all in advance!
Bakmeel

---

### Post by Bachstelze on 2010-06-15
You don't even need to install anything on your server. :) Just create a SSH tunnel like this:

```
ssh -L 2525:smtp.isp.com:25 your.server.org
```

Replace smtp.isp.com by the adress of your ISP's SMTP, and put localhost, port 2525 as SMTP in Evolution. You're done. :)

---

### Post by Bakmeel on 2010-06-15
Wauw! :-) That was easy...

Thanks for the tip... I begin to realise that ssh tunneling is a powerful asset! Thanks for the tip!

Bakmeel

---

### Post by Bachstelze on 2010-06-15
Also don't forget ~/.ssh/config so you don't have to type the whole command every time. ;)

```
Host your.server.org
    LocalForward 2525 smtp.isp.com:25
```

---


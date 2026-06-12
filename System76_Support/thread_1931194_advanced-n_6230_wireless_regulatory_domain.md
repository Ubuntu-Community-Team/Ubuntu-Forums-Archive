---
title: "advanced-n 6230 wireless regulatory domain"
date: 2012-02-25
forum: System76 Support
---

### Post by jschall1 on 2012-02-25
I have a gazelle professional with the Intel advanced-n 6230 running kubuntu 11.10.

I've been having a lot of trouble connecting to the wifi at my university, I sent IT an email with logs and they said that they were resetting the access point in the particular building where I was having the problem, and that they noticed in my logs that my regulatory domain was set to world instead of US and that could cause problems.

So I did some googling, and found that the iw command is used to set the regulatory domain. However, I assume that setting it that way will not persist through a reboot. I haven't had a chance to test it at school again but I'm guessing it's either: a. illegal to have it set to world while in the US, or b. the world domain tries not to break any regulation that exists in the world.

Why is it getting set wrong? What can I do to ensure it is set correctly?

---

### Post by jschall1 on 2012-02-25
What it was set to:
jschall@jon-laptop:~$ iw reg get
country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

US (looks less restricted)
jschall@jon-laptop:~$ sudo iw reg set US
jschall@jon-laptop:~$ sudo iw reg get
country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)

---

### Post by jschall1 on 2012-02-25
Well, at this point I doubt it's a problem on my end anyway, I'd love to learn more about the regulatory domain thing, but I kind of doubt that it is causing me problems. I think they have a bad or misconfigured access point...

---


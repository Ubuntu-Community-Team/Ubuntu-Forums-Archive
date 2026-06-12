---
title: "strange dmesg output"
date: 2009-03-17
forum: The Cafe
---

### Post by orlox on 2009-03-17
I have a screenlet that outputs dmesg on my desktop every once in a while. Today, after a period of inactivity, I saw my desktop, and found this strange message:

```

TCP: Treason uncloaked! Peer 217.70.119.238:38462/44943 shrinks window 477191629:477191634. Repaired.

```

repeated some times...Sounds serious, but as everything seems to keep working as it should, Im not taking to much attention on this...Should I??

(On the other hand, I posted this here cause I found funny the "Treason uncloaked!" part of the message :P)

---

### Post by snova on 2009-03-17
Since I don't have a copy of the source, this site will do. It originates here:

[http://lxr.linux.no/linux+v2.6.28.8/net/ipv4/tcp_timer.c#L302](http://lxr.linux.no/linux+v2.6.28.8/net/ipv4/tcp_timer.c#L302)

[PHP]
        if (!tp->snd_wnd && !sock_flag(sk, SOCK_DEAD) &&
                !((1 << sk->sk_state) & (TCPF_SYN_SENT | TCPF_SYN_RECV))) {
                    /* Receiver dastardly shrinks window. Our retransmits
                     * become zero probes, but we should not timeout this
                     * connection. If the socket is an orphan, time it out,
                     * we cannot allow such beasts to hang infinitely.
                     */
[/PHP]

What it *means*, I have no idea...

---


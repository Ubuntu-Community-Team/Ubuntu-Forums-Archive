---
title: "Ridiculous Time"
date: 2019-09-21
forum: The Cafe
---

### Post by westie457 on 2019-09-21
Just ran a 'sudo apt update' with this result.   Fetched 8,324 kB in 213503982334601d 6h 59min 42s (0 B/s)

Is there something seriously wrong.:lolflag:

---

### Post by Frogs Hair on 2019-09-21
I'm on the development release using the U.S. sever and it's updating fine. Your download server may have an issue.

---

### Post by Skaperen on 2019-09-21
how often does that happen?

converting that number to pure seconds was about 6 hours short of 2**64 seconds.  that suggests to me that some clock somewhere jumped backwards by about 6 hours.  maybe a time zone  change during the duration measurement did that.

---

### Post by westie457 on 2019-09-21
I know my d/load speed can be a bit flaky at times from any server, this for me is a reasonable speed.

Fetched 148 MB in 1min 21s (1,826 kB/s)

I am running Ubuntu Budgie 18.04 on this machine.

I think this might be 'one of those things' to be filed under quirky behaviour.

In the past I have had a reported download speed in PB/s for the same command.

---

### Post by Skaperen on 2019-09-21
that time would be about 18 seconds if the shift of -6 hours had not taken place.

---

### Post by westie457 on 2019-09-21
> [COLOR=#000000]how often does that happen?[/COLOR]
This is the first time on this machine. 
The issue itself is not worth troubleshooting.
I just thought it strange and funny that a simple 'sudo apt update' would report itself as taking 58+ million years to complete.

The other times on a different machine when the reported speed was in PB's I am reasonably sure there is no server or connection capable of that speed.

---

### Post by VMC on 2019-09-22
The issues I have are with ipv6. I need to turn off ipv6. Otherwise updates just sits there forever.

---


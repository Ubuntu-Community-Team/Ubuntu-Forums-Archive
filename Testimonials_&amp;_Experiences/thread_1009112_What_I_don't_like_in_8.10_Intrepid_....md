---
title: "What I don't like in 8.10 Intrepid ..."
date: 2008-12-12
forum: Testimonials &amp; Experiences
---

### Post by cwmoser on 2008-12-12
I find this release (8.10) a little disappointing as compared to 8.04 Hardy.

Here is what I think are real disappointments:

- Network connection is established after you log in.  I remote into my home pc and sometimes need to reboot it.  With 8.10, I would not be able to remote back in until I returned home and logged in.

- Quick Books ran with wine compatibility using CodeWeaver's Cross Over just fine.  It will not even crank up with 8.10
I upgraded to the newer version of Cross Over and still Quick Books would not start up.  

- Not sure if its my hardware or not, but the video seems a little quirky - title bars not present - have to click off the window and back on to get it work.

I think I'm going to stay with 8.04 LTS and not deal with the *.10 releases.

Have you found any other issues with 8.10?

Carl

PS:  Don't take me as a Ubuntu basher -- I really like Ubuntu 8.04 Hardy

---

### Post by zika on 2008-12-12
> Network connection is established after you log in. I remote into my home pc and sometimes need to reboot it. With 8.10, I would not be able to remote back in until I returned home and logged in.

it doesn't have to be. edit Your /etc/network/interfaces so You get:```
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp

```
and You will have connection the moment You boot in Ubuntu.

---


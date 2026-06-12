---
title: "The future of snappy/snaps?"
date: 2017-08-05
forum: The Cafe
---

### Post by k1200 on 2017-08-05
Hi Forum Friends,

I've just been playing around with Snappy (aka ubuntu core) because of a robotics project I'm working on with a friend. We were really inspired by this blog:

[https://kyrofa.com/posts/from-ros-prototype-to-production-on-ubuntu-core-1-5](https://kyrofa.com/posts/from-ros-prototype-to-production-on-ubuntu-core-1-5)

since snaps allow us to package our product and deploy across across millions of cross-platform devices. Its been around for almost two years now but I'm finding it difficult to use without the flexibility of apt. I cant find any snaps with the tools I need, e.g. wget, others

For e.g. we want to test if snappy on a Raspberry Pi can support a specific i2c device over the GPIO header but there's no i2c-tools snap. Maybe this is an extreme example, but what's the communities thoughts on the developer friendliness of snaps vs production benefits specifically on embedded arm boards

---

### Post by cariboo on 2017-08-05
Have you had a look at:

[https://forum.snapcraft.io/](https://forum.snapcraft.io/)

---

### Post by jsmolka on 2017-08-08
[SIZE=2]For the moment you have to work with "trial and error" ... 

This project is still very young and there are changes and improvements on every day -- also there is no written documentation and you have to look for information in many different places right now. 

I just created a plain timer snap ([ttimer]("https://dashboard.snapcraft.io/dev/snaps/8079/")) and it has still some issues because of missing instructions or buggy code in the core and interfaces -- e.g. the connection to a web browser (the info button of the ttimer app) is a known bug they are working on already.[/SIZE]


[COLOR=#a9a9a9][SIZE=1]-- have a try !  -----------[/SIZE][/COLOR] 
[FONT=comic sans ms][SIZE=2]...:~$ [COLOR=#008000]sudo snap install ttimer

:popcorn: [/COLOR][/SIZE][/FONT]

---


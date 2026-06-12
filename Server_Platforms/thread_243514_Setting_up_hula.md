---
title: "Setting up hula"
date: 2006-08-25
forum: Server Platforms
---

### Post by M7S on 2006-08-25
I am trying to install hula on my desktop computer to be able to make a shared calendar between my desktop and my laptop in evolution. I installed hula via synaptic and  following the instructions on help.ubuntu.com/community/Hula I runned "sudo hulasetup" and "sudo /etc/init.d/hula start". Then what? I guess I should try to connect to the webadmin at port 89, so I wrote 127.0.01:89 in firefox addresbar. Firefox told me it was unable to connect. I tried to open  port 89 with firestarter (not that I tought that would do any difference since I used my localhost) that didn't work. I've searched around internet for over an hour but can't find any infromation on what I am doing wrong.

Have I completly misunderstood how hula works and what it is or am I just missing some simple step needed to set up hula? I feel like an total newbie right now and I don't like it. :(

I'm running an apache2 server for mythweb. Could that have anything to do with why hula isn't working?

EDIT: Problem solved reason for not working was probably that I didn't restart apache ](*,) At least I got it to work now when I started up my computer. :)

---


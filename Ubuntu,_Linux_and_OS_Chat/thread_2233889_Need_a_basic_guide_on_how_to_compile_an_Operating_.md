---
title: "Need a basic guide on how to compile an Operating System"
date: 2014-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by J_Me on 2014-07-11
Can someone explain howto compile an OS or link to something that's clear and basic.
Thanks

---

### Post by reddevil2064 on 2014-07-11
You'll want to start here:

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Also give Gentoo a shot if you want to experience compiling everything from scratch.

---

### Post by ibjsb4 on 2014-07-11
I wouldn't call it compiling, but you can start with the mini iso and just add the packages you want.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini+iso&sa=Search&cof=FORID:9)

Server gui will give you some ideas on how to build it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by J_Me on 2014-07-11
Thanks for the reply, I was hoping for something a little shorter the LFS handbook is 400 pages, but it does cover everything in detail though.
Gentoo is not for me as this project will run on a raspberry pi.
Thanks again

---

### Post by reddevil2064 on 2014-07-11
If you're wanting to do this for a RaspberryPi why not just use the precompiled packages already available for that platform? It's going to take a painfully long time to get an environment built and compiled on a Pi, this is speaking from experience when compiling some multimedia streaming tools.

---

### Post by tgalati4 on 2014-07-11
Perhaps explain what your project is trying to accomplish and we can direct help in that direction.  For the RaspberryPi, you can do development on any machine and then cross-compile into the ARM binaries.  You could set up a development environment on the Pi itself, but it is a slow platform for such work.  If you really need to recompile the kernel to perform outside-the-box, then you will need to set up a proper Pi build environment.

Let me Google that for you (raspberry pi development environment)

[http://elinux.org/Raspberry_Pi_Programming](http://elinux.org/Raspberry_Pi_Programming)

[http://visualgdb.com/tutorials/raspberry/](http://visualgdb.com/tutorials/raspberry/)

[http://www.raspberrypi.org/forums/viewtopic.php?f=2&t=4521](http://www.raspberrypi.org/forums/viewtopic.php?f=2&t=4521)

---

### Post by coffeecat on 2014-07-11
Not an Ubuntu/Ubuntu flavour support thread.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by J_Me on 2014-07-11
I just found a tutorial on compiling the project using ubuntu 12.04. So with that and the info from tgalati4 I think I'll mark this thread as solved.
Thanks for the suggestions and links everyone


p.s. I had a much more detailed reply ready to copy and paste but the thread got moved, nevermind.

---


---
title: "Ubuntu Studio 8.10 Dual/quad CPU: yes or don't?"
date: 2008-11-14
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2008-11-14
Hi, I'm a bit confused:

The [release notes of Ub_Studio 8.10]("http://www.ubuntu.com/getubuntu/releasenotes/810") state that the -rt kernel doesn't support multiple cpu's. The advice is to not upgrade. 

As far as I understand (sorry, english is not my native language), I should not use ub_studio 8.10 at all if I have a dual or quad cpu. But it seems strange to me, as most DAW are more than single cpu nowadays. Wondering if the advice is only about upgrading from an existing installation of 8.04, and does not apply to a fresh install of 8.10.

¿Can someone enlighten me? ¿Should I install 8.10 on a quad-core machine?
¿What's your advice?

---

### Post by JC Cheloven on 2008-11-15
Bump.

---

### Post by warbread on 2008-11-17
I recommend not installing.  I've had a world of trouble since I installed from scratch (not an upgrade).  I'm using Hardy's -rt kernel and I'm still having instability issues.  Just wait.

---

### Post by Stochastic on 2008-11-17
It's a problem with the Intrepid Realtime patched kernel.  There's a major bug in it where even in multiple core CPU machines only one core is ever used.  This only affects the RT patched kernel so if you're using UbuntuStudio for non-audio purposes (i.e. graphics, webpages, even video) then you don't need the RT kernel and the vanilla one should work fine (including multiple core support).  But if you're using UbuntuStudio for audio purposes then you should stick with Hardy 8.04 until these RT issues are resolved.

---

### Post by Ng Oon-Ee on 2008-11-18
A bit to add to that, Ubuntu Studio itself works fine, even the audio app, but as mentioned there are bugs with the RT kernel.

This is why, upon installing Ubuntu Studio 8.10, it does NOT install the RT kernel for you. So you get the same vanilla kernel all the other users get, which means the only issues would be the ones you would have gotten anyway. And yes, you get multiple core support.

The flipside is you don't get the RT kernel, so no real-time support for you. I've installed that from the repos, and the only bugs are shutting down problems if your network is enabled (I just disable networking before shutting down, I have to do that with vanilla kernel anyway and its not much of a hassle) as well as only single core usage. So I only use it for stuff that needs the RT (mainly my audio recordings, of course) and mostly use the vanilla kernel.

A piece of advise, if you're using the nvidia binary-only driver, your Xorg will fail to start on first boot of the RT kernel. You should first boot to root prompt for the RT kernel, install the driver (I always use envyng), and then restart.

---

### Post by Ng Oon-Ee on 2008-11-18
.

---

### Post by JC Cheloven on 2008-11-19
Thank you everybody.

I do use Ubuntu Studio for audio purposes, so I think I'll stick with 8.04. I don't wanna mess everything. Sound in linux is complicated enough by himself :-D

Greetings

---

### Post by Ng Oon-Ee on 2008-11-19
> **JC Cheloven said:**
> Sound in linux is complicated enough by himself :-D

Quoted for truth. I used to use Windows for recording though, and now that I've tasted JACK, I can't imagine going back to latencies measured in tenths of a second rather than in ms.

---

### Post by It-Alien on 2008-12-05
where can I read about the status of this bug?

I didn't notice about this problem until I had the bad idea of upgrading to 8.10, so currently I'm stuck with Windows for the RT stuff.

should I install the old RT kernel back or do you think this problem will be addressed in a few time?

---

### Post by markbuntu on 2008-12-11
It will get fixed, it is just a matter of waiting.

---


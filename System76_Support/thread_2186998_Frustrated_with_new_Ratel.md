---
title: "Frustrated with new Ratel"
date: 2013-11-10
forum: System76 Support
---

### Post by grizdog on 2013-11-10
Mostly this thread is just a warning to others, but if anyone has any ideas about how to get out of this, I would be happy to hear them.

The problem I am havng now that seems very strange is that I cannot get the thing into recovery mode.  I managed it once, but since then it just won't do it.  I have held down the left shift key as it booted at least 10 times, tried other keys like right shift, escape, and tab, entered the bios... nothing works.  I really need a root prompt and can't get one.  

I bought the new Ratel configured with an optional video card.  Unfortunately, I did not yet have my new monitor, and my old monitor does not have a DVI port, but the video card does not have a VGA port.  So I plugged the  old monitor into the onboard video and turned the machine on, and got nothing on the monitor.  I posted another thread about theis.  With no video, I turned off the computer (which may have been my fatal mistake) and went off to a friend's house to borrow a monitor with a DVI port.  I plugged that into the video card, and it worked.

Problem is, now the computer just comes up into the standard graphical login screen - not the the initial sequence where among other things, you can set up an administrative account.  I am guessing that I lost that the first time I turned it on, and then turned it off, with no video.  Anyway, now all I can do is login to a guest account, with no password.  Whenever I try to do anything administrative, it asks my for a password, and nothing simple, like just an <enter>, seems to work.  So I can cruise the web, but I can't do any configuration.

With a root prompt I could type ```
adduser alex sudo
``` and I would have my administrative account. I'm not sure what else I will have missed in the startup sequence, it would be nice if I could get that to startup sequence, but for now I would settle for a root prompt.

As I said in the beginning, this is mostly a warning, although I would appreciate any ideas.  I plan to call System 76 Monday morning and either get a fix or a return authorization.  I have installed Ubuntu and other Linux distros on other machines before, and I don't remember having such problems as I have had with this pre-installed, Ready-to-go-right-out-of-the-box "solution".  In fairness, my other System 76 box, laptop, did work fine, but this has been very frustrating.

---

### Post by isantop on 2013-11-11
This is actually being caused by a bug in Ubuntu when you plug the monitor into the incorrect video ports (the upper, vertical ones on the motherboard rather than the lower, horizontal ports on the graphics card). All new machines will now ship out with a note on the back instructing the user which ports to use, and I've opened a thread with a fix here: [http://ubuntuforums.org/showthread.php?t=2187265](http://ubuntuforums.org/showthread.php?t=2187265)

---

### Post by grizdog on 2013-11-11
Thanks, Ian.  I think it's also worth pointing out that you can go into recovery mode by pressing the reset button just as the first Ubuntu screen comes up.  Don't know why the shift key didn't work, but that worked fine, gave me a root prompt.

Now that the box is up, life is good.

---


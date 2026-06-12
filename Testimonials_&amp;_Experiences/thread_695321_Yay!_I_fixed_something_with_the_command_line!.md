---
title: "Yay! I fixed something with the command line!"
date: 2008-02-12
forum: Testimonials &amp; Experiences
---

### Post by mikeize on 2008-02-12
So my electricity went out today, and the sudden shutdown somehow screwed up ubuntu (can someone explain?).  Well, the result was that I couldn't log in!  I got an error saying that my /home/mike couldn't be found, did I want to login using the root partition as my /home, etc etc.  Yes or no, either choice ended up with me back at the login prompt.

So I switched session to failsafe terminal, and ran firefox from the prompt.  After some frustrating research I thought I knew enough to take a stab at the problem.  Anyway, I simply did:

sudo mount /dev/sda3 /home
sudo reboot

and voila!  peachy keen.
I'm very happy/proud of myself.  I still have no idea why this was necessary, as my fstab file seemed fine (i checked it first).  But nonetheless, I'm glad this was a 2 hr, rather than 2 days/weeks/reinstallation issue!  
Just wanted to share.  thanks!

-mike

---

### Post by HappyFeet on 2008-02-12
great to hear. rock on. :guitar:

---

### Post by kellemes on 2008-02-13
Most people probably would advice a reinstall.
You just fixed it the tux-way!

Well done! :)

---

### Post by ukripper on 2008-02-13
Great job Comrade!

---

### Post by mikeize on 2008-02-13
heh heh, thank you!

of course today, I spent 45 minutes frustrated because my printer wouldn't work.  And then I realized it was unplugged (usb)!  :oops:

so much for my "computer savvy", eh?

Anyway, can someone explain how my original problem occurred?  ie, a power interruption caused ubuntu to 'forget' where my home dir was.

---

### Post by lespaul_rentals on 2008-02-13
ReiserFS or ext3 filesystem I'd assume?  Sometimes power failures can cause issues, but those two filesystems tend to recover after a mount and reboot.

Good job.  ;)

---


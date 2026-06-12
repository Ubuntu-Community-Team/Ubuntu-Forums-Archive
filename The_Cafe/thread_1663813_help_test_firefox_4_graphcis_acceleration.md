---
title: "help test firefox 4 graphcis acceleration"
date: 2011-01-10
forum: The Cafe
---

### Post by ssam on 2011-01-10
> One of the new features of Firefox 4 is graphics hardware acceleration.   This, along with the new layers code, will help improve Firefox performance during things like page rendering and full-screen video.

Firefox’s hardware acceleration interacts with a machine’s graphics hardware via DirectX or OpenGL, depending on platform.  These interactions tend to be very sensitive to the graphics environment on the system (e.g., the specific video card(s) on the system, how much VRAM is available, the version of the video driver, the OS version, etc).  In fact, there are so many permutations of the relevant factors that we can’t test them all internally.  We need help from the community, so we can get exposure on as many unique hardware environments as possible.

[http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/](http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/)

All you need to do is install firefox 4, install a plugin Grafx Bot, and click run tests. it will render about load of tests with and without the new acceleration, and report back any differences. takes about 10 mins.

---

### Post by mikewhatever on 2011-01-10
I thought hardware hardware acceleration was disable in the current beta for Linux. Did it work for you?
Edit: Apparently it enables hardware acceleration - layers.accelerate-all.

---

### Post by ssam on 2011-01-10
i got a few failures
[http://brasstacks.mozilla.com/resultserv/data/results/11621141-4dc8-4a27-b3b5-626f7f9d7ab9](http://brasstacks.mozilla.com/resultserv/data/results/11621141-4dc8-4a27-b3b5-626f7f9d7ab9)
but its mostly working.

i think if they enabled it now there would be a few rendering bugs on some linux drivers. this test is to help track them down on a wide range of hardware.

---

### Post by mikewhatever on 2011-01-10
Cool, here is mine.
[http://brasstacks.mozilla.com/resultserv/data/results/c1c92a23-d00a-4e58-a441-9da8c2986897](http://brasstacks.mozilla.com/resultserv/data/results/c1c92a23-d00a-4e58-a441-9da8c2986897)

---

### Post by TheLions on 2011-01-10
Nvidia 7600GT (blob), 100% pass

---

### Post by rajeev1204 on 2011-01-10
This is the test you should try too;

[Hardware Acceleration Stress Test]("http://demos.hacks.mozilla.org/openweb/HWACCEL/") 

I get 7 fps with my ATI hardware and a lot of headache but i guess they are working on that.

---

### Post by Spr0k3t on 2011-01-10
Couple failures on this end.  [http://brasstacks.mozilla.com/resultserv/data/results/b1252fa1-afe0-4859-8bb3-f0fec2365dc5](http://brasstacks.mozilla.com/resultserv/data/results/b1252fa1-afe0-4859-8bb3-f0fec2365dc5)

Also, the hardware acceleration stress test yielded 92fps.

---

### Post by mikewhatever on 2011-01-10
> **rajeev1204 said:**
> This is the test you should try too;

[Hardware Acceleration Stress Test]("http://demos.hacks.mozilla.org/openweb/HWACCEL/") 

I get 7 fps with my ATI hardware and a lot of headache but i guess they are working on that.

Got 6 with Intel's gma500. :P

---

### Post by ssam on 2011-01-12
ran on a Matrox card at uni. anyone have any other interesting graphics cards?

---

### Post by Spr0k3t on 2011-01-12
> **grafix10 said:**
> how to test it ?
got strange issues with firefox4 too

Once you have installed the add-on, go to the tools menu and launch Grfx-Bot.

---

### Post by zer010 on 2011-01-12
I had gotten FF4beta8 just to run this test.  I had a few errors and the lag time was unbelievably slow.

---

### Post by mikewhatever on 2011-01-13
Here's another, with Nvidia 7400 go.
[http://brasstacks.mozilla.com/resultserv/data/results/45239753-84c5-4d4e-8b42-290b50995232](http://brasstacks.mozilla.com/resultserv/data/results/45239753-84c5-4d4e-8b42-290b50995232)

---

### Post by mikewhatever on 2011-01-15
Looks like chances of having hardware acceleration are pretty slim for us.
[https://hacks.mozilla.org/2011/01/firefox-4-beta-9-a-huge-pile-of-awesome/comment-page-1/#comment-349829](https://hacks.mozilla.org/2011/01/firefox-4-beta-9-a-huge-pile-of-awesome/comment-page-1/#comment-349829)

---


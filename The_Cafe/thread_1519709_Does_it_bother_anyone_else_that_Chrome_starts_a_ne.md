---
title: "Does it bother anyone else that Chrome starts a new process with every new tab?"
date: 2010-06-28
forum: The Cafe
---

### Post by user1397 on 2010-06-28
It kind of bothers me... I just don't understand why with all of Chrome's advanced design and simplicity they went with this approach instead of all of it being one process...

Well yea, just wondering what you guys think

---

### Post by Bachstelze on 2010-06-28
It doesn't bother me, 'cause I don't use Chrome

---

### Post by koenn on 2010-06-28
> **ubuntuman001 said:**
> It kind of bothers me... I just don't understand why with all of Chrome's advanced design and simplicity they went with this approach instead of all of it being one process...

Well yea, just wondering what you guys think

IIRC, this is meant to be a feature. With each tab its own process, one site can't crash your entire browser (just the process of its tab). This possibly also means that security can be more easily managed.

---

### Post by nrs on 2010-06-28
I thought it was the main selling point?

---

### Post by lisati on 2010-06-28
Perhaps someone, as part of the design process, decided it was easier and/or more prudent to start a new process instead of keeping as much as possible together in one place.
> **Bachstelze said:**
> It doesn't bother me, 'cause I don't use Chrome
Ditto.

---

### Post by Npl on 2010-06-28
> **koenn said:**
> IIRC, this is meant to be a feature. With each tab its own process, one site can't crash your entire browser (just the process of its tab). This possibly also means that security can be more easily managed.I`d prefer if the site just couldn`t crash **the browser or parts of it at all** which should be a reasonable goal for developers. Now isolating external stuff like the flash-plugin I can understand, but trapping **your own code** in isolation (with all the performance penalties of separate processes and communication between them involved) so it doesnt take down the whole program sounds like a lack of self-confidence.

I wonder how the planning for this feature went like... "Guys we can only crash on 1 page at a time, fix that please!"?

---

### Post by Phrea on 2010-06-28
I don't use Chrome.
Should be in your poll.

---

### Post by Mohamedzv2 on 2010-06-28
At first, it did. Now it doesn't really interfere much with my browsing. I'm kind of used to it now.

---

### Post by koenn on 2010-06-28
> **Npl said:**
> I`d prefer if the site just couldn`t crash **the browser or parts of it at all** which should be a reasonable goal for developers. Now isolating external stuff like the flash-plugin I can understand, but trapping **your own code** in isolation (with all the performance penalties of separate processes and communication between them involved) so it doesnt take down the whole program sounds like a lack of self-confidence.

I wonder how the planning for this feature went like... "Guys we can only crash on 1 page at a time, fix that please!"?

Hey, *I* didn't design the thing. You should post your comments on a chrome mailing list somewhere.

Anyway, given that a browser will pretty much have to execute whatever it finds on a given URL (which will become increasingly more in the future), some compartmentalization sounds like a rather good idea.

---

### Post by Tristam Green on 2010-06-28
> **koenn said:**
> IIRC, this is meant to be a feature. With each tab its own process, one site can't crash your entire browser (just the process of its tab). This possibly also means that security can be more easily managed.

It bothers me somewhat, because it's not just one site that crashes Chrome, but the entire conglomerate of sites that do.

Bear in mind on the usual builds of Chromium, i have no issues.  I only do on the Google release.

---

### Post by endotherm on 2010-06-28
a process is an object with distinct security and resource boundaries around it, keeping it from harming others and others from harming it. by isolating each tab, one tab crashing can't take down the whole session, and it means that anyone who wants to read one of your other open tabs would need to leverage an interprocess communication hack to do so. defeats attacks like the click-napping stuff that started making the new a few months ago.

---

### Post by lukeiamyourfather on 2010-06-28
> **nrs said:**
> I thought it was the main selling point?

That's correct, it is. Security and stability are the primary reasons at the cost of some computing resources. Its a good trade if you ask me.

---

### Post by Shining Arcanine on 2010-06-28
> **ubuntuman001 said:**
> It kind of bothers me... I just don't understand why with all of Chrome's advanced design and simplicity they went with this approach instead of all of it being one process...

Well yea, just wondering what you guys think

This design is superior, because it forces the developers to support multicore processors, unlike the single process approach. It also means that an invalid page fault in one tab/plugin will not kill the browser.

There are other ways of doing it, but this way makes these guarantees natural by design, while other ways requires more constant vigilance on the part of the chromium development team to make such guarantees, because they would need to ensure that every change to the browser maintains those guarantees. That has similar difficulty to trying to flip a coin and get heads each time.

---

### Post by GeneralZod on 2010-06-28
I'd also *guess* that the "one process per tab" would lead to much less of the memory fragmentation that plagues other browsers: With "one process per tab", once you close a tab, you'll get *all* the memory allocated for the contents of that tab back (which doesn't necessarily happen if the memory allocated for that tab is mixed in with that allocated for other tabs, as is likely with an "all in one" process) as returning all of the memory used for a process is presumably easier for the operating system.

---

### Post by lukeiamyourfather on 2010-06-28
> **whamuel said:**
> This sounds very interesting. I've always used Firefox, but this discussion is making me consider giving Chrome a try. Is it that much more taxing on your system, because of the multiple processes?

Comparing apples to apples it will use more resources than other browsers when rendering the same pages. Though it feels much faster because many pages can be rendered at one time and all in different processes (e.g. on different cores too). It also loads very quickly. So regardless of what resources it uses, the experience for the end user is much better than most other current browsers like Firefox. Cheers!

---

### Post by days_of_ruin on 2010-06-28
> **Phrea said:**
> I don't use Chrome.
Should be in your poll.

There is, it's called not replying.

---

### Post by beastrace91 on 2010-06-28
> **ubuntuman001 said:**
> It kind of bothers me... I just don't understand why with all of Chrome's advanced design and simplicity they went with this approach instead of all of it being one process...

Well yea, just wondering what you guys think

In case someone else didn't say it already - it is for stability. This way when one of your tabs hard locks (for whatever reason) it doesn't crash the whole browser like it would on Firefox.

~Jeff

---

### Post by NMFTM on 2010-06-28
Does anyone know if Firefox is going to get this feature?

---

### Post by Bluesan on 2010-06-28
I dual boot Win 7 and Ubuntu, and I prefer Chrome, not only because it's fast, but, because I can seamlessly sync the browser between the two OSs. (There is a similar option with Firefox, but personally, I've found it problematic, where Chrome just works.)

Running 64 bit on both, I did find that I needed to abandon openJdk, and install Sun Java 6 to get it to run properly on Ubuntu.

Regarding the new process in new tabs, it means more to a user who uses Windows, than to Linux, but, It's an interesting security feature, that doesn't seem to get in the way.

So, it doesn't bother me in the least.

> Chrome will typically allocate each tab to fit into its own process to "prevent malware from installing itself" and prevent what happens in one tab from affecting what happens in another, however, the actual process-allocation model is more complex.[52] Following the principle of least privilege, each process is stripped of its rights and can compute, but cannot write files or read from sensitive areas (e.g. documents, desktop)&#8212;this is similar to the "Protected Mode" used by Internet Explorer on Windows Vista and Windows 7. The Sandbox Team is said to have "taken this existing process boundary and made it into a jail";[53] for example, malicious software running in one tab is supposed to be unable to sniff credit card numbers entered in another tab, interact with mouse inputs, or tell Windows to "run an executable on start-up" and it will be terminated when the tab is closed.[15] This enforces a simple computer security model whereby there are two levels of multilevel security (user and sandbox) and the sandbox can only respond to communication requests initiated by the user...

[http://en.wikipedia.org/wiki/Google_Chrome#Security](http://en.wikipedia.org/wiki/Google_Chrome#Security)

---

### Post by cb951303 on 2010-06-28
this is a feature. in fact google started marketing chrome with this feature.

---

### Post by NMFTM on 2010-06-28
> **NMFTM said:**
> Does anyone know if Firefox is going to get this feature?
Yes, apparently they are:
[https://wiki.mozilla.org/Content_Processes](https://wiki.mozilla.org/Content_Processes)
[http://www.techspot.com/news/35383-Multiprocess-support-in-Firefox-gets-closer-to-reality.html](http://www.techspot.com/news/35383-Multiprocess-support-in-Firefox-gets-closer-to-reality.html)

---

### Post by chessnerd on 2010-06-28
I don't use Chrome personally, but I don't think it's that big of an issue. In a way, it's nice because if you know which process a certain tab is running in, you can kill that process and bring back your browser if it is locked up. I've done this before for my sisters, who use Chrome on Windows, when the browser locked up on them while they were playing Farmville/Cafe World/PetVille/Other-mindless-Facebook-game.

---

### Post by Jayayess1190 on 2010-06-28
[Explanation of process per tab]("http://www.chromium.org/developers/design-documents/process-models").

---

### Post by ubunterooster on 2010-06-28
It makes more sense as we get more cores.

---

### Post by formaldehyde_spoon on 2010-06-28
> **Npl said:**
> I`d prefer if the site just couldn`t crash **the browser or parts of it at all** which should be a reasonable goal for developers. Now isolating external stuff like the flash-plugin I can understand, but trapping **your own code** in isolation (with all the performance penalties of separate processes and communication between them involved) so it doesnt take down the whole program sounds like a lack of self-confidence.

I wonder how the planning for this feature went like... "Guys we can only crash on 1 page at a time, fix that please!"?
This will happen just as soon as a browser developer has complete control over the world's websites...

When the client is running code from the website, the browser can't be held responsible for crashes.  Crashing only one tab is an excellent feature, and one that other browsers are implementing/planning to implement too.

---


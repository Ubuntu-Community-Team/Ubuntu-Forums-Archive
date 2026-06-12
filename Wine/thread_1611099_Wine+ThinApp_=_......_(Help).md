---
title: "Wine+ThinApp = ......?????? (Help)"
date: 2010-11-01
forum: Wine
---

### Post by steven.smith on 2010-11-01
Hey there all! So recently I've been playing around and researching Window's programs that can work on linux. Of course, a long standing tradition is to use Wine and hope to find a program that is compatible, however I was wondering about a few things that I hope someone can clarify, mainly pertaining to ThinApp.

I could go on and on for quite awhile about the things I've read pertaining to ThinApp and Wine and what makes them comparable, however the basic question comes down to:
    "Can I run programs created in ThinApp on Ubuntu using Wine?"
~~~ This of course barring any programs/software that involves special drivers/adapters to properly function.

I haven't had the time yet to try out any virtualized apps on my linux box yet, but I thought I would post it here to see what feedback you all might have :D

So, any and all [relevant] advice is welcome.

---

### Post by cogadh on 2010-11-01
Well, in theory you could. From Wine's perspective, its just another executable like any other, but I would have to guess that you would probably take a significant performance hit, between the virtualization ThinApp is already doing and the "translation" that Wine is doing. The only way to find out for sure is to try it.

---

### Post by steven.smith on 2010-11-01
> **cogadh said:**
> Well, in theory you could. From Wine's perspective, its just another executable like any other, but I would have to guess that you would probably take a significant performance hit, between the virtualization ThinApp is already doing and the "translation" that Wine is doing. The only way to find out for sure is to try it.

Direct and to the point :). I simply don't have the time right now to actually try them out (hopefully over the weekend). I sort of figured that since ThinApp programs run isolated in their environment and saves any registry settings to itself rather than the actual OS, I simply figured that it would work so long as Wine could open it. I'm not sure how resource intensive running both Wine and the App will be, but I can't imagine it being drastically slower, but then again, I haven't tried it yet, so who's to say.

Thought I would ask other people's opinions before actually digging into it.

---

### Post by Refalm on 2010-11-02
Wine has different kind of system files than Windows.
The actual difference between the XP and 7 setting in Wine is a trick, since all the system files just stay the same.

But it could also be a non-issue, since ThinApp picks up all the dll's the application needs anyway.

---

### Post by ggeldorp on 2010-11-02
Unfortunately, currently applications packaged with ThinApp don't work on Wine. One of the APIs that the ThinApp runtime depends upon (NtCreateProcess) isn't supported by Wine.

---

### Post by Quadunit404 on 2010-11-02
> **ggeldorp said:**
> Unfortunately, currently applications packaged with ThinApp don't work on Wine. One of the APIs that the ThinApp runtime depends upon (NtCreateProcess) isn't supported by Wine.

Hmm, and where did you hear that? Because I just checked and VMWare ThinApp apparently works in Wine1.2-RC6 and above.

---

### Post by ggeldorp on 2010-11-02
Which ThinApp version did you use? The problem occurs with 4.5 and 4.6. Versions 4.0.4 and earlier work ok.
I'm a VMware engineer working on ThinApp, we've been looking at this to see how to best solve it.

---

### Post by steven.smith on 2010-11-02
> **Quadunit404 said:**
> Hmm, and where did you hear that? Because I just checked and VMWare ThinApp apparently works in Wine1.2-RC6 and above.

I wasn't really talking about whether the ThinApp program _itself_ works with wine, I was talking about the programs created from ThinApp.


> Unfortunately, currently applications packaged with ThinApp don't work on Wine. One of the APIs that the ThinApp runtime depends upon (NtCreateProcess) isn't supported by Wine.

Does this come from personal experience? Because I don't ever remember seeing anything about a dependency for it; not that I'm saying it can't be true, but I don't recall it ever being mentioned.

---

### Post by ggeldorp on 2010-11-02
> **steven.smith said:**
> I wasn't really talking about whether the ThinApp program _itself_ works with wine, I was talking about the programs created from ThinApp.

The problem I mentioned related to NtCreateProcess is in the ThinApp runtime (which is embedded in the package created by ThinApp), so it affects all programs created using ThinApp. Now, since the ThinApp tools themselves are also packaged using ThinApp, it also affects the tools, but that's just a side-effect. 

> Does this come from personal experience? Because I don't ever remember seeing anything about a dependency for it; not that I'm saying it can't be true, but I don't recall it ever being mentioned.Yeah, last time I tested was about 3 weeks ago with ThinApp 4.6.

---

### Post by steven.smith on 2010-11-03
> Which ThinApp version did you use? The problem occurs with 4.5 and 4.6. Versions 4.0.4 and earlier work ok.
I'm a VMware engineer working on ThinApp, we've been looking at this to see how to best solve it.

I'm a little confused. Are you saying that running the programs _won't_ work; or that there could be some problems doing so?

---


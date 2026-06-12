---
title: "Spread ReactOS?"
date: 2009-08-27
forum: The Cafe
---

### Post by coldReactive on 2009-08-27
Would anyone be interested in helping out with a site similar to Spread Firefox, but for ReactOS?

I would like to see your views on such a thing. This is not a final idea yet.

You can also go to the **#reactos-spread** channel on **irc.freenode.net**

---

### Post by Ozor Mox on 2009-08-27
I don't think ReactOS is considered by its developers to be ready for general use yet. Surely it would be better to wait until then to try and spread the word?

---

### Post by coldReactive on 2009-08-27
> **Ozor Mox said:**
> I don't think ReactOS is considered by its developers to be ready for general use yet. Surely it would be better to wait until then to try and spread the word?

They also need more developers of course.

---

### Post by Ozor Mox on 2009-08-27
> **coldReactive said:**
> They also need more developers of course.

Oh, to get developers not users. In that case, forget what I said :)

---

### Post by decoherence on 2009-08-27
> **coldReactive said:**
> Would anyone be interested in helping out with a site similar to Spread Firefox, but for ReactOS?

I would like to see your views on such a thing. This is not a final idea yet.

You can also go to the **#reactos-spread** channel on **irc.freenode.net**

What would the target audience be? When the Spread Firefox campaign kicked off, Firefox was a nice, usable alternative to MSIE.

I haven't used ReactOS in a dog's age. In its current state, is it a usable alternative to Windows? If not, who do you plan on targeting the campaign at?

At the very least, you've got me interested enough to give it another try! (perhaps I've answered my own question, then?)

cheers,

---

### Post by coldReactive on 2009-08-27
> **decoherence said:**
> What would the target audience be? When the Spread Firefox campaign kicked off, Firefox was a nice, usable alternative to MSIE.

I haven't used ReactOS in a dog's age. In its current state, is it a usable alternative to Windows? If not, who do you plan on targeting the campaign at?

At the very least, you've got me interested enough to give it another try! (perhaps I've answered my own question, then?)

cheers,

When did you last use it?

---

### Post by fatality_uk on 2009-08-27
> **coldReactive said:**
> Would anyone be interested in helping out with a site similar to Spread Firefox, but for ReactOS?

I would like to see your views on such a thing. This is not a final idea yet.

You can also go to the **#reactos-spread** channel on **irc.freenode.net**

Not really. It's running to stand still. If it ever got anywhere near a beta I might take another look, but for now, I have way too many other things in my life and too little time.

---

### Post by decoherence on 2009-08-27
> **coldReactive said:**
> When did you last use it?

years ago. Before they did that big audit.

I'm installing it on a VM now...

---

### Post by BackwardsDown on 2009-08-27
> **decoherence said:**
> years ago. Before they did that big audit.

I'm installing it on a VM now...

To get you up to date:
It does not crash every 10 minutes anymore.
Firefox 2.0 is pretty stable, Firefox 3.0 is not. Mirc runs perfectly. I have found that not many apps are running well. But its getting better.

With the next version of ReactOS you should be able to browse pretty stable with the latest Firefox. They also want to work heavily on Visual Studio.

---

### Post by decoherence on 2009-08-27
> **BackwardsDown said:**
> To get you up to date:
It does not crash every 10 minutes anymore.
Firefox 2.0 is pretty stable, Firefox 3.0 is not. Mirc runs perfectly. I have found that not many apps are running well. But its getting better.

With the next version of ReactOS you should be able to browse pretty stable with the latest Firefox. They also want to work heavily on Visual Studio.

Here I am, posting from FF2 in ReactOS. It seems fine to me! It installed in about 40 seconds. The "Download!" program is a very nice addition. Much more impressive than last time I used it!

I'm going to see how far I can push it before it breaks. I'll start with the Netware client.... (evil laughter)

Thanks for reminding me of this interesting project!

---

### Post by aaaantoine on 2009-08-27
If it were more stable, I would probably be using ReactOS over standard Linux because of my dependence (or preference) for many Windows applications.  So it's good to hear that the project is making progress.

That is to say, if there were a GPL'ed NT operating system that worked as well as (or almost as well as) Windows, I would be using it.

(Disclaimer: My opinion on this matter changes from time to time.)

---

### Post by decoherence on 2009-08-27
One quick question.... how does networking work? Nothing appears under My Network and if I type \\server\share, again nothing happens.

thanks!

---

### Post by phrostbyte on 2009-08-27
ReactOS will run Windows app perfectly when Wine runs Windows apps perfectly (except for drivers and driver-focused applications). Both projects share a lot of code. 

Wine is basically trying to recreate Windows as well, but their "kernel" is just a thin layer above a host OS. They aren't trying to perfectly recreate kernel-space APIs. 

ReactOS is trying to fully create the Windows kernel, so they need all kinds of subsystems that needed in Wine, which means it's a lot more effort involved.

In addition, there are efforts (from the Chinese government?) to integrate Windows-like kernel subsystems into Linux, and this also shares/uses code from ReactOS and Wine:
[http://en.wikipedia.org/wiki/Linux_Unified_Kernel](http://en.wikipedia.org/wiki/Linux_Unified_Kernel), in theory, an OS uses LUK could use both Windows and Linux drivers at the same time.


I'd like to also add that all these projects are MASSIVE. The amount of effort creating an entire OS from scratch is very very very very different from the effort trying to write a music player from scratch, for instance. The Linux kernel (and it's only a KERNEL!) has over 1000+ developers.

---

### Post by coldReactive on 2009-08-27
> **decoherence said:**
> One quick question.... how does networking work? Nothing appears under My Network and if I type \\server\share, again nothing happens.

thanks!

Should ask those questions on the forum or in #reactos on irc.freenode.net. Most developers for ReactOS don't even look at its own forum.

---


---
title: "Matters approaching"
date: 2014-05-07
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2014-05-07
Mark Shuttleworth to technical-board:
[https://lists.ubuntu.com/archives/technical-board/2014-March/001852.html](https://lists.ubuntu.com/archives/technical-board/2014-March/001852.html)

so far only Stéphane Graber replied.

What do you think ?


For me, I will like an more secure, read only system for the base, and some lxc, docker approaches to do anything else.

---

### Post by grahammechanical on 2014-05-07
As so often happens I do not understand much of what is going on but as I have followed, from afar, the development of Ubuntu phones/tablets and thought about convergence I can see that there comes a point where something has to give. The way things are done on the desktop has to give way to the methods of Ubuntu phone. Or at least become part of a "developer mode" of operation for the desktop.

I am thinking of things like the terminal. In Linux there are no end of ways in which users can mess up the user environment. Imagine someone buying a Ubuntu tablet and then using the terminal to download some theme from who knows where, which then breaks the UI. And then the user demands a refund. Retailers are not going to like that. And Ubuntu gets the blame for being unstable.

How many times have I seen in posts on this forum similar words to these: "Ubuntu broke Windows." No. The user made the wrong choice and overwrote the Windows partition. But the user blames Ubuntu. So, I will not be surprised to find my Ubuntu tablet (if I buy one) tightly locked down. And I will not complain. But others will. Some will want to put Linux Mint on their phones and then wonder why the phone no longer works as a phone and is impossible to use a laptop. "But I thought Linux Mint was built on Ubuntu." They will cry.

Regards.

---

### Post by cariboo on 2014-05-07
Android and IOS based tablets are already locked down, you have to root them in order do anything that is not strictly enabled in the operating system. I can't remember the reason why, but I had to edit the hosts file on my Asus tablet, it took about an hours research before I was confident that I could root the tablet without affecting the rest of the system. I can see the same sort of thing happening if we go to an image based system for the desktop.

I can see similar things happening if this comes about, the unfortunate thing is that not all hardware is supported out of the box, and there needs to be some way for the user to work around these problems. The other thing I can see is that a very narrow range of hardware will be supported,  causing the enthusiast user to wander off to other distros.

---

### Post by ventrical on 2014-05-07
My own personal view is that the cart is before the horse. We have been asked to test Mir which more or less is one of the catalysts of this convergence process and yet we barely have a workable  patch in place that gives us anything to bite into (at least at the desktop level). <we can run a few test and make some compares> 

> 
As so often happens I do not understand much of what is going on but as I  have followed, from afar, the development of Ubuntu phones/tablets and  thought about convergence I can see that there comes a point where  something has to give. The way things are done on the desktop has to  give way to the methods of Ubuntu phone. Or at least become part of a  "developer mode" of operation for the desktop.


> 
I can see similar things happening if this comes about, the unfortunate  thing is that not all hardware is supported out of the box, and there  needs to be some way for the user to work around these problems. The  other thing I can see is that a very narrow range of hardware will be  supported,  causing the enthusiast user to wander off to other distros.         


  It  injects a brand of mayhem into the project as a whole when trying to mate apples with oranges. I know it is too late for should-a, could-a , woulda-s but  mir  should be the matter *current* because, from what I undestand, if we do not have Mir in the right set we do not have any semblance of convergence . We have divergence and disunity . A lot of hardware gets laid waste by the roadside.

  I am not saying to change horses in mid stream, I am just saying that we have to get the horse pointed in the right direction and keep him on the path. Convergence will happen naturally after that.

Regards..

---

### Post by cariboo on 2014-05-07
Mir is a work in progress, we're pretty early into the development cycle, and there is lots of time to get mir+unity8 working properly on most systems before it becomes the default DE in 16.04, in other words, patience grasshopper. :) :) :)

---

### Post by grahammechanical on 2014-05-07
From my eavesdropping of web chats this much is clear to me that Mir and Unity 8 go together and convergence cannot happen without those two pieces. Unity 8 is different code to unity 7. It is not simply an upgrade.

There clearly will be issues with proprietary video drivers. A lot will depend on how well open source video drivers compare with proprietary video drivers. I guess that Canonical may have to invest in open source driver development. Now, I begin to worry how well Canonical patches will be received by upstream developers. I see a hint in something that Mark Shuttleworth said that Canonical could start to become an upstream itself. And if Ubuntu phones/tablets do indeed bring money into Canonical coffers then that will make this a possibility. Money = paid developers = quality code in shortest time.

---

### Post by ventrical on 2014-05-07
> **grahammechanical said:**
> From my eavesdropping of web chats this much is clear to me that Mir and Unity 8 go together and convergence cannot happen without those two pieces. Unity 8 is different code to unity 7. It is not simply an upgrade.

There clearly will be issues with proprietary video drivers. A lot will depend on how well open source video drivers compare with proprietary video drivers. I guess that Canonical may have to invest in open source driver development. Now, I begin to worry how well Canonical patches will be received by upstream developers. I see a hint in something that Mark Shuttleworth said that Canonical could start to become an upstream itself. And if Ubuntu phones/tablets do indeed bring money into Canonical coffers then that will make this a possibility. Money = paid developers = quality code in shortest time.


 I have to ask this question then. Is there a paid version of Ubuntu Trusty etc.. for the desktop and if so , why is Canonical not marketing it? (I know there is paid support. I'm talking about paid version of OS or is that inclusive with support?)

---

### Post by ventrical on 2014-05-07
> **cariboo907 said:**
> Mir is a work in progress, we're pretty early into the development cycle, and there is lots of time to get mir+unity8 working properly on most systems before it becomes the default DE in 16.04, in other words, patience grasshopper. :) :) :)

Yes master. :) But Sen Cariboo... were we not supposed to have Mir by now? :) Does not Sen Dragonworth keep rolling up the foo foo switch on Mir? Master , I am confused.. :)

---

### Post by cariboo on 2014-05-07
Mir might be progressing, but here is more to it than just the Mir package. There is a lot of underlying code that needs to be updated, created. We will be notified when they devs feel good enough about the software to allow us to try and break it.

---

### Post by anca-emanuel on 2014-06-18
[http://lwn.net/Articles/602579/](http://lwn.net/Articles/602579/)

[http://0pointer.de/blog/projects/stateless.html](http://0pointer.de/blog/projects/stateless.html)

---


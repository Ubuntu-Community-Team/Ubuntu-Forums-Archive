---
title: "Rolling your own distro: current tools?"
date: 2022-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by schwim-dandy on 2022-06-07
Hello there everyone!

I've been reading a lot about rolling your own Ubuntu distro and I keep running across documents, wiki entries and links that are no longer relevant.  As an example,[ this wiki page]("https://wiki.ubuntu.com/DerivativeDistroHowto") states that I should use the [Ubu Customization Kit]("http://uck.sourceforge.net/") or [Remastersys]("http://www.remastersys.org/").  The first points towards an abandoned project and the second points towards a Microsoft powered media/news outlet.  I just feel like I'm investing hours in learning about options that are no longer relevant.

What do people use currently for packaging an Ubuntu-based flavor?  In particular, this will be a minimal server install with Openbox on top. 

Thanks for your time!

---

### Post by deadflowr on 2022-06-07
I've never used it, but I have heard great things about cubic: [https://launchpad.net/~cubic-wizard/+archive/ubuntu/release]("https://launchpad.net/~cubic-wizard/+archive/ubuntu/release")

---

### Post by schwim-dandy on 2022-06-07
> **deadflowr said:**
> I've never used it, but I have heard great things about cubic: [https://launchpad.net/~cubic-wizard/+archive/ubuntu/release](https://launchpad.net/~cubic-wizard/+archive/ubuntu/release)

That looks to be exactly what I need, thanks so much for sharing the link!

---

### Post by guiverc on 2022-06-07
> **schwim-dandy said:**
> What do people use currently for packaging an Ubuntu-based flavor? 


[Ubuntu *flavors*]("https://ubuntu.com/download/flavours") are created by Ubuntu infrastructure with all details existing on launchpad. If I needed to re-spin a *daily* ISO for a *flavor* I'm involved with, I'd login to a Ubuntu site & click a button (*that's visible for product managers* *when signed in*) and a new *daily* ISO would start being generated.  Ubuntu *flavors* have the advantage over *respins* in that we don't generate our own ISOs.

If I wanted to create an ISO myself, and wasn't able to use the Ubuntu/launchpad infrastructure; I'd likely read a *blog* from someone who did it. What comes to mind is likely too old, but I recall what Jacque Montague Raymer (*creator of Makulu Linu*x) blogged about, creating all he wanted on a system then running a script that created the ISO (*he released as Makulu Linux*) from that install. Jacque's blogged that the script he used wasn't new, where he got it from, why he made the changes he did & advantages/disadvantages over other methods etc.  The blogs I'm thinking of were years ago now (*when Makulu switched from its earlier Debian based to a Ubuntu one*) so maybe too old, but I'm using that as example.

I'll add this link where I cover some of what I've written about here, but it also has some other links that maybe useful - [https://askubuntu.com/questions/1393901/tools-for-creating-a-custom-linux-os-based-on-ubuntu](https://askubuntu.com/questions/1393901/tools-for-creating-a-custom-linux-os-based-on-ubuntu)

---

### Post by schwim-dandy on 2022-06-08
> **guiverc said:**
> [Ubuntu *flavors*]("https://ubuntu.com/download/flavours") are created by Ubuntu infrastructure with all details existing on launchpad. If I needed to re-spin a *daily* ISO for a *flavor* I'm involved with, I'd login to a Ubuntu site & click a button (*that's visible for product managers* *when signed in*) and a new *daily* ISO would start being generated.  Ubuntu *flavors* have the advantage over *respins* in that we don't generate our own ISOs.

If I wanted to create an ISO myself, and wasn't able to use the Ubuntu/launchpad infrastructure; I'd likely read a *blog* from someone who did it. What comes to mind is likely too old, but I recall what Jacque Montague Raymer (*creator of Makulu Linu*x) blogged about, creating all he wanted on a system then running a script that created the ISO (*he released as Makulu Linux*) from that install. Jacque's blogged that the script he used wasn't new, where he got it from, why he made the changes he did & advantages/disadvantages over other methods etc.  The blogs I'm thinking of were years ago now (*when Makulu switched from its earlier Debian based to a Ubuntu one*) so maybe too old, but I'm using that as example.

I'll add this link where I cover some of what I've written about here, but it also has some other links that maybe useful - [https://askubuntu.com/questions/1393901/tools-for-creating-a-custom-linux-os-based-on-ubuntu](https://askubuntu.com/questions/1393901/tools-for-creating-a-custom-linux-os-based-on-ubuntu)

Thanks very much for the information and link.  I'm slowly figuring out what I need to do to prepare for the process.

---


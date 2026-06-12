---
title: "Ubuntu Enterprise Cloud"
date: 2009-12-12
forum: Server Platforms
---

### Post by schmildo on 2009-12-12
I am having alot of problems trying to find out what "Ubuntu Enterprise Cloud" actually is.
I've searched ubuntu server's site, google, googlevideos,youtube... and all I get is marketing terminology.

[http://www.ubuntu.com/cloud](http://www.ubuntu.com/cloud)

"Private ***clouds*** offer ***immediacy*** and ***elasticity*** in your own IT infrastructure. Using ***Ubuntu Enterprise Cloud***, you can experience the benefits of ***cloud computing*** behind your firewall. Deploy ***workloads*** and have them running immediately. ***Grow*** or ***shrink*** ***computing capacity*** to meet the needs of your application."

I keep finding benifits of 'cloud computing', and not implementation details. Given sufficent time, I could demonstrate the benifits of vegemite were identical to cloud computing, but the purpose and usage of these two products is very different.

As an example of one cloud application, I had a look around and found out about 'Ubuntu One', and, after seeing more marketing talk I discovered it to be a simple fire sharing application, where the files are stored on a remote server, but syncronised with whatever machine you load the client application onto. (and also has a web interface)

If someone could possibly explain to me the technical side of "Ubuntu Enterprise Cloud" I'd be relieved... and indeed very happy if someone could contact the administrator of the ubuntu server website, and ask them to explain what it is on the site. It seems unreasonable to make such a huge change, and not explain the concepts behind *this implementation* of 'cloud computing'. 


I'm I.T savvy, truly I am, which is why i'm so incredibly frustrated that I've spent this much time researching this, and still not been able to get the details. LOL!

Is it just me? Did I miss that memo? Did I fail to submit my TPS report?!

Thanks, 
Tim.

---

### Post by bnight on 2009-12-12
Hello,

Baisicly Ubuntu Cloud is based on eucalyptus and kvm to provide Technology like Amazon CS2 cloud but for free. 

I personally think that this is great but i don`t have success in building Ubuntu cloud. 

Even that I have a lot of exparience with virtualization and cloud computing.

For me this Ubuntu cloud don`t work at all.

So you don`t have to waste your time and try to makeing it work.

---

### Post by tgalati4 on 2009-12-12
I want my red stapler back.

Cloud computing is a buzz word to get IT departments to spend money.

---

### Post by craigp84 on 2009-12-12
tgalati4 is being relocated to the basement for his insolence! :)

Ubuntu Enterprise Cloud isn't a product, it's a meta product. It describes the case where you may choose to use a couple of software products (eucalyptus, kvm)  to create a private / internal version of what's available at amazon and various other vendors.

Cloud computing (like Service Oriented Architectures before it) has been latched onto by the marketing bods. If find the best approach is just to avoid the term and talk about the actual technologies underlying the idea -- techies will follow what you're talking about much more easily!

When you run across a blank stare in the course of talking about VM instances and the like just say "cloud computing" and watch that vacant stare be replaced by a smile -- the blank stare wasn't a techie, he was management, and now you've just appeased him :-)

---

### Post by munky99999 on 2009-12-12
Ok the issue with IT is that we have massively powerful hardware these days. That 9/10 people arent going to utilize it.

Cloud computing is essentially the ability to do virtualization on your server but your ideal is to set it up so you have MANY virtuals running on 1 hardware. Many of them sharing the same hardware. That's virtualization. Where you move into the cloud is when you have more then 1 computer working together. Though generally you still have many virtuals running on each hardware.

Where eucalyptus and UEC comes in. They are basically giving you the basis of the cloud of having many nodes working together.

The new and cool thing is the implementation of Rocks linux beowulf clustering tech into the mix.

This means I can have a virtual which can use many nodes for myself. While also being able to associate the couple of users who dont need any power. 


So for example. I could get 10 computers with 128gigs ram each. With 4 quad core xeons each. So basically 160 cores in my cloud.

I setup a thinclient at everyone's desk. which uses the network to communicate. Then lets say I have 50 people who are going to use this cloud.

-The secretaries who play solitaire all day can easily survive with 1 core and 2 gigs ram.
-The database/accounting fellas could use 4 cores and 4 gigs ram lets say.
-The programmers could use 8 cores and 12 gigs ram
-The graphics rendering people need the most they can get. Say we have only 2 instances where they need to render. After all the above we might still have 80 cores left. Thanks to rocks linux. UEC should be able to give 40 cores to each instance. Instead of the max of 16 cores due to hardware limits.


That kind of flexibility is very powerful.

---

### Post by Druke on 2009-12-12
I find [this]("https://help.ubuntu.com/9.10/serverguide/C/eucalyptus.html") to be a helpful guide on what it is, but [this]("https://help.ubuntu.com/community/Eucalyptus") is a helpful guide on how to make it work.

Basically a really spiffy KVM server.

---

### Post by tgalati4 on 2009-12-13
I have finished rearranging my office in the basement.  Can I have my cake please?

Some useful links.

---

### Post by Druke on 2009-12-13
?

---


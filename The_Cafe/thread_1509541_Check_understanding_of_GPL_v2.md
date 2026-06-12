---
title: "Check understanding of GPL v2"
date: 2010-06-14
forum: The Cafe
---

### Post by weezer316 on 2010-06-14
Hi,

Possibly not the place for this but here goes anyway. Cant find anywhere else on the web to post it that might get an answer.

We, namely my company, are looking at using a peice of software called OpenKM for our Content management system. This is a web based CMS and rally is quite good. However, we also sell content, being the content being heaps of word docs, spreadsheet, clinical procedures etc for dental practices at the moment via a customer designed peice of software.

What we want to do is start delivering this content over the web using this OpenKM, and charging people for access to the content. We wouldnt be selling copies of OpenKM (its open source) rather hosting and running it ourselves but charging for access to the content. Software as a service (SaaS) i believe its called.

Now, under version2 of the GPL is this allowed? To the best of my knowledge it is. Im trying to make sure though befire we go ahead!

Any ones thoughts would be appreciated.

Weezer

---

### Post by Bachstelze on 2010-06-14
If you want to be absolutely sure, consult a lawyer, or ask the FSF directly. I'd say yes, but don't blame me if it is in fact not allowed. :p

---

### Post by NCLI on 2010-06-14
I'm 99% certain that's a yes. AFAIK, you could even sell OpenKM if you wanted to, as long as you allow users to download the source for free, and update the source if you make any alterations to the code.

---

### Post by weezer316 on 2010-06-14
I asked the FSF, they want $150 for 30 mins consultation as we are a commercial organization.

Im trying to think of examples of such a thing but I cant. Any ideas who does something similair? Thinking remote assistance tools......

---

### Post by mickie.kext on 2010-06-14
> **weezer316 said:**
> Hi,

Possibly not the place for this but here goes anyway. Cant find anywhere else on the web to post it that might get an answer.

We, namely my company, are looking at using a peice of software called OpenKM for our Content management system. This is a web based CMS and rally is quite good. However, we also sell content, being the content being heaps of word docs, spreadsheet, clinical procedures etc for dental practices at the moment via a customer designed peice of software.

What we want to do is start delivering this content over the web using this OpenKM, and charging people for access to the content. We wouldnt be selling copies of OpenKM (its open source) rather hosting and running it ourselves but charging for access to the content. Software as a service (SaaS) i believe its called.

Now, under version2 of the GPL is this allowed? To the best of my knowledge it is. Im trying to make sure though befire we go ahead!

Any ones thoughts would be appreciated.

Weezer

**Yes this is 100% allowed.** In fact I have implemented that kind of solution couple of times for customers. 

Some more information: 

Note that under General Public License (as opposed to Afero General Public License), SaaS does not count as distribution or conveying, so by implementing CMS you actually do not distribute software at all and you do not need to opensource anything. It is counted as in-house usage, and you are not bound by GPL at all. GPL only apply to distribution. Also, distribution around your organisation does not count. Only to outside world. 

That said, if you do some fine in house development, it would be nice to contribute it back to OpenKM project.

---

### Post by weezer316 on 2010-06-14
Mickie,

Of course I would share any stuff I implement on my own, but to be honest its unlikey, where we released those changes for our public CMS or not. I was however terrified I would be breaking the GPL.

Have you got an example of this Mickie? Would be handy to show y boss to calm his nerves!

And thanks!

Wheeler

---

### Post by jwbrase on 2010-06-14
> **weezer316 said:**
> Hi,

Possibly not the place for this but here goes anyway. Cant find anywhere else on the web to post it that might get an answer.

We, namely my company, are looking at using a peice of software called OpenKM for our Content management system. This is a web based CMS and rally is quite good. However, we also sell content, being the content being heaps of word docs, spreadsheet, clinical procedures etc for dental practices at the moment via a customer designed peice of software.

What we want to do is start delivering this content over the web using this OpenKM, and charging people for access to the content. We wouldnt be selling copies of OpenKM (its open source) rather hosting and running it ourselves but charging for access to the content. Software as a service (SaaS) i believe its called.

Now, under version2 of the GPL is this allowed? To the best of my knowledge it is. Im trying to make sure though befire we go ahead!

Any ones thoughts would be appreciated.

Weezer

The GPL does not restrict how you may use GPLed software. All it does is say that you may not distribute GPLed software or derivative works of GPLed software under a license that gives the end user less rights than the GPL does, and that you may not distribute GPLed software or derivative works without making the source code available if the user wants it. So as long as you aren't distributing binaries or source code to OpenKM (or other GPLed software), you don't have to worry about the GPL.

---

### Post by mickie.kext on 2010-06-14
> **weezer316 said:**
> Mickie,

Of course I would share any stuff I implement on my own, but to be honest its unlikey, where we released those changes for our public CMS or not. I was however terrified I would be breaking the GPL.

Have you got an example of this Mickie? Would be handy to show y boss to calm his nerves!

And thanks!

Wheeler

Unfortunately, I can't give you an example because it was CRM solution (SugarCRM to be exact) so you have to be a customer to have access and see how it works. 

But for example, you could search for [Drupal sites]("http://www.lullabot.com/articles/is-site-running-drupal"). Drupal is another GPLv2 CMS and you basicaly need to find any site ruining drupal and selling something for an example.

If your boss is still itchy, then you can see for [OpenKM]("http://www.openkm.com/Professional-Support.html")'s professional support. If you buy support for their product, then they have to dispel any legal uncertainty. If you later find that their support is not needed for you, then you can dump it and keep using the program.

---

### Post by LeifAndersen on 2010-06-14
Also, check out anyone who's using a Wordpress based website.  Those are using GPL if I remember, and they're not violating it (I hope anyway, my blog [http://leifandersen.net](http://leifandersen.net) uses wordpress, than again, I haven't actually made any money off of it).

---

### Post by grahammechanical on 2010-06-14
You can read the license for yourself at [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)  Version 3 is on that page. Go to old licenses to see version 2 and version 1. It all seems clearly written.

regards

---

### Post by nikhilbhardwaj on 2010-06-14
> **grahammechanical said:**
> You can read the license for yourself at [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)  Version 3 is on that page. Go to old licenses to see version 2 and version 1. It all seems clearly written.

lol
in my view the gpl is the only thing complicated about linux and open source in general

---

### Post by weezer316 on 2010-06-14
Clearly written liscence? You are having a laugh surely!

My brain melts reading through it. Im afraid it may dribble out my ear when i go to bed.

Thanks for your answers though, much appreciated.

---


---
title: "Do modifications to software under the Open Source Initiative have to be released"
date: 2011-06-09
forum: The Cafe
---

### Post by rflook on 2011-06-09
Im really hoping someone knows the answer to this as havent had any luck from the OSI. Im currently delivering a high school qualification in the UK and part of the course is on open source. We have just had an examination paper with a question on what are the disadvantages of using open source software to create a restaurant booking system. 

One of the model answers says that the restaurant would have to then release their changes to the public. As I understand it the GNU licences do not require this, if you want to keep your work private then so be it. But I cant seem to find out whether this also holds true for the OSI side of things. Their definition on their website doesnt really say either way. 

Id be incredibly grateful if anyone could give me some guidance on this

---

### Post by Joe of loath on 2011-06-09
Any products derived from the GPL require to be released under an equivalent license. There are, however, permissive licenses available, like the BSD and MIT licenses. They allow derivative works to be closed source.

---

### Post by Barrucadu on 2011-06-09
If the restaurant distributed the binaries, they would also have to make the source available. However, if they did not distribute the binaries they have no obligation to provide the source (as far as I understand it)

---

### Post by tgalati4 on 2011-06-09
A bigger issue is patent encumberance which leads to future lawsuits.

---

### Post by Mr. Picklesworth on 2011-06-09
> **Barrucadu said:**
> If the restaurant distributed the binaries, they would also have to make the source available. However, if they did not distribute the binaries they have no obligation to provide the source (as far as I understand it)

If I'm not mistaken, I believe the root of this with the GPL is that everyone who has the binary is entitled to the source under the same license. Other licenses are different, naturally. Not sure I can think of a disadvantage for open source in general, unless there is a little more information&#8230;

---

### Post by forrestcupp on 2011-06-09
It seems like most of your answers are from the viewpoint of the GPL and the Free Software Foundation. The OP made it clear that he understands that according to the GPL, you don't have to release changes unless you distribute them. He's asking about the OSI, which is different from the FSF.

I think the answer is that there are a lot of licenses that are compatible with the OSI, and it just depends on what license you are using. But I can say that one of the main differences in philosophy between open source and free software is that open source is about working together to not reinvent the wheel, and free software is more about freedom of rights.

---

### Post by earthpigg on 2011-06-09
I believe this:

> One of the model answers says that the restaurant would have to then release their changes to the public.

Is an incorrect answer. If the restaurant is not distributing the software outside of the restaurant, it does not have to release the corresponding source code.

If it is only available on company-owned machines, then the source code ought to be available to users of those company-owned machines on those company-owned machines.

There is no requirement that employees using those company-owned machines be allowed to send personal email from that computer or put a thumb drive in that computer or do anything with that computer aside from their job - which is, presumably, not programming.

> But I cant seem to find out whether this also holds true for the OSI side of things. Their definition on their website doesnt really say either way. 

OSI says this:

> Open source doesn't just mean access to the source code. The distribution terms of open-source software must comply with the following criteria:

(criteria here)

But then it goes on to say this:
> The following licenses have been approved by the OSI via the License Review Process.
...
[LIST]
[*]GNU Affero General Public License v3 (AGPL-3.0)
[*]GNU General Public License version 2.0 (GPL-2.0)
[*]GNU General Public License version 3.0 (GPL-3.0)
[*]GNU Library or "Lesser" General Public License version 2.1 (LGPL-2.1)
[*]GNU Library or "Lesser" General Public License version 3.0 (LGPL-3.0)
[/LIST]

The conclusion I draw is that while the OSI would *prefer* that the restaurant release their changes (for many good reasons, many of which would *benefit the restaurant*), the restaurant is nonetheless not required to do so. 

That just means that the restaurant probably wouldn't be given permission to put an OSI logo on their storefront. Nonetheless, the software used in the restaurant would remain Free and Open Source Software. They could generate their own logo with the subtext "We Use Free and Open Source Software" associated with it -- IIRC, neither the term "Free Software" nor "Open Source Software" is trademarked or copyrighted in any way.

Kind of like how I can sell beef and say it was "grown humanely, with a cow that was free to wander where he felt, and without injecting steroids" and I can make up my own logo to go along with that, but cannot necessarily use the "organic" or "natural" claim unless I meet a certain set of very specific requirements associated with certain trademarked and/or gov't regulated logos.

---

### Post by earthpigg on 2011-06-09
EDIT: Removed what became rough draft of blog post, replacing with what the blog post ended up being. Click [here]("http://ctmason.wordpress.com/2011/06/09/the-greedy-restaurant-shares-software-improvements-with-other-restaurants/") if you want to read it with nitty-gritty formatting intact. In keeping true to my promise to myself not to have *another* Ubuntu or Linux blog, no mention of either was made. :) I think write-ups like this have some value because they apply purely to greed to compel someone to act... well, to act as I want them to act because they want to act that way. General Eisenhower would be proud of me.

Feel free to tear this to shreds if I made any errors in logic or rationale. Blog post begins....


I recently came across a question asked by a high school student in the United Kingdom. One of his teachers had asked a question that seemed to imply that needing to share improvements to open source restaurant reservation software with the open source project that created the software was a disadvantage of using open source software.

>     Im currently delivering a high school qualification in the UK and part of the course is on open source. We have just had an examination paper with a question on what are the disadvantages of using open source software to create a restaurant booking system.

    One of the model answers says that the restaurant would have to then release their changes to the public.

For some reason, the fact that this was a **model answer** bothers me, because that implies that this answer is something the student should *strive to emulate to receive a good grade*. As if that answer could possibly be part of a coherent answer that makes any reasonable attempt to take the full implications of open source economics into consideration.

So, let us examine the many ways in which sharing code improvements with &#8220;the public&#8221; for $0.00 is to the advantage of the individual restaurant. Each of the below points could easily be expanded to be an essay unto itself, but I shall endeavor to be brief. We will start by examining a few ways in which it has no negative effect on the individual restaurant because it almost certainly isn&#8217;t going to help the competition. Then, we will look at how it will help the restaurant.

Sharing Hurts Nothing.

To begin with, their food and customer service will never be identical to another restaurant &#8211; a streamlined reservation system does not change the attire or politeness of staff, nor the amount of curry in the food. Restaurants supply a heterogeneous product, and that product ain&#8217;t software.

Furthermore, the software would not even necessarily work for any other restaurant unless it was using an identical software stack minus these trivial modifications.

Thirdly, restaurants outside that city or county are not competitors. If one restaurant in several cities or counties use, improve, and share the software then each of these restaurants will benefit at the expense of all other restaurants in their respective cities. Unless the software becomes ubiquitous, odds are the small number of restaurants adopting the software will be from different cities &#8212; located in different markets.

Sharing Has Many Benefits.

It is in each individual restaurant&#8217;s best interests to submit the improvements upstream so that each time a new version of the software comes out, they can benefit from all of the other improvements without the need to re-patch the new version of the software with the stuff they wrote. It is far more efficient and streamlined to allocate resources towards working as part of the wider team than to allocate all of the resources that would be needed to maintain internal patches and revision control.

If a single competing restaurant in the given city does use the improved software, then it will still be in that other restaurant&#8217;s best interests to share-alike as well any improvements they make (or bug reports, or even feature requests) &#8212; so the two restaurants in the same city (eg, market) using this software can both share a comparative advantage over the other n restaurants in town.

Finally, explicit costs of sharing code improvements upstream (eg, &#8220;to the public&#8221;) are nil as the IT guy that is familiar with Open Source and can do a bit of coding is already assumed to be an employee in the scenario created by the question, and the Marginal Benefit of releasing modified source code back is almost certainly going to exceed Marginal Cost. If there is one thing drilled into the head of any student of economics, it is that if MB > MC &#8211; you move forward and do it. Period, and end of story.

So, clearly, it is not a disadvantage for a restaurant to share improvements made to the software &#8220;with the public&#8221;. They will not be getting any direct revenue for this software, but they will be getting additional indirect revenue through the continuous improvement in their critical customer service infrastructure that this is a key contributor to. The restaurant should not contribute code improvements upstream to be nice or to be communists, they should share this stuff for $0.00 to be greedy rational self-interested business people trying to make as much money as humanly possible.

---


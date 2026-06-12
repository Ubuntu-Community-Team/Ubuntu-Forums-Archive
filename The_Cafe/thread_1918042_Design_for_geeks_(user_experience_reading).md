---
title: "Design for geeks (user experience reading)"
date: 2012-01-31
forum: The Cafe
---

### Post by keithpeter on 2012-01-31
Hello All

[http://www.randsinrepose.com/archives/2012/01/16/a_design_primer_for_engineers.html](http://www.randsinrepose.com/archives/2012/01/16/a_design_primer_for_engineers.html)

Quite funny article with some suggested reading about the role of 'design' in programming. 

I'm trying to *understand* the GNU/Linux world's move to a 'designed user experience' (Unity, Gmome Shell) as opposed to the random bricolage that has got us through the last 20 years.

**Anyone got any references on 'user anthropology' which appears to be the latest thing?**

I'm rereading Jef Raskin's *The Humane Interface* at present, and have started to hack my way through Cooper's *About Face*.

Please note: I use Gnome Shell and Unity on 12.04 on a daily basis, and I'm not interested in why you don't like them, why you don't agree with 'design', why you think Canonical has got it wrong &c :twisted:

I'm after information and resources here.

---

### Post by grahammechanical on 2012-01-31
It is the market place that is bringing this change.

Every year for years someone would say: "This is the year for Linux on the desktop." It hasn't happened. But something else has happened.

People are buying computer devices that they do not know are computers. And they do not care about the OS. They are buying on looks, functionality, and what it seems everyone else is buying.

There may have been good philanthropic principles behind the establishment of Ubuntu but there also needs to be good commercial principles as the foundation of Canonical.

Besides, it looks good. It is commercialism. It keeps the money 'go-round' going around.

Regards.

---

### Post by keithpeter on 2012-01-31
Hello grahammechanical

I suspect you are right.

I'm trying to understand how those imperatives translate into code.

And how they change the 'bazaar' model (developer owns project) of foss development.

---

### Post by rg4w on 2012-01-31
Thanks for the link.  One of the best articles I've read in a while.

The whole usability/design/engineering mashup is indeed a challenge in the FOSS world, because good design is an expensive process and it's often difficult to pay for it when the product is given away for free (yes, I know the difference between gratis and libre, but I also know that it doesn't matter as long as gratis is always just a make file away).

With OSes like Ubuntu, the challenge is that we want to appeal to the average person, but the average person has no interest in replacing the OS that came with their computer with something they downloaded off the Internet.  That's the stuff of geekdom, so we find ourselves in a netherworld in which we want to see the OS "cross the chasm" (in the Moore sense) to appeal to a broader, more gentrified audience, but truth be told that audience simply doesn't exist for an OS that wasn't pre-installed on the computer that gentrified audience purchased.

Until the average person can walk into Best Buy and purchase a computer with Ubuntu on it, Ubuntu will never exist as a mass-market product.  It simply isn't a whole product by itself, since it needs a computer to use it.

To get the attention of OEMS, "free" in either sense isn't much of a feature.  So instead, Ubuntu is differentiating itself through design initiatives which may be somewhat controversial (Unity, HUD) but one thing about them is unquestionable:  they get people's attention.  When was the last time BBC wrote about the Linux kernal?  They recently wrote about the HUD.

So on the "let's get some attention" level the current trajectory is working.  The question is now about the efficacy of such designs.

Apple sells a whole-product solution, OS + computer.  But IMO they've been successful for the very reasons the article you cited points out:  there's a strong drive at all levels of the company to integrate the design process across all aspects of operations.

But that alone isn't enough.  And it's not enough to be merely different.   What distinguishes Apple's design work is that it's usually very good.

Good doesn't come cheap.  For every design we see from Apple, many dozens were tried and discarded.  Making multiple versions of solutions to hone in on the most effective one costs a lot more than just making one and hoping it's the best one.

In such trial-and-error, there must be a willingness to accept outcomes that may be quite different from initial goals.

For example, Steve Jobs initially felt that it was very important that the iPhone include only apps that Apple made.  Scott Forstall eventually managed to convince him to try opening it up for third-party developers; worked out rather well, but its success relied on the initial decision maker being flexible and open to new ideas, willing to let them override even closely-held ones like Jobs' infamous fetish for closed systems.

With design, one way to make a compelling case is to gather good data from testing different prototypes.  But who has the time/budget to make everything at least twice?

Paper prototyping can help with some of that, and Jared Spool at UIE has published some good info on the role of paper prototyping.

Moving up a notch on the fidelity scale, high-level dev tools like LiveCode, RealBASIC, and Quickly can help craft functional prototypes very cost-effectively.

But even with such tools, it takes considerable time to create the prototypes and significant resources to orchestrate good testing to evaluate the resulting data adequately.

I believe there may be ways to employ the community to help with such user testing, to acquire more data at lower cost in ways similar to what we see with code.

But while code contributions seem readily accepted by Canonical, the design team there doesn't seem to have a community liaison function as there is with code contributions, so the frequency and thoroughness of user testing is limited to what can be done in-house.

Do you see a role for community support of usability testing and research for FOSS projects like Ubuntu?

If so, what would it look like?

---

### Post by keithpeter on 2012-01-31
> **rg4w said:**
> Until the average person can walk into Best Buy and purchase a computer with Ubuntu on it, Ubuntu will never exist as a mass-market product.  It simply isn't a whole product by itself, since it needs a computer to use it.

Hello rg4w and all

Many points here, but I think the snippet above nails it. I'm sure Canonical's recent developments can be seen as their attempt to find industry partners. 

What I'm getting at in this thread however is the recent emergence of 'design' of a 'user experience' both in the Gnome project and in Canonical's own variant interface. We are seeing decisions (e.g. the somewhat eccentric decision to hide the power off option in the Gnome Shell settings menu) about 'what is good for users' being taken at a central level in the UI design. I think this is a new trend (although Gnome has had a set of human interface guidelines for some time).

PS: I'm glad I'm not the only one who thinks of GNU/Linux users in terms of Moore's Chasm and [Roger's model of innovation]("http://en.wikipedia.org/wiki/Diffusions_of_innovations").

I'll think about the other stuff on the train ride into work tomorrow!

---


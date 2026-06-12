---
title: "vanilla framework free to use on personal projects? i.e blogs?"
date: 2022-07-29
forum: Ubuntu, Linux and OS Chat
---

### Post by drawde111 on 2022-07-29
Hi,

Just wanted to know if we can freely use this framework for our personal or commercial project?
[https://vanillaframework.io/](https://vanillaframework.io/)

---

### Post by TheFu on 2022-07-29
You need to read the license for each component to know.  Or have your lawyer do it.  Certain, common, licenses do allow that level of use, but if even 1 component doesn't, then no, you cannot.

---

### Post by drawde111 on 2022-07-30
Thanks.I'll have another read and see if I can make sense of it.

---

### Post by TheFu on 2022-07-30
> **drawde111 said:**
> Thanks.I'll have another read and see if I can make sense of it.

This is one of those things that all software devs need to spend time learning, but few do.  Each license determines what can be done, how.  

Some are 'business friendly', which is why Roku and Apple have chosen to use BSD and MIT licensed code. In general, just the credit for the resulting product has to be shared and often, that can be accomplished by dropping a text file, buried somewhere, into the deployed code.  

Then there are the GNU licenses.  Some are restrictive and some are permissive.  Some mandate that any changes, made for any purpose, must be shared.  Some only mandate that changes made be shared if the software is shared with anyone else.  GNU licenses are written in a way that makes them "viral" - if you add code to the existing code or link with GPL code, then your code much follow the GPL.  Businesses hate that.  The LGPL can be used with commercial uses, but only as long as the LGPL parts can be updated by any end-user.  That is fairly difficult for most users, so it is effectively making a GPL viral license.

Then there are 5000+ other licenses.  Every dev and their lawyer can make up anything they want and add it in as terms of use or the EULA.  Until you read each component's license, you don't know.

If you never, ever, ever, share your little project with anyone, then nobody will know if you've violated any license terms.  But as soon as you share it with anyone else, perhaps someone running MS-Windows, then the MS-EULA lets MSFT scan their hardware for anything they like and if they see anything illegal, they can tell the company or govt. It is in the EULA for all currently supported MS-Windows releases and has been for years.

When I was learning this stuff, I carefully read the GPL, LGPL, AGPL, MIT, BSD licenses.  Then I started mentally grouping each into how they would restrict my use of the software.  Many commercially viable libraries have dual licenses - a F/LOSS license until the people using the code become a business with over $200K in annual revenues  (or $5M).  But until we read the license, we don't know.

Licenses aren't really THAT hard to read. Just need to be detail oriented and note what is said and what is not said.  Lawyers are good at using general terms which seem to be very specific, but actually are generic and allow for much more than normal people would consider.  Read any website's analytics or privacy policy.  Most list the stuff they capture then say they only share it with 3rd parties that aid their business interests.  That doesn't sound too bad, after all we know this is part of running a web server.  What they don't say is that the data is purchased by the 3rd parties, then resold over and over to anyone with $0.05 per individual annual record which contains 50K views for each user.  Here's my blog and Privacy Policy: [https://blog.jdpfu.com/2007/03/24/PrivacyPolicy](https://blog.jdpfu.com/2007/03/24/PrivacyPolicy)  I tried to be clear and honest in that page. I doubt you'll come across any other website that is as up front and documents it.

Software licenses are similar.  F/LOSS ones aren't 1-sided like nearly every business agreement is.

---

### Post by grahammechanical on 2022-07-31
Are there any members of this forum qualified or willing to give a yes or no answer to this question? I doubt it. As far as I can tell Vanilla is Canonical code and is released under the GNU Lesser General Public Licence (LGPLv3).

[https://opensource.org/licenses/lgpl-3.0.html](https://opensource.org/licenses/lgpl-3.0.html)

Here is an interesting view of the Lesser GPL

[https://www.gnu.org/licenses/why-not-lgpl.html](https://www.gnu.org/licenses/why-not-lgpl.html)

> The choice of license makes a big difference: using the Lesser GPL permits use of the library in proprietary programs; using the ordinary GPL for a library makes it available only for free programs.

In this context "free" and "Proprietary" has reference to the source code being available for download, modification and re-distribution. Not to the price.

What do you mean by "commercial project?" A software project to be used by a commercial organization or to be sold? Further reading:

[https://opensource.org/faq#commercial](https://opensource.org/faq#commercial)

>  **Can Open Source software be used for commercial purposes?** 	Absolutely. All Open Source software can be used for commercial purpose; the Open Source Definition [guarantees]("https://opensource.org/docs/osd#fields-of-endeavor") this. You can even [sell]("https://opensource.org/faq#selling") Open Source software.
  	However, note that *commercial* is not the same as *proprietary*.  If you receive software under an Open Source license, you can always  use that software for commercial purposes, but that doesn't always mean  you can place further restrictions on people who receive the software  from you. In particular, [copyleft]("https://opensource.org/faq#copyleft")-style  Open Source licenses require that, in at least some cases, when you  distribute the software, you must do so under the same license you  received it under.



>  **How do I make money if anybody can sell my code?**
 	You can sell services based on the code (i.e., sell your time), sell  warranties and other assurances, sell customization and maintenance  work, license the trademark, etc. The only kind of profit strategy that  is incompatible with Open Source is monopoly-based sales, also known as  "royalties". See [this article]("http://blogs.fsfe.org/greve/?p=260")  for how to think about business strategies that make money from Open  Source. Also, this 2015 survey of open source leaders (including many  OSI Directors) provides several [business models for Free and Open Source software]("https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2769875").

 	
   **Can I sell Open Source programs? Even if I haven't written it?**
 	Yes, you can. But depending on the license, you probably can't stop  your customers from selling it in the same manner as you. See the [commercial use]("https://opensource.org/faq#commercial") for more details.

 	
   **Does Open Source mean anybody else can use my name and logo?**
 	No, at least not any more than they could otherwise. Open Source is about software source code, *not*  about identity. That is, letting people use your code under an Open  Source license is not the same as letting them use your trademarks or  other identifying attributes, except insofar as they would be permitted  to anyway (for example, in [nominative use]("https://en.wikipedia.org/wiki/Nominative_use")  doctrine). There are many companies and other organizations that  release open source code while exercising tight control over their  trademarks.

  	Trademarks and other marks of attribution are primarily about  preventing public confusion over identity and provenance, and therefore  trademark regulation is useful in Open Source software in the same way  it is useful generally.



Refgards

---


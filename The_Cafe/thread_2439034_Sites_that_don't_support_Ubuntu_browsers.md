---
title: "Sites that don't support Ubuntu browsers"
date: 2020-03-21
forum: The Cafe
---

### Post by crip720 on 2020-03-21
The other day was checking out the free steaming options on Sling.  When site loaded was saying they don't support Ubuntu browsers.  After installing an 'user agent switcher', their site worked perfectly.  Since they do seem to work well on Ubuntu browsers, I figure they just don't want to be bothered.  Was using firefox first, then had switcher to change to chrome windows.  Any opinions.

---

### Post by DuckHook on 2020-03-22
Depressingly common. As you discovered, the user agent workaround usually easily sneaks by this sort of thing.

Sling is but symptomatic of a larger problem. Government sites routinely post fillable PDFs that only work on Acrobat Reader. If they detect a non Acrobat reader, they lock up and refuse to open. The developer just couldn't be bothered to design the form generically (it's not that hard).

---

### Post by Irihapeti on 2020-03-22
Maybe they're just terrified that Ubuntu users are all hackers, so they want to keep us away. :)

---

### Post by kurt18947 on 2020-03-22
> **Irihapeti said:**
> Maybe they're just terrified that Ubuntu users are all hackers, so they want to keep us away. :)

As well they should. We're all scheming lying ner'-do-wells  doncha know? :D :D In fact, I imagine it may have to do with the inability/unwillingness to provide technical support.

---

### Post by Frogs Hair on 2020-03-22
Strange, just  tried Sling on Solus OS and it worked after allowing Firefox to install needed components an enabling DRM. Seems they have a Linux bias. :D

---

### Post by crip720 on 2020-03-22
Sling specifically says Ubuntu browsers, not Linux.  Don't know if same would happen with Arch or Fedora or another type.  This happens when trying to watch([https://watch.sling.com/](https://watch.sling.com/)).  Home page works okay(sling.com)

---

### Post by Frogs Hair on 2020-03-22
I tested on Ubuntu Budgie and only Ubuntu Firefox gets the warning/block and Chrome works just fine.

---

### Post by crip720 on 2020-03-23
Wonder if they just have something against Firefox on Ubuntu?  My Chrome works also, but usually just  use it for videostream.  Just changed user-agent to firefox windows and sling says firefox not supported either.  Looks like they just don't like firefox and not Ubuntu in general.

---

### Post by Frogs Hair on 2020-03-23
> Wonder if they just have something against Firefox on Ubuntu? Seems to be their target.

---

### Post by sdsurfer on 2020-03-25
As one who has developed since Windows 3.0, a very basic premise is commonly ignored today to the point of pious pretentiousness.

That premise is from Tim Berners Lee, that we as developers should never dictate to the end user how they should browse the Internet. It is up to us to make it easy for them.

In the early days clients (in this case, client being web browser) had their own ideas on how to render HTML to the user. There was no real standard, and when one was formed, each thought they were so awesome and would take over the market share that the only loosely, if at all, followed it. We had to formulate all sorts of hacks and mods to get Mosaic, Netscape, I.E., and that newbie "FireFox" to play nicely together. But we did it, because we understood -*** and respected*** - that basic premise.

As years went by, more and more lazy developers - and it is indeed lazy - moved into positions of power in which they dictated what they would and would not support. They would find some evidence - and if you look hard enough on the 'net, you will always find what you are looking for - that the ROI to support this browser or that was not worth their time. In my last position one of those devs sold the idea to business that if someone wanted to support older IE browsers, they would personally have to pay for it. The irony is that internal business staff were issued Windows computers that could not upgrade to the later browsers, so they were instructed to use Chrome or Firefox. 

So sadly, what you are facing is a huge problem that is not going away. The solution is **really** simple - instead of identifying the browser and acting as a gatekeeper, you identify if the client has the capabilities to do what you want to do and proceed to ***gracefully degrade*** so the user can ***still access your content.*** This is why Flash failed, it only had limited capability to gracefully degrade and most developers using it failed to implement, or understand, how to do that.

---

### Post by DuckHook on 2020-03-25
^^^+++^^^ This.

---

### Post by Skaperen on 2020-03-27
> **Irihapeti said:**
> Maybe they're just terrified that Ubuntu users are all hackers, so they want to keep us away. :)

but they're not keeping us away, just encouraging us to become hackers (BTDT).

---

### Post by Skaperen on 2020-03-27
> **crip720 said:**
> Sling specifically says Ubuntu browsers, not Linux.  Don't know if same would happen with Arch or Fedora or another type.  This happens when trying to watch([https://watch.sling.com/](https://watch.sling.com/)).  Home page works okay(sling.com)

it could be because they fear we can record videos while playing them.  is this something Ubuntu has over the other distros?

---

### Post by Skaperen on 2020-03-27
lazy??? are you saying that doing things right is harder to do?  i suppose that is true if making things easier is by using software to do it for you and the developers of that software just don't know how to do it right.

---

### Post by sdsurfer on 2020-03-30
> lazy??? are you saying that doing things right is harder to do?

No it's absolutely not more difficult! That's kind of my point, it's a matter of willingness to understand the underlying problem and willingness to grow, especially with front end/client stuff.

For example take a "web page designer." He/she learns to build web pages, maybe even Javascript/server side script a bit, and people start paying them. They begin to feel like a professional. Then along comes someone they perceive as a know-it-all and says, "Hey, have you seen this site? None of your pages validate."

[https://validator.w3.org/](https://validator.w3.org/)

Rather than to accept that as new knowledge, and expand their understanding, they immediately find references that validation is not important (see "you will find what you're looking for") and build an argument against validation, how it's not important, and have a whole library of arguments and justifications against it every time the topic comes up. The irony is people sometimes spend far more energy arguing against a concept than if they had accepted: "here is something I didn't know, something that will ***make me a better developer."***

Another (and a personal pet peeve of mine) is the perception that coding to XHTML over HTML makes you a better developer. Before HTML 5, you could have perfectly valid HTML 4.01 pages and no value would be added by switching to an XHTML doctype. It wouldn't make it smarter or better or faster, because for 95% of published pages, HTML is more appropriate. Why?

Because the "X" in XHTML is for ***extending*** HTML. It is extremely powerful, but very few ever understood or used it's power. With a custom DDT (Document Definition Type) you could do all sorts of things, like define context to the client.

```
The <movie>Titanic</movie> is a movie about a <adjective>titanic</adjective> ship.
```

This was huge (pun intended)  at the time, especially for search engines and screen reader clients. You could now tell the client I mean a movie here and an adjective there. So if you're not extending HTML, what is more appropriate?

I have seen prospective hires discarded simply because they didn't code with an XHTML doctype, when all they were coding was . . . HTML. Totally more appropriate.

---

### Post by DuckHook on 2020-03-30
> **sdsurfer said:**
> No it's absolutely not more difficult! That's kind of my point, it's a matter of willingness to understand the underlying problem and willingness to grow, especially with front end/client stuff&#8230;
Perhaps not harder, but it does require more care, and a consideration for others (and their differences) that is out of fashion these days. If I might risk distilling your thoughts down to a single word, you are addressing *inclusivity*.

Your examples are excellent. They do raise further issues that are closely related to the ones you already address:

The Internet has largely abandoned Tim Berners Lee's original vision of it being an empowerment technology&#8212;one in which people actually contribute as much as they absorb. That communal philosophy was starved of air at birth to be hijacked by a consumerist strategem wherein the vast majority of people are conditioned to mindlessly consume "stuff" that is drip-fed to them by "content providers", entertainment cartels and their increasingly vertically integrated ISPs.

Such an environment is hostile to your (and Berners Lee's) vision of an inclusive Internet. In fact, by its very nature, it must promote the opposite: an environment of exclusivity, where silos are built to fence old users in and charge newcomers at the door. This dynamic is antithetical to the practice of validation. If one's motive is to build silos, to divide and conquer, then why would one support an opposing movement towards openness and inclusivity?

New developers are indoctrinated in this exclusionary thinking. It rubs against their training to design webpages, or apps, or OSes for that matter, to be accessible to all. I suspect that this dynamic is at least partially the reason for the indifference and neglect that you cite in your examples.

---

### Post by Frogs Hair on 2020-03-30
The site noted at the beginning of the thread doesn't support Opera either. There was no message pertaining to Ubuntu only Opera.

---

### Post by QIII on 2020-03-30
Firefox is not an "Ubuntu browser", but I get that message using Firefox.  I get no such message using Chrome, even without a user agent.

On Fedora, I get the warning about "Fedora browsers" when using Firefox.

This is not laziness.  All that matters is whether or not the browser itself is standards-compliant.  The OS is immaterial with a standards-compliant browser.  Microsoft's browsers are not, by the way.  Sometimes this sort of OS check is deliberate due to the fact that the developers and their employers have fallen victim to FUD and are convinced that Linux is an illicit tool of nefarious agents bent on stealing their content.  They probably rarely have anything to do with their own server admins, who are likely serving content from Linux servers -- and those very likely Debian family like Ubuntu or Red Hat family.

Sling.com appears to be using Windows and IIS.

---

### Post by Frogs Hair on 2020-03-30
> Sometimes this sort of OS check is deliberate due to the fact that the developers and their employers have fallen victim to FUD  I noted in earlier post that Firefox on Solus was not blocked, so the message is targeted. I just updated to the Chromium based version on Edge on Windows and will have see what happens with that.

 Edit: Edge is supported.

---

### Post by QIII on 2020-03-30
Interestingly, on Solus using Firefox I get a message saying that Sling is not supported on Firefox.

Installing Chrome on Solus to see what happens.

Edit:  Chrome on Solus works fine.  Looks like the target of their ire may be Firefox.

---

### Post by QIII on 2020-03-31
Same is true with Debian.  Firefox is a NOGO, Chrome works.

---

### Post by Frogs Hair on 2020-04-03
> [COLOR=#000000]Interestingly, on Solus using Firefox I get a message saying that Sling is not supported on Firefox.[/COLOR] It still works here on Solus. :confused: Initially ,  I had to enable DRM and allow Firefox to install components and refresh the page.

---


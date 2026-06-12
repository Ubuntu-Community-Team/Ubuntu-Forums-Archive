---
title: "Why OpenOffice?"
date: 2012-01-27
forum: The Cafe
---

### Post by neu5eeCh on 2012-01-27
I was just reading [this]("http://www.linuxtoday.com/developer/2012012700141OSSW") article, and the same question occurs to me as occurs to the author. Why don't IBM and others, on whom Oracle dumped OpenOffice, just kick it the rest of the way out the window and throw some of their brains, dollars and devs behind Libre Office? What? Is it spite? Arrogance? Disdain? Money? Prestige? Just wondering...

---

### Post by JDShu on 2012-01-27
This is my own conjecture:

With OpenOffice, they retain almost full control over the code and are confident about it. The permissive license also decreases the legal hurdles for them. On the other hand LibreOffice involvement would require taking time to work with the wider community to get features they want into the product. In the short term, this might not be acceptable for their clients.

---

### Post by neu5eeCh on 2012-01-27
I was just reading up on their different licenses after your comment:

LibreOffice: GNU LGPL License
OpenOffice: (Looks like a mess to me.)

> Portions of OpenOffice.org are Copyright 1999, 2010 by contributing authors and Oracle and/or its affiliates.
  Sections or single pages are covered by certain licenses. If a  license notice is displayed, you may use the content of that page  according to that license.
  In all other cases, the page is licensed under the Apache License, Version 2.0 [(ALv2)]("http://www.apache.org/licenses/LICENSE-2.0.html").


When trying to sort out the differences between the two licenses, my eyes began to glaze over. They seem very similar. Having read them, I'm too unfamiliar with the two licenses to see what advantage IBM or Apache gains. They both seem to be permissive licenses. Having control over the code makes sense, but how is that an advantage if they spend all their time playing catch up with LibreOffice (if that's true)?

---

### Post by forrestcupp on 2012-01-27
I think the only reasons are pride, stubbornness, and they don't want people to think they're ready to give up the OpenOffice name.

---

### Post by JDShu on 2012-01-27
> **VTPoet said:**
> I was just reading up on their different licenses after your comment:

LibreOffice: GNU LGPL License
OpenOffice: (Looks like a mess to me.)



When trying to sort out the differences between the two licenses, my eyes began to glaze over. They seem very similar. Having read them, I'm too unfamiliar with the two licenses to see what advantage IBM or Apache gains. They both seem to be permissive licenses. Having control over the code makes sense, but how is that an advantage if they spend all their time playing catch up with LibreOffice (if that's true)?

The LGPL is not really a permissive license. I don't understand the license text well enough to explain them accurately, but the LGPL requires modifications to the original code to be shared. It's only code that only "links" to the LGPL'd code that does not need to be shared.

To answer your question[1], IBM is a solutions company. So what might happen is a company wants a certain feature on OpenOffice and ask IBM for it. Because OpenOffice is Apache licensed, IBM can create the feature and ship it quickly to their client without needing to interact with the LibreOffice community.

Of course in the long term, LibreOffice might become more fully featured than OpenOffice and better in every way possible, but IBM is a corporation... it's the short run that matters at any given time :P

[1] Again, my own conjecture. Maybe somebody could prove me wrong :)

---

### Post by LowSky on 2012-01-27
I belive the last installment of Lotus Notes was built on OpenOffice.org, so that might play into things as well.

---

### Post by KiwiNZ on 2012-01-27
> **LowSky said:**
> I belive the last installment of Lotus Notes was built on OpenOffice.org, so that might play into things as well.

Lotus Notes is email ,contact management etc their office application is Lotus Symphony

---

### Post by neu5eeCh on 2012-01-27
> **KiwiNZ said:**
> Lotus Notes is email ,contact management etc their office application is Lotus Symphony

According to the article, IBM has stopped development of Lotus Symphony since Oracle "dumped" (as it were) OpenOffice on them.

---

### Post by KiwiNZ on 2012-01-27
> **VTPoet said:**
> According to the article, IBM has stopped development of Lotus Symphony since Oracle "dumped" (as it were) OpenOffice on them.

[http://www-03.ibm.com/software/lotus/symphony/home.nsf/home](http://www-03.ibm.com/software/lotus/symphony/home.nsf/home)

"
**Lotus Symphony 3.0.1 is HERE !!!!!**

 		**[B]Buzzmaster1**  |  Jan 18, 2012 9:02 AM[/B]

  		  Lotus Symphony 3.0.1 is our latest release. There are many enhancements  in this release including support for 1 million rows in spreadsheets,  bubble charts and a new design for the home page. Download Symphony  3.0.1 today. "

---

### Post by forrestcupp on 2012-01-28
> **KiwiNZ said:**
> [http://www-03.ibm.com/software/lotus/symphony/home.nsf/home](http://www-03.ibm.com/software/lotus/symphony/home.nsf/home)

"
**Lotus Symphony 3.0.1 is HERE !!!!!**

 		**[B]Buzzmaster1**  |  Jan 18, 2012 9:02 AM[/B]

  		  Lotus Symphony 3.0.1 is our latest release. There are many enhancements  in this release including support for 1 million rows in spreadsheets,  bubble charts and a new design for the home page. Download Symphony  3.0.1 today. "

Let's hope they keep it coming. It's good to have other interesting alternatives. Symphony has a few features that are pretty nice.

---

### Post by neu5eeCh on 2012-01-28
> **KiwiNZ said:**
> [http://www-03.ibm.com/software/lotus/symphony/home.nsf/home](http://www-03.ibm.com/software/lotus/symphony/home.nsf/home)

"
**Lotus Symphony 3.0.1 is HERE !!!!!**

         **[B]Buzzmaster1**  |  Jan 18, 2012 9:02 AM[/B]

            Lotus Symphony 3.0.1 is our latest release. There are many enhancements  in this release including support for 1 million rows in spreadsheets,  bubble charts and a new design for the home page. Download Symphony  3.0.1 today. "

OK... and [this]("http://www.edbrill.com/ebrill/edbrill.nsf/dx/ibm-lotus-symphony-3.0.1-is-now-available") from Ed Brill:

> This will also likely be the last release of IBM's own fork of the  OpenOffice codebase. Our energy from here is going into the Apache  OpenOffice project, and we expect to distribute an "IBM edition" of  Apache OpenOffice in the future. We have contributed the Lotus Symphony  code into the OpenOffice project, along with human resource across  development/product management/marketing organizations. I'm excited by  what I see happening at Apache, but for now, the new release of Symphony  keeps the current project updated for existing and potential customers.  

Like I said, this would appear to be the end of development on Lotus Symphony.

---

### Post by KiwiNZ on 2012-01-28
You maybe right, all three iterations seemed doomed due to fragmentation and lack of progress. They simply do not offer a viable alternative in real life applications.

---

### Post by forrestcupp on 2012-01-28
> **VTPoet said:**
> 
Like I said, this would appear to be the end of development on Lotus Symphony.

Looks like maybe they'll incorporate features from LS into OpenOffice. That might not be a bad thing. We still have LibreOffice for those who don't like Symphony's style.

---


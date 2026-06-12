---
title: "Launchpad Source Code Released"
date: 2009-07-21
forum: The Cafe
---

### Post by ghindo on 2009-07-21
> Canonical releases source code for Launchpad

Release of Launchpad to encourage innovation

London July 21, 2009: Canonical, the founder of the Ubuntu project, announced today that it has open-sourced the code that runs Launchpad, the software development and collaboration platform used by tens of thousands of developers.[http://www.ubuntu.com/news/canonical-open-sources-launchpad](http://www.ubuntu.com/news/canonical-open-sources-launchpad)

---

### Post by philcamlin on 2009-07-21
cool :popcorn:

---

### Post by jpeddicord on 2009-07-21
I'm really surprised: code hosting and Soyuz are included, when there were previously going to be held back. If there's any Launchpad developers reading this: excellent work. :D

---

### Post by master5o1 on 2009-07-21
Yay! Though I have absolutely no use for the code.  Someone else might, right?

---

### Post by Jimleko211 on 2009-07-21
Very cool.  I think Canonical just got some brownie points from the FOSS junkies.

---

### Post by keiichidono on 2009-07-21
> **Jimleko211 said:**
> Very cool.  I think Canonical just got some brownie points from the FOSS junkies.

Big time, can't release an open source operating system without the open source apps to go with it.

---

### Post by gnomeuser on 2009-07-21
Excellent news, I am happy they addressed the concerns of those of us who feared the buildsystem especially continuing to be closed. I congratulate Canonical on doing the right thing and living up to the year long promise of releasing Launchpad.

Hopefully now we can get a plan for releasing Landscape and the Ubuntu One server. While I am happy that Canonical finally realized the advantages in freeing Launchpad I am mildly concerned with their desire to continue developing and releasing non-free software which will become more and more ingrained in the distribution with the excuse that the client side is free but everything that touches your data you aren't allowed to vet for security or help enhance. It's a common problem with this whole cloud business, nifty as it is.

But today, we celebrate. Something good happened, so here is to Launchpads bright future. I can't wait to see where we take it together.

---

### Post by Ozor Mox on 2009-07-21
> **gnomeuser said:**
> Excellent news, I am happy they addressed the concerns of those of us who feared the buildsystem especially continuing to be closed. I congratulate Canonical on doing the right thing and living up to the year long promise of releasing Launchpad.

Hopefully now we can get a plan for releasing Landscape and the Ubuntu One server. While I am happy that Canonical finally realized the advantages in freeing Launchpad I am mildly concerned with their desire to continue developing and releasing non-free software which will become more and more ingrained in the distribution with the excuse that the client side is free but everything that touches your data you aren't allowed to vet for security or help enhance. It's a common problem with this whole cloud business, nifty as it is.

But today, we celebrate. Something good happened, so here is to Launchpads bright future. I can't wait to see where we take it together.

Is there a reason why people say that companies with some open source aspects (like Canonical) should be all or nothing with FOSS? Why can't they have some open source and some closed projects, perhaps to generate income for the open source ones?

Not arguing, just curious.

---

### Post by gnomeuser on 2009-07-21
> **Ozor Mox said:**
> Is there a reason why people say that companies with some open source aspects (like Canonical) should be all or nothing with FOSS? Why can't they have some open source and some closed projects, perhaps to generate income for the open source ones?

Not arguing, just curious.

You assume, falsely, that one cannot create income from pure open source. Many companies do so, Red Hat probably being the most successful pure open source example. 

There is a lot of money to be made from things like support contracts, specialized development and services around the platform - Ubuntu One is such a service and it would work just as well if they let people help them grow that extension to the platform - nobody in their right mind would setup their own server and run it to save those 10$ a month the high end parts would cost and if the fear is that people might run to a cheaper partner who merely takes the source code and offers a cloned service ask yourself this. Would you rather have your service managed by the people who develop it and are invested in making it grow with the community or people who have no just interest and only want to make a quick buck. There might be people in category b here but after the first problem or so if the service isn't supported properly they will run back to Canonical. The same goes for feature requests, either you get those for free from the cloners or the customers come to those who will consistently improve the platform accordingly. Nobody supports it as well as the people who are invested in the platform. As a bonus you create a vetted platform people will trust and that interested developers might run their own test instance of thus encouraging free development time on your project.

---

### Post by Mr. Picklesworth on 2009-07-21
Hooray! Now, I hope other deployments of Launchpad all integrate neatly together. If they do, this will be quite beautiful :)

---

### Post by gnomeuser on 2009-07-21
> **Mr. Picklesworth said:**
> Hooray! Now, I hope other deployments of Launchpad all integrate neatly together. If they do, this will be quite beautiful :)

I think now that it is open and projects can help craft Launchpad, rather than multiple instances we will see more projects move to Launchpad and add to the existing infrastructure now that they can trust that they have a degree of control over where it is going and which features will be implemented.

Hosting is largely not an issue for most projects, openness is. 

Just like there aren't many Sourceforge clones out there (I think GNU has one called Savanna but that's about it). Once the platform is open and trustworthy there is very little reason to merely do hosting yourself rather than engage with the existing service and develop it.

This all hinges on the fact that now that the code is open the community will be as well naturally. E.g. it would be hard to imagine say Fedora going to Launchpad.net for it's needs if they felt they were being asked to hand out all control to Canonical rather than an open community they could be part of. If that level of openness doesn't happen then we will likely see either spawning of distribution or project specific Launchpad instances or a complete discarding of LP as a future platform choice for these projects, of which I think the latter is more likely.

---

### Post by Ozor Mox on 2009-07-22
> **gnomeuser said:**
> You assume, falsely, that one cannot create income from pure open source. Many companies do so, Red Hat probably being the most successful pure open source example. 

There is a lot of money to be made from things like support contracts, specialized development and services around the platform - Ubuntu One is such a service and it would work just as well if they let people help them grow that extension to the platform - nobody in their right mind would setup their own server and run it to save those 10$ a month the high end parts would cost and if the fear is that people might run to a cheaper partner who merely takes the source code and offers a cloned service ask yourself this. Would you rather have your service managed by the people who develop it and are invested in making it grow with the community or people who have no just interest and only want to make a quick buck. There might be people in category b here but after the first problem or so if the service isn't supported properly they will run back to Canonical. The same goes for feature requests, either you get those for free from the cloners or the customers come to those who will consistently improve the platform accordingly. Nobody supports it as well as the people who are invested in the platform. As a bonus you create a vetted platform people will trust and that interested developers might run their own test instance of thus encouraging free development time on your project.

Oh no, I don't think it is not possible to make money from open source. In fact, I have argued a number of times on these forums that it is, and cited Red Hat, Novell, IBM etc. as examples. I've just always thought it's a bit unfair that people jump on Canonical for anything they make that is closed despite the good they are doing with Ubuntu, now Launchpad, etc., when there are so many entirely closed software companies that no one mentions.

Still, you make some good arguments for an open Ubuntu One, and I think it would be great if they opened everything else they do. If they are better off keeping it closed, and they make a ton of money and fund Ubuntu with that, then I think that would be great too :D

---

### Post by j7%&lt;RmUg on 2009-07-22
This is great, now i can have a look at the lp code and of course learn from it.

Congratulations to the lp-dev team for getting this far.

---

### Post by 23meg on 2009-07-26
[QUOTE=nisshh]This is great, now i can have a look at the lp code and of course learn from it.[/QUOTE]

The fact that the entire revision history has been retained as well (which is awesome) should help.

---

### Post by dragos240 on 2009-07-26
This is why Linux rockz!

---


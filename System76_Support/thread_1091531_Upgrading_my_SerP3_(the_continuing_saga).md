---
title: "Upgrading my SerP3 (the continuing saga)"
date: 2009-03-09
forum: System76 Support
---

### Post by Trevor Bramble on 2009-03-09
76ers (that is, Thomas Aaron),

It looks like the 64-bit overhead might be more than I'm set up to handle with just the 2 gigabytes of RAM in the system. With Firefox (*2), Eclipse (*2), SQL Developer, Amarok, and a few small apps open, I'm over %80 utilized and occasionally clinging to the ceiling until closing things out.

2*4GB looks amazingly expensive, but 2*2GB does not.  So, what I'm sure the usual RAM questions are:

1. What sort to buy?
2. Buy a matched pair or just one more 2GB?

Somewhat related: I see that my 128MB swap partition is %100 utilized.  Should that be resized?  How big should it be?  Obviously the old math based on RAM is no longer applicable.

---

### Post by thomasaaron on 2009-03-09
Hmmm... 

If you have 2GB in your system now, you probably have 2ea 1GB cards. So, to go to 4GB (total) you would probably need to by a 2ea 2GB cards.

The motherboard limit for that computer is, I believe, 4GB total.

---

### Post by steveneddy on 2009-03-09
> **Trevor Bramble said:**
> I see that my 128MB swap partition is %100 utilized.  Should that be resized?  How big should it be?  Obviously the old math based on RAM is no longer applicable.

The swap should be around 1.5 Gigs with between 2-4 Gigs of RAM.

Make the swap larger and you will see RAM usage go down.

Add more RAM and you will see swap usage almost gone.

But 128mb swap is really too small. Enlarge it to at least one Gig.

---

### Post by thomasaaron on 2009-03-09
Thanks, Steveneddy. I didn't see that question.

---

### Post by Trevor Bramble on 2009-03-09
> If you have 2GB in your system now, you probably have 2ea 1GB cards. So, to go to 4GB (total) you would probably need to by a 2ea 2GB cards.

The motherboard limit for that computer is, I believe, 4GB total.

You're right.  For some reason I thought I'd selected 1*2GB when ordering. =^)

I looked up the product number to find which specifications I should match and it looks like [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820134661") will be good.  Right?



> The swap should be around 1.5 Gigs with between 2-4 Gigs of RAM.

Make the swap larger and you will see RAM usage go down.

Add more RAM and you will see swap usage almost gone.

But 128mb swap is really too small. Enlarge it to at least one Gig. 
And RAM, I would imagine, is preferable.

I'll enlarge it to 1G and see how it goes.  And either leave it alone or resize as needed when the new RAM comes in.

Thanks!

---

### Post by thomasaaron on 2009-03-09
Those cards will work fine.

For what it's worth, when we image computers, we make the swap equal to the installed RAM. Steveneddy is right that this *might* be a little overkill due to the increased speed of computers. Nevertheless, we find it to be the safest bet.

---

### Post by Trevor Bramble on 2009-03-09
Cool.  Maybe I'll go as far as 1.5 after all.

Thanks again, Thomas Aaron!

---


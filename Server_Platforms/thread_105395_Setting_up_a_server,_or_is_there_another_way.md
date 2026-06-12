---
title: "Setting up a server, or is there another way"
date: 2005-12-18
forum: Server Platforms
---

### Post by timczer on 2005-12-18
Here is my situation.  As a work project, we are looking to set up a wiki (or something similar) to host training materials.  We are in three markets and want to make various materials availabe to all three markets, and have the material updatable as it is used and improved.  I thnk that some type of wiki would be best for this.  

In the short term, I want to start putting this project together from my computer I use at home.  I currently have Windows XP and Breezy on a drive and I use the Breezy desktop most of the time.  I have an additional 80 gig hard drive that I use to test run other OS's.  My question is, for setting up this wiki and allowing some sort of access to it from these other markets, what is the best way to do it?  Should I set up a server on this other hard drive?  How would that work and is there a tutorial that would show me how?? Is this the best way of hosting a wiki?  Is there another set-up that would allow me to host the wiki through my current Breezy setup using the additional drive space?

---

### Post by schilcha on 2005-12-18
You don't really need a second install of ubuntu. I did a standard installation of ubuntu on my desktop and installed twiki ([www.twiki.org](www.twiki.org)) there -- no advertisement, I just don't know exactly about wiki itself (I guess it's pretty similar). All I had to do was installing a webserver (I use apache, since I know it). Just search for it in synaptic. 
If you need the second harddrive for the wiki, mount it at /srv and make your webserver have it's document-root on this partition.

---


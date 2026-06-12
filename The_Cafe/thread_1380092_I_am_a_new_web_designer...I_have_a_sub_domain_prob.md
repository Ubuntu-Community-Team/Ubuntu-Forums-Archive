---
title: "I am a new web designer...I have a sub domain problem"
date: 2010-01-13
forum: The Cafe
---

### Post by jauntybluefish on 2010-01-13
Hi guys, sorry if this is the wrong place to post this, but I need help.
Ok guys, 

I have been playing with my new web site and have enjoyed the liberating experience of creation and then display of that creation for all to see.

I have a problem that I just cannot get my head around.
Support have been quick and patient so far, but the replies leave me none the wiser.
I hope someone here can offer a simple explanation of what I must do to correct the problem.
OK...one of my sub-domains does not appear when typing the address.

This is the last reply from support

 	Quote:
 	 	 		 			 				Please find two links below which points to the same folder:
[http://www.silvercoastnetwork.ajm7.com/](http://www.silvercoastnetwork.ajm7.com/)
[http://www.ajm7.com/silvercoastnetwork/](http://www.ajm7.com/silvercoastnetwork/)

The first one doesn't work because the system looks for images here
[http://www.silvercoastnetwork.ajm7.c...ap-regions.png]("http://www.silvercoastnetwork.ajm7.com/images/map-regions.png")

HTTP request to the subfolder for subdomain.
In this case   images must be the subfolder for  silvercoastnetwork.ajm7.com subdomain.
It is not acceptable on our hosting.
As far as I can see [http://ajm7.com/](http://ajm7.com/) and [http://www.silvercoastnetwork.ajm7.com/](http://www.silvercoastnetwork.ajm7.com/) are the same.
So why don't you re-point  silvercoastnetwork.ajm7.com directly to public_html folder?
It will work properly in that case.
Alternatively you need to replace all links like [http://www.silvercoastnetwork.ajm7.com/images/somefile](http://www.silvercoastnetwork.ajm7.com/images/somefile) with [http://ajm7.com/images/some](http://ajm7.com/images/some) file. 			 		 	 	 
In addition I have found that images do not display when going to [http://silvercoastnetwork.ajm7.com/](http://silvercoastnetwork.ajm7.com/)   .


I have not the faintest idea what he is trying to tell me to do.

The confusing thing is, that I have 2 other sub domains that were created and uploaded using the same sequence of events in the cpanel file manager and filezilla on my laptop and they both work just fine.
How can it not just work??

When replying, please bear in mind that I am only a self taught designer in trouble and have no brain between my ears at all. (of course you guys have all the brains right)

Thank you in advance.
Andy

---

### Post by abyssius on 2010-01-13
[http://www.ajm7.com/silvercoastnetwork/](http://www.ajm7.com/silvercoastnetwork/)
[http://www.ajm7.com/silvercoastnetwork/images/silver.png](http://www.ajm7.com/silvercoastnetwork/images/silver.png) (this works)

[http://www.silvercoastnetwork.ajm7.com/](http://www.silvercoastnetwork.ajm7.com/)
[http://www.silvercoastnetwork.ajm7.com/images/silver.png](http://www.silvercoastnetwork.ajm7.com/images/silver.png) (this doesn't)


It appears that /silvercoastnetwork is simply a sub-directory of the main folder on the server that is hosting ajm7.com rather than a sub-domain. In the example that works above, silver.png is located in the folder /images which is a sub-directory of the folder /silvercoastnetwork - which in turn is a sub-directory of the main folder that holds the ajm7.com site files.

In the url that doesnt work, you are declaring that ajm7 is a sub-domain of silvercoastnetwork.com. This isn't the case. I could be wrong, but I think that the only real domain is ajm7.com, so all your file references have to come from that main domain.

---

### Post by jauntybluefish on 2010-01-13
Thanks abyssius,
language i can understand I think.

The other sub domains I have, are all written like this.
vineyardretreat.ajm7.com, where vineyardretreat is a sub domain of ajm7.com. and they work just fine.

It is really confusing when an identical sequence of events leads to something like this that is plainly wrong but should not be wrong because then all the other domains would be misbehaving too.

Thanks again.

---


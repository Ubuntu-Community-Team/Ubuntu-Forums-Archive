---
title: "how to use two servers to run websites"
date: 2008-02-22
forum: Server Platforms
---

### Post by mcraul on 2008-02-22
I asked this question before but not very well so here goes again :)

I currently have 40 websites hosted on a dell poweredge server running redhat. I have 60gigs dedicated to pictures and media for the websites but the drive is filling up. What I want to do is setup another server with 160gig hd running ubuntu server and dedicate that to media/pictures only. In a rack space enviroment can i run the second server to serve out the media for the websites that are hosted on the other server? and if i can how does one go about doing that?


Thanks again!

---

### Post by simvin76 on 2008-02-22
Hello

Maybe a stupid suggestion:
Add a second network card to your webserver and use the new ubuntu server as a NFS server.

If you move the media files to the ubuntu server and mount the NFS share to the old media files directory, you wouldn't need to reconfigure anything (beside a NFS client).


Take care
/Simon

---

### Post by mcraul on 2008-02-22
ok great thats what i thought i should do i just wanted confirmation.
one more question. well it slow down access time on the users end? 

thanks for the quick reply

---

### Post by lespaul_rentals on 2008-02-22
You might see a slight performance decrease, but so long as the servers are using Gigabit Ethernet and are good machines it won't be huge.

By the way, congratulations on your large amount of websites!  That's very cool!  I bet it's kind of intense.

---

### Post by mcraul on 2008-02-22
thank you so much,  we exclusively do auto dealership websites.  and are expanding and expect to add even more sites i am going to have fun scaling it all :popcorn: 

but my boss was worried about access times issues so i think we will be ok the servers have 4gigs of ram

---

### Post by Brazen on 2008-02-22
A more common option would be to set up the new server with it's own dns name, such as media.company.com and then your img tags would point there.  For example, where a current image tage may point to [www.company.com/media/corvette.jpg](www.company.com/media/corvette.jpg) or maybe even a relative path such as media/corvette.jpg, the new path would be media.company.com/media/corvette.jpg.  This is a common practise for high traffic sites.

The other option would be to proxy the new server into the website.  This would let you keep the same path in your img tags.  For instance, on the original web server you would proxy media/ so it points to server2.company.local/media/.  This basically only needs two new entries in your apache config to work.

---

### Post by rickyjones on 2008-02-22
> **simvin76 said:**
> Hello

Maybe a stupid suggestion:
Add a second network card to your webserver and use the new ubuntu server as a NFS server.

If you move the media files to the ubuntu server and mount the NFS share to the old media files directory, you wouldn't need to reconfigure anything (beside a NFS client).


Take care
/Simon

I just wanted to chime in and say that this is what I would do. 

Another way to go is to move the media to the new server and serve those images via Apache2. Of course, this means that you would have to change all the websites affected... so that wouldn't be a very good option.

Go with NFS mounts. As long as you have fast networking available you should be fine.

-Richard

---

### Post by mcraul on 2008-02-22
ok so do you think its more effcient to give that second server a subdomain? it would def make things a big easier but will I still have to share out the server with nfs or? well maybe not i guess

---

### Post by rickyjones on 2008-02-22
> **mcraul said:**
> ok so do you think its more effcient to give that second server a subdomain? it would def make things a big easier but will I still have to share out the server with nfs or? well maybe not i guess

I notice a lot of websites storing their graphics on a secondary server to improve load times usually. But, since you already have existing sites it would be easier and just as effective to use NFS to move the images to a new server.

---

### Post by lifewithryan on 2008-02-22
I would do it the way Brazen mentions.  It would then also allow you to say, setup a cache-fly account and host your media there if you started serving up video's etc.  

Well it would sort of plant the seed.  But either way should work.

---

### Post by Brazen on 2008-02-24
> **mcraul said:**
> ok so do you think its more effcient to give that second server a subdomain? it would def make things a big easier but will I still have to share out the server with nfs or? well maybe not i guess

It is far more efficient, but it's more work because you would have to change all the img tags.

---

### Post by k_grdn on 2008-02-24
Hi,

With this many sites and if you have the resources why not replace the existing drive with a bigger one, pair it up with the other server.

Using heartbeat set one up as the director giving you a cluster setup.

Hence: Your content will allways be available, you'll have 2 copies of eveything and you have 2 servers acting as one.

With heartbeat you can use weighted algorithms so the high spec server can serve more requests.  

Regards,

k_grdn

---

### Post by astrotech226 on 2008-02-24
> **k_grdn said:**
> Hi,

With this many sites and if you have the resources why not replace the existing drive with a bigger one, pair it up with the other server.


I'm going to have to agree with this.  It really depends on how much your content changes, but it's cake to run two web servers handing out the same pages.  Round robin DNS works great for a smaller setup like you have.

If you have two servers, one for content and the other for media, you now have two single points of failure.  Twice as many drives, twice as many power supplies, etc to fail.

It's also not that complicated to set up SAN, NAS or NFS storage so each web server can access the same content.  This makes deploying changes much easier.  When you start hosting more sites and need more servers, you are now in a position to be highly scalable.  Might need to throw a few load balancers in the front, but this can all be done fairly inexpensively if you build the equipment yourself.

---


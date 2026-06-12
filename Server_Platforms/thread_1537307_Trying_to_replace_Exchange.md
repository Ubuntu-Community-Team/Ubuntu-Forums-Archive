---
title: "Trying to replace Exchange"
date: 2010-07-23
forum: Server Platforms
---

### Post by houstonbofh on 2010-07-23
All the data I can find is 3 years old or better, so lets bring it out again.

Right now we are doing hosted Exchange.  We want to bring it in house.  We want to stay off MS.  We have everything working except the global address book, and shared calendars.  What have people done to plug in this functionality? And it needs to be cross-platform since we have Linux and Mac desktops as well.  I am thinking ical, but which one?

So, has anyone done this and come up with something Windows users don't complain about? :)

---

### Post by cdenley on 2010-07-23
I use Zimbra. Windows users can use Outlook with the non-free version. Works just like Exchange, I think. It is an all-in-one collaboration suite.

---

### Post by arrrghhh on 2010-07-23
> **cdenley said:**
> I use Zimbra. Windows users can use Outlook with the non-free version. Works just like Exchange, I think. It is an all-in-one collaboration suite.

Are there any good how-to's on Zimbra?  I struggled with it on my personal server, and it didn't work out too well.

Also, how does Zimbra work scaled to a fairly large enterprise?  Can you connect BB's and the like to it?

---

### Post by cdenley on 2010-07-23
> **arrrghhh said:**
> Are there any good how-to's on Zimbra?  I struggled with it on my personal server, and it didn't work out too well.

How to for what? Installing can't be any easier. Extract then execute. The only thing that got me when I first started using it was I didn't know how to find the administrative web interface.
[https://zimbraserver:7071/](https://zimbraserver:7071/)
> **arrrghhh said:**
> 
Also, how does Zimbra work scaled to a fairly large enterprise?  Can you connect BB's and the like to it?
[http://www.zimbra.com/products/zimbra_mobile.html](http://www.zimbra.com/products/zimbra_mobile.html)
[http://www.zimbra.com/products/blackberry-enterprise-server.html](http://www.zimbra.com/products/blackberry-enterprise-server.html)

---

### Post by sylvester_0 on 2010-07-23
+1 for Zimbra. It's dead simple to set up and maintain, though the open source version is lacking some nice features that are in the spendy (IMO) network edition. We used it for a year and a half and it served us well. I recently moved our internal stuff to Exchange 2010 (~$300/year through MS Action Pack) because of the need for Blackberry sync. Honestly if Zimbra had free mobile sync I would have stuck with it.

Another thing to consider is that the paid BlackBerry connector is in a "beta" state and as of my last check doesn't work with the latest BlackBerry Enterprise Server 5 that's been out for some time now. Again, I've been away from the community from some time, but Zimbra started on their own, were bought out by Yahoo and now they're owned by VMWare. I don't know if the changes in ownership have helped or hindered, it's just something to consider.

---

### Post by cdenley on 2010-07-23
> **sylvester_0 said:**
> Honestly if Zimbra had free mobile sync I would have stuck with it.

Zimbra mobile is included with the Network Edition. I know it used to cost extra. I never tried anything with BES, so I can't comment on that.

---

### Post by arrrghhh on 2010-07-23
I tried it about a year ago or so and couldn't get the damned thing installed... Or maybe it was installed and I couldn't find the admin interface!

It was just a 'what-if' kind of thing for my home server so I gave up on it.  I'm pretty certain we're going with Exchange 2010 for our network, but I figured I should at least mention Zimbra, if anything to get the M$ guys goin ;)

---

### Post by sylvester_0 on 2010-07-23
> **cdenley said:**
> Zimbra mobile is included with the Network Edition. I know it used to cost extra. I never tried anything with BES, so I can't comment on that.

That's great to hear; it was a huge downer for me to have to pay $500 a year just to have the mobile plugin. I just confirmed that BES 5 isn't yet supported by the BB connector: [http://bugzilla.zimbra.com/show_bug.cgi?id=35910](http://bugzilla.zimbra.com/show_bug.cgi?id=35910) :(

Zimbra Open Source is definitely a great product though if you're looking for a free solution! Their forums/bugzilla/wiki are all very active and informative. [http://wiki.zimbra.com/wiki/Ubuntu_8.04_LTS_Server_%28Hardy_Heron%29_Install_Guide](http://wiki.zimbra.com/wiki/Ubuntu_8.04_LTS_Server_%28Hardy_Heron%29_Install_Guide)

---

### Post by rslrdx on 2010-07-23
I like zimbra, I setup a couple of servers a while back with it,  but while it seemed great at first, it was a bit crippled. the free version lacks backup features, and the only solution to that was a backup script setup to run on schedule by cron that actually stoped the service (cold backups only), backed up everything to a tar file (including mailboxes) and uploaded the file to an ftp location. just that took about 15 minutes to complete with no more then 100 EMPTY! mailboxes right a migration. ended up with huge files. This is something really important to notice I think, its a shame it didnt have this features just so that it would make you pay for the version that gave you backup options.

The other problem I had was not being able to make file attachment filters for different groups of people, it was either filter some files for everyone or filter nothing at all. 

AGAIN this was a while back, it may have changed, but i would really check into this details.

Another thing that it lacked but didnt bother me was sorting the messages list view by attachments and the ability to search for attachments.

I honestly hope this things have been "fixed"

---


---
title: "Starling Netbook (star3) to Remain on Ubuntu Netbook Edition 10.04 LTS"
date: 2010-10-11
forum: System76 Support
---

### Post by thomasaaron on 2010-10-11
At System76 we take a holistic approach to creating products. Our PC's aren't simply pieces of hardware with software loaded on them. They're an entire customer experience. A customer should be surfing the web within minutes of receiving their computer. Every System76 computer, from the Starling Netbook to the ultra high-end Serval Professional, should be responsive and snappy. Common task and applications should be easy to access and use. Finally, if you need help, you have System76, Canonical, and the exceptional Ubuntu community available to you.
 
System76 services a very broad range of customers. Our customers include fellow computer geeks, businesses, schools, government, and many people that have never used Ubuntu. We love attracting newcomers. They've learned that Ubuntu is a better option and, with their System76 PC, they're experiencing that better option. The Open Source universe expanded just a bit.
 
This brings me to Ubuntu Netbook Edition 10.10 and Unity. Unity is a new netbook user interface incubated and released by Canonical in May 2010. The interface is designed to maximize vertical pixel availability on small screens while considering the needs of future touch technologies and user experiences. I started using the software via ppa in Ubuntu 10.04. As was to be expected, the edges were rough. Unity has improved considerably over the last few months and is now the default user interface for Ubuntu Netbook Edition 10.10.
 
Unfortunately, many of Unity's rough edges remain apparent. The interface is slow and in many ways confusing to use. Applications launch slowly, the Starling Netbook's fan runs high for a while then dips, and Mutter crashes. Searching for the word “Update” displays Gwibber Social Client, Update Manager, as well as Adept, Akregator, and sometimes Amarok. Sometimes installed applications are visible. Sometimes only available applications. It's difficult to tell what's going to happen when an icon is clicked. Will an application launch? Will Ubuntu Software Center prompt to install software? Will a separate category open?
 
Given our holistic approach to building products and the broad range of customers we serve, System76 will give Unity another release cycle to reach it's maximum potential. We have every confidence in the ability of Ubuntu developers to create the world's finest software. Unity needs a bit more time. Until then, the System76 Starling Netbook will remain on Ubuntu Netbook Edition 10.04 LTS.
 
Carl Richell
President
System76

---

### Post by rdelfin on 2010-10-11
Thank you so much for the promptness and clarification.  

I was wondering why my Star3 netty was not finding any 'important updates' no matter how many times I clicked on the "check for updates" button... now I know why.

Thank you again!  :popcorn:

---

### Post by eveningsky339 on 2010-10-13
You made the right choice.  New software can take a long time to mature completely, and with a nice LTS like Lucid, there's no need to ship with the young and restless Unity.

---

### Post by tlroche on 2010-10-13
just wondering ...
> **thomasaaron said:**
> Carl Richell
President
System76
... how come bossman can't post for himself ?-)

---

### Post by isantop on 2010-10-14
> **tlroche said:**
> just wondering ...

... how come bossman can't post for himself ?-)

I think Tom got around to posting it first! Carl originally posted it on facebook.

---

### Post by superfrogman94 on 2010-10-25
Is the original starling netbook (start1) good to upgrade?
i was thinking on doing it but not sure...

---

### Post by isantop on 2010-10-26
The big problem we have with 10.10 Netbook Edition right now is unity, and since that is a constant across all installations of netbook edition, I'd say it would be best to wait.

That said, 10.10 does fix a number of issues with the Star1. Wireless is supported out of the box, and opening te system monitor does freeze the system. So, if you want to give Unity a shot or you want to use desktop edition instead, there's no problem with that. It's actually a similar situation with Star3's, since users can do whatever they like with their systems anyway.

In a nutshell, there are no technical issues with 10.10 on any of our systems (anymore). There are some usability issues in unity, but if you're okay with that, go ahead!

---

### Post by platz on 2010-10-29
I upgraded my wife's star3 to 10.10 when it was still in beta. Since then she had had some grips about using it. How would you recommend reverting back to 10.04 LTS? I'm thinking a clean install.

---

### Post by isantop on 2010-10-29
Hi.

A clean install is definitely the way to go. There is no easy way to downgrade Ubuntu, only the other way around.

(I suppose you could go through and change all of you repositories to Lucid, then manually set every package to remain at the latest Lucid version, upgrade, then manually remove the version hold from every package, but that sounds a bit tedious! ;) )

---

### Post by isantop on 2010-10-29
I have some information for people curious about trying Ubuntu 10.10 on their Starling systems.

The USB Startup Disk Creator in Ubuntu 10.10 is not capable of making LiveUSB drives for Ubuntu 10.04 due to an incompatibility with a few key underlying system components. If you do install Ubuntu 10.10, you will not be able to make a LiveUSB for Ubuntu 10.04, and thus will not be able to downgrade your system in the event you do not like the new Unity netbook environment.

If you want to give 10.10 a try, you can test Unity out from the LiveUSB before installing. I recommend you test it out very thoroughly before installing, because it is very difficult to go back from 10.10 to 10.04 via USB.

---

### Post by platz on 2010-10-30
I've reverted my star3 to Lucid; but of course, no System76 driver. Without it, the wireless doesn't work properly, possibly some other problems as well. I needed a wired connection to the internet in order to download the most recent System76 driver and install it. Now everything seems OK, back with a clean Lucid install.

---

### Post by bvandev on 2010-11-16
For the record, I moved my Starling (star1) to 10.10 the first week.  It's great.  The new interface is truly innovative.

Sure there are a couple of small usability issues, some functions don't work quite as expected, but nothing is broken.  

For me, the pros easily outweigh the cons.

---

### Post by alpeterson on 2010-11-24
> **isantop said:**
> The big problem we have with 10.10 Netbook Edition right now is unity, and since that is a constant across all installations of netbook edition, I'd say it would be best to wait.

That said, 10.10 does fix a number of issues 


So, how do we get rid of Unity, and get back the netbook interface of 10.04?  If we can do that, then people can use 10.10. (right now it is unusable)

(10.10 also has less applications that I care about, and uses more disk space, so my 4gb disk is too full)

I fell in love with Ubuntu because of that interface, it used screen space very well. (needed some improvements and refinements, but was definitely on the right track).

---

### Post by tlroche on 2010-11-24
> **alpeterson said:**
> how do we get rid of Unity, and get back the netbook interface of 10.04?

I'm still on karmic, so I haven't tried this yet, but here's the best-looking text I've seen [for reverting from Unity to UNR in maverick]("http://tinyurl.com/maverickUnitytoUNR"). That being said, hopefully someone has actually done this on a starling in maverick, and can comment.

---

### Post by henrydubb on 2010-12-30
I recently upgraded to 10.10 and everything is great.

But...

When I got 10.04 working I had a strong distaste for the Netbook edition. After a few minutes I logged out and logged in to gnome edition. Put AWN on the left side with gnome panel on the top.

So when I upgraded it was Gnome not the Netbook edition.  

What does Netbook Edition give folks that Gnome doesn't. If you can live with Gnome - non Netbook - it is Unity free, that's what I did.

---

### Post by isantop on 2010-12-30
Unity does have a couple of nice features that save screen space, like the global menu bar, window buttons in the upper panel, and come Ubuntu 11.04, an autohiding launcher. So far, Unity is shaping up really well in 11.04 alpha, and I'm personally confident we'll be shipping it across the line in April. They have a long development cycle, and they're putting it to good use.

---

### Post by henrydubb on 2011-01-30
Well I have that now in 10.10 with Gnome, AWN, and global menu. I am afraid about 11.04 though with it being so Unitified.

Hide [IMG]http://s3.amazonaws.com/twitpic/photos/large/233209356.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1296392461&Signature=X5Z3lmG6NXuiGtOe0fUqr07ldkk%3D[/IMG]

No Hide [IMG]http://s3.amazonaws.com/twitpic/photos/large/233209476.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1296392451&Signature=cuyPWQHs08RZGKYf4Nr%2FFr6boUA%3D[/IMG]

---

### Post by isantop on 2011-01-31
The unity in natty is based on Compiz, like Gnome, rather than Mutter, like Unity 10.10. It's much faster and much more stable, even now. There are still lots of features that need to be implemented, but with almost three months until release, I'm sure It'll be great.

---

### Post by Carleas on 2011-04-28
Will 11.04 be supported on star3/4s?

---

### Post by isantop on 2011-04-29
We will be supporting 11.04 on the Starlings.

---


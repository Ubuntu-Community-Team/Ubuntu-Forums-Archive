---
title: "search engine for used cars"
date: 2012-03-10
forum: The Cafe
---

### Post by raccoonone on 2012-03-10
My friend and I just built a search engine for used cars. The backend is Django, Solr, Postgres, with RabbitMQ + Celery driving the webcrawler. All running on an Ubuntu Server on EC2 :)

Right now we're indexing ~500GB/day, and hoping to have more listings than Autotrader.com soon =)

Would love feedback, if any of you are into cars: [http://carsabi.com](http://carsabi.com)

---

### Post by Paqman on 2012-03-11
Er, I take it from the fact it didn't like a UK postcode that it's US only.

---

### Post by raccoonone on 2012-03-11
Ah, yes, it's US only at the moment. Sorry about that.

---

### Post by drawkcab on 2012-03-12
Where were you two years ago when I bought my Mazda???   :D

---

### Post by barnaclebill18 on 2012-03-12
I like it!

---

### Post by wewantutopia on 2012-03-12
Really nice!  Surprising to see how many are within 10 miles.

Would be nice if you could group models by all makes into broader, searchable, categories: sedan, coupe, van, pickup etc. etc.

Great job!

---

### Post by raccoonone on 2012-03-13
Yep, that's on our roadmap. It's been a bit difficult though, because not all the sites we crawl have that data listed, and especially for private parties that post on Craigslist they normally rely on the picture to show which it is.

I'll bump it up in our bug tracker, and try to get it implemented. Been spending all my time making our search stack faster. Sharding Solr went a long way towards that though :)

---

### Post by acc61287 on 2012-03-13
nice one!

---

### Post by forrestcupp on 2012-10-06
I wish I would have known about this a few months ago when I bought my truck.

Now, if you can give us a search engine that can search through every Chilton's repair manual for free, that would be great, too. :D

---

### Post by ibjsb4 on 2013-01-17
Guess it hasn't made it to Montana yet, no listings :(

---

### Post by mJayk on 2013-01-18
Well done nice to see someone do something useful

---

### Post by mörgæs on 2013-01-18
Is the site blocked for non-american users? I don't get any results when searching (for example) zip code 98101.

---


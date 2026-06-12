---
title: "Squid 2.7 Block Sites"
date: 2009-09-12
forum: Server Platforms
---

### Post by expatCM on 2009-09-12
I am trying to block a number of websites through Squid.

What I have done is to created a text file listing the sites to be blocked and saved it at /etc/squid/

I have also prepared two statements for the squid.conf file. The statements are

acl blockedsites url_regex -i "/etc/squid/blocked.txt"

http_access deny blockedsites

I put then in squid.conf and then applied changes to squid.  Squid then either works but does not block the sites or complains about the lines I have added and will not save the changes.

I think this must be due to where I have put them in the file but I cannot figure out where that should be.  Can anyone tell me how to work out where to put them?

---

### Post by expatCM on 2009-09-14
Does anyone have any ideas .......  squid.conf is about 5000 lines long which makes it a bit hard to sort out ...

---

### Post by windependence on 2009-09-14
You're going about this totally wrong.

Install Squidguard:

[http://www.squidguard.org/](http://www.squidguard.org/)

-Tim

---

### Post by expatCM on 2009-09-14
ah ... that probably explains why it does not work for me.  Strange to say that google suggests that the approach does work for others though.

Just took a look at SquidGuard, thank you for the suggestion.  Do you happen to know if it actually works with Ubuntu? ...  the list of operating systems it is known to work with is interesting in that Ubuntu is not there.

---

### Post by expatCM on 2009-09-14
yes, SquidGuard seems to also take you into dependency hell.  The notes helpfully tell you to first install Bison, Flex, GCC and Berkeley DB V.2.7.7, V3.2.x or 4.x 

Now ... Berkeley DB is a bit of a problem ....  if you look on apt there are a number of choices and none quite match the description ....  If I make a guess I would say that libdb-je-java is about the closest.  Does anyone happen to know?

---

### Post by windependence on 2009-09-14
apt-get install squidguard doesn't work?

I run mine on FreeBSD, sorry. particulary on pfsense.

-Tim

---

### Post by expatCM on 2009-09-14
hmmmm .... clearly I am much less smart than I think.

Yes, it does work.  Thank you for pointing that out.  I was reading off the steps on the squidguard site and did not even consider that there was an easy way ....

---


---
title: "SMS Service"
date: 2007-07-25
forum: Server Platforms
---

### Post by rory_fireshaper on 2007-07-25
I came up with a brilliant idea for a SMS Service (like sending in the ISBN of a product to a number and getting a text message back with the price of that item on various places online) but I don't know how to go about doing it. I've done research on setting up SMS Services on Google and I got Kannel (an SMS Gateway) but I really don't know what else I need.

Can someone help or at least point me in the right direction?

---

### Post by twistedtwig on 2007-07-26
I guess you would need to build / buy / get a bot that crawls a lot of sites like amazon etc and searches by ISBN and retreives the information you require.  I guess some of these sites might have web service portals that you could connect to and get the information in a far nicer way the scanning pages but I have never looked at it.

You would either do this each time you get a request or store the results in a Local DB so you only need to refresh your info on a daily / weekly or what ever basis.

Then its  a case of pulling it all toghether and sending it in a compact for to the SMS

---


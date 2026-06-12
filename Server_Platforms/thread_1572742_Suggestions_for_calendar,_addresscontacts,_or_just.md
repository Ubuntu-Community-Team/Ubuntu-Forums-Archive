---
title: "Suggestions for calendar, address/contacts, or just general PIM server?"
date: 2010-09-11
forum: Server Platforms
---

### Post by penyuan on 2010-09-11
Good day,

In recent months I've been researching ways to detach myself from Google's tentacles, and realised that one of the hardest things is to migrate all my PIM information away from it.

Right now I really want to setup a tiny Ubuntu (but doesn't absolutely need to be Ubuntu, I am just more familiar with it) server myself (I already have a domain name) so that it can replace what I rely on Google for right now: calendar, contacts, and slightly less importantly, the todo list function.

I am intrigued by VIA's Artigo A1100 pico-itx computer ([http://www.via.com.tw/en/products/embedded/artigo/a1100/index.jsp](http://www.via.com.tw/en/products/embedded/artigo/a1100/index.jsp)) ([http://www.engadget.com/2010/04/20/vias-artigo-a1100-is-the-nettop-for-diyers/](http://www.engadget.com/2010/04/20/vias-artigo-a1100-is-the-nettop-for-diyers/)), because it is so small. I would love to setup the server once in a "set and forget" fashion, and also move the server easily if I relocate.

I am also looking for the most Free (as in freedom) solution possible without too much manual tinkering. I have experience building PCs, installing OS (plus a Mac Mini web/file server once), compiling software, tiny bit of shell scripting, but that's about it.

Once the server is setup, I would like to be able to use Thunderbird (or equivalent) to sync my contacts and calendar with it, while keeping local copies in case my client computer does not have Internet connection.

Ideally, I would also like to sync my iPhone's calendar and contacts with the server, too. Again also having a local copy on the iPhone for offline access.

So far I have stumbled upon Bedework ([http://www.bedework.org/](http://www.bedework.org/)) for CalDAV calendaring, but it looks like overkill (or not)? As for contact management I only know of OpenLDAP but lots of manual configuration seems needed?

Does anyone have any suggestions/experience in this regard? I would appreciate any help on making setting up such a server as easy as possible. I am eager to get this done ASAP so I no longer need to sign away my life to Google. :)

Thank you very much!!

---

### Post by thingy on 2010-09-11
You could setup a Zimbra server on Ubuntu ([http://www.zimbra.com/learn/]("http://www.zimbra.com/learn/"))

To better understand what you can do with it, play with their online demo here: [http://www.zimbra.com/products/hosted_demo.php]("http://www.zimbra.com/products/hosted_demo.php")

Unfortunately, it looks like you have to register to use the hosted demo environment. :-|

---

### Post by penyuan on 2010-09-11
> **thingy said:**
> You could setup a Zimbra server on Ubuntu ([http://www.zimbra.com/learn/](http://www.zimbra.com/learn/))

To better understand what you can do with it, play with their online demo here: [http://www.zimbra.com/products/hosted_demo.php](http://www.zimbra.com/products/hosted_demo.php)

Unfortunately, it looks like you have to register to use the hosted demo environment. :-|

Thanks for the link, it looks very promising!

However, the open source version of Zimbra does not support syncing to iPhones, which I would prefer. Or do you know if there is a way to do it without going through Zimbra?

Again thanks for the tip, but if there are alternatives I would still love to know!

---

### Post by Mr.Kappa on 2011-07-15
Also I want to detach from google (i'm using an android phone), have you find a solution??


Ok I've found out SOGo ([http://www.sogo.nu]("http://http://www.sogo.nu")) that uses the funambol app on android/iphone/whateveryouhave , it's fantastic!

---

### Post by penyuan on 2011-07-15
Unfortunately, after all this time I still haven't found a good solution. At least not one that doesn't involve serious tweaking and configuration.

Zimbra server didn't work well because I need to pay extra for mobile device sync functionality.

I've also looked into SOGo (lots of configuration needed, it doesn't work out of the box), Citadel groupware (works, but poor mobile device support), and Kolab (can't get it to send mail).

This has become very frustrating for me, as there really doesn't seem to be a good out of the box solution to sync your calendars and contacts other than relying on an untrustworthy, freedom-unfriendly, cloud solution like Google...

If anyone can contribute ideas and experience that would be great! Thanks.

---

### Post by p2ranger on 2011-07-15
There's a podcast I listen to called The Linux Action Show. They had a podcast recently that talked about building your own cloud system and some options they have come across

[http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/](http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/)

There's also the Amahi servrer they talk about in this episode

[http://www.jupiterbroadcasting.com/9531/amah-server-review-las-s17e04/](http://www.jupiterbroadcasting.com/9531/amah-server-review-las-s17e04/)

Hope this gives you some ideas. I would like to separate from Google as well, but their services are at the cost of my privacy, but they work for me

Jason

---

### Post by penyuan on 2011-07-16
> **p2ranger said:**
> There's a podcast I listen to called The Linux Action Show. They had a podcast recently that talked about building your own cloud system and some options they have come across

[http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/](http://www.jupiterbroadcasting.com/8506/build-your-cloud-pt1-las-s16e10/)

There's also the Amahi servrer they talk about in this episode

[http://www.jupiterbroadcasting.com/9531/amah-server-review-las-s17e04/](http://www.jupiterbroadcasting.com/9531/amah-server-review-las-s17e04/)

Hope this gives you some ideas. I would like to separate from Google as well, but their services are at the cost of my privacy, but they work for me

Jason
I will take a look at them, thanks!

---


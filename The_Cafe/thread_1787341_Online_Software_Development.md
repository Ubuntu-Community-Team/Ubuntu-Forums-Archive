---
title: "Online Software Development"
date: 2011-06-21
forum: The Cafe
---

### Post by divergex on 2011-06-21
I am looking for opinions about open vs. closed source. I want to build a bookkeeping web app and because of it being hosted online I will need to charge to pay for bandwidth, and a modest profit would be desirable as well.

In general, would you ever use such an app/service if it were closed source? Why or why not?

---

### Post by Thewhistlingwind on 2011-06-21
If your using a client/server model, open or closed source doesn't really matter.

The meat of the application is under your control anyway.

---

### Post by sanderd17 on 2011-06-21
I would only use it if my data is not stuck with your service. e.g. if I can export it in a convenient way. Open or closed source does not matter that much, except when you use open source that you can give the client more details about the exportability.

---

### Post by divergex on 2011-06-21
I would definitely allow an easy export of your data. The service would be meant as a "launchpad" anyway, i.e. I would expect people to outgrow it at some point. I would not try to make it everything to everyone.

Would the closed/open source decision be different if it were a desktop app?

---

### Post by lulled on 2011-06-21
So you're planing to do something like WordPress: if you like, you can host your blog with them OR you can download the source, edit (if you will) and host your at your server?

---

### Post by divergex on 2011-06-21
Yes - the idea is to offer a hosted version at a very reasonable cost, say less than $50 a year, but also offer the ability to put it on your own server if you wish to use it internally. But as it's designed primarily for one-person businesses, those who choose to run it internally would most likely modify it to make it more robust.

---

### Post by lulled on 2011-06-21
Well, if it's a web application and you're going to make the app available for those who wants to host it themselves and they will be able to edit the app to better fit their needs, thus the source will be opened.

As for the chosen program language, it won't really matter, for either if you go with PHP, let's say, or .NET, you'll have to provide the source.

---

### Post by divergex on 2011-06-21
Sounds good. I have no problem providing the source. My next decision would be what license would best serve such a product? Straight GPL or something like Apache?

---

### Post by DangerOnTheRanger on 2011-06-21
Well, let's see:

Want to allow others to create proprietary products that use code from your project: Then you could use:

[LIST]
[*]The Apache license
[*]The BSD license (2 or 3 clause)
[*]The MIT license
[/LIST]
On the other hand, if you want all derivatives of your project to be FOSS software as well, you should use any of the following:

[LIST]
[*]The GNU GPL license
[*]The GNU AGPL license
[/LIST]
Personally, I'd go with the AGPL license, since the AGPL has an extra requirement specifying that if any derivatives of your (AGPL-licensed) program are made available for use from a server, then their (those derivative program's) source code must also be made available. Since you're making a web-centric app, this sounds like the way to go.

---

### Post by divergex on 2011-06-21
The AGPL does indeed sound appropriate. I will check it out.

---

### Post by Spice Weasel on 2011-06-21
[IMG]http://i.imgur.com/MgifXl.jpg[/IMG]

---


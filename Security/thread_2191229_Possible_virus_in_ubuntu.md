---
title: "Possible virus in ubuntu?"
date: 2013-12-01
forum: Security
---

### Post by danielaruiz-h on 2013-12-01
Hi! I'm new in ubuntu/linux, so please try to answer in a simple language. Here's my problem: I installed ubuntu on my netbook 7 months ago and I didn't have problems, but a week ago it happend's sometimes that when I open a link on internet, or click somewhere, automatically open a new window called "peliculas online" (online movies in spanish... i'm from Chile) an the web adress is the next: [http://lpcl.glomobi.com/lp.aspx?lpId=338481&partnerId=ck-apptv2&reqid=137119189&oid=2712&s1=69391|rs&xc=15357&xt=1](http://lpcl.glomobi.com/lp.aspx?lpId=338481&partnerId=ck-apptv2&reqid=137119189&oid=2712&s1=69391|rs&xc=15357&xt=1)

When I try to close it, it appears a message with the tipical: Are you sure you want to close this page? and when i close it, a new little window appears with a similar message. :confused: I have to close it again to make it really close. Does someone know how can i deactivate it? Pleasee help. Thanks !!!

---

### Post by bapoumba on 2013-12-01
I'm not familiar with "peliculas online" but may this is be something in your browser ? An extension, addon, Facebook app ? Please check in your browser plugins and FB apps and remove anything you do not recognize. Alternatively, create another user profile in your browser and see if you still see the pop up. Which browser are you using ?

---

### Post by sandyd on 2013-12-01
> **danielaruiz-h said:**
> Hi! I'm new in ubuntu/linux, so please try to answer in a simple language. Here's my problem: I installed ubuntu on my netbook 7 months ago and I didn't have problems, but a week ago it happend's sometimes that when I open a link on internet, or click somewhere, automatically open a new window called "peliculas online" (online movies in spanish... i'm from Chile) an the web adress is the next: [http://lpcl.glomobi.com/lp.aspx?lpId=338481&partnerId=ck-apptv2&reqid=137119189&oid=2712&s1=69391|rs&xc=15357&xt=1](http://lpcl.glomobi.com/lp.aspx?lpId=338481&partnerId=ck-apptv2&reqid=137119189&oid=2712&s1=69391|rs&xc=15357&xt=1)

When I try to close it, it appears a message with the tipical: Are you sure you want to close this page? and when i close it, a new little window appears with a similar message. :confused: I have to close it again to make it really close. Does someone know how can i deactivate it? Pleasee help. Thanks !!!
Its likely a browser extension or plugin, or a DNS hijacking

First, try running firefox in private browsing mode, do the popups appear then?

Then, if they still appear, start disabling all your browser extensions. If it dissapears then, then it is a browser extension causing the issue.

Else,
Try closing firefox and running
```

mv .mozilla mozilla-bak
```
and open firefox again

If that works without popups (note that your bookmarks and history, and rest of the stuff arent lost even if they dont show up in the browser), that means that it is a browser issue.

If its a browser issue, run the below, export the things that you need from Firefox
```

mv .mozilla mozilla-new
mv mozilla-bak .mozilla
```

Then, run the below to rename the infected firefox profile, and import the bookmarks, history, .etc that you exported from the old firefox.
```

mv .mozilla mozilla-old
```
The infected firefox profile is now named mozilla-old, and firefox should automatically generate a new profile for you

---


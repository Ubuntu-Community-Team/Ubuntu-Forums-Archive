---
title: "Squid - Creating custom error pages for Ubuntu"
date: 2006-10-11
forum: Server Platforms
---

### Post by TonyD on 2006-10-11
Hi Guys

I am new in the linux game,but managed to get a server up and running with postfix mail and squid. i would like to know how to create a custom error page when a user is denied to go to a specific site due to ACL controls. The squid home page does'nt have a clear instruction that pertains to Ubuntu and it would look better to have page come up with a logo and contact info than just a plain access denied page. Any help will be appreciated
:-D

---

### Post by AnRkey on 2008-01-11
The files you need to edit are in /usr/share/squid/errors/English/ and they are in HTML format. You can use nano to edit them.

I am still working on a way to add images though. If you figure it out then let me know.

Later,

AnRkey

---

### Post by TonyD on 2008-01-11
> **AnRkey said:**
> The files you need to edit are in /usr/share/squid/errors/English/ and they are in HTML format. You can use nano to edit them.

I am still working on a way to add images though. If you figure it out then let me know.

Later,

AnRkey

Thanks for the info. I tried it and it works great. Will work on getting an image in there. Should be possible by placing a link to an image thats available via server in the HTML file:confused:

Well i will give it a try:lolflag::guitar:

---

### Post by AnRkey on 2008-01-11
> **TonyD said:**
> ...Should be possible by placing a link to an image thats available via server in the HTML file:confused: ...:

I have tried putting this in just under the <BODY> section, <IMG SRC="logo.png" NAME="Compubliss" BORDER=0>

The image simply does not load though... I think I am getting close

R

---

### Post by AnRkey on 2008-01-11
OK I have a solution for this now. Here is the code for the error pages.

```

<IMG SRC="http://192.168.0.252/images/compubliss.png" NAME="Compubliss" BORDER=0><HR noshade size="1px">

```

I put the image on an Apache install that runs on the proxy server. And then I just added the image with html to the top of the error pages, just below the <BODY> tag.

Let me know if this helps you.

Later,

R

---


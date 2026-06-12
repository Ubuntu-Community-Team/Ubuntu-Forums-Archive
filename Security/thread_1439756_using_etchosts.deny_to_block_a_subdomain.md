---
title: "using /etc/hosts.deny to block a subdomain"
date: 2010-03-26
forum: Security
---

### Post by _nikolaos on 2010-03-26
My question is how to block a subdomain of a site. To make it as clear as possible, I'll give an example.

I am regularly entering this arbitrary site

_[http://www.somesite.abc/](http://www.somesite.abc/)_

which redirects me to this page

_[http://www.somesite.abc/index.html](http://www.somesite.abc/index.html)_

and this *index.html* takes an image from a subdomain which is a subfolder of itself, that is:

_[http://www.somesite.abc/images/forindex.jpg](http://www.somesite.abc/images/forindex.jpg)_

What I am asking is blocking the images to be taken, but not the main page itself, i.e. to block _[www.somesite.abc/images/](www.somesite.abc/images/)_ without blocking the overall _[www.somesite.abc](www.somesite.abc)_

My idea was to use the **/etc/hosts** file by redirecting to loopback address:

```

127.0.0.1 www.somesite.abc/images

```

but it looks as if it doesn't affect things at all.

Should I use it another way? Modifying **/etc/hosts.deny** maybe useful?

Thanks.

---

### Post by bodhi.zazen on 2010-03-26
You will probably have better success with a filtering proxy such as privoxy or squid.

---

### Post by adam814 on 2010-03-27
If it really is just one or two sites and you're using Firefox you could just right-click one of the images and check the box for "Block images from www.somesite.abc".

---

### Post by _nikolaos on 2010-03-27
I would not limit this to the images, but - generally - the contents of some subfolder of a site is to be blocked. It is not like most websites, where they pop-up a window ad, a flash ad etc, which is "borrowed" from another website.This is easy to block utilizing **/etc/hosts** file. The case I discuss is taking the useful pages from a website and dropping other elements and pages that are contained in its "subfolders".

I'll check *squid*, but it's not extra software for that job I am not looking for.

Thanks.

---

### Post by OpSecShellshock on 2010-03-27
If you're using Firefox with NoScript, there are options that let you go into pretty fine detail as to what gets allowed and what doesn't. One way to do that is to open the NoScript options, look on the general tab, select the box for "right click to something something" and then pick the radio button next to full addresses. That way the options for allowing scripts will be broken down into more detail than just 2nd level domains. If you want even more control, you can use the ABE feature, but I haven't messed around with that enough to give any practical advice on it.

That's only going to affect the browser, and the permissions will only be effective for the individual user who set them up (meaning you can't push the same settings down to all users).

Similarly, you can use AdBlock Plus, navigate to the page, press Shift+Ctrl+V to list all of the scripts and objects on the page, then go through and filter them one by one. This might actually suit your needs more since it presents full paths and allows you to customize what gets blocked.

---

### Post by _nikolaos on 2010-03-27
I'm using Chrome. An extra software solution is not in my mind. Thanks.

---

### Post by Da_Coynul on 2010-03-28
_nikalos,

Try **Adsuck** with a regex file:
[http://www.peereboom.us/adsuck/man.html]("http://www.peereboom.us/adsuck/")

I just posted a HOWTO that might help you get started here:
[http://linux4tw.wordpress.com/2010/03/28/howto-install-adsuck-on-ubuntu/]("http://linux4tw.wordpress.com/2010/03/28/howto-install-adsuck-on-ubuntu/")

I am also using Chrome and that's what got me interested in this.

:idea:

---


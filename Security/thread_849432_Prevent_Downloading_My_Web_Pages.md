---
title: "Prevent Downloading My Web Pages"
date: 2008-07-04
forum: Security
---

### Post by Brenda Watsen on 2008-07-04
Hi,

I installed the new sever version of ubuntu.
I setup my website and some folders in the directory: **/var/www/**
These are: 

[COLOR="Blue"][B]- index.html
- pics (pics/home_page)
- webfiles
[/B][/COLOR]
After I setup all this I asked a friend to look at my website.
He then told me that he had download all my contet from my website and I took a look.

Everything was the same. I was very scared of him.
At that moment I had a feeling about what a hacker can do:(.

**Questions**

1) Is there a solution to protect the content (data) in the /var/www/ directory from downloading (files, pictures, scripts)

Thank you very much :)

---

### Post by Dr Small on 2008-07-04
Maybe I'm not following you correctly, but HTTP is setup so things can be downloaded.

---

### Post by HermanAB on 2008-07-04
Yup, the whole purpose of a web site is to allow other people to download (read) your files.  In web server parlance a page read is known as a 'Get' request.  This is perfectly safe, since Apache doesn't normally allow things to be uploaded.

---

### Post by hyper_ch on 2008-07-05
I think his friend got prompted to download the indexfile instead of having it just displayed in the browser

---

### Post by Brenda Watsen on 2008-07-05
He download everything that was in the www directory.
Everything below:

[COLOR="Blue"][B]- index.html
- pics (pics/home_page)
- web files[/B][/COLOR]

So I think that if everyone can do this then they can put my content also in their web server.

I could have other things in the www directory that he could download.

He used a software called: HTTrack Website Copier
He show me all the content he downloaded from my web server.

I don't think this is a good thing.
If everybody can do this then we don't have to pay for a website.
We can just completely download a website we like. A website that  someone payed for we can simply sit on our chair and download it.

Is there someone who knows how to avoid people doing this?
Maybe someone know a website with information how to avoid this.

Thank you in advanced

---

### Post by szim90 on 2008-07-05
HTTrack's website has some suggestions to prevent people from using website downloaders (like HTTrack) - [http://www.httrack.com/html/abuse.html](http://www.httrack.com/html/abuse.html)

---

### Post by renesilva on 2008-07-06
If he could see the "Index of /" page of your directory he could download it all, just add an index file on each folder you have (index.html), that way he wont see that directory. Or you can configure the directives on that folder with some directives (like Options -Indexes) and he won't see this indexes Files. You can look more options [http://httpd.apache.org/docs/2.2/mod/core.html#directory]("http://httpd.apache.org/docs/2.2/mod/core.html#directory")

---

### Post by hyper_ch on 2008-07-06
if people can see the website on their computer then they can download it. There's no way around.

---


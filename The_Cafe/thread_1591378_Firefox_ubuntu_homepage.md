---
title: "Firefox ubuntu homepage"
date: 2010-10-09
forum: The Cafe
---

### Post by P4man on 2010-10-09
In a default install, you get this customised google/ubuntu homepage.

Now Im completely fine with using google, but this page is rubbish and the first thing I do is set the normal google homepage, so at least I have access to my mail, news, and more importantly, "non polluted" search results.

In doing so, am I depriving canonical of google's money?

---

### Post by CharlesA on 2010-10-09
They have no control with what you do after you install; I look at it as an "advertisment." *shrug*

One of the first things I do when I install is to change the home page.

---

### Post by P4man on 2010-10-09
Well, I fear its not just an advertisement, but also a major source of funding for canonical. I dont know if they get any money from google for my searches when I use the regular google homepage.

---

### Post by CharlesA on 2010-10-09
I'm not quite sure where this question would best be asked (and answered), maybe on launchpad?

---

### Post by lovinglinux on 2010-10-09
> **P4man said:**
> In a default install, you get this customised google/ubuntu homepage.

Now Im completely fine with using google, but this page is rubbish and the first thing I do is set the normal google homepage, so at least I have access to my mail, news, and more importantly, "non polluted" search results.

In doing so, am I depriving canonical of google's money?

Yes. This is the string from the home page search, which includes Ubuntu partner ID:

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=
```

The Google search engine in your search bar also has a partner identification:

```
http://www.google.com/search?client=ubuntu&channel=fs&q=
```
If you have removed both, then you could manually add the Ubuntu partner ID to your searches. The easiest way of doing that is to install [Add to Search Bar]("https://addons.mozilla.org/en-US/firefox/addon/3682/") extension, then visiting the default home page, right-clicking on the search field and adding it to your search bar.

---

### Post by andymorton on 2010-10-09
> **lovinglinux said:**
> Yes. Nevertheless, you can add the Canonical partner ID to your searches:

```
http://www.google.com/cse?cx=partner-pub-9300639326172081%3Ad9bbzbtli15&ie=UTF-8&sa=Search&q=
```

The easiest way of doing that is to install [Add to Search Bar]("https://addons.mozilla.org/en-US/firefox/addon/3682/") extension, then visiting the default home page, right-clicking on the search field and adding it to your search bar.

Sadly, the add on isn't available for FF 4 beta 6. Hopefully it will be updated soon.

---

### Post by P4man on 2010-10-09
thanks lovinglinux, thats what I feared. Canoncial is doing themselves a great disservice by not providing a homepage that people might actually keep.  Just provide the standard google homepage and perhaps add a ubuntu logo or some ubuntu search to it.

Anyway, Ill add the ubuntu client line, but Id be surprised more than a handful of people do, while I expect a vast number to change their homepage. I do almost all my searches from the homepage and not the searchbox.

edit: doesnt the "Ubuntu firefox modification" plugin take care of this? It should!

---

### Post by lovinglinux on 2010-10-09
> **andymorton said:**
> Sadly, the add on isn't available for FF 4 beta 6. Hopefully it will be updated soon.

That is provided by Ubufox extension, which is not compatible with FF 4 yet.

Keep in mind that Google partnership is also an important revenue stream for Mozilla, so using the Ubuntu home page for searches, probably deprives Mozilla from receiving the revenue, since it doesn't include the Firefox client in the string.

Here is the Mozilla string:

```
http://www.google.com/search?ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&q=
```

---

### Post by lovinglinux on 2010-10-09
> **P4man said:**
> thanks lovinglinux, thats what I feared. Canoncial is doing themselves a great disservice by not providing a homepage that people might actually keep.  Just provide the standard google homepage and perhaps add a ubuntu logo or some ubuntu search to it.

Anyway, Ill add the ubuntu client line, but Id be surprised more than a handful of people do, while I expect a vast number to change their homepage. I do almost all my searches from the homepage and not the searchbox.

edit: doesnt the "Ubuntu firefox modification" plugin take care of this? It should!

You could modify the home page using Stylish.

I don't use the home page, my searches are all done through the search bar. To be honest, I never thought about this until I replied to your thread. Now I have a dilemma: add Ubuntu or Firefox string. I guess I will add both and alternate my searches.

---


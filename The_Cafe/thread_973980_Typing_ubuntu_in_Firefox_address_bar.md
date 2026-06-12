---
title: "Typing ubuntu in Firefox address bar"
date: 2008-11-07
forum: The Cafe
---

### Post by RobsterUK on 2008-11-07
I'm not really sure where this post belongs.

I've got into the habit over the last year or so of typing web searches into the Firefox address bar, especially if its one word that I know will take me straight to the site I want like "youtube" "amazon" "ebay"

I noticed today that this doesn't work if you type "ubuntu"

Does anyone know why this is, and/or any other examples where this doesn't work. At first I thought it might be that the word is too short, but some of the other ones that work are the same length or shorter.

---

### Post by Joeb454 on 2008-11-07
It takes me straight to [http://www.ubuntu.com](http://www.ubuntu.com)

---

### Post by scragar on 2008-11-07
"ubuntu" redirects me to ubuntu.upc.edu/
"ubuntu linux" redirects me to ubuntu.com

honestly though, it's gonna be less effort to use ctrl+enter to have it put the .com in, rather then typing linux to go along side it.

---

### Post by nomasteryoda on 2008-11-07
The reason you are getting directed to a different URL is your DNS server's cache is pointing to the wrong location.

That search box in Firefox uses Google on my ISP, but when I'm traveling I get sent to another search engine. If you don't believe me, try replacing your DNS entries in the network settings with OpenDNS IP addresses then restart the network and try searching from the address bar. You will be directed to the OpenDNS search engine.

---

### Post by Joeb454 on 2008-11-07
> **nomasteryoda said:**
> The reason you are getting directed to a different URL is your DNS server's cache is pointing to the wrong location.

That search box in Firefox uses Google on my ISP, but when I'm traveling I get sent to another search engine. If you don't believe me, try replacing your DNS entries in the network settings with OpenDNS IP addresses then restart the network and try searching from the address bar. You will be directed to the OpenDNS search engine.

That's what OpenDNS does. You can disable this, I emailed their support about it :)

And I always use the shortcuts for .com (and .org and .net)

That said, I can just type "uf" to bring me here ;)

---

### Post by RobsterUK on 2008-11-07
> **nomasteryoda said:**
> The reason you are getting directed to a different URL is your DNS server's cache is pointing to the wrong location.

That search box in Firefox uses Google on my ISP, but when I'm traveling I get sent to another search engine. If you don't believe me, try replacing your DNS entries in the network settings with OpenDNS IP addresses then restart the network and try searching from the address bar. You will be directed to the OpenDNS search engine.

Hmm that's interesting. I thought the reason it queried Google when you type in the address bar, was that firefox was set to do that rather than it being the response of the DNS server.

In firefox about:config there is a keyword.url setting you can use to change the search engine it uses.

When I type "ubuntu" I end up with the error mentioned and [http://ubuntu/](http://ubuntu/) in the address bar.

EDIT: Ok I see what your saying. Firefox only queries a search engine if the DNS server doesn't return a result, and for some reason my DNS server is returning a result for "ubuntu" how strange. It became clear when I tried changing keyword.url to use yahoo, and the same thing happened.

---

### Post by brucewagner on 2008-11-07
> **Joeb454 said:**
> That said, I can just type "uf" to bring me here ;)

'uf' takes me to [http://www.ufl.edu](http://www.ufl.edu)

What do you mean, '...use the shortcuts'...?

---

### Post by Joeb454 on 2008-11-07
> **brucewagner said:**
> 'uf' takes me to [http://www.ufl.edu](http://www.ufl.edu)

What do you mean, '...use the shortcuts'...?

If you bookmark something you can assign it keywords. Try it and see :)

---

### Post by picpak on 2008-11-07
I think this only happens if your hostname is ubuntu. For example, if you open up a terminal:

```
kim@**ubuntu**:~$ 

```

The bolded part that says "ubuntu" is your hostname.

---

### Post by Joeb454 on 2008-11-07
> **picpak said:**
> I think this only happens if your hostname is ubuntu. For example, if you open up a terminal:

```
kim@**ubuntu**:~$ 

```

The bolded part that says "ubuntu" is your hostname.

The hostname of your computer has no effect on the way firefox works :)

---

### Post by schauerlich on 2008-11-07
> **Joeb454 said:**
> That said, I can just type "uf" to bring me here ;)

Funny, typing "f u" brings me to your profile page...

---

### Post by Martje_001 on 2008-11-07
> **EDavidBurg said:**
> Funny, typing "f u" brings me to your profile page...
:/

---

### Post by Joeb454 on 2008-11-07
> **EDavidBurg said:**
> Funny, typing "f u" brings me to your profile page...

Watch it....

---

### Post by wolfen69 on 2008-11-07
> **Joeb454 said:**
> If you bookmark something you can assign it keywords. Try it and see :)

don't need it. it doesn't any faster than the fast dial add on. instant access to all my fav sites.

---

### Post by kef_kf on 2008-11-07
> **Joeb454 said:**
> That's what OpenDNS does. You can disable this, I emailed their support about it :)


how can i disable this? its the only reason im not using opendns right now.

---

### Post by Joeb454 on 2008-11-07
> **kef_kf said:**
> how can i disable this? its the only reason im not using opendns right now.

I never got round to trying it, due to a reinstall, but here's what I got back from their tech support:

[QUOTE=OpenDNS]To disable the guide and enable your browsers default search engine, please disable:
*typo correction,
*filtering of .cm wildcard,
*OpenDNS proxy.[/QUOTE]

---

### Post by Npl on 2008-11-07
> **Joeb454 said:**
> The hostname of your computer has no effect on the way firefox works :)AFAIK it does. if you type "something" in the addressbar of a browser it will 
1) try to resolve "something" in your Local Network
2) try resolving a few pre-/post-fixes ([www.something.com](www.something.com), [www.something.net](www.something.net), etc).

So having your hostname called "something" might prevent your browsers from seeking for the addresses in 2.

---

### Post by schauerlich on 2008-11-08
> **joeb454 said:**
> watch it....

<33

---

### Post by kernelhaxor on 2008-11-08
What it does is: if you type in a phrase in the address bar .. it does a google search and redirects you to the first link in the search results ..

I tried it for a bunch of phrases .. all the pages that I was redirected to were the first search results for the respective phrases

---


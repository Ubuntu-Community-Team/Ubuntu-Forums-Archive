---
title: "Help build a search engine"
date: 2008-05-11
forum: The Cafe
---

### Post by hellmet on 2008-05-11
I'm absolutely not sure if this is even remotely possible, but I was thinking of starting a web-search engine for Indian sites only. That is the Indian domain name extensions like .in, .co.in etc. This idea is similar to the Chinese website Baidu for chinese websites.

I was wondering if someone would like to join me in this project, and if people had ideas on how to write and further build a search engine.

I'm not a coder, but I learn things very fast, and am from a CS background with sound knowledge in C. 

Appreciate your opinions!!

---

### Post by Mateo on 2008-05-11
i'm in the planning stages of a search engine myself.  not sure how much you've researched it, but a search engine in made up of 3 parts:  crawler, indexer, search engine.  The best opensource crawler I've found is Heritrix, which is archive.org's crawler. i'd recommend modifying that rather than starting from scratch.

---

### Post by LaRoza on 2008-05-11
> **hellmet said:**
> I'm absolutely not sure if this is even remotely possible, but I was thinking of starting a web-search engine for Indian sites only. That is the Indian domain name extensions like .in, .co.in etc. This idea is similar to the Chinese website Baidu for chinese websites.

I was wondering if someone would like to join me in this project, and if people had ideas on how to write and further build a search engine.

I'm not a coder, but I learn things very fast, and am from a CS background with sound knowledge in C. 

Appreciate your opinions!!

You should for best results use an established search engine like google: [http://www.google.com/intl/hi/](http://www.google.com/intl/hi/)

You can customize the searches for it to restrict it to certain types of sites. It would be better than anything a single person could do.

---

### Post by hellmet on 2008-05-11
> **LaRoza said:**
> You should for best results use an established search engine like google: [http://www.google.com/intl/hi/](http://www.google.com/intl/hi/)

You can customize the searches for it to restrict it to certain types of sites. It would be better than anything a single person could do.
I wouldn't want to use Google for anything. 

Lemme have a look at Heritrix

---

### Post by LaRoza on 2008-05-11
> **hellmet said:**
> I wouldn't want to use Google for anything. 


Does it not work well for Indian sites?

---

### Post by Joeb454 on 2008-05-11
I don't know, but I found [http://www.google.co.in/](http://www.google.co.in/)

It allows you to search for pages just from India

---

### Post by hellmet on 2008-05-11
> **Joeb454 said:**
> I don't know, but I found [http://www.google.co.in/](http://www.google.co.in/)

It allows you to search for pages just from India

I'd be glad if you guys could stop giving me alternatives. I don't want anything to do with Google. I'm not looking at solving : How do I search Indian websites?. I want to solve : How do I build my own search engine for Indian domain names?
Enough of monopolies ruling everything.

---

### Post by zipperback on 2008-07-03
> **hellmet said:**
> : How do I build my own search engine for Indian domain names?

There are a number of things that you need to consider when you are going to build a search engine.

How large is your server farm going to be?

What operating system are you going to be running for your server?

What programming language do you have the most experience with?

Do you have a solid working understanding of how to write code that can properly thread?

How much money do you have to invest in this project? 

How many programmers do you intend to hire to build this system?

Will this project be released as an open source application available freely for people to download? And if so, what license do you intend to release it under. If not, why not?


As far as using the system just for Indian domain names, that isn't a problem really. Just create a filter that checks for the specific TLD that you want to allow. For example .in is acceptable but .com would be rejected.

If you really do want to build your own search engine, then my advice is to create a detailed wish list of everything that you want it to do, and then once you have that done, go through it and prioritize the list from the most important items to the least important items. 

Then create a solid code base, with the most important items on your list first. Once you are sure that your code base is bug free, then slowing begin adding new features to it over time, making sure that you fully complete the new feature that you are adding to the system, and that it too is bug free before you move on to the next feature.

Creating a search engine isn't just something you can sit down and code in a few hours. If you want to create a serious search engine which can be as effective as google.com, yahoo.com, live.com, or any of the other big search engines, you will need to carefully plan your system out before you write any code for it.

- zipperback
:popcorn:

---

### Post by Dr Small on 2008-07-03
> **LaRoza said:**
> You should for best results use an established search engine like google: [http://www.google.com/intl/hi/](http://www.google.com/intl/hi/)

You can customize the searches for it to restrict it to certain types of sites. It would be better than anything a single person could do.
```
Failed to Connect
Firefox can't establish a connection to the server at www.google.com.
```

:D

---

### Post by mech7 on 2008-07-03
What about:

[http://search.wikia.com/wiki/Search_Wikia](http://search.wikia.com/wiki/Search_Wikia)

---

### Post by fatality_uk on 2008-07-03
> I want to solve : How do I build my own search engine for Indian domain names?

The reason other were suggesting other sites is I think they have a good understanding of the complexities of what your are looking to do. It isn't something you could hope to do effectively without a great deal of help and I would suggest it will take at least 12-18 months before you have any working model to deploy.

If you were to tackle a project like this, it would essentially be broken into these parts:

1: Understand what you wanted to have stored in your database. URL, site description etc. Code the DB according to that.

2: Create a crawler. A program that will analyse each web page submitted to your site and strip data such as meta tags,URl etc (See ref 1)

3: Write the code for a search. This is a tough part. You cant just > SELECT * FROM my_ind_db WHERE user_search LIKE my_ind_db.descriptionMost searches take place on views built from massive tables.

[http://www.google.co.in/search?hl=en&q=ubuntu&btnG=Google+Search&meta=](http://www.google.co.in/search?hl=en&q=ubuntu&btnG=Google+Search&meta=)

Just look at the link above. This results look so simple, it's not. You have to sort those pages by some sort of ranking system. Have relevance built into the search code.

4: Promote the site. When you start, your database will be empty. You have to decide how you are going to fill that up?

---

### Post by hellmet on 2008-07-08
I think I found something interesting here. [www.guruji.com](www.guruji.com) does exactly what I wanted to do!!

---

### Post by mech7 on 2008-07-08
Also there is search monkey.. if you want to customize your search engine :D

[http://developer.yahoo.com/searchmonkey/](http://developer.yahoo.com/searchmonkey/)

---


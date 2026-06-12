---
title: "Smart scopes"
date: 2013-06-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-06-08
As it just landed will keep short the neg. comments
There are some interesting & useful scopes that myself *may* make use of  if continuing with unity past 13.04 (50-50 there
Some of the things looking for took a bit to figure out but otherwise worked fairly well
(ex. - getting results for manpages thru the manscope - needed category of 'code', scope of manpages, searches on only manpage name itself

What will eventually become tiresome here is that it, (smart scopes) decides what categories & scopes to enable as one types  a search. There seems to be no way yet or ever to allow the user to set & tell 'smart' to leave alone. So alot of time can be lost disabling/enabling to fine tune/limit results

There are some available options (schemas/keys), but they are limited & not as useful as they could be..
2 examples, don't expect much positive response
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189058](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189058)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189060](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189060)

the music lens - 
With a whole host of new music player scopes (good deal there), the music lens can become a complete joke if one installs more than 1 supported player, There is no longer a "source" filter, so the more players installed the more duplicated results with no clear way to tell which result, (icon/thumbnail),  goes to what player
[https://bugs.launchpad.net/bugs/1189038](https://bugs.launchpad.net/bugs/1189038)

---

### Post by P-I H on 2013-06-09
I have all my data, music, videos on an Ubuntu server using NFS. Current version of the lenses don't search the folders on the server, which should be quite useful.

---

### Post by mc4man on 2013-06-16
At least here find a number of the new scopes useful, many of which require online access enabled &  the 'more-suggestions scope'

However have no interest in products from Amazon, Target, ect from being displayed, ever.
Those are not from a packaged scope so to remove am doing in dconf as in screen.

Got their names from here - [https://productsearch.ubuntu.com/smartscopes/v1/search?q=](https://productsearch.ubuntu.com/smartscopes/v1/search?q=)

---

### Post by mc4man on 2013-08-29
2 more "more-suggestions scopes" that I've no use for here that can be 'blacklisted' in gsettings
more_suggestions-ebay.scope
more_suggestions-etsy.scope

---

### Post by philinux on 2013-10-12
[http://www.webupd8.org/2013/10/how-to-disable-amazon-shopping.html](http://www.webupd8.org/2013/10/how-to-disable-amazon-shopping.html)

> In Ubuntu 13.10 (Saucy Salamander) you can't remove the Shopping lens but there is another way to achieve the same thing and it seems this isn't obvious because I've seen quite a few users complaining about it.

[edit]. That being said I think it is simpler. Just toggle the "include online search results" in Security and Privacy settings found under the search tab.

---


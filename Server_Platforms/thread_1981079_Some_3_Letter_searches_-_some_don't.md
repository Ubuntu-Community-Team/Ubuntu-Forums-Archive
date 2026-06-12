---
title: "Some 3 Letter searches - some don't?"
date: 2012-05-16
forum: Server Platforms
---

### Post by Bluesplayer on 2012-05-16
Hi

I altered the my.conf file found in /etc/mysql/ and added this:

```
[mysqld]
ft_min_word_len=2
```I then rebuilt the search index using this:

```
REPAIR TABLE table_name QUICK
```I restarted mysql. 
When I checked the variables on the dabatase ft max word len is now set to 2.

I restarted mysql.

Some words I can search for so 3 letter word searches are working but for a word like 'For' (which I wanted to work) I get nothing?  Is this a mysql limition as it is a too popular word or something?  Maybe I need to rebuild the index differently?

Regards

---

### Post by rubylaser on 2012-05-16
What does your Query look like?

---


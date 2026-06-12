---
title: "Network Search Engine with Beagle"
date: 2009-03-31
forum: Server Platforms
---

### Post by R.Bucky on 2009-03-31
I have built an intranet at my place of employment and used Beagle with the web interface for an internal search engine. It has indexed our Exchange Server with ease. However, the links it provide go something like file:///media/drivename/PUBLIC/etc/etc.pdf. The search engine thinks it is on the local Ubuntu Server (and, it is...). I need to change the way the search results are linked to make it a letter drive so that our XP machines can simply retrieve the file. So, instead of file:///media/drivename/PUBLIC/etc/etc.pdf, I want it to read H:/PUBLIC/etc/etc.pdf. 

Has anyone toyed with Beagle in this respect? HELP - - 

Or, can someone suggest an alternative as a network only search engine?

---

### Post by sammy_pal on 2009-04-02
You can try [Xapian-omega]("http://trac.xapian.org/wiki/Omega") as an alternative.

---

### Post by R.Bucky on 2009-04-02
Xapian - I will take a look at that today. I found that someone rewrote a bit of the peagle.php server script to solve the my problem. It is located [here]("http://www.kde-apps.org/content/show.php?content=38289&forumpage=2&PHPSESSID=56f6e905355299903bbcaa1bc1a2a7ad") on the Peagle kde apps page. However, Peagle is back to the search result "Unknown" that it provided for me last year. I was never able to figure out why Peagle never gave me results. But, that is another thread.

So, the fix for Beagle returning appropriate links while using the Peagle server while indexing files on a Samba share is:

```
function link_open($url)
{
global $set; $url=str_replace("/home/","////SambaServer/",$url);
switch($set["desktop"])
{
case "kde":case "gnome":case "mailcap":case "custom":return("/open?o=".rawurlencode($url));break;
case "link":return($url);break;
}
}
```

Find and replace the above code in the peagle.php. And, you should be good!!

Now, on the Xapian!

---


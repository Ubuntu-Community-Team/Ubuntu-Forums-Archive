---
title: "Apache Symlink problem"
date: 2006-04-10
forum: Server Platforms
---

### Post by SleightfulMind on 2006-04-10
I have created a PHP file in a directory entitled link.php and a symlink in the same directory entitled abcd. The symlink points to link.php. Because the abcd symlink does not have the .php suffix, it does not parse the target file as a PHP file, instead it just outputs the file as if it were an html file. I tried changing the symlink to abcd.php and then it works fine. Is there a way to make apache parse the resultant file as PHP instead of html? I want to do this so that I can generate search-engine friendly permalinks to content. That way I can make a URL [http://mysite.tld/abcd](http://mysite.tld/abcd) which is symlinked to news.php. The news.php file then discovers that it was called by the uri /abcd and can resolve this ID to a news article and spit out the approriate content.

It is possible for me to simply add .php to the end of the symlink, but I would prefer not to do this.

Basically, I want apache to determine the mime-type of the resultant file first, then parse it accordingly. Furthermore, I want apache to pass the appropriate variables to the script so that it can see it was called by the URI /abcd.

Thanks for any help!

---

### Post by adamkane on 2006-04-10
This is an intermediate Apache/PHP topic. If you don't receive an answer, check out the online Apache and PHP documentation.

Sorry for not being very helpful. I'm sure there are people here who know more than I do.

---


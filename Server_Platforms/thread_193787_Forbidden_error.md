---
title: "Forbidden error"
date: 2006-06-10
forum: Server Platforms
---

### Post by Cornmuffin on 2006-06-10
I recently set up an apache2 web server with ubuntu on an old slot 1 p3 I had laying around.  I have eveything set up and working and I can access the site and see it just fine.  I do have *some* html experience but this is the first time I've used it to actually create a fully functioning webpage.  In my /var/www directory I have an html doc called "index.html".  It just has some very basic code in it now that I have been using to practice html with.  I wasn't having any problems until I tried to place a link on the the site (linking to another page on my server).  Here is the HTML in index.html:

```
<html>
<title> Watch Out, I'm on the Web </title>
<a href="testpage.html"><img border = "0" src="testlink.jpg"></a>
</html>

```

When I go to my main page, that all looks and functions just as it should.  The problem is when I click on the link, I get a 403 forbidden error saying I don't have permission to access /testpage.html on this site.  Is there something I have to change in an appache configuration file to allow general access beyond the site's index?  Thanks for your help!

---

### Post by lcg on 2006-06-10
[QUOTE=Cornmuffin]I recently set up an apache2 web server with ubuntu [...]
I wasn't having any problems until I tried to place a link on the the site (linking to another page on my server).  Here is the HTML in index.html:

```
<html>
<title> Watch Out, I'm on the Web </title>
<a href="testpage.html"><img border = "0" src="testlink.jpg"></a>
</html>

```

When I go to my main page, that all looks and functions just as it should.  The problem is when I click on the link, I get a 403 forbidden error saying I don't have permission to access /testpage.html on this site.  Is there something I have to change in an appache configuration file to allow general access beyond the site's index?  Thanks for your help![/QUOTE]
What happens if you try to access testpage.html directly from your browser without following a link (by entering the complete URL)? Does apache have read permission for testpage.html? If not, try making it world readable. Does that solve your problem?

HTH,
Lars

---

### Post by Cornmuffin on 2006-06-11
](*,)   Yeah that worked....I just knew it was going to be some simple oversight such as that.  Thanks for your help!

---

### Post by lcg on 2006-06-11
[QUOTE=Cornmuffin]Yeah that worked....I just knew it was going to be some simple oversight such as that.  Thanks for your help![/QUOTE]
You're welcome.
And believe me, you aren't the first to struggle with this problem! ;)

Lars

---


---
title: "Frameset html shows up instead of my code"
date: 2009-09-07
forum: Server Platforms
---

### Post by Kaparzo on 2009-09-07
Hi folks,

Still new to using Apache2 on Ubuntu-Server.

I'm trying to get my site verified by google and they required a META tag included on the main page of the site.

I've copied and pasted as directed onto my index.html file, but google can't identify it.

The webpage works fine with any browser, however...

When I used web-sniffer.net to see what default output my page is giving off, it gives me this: 

> <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
<html>
<head></head>
<frameset rows="*">
<frame src="http://72.43.555.555" frameborder="0">
<noframes>
<p>This frameset document contains:
<ul>
<li><a href="http://72.43.555.555">http://72.43.555.555</a>
</ul>
</noframes>
</frameset>
</html>


When I view source the page, that same code comes up, although the page is full of HTML code that I'm using when you're viewing it graphically.

Is this some sort of security feature in apache2?  Can I temporarily disable it?

---

### Post by Kaparzo on 2009-09-12
bump

can't even validate my code on w3 schools

---

### Post by wojox on 2009-09-12
Web sniffer is supposed to show you the code.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
<html>
<head>
<title></title>
</head>
<frameset rows="*">
<frame src="http://72.43.555.555" frameborder="0">
<noframes>
<p>This frameset document contains:
<ul>
<li><a href="http://72.43.555.555">http://72.43.555.555</a>
</ul>
</noframes>
</frameset>
</html> 

```

Try that you left out <title></title> for validation.

---

### Post by hessiess on 2009-09-12
Unless you are using a frameset deliberately then you shouldn't be getting one, I am not aweare of an Apache option which serves pages in a frameset.

---

### Post by Kaparzo on 2009-09-16
> **wojox said:**
> Web sniffer is supposed to show you the code.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
<html>
<head>
<title></title>
</head>
<frameset rows="*">
<frame src="http://72.43.555.555" frameborder="0">
<noframes>
<p>This frameset document contains:
<ul>
<li><a href="http://72.43.555.555">http://72.43.555.555</a>
</ul>
</noframes>
</frameset>
</html> 

```

Try that you left out <title></title> for validation.

thing is that my original code has <title>Something</title> in it

its really weird, view source on this page to see waht i mean:

[http://www.vanguardnyc.net]("http://www.vanguardnyc.net")

---

### Post by hessiess on 2009-09-17
The website is available without the frame set at:

[http://72.43.110.183/](http://72.43.110.183/)

validate:

[http://validator.w3.org/check?uri=http%3A%2F%2F72.43.110.183&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2F72.43.110.183&charset=%28detect+automatically%29&doctype=Inline&group=0)

---

### Post by Kaparzo on 2009-09-17
> **hessiess said:**
> The website is available without the frame set at:

[http://72.43.110.183/](http://72.43.110.183/)

validate:

[http://validator.w3.org/check?uri=http%3A%2F%2F72.43.110.183&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2F72.43.110.183&charset=%28detect+automatically%29&doctype=Inline&group=0)

wow thanks

very strange

---

### Post by hessiess on 2009-09-17
> **Kaparzo said:**
> wow thanks

very strange

I guess the problem must be with your DNS provider.

---

### Post by Kaparzo on 2009-09-21
> **hessiess said:**
> I guess the problem must be with your DNS provider.

We figured it out, the DNS provider has a "cloaking" feature

[http://www.gkg.net/domain/support/faq/parking.html#Anchor-What-2](http://www.gkg.net/domain/support/faq/parking.html#Anchor-What-2)

Thanks everyone

---


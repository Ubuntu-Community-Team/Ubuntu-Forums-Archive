---
title: "Looking for a really, really nice person to help me with my site."
date: 2007-01-09
forum: The Cafe
---

### Post by CheshireMac on 2007-01-09
Hey folks. I own a blog that I'm looking to make famous (This is a serious endeavour). It's a music review blog, and I'm doing a lot of interviews with artists (some are pretty big), but all I know how to do is write . . .I'm a journalist, and a hobby-programmer . . .but I'm lousy with web-design. 
I'm looking for someone that would be interested in helping me in this project (It's really fun, if you like Jazz/Blues). The problem I have is that the site is so blah . . .it needs some glam, and it needs some knowledge of websites. ~LOL~ Links, sections, things like that. 

[http://jazzreviewed.blogspot.com]("http://jazzreviewed.blogspot.com")

The help would really be appreciated, and it'll be really fun working with me, I promise. ~LOL~ 

Another thought that I had was starting a thread about suggestions, so let's do that also. :)

---

### Post by Biggus on 2007-01-09
Mmmm you could maybe stick in a couple of meta tags at the top like :

<meta content='put description here' name='description'/>
<meta content='put, keywords, here' name='keywords'/>
<meta content='ALL' name='robots'/>
<meta content='Global' name='distribution'/>
<meta content='General' name='rating'/>

for starters. It makes no difference to the reader, but Google will like to see them when it crawls your site eventually.

---

### Post by CheshireMac on 2007-01-09
> **Biggus said:**
> Mmmm you could maybe stick in a couple of meta tags at the top like :

<meta content='put description here' name='description'/>
<meta content='put, keywords, here' name='keywords'/>
<meta content='ALL' name='robots'/>
<meta content='Global' name='distribution'/>
<meta content='General' name='rating'/>

for starters. It makes no difference to the reader, but Google will like to see them when it crawls your site eventually.

How do I insert those?

---

### Post by Biggus on 2007-01-09
It's in your blogger control panel.

I was gonna show ya how, but 'old' blogger is down just now.

I think you 'new' bloggers have a little tab which lets you edit the html at source.

You wanna insert these lines so it looks like

>  <link rel="alternate" type="application/atom+xml" title="And All That Jazz - Atom" href="http://jazzreviewed.blogspot.com/feeds/posts/default" />
<link rel="alternate" type="application/rss+xml" title="And All That Jazz - RSS" href="http://jazzreviewed.blogspot.com/feeds/posts/default?alt=rss" />
<link rel="service.post" type="application/atom+xml" title="And All That Jazz - Atom" href="http://www.blogger.com/feeds/4024165322828602259/posts/default" />
<link rel="EditURI" type="application/rsd+xml" title="RSD" href="http://www2.blogger.com/rsd.g?blogID=4024165322828602259" />
  

    <title>And All That Jazz</title>

[B]<meta content='put description here' name='description'/>
<meta content='put, keywords, here' name='keywords'/>
<meta content='ALL' name='robots'/>
<meta content='Global' name='distribution'/>
<meta content='General' name='rating'/>[/B]

    <style id='page-skin-1' type='text/css'>
/*
-----------------------------------------------
Blogger Template Style
Name:     Minima Black
Designer: Douglas Bowman
URL:      [www.stopdesign.com](www.stopdesign.com)
Date:     26 Feb 2004
Updated by: Blogger Team
----------------------------------------------- */

---

### Post by CheshireMac on 2007-01-09
> **Biggus said:**
> It's in your blogger control panel.

I was gonna show ya how, but 'old' blogger is down just now.

I think you 'new' bloggers have a little tab which lets you edit the html at source.

You wanna insert these lines so it looks like

So I want to open my whole blog as HTML and insert that? Okay . . .thanks. :)

---

### Post by em es on 2007-01-09
You have to go to your Blogger Dashboard and edit your template. Then click on the sub menu, I think it's called "edit HTML" and add your meta tags at the top. beneath the <html> and <title> tags and inside the <head> tags

This is the beginning of my Blog, it should be similar to yours:
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
  <head>
    <b:include data='blog' name='all-head-content'/>
    <title><data:blog.pageTitle/></title>
[COLOR="Red"]Put the tags Biggus told you about in here[/COLOR]
    <b:skin><![CDATA[/* 
 * Blogger Template Style
 * Name:     TicTac (Blueberry)
 * Author:   Dan Cederholm
 * URL:      www.simplebits.com
 * Date:     1 March 2004
 * Updated by: Blogger Team
*/

/* Variable definitions
   ====================
```

Make sure you edit the meta information Biggus told you, the important ones are: keywords, description and maybe author.

EDIT: It seems I should post a little faster in future...

---

### Post by CheshireMac on 2007-01-09
Got that taken care of. :) Thanks. While I was at it, I got NVU, and I've copied the HTML over to it and saved it for editing . . .now all I need to do is think of what I want to make this thing look like. ~LOL~

---

### Post by CheshireMac on 2007-01-09
Is Blogspot limited in it's fonts, backgrounds, etc? Or can I add new stuff from my own choosing in NVU and paste it to the Blogger?

---

### Post by CPtAJ on 2007-01-09
Well, if no one steps up I wouldn't mind giving you a hand. I'll drop you a line on msn.;)

---

### Post by Riyonuk on 2007-01-09
Its kinda plain...just black and white. And must you use blogspot? Is it at all possible to host it on your own server? It would look better without the banner up there. Add me on msn, I maybe can help.

---


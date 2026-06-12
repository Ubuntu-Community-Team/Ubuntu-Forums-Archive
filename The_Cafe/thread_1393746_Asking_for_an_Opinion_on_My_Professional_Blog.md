---
title: "Asking for an Opinion on My Professional Blog"
date: 2010-01-29
forum: The Cafe
---

### Post by Rob@ThePCWiz.info on 2010-01-29
Hello readers & potential responders.
I have recently created a blog on a subdomain of my website, and would like a few peoples opinions on how it looks. The blog is meant to promote myself as a potential employee, to potential employers, in a way that I personally have never seen before.

I blog about my goals and achievements, show off some of my work, and just tell people about my days in general, or what is on my mind.
In order to give potential employers a look into who I am, in a professional, modest way.

The blog is located at [http://rob.ThePCWiz.info]("http://rob.ThePCWiz.info") and i would appreciate all comments, questions, and suggestions.

---

### Post by Tibuda on 2010-01-29
don't use <marquee>

never

---

### Post by Rob@ThePCWiz.info on 2010-01-29
Why not use <marquee> ? i was kind of diggin it... i like it. does it not come up correctly in some browsers? I mean i could prolly just remove it fine... no problem.

---

### Post by Tibuda on 2010-01-29
> **Rob@ThePCWiz.info said:**
> Why not use <marquee> ? i was kind of diggin it... i like it. does it not come up correctly in some browsers? I mean i could prolly just remove it fine... no problem.

About <marquee>:
1. it is distracting and does never look good. it may look good for a kid club website, but not for professional website.
2. it is deprecated/non-standard tag. browsers only support it as legacy.

Some extra notes:
3. Avoid inline styles, use classes/ids and a separate css file. It looks dumb at first, but it makes a huge difference in the future when you start to work in big websites. I'm talking about those lines:
```
<div style="height:400;width:100%;overflow:auto;border-width:2;border:groove;">
<div style="border:2;height:75;width:100%;overflow:auto;border-width:2;border:groove;" align=center>
```
You could instead use (I'm using both id and class):
```
#maincontent { height:400;width:100%;overflow:auto;border-width:2;border:groove; }
.latest { border:2;height:75;width:100%;overflow:auto;border-width:2;border:groove; text-align: center; }
```
in the stylesheet
```
<div id="maincontent">
<div class="latest">
```
in the content. Much easier to read/understand those <div>s.

4. Those borders are ugly, and the main content needs some spacing/padding. Perhaps something like (using the same notation as the last example):
```
#maincontent { padding: 24px 48px; line-height: 1.5em; }
.latest { text-align: center; }
```
see how your site will look much better without the borders and with the extra spacing: [http://omploader.org/vM2U0Ng](http://omploader.org/vM2U0Ng) (I made the changes using Firebug, which is a neat tool for a webdesigner)

---

### Post by squilookle on 2010-01-29
to get to the resume, you have to mouse over downloads, then documents. it's simple and the menu is nicely done. 

however, i reckon very few potential employers are going to stay on the site long enough to figure that out and download it. you may wantg to consider having an even easier and more obvious link to it.

---

### Post by lisati on 2010-01-29
> **squilookle said:**
> to get to the resume, you have to mouse over downloads, then documents. it's simple and the menu is nicely done. 

however, i reckon very few potential employers are going to stay on the site long enough to figure that out and download it. you may wantg to consider having an even easier and more obvious link to it.

+1. One possibility would be to mention the download menu in your blurb.

---

### Post by koleoptero on 2010-01-30
And never call people "potential" anything, it's bad either way.

---

### Post by RabbitWho on 2010-01-30
Yeah scrolling marquee is sooo 1999, I had loads on my neopets website when I was 13. and it screams "I can't afford/can't use flash" and it's not very smooth on most computers, and I seem to remember that it didn't work at all or some people, but then that was 10 years ago so who knows if that's still true.

Too many fonts. 

For the entire rest of your life: Choose 2 fonts. Stick with them.

And the scroll boxes, uch, this is what it looks like on a wide-screen computer:

---

### Post by Sporkman on 2010-01-30
I like your menubar & menu pulldowns - very sharp looking.

---

### Post by Paqman on 2010-01-30
Argh! Marquee! Kill it!

A few points:
[LIST]
[*]Get rid of gimmicky markup such as marquee
[*]As mentioned above, define all your styles in a proper stylesheet
[*]Don't use javascript for layout, and make sure everything with js degrades gracefully
[*]People don't read websites, they scan them: full width text is difficult to scan. Go for about 6-10 words to a line max, and use a sans serif font. They're easier to read on screen. Grey on white isn't the best choice of colours either, go  for higher contrast.
[*]Don't host a "prank virus" on your site, it makes you look like a script kiddy
[*]Why is your "latest" section only 75px high? You've already got more content than it will fit with two items. Scroll bars just hide the content from your users, which will annoy them.
[*]You're use of borders is a little inconsistent. Your content on the page and your header don't line up at the right. Besides, what's the point in having a border on an area that spans the page anyway? Borders are there to help delineate content, there's nothing wrong with skipping them if they aren't needed.
[*]The amount of items you've got in your menu doesn't really call for a dropdown IMO. 
[*]If you're hoping to pick up work through this site, how do people contact you? Make it really obvious, put it on ever page. And include some content on the site detailing your skills (ie: more than just "I work on computers". People probably won't bother downloading your CV unless you give them a reason to.
[*]Check your code for W3C compliance for HTML and CSS, I wouldn't hire anyone for web work who hadn't bothered.
[/LIST]

---

### Post by Sporkman on 2010-01-30
> **Paqman said:**
> Argh! Marquee! Kill it!


:lol: ...before it gets to the Children!!

---

### Post by hessiess on 2010-01-30
If you are trying to use this site to advertise your ability's, your sending out a vary bad message because the design and functionality are awful.

Blog:
Use a decent blog CMS like word press, If you are writing your own CMS, its not doing you any favours;)

HTML:
DO NOT use deprecated tags like font, make your HTML validate with a XHTML strict DTD.

Layout:
Get rid of the scroll box.

LOL:
> and could easily create a social networking website

Just having a basic understanding of a database is NOT enough to implement a social networking website, web programming is a lot more complicated than it appears to be at first.

---

### Post by Barrucadu on 2010-01-30
Please, please, *please*: get rid of the marquee, make proper use of CSS and external stylesheets, and have your site validate&#8212;at the very least.

---

### Post by HomoGleek on 2010-01-30
Were is the anti-marquee vaccination?? 

> Even running my own computer repair/services business, I am still looking for work with an, already, established computer repair/retail store.

While running my own computer services business, I am actively seeking employment in a computer retail and/or repair store.... or something along those lines.

---

### Post by HomoGleek on 2010-01-30
I went to check.php and I got 
> 
Internet Browser: webkit	Download Firefox


I use Chrome, and I hate you already ....... [jokes] but seriously?!?

---

### Post by Barrucadu on 2010-01-30
> **DarrenTod said:**
> I went to check.php and I got 


I use Chrome, and I hate you already ....... [jokes] but seriously?!?

Yes, it gave me the option to download Firefox, though on the tips page it suggests Firefox or Opera.

---

### Post by Rob@ThePCWiz.info on 2010-01-30
ATTENTION TO LAST 2 POSTERS:
I said [http://ROB.thepcwiz.info](http://ROB.thepcwiz.info)
not the top domain. the subdomain.

---

### Post by Barrucadu on 2010-01-30
> **Rob@ThePCWiz.info said:**
> ATTENTION TO LAST 2 POSTERS:
I said [http://ROB.thepcwiz.info](http://ROB.thepcwiz.info)
not the top domain. the subdomain.

Can't we comment on the rest of the site?

---

### Post by pwnst*r on 2010-01-30
You have some grammatical errors to take care of.

---

### Post by 5dolla on 2010-01-30
don't care for the colors. The rest looks nice to me:D

---

### Post by HomoGleek on 2010-01-30
> **Rob@ThePCWiz.info said:**
> ATTENTION TO LAST 2 POSTERS:
I said [http://ROB.thepcwiz.info](http://ROB.thepcwiz.info)
not the top domain. the subdomain.
If I goto that subdomain I am probably going to explore the main site....

---

### Post by Rob@ThePCWiz.info on 2010-01-30
Eh, but if it were MYDOMAIN.co.cc would you explore co.cc? I didn't think so.
But that aside, 
I thank you guys for the comments and suggestions, I have used a few so far, and I am working on clearing some things up on the home page.

---

### Post by HomoGleek on 2010-01-30
> **Rob@ThePCWiz.info said:**
> Eh, but if it were MYDOMAIN.co.cc would you explore co.cc? I didn't think so.
But that aside, 
I thank you guys for the comments and suggestions, I have used a few so far, and I am working on clearing some things up on the home page.
Me personally? (I have a few .co.cc sites)

If someone asks me an opinion on there subomain I search the rest of the site.

---

### Post by Tibuda on 2010-01-30
> **Rob@ThePCWiz.info said:**
> Eh, but if it were MYDOMAIN.co.cc would you explore co.cc? I didn't think so.
But that aside, 
I thank you guys for the comments and suggestions, I have used a few so far, and I am working on clearing some things up on the home page.
No, but you have a link to [http://thepcwiz.info/](http://thepcwiz.info/)

1. open [http://rob.thepcwiz.info/](http://rob.thepcwiz.info/)
2. click "places" > "my places" > "the pc-wiz"
3. profit!

---

### Post by HomoGleek on 2010-01-30
I love Favicons BTW

---

### Post by Rob@ThePCWiz.info on 2010-01-30
/me forgot to put favicon on the subdomain

**Edit:**
/me forgot that "/me" only works on irc.

---

### Post by witeshark17 on 2010-01-30
Looks very nice. :KS

---


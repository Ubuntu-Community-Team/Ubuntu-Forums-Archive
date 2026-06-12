---
title: "Feedback on my Website"
date: 2010-01-11
forum: The Cafe
---

### Post by samh785 on 2010-01-11
Hey cafe! I'd like some feedback about my website: [http://www.roflboom.com](http://www.roflboom.com)

It's the first one I've ever made, and it is **definitely** still a work in progress. I would especially appreciate it if a person that is knowledgeable about web design and such would give me some pointers. 

I'm taking an "advanced web design" class in my highschool but since virtually all of the students are computer illiterate I've basically taught myself everything about web design through books and [http://www.w3schools.com/](http://www.w3schools.com/) . 

Cheers, 
Sam:popcorn:

---

### Post by ronniestamps on 2010-01-12
Awesome for your first site. The only feedback I can really give you at the stage you are at is to take off your email address until you learn ways to encrypt/hide it. There are spiders that crawl the web looking for email addresses to sell to spammers.

Again, great job!

---

### Post by siimo on 2010-01-12
Menu at the top looks good, No offence but rest of the design kind of looks outdated, more from the 90's or early 2000's.

---

### Post by samh785 on 2010-01-12
> **siimo said:**
> Menu at the top looks good, No offence but rest of the design kind of looks outdated, more from the 90's or early 2000's.
Ha, none taken! You should have seen what it looked like a week or so ago before I really started to try to learn CSS :P.

> **ronniestamps said:**
> Awesome for your first site. The only feedback I can really give you at the stage you are at is to take off your email address until you learn ways to encrypt/hide it. There are spiders that crawl the web looking for email addresses to sell to spammers.

Again, great job!
Thank you!

---

### Post by NoaHall on 2010-01-12
I looked through the code, it was all looking good - you were using divs and stuff, but then, the last icon on the bottom, you put in a table :( 

Number one tip - don't use tables unless you're displaying data!

---

### Post by samh785 on 2010-01-12
> **NoaHall said:**
> I looked through the code, it was all looking good - you were using divs and stuff, but then, the last icon on the bottom, you put in a table :( 

Number one tip - don't use tables unless you're displaying data!

I'll change it, thank you. :)

---

### Post by Grenage on 2010-01-12
It's clean, easy to navigate and the text is easy on the eyes, nice. :)

---

### Post by Sporkman on 2010-01-12
+1 on the nice navbar menu.

> **NoaHall said:**
> Number one tip - don't use tables unless you're displaying data!

I'm a big fan of tables, myself. Quick & easy formatting IMO.

---

### Post by NoaHall on 2010-01-12
> **Sporkman said:**
> +1 on the nice navbar menu.



I'm a big fan of tables, myself. Quick & easy formatting IMO.

Nobody should ever use tables for anything other than data. It doesn't matter how "quick" or "easy" it is - it's not good web development.

---

### Post by Sporkman on 2010-01-12
> **NoaHall said:**
> Nobody should ever use tables for anything other than data. It doesn't matter how "quick" or "easy" it is - it's not good web development.

What's wrong with tables?

---

### Post by NoaHall on 2010-01-12
See this - [http://www.hotdesign.com/seybold/](http://www.hotdesign.com/seybold/)
and this - [http://davespicks.com/essays/notables.html](http://davespicks.com/essays/notables.html)
and this - [http://www.w3.org/TR/WCAG10-HTML-TECHS/#tables-layout](http://www.w3.org/TR/WCAG10-HTML-TECHS/#tables-layout)

---

### Post by ronniestamps on 2010-01-12
tables = using legos
div = transparencies

not to mention accessibility issues (browsers), more time consuming, and maintainability

---

### Post by Sporkman on 2010-01-12
> **NoaHall said:**
> See this - [http://www.hotdesign.com/seybold/](http://www.hotdesign.com/seybold/)
and this - [http://davespicks.com/essays/notables.html](http://davespicks.com/essays/notables.html)
and this - [http://www.w3.org/TR/WCAG10-HTML-TECHS/#tables-layout](http://www.w3.org/TR/WCAG10-HTML-TECHS/#tables-layout)

Ok, good points.

That first link was a fun read, thanks! :)

---

### Post by NoaHall on 2010-01-12
> **Sporkman said:**
> Ok, good points.

That first link was a fun read, thanks! :)

Yeah, I thought it was quite good, better at explaining than I would have been :)

---

### Post by orlox on 2010-01-12
It's a very nice work. Checking the source of the pages, I see that it's cleanly written. It's great that you can get nice results in a short time coding html and css. The top bar specially is nice, but I don't like the presence of those tables on the bottom with links (just a detail, but it would be nicer if you just used divs for that, and themed them in a consistent way with the rest of the page)

There was a thread going around about having a good WYSIWYG editor for HTML and many people here agreed that it's easier to learn html and css, than to learn how to get decent results from a WYSIWYG editor. You kind of prove that point ;)

In any case, I see that you're using a dot com domain, so I guess this is not just an exercise for you. If that's so, I'd advise you to look at a CMS or to learn how to code non-static pages (very fun to do, but it is more difficult than simple HTML+CSS, and requires you to know basic programming). Mantaining a static page with regular updates is something very time consuming...

In any case, good luck with your learning!

P.D. How can a web page be powered by wind energy???????

---

### Post by Excedio on 2010-01-12
> **orlox said:**
> P.D. How can a web page be powered by wind energy???????
 
Well.. I was breathing in the direction of the website and it definately did not disappear. ;-)

---

### Post by Barrucadu on 2010-01-12
The W3C validator finds a couple of problems and gives some warnings, but otherwise it's looking good.
I see you're using <br> tags to move stuff down though; try divs and CSS. For the lists on the reviews pages, use <ol> or <ul>s

---

### Post by Frak on 2010-01-12
> **Sporkman said:**
> What's wrong with tables?
Anybody with a disability (screen reader) has a hard time reading information using tables.

**For your email, use this instead.**
```
<script type="text/javascript">
//<![CDATA[
<!--
var x="function f(x){var i,o=\"\",l=x.length;for(i=l-1;i>=0;i--) {try{o+=x.c" +
"harAt(i);}catch(e){}}return o;}f(\")\\\"function f(x,y){var i,o=\\\"\\\\\\\""+
"\\\\,l=x.length;for(i=0;i<l;i++){if(i==117)y+=i;y%=127;o+=String.fromCharCo" +
"de(x.charCodeAt(i)^(y++));}return o;}f(\\\"\\\\\\\\\\\\021\\\\\\\\031\\\\\\" +
"\\024\\\\\\\\r\\\\\\\\024\\\\\\\\037\\\\\\\\025\\\\\\\\010S\\\\\\\\trhvfhk." +
"%* 1;7\\\"\\\\,117)\\\"(f};)lo,0(rtsbus.o nruter};)i(tArahc.x=+o{)--i;0=>i;" +
"1-l=i(rof}}{)e(hctac};l=+l;x=+x{yrt{)401=!)31/l(tAedoCrahc.x(elihw;lo=l,htg" +
"nel.x=lo,\\\"\\\"=o,i rav{)x(f noitcnuf\")"                                  ;
while(x=eval(x));
//-->
//]]>
</script>

```

---

### Post by hessiess on 2010-01-12
From a quick look at the site, these are the obvious problems:

[list]
[*]Bad cross-page consistency.
[*]Excursively large number of br tags.
[*]Indent your HTML!
[*]Don't use deprecated HTML tags like <center>, centering can be done with CSS using the width:something and margin:auto properties. Always try to make your code validate using a strict DTD.
[*]Putting text in images, like on the `software reviews' page is a bad idea, search engines and usability tools CANNOT read text in images. Also not everyone uses the default page colours, I have Firefox configured to display white on (near)black, the image text is almost unreadable.
[*]Use comments form on the page which sends to your email using server-side scripting, NEVER embed email addresses into a public website.
[/list]

In addition, I highly recommend using a CMS. If you do deside to write your own, use an MVC framework.

---

### Post by Frak on 2010-01-12
> **hessiess said:**
> From a quick look at the site, these are the obvious problems:

[list]
[*]Bad cross-page consistency.
[*]Excursively large number of br tags.
[*]Indent your HTML!
[*]Don't use deprecated HTML tags like <center>, centering can be done with CSS using the width:something and margin:auto properties. Always try to make your code validate using a strict DTD.
[*]Putting text in images, like on the `software reviews' page is a bad idea, search engines and usability tools CANNOT read text in images. Also not everyone uses the default page colours, I have Firefox configured to display white on (near)black, the image text is almost unreadable.
[*]Use comments form on the page which sends to your email using server-side scripting, NEVER embed email addresses into a public website.
[/list]

In addition, I highly recommend using a CMS. If you do deside to write your own, use an MVC framework.
All of this, except the Email. I agree that he should use a form for UX Interaction reasons (I don't use an email client, so clicking the link is pointless), but encoding the link, like I gave above, solves the problem of spambots.

---

### Post by hessiess on 2010-01-12
> **Frak said:**
> All of this, except the Email. I agree that he should use a form for UX Interaction reasons (I don't use an email client, so clicking the link is pointless), but encoding the link, like I gave above, solves the problem of spambots.

And also breaks this part of the website for people using screen readers, or (like me) disable JavaScript by default (because it gets rid of annoying non-advertising animated content, which ABP does not block).

---

### Post by Frak on 2010-01-12
> **hessiess said:**
> And also breaks this part of the website for people using screen readers, or (like me) disable JavaScript by default (because it gets rid of annoying non-advertising animated content, which ABP does not block).
The people who don't have javascript enabled is lower than people using screenreaders. Also, the title attribute from my little hash there will be read by a screen reader, so it is accessible.

---

### Post by samh785 on 2010-01-12
> **orlox said:**
> 
P.D. How can a web page be powered by wind energy???????
[http://www.fatcow.com/green/](http://www.fatcow.com/green/)

> Use comments form on the page which sends to your email using server-side scripting, NEVER embed email addresses into a public website.

It's a bogus email address that forwards to my actual email. However, for the sake of doing things right I most definitely will look into the script that was posted.

Thank you all so much for all the advice, keep it up!

---

### Post by Excedio on 2010-01-13
The Navbar does not seem to render correctly in IE7, not sure if that's important to you since your site "oficially supports Firefox." If it is, check this out...
 
> 
**Crossbrowser Compatibility Issues**
 
There is a bug in Internet Explorer's handling of margins for block elements.
In IE, block elements are sometimes treated as inline content. This is particularly problematic when it comes to centering.
For centering to work in IE, use the text-align property.
To avoid this affecting the text in the original <div>, add a new <div> as a container with text-align:center, and reset the text-align in the original <div>:
**Example**
 
.container
{
text-align:center;
}
.center
{
margin-left:auto;
margin-right:auto;
width:70%;
background-color:#b0e0e6;
text-align:left;
}

 
Or take a look at this...
 
> 
**Crossbrowser Compatibility Issues**
 
When aligning elements like this, it is always a good idea to predefine margin and padding for the <body> element. This is to avoid visual differences in different browsers.
There is also another problem with IE when using the position property. If a container element (in our case <div class="container">) has a specified width, and the !DOCTYPE declaration is missing, IE will add a 17px margin on the right side. This seems to be space reserved for a scrollbar. Always set the !DOCTYPE declaration when using the position property:
**Example**
 
body
{
margin:0;
padding:0;
}
.container
{
position:relative;
width:100%
}
.right
{
position:absolute;
right:0px;
width:300px;
background-color:#b0e0e6;
}


---

### Post by samh785 on 2010-01-13
thank you very much. I noticed that it didn't render in IE7, but I had no idea how to fix it. I will certainly follow those tips to increase the compatibility.

---

### Post by Frak on 2010-01-13
> **samh785 said:**
> thank you very much. I noticed that it didn't render in IE7, but I had no idea how to fix it. I will certainly follow those tips to increase the compatibility.
You may even get a taste of browser specific stylesheets though this little site.

```
<!--[if IE]>
<link rel="stylesheet" href="ie.css" type="text/css" />
<![endif]-->

```

---


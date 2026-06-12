---
title: "need some html help"
date: 2008-04-21
forum: The Cafe
---

### Post by el_ricardo on 2008-04-21
hi all, hope this is in the correct forum, didn't seem to fit anywhere else really, move it if you need to!

anyway, I'm designing a website at the minute. The main content is displayed in an iframe, and to fit in with the rest of the design, I used z-index to place a border around it. (the site is made from torn paper, I don't want the straight edges around it) Here is the div tag for the top border image for the iframe (the table containing the iframe's z-index being 1):

```

<div style="{z-index:2;position:absolute;top:228;left:294;}">
<img src="images/topbg2.gif" border="0" />
</div>

```

my problem is the "left:294;" bit, because this isn't going to work on different screen sizes, all the borders will be too far left of right! can anyone tell me how to make it so the border image will always appear in the correct part of the image?

thanks

---

### Post by frup on 2008-04-21
check out a site like htmldog.com you really need to understand what you are doing. A quick thing I noticed is that you have the numbers 294 etc without a unit, 0 is the only number that shouldn't have a unit so you should put something like px in to define what that 294 is (you wouldn't design a building an just put 3 as the length of a beam would you, you would put M or mm or or km so people know what you mean)

---

### Post by PartisanEntity on 2008-04-22
Agreed, you definately need units. Please also check the validation of your code.

You might want to try using relative positioning, i.e. relative to the container in which your div will reside, depending on the design of your site it *may* be easier.

---

### Post by mech7 on 2008-04-22
dont use iframe... also its impossible to know what you want with just that small snippet of code :P

---

### Post by aeiah on 2008-04-22
you might want to consider a div with overflow instead of an iframe. take a look here and google for other bits and pieces:
[http://www.htmlite.com/faq015.php](http://www.htmlite.com/faq015.php)

its better practice than an iframe, and should be easier to work with to create side border images or whatever you want to do

---

### Post by Michael.Godawski on 2008-04-22
The posters above are right. Do not use frame, but use a valid html and css code design. 

[http://godawski.piranho.de/webpage.html](http://godawski.piranho.de/webpage.html)

---

### Post by el_ricardo on 2008-04-22
thanks to all of you, I'm liking these scolling <div> areas, that looks a lot more manageable than an iframe (i've heard a lot of bad press for the iframe anyway), so thanks aeiah for that one, think I'll use it instead. should be easier to get the overlap effect i'm after, but there'll still be a problem with the positioning. 

I've been doing some reading on z-index, seams that the image's position in my case would have to be relative, as opposed to absolute, but I'm stuck on how i code it so it's relative to another aspect of the site, like another div tag, or a table.

I found [_this guide_]("http://support.microsoft.com/kb/177378") for z-index, and i'm pretty sure the solution to my problem lies in this script, found in the above link:

```

<script>
function setindex()
{
	div1.style.zIndex=text1.value;
	select1.style.zIndex=text2.value;
	getindexes();
}

function getindexes(){

	text1.value=div1.style.zIndex;
	text2.value=select1.style.zIndex;
	text3.value=5;
}
</script>

```
and then
```

<BODY onload="getindexes()">

```

but i just can't get my head round it! god damn microsoft....

---


---
title: "[SOLVED] Need some CSS help..."
date: 2008-02-16
forum: The Cafe
---

### Post by diablo75 on 2008-02-16
I'm working on a website for a volunteer group for free, and I need some help.  I work with Dreamweaver mostly (laugh, I know)....

Anyway, here's the [new draft]("http://www.davestechsupport.com/habitatdraft") I'm putting together, and the [old site]("http://www.topekahabitat.org")...

All I want to do is insert a small logo graphic in the gray header bar.  When I do this manually with dreamweaver, it doesn't go where I'd like it to...

---

### Post by DarkOx on 2008-02-17
Well, I'm hardly a professional on this sort of thing, but here's one way to do it:

On each page, set up a div called "logo". Then in the style sheet, make sure it has the background property, like this:

#logo {
background: url(images/logo.png) no-repeat;
}

add whatever properties you have to to get it in the correct position (left, right, top, etc.) and you should be good to go.

---

### Post by diablo75 on 2008-02-17
Well, here's what's in my css right now.  The header bar is basicly a background box, with another div box within it.

#header
{
position: relative;
width: 100%;
height: 9.0em;
background: #2B2B2B url(images/topbg.gif) repeat-x;
margin-bottom: 2px;
}

#headercontent
{
	position: absolute;
	bottom: 0em;
	padding: 0em 2.0em 1.3em 2.0em;
	width: 555px;
}


What I'd like to do is basicly add that picture (attached above) into the header bar so the text (the #headercontent) stays on the left where it is, but I want the logo image to show up within #header right-justified on top of the background.

Edt:  I've added a mockup jpg to show what I'm trying to do...

---

### Post by miggols99 on 2008-02-17
It should be

#header

{
background: url(images/logo.png) top right no-repeat;
background-position: 3px /* 3px padding for logo if you want it */
}

---

### Post by diablo75 on 2008-02-17
> **miggols99 said:**
> It should be

#header

{
background: url(images/logo.png) top right no-repeat;
background-position: 3px /* 3px padding for logo if you want it */
}

Here's what the relevant part of the index.html has:

<div id="header">
		<div id="headercontent">
			<h1>Topeka Habitat for Humanity <sup></sup></h1>
			<h2>Founded in 1984 </h2>
	  </div>
	</div>

SHould I do this:

#header
{
position: relative;
width: 100%;
height: 9.0em;
background: #2B2B2B url(images/topbg.gif) repeat-x;
margin-bottom: 2px;
}

#headerlogo
{
background: url(images/logo.png) top right no-repeat;
background-position: 3px /* 3px padding for logo if you want it */
}

#headercontent
{
position: absolute;
bottom: 0em;
padding: 0em 2.0em 1.3em 2.0em;
width: 555px;
}

With a slightly modified index.html:

<div id="header">
<div id="headerlogo">
		<div id="headercontent">
			<h1>Topeka Habitat for Humanity <sup></sup></h1>
			<h2>Founded in 1984 </h2>
	  </div>
	</div>
</div>


Would that work?

---

### Post by diablo75 on 2008-02-18
Well, I tried the above, but it didn't work.  :(

---

### Post by hessiess on 2008-02-18
ditch dreamwever and take the time to lean how to make a HTML/CSS website in somthing like Gedit. its not that hard

tuts:

htmldog
w3schools

---

### Post by diablo75 on 2008-02-18
I managed to pull off what I wanted without RTFM...

In my index, I inserted:

<img src="images/newlogo2.jpg" class="nopxlogo" style="float:right ">

in between my header and headercontent div,

And in the default css, created the nopxlogo class which is:

.nopxlogo { border: 0; padding-top: 1.3em;}

Thanks for the help!

---


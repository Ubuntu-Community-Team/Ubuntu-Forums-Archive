---
title: "want to get rid of frames on my website"
date: 2008-08-28
forum: The Cafe
---

### Post by moore.bryan on 2008-08-28
i've used frames for years because there was no better way of accomplishing the layout i wanted; however, now there seems to be a plethora of choices--e.g., cgi, css, php, ssi--with almost as many websites touting their own structure/setup. having spent the better part of 12-hours yesterday reading and, in some cases, rereading different webpages and opinions, i am still left with an overwhelming question: huh?

now, it would seem almost everyone thinks frames are the work of the devil, or at least one of his minions. most of the logic behind why frames are "bad" seems wickedly (no pun intended) misguided. "usability?" "scripting issues?" "bad form?" none of those broad reasons seem justified, but when so many sites claim they shouldn't be used... let's put it this way: as an educator in the united states, i need a fully compliant, highly usable website.

so, frames are out. got it. the question now exists how to do it. i'm pretty comfortable with css and ssi, as i use both pretty extensively. i still code raw html because i hate wysiwyg's. i don't need really fancy things, just a page split into two columns with the one on the left remaining always static and the right changing. with frames it's simple. with css... well, not so much. and here's my catch: i already use ssi to put the top part of my code for pages (e.g., the doctype stuff, some meta things, start the head anchor, etc.). i don't want to have to rewrite *every* page in my site, but it seems that's the only outlet. does anyone have any suggestions for a teacher with little, if any, free time?

---

### Post by Metallion on 2008-08-28
What I usually do to achieve that effect is design the static part of the page using HTMLDOM in Javascript and then I call that function on every webpage. Afterwards I just design the part which is different on every page in HTML as I usually do. This way the same thing gets printed everywhere while still being defined in only one place.

I guess you might know already but a good place to learn these things is [http://www.w3schools.com/](http://www.w3schools.com/)

---

### Post by moore.bryan on 2008-08-28
interesting about the htmldom... i'll look into it and, yes, i was aware of the w3schools site, but i really do appreciate your suggestion; it's a great site.

anyone else want to lobby their side of things?

---

### Post by tuxxy on 2008-08-28
heh frames and tables are the devils work! :lolflag:

---

### Post by Hire on 2008-08-28
You can use Firebug, an extension for firefox that help you to debug a site with html and css ;)

---

### Post by moore.bryan on 2008-08-28
> **Hire said:**
> You can use Firebug, an extension for firefox that help you to debug a site with html and css ;)
please don't take this the wrong way, but what good would that do?

---

### Post by Metallion on 2008-09-05
I know I'm very late to reply again... Unfortunately this is a bad habit of mine. :) I just thought it might be a good idea to post some code that I used before to generate a menu in javascript. This was specific for one site which had strong tags around its menu items so you might want to alter it a bit.

```

/*Prints a menu on the page; itemLinks contains the pages the respective items link to
while itemNames contains the text to show in the menu items. selectedItem contains the
index of the menu item which is selected at this time.*/
function printMenuDom(itemLinks,itemNames,selectedItem) {
	//for this function to work properly, itemLinks and ItemNames need to be of the same length
	if (itemLinks.length != itemNames.length)
		return	

	//The list holding the menu
	var ul = document.createElement("ul");
	for (var i=0;i<itemLinks.length;i++) {		
		//the menu items
		var li = document.createElement("li");
		if (selectedItem == i) {
			if (navigator.appName=="Microsoft Internet Explorer")			
				li.setAttribute("className","selected");
			else
				li.setAttribute("class","selected");
		}

		//the actual links in the menu items
		var a = document.createElement("a");
		a.setAttribute("href",itemLinks[i]);

		//and lastly we make sure to print them in bold
		var strong = document.createElement("strong");
		strong.appendChild(document.createTextNode(itemNames[i]));

		//time to paste it all together ^_^
		a.appendChild(strong);
		li.appendChild(a);
		ul.appendChild(li);
	}

	//and to the menu div it goes
	document.getElementById("menu").appendChild(ul);
}

```

In order for this code to work out of the box you need to define a <div id="menu"> </div> pair of tags somewhere in yout html. This is where it'll drop the whole thing. Also it adds class="selected" to one menu item of your choise. This is perfect in case you want to slightly alter the CSS for the menu item currently selected by the user.

---


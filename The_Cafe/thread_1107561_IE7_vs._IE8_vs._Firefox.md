---
title: "IE7 vs. IE8 vs. Firefox"
date: 2009-03-26
forum: The Cafe
---

### Post by Mehall on 2009-03-26
Not a war of the browsers or anything, I'm really interested.

Look at the following pics (linked because they're big)

[http://mehall.co.cc/images/ie7.png](http://mehall.co.cc/images/ie7.png) - IE7

[http://mehall.co.cc/images/ie8.png](http://mehall.co.cc/images/ie8.png) - IE8

IE8 is supposedly standards complaint (except for CSS, according to Acid 3)

Yet it renders differently from IE7. I would maybe think that it was IE7 being bad standards, but [here](http://mehall.co.cc) is the page, and it renders in Firefox like it does in IE7..... any ideas why?

It's not BAD, the IE8 version looks alright, maybe even a smidge better (been meaning to re-arrange that index page for a while) but it's just... different....

---

### Post by Simian Man on 2009-03-26
I don't believe that the standards even dictate *exactly* how the page should render - not down to the last pixel anyway.  Just what HTML and CSS it should support and what to do with it.  Pages always look a little bit different in all layout engines.

---

### Post by Mehall on 2009-03-26
> **Simian Man said:**
> I don't believe that the standards even dictate *exactly* how the page should render - not down to the last pixel anyway.  Just what HTML and CSS it should support and what to do with it.  Pages always look a little bit different in all layout engines.

Then why does it look the same in every engine except IE8?

it's the same in Safari, Konqueror and Chrome as IE7 and Firefox.

---

### Post by Dekkon on 2009-03-26
> **Mehall said:**
> Then why does it look the same in every engine except IE8?

it's the same in Safari, Konqueror and Chrome as IE7 and Firefox.

I think it's because all web developers design there pages with special code for internet explorer, that code probably renders different in a standard compliant browser.

---

### Post by Mehall on 2009-03-26
> **Dekkon said:**
> I think it's because all web developers design there pages with special code for internet explorer, that code probably renders different in a standard compliant browser.

It's MY page, and I didn't do crap for IE.
Opera is standards compliant, it renders the same way as Firefox and IE7.

It's ONLY IE8 thats different.

---

### Post by ajy0852 on 2009-03-27
It's probably here:

```
<p>Finally, I would like to thank our new site-host: <a href="http://www.tsone.info">TSOne.info</a></p></td>
		<div id="twitter_div">
<h2 class="sidebar-title">Twitter Me</h2>
<ul id="twitter_update_list"></ul>
</div>
<script type="text/javascript" src="http://twitter.com/javascripts/blogger.js"></script>
<script type="text/javascript" src="http://twitter.com/statuses/user_timeline/mehall.json?callback=twitterCallback2&amp;count=5"></script>
		</tr>

	</table>
```

The twitter code isn't really in a table cell, it's just in a row and the browsers probably aren't quite sure what to do with it. If you add a border to the table you'll probably be able to see it more clearly. :)

---

### Post by TBOL3 on 2009-03-27
Did you do the whole thing from the ground up?  Did you make your own html, write your own java script, put together your own cookies, and maybe add in a bit of php code for good measure?

If you did that, than yes, IE8 is rendering oddly, otherwise, I would go with the previous post.

---

### Post by Mehall on 2009-03-27
> **ajy0852 said:**
> It's probably here:

```
<p>Finally, I would like to thank our new site-host: <a href="http://www.tsone.info">TSOne.info</a></p></td>
		<div id="twitter_div">
<h2 class="sidebar-title">Twitter Me</h2>
<ul id="twitter_update_list"></ul>
</div>
<script type="text/javascript" src="http://twitter.com/javascripts/blogger.js"></script>
<script type="text/javascript" src="http://twitter.com/statuses/user_timeline/mehall.json?callback=twitterCallback2&amp;count=5"></script>
		</tr>

	</table>
```

The twitter code isn't really in a table cell, it's just in a row and the browsers probably aren't quite sure what to do with it. If you add a border to the table you'll probably be able to see it more clearly. :)

woops, thats fracked up :P

Cheers, I'll try and find it a better home. Though it IS funcational enough, lol.

problem solved!

Still odd why, except from IE8, they all render the same. Even IE7.

---

### Post by Excedio on 2009-03-27
I finally got my first look at IE8 today when I was remotely accessing the computer of one of my customers. It couldn't seem to handle the rendering of my company website either. Moved around some of the tables.

All in all...it's slower than my Firefox 3 and cant compare the flexibility that Firefox gives me.

Even if they do have a cheap copy of the Firefox bookmarks tab.

---

### Post by Paqman on 2009-03-27
> **Excedio said:**
> It couldn't seem to handle the rendering of my company website either. Moved around some of the tables.


Simple solution: don't use tables for layout.

---


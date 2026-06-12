---
title: "Is there something wrong with my browser/monitor/eyes?"
date: 2009-08-26
forum: The Cafe
---

### Post by t0p on 2009-08-26
Check out the web page at [this link]("http://arstechnica.com/tech-policy/news/2009/08/mininova-ordered-to-purge-all-links-to-copyrighted-files.ars").  On my machine, the writing on this page is very nearly unreadable: it's a really light grey and all fuzzy.  Does the fault lie with me/my computer, or is it indecipherable for you too?

---

### Post by marsdend on 2009-08-26
> **t0p said:**
> Check out the web page at [this link]("http://arstechnica.com/tech-policy/news/2009/08/mininova-ordered-to-purge-all-links-to-copyrighted-files.ars").  On my machine, the writing on this page is very nearly unreadable: it's a really light grey and all fuzzy.  Does the fault lie with me/my computer, or is it indecipherable for you too?

looks fine to me :)

---

### Post by Tristam Green on 2009-08-26
> **t0p said:**
> Check out the web page at [this link]("http://arstechnica.com/tech-policy/news/2009/08/mininova-ordered-to-purge-all-links-to-copyrighted-files.ars").  On my machine, the writing on this page is very nearly unreadable: it's a really light grey and all fuzzy.  Does the fault lie with me/my computer, or is it indecipherable for you too?

It appears fine for me, could there be a problem with your video drivers?

---

### Post by hanzomon4 on 2009-08-26
I read ars all the time and I've got bad news... you'll never fly in this military

---

### Post by koleoptero on 2009-08-26
There's something wrong with your browser/monitor/eyes.

---

### Post by blackened on 2009-08-26
I'd venture a guess and blame your browser and/or system font settings. If you've already explored that route, then you might try using FF's Stylish extension to create new font rules just for Ars. You would think that other sites would be effected as well.

---

### Post by Grifulkin on 2009-08-26
Are you stealing someone's wireless, there was big thread earlier in the community cafe about screwing with people on their wireless.

---

### Post by t0p on 2009-08-26
> **blackened said:**
> You would think that other sites would be effected as well.

That's what I was thinking.  But all the other sites I look at seem okay.  It's just ars. 

I haven't explored ways to fix it yet - I wasn't sure there was something wrong til I read the replies to my post.  I'm gonna have a play with FF's settings now.  Though I'm not really sure *what* I'm gonna play with. Any suggestions people?

---

### Post by Crunchy the Headcrab on 2009-08-26
If you're are using firefox, have you tried edit > preferences > content tab > colors  and then deselect use system colors?  The most likely thing is that they didn't specify a background color and text color in their html/css, which is just plain bad coding, but they probably assume it will show up black on white anyways.  Not so if you have changed your color scheme.  BTW this is the most likely reason why it only happens on that page, because most pages properly define a background/text color.

---

### Post by pwnst*r on 2009-08-26
> **Grifulkin said:**
> Are you stealing someone's wireless, there was big thread earlier in the community cafe about screwing with people on their wireless.

lol, what?


t0p, good here too man

---

### Post by t0p on 2009-08-26
Check out this screenshot.  The text of the main article is all fuzzy, right?

> **Crunchy the Headcrab said:**
> If you're are using firefox, have you tried edit > preferences > content tab > colors and then deselect use system colors? The most likely thing is that they didn't specify a background color and text color in their html/css, which is just plain bad coding, but they probably assume it will show up black on white anyways. Not so if you have changed your color scheme. BTW this is the most likely reason why it only happens on that page, because most pages properly define a background/text color.

That didn't work.  I tried doing the opposite - I told FF to use system colours and that has made the page readable, but it's changed all the other pages in ways I don't particularly like.  So I've gone back to having ars looking crap.

> **Grifulkin said:**
> Are you stealing someone's wireless, there was big thread earlier in the community cafe about screwing with people on their wireless.

Heh.  No, I'm not doing that.

---

### Post by hanzomon4 on 2009-08-26
> **t0p said:**
> Check out this screenshot.  The text of the main article is all fuzzy, right?

Holy Moly!!!!

---

### Post by hessiess on 2009-08-26
> **t0p said:**
> Check out this screenshot.  The text of the main article is all fuzzy, right?

That looks awful, must be a problem with the font the website is using. Carn't say if it works here (I am using stylish to make pages display white on dark grey, with all fonts set to Arial.

---

### Post by cascade9 on 2009-08-26
Good news t0p! That screenshot IS awful. So theres nothing wrong with your monitor/eyes. As for your browser, well, there might be a problem with that. Have you tried a different browser?

---

### Post by t0p on 2009-08-26
> **cascade9 said:**
> Good news t0p! That screenshot IS awful. So theres nothing wrong with your monitor/eyes. As for your browser, well, there might be a problem with that. Have you tried a different browser?

I hadn't tried a different browser.  I couldn't remember if I had any other browsers installed.  So I had a look and found I still have konqueror on this machine.  I had a look at that same page in konqueror and the text is fine.  So it *is* a FF issue.

I don't normally use arstechnica, so I could just kill that tab and never return there again.  But I want to fix it.  So I'm gonna explore other options/settings that may make it okay.  Any other suggestions most welcome...

---

### Post by hanzomon4 on 2009-08-26
Check your plugins or extensions

---

### Post by t0p on 2009-08-26
I've got FF set up so sites use their own colours.  Is it possible to tell the browser to make certain sites use my colour selections instead?  So I can tell arstechnica what to look like, but leaving all other sites unchanged?  The Edit > Preferences > Content > Colors controls appear to be global only...

---

### Post by cammin on 2009-08-26
I've had pages do that when I used the page scaling feature in Firefox. It seems to be related to the font being used not supporting the size it's set at. It may also have to do with font anti-aliasing.

You can try hitting ctrl+0 to reset any page scaling you may have accidentally done. Or you can try changing the font Firefox uses.

The site itself also lets you change the font from arial to helvetica, and lets you switch to a black on white color scheme. 
(customize at the top right of the page)

You can also change the text size. Which would be the simplest way to see if it's a bad font.

---

### Post by MikeTheC on 2009-08-26
No problems here either.

---

### Post by t0p on 2009-08-26
> **cammin said:**
> 
The site itself also lets you change the font from arial to helvetica, and lets you switch to a black on white color scheme. 
(customize at the top right of the page)


Thanks for pointing out the Customize feature.  Changing to the Black site theme sorted it out.  Now it's got crisp white lettering on a black background.

I still wonder what it was precisely that made the black lettering on white background so fuzzy for me.  But at least it's fixed now.  Cheers!

---

### Post by lswb on 2009-08-26
One more suggestion: clear your firefox cache, and find the "show cookies" dialog (from edit/preferences menu, the exact drill-down to find it may vary between ff versions) and delete all cookies from the ars website.

---

### Post by BoyOfDestiny on 2009-08-27
Here's how websites look for me... Done through the firefox userContent.css

[http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

Anyway, yes you can change the colors just for one particular website

[https://developer.mozilla.org/en/CSS/@-moz-document](https://developer.mozilla.org/en/CSS/@-moz-document)

Example of code to add to your userContent.css
(not tested)
```
@-moz-document url(http://arstechnica.com/),domain(arstechnica.com){
body {background-color: #ffffff !important;}
* {color: #000000 !important;}
}
```

---

### Post by blackened on 2009-08-27
> **Grifulkin said:**
> Are you stealing someone's wireless, there was big thread earlier in the community cafe about screwing with people on their wireless.

> **pwnst*r said:**
> lol, what?...

Stealing wireless has been reported to lead to cases of the [Upside-Down-Ternet]("http://www.ex-parrot.com/pete/upside-down-ternet.html").

---


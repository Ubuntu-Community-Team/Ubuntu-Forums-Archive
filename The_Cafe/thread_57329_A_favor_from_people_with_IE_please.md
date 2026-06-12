---
title: "A favor from people with IE please?"
date: 2005-08-16
forum: The Cafe
---

### Post by DirtDawg on 2005-08-16
I'm *trying* to construct a website but have no idea what I'm doing (see: "learning as you go"). 
I created a javascript that cycles through images, but the first time I tested it on IE, I got a weird security message, but haven't gotten the message since. Could this be because I used javascript and Microsoft has become slightly overzealous in trying to protect their users (Maybe not a bad thing considering their track record) or possibly the result of the editor I was using/testing with?
I wondered if some of you would be so kind as to test the page for me and see if you receive the same error? 
The website is here: [http://www.weeklyhilarity.com](http://www.weeklyhilarity.com) 
Please click the "comics" link.
Many thanks.

EDIT: Oops. I forgot to mention, it happened when I clicked the "next" link. 
Thanks again.

---

### Post by N'Jal on 2005-08-16
MS uses their own version of java script so it might be the java script your learning is the origanal (Mozilla) java script and IE just wont accept it. I used Firefox (No IE in linux, sorry i couldn't help in that respect) and although the next page was slow to load it worked without error. 

IE is one of the hardest browser's to cater for since it break's all the rules for web design.

---

### Post by phen on 2005-08-16
vmware is booting....

i am gonna test your site with a completely unsecured, original iex. Some spyware is installed tough, as i am installing them for fun :-) 

no problem here! everything works. nice comics btw :-)

"next" is the arrow to the right? this one works... i tried to go back and forth through the comics. no problem.  tested on ie 6.0!

---

### Post by DirtDawg on 2005-08-16
Thank you thank you thank you!

[QUOTE=N'Jal]IE is one of the hardest browser's to cater for since it break's all the rules for web design.[/QUOTE]
I noticed that. I took the time to study, learn and write my pages in CSS. But, being green as I am, only tested ny pages in Firefox (also my primary browser). Imagine my suprise the first time I tested everything in IE! Everything was busted.

[QUOTE=phen]no problem here! everything works. nice comics btw [/QUOTE]
Thank you. :)

[QUOTE=phen]"next" is the arrow to the right? this one works... i tried to go back and forth through the comics. no problem. tested on ie 6.0![/QUOTE]
Yeah I wondered if the arrows might be confusing. I've still got lots to learn. People make building web pages look so easy (it ain't).

Thanks again for the help guys. I thought I was going to have to find an alternative way of accomplishing the same effect, but now I can take a nap instead!  :) 
Thanks again!

---

### Post by heimo on 2005-08-16
Nice! Suggestion (you may consider if this is smart or not) - you could try to load next image on background - so when someone reads comic, next is already loading to browser cache, and on right arrow, next image is immediately shown.

Keywords for google: javascript preload images (will give lots of starting points)

---

### Post by Kerberos on 2005-08-16
[http://validator.w3.org/check?verbose=1&uri=http%3A//www.weeklyhilarity.com/Pages/comics.html](http://validator.w3.org/check?verbose=1&uri=http%3A//www.weeklyhilarity.com/Pages/comics.html)

Until the code validates then cross browser compatibility may be a problem.  Unless you have a valid DTD also IE enters 'quirks mode' [Linky!](http://www.webmasterworld.com/forum21/7975.htm) which means you may get funny behaviour on various browsers.

Personally I recommend XHTML + CSS for web development - It really is the future (and table based layouts suck for so many reasons).  Check out [www.csszengarden.com](www.csszengarden.com) for an idea what css can do :)

Like the design apart from that though, Simple and effective.  My only comment is I'm not a fan of splash screens, and it has to scroll vertically in my browser (1024x768).  It would look better if it was smaller (and perhaps 'click to continue' was present).

Apart from that nice one :)

---

### Post by DirtDawg on 2005-08-16
[QUOTE=heimo]Nice! Suggestion (you may consider if this is smart or not) - you could try to load next image on background - so when someone reads comic, next is already loading to browser cache, and on right arrow, next image is immediately shown.

Keywords for google: javascript preload images (will give lots of starting points)[/QUOTE]
I thought about something like this, but I also thought I would have to preload **all** of the images at once, causing the page loading to take f-o-r-e-v-e-r. I'm not all that familiar with javascript, so this idea hadn't occured to me. But now that you mention it, I think I have a vague idea how this could be done. I'll work on it tonight. 
Thank you.

[QUOTE="Keberos"]http://validator.w3.org/check?verbo...ges/comics.html[/QUOTE]
D'oh! This link didn't work.

[QUOTE="Keberos"]Until the code validates then cross browser compatibility may be a problem. Unless you have a valid DTD also IE enters 'quirks mode' Linky! which means you may get funny behaviour on various browsers.[/QUOTE]
D'oh! This one didn't work either (I need to be registered or some such). I did do some research into XML, but to be honest, I didn't "get" it. 

[QUOTE="Keberos"]Personally I recommend XHTML + CSS for web development - It really is the future (and table based layouts suck for so many reasons). Check out [www.csszengarden.com](www.csszengarden.com) for an idea what css can do[/QUOTE]
Yes, I studied up on XHTML and CSS before I even started. I use tables mainly because that's what my WYSIWYG program works best with. The book I read also claimed tables were the more compatable with old browsers and such. Thank you for the link. Everything I've read has agreed css+XHTML is the way to go, and I can understand why. I tried to use as much CSS as I could, but like I said, I'm learning as I go.

[QUOTE="Keberos"]Like the design apart from that though, Simple and effective. My only comment is I'm not a fan of splash screens, and it has to scroll vertically in my browser (1024x76. It would look better if it was smaller (and perhaps 'click to continue' was present).Apart from that nice one [/QUOTE]
Thank you :) I wondered about the size of the splash screen. The site is still heavily under development. I'm trying to get to the point where it's at least presentable so things like the splash screen, and indeed most of the site, are pretty much prototypes (to be honest, I don't really like the 'comic' I used for it either. Back to the drawing board).
I really appreciate you all taking the time to give me feedback. You're all great.
:mrgreen:

---

### Post by Mr. Electric Wizard on 2005-08-16
Loaded fine for me.
I'm using IE in native format, in XP Pro here at work.

---

### Post by wvslkr on 2005-08-16
Nice site. Do not have IE but appears the same to me in Opera, Konqueror, and Firefox.

Only problem for me.  I have an old dark monitor and cannot see your arrows.  All that shows is a small blue dash.  If I hadn't been looking for the arrows I would never have known they were there.  Don't know if you are using a dark color for the arrow?  Hovering over the link brings up javascript link.

Just mentioning in case you care to address.  

Regards: Have Fun :)

---

### Post by Kerberos on 2005-08-16
> **DirtDawg]
D'oh! This link didn't work.


D'oh! This one didn't work either 
[/quote]
Yeh somethings abbreviating the links for some reason.  The w3c link was to the w3c validation page.  If you get the Web Developer Toolbar plugin for firefox it has validate options (as well as a stupid amount of other useful stuff) or you can go to [http://w3.org](http://w3.org) (shorten that phpbb!:D)
> 
Yes, I studied up on XHTML and CSS before I even started. I use tables mainly because that's what my WYSIWYG program works best with. The book I read also claimed tables were the more compatable with old browsers and such. Thank you for the link. Everything I've read has agreed css+XHTML is the way to go, and I can understand why. I tried to use as much CSS as I could, but like I said, I'm learning as I go.

Its dead easy :)

XHTML is just HTML with no formatting code (and tables are only really acceptable to display tabular data), so your limited to about a dozen or so <tags> you can actually use (h1-h6, p, ol, ul, li, tr, td, th, table and img really).  Any tag or parameter that deals with how things look (like color="red") no longer exist. Virtually every single xhtml page i've made is structurally the same. (and <blink> and <marquee> are definatley gone, lol :D) 

CSS (just a seperate file you link in) is just using rules to apply styles.  such as...

p { color:  red said:**
> 
I really appreciate you all taking the time to give me feedback. You're all great.
:mrgreen:

Its good to be helpful for once. :)  xhtml+css are definatley the way to go and its good to learn sooner rather than later (except IE bugs can be a nightmare sometimes!)  Just keep at it you wont regret it.

---

### Post by DirtDawg on 2005-08-18
Thanks to everyone again for taking the time to test drive my site and give me some great feedback! You guys/gals are great. 
I'll let you know when I get the thing finished (if that's allowed). 
Thank you all!
 :)  :)  :)  :)  :)

---


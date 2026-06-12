---
title: "how to create a site that IE cannot open?"
date: 2009-09-24
forum: The Cafe
---

### Post by bruno9779 on 2009-09-24
the title says it all.

I want to add some sort of softcap to a site i manage, so that IE users cannot access it.

Does anyone know how to go about this?

---

### Post by -grubby on 2009-09-24
What a responsible webmaster. Ever heard of [Browser Neutrality](http://www.anybrowser.org/campaign/)?

That aside, the best way to block IE would be to check the user agent and do stuff with it.

---

### Post by KiwiNZ on 2009-09-24
One question ...why ?

---

### Post by wojox on 2009-09-24
Like grubby said check user agent and redirect if IE. Do you have php installed? It can be done with that.

---

### Post by utnubuuser on 2009-09-24
+1 net neutrality

---

### Post by levian on 2009-09-24
this is interesting, i would like to know how too. hehe.

---

### Post by bruno9779 on 2009-09-24
The question isn't "why?" it is "why not?".

If the content of one site is specific to one browser, I don't see why not keep other browsers out. It is like targeted advertising.

---

### Post by -grubby on 2009-09-24
> **bruno9779 said:**
> 
If the content of one site is specific to one browser,


Please elaborate on how content can be specific to a web browser.

[quote=bruno9779]
I don't see why not keep other browsers out. It is like targeted advertising.
[/quote]

:confused:

---

### Post by wojox on 2009-09-24
It's a pain having to add extra code for IE 6/7 which a lot of people still use.

---

### Post by -grubby on 2009-09-24
Another thing: I'm not sure of your reasoning here, but if you want to block IE because you don't want to make sure your website works in IE, there's a much simpler solution: Just don't check if your site works in it.

A broken web page and a blocked web browser are equally unprofessional, but the first doesn't require as much work.

---

### Post by Sean Moran on 2009-09-24
Not meaning to interrupt but with the number of websites that popup that message of "Works best with IE" and that infernal flash block, I can see the point of such an exercise, although a little satirical IMHO.  (Best way to stop certain browsers from seeing your website is to turn off the modem before uploading.)

Determining the web-broswer from the http:request isn't difficult, although I'd have to do a little searching to get a script for it.  It's all been written up there.

---

### Post by bruno9779 on 2009-09-24
I am not likely to implement it on a website, but it is a skill I'd like to have.

My evil mind goes already off wandering what could come of it when added to a few other black-hat tricks...

---

### Post by -grubby on 2009-09-24
> **bruno9779 said:**
> I am not likely to implement it on a website

Thank god.

[quote=bruno9779]
but it is a skill I'd like to have.
[/quote]

Why? How would that be useful in any situation at all?

---

### Post by mehaga on 2009-09-24
Many sites work in IE only, he wants revenge :)  

I suggest you embarrass IE by using stuff it doesn't properly support yet - like Canvas. Put a message for IE users saying something like 'You need a modern browser to view this site (FF, Chrome...)' :p

---

### Post by Giant Speck on 2009-09-24
> **-grubby said:**
> Why? How would that be useful in any situation at all?

Because Microsoft is evil, Internet Explorer is a product of that evil, and the gullible public must be forcefully liberated from the tyranny.

---

### Post by bodyharvester on 2009-09-24
> **-grubby said:**
> Why? How would that be useful in any situation at all?

what if there is a mad scientist who uses IE and believes that if he can access the next website easily he will destroy the world :p

---

### Post by -grubby on 2009-09-24
> **vekaz said:**
> Many sites work in IE only, he wants revenge :)

I didn't know it was necessary to seek revenge when you disagree with something.

---

### Post by Giant Speck on 2009-09-24
> **-grubby said:**
> I didn't know it was necessary to seek revenge when you disagree with something.

I disagree with you.  I hope your wife and children like instant oatmeal.

---

### Post by -grubby on 2009-09-24
> **Giant Speck said:**
> I disagree with you.  I hope your wife and children like instant oatmeal.

haha

EDIT: that was meant to be in all caps.

---

### Post by Sean Moran on 2009-09-24
I'm starting to admire what I glean from the Ubuntu philosophy, so don't waste time with the revenge and stuff, but just get on with the good stuff...

... one compromise might even allow scope for a little tricky business; the facade of economy-class cyber travel in a way, and you could simply add a little button somewhere on the index page that mentions something like "Browser X viewers click here for deluxe edition" and leave the punters with something to sleep on overnight, without the need to change a single thing other if you don't want to.

Still a little clandestine, but it could get the required result without comprimising the best-quality of the sites, perhaps?  More of a comical satire.

---

### Post by mehaga on 2009-09-24
> **-grubby said:**
> I didn't know it was necessary to seek revenge when you disagree with something.

It's not and I don't think he should.

---

### Post by -grubby on 2009-09-24
> **vekaz said:**
> It's not and I don't think he should.

Is that what the little smiley face was for?

---

### Post by mehaga on 2009-09-24
> **-grubby said:**
> Is that what the little smiley face was for?

You read me like an open book :p

---

### Post by bruno9779 on 2009-09-24
Come on guys, it isn't exactly about revenge.

But think if anyone could drop those few fateful lines of code on the server that hosts this _[It is better with ...]("http://itsbetterwithwindows.com/")_

It would be just hilarious

---

### Post by KiwiNZ on 2009-09-24
> **bruno9779 said:**
> Come on guys, it isn't exactly about revenge.

But think if anyone could drop those few fateful lines of code on the server that hosts this _[It is better with ...]("http://itsbetterwithwindows.com/")_

It would be just hilarious

No it would not.

---

### Post by mehaga on 2009-09-24
OMG, it's even worse than revenge :D

---

### Post by t0p on 2009-09-24
html5

---

### Post by coldReactive on 2009-09-24
> **t0p said:**
> html5

There's already a piece of code (not from Microsoft) that allows IE8 to see and parse HTML5.

---

### Post by Cope57 on 2009-09-24
Does not matter what browser people use.  Create your site to be web standards compliant, and their browsers will do what they do.  A web standards compliant browser will be able to view your site with no issues.

The Basics - what you should run on all your web pages

[LIST]
[*] The [MarkUp Validator]("http://validator.w3.org/"). - Also known as the HTML validator, it helps check Web documents in formats like HTML and XHTML, SVG or MathML.
[*] The [Link Checker]("http://validator.w3.org/checklink") - Checks anchors (hyperlinks) in a HTML/XHTML document. Useful to find broken links, etc.
[*] The [CSS Validator]("http://jigsaw.w3.org/css-validator/") - validates CSS stylesheets or documents using CSS stylesheets.
[/LIST]

---

### Post by madnessjack on 2009-09-24
If you want to show something to IE, just use conditional comments
[http://en.wikipedia.org/wiki/Conditional_comment](http://en.wikipedia.org/wiki/Conditional_comment)

I use this for patches. If you write well formed html with css (using existing standards, none of this future experimental crap) you shouldn't have a problem in the first place.

As I said I use this to patch png and maybe the odd box model issue, but if you're excluding IE you're in the wrong. It's a perfectly good browser for anyone who doesn't know better (or more frankly, doesn't care).

---

### Post by x3roconf on 2009-09-24
Only jerks use internet explorer :lolflag:

---

### Post by hessiess on 2009-09-24
> **Cope57 said:**
> Does not matter what browser people use.  Create your site to be web standards compliant, and their browsers will do what they do.  A web standards compliant browser will be able to view your site with no issues.

The Basics - what you should run on all your web pages

[LIST]
[*] The [MarkUp Validator]("http://validator.w3.org/"). - Also known as the HTML validator, it helps check Web documents in formats like HTML and XHTML, SVG or MathML.
[*] The [Link Checker]("http://validator.w3.org/checklink") - Checks anchors (hyperlinks) in a HTML/XHTML document. Useful to find broken links, etc.
[*] The [CSS Validator]("http://jigsaw.w3.org/css-validator/") - validates CSS stylesheets or documents using CSS stylesheets.
[/LIST]

This would be fine except for the simple fact that _internet explorer is *NOT* standards compliant_ and things start to fall apart when you start using the more advanced features of CSS.

---

### Post by coldReactive on 2009-09-24
> **x3roconf said:**
> Only jerks use internet explorer :lolflag:

One of my best friends uses IE, and he's not all that of a jerk, believe me, he's a pacifist.

---

### Post by Fzang on 2009-09-24
Just pretend that IE doesn't exist and don't code anything specifically for IE. If the page looks like a malformed cow on IE it's their fault for using IE.

---

### Post by Xbehave on 2009-09-24
There are many reasons to block IE.
[LIST=1]
[*]To get back at IE users for IE-only sites
[*]To conduct polls with less noise from computer illiterate
[*]To conduct polls about Open-source with less noise from windows users
[*]It looks bad to have a malformed page and most IE users will blame you NOT IE
[*]**Because you can**
[/LIST]

From madnessjack's comment + google i think something like this may work (i think it goes in the <body> but i may be wrong)
```

<!--[if IE]>
    <script type="application/javascript">
      self.close();
    </script>
<![endif]>
```
or
```
<!--[if IE 6 ]>
    <script type="application/javascript">
      self.close();
    </script>
<![endif]>
```
repeat for 7 & 8

---

### Post by Tristam Green on 2009-09-24
> **x3roconf said:**
> Only jerks use internet explorer :lolflag:

What an awesome attitude to have.

All workers who are bound by their corporate IT policies to use Internet Explorer as an officially-supported (by Corp IT) are now jerks, by that logic.

> **Xbehave said:**
> There are many reasons to block IE.
[LIST=1]
[*]To get back at IE users for IE-only sites
[*]To conduct polls with less noise from computer illiterate
[*]To conduct polls about Open-source with less noise from windows users
[*]It looks bad to have a malformed page and most IE users will blame you NOT IE
[*]**Because you can**
[/LIST]

From madnessjack's comment + google i think something like this may work (i think it goes in the <body> but i may be wrong)
```

<!--[if IE]>
    <script type="application/javascript">
      self.close();
    </script>
<![endif]>
```
or
```
<!--[if IE 6 ]>
    <script type="application/javascript">
      self.close();
    </script>
<![endif]>
```
repeat for 7 & 8

All of the aforementioned reasons are bunk.

And, it's just as easy to block Jscript in IE as it is in Firefox.

---

### Post by Jackelope on 2009-09-24
Keep in mind that some IE users are not computer illiterate...we just prefer it because its pretty. :tongue:

Seriously tho, some of us HAVE to use it at work, but still would like to have access to the whole web.  So no IE blocking please. Just use HTML5 and embedded ogg videos. It will screw with IE until they get their stuff straight.

---

### Post by chucky chuckaluck on 2009-09-24
> **vekaz said:**
> Many sites work in IE only, he wants revenge :) 

there's no greater revenge than denying the majority of users access to your website. such a webmaster will have so much more time for other hobbies if no one is visiting his site.

---

### Post by madnessjack on 2009-09-24
Let's face it - the majority of users who browse the internet don't care. Maybe Microsoft is holding them back by not supporting these features but at the end of the day browsers were designed to display hypertext ([http://en.wikipedia.org/wiki/HTML](http://en.wikipedia.org/wiki/HTML)). There is nothing in the original definition for HTML that states browsers MUST display these fancy web applications.

The problems with IE6 lack of security is a different issue entirely...

TBH if we want to move on with the web I don't think HTML5 is the way to go. Just sayin.

Disclaimer: I am no expert, just ignorant ;-)

---

### Post by Xbehave on 2009-09-24
> **Tristam Green said:**
> All of the aforementioned reasons are bunk.

And, it's just as easy to block Jscript in IE as it is in Firefox.Right but at that point, the user is computer literate and can probably get past any trick you throw at them, and you could also write the entire page using javascript tricks so if you have no javascript the page wont render.

---

### Post by bruno9779 on 2009-09-24
> **Jackelope said:**
> Keep in mind that some IE users are not computer illiterate...we just prefer it because its pretty. 

:lolflag::lolflag::lolflag::lolflag:

how so?

---

### Post by koshatnik on 2009-09-24
> **Xbehave said:**
> There are many reasons to block IE.
[LIST=1]
[*]To get back at IE users for IE-only sites
[*]To conduct polls with less noise from computer illiterate
[*]To conduct polls about Open-source with less noise from windows users
[*]It looks bad to have a malformed page and most IE users will blame you 


Sounds a bit pathetic to me.

---

### Post by bodyharvester on 2009-09-24
> **x3roconf said:**
> Only jerks use internet explorer :lolflag:

surely no body took this seriously? its a joke people, laugh it off or shrug it off, there is no need to get your knickers in a twist over any opinion when its on the tinterweb

enjoy yourselves

can a security issue in a web browser affect the website it displays?

---

### Post by misfitpierce on 2009-09-24
[http://www.devin.com/ieblock_howto.shtml](http://www.devin.com/ieblock_howto.shtml) - That says it all with javascript way prob being the easiest. Enjoy.

---

### Post by Teber on 2009-09-24
> **Fzang said:**
> Just pretend that IE doesn't exist and don't code anything specifically for IE. If the page looks like a malformed cow on IE it's their fault for using IE.

amen to that. 

however there's a good reason for making a site accessible to IE: why keep IE users in the dark about the good things of linux? or for that matter about anything. isn't the internet all about information sharing?

---

### Post by Tristam Green on 2009-09-24
> **Xbehave said:**
> Right but at that point, the user is computer literate and can probably get past any trick you throw at them, and you could also write the entire page using javascript tricks so if you have no javascript the page wont render.

Does it matter though?  It's still wrong.

---

### Post by doas777 on 2009-09-24
if you really want to keep IE off your site, just make your code standards compliant. that'll do it. 
of course 99% conformance is much harder than simply testing your site in IE.

---

### Post by BslBryan on 2009-09-24
This has become more of a public debate than anything else.  The OP asked a question and posters came here and attacked him, when all against his idea should have just ignored him.  

His question was answered more than once and I suggest that this thread be closed.

---

### Post by koshatnik on 2009-09-24
> **BslBryan said:**
> This has become more of a public debate than anything else.  The OP asked a question and posters came here and attacked him, when all against his idea should have just ignored him.  

His question was answered more than once and I suggest that this thread be closed.

Chill out man. Banter and conjecture is good.

---

### Post by Barrucadu on 2009-09-24
Here's an excerpt of the code from my website:
[php]function usingIE($patronise=true) {
  $usingie = strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE') || isset($_GET['ie']);

  if($usingie && $patronise) {
    patronisingMessage();
  }

  return $usingie;
}[/php]

**patronisingMessage()** prints a [message](http://www.barrucadu.co.uk/?ie) using *really* basic HTML and CSS telling users to use a proper browser :p
I've also got a warning on the main page (which, obviously, only non-IE users see) saying it may not work in anything but Opera 10 and FF 3.5, as that's all I've tested the site in.

I got tired of &#8216;helpful&#8217; emails saying it doesn't work in IE. I know. I don't care. It should support the standards. It's not my fault the developers are incompetent.

---

### Post by hoppipolla on 2009-09-24
Haha I think this is a wicked idea xD

And well said Barrucadu, I agree. One of my sites breaks a bit on IE too which is just ridiculous as it's obviously a bug in the browser - it works fine in Firefox and Chrome! :)

---

### Post by tcoffeep on 2009-09-24
This thread, and everyone who thinks this is a good idea, is/are ridiculous.

---

### Post by hoppipolla on 2009-09-24
> **tcoffeep said:**
> This thread, and everyone who thinks this is a good idea, is/are ridiculous.

I just think it's funny ._.

---

### Post by doas777 on 2009-09-24
> **tcoffeep said:**
> This thread, and everyone who thinks this is a good idea, is/are ridiculous.


well thank you for setting us straight. where would we be without your wisdom?

oh yeah, we'd be enjoying this thread.

---

### Post by coldReactive on 2009-09-24
> **tcoffeep said:**
> This thread, and everyone who thinks this is a good idea, is/are ridiculous.

Well, if abc.go.com doesn't allow linux users to view full episodes, then why not break IE users by not letting them view our websites.

---

### Post by fela on 2009-09-24
> **x3roconf said:**
> Only jerks use internet explorer :lolflag:

Ignorant people and jerks.

And microsoft employees. But I guess that falls under 'jerks'.

Actually, no. I bet most microsoft employees run firefox or chrome.

---

### Post by fela on 2009-09-24
> **coldReactive said:**
> Well, if abc.go.com doesn't allow linux users to view full episodes, then why not break IE users by not letting them view our websites.

Because of rule #21 in life: two wrongs don't make a right.

---

### Post by Incendia on 2009-09-24
> **x3roconf said:**
> Only jerks use internet explorer :lolflag:

> **coldReactive said:**
> One of my best friends uses IE, and he's not all that of a jerk, believe me, he's a pacifist.

> **Jackelope said:**
> Keep in mind that some IE users are not computer illiterate...we just prefer it because its pretty. :tongue:

I use it side-by-side with Firefox on my Windows 7 Partition, because it does look nice. & I don't think I'm a jerk. :]

---

### Post by unoodles on 2009-09-24
What you really should do is drop this simple line of code in your website.
No need to check user-agents.

[http://crashie.com/](http://crashie.com/)

---

### Post by CJ Master on 2009-09-24
> **unoodles said:**
> What you really should do is drop this simple line of code in your website.
No need to check user-agents.

[http://crashie.com/](http://crashie.com/)

AVG blocked the website. I assume it makes Internet Explorer crash?

---

### Post by doas777 on 2009-09-24
> **CJ Master said:**
> AVG blocked the website. I assume it makes Internet Explorer crash?

if you are using IE7 or earlier with javascript enabled.
the line involved is:
[PHP]<script>for(x in document.write){document.write(x);}</script>[/PHP]

---

### Post by CJ Master on 2009-09-24
> **doas777 said:**
> if you are using IE7 or earlier with javascript enabled.
the line involved is:
[PHP]<script>for(x in document.write){document.write(x);}</script>[/PHP]

I am by no means a Javascript expert, but that looks like a simple infinite loop.

---

### Post by coldReactive on 2009-09-24
> **CJ Master said:**
> I am by no means a Javascript expert, but that looks like a simple infinite loop.

even simpler:
```
while(1) { /* blah */ }
```

---

### Post by 1clue on 2009-09-24
> **bruno9779 said:**
> The question isn't "why?" it is "why not?".

If the content of one site is specific to one browser, I don't see why not keep other browsers out. It is like targeted advertising.

Except that someone who may be interested in converting to that browser can't see some sort of pertinent information that may be useful?

Linux is all about open standards.  Exclusion is a Microsoft tactic.  Internet neutrality++.

Let me know what site you're talking about, and I'll be sure I won't go there with Firefox either.

---

### Post by doas777 on 2009-09-24
> **CJ Master said:**
> I am by no means a Javascript expert, but that looks like a simple infinite loop.

I'm not great with jscript either, but it seems like there is a recursive element as well.

---

### Post by michaelzap on 2009-09-24
I've used this (as a PHP function):
```
$output='';

$oldIE=false;
$ua=strtolower($_SERVER['HTTP_USER_AGENT']);
if((strstr($ua,"win")) && (strstr($ua,"msie")) && !(strstr($ua,"opera"))){
   $all_browser_info=explode(" ",stristr($ua,"msie"));
   $IEversion=$all_browser_info[1];
   if($IEversion<7){
      $oldIE=true;
   }
}

if ($oldIE==true){
   $output='<div id="ie6">
<h1>Your browser needs to be updated</h1>
<p>You appear to be using Internet Explorer 6.<br /><strong>This browser was released in 2001 and our website - along with many others - may not display or function properly</strong> with such an outdated browser.<br />In addition, <strong>this browser is not secure</strong>, and browsing the internet with it may expose you to many more risks.</p>
<p>Please use one of the links below (or Windows Update) to upgrade your browser now.</p>
<p><a href="http://www.microsoft.com/windows/internet-explorer/" target="_ie8">Internet Explorer 8</a> | <a href="http://www.mozilla.com/en-US/firefox/" target="_ff">Mozilla Firefox</a></p>
<p>Note: If you are in a corporate or other environment where you cannot install or update software on your own, please contact your technical support staff<br />to resolve this. This is not a condition that should continue to be ignored.</p>
</div>

';
}

return $output;
```

But I will probably use [this]("http://www.pushuptheweb.com/") in the future.

IE6 really is the bane of a web designer's existence, and it's probably responsible for the infection of the majority of zombie PCs in the world.

---

### Post by hoppipolla on 2009-09-24
> **michaelzap said:**
> IE6 really is the bane of a web designer's existence, and it's probably responsible for the infection of the majority of zombie PCs in the world.

I never support IE6 when I make sites... I only learnt recently that people even still use it! lol

---

### Post by Viva on 2009-09-24
Being a webmaster, I've considered this too. It is a pain in the **** to make your website work properly in some versions of IE even though you follow web standards. You'll end up hating IE after a few tries.

---

### Post by ecmatter on 2009-09-24
> **Teber said:**
> isn't the internet all about information sharing?

No.  The internet is all about false choices and straw men.

---

### Post by michaelzap on 2009-09-24
> **ecmatter said:**
> No.  The internet is all about false choices and straw men.

I thought it was about buying stuff that you don't really need and that seems cheap until you add in the shipping and handling.

---

### Post by doas777 on 2009-09-24
> **ecmatter said:**
> No.  The internet is all about false choices and straw men.

and  Cats are made of Rubber and Lies.

---

### Post by tcoffeep on 2009-09-24
> **doas777 said:**
> well thank you for setting us straight. where would we be without your wisdom?

oh yeah, we'd be enjoying this thread.

Thank you for proving my point.

You, all of you, who think this is an LOLFUNNY thing to do, you need to get your act together. The entire "They do it, so let's do it back!" is flawed, useless, and a waste of your time. You should be looking for ways to open doors, not slam them shut, lock them, and sit there with a shotgun *just-in-case-those-rat-bastards-break-through*.
I'm ashamed that I claim to be a part of the linux community when some of you, who think this is something smart to do or funny, claim the same. I'm hoping that one day linux and windows users can talk without some ignorant ******* going on about why X is better than Y.
IE isn't as bad as half of you make it out to be. I know people who use IE and make it work(tm), without problems, and have tried Firefox/Opera/Chrome/etc and preferred IE. It's a personal choice on their end, and they're jerks? Not to mention that they've never caught viruses. They don't complain if a website breaks on them because their browser isn't fully-compatible (which, iirc, ms is working on). They switch to another -if they have to-, which most of the time, they don't, because half the time, it's a crappy second-rate blog.
I'm tired of reading these stupid threads about trying to block user's access to certain websites. The users don't do it. The people who run the websites do. If you want to get back at them, block their IP, don't f*** over your everyday user. Not everyone is an idiot.
On that note, I'm done with this thread. There are some of you in this thread making sense, but a lot of you are just being immature little kids.

-B

---

### Post by horace on 2009-09-24
Using xhtml and serving it with the correct content type of application/xhtml+xml is something IE still can't cope with, and standards-compliant too!

---

### Post by SomeGuyDude on 2009-09-24
Thread nominated for both "dumbest idea in a while" and "perfect reinforcement for why Linux users are seen as jack@sses".

---

### Post by tcoffeep on 2009-09-24
> **SomeGuyDude said:**
> Thread nominated for both "dumbest idea in a while" and "perfect reinforcement for why Linux users are seen as jack@sses".

*props*

Sup, holmes?

---

### Post by michaelzap on 2009-09-24
> **tcoffeep said:**
> *props*

Sup, holmes?

And now also for "Most likely to attract trolls who just want to demonstrate their capacity for OUTRAGE at anything they disagree with".

---

### Post by tcoffeep on 2009-09-24
> **michaelzap said:**
> And now also for "Most likely to attract trolls who just want to demonstrate their capacity for OUTRAGE at anything they disagree with".

I'm sorry. But I'm not going to respect a thread that restricts freedom ;) isn't that the "Linux Way"?

---

### Post by michaelzap on 2009-09-24
> **tcoffeep said:**
> I'm sorry. But I'm not going to respect a thread that restricts freedom ;) isn't that the "Linux Way"?

I'm not asking you to change your opinion or respect anything that you don't. We probably would agree on the general issue of whether it's wise or petty to block IE from viewing a website. What I would ask you to reconsider is your attitude and manner of expressing your opinion.

Shouting someone down and insulting people who express an opinion or idea isn't likely to convince them. It might silence them, but it doesn't convince them. And it's all to common nowadays for people to mistake volume for passion and think that shouting, "You're wrong and an idiot and I'm done talking to you!" is a perfectly acceptable way to participate in a community discussion.

Consider also the effect that your attitude has on the general feeling of friendliness and openness in these forums in general, and how a newcomer who reads this thread might feel concerned about expressing an opinion or idea that might be jumped on like this.

---

### Post by TheBuzzSaw on 2009-09-24
[http://www.werewolfhaven.net/](http://www.werewolfhaven.net/)

Check the HTML near the top. There is code that targets IE and redirects (IE6 specifically, in this case).

```
<!--[if lte IE 6]>
    <script type="text/javascript">window.location='ie6.html';</script>
    <noscript><meta http-equiv="refresh" content="1;URL=ie6.html"></noscript>
<![endif]-->
```

[http://www.werewolfhaven.net/ie6.html](http://www.werewolfhaven.net/ie6.html)

LOL

---

### Post by tcoffeep on 2009-09-24
I wouldn't want a newcomer reading a thread like this. It's offensive, to say in the least. Especially, say, if they're considering switching to Ubuntu and are using IE to check out the forums. First thing they see are things like "How do I stop the user's freedom if they choose to use IE?" when, apparently, we're supposed to embrace freedom (well.. sorta). Or that they're jerks. It's offensive. I'm only stating my opinion. I don't butter it up, and try to serve it to be delightful.


My cookies, on the other hand, are delightfully sweet with a hint of cinnamon. Those, I try to make acceptable. :)

---

### Post by doas777 on 2009-09-24
> **tcoffeep said:**
> I'm sorry. But I'm not going to respect a thread that restricts freedom ;) isn't that the "Linux Way"?


as long as you're having fun I suppose...

---

### Post by TheBuzzSaw on 2009-09-24
It's hardly a freedom issue. For instance, why let IE view Firefox add-on pages? ;)

---

### Post by michaelzap on 2009-09-24
> **tcoffeep said:**
> I wouldn't want a newcomer reading a thread like this.

Now consider how that same newcomer might feel if they read this thread and friendly Linux users generously explain why this isn't such a good idea and how it goes against the spirit of Ubuntu instead of shouting insults at each other. They'd both understand that point of view and also feel comfortable here. You'd still be expressing your opinion, and maybe it would even be heard and appreciated.

---

### Post by SomeGuyDude on 2009-09-24
> **TheBuzzSaw said:**
> It's hardly a freedom issue. For instance, why let IE view Firefox add-on pages? ;)

If you're putting Firefox specific code simply for purposes of excluding non-FF users, that makes you a Class A douchebag.

I can't stand people who feel slighted by someone or another so they think the best solution is to act just as childish as the other guy. Way to make the community look good, fellas.

---

### Post by dragos240 on 2009-09-24
> **levian said:**
> this is interesting, i would like to know how too. Hehe.

+1

---

### Post by tcoffeep on 2009-09-24
> **TheBuzzSaw said:**
> It's hardly a freedom issue. For instance, why let IE view Firefox add-on pages? ;)

what if they're curious over the advantages

---

### Post by hoppipolla on 2009-09-24
People need to learn to just take things lightly :(

It just made me laugh when I saw the thread concept, and if he wants to do that with his site then that's his choice. It's not a big deal.

---

### Post by michaelzap on 2009-09-24
> **SomeGuyDude said:**
> I can't stand people who feel slighted by someone or another so they think the best solution is to act just as childish as the other guy. Way to make the community look good, fellas.

Interesting comment given your posts here...

Firefox add-ons only work in Firefox, so it would obviously make sense to redirect IE users in that case, no?

---

### Post by tcoffeep on 2009-09-24
Wait. I said I was done with this thread.

Damn it!

---

### Post by dragos240 on 2009-09-24
What I would like to do Is block IE users to my site, and Redirect them to the fiefox page.

---

### Post by Viva on 2009-09-24
> **SomeGuyDude said:**
> Thread nominated for both "dumbest idea in a while" and "perfect reinforcement for why Linux users are seen as jack@sses".

Are they? The general opinion is that linux users are geeks. Terms like Zealots and Jackasses are often used by windows power users and politically correct douchebags with holier-than-thou attitude either to score cheap points or to end a conversation.

---

### Post by hoppipolla on 2009-09-24
> **Viva said:**
> Are they? The general opinion is that linux users are geeks. Terms like Zealots and Jackasses are often used by windows power users and politically correct douchebags with holier-than-thou attitude either to score cheap points or to end a conversation.

Ok that's more flame bait (and man I really think this thread needs to just **calm down** lol) but it did make me smile, and you may be right lol :)

---

### Post by TBOL3 on 2009-09-24
> **fela said:**
> Because of rule #21 in life: two wrongs don't make a right.

Sweet, a list of rules to follow.  Thanks so much, only can you tell me what #1-20 is?  Also, I would like to know if there is more than 21...thanks, this will make my life much easier (maybe I can make a bash script for it).

---

### Post by TheBuzzSaw on 2009-09-24
> **SomeGuyDude said:**
> If you're putting Firefox specific code simply for purposes of excluding non-FF users, that makes you a Class A douchebag.

I can't stand people who feel slighted by someone or another so they think the best solution is to act just as childish as the other guy. Way to make the community look good, fellas.
Hardly. Targeting certain browsers for technical reasons is perfectly acceptable. I can agree that blocking out certain browsers strictly for social/political reasons is pretty low, but your idea of "blocking for any reason = evil" is severely misguided.
> **tcoffeep said:**
> what if they're curious over the advantages
I'm not implying that it's a good idea. I'm just indicating that there *are* valid reasons for blocking certain browsers outside of pure hatred.

---

### Post by Warpnow on 2009-09-24
> **dragos240 said:**
> What I would like to do Is block IE users to my site, and Redirect them to the fiefox page.

Because god forbid anyone disagree with you that FF is better than IE?

Especially seeing as how if you are, say, running Windows 98 on a pentium 2 with 128mbs of ram, as a few of my friends are, Firefox will not boot let alone browse webpages, so ie is their only option.

If I heard a site was doing this, I would stop visiting them. No way I'm going to associate myself with such disgraceful pieces of crap.

---

### Post by KiwiNZ on 2009-09-24
If I were to say to much about this idea I would probably breach the COC so I am going say what can be stated has been stated and close this ......................

---


---
title: "? The future browser for Ubuntu?"
date: 2006-10-03
forum: The Cafe
---

### Post by nu2this on 2006-10-03
I was just curious will Ubuntu be taking up this browser?
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
Too late for Edgy, but beyond?

---

### Post by maniacmusician on 2006-10-03
it'd be interesting. but for me, it depends on how functional it is with ff extensions. also how attractive it is. I cant stand ugly browsers, they ruin my day.

---

### Post by K.Mandla on 2006-10-03
> **maniacmusician said:**
> it'd be interesting. but for me, it depends on how functional it is with ff extensions. also how attractive it is. I cant stand ugly browsers, they ruin my day.
It's working for me, and it doesn't seem any uglier. I found a 386 package [here]("ftp://mirrors.usc.edu/pub/gnu/gnuzilla"), and all my extensions (all four of them) are working just fine.

---

### Post by rowanparker on 2006-10-03
> **maniacmusician said:**
> it'd be interesting. but for me, it depends on how functional it is with ff extensions. also how attractive it is. I cant stand ugly browsers, they ruin my day.
I know the feeling.

School uses Internet Explorer ](*,)

---

### Post by slimdog360 on 2006-10-03
"Love is like riding through the frozen tundra on a snowmobile. Suddenly it flips over, and you are trapped. Then at night, the ice weasels come."

can someone post a link to a screenshot or two of Iceweasel, I cant find any and Im in between operating systems at the moment.

---

### Post by _simon_ on 2006-10-03
^ It looks just like firefox, apart from it saying "Iceweasel" in the title bar you'd never know the difference.

---

### Post by Jussi Kukkonen on 2006-10-03
> can someone post a link to a screenshot or two of Iceweasel, I cant find any and Im in between operating systems at the moment.

Oh poor you... Did your X break your heart?

---

### Post by rowanparker on 2006-10-03
New users wouldn't know to look for IceWeasel, they will be asking for firefox. If it is made clear to them that IceWeasel is exactly the same, it will be alright.

---

### Post by _simon_ on 2006-10-03
If iceweasel was packaged with Ubuntu and showed in the menu then they would use it.

---

### Post by rowanparker on 2006-10-03
> **_simon_ said:**
> If iceweasel was packaged with Ubuntu and showed in the menu then they would use it.
Only if they were told.

Before this thread, I didn't know what IceWeasel was, nor would I just open it whilst looking for a web browser.

---

### Post by llonesmiz on 2006-10-03
Well, in the menu you'd see "IceWeasel Web Browser"...

---

### Post by mushroom on 2006-10-03
Was it really necessary to call it Iceweasel?

---

### Post by _simon_ on 2006-10-03
> **rowanparker said:**
> Only if they were told.

Before this thread, I didn't know what IceWeasel was, nor would I just open it whilst looking for a web browser.

Yeah but the Applications menu has an Internet submenu, if Iceweasel was listed there the same way Firefox is then they would know.

Firefox is listed as "Firefox Web Browser" so they would just need to put "Iceweasel Web Browser" ;)

---

### Post by Kateikyoushi on 2006-10-03
Looks like a solution to the firefox misery.

---

### Post by zenwhen on 2006-10-03
> **rowanparker said:**
> Only if they were told.

Before this thread, I didn't know what IceWeasel was, nor would I just open it whilst looking for a web browser.

If it uses a globe icon, people will click it.

---

### Post by henriquemaia on 2006-10-03
Dillo! Lynx! Save the web!

---

### Post by sabitha on 2006-10-03
> **llonesmiz said:**
> Well, in the menu you'd see "IceWeasel Web Browser"...

how to install?
what about plugins?

---

### Post by maniacmusician on 2006-10-03
dillo is one of them ugly browsers that I can't stand. I used it once, and didnt enjoy it all. it's fast, but thats it.

---

### Post by henriquemaia on 2006-10-03
> **maniacmusician said:**
> dillo is one of them ugly browsers that I can't stand. I used it once, and didnt enjoy it all. it's fast, but thats it.

You can't judge others by the looks. What matters is what's in one's heart. ;)

---

### Post by Michael_aust on 2006-10-03
To solve the problem of people not knowing what iceweasel was, couldnt uou just create a meta package for firefox, that would have iceweasel as a dependency.  Then during the install pop up a message saying the reason why it is not called firefox.

---

### Post by K.Mandla on 2006-10-03
> **sabitha said:**
> how to install?
what about plugins?
If you use that compressed 386 package from the ftp link above, decompress it and there's an iceweasel executable inside. I've put mine in my home directory, and redirected Openbox's menu at it. Works like a champ.

I think the look is going to take on whatever GTK2 (?) engine you've got going. I've got the mist engine out of the repositories, and it looks exactly like firefox and swiftfox before it.

[[IMG]http://img395.imageshack.us/img395/5060/screenshotza6.th.png[/IMG]](http://img395.imageshack.us/my.php?image=screenshotza6.png)

Plugins install just like you're used to -- straight from the Mozilla site, or as .xpi files locally.

I like it, actually. And if it comes with a clear conscience and without the baggage that Mozilla has attached to Firefox, I'm switching. :biggrin:

---

### Post by saracen on 2006-10-03
Could someone make a .deb of this?

---

### Post by slimdog360 on 2006-10-03
just got it. It seems to work well but I have got the 'random webpage when mouse click' thing happening a couple of times. not happy jan. But certianly better then firefox if its completely open; Id like to see it being used in edgy. Or maybe a modded epiphany.

---

### Post by slimdog360 on 2006-10-03
> **saracen said:**
> Could someone make a .deb of this?

it runs just like the firefox download. You just have to untar it and call it from either a launcher or terminal, I mean like typing 'iceweasel' minus the quotes into a terminal. So no need to .deb it. You could just replace the iceweasel folder with the mozilla folder for an install.

---

### Post by prizrak on 2006-10-03
The user will not be confused. All you do is make a shortcut, label it "INTERNET" and you are done.

---

### Post by K.Mandla on 2006-10-03
Yup. Just [download the file]("ftp://mirrors.usc.edu/pub/gnu/gnuzilla/iceweasel-1.5.0.4-g1-i386.tar.bz2"). Then

```
tar -xvf iceweasel* -C the_directory_where_you_want_iceweasel_to_reside
```
Of course, if you want it outside your home directory, you need to prefix that with *sudo*.

After that, you can switch to it with the "Preferred Applications" menu ... is that still what it's called in Gnome? I think that's right for Xubuntu.

---

### Post by Brunellus on 2006-10-03
> **Jussi Kukkonen said:**
> Oh poor you... Did your X break your heart?
late to this party, but usually the fix is

sudo dpkg-reconfigure heart

---

### Post by mips on 2006-10-03
> **rowanparker said:**
> New users wouldn't know to look for IceWeasel, they will be asking for firefox. If it is made clear to them that IceWeasel is exactly the same, it will be alright.

I doubt it, people don't even get the swiftfox thing. They heard the word firefox and it sticks like you cannot believe.

---

### Post by Brunellus on 2006-10-03
> **mips said:**
> I doubt it, people don't even get the swiftfox thing. They heard the word firefox and it sticks like you cannot believe.
it's the one familiar word and program in a completely new universe for them, so I don't blame them, really.

---

### Post by K.Mandla on 2006-10-03
Just an FYI, I typed up a quick howto for installing IceWeasel; I'm guessing it will appear in that section in a little bit, once it's approved. (Hint, hint.) 

I know it's kind of dumb to write a howto on something simple like that, but it might be a boost for folks who wouldn't otherwise try it.

---

### Post by maniacmusician on 2006-10-03
the only dumb howto is one that doesnt work :D

---

### Post by Polygon on 2006-10-04
i imagine not soon after this new browser comes standard on ubuntu, there will be scripts to change the icon  AND change the name.

---

### Post by ciscosurfer on 2006-10-04
Just downloaded the Weasel.  Holy crap!  Super fast.  Kicks Firefox to the curb and beats down Swiftfox with ease.  Love the option to install Gnash.  This just might be the next great browser!

---

### Post by macogw on 2006-10-04
> **rowanparker said:**
> Only if they were told.

Before this thread, I didn't know what IceWeasel was, nor would I just open it whilst looking for a web browser.

Well the little world didn't look like the Firefox logo, did it?  It says "Firefox Web Browser, Browse the World Wide Web" when you hover over the little globe.  So, it'll now say "Iceweasel Web Browser, Browse the World Wide Web" and that little tooltip that shows when you hover will serve the same purpose.

I just want to know if FF extensions will still work with it.

---

### Post by macogw on 2006-10-04
> **K.Mandla said:**
> Yup. Just [download the file]("ftp://mirrors.usc.edu/pub/gnu/gnuzilla/iceweasel-1.5.0.4-g1-i386.tar.bz2"). Then

```
tar -xvf iceweasel* -C the_directory_where_you_want_iceweasel_to_reside
```
Of course, if you want it outside your home directory, you need to prefix that with *sudo*.

After that, you can switch to it with the "Preferred Applications" menu ... is that still what it's called in Gnome? I think that's right for Xubuntu.

What directory would you put to make it available to all users?

---

### Post by Kateikyoushi on 2006-10-04
If this is the preinstalled browser new users going to start it as the name says web browser. On the home page they could read an explanation for the name change.

---

### Post by argie on 2006-10-04
If this is such a big problem, surely you could use the globe logo and if there is still trouble, call it "Iceweasel (Firefox Clone)"?

---

### Post by cunawarit on 2006-10-04
I think the key thing is for it to be fully compatible with Firefox extensions. Firefox is a nice browser. But browsers like Opera 9 and Internet Explorer 7 are also nice browsers. What to me separates Firefox from those two is the amazing amount of useful extensions available. 

As for things like Dillo, good on the guys developing it! The world needs a fast, unbloated browser. But Dillo is nowhere near usable as your sole browser yet. 

On a day to day basis I use two browsers. Firefox and eLinks/Links (depending on what machine I am using). I’m a Web developer and I use Firefox for its great development extensions, and Links for its speed and to make sure things look good on text only.

---

### Post by graabein on 2006-10-04
> **K.Mandla said:**
> I like it, actually. And if it comes with a clear conscience and without the baggage that Mozilla has attached to Firefox, I'm switching. :biggrin:

I'm late on this. What baggage is there on Firefox? Can someone post some links please? I've heard of Swiftfox and Flock but IceWeasel is new to me.

:-k

---

### Post by _simon_ on 2006-10-04
Some blurb on Gnuzilla and IceWeasel:
> 
Introducing Gnuzilla and IceWeasel

Gnuzilla is the GNU version of the Mozilla suite, and IceWeasel is the GNU version of the Firefox browser. Its main advantage is an ethical one: it is entirely free software. While the source code from the Mozilla project is free software, the binaries that they release include additional non-free software. Also, they distribute non-free software as plug-ins. (IceWeasel does keep the triple licensing used by Firefox to facilitate the reuse of code.)

IceWeasel also includes some privacy protection features:

   1. Some sites refer to zero-size images on other hosts to keep track of cookies. When IceWeasel detects this mechanism it blocks cookies from the site hosting the zero-length image file. (It is possible to re-enable such a site by removing it from the blocked hosts list.)
   2. Other sites rewrite the host name in links redirecting the user to another site, mainly to "spy" on clicks. When this behavior is detected, IceWeasel shows a message alerting the user.


---

### Post by hk_2999 on 2006-10-04
Im completely confused, and a bit late on the news?

Why would ubuntu want to replace firefox?

What makes it broken?

If it aint broke, don't fix it.

---

### Post by brt on 2006-10-04
+1 IceWeasel as Ubuntus default Browser

keeping the globe icon may help some users.

as IceWeasel is more secure, faster (true?) and all the Firefox Extensions can be used its "safe" to drop the name Firefox. 

I think most People won't judge browsers by their name but functionality. And for the rest there will always be the option to install the genuine firefox anyways.

---

### Post by hk_2999 on 2006-10-04
But isn't Firefox 2.0 coming soon?

I'm sure it'll be very secure and even includes phishing filters and all.

Mozilla had never been known for their incompetence.

---

### Post by dca on 2006-10-04
> **hk_2999 said:**
> But isn't Firefox 2.0 coming soon?

I'm sure it'll be very secure and even includes phishing filters and all.

Mozilla had never been known for their incompetence.

Yeah, but the problem wasn't with the browser or its functionality, it was with Mozilla getting up in arms about icons, trademarks, and the like if it is going to be included in a Linux distro...  If the distro(s) don't supply the proper icon (the fox w/ the globe or something) and other issues, the distros can't use the name...   Who knows, maybe this could now be an option (preferred browser installation) for the user to decide during install.  I believe Opera is now in the repos and that's my default browser...

---

### Post by K.Mandla on 2006-10-04
> **brt said:**
> keeping the globe icon may help some users.
Or installed by default with the Tango network icon ... or a variation thereof.

> **macogw said:**
> What directory would you put to make it available to all users?
/usr/opt? maybe /usr/share? I know Swiftfox installs to /usr/lib/ ... Perhaps someone has a suggestion for that. I don't usually work with multi-user machines ... :(

---

### Post by Polygon on 2006-10-04
> **hk_2999 said:**
> But isn't Firefox 2.0 coming soon?

I'm sure it'll be very secure and even includes phishing filters and all.

Mozilla had never been known for their incompetence.

then the debian or ubuntu devs will simply update iceweasle or whatever with the new 2.0 code. The only real thing we are not allowed to use is the firefox name and logo, all the other code we can use and distribute freely. So give it a week or two after 2.0 comes out and im sure you will see the updated ubuntu/debian browser for ubuntu.

---

### Post by AndyCooll on 2006-10-04
> **graabein said:**
> I'm late on this. What baggage is there on Firefox? Can someone post some links please? I've heard of Swiftfox and Flock but IceWeasel is new to me.

:-k

It's all linked to whether Firefox is free or not. See here: [Firefox not really free?]("http://www.internetnews.com/dev-news/article.php/3634591")

:cool:

---

### Post by K.Mandla on 2006-10-04
> **AndyCooll said:**
> It's all linked to whether Firefox is free or not.
And unfortunately, Swiftfox's terms seem likewise restrictive.

[quote=Swiftfox Web site]Binaries provided by [getswiftfox.com]("http://www.getswiftfox.com") are not licensed MPL and therefore are not freely distributable. The license to use Swiftfox extends to the user that downloads Swiftfox from this web site. No one may repackage or redistribute Swiftfox binaries in any form without prior permission. Any questions relating to licensing can be directed to me and I will do my best to assist. Please also note that the licensing restrictions were put in place to safeguard Swiftfox users against the possibility of obtaining tainted versions from anyone who may wish to maliciously alter the binary and redistribute it. **Yes, that makes Swiftfox "non-free" in the Debian sense** but it will always be free of charge to all users. If anyone has a better solution I would be glad to hear it.

Source code is available. Swiftfox is trademark Jason Halme and as such any unofficial builds need to be named differently and can not use the Swiftfox brand.

Downloading any binary, source package or patch from this web site constitutes acceptance of these terms and those mentioned in the license. [/quote]
(Emphasis is mine.) More [here]("http://www.getswiftfox.com/LICENSE").

I'm a little embarrassed that I was such a proponent. :-#

---

### Post by Polygon on 2006-10-04
ok i just downloaded iceweasel... its pretty freaking fast, loads at least twice as fast as firefox does. But i have noticed i cant install google toolbar cause it says i dont have firefox.... this might pose a problem when some people try to install some other extensions

and i also notice that the default theme is still "firefox: the browser reloaded", can we still use the default theme or do we have to change the name there too?

---

### Post by K.Mandla on 2006-10-04
Try opening about:config in the address bar, then changing general.useragent.extra.firefox to read "firefox" rather than "iceweasel" ... that might do the trick.

I haven't tried themes yet. Download one and tell us what happens.

---

### Post by Kilz on 2006-10-04
> **K.Mandla said:**
> And unfortunately, Swiftfox's terms seem likewise restrictive.


(Emphasis is mine.) More [here]("http://www.getswiftfox.com/LICENSE").

I'm a little embarrassed that I was such a proponent. :-#

Sadly the author takes away the freedoms of users, without really adding anything. Unlike Flock, Swiftfox is a duplicate of Firefox. If anything it takes away things to make itself load faster.

---

### Post by Stirling on 2006-10-04
> **Kilz said:**
> If anything it takes away things to make itself load faster.
I am curious, what is disabled besides Pango?

---

### Post by K.Mandla on 2006-10-04
> **mushroom said:**
> Was it really necessary to call it Iceweasel?

[Quote=Wikipedia]The name comes from a Matt Groening quote: "Love is like riding through the frozen tundra on a snowmobile. Suddenly it flips over, and you are trapped. Then at night, the ice weasels come."[/quote]

[http://en.wikipedia.org/wiki/IceWeasel](http://en.wikipedia.org/wiki/IceWeasel)

---

### Post by Kilz on 2006-10-04
> **Stirling said:**
> I am curious, what is disabled besides Pango?

Even if its only one thing, thats enough. Especialy since it doesnt add anything, like say Flock (even when adding it is released under the gpl though). It also takes away one of the [4 main freedoms of free software.]("http://www.gnu.org/philosophy/free-sw.html") The freedom of redistribution. Firefox allows users to redistribute it, Swiftfox does not.

---

### Post by K.Mandla on 2006-10-04
> **Stirling said:**
> I am curious, what is disabled besides Pango?
The [changelog for Swiftfox 1.5.0.7]("http://www.getswiftfox.com/builds/releases/changelog") might give you an idea of what's there or disabled. 

I've got nothing against Swiftfox, but I see now I should have been a little more aware of the terms -- and guts -- of what I was endorsing. 

My apologies. :(

---

### Post by wmcbrine on 2006-10-04
I see people saying Iceweasel is faster than Firefox.
Does anyone know why that would be?

---

### Post by Polygon on 2006-10-04
well as far as i know they removed all the things that pertain to the name "firefox" and all the other non free stuff, and they made a few improvements of their own, so maybe somehow doing those things made it run like 2x faster then firefox

---

### Post by plb on 2006-10-04
> **Polygon said:**
> well as far as i know they removed all the things that pertain to the name "firefox" and all the other non free stuff, and they made a few improvements of their own, so maybe somehow doing those things made it run like 2x faster then firefox

yeah they also added increased privacy features....I have faith in the debian devs...they are a knowledgable bunch.

---

### Post by K.Mandla on 2006-10-05
P.S.: The howto I promised is [here]("http://www.ubuntuforums.org/showthread.php?t=270631"). I'm a little embarrassed by it; it's such a thumbsucker of a howto. :oops:

---

### Post by Lopsicle on 2006-10-05
I just downloaded it and wow it is fast. Thanks K.Mandla for your "how to"
Yeah! we want more thumbsucker "how too's"

---

### Post by slimdog360 on 2006-10-05
we need a new icon. Im thinking a globe covered in ice with a weasel on top.

---

### Post by K.Mandla on 2006-10-05
> **slimdog360 said:**
> we need a new icon. Im thinking a globe covered in ice with a weasel on top.
Hey, yeah. that would be cool. Kind of an upside down firefox logo, but in light blue and icy looking ... hmmm ... :-k

---

### Post by Brunellus on 2006-10-05
it should go in the ubuntu 'frisky ferret' release.  or something.

---

### Post by slimdog360 on 2006-10-05
Im going to take a crack at the source code and see if I can fix the random webpage thingy. I see its caused by some text being highligted then the mouse click puts this into the address bar and searches for the closest thing.
 Its very annoying.

---

### Post by K.Mandla on 2006-10-05
How is that happening again? Highlight text and click and it takes you to a random page? I'm not getting that here. What extensions do you have installed?

---

### Post by slimdog360 on 2006-10-05
noscript and adblockplus but it happens without them and even then not all the time.

---

### Post by prizrak on 2006-10-05
> **slimdog360 said:**
> Im going to take a crack at the source code and see if I can fix the random webpage thingy. I see its caused by some text being highligted then the mouse click puts this into the address bar and searches for the closest thing.
 Its very annoying.

Actually it's not a bug it's a feature. The way it seems to work is, highlight text and hit the middle button. The middle button is supposed to open stuff in new tab, since the highlighted text is not actually a link it just searches for it with "I'm Feeling Lucky" it would seem. I think it can be turned off in about:config or at least it's likely.

---

### Post by K.Mandla on 2006-10-05
> **prizrak said:**
> Actually it's not a bug it's a feature. The way it seems to work is, highlight text and hit the middle button. The middle button is supposed to open stuff in new tab, since the highlighted text is not actually a link it just searches for it with "I'm Feeling Lucky" it would seem. I think it can be turned off in about:config or at least it's likely.
Hmm. It's not doing it for me. Would that have anything to do with the desktop environment? I'm using Openbox, so there are a lot of things that don't quite work like they do for other folks. ... ;) 

Or wait, I'm using Tab Mix Plus too, and I might have disabled that feature. I'll check.

EDIT: Okay, I think that's what that was. I enabled the middle click options in Tab Mix Plus, and when I highlight text and middle-click, I'm taken directly to a somehow-related page. I kinda like that. I might keep it. :mrgreen:

---

### Post by rowanparker on 2006-10-05
> **K.Mandla said:**
> Hmm. It's not doing it for me. Would that have anything to do with the desktop environment? I'm using Openbox, so there are a lot of things that don't quite work like they do for other folks. ... ;) 

Or wait, I'm using Tab Mix Plus too, and I might have disabled that feature. I'll check.

EDIT: Okay, I think that's what that was. I enabled the middle click options in Tab Mix Plus, and when I highlight text and middle-click, I'm taken directly to a somehow-related page. I kinda like that. I might keep it. :mrgreen:

Yeah, I'm using that in FF, good find. Is their anyway to make it load in a new tab?

---

### Post by raublekick on 2006-10-05
i was just testing out this feature at school, highlighted the end part of the last post, and got taken to this:

[http://www.squarefree.com/extensions/thumbs/](http://www.squarefree.com/extensions/thumbs/)

buh hwah!?

---

### Post by prizrak on 2006-10-05
> **raublekick said:**
> i was just testing out this feature at school, highlighted the end part of the last post, and got taken to this:

[http://www.squarefree.com/extensions/thumbs/](http://www.squarefree.com/extensions/thumbs/)

buh hwah!?

ROFL, now that's a useful feature :)

---

### Post by slimdog360 on 2006-10-05
I think I'll come back to it when the bugs are ironed out. I cant log into deviantart also a few features like the drop down box in deviantart does not work. Not to mention the random webpage thing.

---

### Post by Parkotron on 2006-10-12
I've just noticed that IceWeasel doesn't want to render SVG, even though it's version 1.5.0.4, which should support SVG. It just tries to save any link to an SVG to disk. Is anyone else having this problem?

Because it was mentioned earlier, I thought I'd share the IceWeasel icon I recently whipped up. A few samples are attached below along with a tarball including all major sizes and the SVG source. The icon isn't great. It scales down poorly, makes poor use of the available space, and my vector graphics skills leave a lot to be desired. 

I like the concept of a weasel on a globe. I chose an [ermine]("http://en.wikipedia.org/wiki/Stoat"), because it's the most common weasel species in my area and it turns stark white in winter, which seems appropriate for the IceWeasel theme. I'm really not sure that the icicle-for-a-tail concept works all that well; it seemed like a good idea at first, but it didn't turn out as well as I hoped. Maybe if I could draw an icicle that doesn't look like a carrot with a blue gradient, it would work better.

Anyway, I'm posting my icon because:
#1 It's (slightly) better than nothing.
#2 I hope it'll inspired someone else to do better.

---

### Post by K.Mandla on 2006-10-12
Throw it into the wiki. The Debian managers might pick it!

[https://wiki.ubuntu.com/IceWeaselIcon](https://wiki.ubuntu.com/IceWeaselIcon)

And while you're at it, see if you can whip up one for IceDove and IceApe.

[https://wiki.ubuntu.com/IceDoveIcon](https://wiki.ubuntu.com/IceDoveIcon)
[https://wiki.ubuntu.com/IceApeIcon](https://wiki.ubuntu.com/IceApeIcon)

---

### Post by maniacmusician on 2006-10-12
@Parkotron: About the SVG, i get that with swiftfox as well (1.5.06). it doesnt open it, but wants to save it.

---

### Post by Parkotron on 2006-10-12
Oops. I've been away from the forums for a few days and I missed all the IceWeasel icon excitement. Obviously, my icon can't compete in drawing quality, but it is a different layout than the others, so I'll add it to the wiki just for kicks.

maniacmusician: Thanks for confirming. Maybe I'll try compiling it myself to see if SVG support is an option.

---

### Post by Somenoob on 2006-10-12
I hope Opera replaces Firefox.

---

### Post by Magnes on 2006-10-12
> **Somenoob said:**
> I hope Opera replaces Firefox.

It can't. It's closed commercial software.

---

### Post by chaosgeisterchen on 2006-10-12
IceWeasel is very likely to become the new standard browser.

Opera can be easily installed afterwards, but, as it was already said, it's closed source and fully against Ubuntu's ideals.

---

### Post by Kilz on 2006-10-12
> **maniacmusician said:**
> @Parkotron: About the SVG, i get that with swiftfox as well (1.5.06). it doesnt open it, but wants to save it.

But Swiftfox will never be able to replace Firefox in distro's. Its non free. It uses its own license that forbids redistribution.

---

### Post by mips on 2006-10-12
> **Parkotron said:**
> 
Because it was mentioned earlier, I thought I'd share the IceWeasel icon I recently whipped up. 

No offense but it looks like that weasel is humping the earth/globe :)

---

### Post by total wormage on 2006-10-12
> **mips said:**
> No offense but it looks like that weasel is humping the earth/globe :)
second :p

---

### Post by maniacmusician on 2006-10-12
> **Kilz said:**
> But Swiftfox will never be able to replace Firefox in distro's. Its non free. It uses its own license that forbids redistribution.
......?

I never said it was going to. He said he was having a problem with iceweasel, and I confirmed that it was the same in swiftfox (implying that the issue was in all firefox-based browsers, not just the new iceweasel)

---

### Post by Kilz on 2006-10-12
> **maniacmusician said:**
> ......?

I never said it was going to. He said he was having a problem with iceweasel, and I confirmed that it was the same in swiftfox (implying that the issue was in all firefox-based browsers, not just the new iceweasel)

ok, sorry if I didnt understand.

---

### Post by Naralas on 2006-10-12
> **rowanparker said:**
> I know the feeling.

School uses Internet Explorer ](*,)

USB Key with Firefox for the win ^_^

Cept my school found out and disabled Firefox from running period... if I wasnt only there for the rest of this semester I would try find a way around it.

---

### Post by Mr. Picklesworth on 2006-10-12
I would rather they used Epiphany in Ubuntu.
It is a nice browser, it's based on Mozilla, it's made for Gnome, and it's fast.
It has some neat tab stuff, too, where if I open a link in a new tab I can still hit the Back button from the new tab to return to the parent page.


In my opinion, IceWeasel is a bit daft. It's nice to see that they've proven how Mozilla did not need to hire anyone for artwork, though... except when it comes to the name.
Sure, take a jab at Firefox, but don't do it in a stupid way that will haunt you for the entire life of your software!
IceWeasel is a horrible name which sounds nothing like an approachable and friendly web browser. They do want to do this in order to *improve* something... right?

So, they need to fix it. Change the name and stop provoking bad relations. (By the way: May it be known that this is the first and last time I will ever directly mention any kind of Firefox vs. IceWeasel thing)

---

### Post by maniacmusician on 2006-10-12
> **Naralas said:**
> USB Key with Firefox for the win ^_^

Cept my school found out and disabled Firefox from running period... if I wasnt only there for the rest of this semester I would try find a way around it.
my school made the smart choice and switched to FF as a default, after i pestered the sysadmin about how insecure IE was and sent him about 20 articles on the subject.

---

### Post by rowanparker on 2006-10-13
> **Naralas said:**
> USB Key with Firefox for the win ^_^

Cept my school found out and disabled Firefox from running period... if I wasnt only there for the rest of this semester I would try find a way around it.

We are not allowed to open any .exe's. All you can run is a macro in MS word so if there is a FF plugin for that I could make FF, that's all I can think of.

> **maniacmusician said:**
> my school made the smart choice and switched to FF as a default, after i pestered the sysadmin about how insecure IE was and sent him about 20 articles on the subject.

I told my IT teacher to tell the admin, but it was some petty excuse like "One program needs IE", well why not let that program use IE and give us FF.

Although last lesson (friday), I found out that we have a debian box as a router, at least I think it was anyway.



Rowan.

---

### Post by total wormage on 2006-10-13
> **Mr. Picklesworth said:**
> 
...
In my opinion, IceWeasel is a bit daft. It's nice to see that they've proven how Mozilla did not need to hire anyone for artwork, though... except when it comes to the name.
Sure, take a jab at Firefox, but don't do it in a stupid way that will haunt you for the entire life of your software!
IceWeasel is a horrible name which sounds nothing like an approachable and friendly web browser. They do want to do this in order to *improve* something... right?

So, they need to fix it. Change the name and stop provoking bad relations. (By the way: May it be known that this is the first and last time I will ever directly mention any kind of Firefox vs. IceWeasel thing)

In my opinion the name "Firefox" isn't so friendly either when you hear it for the first time, the name "IceWeasel" isn't only a joke which will haunt the team till the end of time. I think the name has a character of it's own (and surely with this name the team isn't going through the whole 'Phoenix / FireBird' thing, with other compagnies already claiming the name ;]]])

---

### Post by chaosgeisterchen on 2006-10-13
> **rowanparker said:**
> We are not allowed to open any .exe's. All you can run is a macro in MS word so if there is a FF plugin for that I could make FF, that's all I can think of.



I told my IT teacher to tell the admin, but it was some petty excuse like "One program needs IE", well why not let that program use IE and give us FF.

Although last lesson (friday), I found out that we have a debian box as a router, at least I think it was anyway.



Rowan.

Fricking ignorance towards open source and change as a whole.

I cannot stand it.. I am very happy that we have quite open-minded staff members in our school. Even if we have no Linux-using staff members there was once an attempt to let everyone have access to Ubuntu by offering the *.iso on the school server.

But it seemed to have failed :(

---

### Post by rowanparker on 2006-10-13
> **chaosgeisterchen said:**
> Fricking ignorance towards open source and change as a whole.

I cannot stand it.. I am very happy that we have quite open-minded staff members in our school. Even if we have no Linux-using staff members there was once an attempt to let everyone have access to Ubuntu by offering the *.iso on the school server.

But it seemed to have failed :(

Unlucky :(

I'm going to try pursuade them to install gimp, as they cannot install photoshop due to the cost. Then I'll try FF again, I'm going to go this thru a teacher so it might work better.

---

### Post by K.Mandla on 2006-10-13
> **Naralas said:**
> Cept my school found out and disabled Firefox from running period... if I wasnt only there for the rest of this semester I would try find a way around it.
Have you tried any of these ideas?

[http://www.ericgiguere.com/articles/masquerading-your-browser.html](http://www.ericgiguere.com/articles/masquerading-your-browser.html)

Seems that if the system is only checking the browser's user-agent value, you might be able to delude them into thinking your using another one. :-? 

Just an idea.

---


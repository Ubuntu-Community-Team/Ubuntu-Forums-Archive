---
title: "Noscript browser plugin"
date: 2012-01-07
forum: Security
---

### Post by aeronutt on 2012-01-07
I'm using 'Noscript' plugin in Firefox and it seems to be a real PIA to use. Many web pages have numerous things noscript blocks...I find myself either taking a lot of time per page enabling scripts that I have no idea what they do, or worse, simply enabling everything on the page.

Seems there should be a pre configured white-list or such of 'probably safe' scripts that noscript would allow out of the box?

Am I missing something?

---

### Post by dirtrider1 on 2012-01-07
While I believe Noscript is a great plugin for security, I don't use it for everyday browsing. Noscript by default white lists a few mainstream sites that are known to be safe like gmail.com but they recommend that the user build there own customized lists and keep them as short as possible.

---

### Post by Ms. Daisy on 2012-01-07
I guess it's a matter of personal tolerance for risk.  For the protection that it gives me, it's worth it to have to click "options" and "allow whatever.com" for the sites I routinely visit.  And I really like that nothing is allowed when I visit a new, unknown site.  

When you first install NoScript, you will have to whitelist your regular sites.  But once they're whitelisted, it requires less interaction.  How many websites do you actually visit on a routine basis?  Whitelist those & you're done.

If you want 100% functionality out of every web page you visit every time, then you won't like NoScript.

---

### Post by aeronutt on 2012-01-07
Easy enough to build my own whitelist, but some sites I visit have 8 or more blocked scripts, of which I have no idea are good or bad or if they'll become bad. I guess whitelisting everything I visit, even though I don't know what i'm whitelisting, is better than wide open. 

For example, THIS page has 3 scripts, 2 of which how would I know to trust?

But...with that said, I'm not even sure what risk I'm managing by blocking these.

---

### Post by Ms. Daisy on 2012-01-07
The way I approach it is this: let's say I'm visiting SomeSite.com.  When I first visit it, the bar on the bottom tells me 

Scripts Currently Forbidden | <Script>: 7 | <Object>:0

I click on the options button and I can see a long list.  If it's a site I know I'll visit a lot, then I will choose "allow SomeSite.com".  That doesn't necessarily allow all the scripts on the site. But it added SomeSite.com to the whitelist permanently.   Then I'll see if I get the functionality I need from the website by allowing this script.  

If something is still broken on the website, then I will look at the options again and allow another one of the scripts.  For the most part, I allow the name of the website and I get what I need.  But there are a few sites that make heavy use of scripts and I had to "allow all this page" to get anything to work. 

Like I said, I really rely on NoScript for searching new sites.  I don't know what anyone else does with their browsers, but I research stuff all the time.  That means I'm visiting new unknown sites all the time.  I use NoScript to help protect me from these unknowns.  I only allow scripts on a site that I'm going to use all the time or that I trust.

---

### Post by 0011235813 on 2012-01-08
Web designers should realize that JS is a bad idea. Most people don't care for fancy menus, and JS is insecure and slows down your browsing. We don't want JS! What's wrong with plain HTML,CSS and WebM? Use direct links, not JS based menus. get rid of dangerous or inappropriate ads, and make them text only; no flashy menus and icons. Until then, we will have to deal with half-crippled web pages because we're forced to use extensions like NoScript (or have JavaScript disabled).

---

### Post by Telengard C64 on 2012-01-08
FWIW, I use Noscript similarly to the way Ms. Daisy described. Yes, some websites require a bit of experimentation to get them working, but it is worth it.

If you choose *Temporarily allow all this page*, you will find that some scripts still get blocked. This happens frequently because of third party scripts from ad networks which rotate in ads from different domains. Most of the sites I use work just fine without the third party scripts.

I would prefer to browse without any scripts at all, for security reasons. It just isn't realistic though, because the modern web is no longer a text only medium.

Just remember that every script you allow to run represents a potential security or privacy risk to your browser and its plugins.

---

### Post by CharlesA on 2012-01-08
> **0011235813 said:**
> Web designers should realize that JS is a bad idea. Most people don't care for fancy menus, and JS is insecure and slows down your browsing. We don't want JS! What's wrong with plain HTML,CSS and WebM? Use direct links, not JS based menus. get rid of dangerous or inappropriate ads, and make them text only; no flashy menus and icons. Until then, we will have to deal with half-crippled web pages because we're forced to use extensions like NoScript (or have JavaScript disabled).

Javascript is needed. Even this forum uses it.

> **Telengard C64 said:**
> FWIW, I use Noscript similarly to the way Ms. Daisy described. Yes, some websites require a bit of experimentation to get them working, but it is worth it.

If you choose *Temporarily allow all this page*, you will find that some scripts still get blocked. This happens frequently because of third party scripts from ad networks which rotate in ads from different domains. Most of the sites I use work just fine without the third party scripts.

I would prefer to browse without any scripts at all, for security reasons. It just isn't realistic though, because the modern web is no longer a text only medium.

Just remember that every script you allow to run represents a potential security or privacy risk to your browser and its plugins.

This. I use noscript the same way. I've had to use the temporarily allow scripts form (somesite) to see if the page will display right or not.

---

### Post by 0011235813 on 2012-01-09
> **CharlesA said:**
> Javascript is needed. Even this forum uses it.



This. I use noscript the same way. I've had to use the temporarily allow scripts form (somesite) to see if the page will display right or not.

I don't understand why JS is so important- What exactly is there that requires so much scripting? I would understand games, or websites like Facebook, and maybe certain types of other things- like on line malware scanners, but why is it **that** important? Wouldn't the Internet be a better place without insecure and slow scripts?

---

### Post by Telengard C64 on 2012-01-09
> **0011235813 said:**
> I don't understand why JS is so important- What exactly is there that requires so much scripting?

I'm guessing the pull-down-menus use JS, as one example. 

> Wouldn't the Internet be a better place without insecure and slow scripts?

Yes the web *would* be far more secure without scripts, but it would also be a text-only web. All the most popular sites rely on client-side-scripting techologies to enhance the user experience and provide content which would be impossible on a static-text-only page.

---

### Post by 0011235813 on 2012-01-09
> **Telengard C64 said:**
> I'm guessing the pull-down-menus use JS, as one example. 



Yes the web *would* be far more secure without scripts, but it would also be a text-only web. All the most popular sites rely on client-side-scripting techologies to enhance the user experience and provide content which would be impossible on a static-text-only page.

People don't care for fancy menus[/quote]. 
As I said previously- that's not a feature many users really care about that much.

Static only web-page? Really? What do you mean by that? Without JavaScript you can:

-Make a site with text.

-Make a site with images.

-Make a site with video and games (HTML5 and Flash)

-Make a site with CSS features

-Make a site which automatically redirects.

-Make a site that has HyperLinks in the navigation bar to allow interactivity.

Now mind you, I'm not saying there shouldn't be *any* JS at all: But JS is a function that is seriously over-rated, over-used and over-exploited (malware).

---

### Post by Ms. Daisy on 2012-01-09
Fibonacci, good luck in your mission to rewrite the web.

---

### Post by 0011235813 on 2012-01-09
> **Ms. Daisy said:**
> Fibonacci, good luck in your mission to rewrite the web.

I'm not trying to re-write the web, I'm trying to explain why JS isn't always such a good idea- why it's overuse has turned it into a nuisance rather than an asset.

---

### Post by flemur13013 on 2012-01-09
FWIW, I used NoScript for a while but ditched it because hassles; I've never had a problem with scripts except them getting "stuck" sometimes.

> **0011235813 said:**
>  Without JavaScript you can:
 ...


I'm an amateur at HTML, and, against my better judgement I used a script in a friend's many-paged website so all the pages would have the same header and footer, and any changes to the headers & footers would only have to be made in one place, because apparently (and amazingly, I think) there's no type of "#include" statement in HTML w/o using JS PHP or some such. Frames and other methods all had issues. 

Without JavaScript (etc) can you include an HTML file inside another HTML file?

---

### Post by 0011235813 on 2012-01-09
> **flemur13013 said:**
> FWIW, I used NoScript for a while but ditched it because hassles; I've never had a problem with scripts except them getting "stuck" sometimes.



I'm an amateur at HTML, and, against my better judgement I used a script in a friend's many-paged website so all the pages would have the same header and footer, and any changes to the headers & footers would only have to be made in one place, because apparently (and amazingly, I think) there's no type of "#include" statement in HTML w/o using JS PHP or some such. Frames and other methods all had issues. 

Without JavaScript (etc) can you include an HTML file inside another HTML file?
I'm afraid I can't say; I'm not really a web-designer. But have you tried using a program like LibreOffice or Google Docs etc. To write the headers& footers in, and then embedding it in an image?

---

### Post by Telengard C64 on 2012-01-09
0011235813, I think I can relate to what you are trying to get across, but you are 15 years too late.

Javascript was created in 1995 by Netscape, and was thus inherited by Mozilla and Firefox. We wanted interactive web content then, and it would be quite a long time until HTML 5 and CSS were available to provide it.

---

### Post by CharlesA on 2012-01-09
> **0011235813 said:**
> I'm afraid I can't say; I'm not really a web-designer. But have you tried using a program like LibreOffice or Google Docs etc. To write the headers& footers in, and then embedding it in an image?

That is a nasty way to do it. You can just use server-side includes (SSI) with HTML or use include statements with PHP (which has nothing to do with Javascript).

[http://www.mediatitan.com/articles/php_server_side_includes.php](http://www.mediatitan.com/articles/php_server_side_includes.php)
[http://webmaster.iu.edu/tool_guide_info/ssi.shtml](http://webmaster.iu.edu/tool_guide_info/ssi.shtml)

---

### Post by 0011235813 on 2012-01-10
> **CharlesA said:**
> That is a nasty way to do it. You can just use server-side includes (SSI) with HTML or use include statements with PHP (which has nothing to do with Javascript).

[http://www.mediatitan.com/articles/php_server_side_includes.php](http://www.mediatitan.com/articles/php_server_side_includes.php)
[http://webmaster.iu.edu/tool_guide_info/ssi.shtml](http://webmaster.iu.edu/tool_guide_info/ssi.shtml)

Probably, but I **did** say I wasn't a web designer. I just said the first thing I could think off.

---

### Post by 0011235813 on 2012-01-10
> **Telengard C64 said:**
> 0011235813, I think I can relate to what you are trying to get across, but you are 15 years too late.

Javascript was created in 1995 by Netscape, and was thus inherited by Mozilla and Firefox. We wanted interactive web content then, and it would be quite a long time until HTML 5 and CSS were available to provide it.

Pity, I am frequently annoyed by JavaScript: But honestly, that was 15 years ago. Would it really be so hard to start making sites without JavaScript?

---

### Post by CharlesA on 2012-01-10
> **0011235813 said:**
> Probably, but I **did** say I wasn't a web designer. I just said the first thing I could think off.

I was just pointing that out. If you put them as an image, it would need more bandwidth than text and would need to be recreated if you wanted to change something.

> **0011235813 said:**
> Pity, I am frequently annoyed by JavaScript: But honestly, that was 15 years ago. Would it really be so hard to start making sites without JavaScript?

It's not that it is "hard" persay, but there are a ton of great javascript libraries, such as jQuery, that make it easier to do things.

My site doesn't use Javascript, but I've tried to use it before to get some of the scripts I have put up there to look "pretty," which didn't turn out well. :p

---

### Post by movieman on 2012-01-10
> **0011235813 said:**
> Would it really be so hard to start making sites without JavaScript?

Good God, man. Think of all the web developers who would be out of work...

Personally I find most sites work OK without Javascript and I only enable it for the few I visit often which don't. Another benefit of NoScript is that when I go to my bank and see the NoScript 'OK' icon I can be pretty sure I haven't been redirected to a phishing site because everything on that page is going to a site I've whitelisted.

But yeah, I generally agree: Javascript is used for far too many things where plain old HTML would be just as good. Allowing people to execute random code in your web browser was a bad idea when it was invented and it's still a bad idea now.

---


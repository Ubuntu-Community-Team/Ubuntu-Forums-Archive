---
title: "Zero-day flaw in Firefox"
date: 2006-10-01
forum: The Cafe
---

### Post by greggh on 2006-10-01
[http://news.com.com/Hackers+claim+zero-day+flaw+in+Firefox/2100-1002_3-6121608.html?tag=nefd.top](http://news.com.com/Hackers+claim+zero-day+flaw+in+Firefox/2100-1002_3-6121608.html?tag=nefd.top)

> An attacker could commandeer a computer running the browser simply by crafting a Web page that contains some malicious JavaScript code, Mischa Spiegelmock and Andrew Wbeelsoi said in a presentation at the ToorCon hacker conference here. The flaw affects Firefox on Windows, Apple Computer's Mac OS X and Linux, they said.

"Internet Explorer, everybody knows, is not very secure. But Firefox is also fairly insecure," said Spiegelmock, who in everyday life works at blog company SixApart. He detailed the flaw, showing a slide that displayed key parts of the attack code needed to exploit it.

The flaw is specific to Firefox's implementation of JavaScript, a 10-year old scripting language widely used on the Web. In particular, various programming tricks can cause a stack overflow error, Spiegelmock said. The implementation is a "complete mess," he said. "It is impossible to patch."

---

### Post by whynotchevron on 2006-10-01
I have NoScript extension installed on my computers 
[https://addons.mozilla.org/firefox/722/]("https://addons.mozilla.org/firefox/722/")
hopefully a good stop-gap measure .:-k

---

### Post by %hMa@?b&lt;C on 2006-10-01
*installs no-script*
am i safe?

---

### Post by greggh on 2006-10-01
I just installed no-script too. If this really turns out to be a flaw affecting the entire implimentation of the JVM in Firefox its going to be very damaging to Firefox and Mozilla.

---

### Post by Kateikyoushi on 2006-10-01
*removes wireless card*
Am I safe ? ^^;

After the comment that it's impossible to patch I am really curious how will they solve it, hopefully they come up with a surprising solution.

---

### Post by ~LoKe on 2006-10-01
And they released this information, why? o_O

---

### Post by slimdog360 on 2006-10-01
*uses konqueror as he always does*
am i safe?

---

### Post by Fass on 2006-10-01
> **~LoKe said:**
> And they released this information, why? o_O

Attention whoring coupled with a paradoxical self-delusion that they want to do what's "good for the Internet," only to later hold on to other bugs for their own purposes, which of course only strengthens the attention whoring aspect of it all.

---

### Post by skymt on 2006-10-01
> **~LoKe said:**
> And they released this information, why? o_O

Because the (cr|h)ackers already know it.

---

### Post by fuscia on 2006-10-01
as part of my conversion to kde nuthuggery, i am safely swinging from the glowing chobes of konqueror. am i really safe? i *do* keep my best secrets in my head (call me 'old school').

---

### Post by Polygon on 2006-10-01
horray for no script! 

basically if you have no script, a page cant run javascript unless you specifically allow it to, ie sites you know are good (like the forums).

---

### Post by mips on 2006-10-01
> **fuscia said:**
> as part of my conversion to kde nuthuggery, i am safely swinging from the glowing chobes of konqueror. am i really safe? i *do* keep my best secrets in my head (call me 'old school').

Don't you miss the firefox extensions ??? That's probably the only reason I use swiftfox and I must say it feels faster than konq.

---

### Post by Lord Illidan on 2006-10-01
Idiot hackers...they are shaming all the real hackers out there...why would they benefit the internet by not working with Mozilla????

---

### Post by henriquemaia on 2006-10-01
> **Polygon said:**
> horray for no script! 

basically if you have no script, a page cant run javascript unless you specifically allow it to, ie sites you know are good (like the forums).

Thanks for the tip. Already using it.

---

### Post by BWF89 on 2006-10-01
> **~LoKe said:**
> And they released this information, why? o_O
One of the reasons why so many people like open source is because instead of hiding a problem or simpily saying there is no problem like the proprietary software companies do we openly publish them so that programmers can try to fix them.

---

### Post by greggh on 2006-10-01
> **BWF89 said:**
> One of the reasons why so many people like open source is because instead of hiding a problem or simpily saying there is no problem like the proprietary software companies do we openly publish them so that programmers can try to fix them.

Yup, but the hackers say that they are keeping a whole bunch of other firefox exploits to themselves so they can use them for botnets.

---

### Post by Cap'n Refsmmat on 2006-10-01
> **greggh said:**
> Yup, but the hackers say that they are keeping a whole bunch of other firefox exploits to themselves so they can use them for botnets.
Or so they claim. In any case, as soon as the exploits begin to spread, someone smarter will catch them and patch them.

---

### Post by BWF89 on 2006-10-01
If the hackers were as smart as the patchers they'd be working to fix problems instead of creating them. Although there are some people that take joy in destorying things.

---

### Post by richbarna on 2006-10-01
> **Lord Illidan said:**
> Idiot hackers...they are shaming all the real hackers out there...why would they benefit the internet by not working with Mozilla????

They aren't hackers, just idiots. Just as a man with a gun isn't a murderer, and a man with a beer isn't an alcoholic. There are plenty of fools in the world. You're right, this benefits nobody.

---

### Post by 13east on 2006-10-01
freakin morons with a computer, hackers can't find anythin productive to do with their lives so they set out to ruin others'. i'm installing noscript onto swiftfox right now. thx for the info.

---

### Post by siimo on 2006-10-01
HAHA! (nelson)

Owned.

---

### Post by greggh on 2006-10-01
> **siimo said:**
> HAHA! (nelson)

Owned.

I bet that Firefox with this flaw used with noscript extension is still a hell of alot safer than Internet Exploder.

---

### Post by fuscia on 2006-10-01
> **mips said:**
> Don't you miss the firefox extensions ??? That's probably the only reason I use swiftfox and I must say it feels faster than konq.

not really. i don't use many firefox extensions, anyway. but, as i change my mind about every five minutes, it's hard for me to say this is permanent.

---

### Post by aysiu on 2006-10-01
I've had NoScript installed for quite some time because almost all of the Firefox vulnerabilities that come out usually have something to do with Javascript.

---

### Post by skymt on 2006-10-01
> **greggh said:**
> I bet that Firefox with this flaw used with noscript extension is still a hell of alot safer than Internet Exploder.

Not really. Internet Explorer has security zones, which provide NoScript functionality built right into the browser. If you lock down Javascript and ActiveX on untrusted sites, it's as safe as Firefox. Safer, in fact, since (as I recall) it can block objects, like Flash and Java applets. That way, you don't have to worry about those as exploit vectors.

---

### Post by aysiu on 2006-10-01
What are you talking about?

There's no easy way to turn off Javascript and ActiveX globally and then one-by-one whitelist sites in Internet Explorer. You actually have to go into the options > security > untrusted sites and manually add each untrusted address.

And NoScript can block Flash and Java.

I believe you don't know what you're talking about.

---

### Post by Bloodfen Razormaw on 2006-10-01
He knows exactly what he is talking about.  He did reference zones, after all.  He is referring to the use of Trusted Sites and Restricted Sites zones to use that switching.  So yes, IE can handle site-specific Javascript, but it is not Javascript-specific.  Every trusted site must have the same settings for Javascript, Active X, Java, etc.  So IE does it, but in a poor way.

However, Noscript does look rather bad compared to Konqueror's built in Javascript controls.  It lets you not just turn Javascript on/off, but you can control what functions are allowed for each domain.

---

### Post by aysiu on 2006-10-01
I'm also talking about Trusted and Restricted Sites (see the attached screenshot in my last post), and that's not as secure as NoScript--sorry.

You're assuming either that Internet Explorer is perfect at detecting which sites are trusted or not trusted or that IE users are really going to click three items deep and manually type in a web address in order to blacklist it *before* they visit the page.

With NoScript, the default is that *everything* is blacklisted, and you whitelist only as you see fit... with one click.

Where's the one-click whitelisting on Konqueror? It's not in the right-click (context menu) for websites. As far as I can tell, you also cannot blanket blacklist and then whitelist as you see appropriate. You have to one by one (just as with Internet Explorer), type in the web addresses of sites you want specific actions for.

So let's say you navigate to a rather sketchy site by accident:

1. In Internet Explorer, you pray that it's detected as a restricted site or... before clicking the link to it, you go to Tools > Internet Options > Security > Restricted Sites > Sites, type the address of the site and then click Add.

2. In Konqueror, you also pray that it's detected with Konqueror's "smart" settings to be untrustworthy, or... before clicking the link to it, you go to Settings > Configure Konqueror > Java & Javascript > New, type the name of the domain, click Reject, click Javascript, click New, select all the options for that site, then click OK.

3. In Firefox with NoScript, you just visit the site. It's already blacklisted. If you want to whitelist it, you click on the NoScript icon on the status bar and say "allow somesite.com" or "temporarily allow somesite.com."

Which do you think is safer? 

A) The browsers that try to determine which sites are safe (any algorithm must be flawed) and force you to click at least four times and then manually type an address in order to blacklist a site.

B) The browser that automatically determines all sites to be unsafe until you manually approve (with one click) the site.

---

### Post by skymt on 2006-10-02
Internet Explorer has another zone in addition to Trusted and Untrusted. It's called the Internet zone. If you disable Javascript in the Internet zone, you can whitelist (add to the Trusted zone) the sites you want, and it blocks Javascript for everything else. Check out the first screenshot. It also has a zone for local sites, so you can automatically whitelist anything on, say, a corporate LAN.

IE also allows for more fine-grained security control. When you click Custom Level, you can choose from a long list of security options, controlling stuff like cookies and semi-obscure HTML tags. See the second screenshot.

You say NoScript lets you whitelist a site with one click. It's actually two (one to bring up the menu, a second to choose to allow the site), but that's nit-picking. It really is more convenient to use NoScript, and that's a security problem. I've tried to get my family to use NoScript, but they always either "Allow scripts Globally" or allow each site they go to, rendering it worthless. In IE it's more trouble, but it's also less likely a user will whitelist a bad site.

Oh, and you don't have to manually type the address. Even Windows has copy-and-paste.

---

### Post by slimdog360 on 2006-10-02
firefox cant do the Active X thing, make that, the dev's choose not to let firefox do the active x thing.

---

### Post by skymt on 2006-10-02
> **slimdog360 said:**
> firefox cant do the Active X thing, make that, the dev's choose not to let firefox do the active x thing.

Yes. So? It supports Javascript, which has plenty of security holes by itself.

IE lets you whitelist ActiveX, which is just as secure, but (obviously) more powerful.

---

### Post by slimdog360 on 2006-10-02
from the experts

[IE]("http://secunia.com/product/11/")
"Microsoft Internet Explorer 6.x, with all vendor patches applied, is rated Extremely critical"


[firefox]("http://secunia.com/product/4227/")
"Mozilla Firefox 1.x, with all vendor patches applied, is rated Less critical"

---

### Post by aysiu on 2006-10-02
> **skymt said:**
> Yes. So? It supports Javascript, which has plenty of security holes by itself.

IE lets you whitelist ActiveX, which is just as secure, but (obviously) more powerful. And, as I showed in previous posts, whitelisting or blacklisting in Internet Explorer is too much of an inconvenience to be useful or considered a viable security measure.

Whitelisting and blacklisting of sites has to be a one-click option--otherwise most people (even power users) aren't going to use that functionality. Anything that involves four clicks and the manual typing in of web addresses will be used by only the super paranoid who are dedicated to a particular browser.

---

### Post by skymt on 2006-10-02
> **aysiu said:**
> And, as I showed in previous posts, whitelisting or blacklisting in Internet Explorer is too much of an inconvenience to be useful or considered a viable security measure.

Whitelisting and blacklisting of sites has to be a one-click option--otherwise most people (even power users) aren't going to use that functionality. Anything that involves four clicks and the manual typing in of web addresses will be used by only the super paranoid who are dedicated to a particular browser.

Did you read my previous post (#29 on page 3)?

---

### Post by EdThaSlayer on 2006-10-02
So i see that firefox's biggest threat is javascript...which they say is quite a buggy but very useful mark up language...

So all i will have to install is No-script(which i...btw...have already installed...)
then that vulnurability is gone...

hey...at least they told us about that weakness...we computer savie users are on alert now...

---

### Post by skymt on 2006-10-02
> **slimdog360 said:**
> from the experts

[IE]("http://secunia.com/product/11/")
"Microsoft Internet Explorer 6.x, with all vendor patches applied, is rated Extremely critical"


[firefox]("http://secunia.com/product/4227/")
"Mozilla Firefox 1.x, with all vendor patches applied, is rated Less critical"

[IMG]http://secunia.com/graph/?type=sol&period=2006&prod=4227[/IMG]
[IMG]http://secunia.com/graph/?type=sol&period=2006&prod=10615[/IMG]

;)

I use Opera. ;) 

I'm not saying IE is the most secure browser on the planet. I'm saying it has more security control than Firefox (even with NoScript), and by using that control, you can make it more secure than Firefox.

---

### Post by slimdog360 on 2006-10-02
> **skymt said:**
> Did you read my previous post (#29 on page 3)?
people who use IE, dont muck around with anything, dont use trusted zones, dont enable/disable activex or java script. Hence if they were to use firefox and intentionally download noscript they would be more likely to use it properly. Making it safer. making firefox the safer choice.

---

### Post by aysiu on 2006-10-02
> **skymt said:**
> [IMG]http://secunia.com/graph/?type=sol&period=2006&prod=4227[/IMG]
[IMG]http://secunia.com/graph/?type=sol&period=2006&prod=10615[/IMG]

I use Opera. ;) 

I'm not saying IE is the most secure browser on the planet. I'm saying it has more security control than Firefox (even with NoScript), and by using that control, you can make it more secure than Firefox.
And I'm disagreeing with you. How does it offer you *more* security control than Firefox?

Control means nothing if it's inconvenient. I'm not going to go through five or six steps *before* visiting a questionable site in order to blacklist it.

---

### Post by aysiu on 2006-10-02
> **skymt said:**
> Did you read my previous post (#29 on page 3)?
Sorry, I hadn't.

But I believe anyone who would enable JavaScript globally or whitelist *every* site she visits is highly unlikely to take five or six extra steps to whitelist or blacklist sites in Internet Explorer.

Basically, I would break it down into these three major groups:

1. Users who just don't care. Convenience is the only thing that matters. If security happens too, they're happy.

2. Users who care about security but also want it to be convenient.

3. Users for whom security is the top priority who want to know *everything* that's going on, and convenience matters very little.

So what I'm saying is that group #1... doesn't matter what browser they use. They will always be operating insecurely--one click, two clicks, five clicks... they won't care. Anything that impedes their browsing isn't worth doing even if it makes them secure.

Group #2 would be ideal for NoScript but would consider the "control" that IE and Konqueror give them unnecessary (why blacklist only *parts* of a potentially untrustworthy site?) and also inconvenient--requiring too many clicks and too much typing.

Group #3 has very few people in it, and this group seems to be the group you're talking about. The likelihood that anyone in this group would be still using Internet Explorer--very low. Maybe they'd use Konqueror. Maybe.

By the way, if you want to talk about control--Firefox offers cookie management that has a lot more control than IE and Opera (not Konqueror, though).

---

### Post by Colonel Kilkenny on 2006-10-02
> **aysiu said:**
> By the way, if you want to talk about control--Firefox offers cookie management that has a lot more control than IE and Opera (not Konqueror, though).

Just out of curiosity. Can you show an example how Firefox cookie management is better than Operas? I really don't know cause I don't use Firefox that much..

---

### Post by skymt on 2006-10-02
> **aysiu said:**
> But I believe anyone who would enable JavaScript globally or whitelist *every* site she visits is highly unlikely to take five or six extra steps to whitelist or blacklist sites in Internet Explorer.

This could be resolved with a simple add-on. The tools are already there in IE, so it would be easy to write an IE toolbar to make it as easy as NoScript. There might even be something like this, I don't know.

> **aysiu said:**
> Basically, I would break it down into these three major groups:

1. Users who just don't care. Convenience is the only thing that matters. If security happens too, they're happy.

This group can't be helped. They will get spyware no matter what.

> **aysiu said:**
> 2. Users who care about security but also want it to be convenient.

This group has been told that Firefox is the most secure browser, so they use it.

> **aysiu said:**
> 3. Users for whom security is the top priority who want to know *everything* that's going on, and convenience matters very little.

This group realizes that there is very little making Firefox more secure than IE, so they use whichever they prefer. That may, in fact, be Internet Explorer. This group also probably has the programming chops to make it easier for themselves, by making a toolbar as I described.

> **aysiu said:**
> So what I'm saying is that group #1... doesn't matter what browser they use. They will always be operating insecurely--one click, two clicks, five clicks... they won't care. Anything that impedes their browsing isn't worth doing even if it makes them secure.

Yes.

> **aysiu said:**
> Group #2 would be ideal for NoScript but would consider the "control" that IE and Konqueror give them unnecessary (why blacklist only *parts* of a potentially untrustworthy site?) and also inconvenient--requiring too many clicks and too much typing.

I blacklist parts of sites all the time. If I would like to use a site that uses Javascript, but don't want advertisers to track me, I'll use Opera Site Preferences to lock down certain features and open others. I only have to do it once for each site, and the defaults I set are usually fine.

> **aysiu said:**
> Group #3 has very few people in it, and this group seems to be the group you're talking about. The likelihood that anyone in this group would be still using Internet Explorer--very low. Maybe they'd use Konqueror. Maybe.

This group might still use IE, for [control like this](http://www.nwnetworks.com/iezones.htm). Or, they might use it because their company requires it.

> **aysiu said:**
> By the way, if you want to talk about control--Firefox offers cookie management that has a lot more control than IE and Opera (not Konqueror, though).

Have you used Opera 9? Site Preferences is the best feature ever, in any browser. It's better than the back button. ;) 

The post I was replying to originally said IE was less secure than Firefox with NoScript. I think I've shown that to be false, *if* you use the tools Microsoft provided.

---

### Post by aysiu on 2006-10-02
You're not talking about tools Microsoft has provided. You're talking about tools that someone *could* write as an add-on.

You can't compare potential software to existing software.

And that still doesn't address group #2 that doesn't want to do all those clicks to get more control. NoScript will take care of any JavaScript vulnerabilities. I don't see why you need greater control than blacklisting an entire fishy (or phishy) site.

---

### Post by skymt on 2006-10-02
Also, I haven't used IE 7. From what I've seen on the web, it looks like it has a lot of new security features, so it wouldn't surprise me if it fixes the zones convenience problem.

---

### Post by aysiu on 2006-10-02
I'm not saying IE doesn't have the potential to be practically secure in the future.

I'm saying that right now, for practical purposes for group #2, Firefox offers the best balance of convenience and security.

You make a security measure too inconvenient to the point of being practically unusable, it's not really secure any more.

Speaking for myself personally and not for any hypothetical group (though I do belong to group #2), I would rather have two PCs--one for internet use and one for everything else--than have to go through all the hoops of trying to whitelist/blacklist with Internet Explorer 6's current functionality (not what IE7 *might* have or some add-on someone *could* create).

---

### Post by skymt on 2006-10-02
> **aysiu said:**
> You're not talking about tools Microsoft has provided. You're talking about tools that someone *could* write as an add-on.

Microsoft provides the tools, they're just harder to use than they could be. A quick Google discovered that Microsoft actually provided an add-on that added zone toolbar buttons. However, it was [only for IE 5](http://www.microsoft.com/windows/ie/ie6/previous/webaccess/pwrtwks.mspx). I also found various third-party utilities that support IE 6. So the software does exist.

I also found an MSDN tutorial on adding toolbar buttons to IE, and it looks pretty easy. I could write and debug a zones button like I described over a weekend. In fact, I might do that.

> **aysiu said:**
> And that still doesn't address group #2 that doesn't want to do all those clicks to get more control. NoScript will take care of any JavaScript vulnerabilities. I don't see why you need greater control than blacklisting an entire fishy (or phishy) site.

Actually, I did. That group won't use IE anyway.

---

### Post by skymt on 2006-10-02
> **aysiu said:**
> I'm not saying IE doesn't have the potential to be practically secure in the future.

I'm saying that right now, for practical purposes for group #2, Firefox offers the best balance of convenience and security.

You make a security measure too inconvenient to the point of being practically unusable, it's not really secure any more.

Speaking for myself personally and not for any hypothetical group (though I do belong to group #2), I would rather have two PCs--one for internet use and one for everything else--than have to go through all the hoops of trying to whitelist/blacklist with Internet Explorer 6's current functionality (not what IE7 *might* have or some add-on someone *could* create).

As I said, group #2 has generally been convinced of the superiority of Firefox, and are therefore out of the equation when it comes to IE security.

Oh, and a lot of people really use your 2 PC solution, just with VMWare.

---

### Post by aysiu on 2006-10-02
[quote=skymt]As I said, group #2 has generally been convinced of the superiority of Firefox, and are therefore out of the equation when it comes to IE security.[/quote]And what I'm saying is that group #2 has the functionality to make Firefox secure easily, so it's not just about "being convinced of the superiority" of Firefox. 

Firefox actually offers them security measures that are solid against JavaScript-based vulnerabilities, and it suits their lifestyle (the balance of convenience and security).

> Oh, and a lot of people really use your 2 PC solution, just with VMWare. I know, and I don't really use that solution. I'm just saying I'd *rather* do that than use Internet Explorer's current security solutions, which are too inconvenient to implement properly, or--as you put it--"Microsoft provides the tools, they're just harder to use than they could be."

---

### Post by skymt on 2006-10-02
[Here's a toolbar button for IE](www.geeksuperhero.com/zones.shtml) that works a lot like NoScript. I'll bet there are a lot more, but I don't want to waste my time looking.

---

### Post by aysiu on 2006-10-02
Excellent! Then people who use Internet Explorer *can* be secure and have convenience--it's simply a matter of education and some good Google skills.

I would like, however, every time someone talks about IE being effectually secure that they mention that add-on. Otherwise, it would be like arguing Firefox is secure without mentioning NoScript.

---

### Post by Not the man I once was on 2006-10-02
Greetings,

I'd like to have my say on this matter if I may. For a year past before defecting to Ubuntu GNU/Linux, I had an almighty and deepening facisnation with Security matters within Windows and, such as the situation is with the Operating System itself, there was always interesting articles and White Papers from Security Solution Vendors such as McAfee and Symantec convering topics from SPAM and Viruses, to Exploits and Botnets but I'd like to warn everyone about a few matters they may not have realised apply.

The flaws were made public at a Convention, thereby allowing Mozilla the opportunity to analyse the threat faced by the Mozilla Firefox Browser. The fact is that, although Mozilla Firefox has a large section of its work associated with JavaScript, it is the language that is at fault and not the implementation with the Browser itself. This is a Universal issue, not simply an issue with Mozilla Firefox.

Secondly, as the flaws were made public, the US Goverment can intervene on the issue that the purpetrators of the Exploit are witholding information that could potetionally affect the Goverments Security - They use Mozilla Firefox. 
This may sound odd but there was a situation in which Microsoft Windows XP's Disk Defragmenter prompted a Security inquiry by a Goverment some years ago therefore this is a viable concern, Mozilla offer bounties for flaws discovered within their Firefox Browser and as it stands, the people who discovered these issues stand to make in the region of $15,000 in the process if their flaws are valid.

Finally don't allow yourselves to be drawn into the pie charts above, remember that mathematics and numbering can be manipulated to show anything  a Company or a person pleases, positive or negative and as such the Secunia reports aren't fully valid in that respect as each person simply takes the information they wish to believe is correct.

My advice is to await an advisory on the issues via Mozilla and to implement the mitigation techniques they suggest, I've read of many people relying on Novell's AppArmour to protect them from these issues but if I'm quite honest, they are relying on software and all software has bugs and issues in itself therefore again, the above point is invalid.

Use common sense and Practicse Safe Hex and the majority of users are expected to be unaffected by these issues. Support Mozilla into resolving these issues and we will only show strength against those who seek to sow fear, uncertainty and deceit.

Regards,

Not the man I once was

---

### Post by skymt on 2006-10-02
> **Not the man I once was said:**
> Finally don't allow yourselves to be drawn into the pie charts above, remember that mathematics and numbering can be manipulated to show anything  a Company or a person pleases, positive or negative and as such the Secunia reports aren't fully valid in that respect as each person simply takes the information they wish to believe is correct.

I posted those charts as a kind of joke. Anyone reading those charts should be able to see that there is only one unpatched vulnerability in Firefox, compared to zero in Opera. With a workaround, such as NoScript, that vulnerability is avoided. The joke is in my use of deceptive charts (10% more vulnerability looks like a lot more than one easily avoided vulnerability) to defend my choice of browser. Many people use worse defenses for their choices. It was funny to me, anyway!

Maybe I should have put a smiley in, as a kind of "joke tag". I'll go do that!

EDIT: Oh wait, I did. I guess you just don't know what ;) means.

---

### Post by GStubbs43 on 2006-10-02
> **skymt said:**
> 
EDIT: Oh wait, I did. I guess you just don't know what ;) means.

It looks like you're just saying that Opera is more secure and that other people should use it. You should put the smiley after the graphs, not "I use Opera." ;)

---

### Post by aysiu on 2006-10-02
I think, as the discussion between me and skymt illustrates, it's not so much that any particular *browser* is inherently more or less secure than another browser.

A lot has to do with the user--the user's practices, research on plugins and add-ons and general awareness of security issues.

---

### Post by Brunellus on 2006-10-02
> **GStubbs43 said:**
> It looks like you're just saying that Opera is more secure and that other people should use it. You should put the smiley after the graphs, not "I use Opera." ;)
...and thus we see yet another hazard of using smilies as punctuation.

---

### Post by skymt on 2006-10-02
> **GStubbs43 said:**
> It looks like you're just saying that Opera is more secure and that other people should use it. You should put the smiley after the graphs, not "I use Opera." ;)

Fixed. ;)

---

### Post by GStubbs43 on 2006-10-02
That's better. :)

---

### Post by ago on 2006-10-02
> **skymt said:**
> [IMG]http://secunia.com/graph/?type=sol&period=2006&prod=4227[/IMG]
[IMG]http://secunia.com/graph/?type=sol&period=2006&prod=10615[/IMG]

;)

I use Opera. ;) 

I'm not saying IE is the most secure browser on the planet. I'm saying it has more security control than Firefox (even with NoScript), and by using that control, you can make it more secure than Firefox.

This chart is absolutely meaningless. It tells that FF patched 9 bugs out of 10 and Opera 1 out of 1. Neither can you compare the number of bugs (since Opera is closed source), nor the bug fixing rate (since 1 ~ 9/10, one is too small of a sample)...

---

### Post by skymt on 2006-10-02
> **ago said:**
> This chart is absolutely meaningless. It tells that FF patched 9 bugs out of 10 and Opera 1 out of 1. Neither can you compare the number of bugs (since Opera is closed source), nor the bug fixing rate (since 1 ~ 9/10, one is too small of a sample)...

...

[quote=me]I posted those charts as a kind of joke. Anyone reading those charts should be able to see that there is only one unpatched vulnerability in Firefox, compared to zero in Opera. With a workaround, such as NoScript, that vulnerability is avoided. The joke is in my use of deceptive charts (10% more vulnerability looks like a lot more than one easily avoided vulnerability) to defend my choice of browser. Many people use worse defenses for their choices. It was funny to me, anyway![/quote]

---

### Post by airtonix on 2006-10-02
And so even if i was stupid enough to actually use IE on windows, I would deserve all the grief that came through that dark portal.

If I was concerned about security....I'd be using linux....oh wait I am.:eek:

And so then if i was using linux, why the *&^% would i use wineIE(5,5.5,6)..:-k..on anything other my private [http://localhost](http://localhost) with code that I created.

---

### Post by ice60 on 2006-10-02
> **aysiu said:**
> What are you talking about?

There's no easy way to turn off Javascript and ActiveX globally and then one-by-one whitelist sites in Internet Explorer. You actually have to go into the options > security > untrusted sites and manually add each untrusted address.

And NoScript can block Flash and Java.

hi, you can just click the icon in the bottom bar to open the zones, also, i think you can just push the internet zone bar up to high to disable scripting, i can't remember though. if not you only have to 'harden' the settings once in the advanced tab.

there's a registry value which lets you add as many zones as you like which would give more control with zones i suppose, add a higher number here vv
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\WindowsUpdate

i like opera best. Secunia absolutely know what they are talking about with that graph.

there was a javascript flaw which only worked if your router had the default password, is this what the thread is about?

---

### Post by aysiu on 2006-10-02
[quote=ice60]hi, you can just click the icon in the bottom bar to open the zones, also, i think you can just push the internet zone bar up to high to disable scripting, i can't remember though. if not you only have to 'harden' the settings once in the advanced tab.
[/quote] I see no such icon. When I click on those two icons on the status bar (right-click, left-click, whatever), nothing happens.

---

### Post by ice60 on 2006-10-02
> **aysiu said:**
> I see no such icon. When I click on those two icons on the status bar (right-click, left-click, whatever), nothing happens.

well, it's that world icon (double-click). maybe it has to be showing the red icon for it to work, but i doubt it. it must just be in windows then.

---

### Post by aysiu on 2006-10-02
> **ice60 said:**
> well, it's that world icon (double-click). maybe it has to be showing the red icon for it to work, but i doubt it. it must just be in windows then.
I'll try it the next time I'm in Windows.

---

### Post by Bloodfen Razormaw on 2006-10-02
> i like opera best. Secunia absolutely know what they are talking about with that graph.
Secunia does, but you might not.  Opera 9.x has one flaw in 3 months, Firefox 1.x has 10 flaws in 11 months.  Opera is and has historically been more secure, but not by as huge a margin as that graph makes it look.  There is a reason Secunia says not to use those graphs as a comparison of security.

> **aysiu said:**
> I see no such icon. When I click on those two icons on the status bar (right-click, left-click, whatever), nothing happens.
Where it says Internet double clicking should open the window.  Works for me.

---

### Post by ice60 on 2006-10-02
> **Bloodfen Razormaw said:**
> Secunia does, but you might not.
what's that suppose to mean? 

maybe i don't know what i'm talking about lol but i spend most of my time talking to people who do, so i suppose the gist of things rub off.

---

### Post by blastus on 2006-10-02
I don't care what the "experts" say about Internet Explorer, Outlook and ActiveX now. In the past, these products/technologies have had a large number of spectacular security holes. For years security has just been an afterthought to Microsoft and this has cost users billions of dollars.

I made the decision back in 2001/2002 to quit using IE and Outlook Express when I noticed that, just by selecting certain spam emails in the view panel in Outlook Express, several Internet Explorer windows would popup and goto various websites. There wasn't a damn thing I could do to stop the windows from popping up so I made sure I never selected or viewed emails while connected to the Internet. Not long after that I heard about an email circulating that, just by selecting it in Outlook Express, would search your hard drive for certain types of files and mass email them out to everyone in your address book. Nice.

However, the final nail was driven into the coffin when I heard about ActiveX dialers. Just by visiting a website in IE, the dialer would install and execute. I managed to get one on my machine but fortunately for me it didn't work. I only found out about it when I ran Spybot several months later. My telephone company even sent out a warning about these long distance ActiveX dialers and that they were blocking calls to certain countries because of it and that they would not compensate users a single dime on their phone bill because it. They recommended people disable ActiveX in IE and unplug their telephone cord from their computer when not connected to the Internet. 

Unlike other types of security threats, this one had the potential to directly cost ME money. No longer did I feel safe about leaving my computer on and the telephone cord plugged into it. For me this was the last straw. I've never touched IE or Outlook Express since.

---

### Post by fatsheep on 2006-10-02
I used to use NoScript for firefox but I got tired of having to whitelist everything.  Also, I got into the habit of whitelisting websites regardless which negates the security value of NoScript. :p  On second thought, this thing looks pretty serious so I'll be reinstalling NoScript for the time being.

---

### Post by kerry_s on 2006-10-02
I'm not worried, those supposed flaws are coming from 2 "hackers" as they like to be called, who just happen to work with MS and are sponsored by MS but refuse to reveal the flaws. Can you say "FUD"?

---

### Post by NoTiG on 2006-10-03
[http://lxer.com/module/newswire/view/70873/index.html](http://lxer.com/module/newswire/view/70873/index.html)

> Lately, I read the headline: "Open Source browser Firefox is so critically flawed that it is impossible to fix, according to two hackers." Further on, in the ZDNet article I read: "The hackers claim they know of about 30 unpatched Firefox flaws. They don't plan to disclose them, instead holding onto the bugs."
Since that sounds suspicious, I decided to start searching for connections with MS. Easy enough, here it is:

    * 21:30-03:00 ToorCon Saturday Night Party - Sponsored by Microsoft [(Link)]("http://www.toorcon.org/2006/conference.html")

---

### Post by saracen on 2006-10-03
What is the difference between the potential damage that this could do on Ubuntu vs. what it could do on Windows.  Are we safer on Ubuntu because of the restricted nature of the filesystem?  This thing can't get root priveleges can it?

---

### Post by Quake on 2006-10-03
I was wondering, is there a Gnome browser that uses the Konqueror engine? (Such as Epiphany which uses the Mozilla engine)

---

### Post by skymt on 2006-10-03
> **Quake said:**
> I was wondering, is there a Gnome browser that uses the Konqueror engine? (Such as Epiphany which uses the Mozilla engine)

No. It would probably need too many KDE libs.

---

### Post by fuscia on 2006-10-03
> **Quake said:**
> I was wondering, is there a Gnome browser that uses the Konqueror engine? (Such as Epiphany which uses the Mozilla engine)

you know you can use gnome in konqueror, yes?

---

### Post by saracen on 2006-10-03
> **fuscia said:**
> you know you can use gnome in konqueror, yes?

I think what he meant was: "you know you can use konqueror in gnome, yes?"

---

### Post by aysiu on 2006-10-03
I clicked on that globe icon in Windows, and all it gives me are the general internet preferences--it's not a site-specific context, which means it's almost as much work as (one less click than) going to Tools > Internet Options.

---

### Post by saracen on 2006-10-03
How do I ban google-analytics.com from running scripts?  It's popping up on most of the sites that I visit but I can't find a way to explicitly ban it.

---

### Post by halfvolle melk on 2006-10-03
[http://developer.mozilla.org/devnews/index.php/2006/10/02/update-possible-vulnerability-reported-at-toorcon/](http://developer.mozilla.org/devnews/index.php/2006/10/02/update-possible-vulnerability-reported-at-toorcon/)

---

### Post by Quake on 2006-10-03
> **fuscia said:**
> you know you can use gnome in konqueror, yes?

I think you mean Konqueror in Gnome...
Yes, I know, but right now I don't want to use KDE applications in Gnome yet, I like everything to look "Gnomish". Just a personal preference right now.

---

### Post by fuscia on 2006-10-03
> **saracen said:**
> I think what he meant was: "you know you can use konqueror in gnome, yes?"

doh!](*,)

---

### Post by ice60 on 2006-10-03
> **aysiu said:**
> I clicked on that globe icon in Windows, and all it gives me are the general internet preferences--it's not a site-specific context, which means it's almost as much work as (one less click than) going to Tools > Internet Options.

did you try clicking the red icon next to it? you still have to fill in the url though.

[quote=saracen] 
How do I ban google-analytics.com from running scripts? It's popping up on most of the sites that I visit but I can't find a way to explicitly ban it.[/quote]doesn't no script do that? there's also an extension called CustomizeGoogle which disables alot of google stuff like ads, anonymises the google cookie, disables the google-analytics cookie and alot more.
[http://www.customizegoogle.com/](http://www.customizegoogle.com/)

---

### Post by Koori23 on 2006-10-03
I read that LX'er article and found it quite normal for FUD to be thrown aroud like that. Microsoft has deep pockets, and the fact that they sponsored beer night. Seriously, I can relate to the claim, I myself become a suprisingly agreeable person when someone brings over a case of beer. 

BTW, the head of Mozilla Security (Window Snyder) is really cute for a computer geek.

---

### Post by aysiu on 2006-10-03
> **ice60 said:**
> did you try clicking the red icon next to it? you still have to fill in the url though. That allows me to change cookie settings for that site. If I click on **Settings**, it just takes me to the general Internet Options settings.

---

### Post by ice60 on 2006-10-03
> **aysiu said:**
> That allows me to change cookie settings for that site. If I click on **Settings**, it just takes me to the general Internet Options settings.
OK. i think i should tell you i haven't used IE for 2/3 years. i don't have windows or IE installed either so i can't check these things.

---

### Post by DoctorMO on 2006-10-03
Are we that helpful that we'll give out help for IE on windows xp?

Man I love this comunity.

---

### Post by aysiu on 2006-10-03
> **ice60 said:**
> OK. i think i should tell you i haven't used IE for 2/3 years. i don't have windows or IE installed either so i can't check these things.
It's okay. I'm checking them for you.

Point is--that add-on for IE is relatively unknown (had to be tracked down through Google searching), and the vast majority of IE users will not blacklist domains for ActiveX or JavaScript.

There are far more Firefox users with NoScript installed than IE users with that obscure add-on installed.

Ultimately, though, it comes down to the user. A dumb user with Firefox will be just as vulnerable to exploits as a dumb user on IE.

---

### Post by skymt on 2006-10-03
> **aysiu said:**
> It's okay. I'm checking them for you.

Point is--that add-on for IE is relatively unknown (had to be tracked down through Google searching), and the vast majority of IE users will not blacklist domains for ActiveX or JavaScript.

There are far more Firefox users with NoScript installed than IE users with that obscure add-on installed.

Ultimately, though, it comes down to the user. A dumb user with Firefox will be just as vulnerable to exploits as a dumb user on IE.

Excellent summary. I think we can all agree with that.

---

### Post by ice60 on 2006-10-03
> **aysiu said:**
> It's okay. I'm checking them for you.

Point is--that add-on for IE is relatively unknown (had to be tracked down through Google searching), and the vast majority of IE users will not blacklist domains for ActiveX or JavaScript.

There are far more Firefox users with NoScript installed than IE users with that obscure add-on installed.

Ultimately, though, it comes down to the user. A dumb user with Firefox will be just as vulnerable to exploits as a dumb user on IE.
yeap, security is all about the user and not so much the software. 

i haven't let java or javascript run for a few years. when they're needed i enable them for that site. i think i've needed java once in 2/3 years. javascript is needed more often, but i think it should only be run through an http filter, something like privoxy, but if you are using Wine then Proxomitron is king with Grypen's Filter Set and the SSL Addons
[http://www.castlecops.com/t124920-About_Grypens_Filter_Set.html](http://www.castlecops.com/t124920-About_Grypens_Filter_Set.html)
[http://www.wilderssecurity.com/showthread.php?t=31087](http://www.wilderssecurity.com/showthread.php?t=31087)

i'd put Proxomitron up there with Linux in terms of how great it is.

---

### Post by fatsheep on 2006-10-03
Here's two videos related to that article if anyone's interested:

[http://news.com.com/1606-2_3-6121987.html?tag=ne.vid](http://news.com.com/1606-2_3-6121987.html?tag=ne.vid)
[http://news.com.com/1606-2_3-6121999.html?tag=ne.video.6121987](http://news.com.com/1606-2_3-6121999.html?tag=ne.video.6121987)

These guys are idiots...  Here's a quote from the video:

"We need to get back to that point where the internet is an elitest place where only intelligent people that are capable of ruining **** can communicate"

Um... right...

---

### Post by whynotchevron on 2006-10-03
finally a little more clarification . boy I got some good names for these two !!
[http://www.newsfactor.com/news/Hype-Surrounds-Alleged-Firefox-Flaw/story.xhtml?story_id=0030003Q1J7I]("http://www.newsfactor.com/news/Hype-Surrounds-Alleged-Firefox-Flaw/story.xhtml?story_id=0030003Q1J7I")

---


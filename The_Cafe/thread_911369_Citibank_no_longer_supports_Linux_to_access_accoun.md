---
title: "Citibank no longer supports Linux to access accounts"
date: 2008-09-05
forum: The Cafe
---

### Post by GISuser on 2008-09-05
I just tried to log into my Citibank account using Ubuntu 7.10, but Firefox 2.x could not render the login screen ([www.citicards.com](www.citicards.com)).  During their website re-design a few weeks ago, they stopped supporting Linux!  I called them up and complained.  The IT customer support were very friendly and were honest, they do not plan to support Linux.   

I am hoping that this post will cause others to voice their concern to Citibank not supporting Linux.  To voice a complaint: 1-800-347-4934.  Hitting zero twice usually gets a real person.  Or visit [www.citibank.com](www.citibank.com) and try to email them a complaint.  I could not, the screen kept going blank!

Thanks.

---

### Post by philinux on 2008-09-05
Get this addon.
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Once installed Tools > User Agent Switcher and choose IE7 windows vista.

The login screen will then render. You need cookies enabled as you know.

[edit] It renders with FF3 ok though.

---

### Post by GISuser on 2008-09-05
Thanks, that worked.  And thanks for reminding me about the add-on.  I totally forgot about the add-on after I rebuild my system a 5 months ago.

---

### Post by sancho panza on 2008-09-05
This needs confirmation. Here's what I experience:
Firefox3, Opera, Epiphany cannot login to Citibank/Citicards.

I dont know if changing user agent works on firefox. Even if I does, this is not a good sign. I wish I had a citibank account and I would have closed it. I have half my mind to call them up nonetheless.
I'm with GISuser.

---

### Post by mkvnmtr on 2008-09-05
I use Firefox 2 something on a Mac and Firefox 3 on Ubuntu to access Banamex here en Mexico which is a part of Citibank. I think it is the Browser and the security encryption that they recognize not the fact we are on Linux. I believe the also connect to Internet Explorer but I have never used it.

---

### Post by npnutn7 on 2008-09-05
when it starts loading, i could see the login screen but it disappear again.

this works for me , just press stop or "Esc" to stop loading the page in the moment you see login screen.

---

### Post by stimpack on 2008-09-05
Change bank ASAP. Don't trust your money to someone who wants you to use the most insecure OS/Browser.

---

### Post by phrostbyte on 2008-09-05
User Agent Switcher for the win, but no way in hell am I going to use a bank that forces me to do that. :popcorn:

---

### Post by doas777 on 2008-09-05
I don't use opera myself, but a colleague of mine uses it on windows, and he found that it would not load a wide-range of sites. he proudly regailed me with tales of his journey (in daily increments...) to discovering the user agent cloaking. I've had the same experience when using firewalls that filter agent-strings (in windows).

I guess i've always assumed that the site dynamically loaded a CSS profile for whatever browser (crap-control for IE and standards compliant for mozilla). I've also thought that their may be differances in javascript and activex runtimes. I guess I never assumed it was OS based (cause how can they tell by agent?) but the browser . you may be quite right however. lots of cyberthugs use alternative OSs too so it could be a security measure.

sancho panza, I agree, we should test for confirmation (of os blocking or browser).
does anyone have access to a win terminal that you could install opera on?

---

### Post by Redache on 2008-09-05
> lots of cyberthugs use alternative OSs too so it could be a security measure.

/Off Topic/
Who write0 code to exploit holes in Windows and Mac OSX. Some of them have a twisted morality that means they won't crap on their own doorstep, so it's technically safer in Linux from a virus standpoint.

+ Most Script Kiddies haven't got a clue and they're the ones who have mass penetration with regards to spam/viruses. The People who write give it to them to spread.
Kill the Kiddies - Stop the War.

/on Topic/

My Bank USED to not allow Firefox use but now they changed their minds. I didn't see how it COULDN'T support Linux as it's a basic SSL site but I guess they're weird that way/hire web dev's who haven't got the best skills.

---

### Post by doas777 on 2008-09-05
> 
[QUOTE]
lots of cyberthugs use alternative OSs too so it could be a security measure.


/Off Topic/
Who write0 code to exploit holes in Windows and Mac OSX. Some of them have a twisted morality that means they won't crap on their own doorstep, so it's technically safer in Linux from a virus standpoint.

+ Most Script Kiddies haven't got a clue and they're the ones who have mass penetration with regards to spam/viruses. The People who write give it to them to spread.
Kill the Kiddies - Stop the War.
[/QUOTE]

I agree entirely. In terms of security measures, I guess I was thinking attacks on the login mechanism (bruteforce, cert theft, phishing site creation, etc). your right though. I won't access my bank account from any windows system anymore (including my well administered and hardened one).

---

### Post by GISuser on 2008-09-09
Thanks again everyone.  I just received a customer survey from Citibank.  I kept pointing them to this thread in the comment section.  Hope this will get their attention, however unlikely.

---

### Post by Nepherte on 2008-09-10
Very strange. I can do online banking in Firefox (without user agent switcher) on the Belgian Citibank site.

---

### Post by airjaw on 2008-09-10
For the longest time, I kept getting this stupid popup on the citibank page that would NOT go away.  It blocked the entire screen and I had to make sure to press "stop" in my browser before it appeared and blocked the username and password login boxes.  This only worked about 10% of the time.  Frustrating, to say the least.

I thought citibank was just idiots for designing such a poor site but then one day I logged in through windows firefox and everything worked.  

I still consider citibank to be idiots.  Although maybe I'm the idiot for sticking with them for so long

---

### Post by mips on 2008-09-10
If a business no longer supports you as a client then change the business you are dealing with.

---

### Post by ooobuntooo on 2008-09-10
Please change user agent back to normal when you are not on the website.
Marketshare etc..

---

### Post by paradox82 on 2008-09-15
The work around the disappearing log in page is to add the following rule to adblock:

*citicards*.swf

This would block the bad flash on the main page (which is useless anyways, not used for navigation).

---

### Post by Methuselah on 2008-09-15
Isn't it ridiculous that people using firefox have to lie to websites so they'll work?

For one, it means that FF has no technical limitations that makes the pages impossible to render.

It also means that IE usage numbers are probably still somewhat inflated because sites which check that browser string will see Vista/IE even from some people happily using Linux/FF or Vista/FF.

Ridiculous!

HTML is not platform/browser specific!

---

### Post by JillSwift on 2008-09-15
It may be better to demand that such sites conform to real web standards, rather than try to sex-up their sites with browser and OS specific fluff. That way one's OS and browser choice won't make a difference to their site's usability.

---

### Post by worx101 on 2008-09-15
If they don't want to do business with me and prefer to stay away from standards... Ok fine by me, I can take my business elsewhere.

---

### Post by billgoldberg on 2008-09-15
How hard is it for those people to make a site that works regardless of OS?

My bank can do it, so they should all be able to do it.

---

### Post by 2cute4u on 2008-09-15
I don't know why it didn't work for you.

My dad has a tried it using firefox 3.1 (with the default UA ) on my computer and it worked perfectly well .Then he even tried it with midori 0.0.21, it also worked with no problem

---

### Post by rajeev1204 on 2008-09-15
Citibank india website is working fine on ff3.

---

### Post by david_lynch on 2008-09-15
> **rajeev1204 said:**
> Citibank india website is working fine on ff3.
Right, but what OS?

---

### Post by david_lynch on 2008-09-15
> **2cute4u said:**
> I don't know why it didn't work for you.

My dad has a tried it using firefox 3.1 (with the default UA ) on my computer and it worked perfectly well .Then he even tried it with midori 0.0.21, it also worked with no problemRight, but what OS is your dad using?

---

### Post by zmjjmz on 2008-09-15
> **david_lynch said:**
> Right, but what OS is your dad using?

Midori only runs on Linux.

---

### Post by 2cute4u on 2008-09-15
> **david_lynch said:**
> Right, but what OS is your dad using?

he was using my machine when it was running Hardy

---

### Post by venator260 on 2008-09-15
What I have to do is right click on the blank area and click play. Then the ad is viewable and I can close it and resume as normal.

---

### Post by mike1234 on 2008-09-15
I think denying a customer access because he/she doesn't use Windows or Mac is very retarded. I can understand their security concerns but if you're a customer what difference does it make? Most everyone uses some sort of flash or java and neither one of these have anything to do with gates or jobs. My bank uses thawte security certificates. :)  Not sure what platform they use.

[http://en.wikipedia.org/wiki/Thawte](http://en.wikipedia.org/wiki/Thawte)

M.

---

### Post by airtonix on 2008-09-30
I would of thought windows was the least secure method for online banking.

I read about a swedish ( or at least a eroupean) bank that tells its customers that their online banking issues will only be supported if they use a linux livecd they supply?

life is full of lol.

---

### Post by rune0077 on 2008-09-30
> **airtonix said:**
> I would of thought windows was the least secure method for online banking.

I read about a swedish ( or at least a eroupean) bank that tells its customers that their online banking issues will only be supported if they use a linux livecd they supply?

life is full of lol.

My bank just uses some fancy little electronic device that I must have in handy everytime I log on. Besides my password, I need a randomly generated number from this device (it looks like a very small pocket calculator). Each of these are unique, and it's the most secure thing in the world. Somebody could steal my password and username through electronic eavesdropping and still not be able to access my account because they lack the randomly generated number. To get that, they would have to physically steal the device from me. I don't get why all Internet banks don't use a scheme like that, since it makes cracking an account virtually impossible.

---

### Post by rajeev1204 on 2008-10-07
> **david_lynch said:**
> Right, but what OS?

Ubuntu hardy of course.

---

### Post by dchriscoe on 2008-12-22
For what is it worth, this worked for me: install Adobe Flash Player 10.

Steps:

1. Go to download section of [http://www.adobe.com/shockwave](http://www.adobe.com/shockwave)
2. Download the Ubuntu 8.04 version to local drive (install_flash_player_10_linux.deb)
3. First remove old version of Player9 if have it installed (important if you do not,it  will not install new Player in Mozilla plugins) 
4. To uninstall Player9 type in the terminal "sudo apt-get remove --purge flashplugin-nonfree"
5. In terminal type "sudo dpkg -i install_flash_player_10_linux.deb" to now install version 10.
6. Restart Firefox and type "about:plugins" in location window.
7. Under Shockwave Flash section, version 10 should be there.
8. On mine even though I deleted version 9 it still showed on plugins and I right clicked on it to disable: this is a unnecessary step but cleaned up my plugins screen.

After this I was able to load the Citibank web page without any problems.  Installing Player10 also fixed two other sites for me.

---

### Post by plb on 2008-12-22
I can access my citibank online via firefox without any type of user agent switcher. Debian Lenny - Iceweasel

---

### Post by racerraul on 2009-04-17
I hate to be the grave digger, but I just recently experienced this issue trying to access my online acct.

Ofcoarse, calling Citibank for support was incredibly stupid.  I might as well have called the local mental institute for help.

In a nut shell they told me to use windows... Argh!!!! I have a window machine, but that is not a solution.

I asked to speak to someone with some technical knowhow to explain to me what the site was designed to do so that I may troubleshoot my own problem, but again... I was getting more feedback using the force with the plants around the house.

My problem was that I couldn't select or type in any of the fields on the webpage. On my own, I found out the site used flash content... a simple right click and selecting play (default is loop) did the trick...

So FYI... yet another option to try, because installing the agent switcher... I did however, install the agent after finding this thread, but not before confirming that worked before installing the agent.

---

### Post by cmargolin on 2009-04-17
As I recall, turning off Flash (using Flashblock) did the trick.

---

### Post by kumoshk on 2009-06-12
Please read this. [See my posts later on&#8212;I don't really think Citibank is much to blame for this, given the probability of ignorance on certain factors, but this is still applicable to other entities, I think.]

> **GISuser said:**
> &#8230; they do not plan to support Linux.
I was on the verge of getting an account with Citibank, but not now.

What is there to support? It's not like they need to rescript everything. It's probably only one line of code that makes the difference (and that not even necessary in any regard). The fact that it works with that extension goes to show it was probably a purposeful move on their part. The question is, why? Does Citibank actually get funds from other companies? Do they have to do it to get some cut on their software prices or something?

Rather, one should say they plan to continue to boycott Linux&#8212;seeing as there's nothing special they have to do to support it. It works fine with with the user agent switcher (although I wouldn't doubt if they'd do their best to eliminate that possibility, if they could).

We need to start a coalition of companies that support Linux, and cater to them, I say. We're not a small crowd, but they'd have everyone think we are (and just about everyone does).

I like how they tell us to install a different operating system just so we can go with their bank. Nope&#8212;not going to do that. I use Linux and that's the way it is. Linux is a way of life, and not a depreciated one&#8212;not an inferior.

We should lobby to get a law passed against companies purposefully discriminating against Linux, and all these discriminatory funding-issues. It's nigh unto racism, if not just as bad. It's like saying you have to join an opposing political party, or get a harmful operation, to use their bank. The problem, though, is that major corporations are those targeting Linux, and those forming the minds of the populace&#8212;not the populace themselves (however much they might be on course to doing it ignorantly). They're out to make money the only motivation for us all, and that is not a good thing (despite how well they've succeeded so far).

I hope someone takes this to heart.

---

### Post by kumoshk on 2009-06-12
> **cmargolin said:**
> As I recall, turning off Flash (using Flashblock) did the trick.

Ah, just noticed this. I use Flashblock. If it really works (see my next post&#8212;it doesn't), maybe I mean to ease up on Citibank. However, we should still lobby and converge&#8212;plenty of other places really do the likes of what we've discussed (just about every downloadable audiobook site, to hint at a few).

Some places still tell you to install Windows or Macintosh OS, though. Such as that, I think, should be eliminated. Laws should be made to make companies have to rephrase things like that, even if there's no mention of Linux (especially where it's not absolutely true that the system is not cross-platform). For instance, they could just tell us their recommendation, rather than saying it's required (not that they should give people license to sue them if the software has unforeseen problems on another OS).

---

### Post by kumoshk on 2009-06-12
> **kumoshk said:**
> Ah, just noticed this. I use Flashblock. If it really works, maybe I mean to ease up on Citibank &#8230;

Um, it's not a Flashblock issue. I disabled it and the problem persists. You might have been thinking of INGDirect with a previous version of Firefox&#8212;I think the problem there was fixed (and they never said they didn't support Linux).

---

### Post by ricardisimo on 2009-06-12
Konqueror works on the Citibank login page, as I recall. Don't quote me on that, as I was using Kubuntu for all of about two weeks. Still, I remember that little detail.

By the way, you can also just right-click on the page and select "Play" instead of "Loop". Works for me in Firefox, without any plugin (although I will check that out.)

---

### Post by kumoshk on 2009-06-12
> **ricardisimo said:**
> By the way, you can also just right-click on the page and select "Play" instead of "Loop". Works for me in Firefox, without any plugin (although I will check that out.)

I don't see any Flash when I go to the site at all. However, I just noticed something important. There's a link at the bottom of the page that says if you don't use one of the browsers or operating systems they indicate then you can still use the site by clicking the continue button hidden at the bottom right corner of the page (sorry—didn't notice that before).

---

### Post by ricardisimo on 2009-06-14
That link to other browsing options never worked for me.

You're telling me that this login page (see attached) has no Flash going on when you go to it? If you're still having issues, try Konqueror.

---

### Post by thisllub on 2009-06-14
Just get another bank.
Tell them why you are leaving.

---

### Post by jfcous on 2009-12-16
I am using Ubuntu 8.04 on a laptop with Firefox 3.0.15.  I found that if I disabled shockwave flash 9.0 r 260  (r 124 is enabled) than I could access the Citibank log-in page.

---

### Post by Gizenshya on 2009-12-16
Well, I'll  add a couple things for digestion...

1.  If a company doesn't want to take proper steps to deal with a significant minority of their customers, you are right to be dissatisfied.  However, calling and saying "support me" does nothing.  As some have mentioned, you should change banks.  But not just change banks, call them and ask about the issue, and then say that that is unacceptable for you, and you are now going to close your account.  Then, go in and close your account, and send in a confirmation that you have closed your account (scan) in with your complaint (e)mail message.  Or, google around for an email addy for senior in the company, and say "*this* is what your lagging online technology is doing-- just thought you might want to know."  And include a scan of your confirmation of cancellation as an attachment.  Maybe even a screenshot of the affected website.

But, that being said...

2.  What customer support people mean when they say "we don't support (OS/platform/whatever)" is "we aren't trained to deal with questions regarding (OS/platform/whatever), so, unfortunately, I will be unable to help you."  They don't mean, since you use (whatever), we don't want your business: go screw yourself.  Well, unless otherwise specified, that is.  Whether we like it or not, *nix experience isn't that common, and it takes a lot to teach someone enough about *nix from scratch to be able to help an experienced *nix user when they have issues.  It just isn't practical by any stretch of the word.  That being said, IMO, any relevant company of any decent size should have a hired *nix tech on hand to handle such inquiries.

3.  But, if they actually did clarify and say something like "we intentionally make our software to be incompatible with (whatever)," then just see #1 and take your business elsewhere.  I'd call them just to make sure.  All these types of conversations are recorded, and they know they are being recorded.  So if I were you I'd record it as well, and include that in an email (mp3) in that senior email message, and perhaps youtube it as well.  Something like "(bank name) customer support" and some other key terms.

But my point is, don't just jump to conclusions.  Make sure you get your facts, and if you are still not satisfied, make the most of it-- but stick to facts, and not assumptions.  You can defeat your whole purpose and get ignored very quickly if you don't do your homework first to get it right.

---

### Post by speedwell68 on 2009-12-16
The core advice when you find any firm that does not support your OS/Browser choice is to vote with your wallet and walk away.  But first make sure they know why you are walking away.  You can complain till you are blue in the face, but it is money that talks the loudest.

---

### Post by earthpigg on 2009-12-16
> 2. What customer support people mean when they say "we don't support (OS/platform/whatever)" is "we aren't trained to deal with questions regarding (OS/platform/whatever), so, unfortunately, I will be unable to help you." They don't mean, since you use (whatever), we don't want your business: go screw yourself. Well, unless otherwise specified, that is. Whether we like it or not, *nix experience isn't that common, and it takes a lot to teach someone enough about *nix from scratch to be able to help an experienced *nix user when they have issues. It just isn't practical by any stretch of the word. That being said, IMO, ***any relevant company of any decent size should have a hired *nix tech on hand to handle such inquiries.***

regarding the part i bolded -- im not so sure this makes sense. having an additional staff member with a higher salary on hand for each shift -- just to handle 1% of ***potential*** customers? the 1% that is most likely to be the learn-to-do-it-yourself and thus ***least likely to call tech support?***

---

### Post by kumoshk on 2009-12-16
> **earthpigg said:**
> regarding the part i bolded -- im not so sure this makes sense. having an additional staff member with a higher salary on hand for each shift -- just to handle 1% of ***potential*** customers? the 1% that is most likely to be the learn-to-do-it-yourself and thus ***least likely to call tech support?***

When working with something as simple as a bank website, you'd think OS-specific support would be a non-issue. Customer service isn't the issue, in my opinion. It's web-site functionality. No need to hire a Linux tech.

---

### Post by Gizenshya on 2009-12-16
Both good points.

However, 'representatives' of that 1% do call.  I've found myself in that situation before (unable to resolve issues on my own), and gotten no help from the company.

and to the second comment, yep.  But they are usually turned off after the topic of OS comes up.  They just assume it is because of the OS, or that there could be issues that they may have no idea about.  They just don't know where to go after that-- even if they have the potential to help.

That being said, be careful not to assume the results of a proper cost-benefit analysis based on guesswork.  Also, even if it is not profitable in-and-of itself, simply having that option could easily turn into a core competency.  It may also increase the propensity to purchase for non-*nix users simply because it increases their specialty or customer support status.  A lot of stores carry stuff that doesn't sell just to have variety, which brings in more customers in for their larger-volume items.  Total economic impact is not always immediately obvious.  I am certain that having at least 1 *nix expert on hand during normal support hours would be more than worth it.

---

### Post by handy on 2009-12-17
The tiny credit union that I belong to supports both OS X & Linux.

Internet access to the banking facility is via web browser, & I use Firefox.  

Why does there exist an Operating System problem here with any of these financial institutions?

Is it that they can't afford to pay software architects to design a foolproof, one size fits all solution?

I don't understand why the likes of Citibank, haven't spent the paltry amount of money on their server software, so as to be using software that functions in a state that is unperturbed by other OSs? 

Further; to the point that the server is able to function in complete ignorance of the OS that is being used by the client.

If my tiny little credit union can do it, then so can the likes of Citibank, who are one of the largest & most policy evil banking corporations in the world.

---

### Post by kumoshk on 2009-12-17
> **handy said:**
> I don't understand why the likes of Citibank, don't haven't spent the paltry amount of money on their server software, so as to be using software that functions in a state that is unperturbed by other OSs?
On the contrary, I believe most os-dependent sites spend much more money on their web development than the normal os-independent ones, seeing as the dependent ones are usually proprietary. They may, however, spend less money of finding someone to make the site, but that's just speculation.

As far as why they did it&#8212;well, I speculate that it's probably because it's either the popular CMS they're familiar with, they hired Windows-only programmers to do everything from scratch (for the sake of owning some proprietary software), or someone paid them to do it. I don't think they're /necessarily/ at direct fault for it.

Having said all that, I think Citibank does address this issue, though I forgot how they did it. Other websites concern me more&#8212;especially those that make you use OS-dependent download managers, such as Audible, etc.&#8212;there's really no reason I know of for that, as they don't need such to prevent re-downloads from third parties, etc. I doubt if it's just because they had too many people that didn't know how to download stuff, or else you'd think they'd be smart enough to leave the normal option additionally available so as not to exclude all the non-Windows, non-Mac users. But then, ignorance, or the desire against redundancy and the false belief that there aren't many of the said users might lead them against this.

---

### Post by alexfish on 2009-12-17
> **GISuser said:**
> I just tried to log into my Citibank account using Ubuntu 7.10, but Firefox 2.x could not render the login screen ([www.citicards.com]("http://www.citicards.com")).  During their website re-design a few weeks ago, they stopped supporting Linux!  I called them up and complained.  The IT customer support were very friendly and were honest, they do not plan to support Linux.   

I am hoping that this post will cause others to voice their concern to Citibank not supporting Linux.  To voice a complaint: 1-800-347-4934.  Hitting zero twice usually gets a real person.  Or visit [www.citibank.com]("http://www.citibank.com") and try to email them a complaint.  I could not, the screen kept going blank!

Thanks.

This May HAVE A STORY  !

The Start

[http://www.encyclopedia.com/doc/1G1-55181005.html](http://www.encyclopedia.com/doc/1G1-55181005.html)

The Middle 
[http://boycottnovell.com/2008/09/03/citibank-and-ms/](http://boycottnovell.com/2008/09/03/citibank-and-ms/)

Spot the bit About This // 
In the case of the Bank of America, even Firefox was banned


Waiting For The End / GET THE STARSHIP READY NOW

---

### Post by Dr. C on 2009-12-17
This is not only retarded but in the case of banking very dangerous. The solution for GNU / Linux users is very simple. Immediately withdraw all funds on deposit with said bank and move them to an institution that supports GNU / Linux. Then advise the bank why this was done. 

This does beg a very important question. What would happen to a bank if say 1% of the funds on deposit were suddenly withdrawn? Can this start a "run" on the bank, especially in these economic times?

In addition to the bank I would also contact the banking regulators and advise them that the bank may be placing depositors funds at risk by inducing the sudden withdrawal of 1% of the funds on deposit by denying  GNU / Linux users access to their on line accounts.

A very dangerous move by a financial institution.

---

### Post by alexfish on 2009-12-17
> **FineE said:**
> This is not only retarded but in the case of banking very dangerous. The solution for GNU / Linux users is very simple. Immediately withdraw all funds on deposit with said bank and move them to an institution that supports GNU / Linux. Then advise the bank why this was done. 

This does beg a very important question. What would happen to a bank if say 1% of the funds on deposit were suddenly withdrawn? Can this start a "run" on the bank, especially in these economic times?

In addition to the bank I would also contact the banking regulators and advise them that the bank may be placing depositors funds at risk by inducing the sudden withdrawal of 1% of the funds on deposit by denying  GNU / Linux users access to their on line accounts.

A very dangerous move by a financial institution.

TAKE YOUR SHARES AS WELL / ITS DIsCRIMINATION

---

### Post by Dr. C on 2009-12-17
> **alexfish said:**
> TAKE YOUR SHARES AS WELL / ITS DIsCRIMINATION

Discrimination in banking can be very dangerous. In this case it can potentially put many depositors at risk even those who use Windows.

---

### Post by alexfish on 2009-12-17
> **FineE said:**
> Discrimination in banking can be very dangerous. In this case it can potentially put many depositors at risk even those who use Windows.

That is so true. So the answer is :The Banks should allow Linux users  access to Their Accounts

Re: situation : Got bills to pay. Transfer funds etc Today 

 Boot up the Computer With Linux , met with a blank screen , server could be down, try next day

Next day situation   phone the Bank , No support For Linux?

What is the immediate solution , Buy Windows 

The operating system is of my choice , The Banks Should Honour That Choice by the very fact I am the customer with a Linux Operating System

For the bank to come out with this type of statement ? Who is at risk , it is not Bank at risk. It is me as The  Customer.

Banks are going through a bad times , Yes we should support them, But they should support us as well . It works both ways

---

### Post by handy on 2009-12-17
Due to the fees I have been charged lately by my "very friendly credit union" I have decided that in future I am going to withdraw all funds as they arrive in that financial institution & pay cash, or use credit card if I must, in future.


Fuuuuck them!  They are stupidly hungry & I for one will not support their greed any more.

---

### Post by HappinessNow on 2009-12-17
> **GISuser said:**
> I just tried to log into my Citibank account using Ubuntu 7.10, but Firefox 2.x could not render the login screen ([www.citicards.com](www.citicards.com)).  During their website re-design a few weeks ago, they stopped supporting Linux!  I called them up and complained.  The IT customer support were very friendly and were honest, they do not plan to support Linux.   

I am hoping that this post will cause others to voice their concern to Citibank not supporting Linux.  To voice a complaint: 1-800-347-4934.  Hitting zero twice usually gets a real person.  Or visit [www.citibank.com](www.citibank.com) and try to email them a complaint.  I could not, the screen kept going blank!

Thanks.

> In August 2008, after a three year investigation by California's Attorney General Citibank was ordered to repay the $14 million (close to $18 million including interest and penalties) that was removed from 53,000 customers accounts over an eleven year period from 1992-2003. The money was taken under a computerized "account sweeping program" where any positive balances from over-payments or double payments were removed without notice to the customers.[http://en.wikipedia.org/wiki/Citibank](http://en.wikipedia.org/wiki/Citibank)

Why anyone would bank with such a company is beyond me. 

Do what I did, close all your Bank accounts and only deal with credit unions.

---

### Post by Dr. C on 2009-12-17
> **alexfish said:**
> That is so true. So the answer is :The Banks should allow Linux users  access to Their Accounts

Re: situation : Got bills to pay. Transfer funds etc Today 

 Boot up the Computer With Linux , met with a blank screen , server could be down, try next day

Next day situation   phone the Bank , No support For Linux?

What is the immediate solution , Buy Windows 

The operating system is of my choice , The Banks Should Honour That Choice by the very fact I am the customer with a Linux Operating System

For the bank to come out with this type of statement ? Who is at risk , it is not Bank at risk. It is me as The  Customer.

Banks are going through a bad times , Yes we should support them, But they should support us as well . It works both ways

It is the bank that is most at risk here and not the customers. The danger is that such a move by the bank could spark a bank panic, if all GNU / Linux users start withdrawing funds all at once, as many have suggested in this thread. Small depositors would be covered by the FDIC but large depositors would not. 

Personally I would withdraw my deposits from the bank in question regardless of my choice in OS before [this]("http://www.dealbreaker.com/images/entries/BNP%20Paribas%20Bank%20Panic") happens.

and for a more modern version [http://newshopper.sulekha.com/hk-bank-run-hits-singapore_photo_443170.htm]("http://newshopper.sulekha.com/hk-bank-run-hits-singapore_photo_443170.htm")

---

### Post by alexfish on 2009-12-17
> **&#20170 said:**
> [http://en.wikipedia.org/wiki/Citibank](http://en.wikipedia.org/wiki/Citibank)

Why anyone would bank with such a company is beyond me. 

Do what I did, close all your Bank accounts and only deal with credit unions.

  	 	 	 	 	 	  Probably Made Most of it Out Of Linux Users That could Not Get on Line

---

### Post by lostinxlation on 2009-12-17
I paid last month's bill at citicard website through firefox on Slackware last week. I also accessed their website through fixrefox on vector linux a minute ago, and had no issue.
Most likely reason to fail the access to their website is lack of some add-on in your system.

---


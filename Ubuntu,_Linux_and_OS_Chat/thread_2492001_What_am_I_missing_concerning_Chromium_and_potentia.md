---
title: "What am I missing concerning Chromium and potential cross site scripting?"
date: 2023-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by donald187 on 2023-10-27
Hi everybody.  Full disclosure, I'm currently on Debian.  One reason is my one remaining concern about Ubuntu and security.  (I've generally resolved my other concerns.)

I'm kind of looking for opinions, educated evaluations, and experiences  rather than hard answers (which are also welcome of course).  I just  think that this topic is more suited for the chat subforum rather than  support as I think that the hard answer is just that medium cve's just  take some time to fix.

Now generally I use Firefox to access my bank but sometimes the login doesn't work so I have to use Chromium.  Just through observation it seems that it sometimes takes more than a week to update the stable channel.  [One time it took three weeks.]("https://ubuntuforums.org/showthread.php?t=2488276")

Generally most cves for Chromium seem to be medium cve's (just by informal observation checking the Ubuntu CVE Tracker).  I get that no one is in a hurry to fix medium cve's.  And not just Ubuntu but through Googling it seems that medium cve's are fixed in time measured in months so I get that.  

In the  [Ubuntu  CVE Priorities]("https://people.canonical.com/~ubuntu-security/priority.html") they say that cross site scripting is a medium cve.  My understanding of cross site scripting is that someone could steal information entered on a form on a web page.  So what I'm concerned about is that since seemingly Chromium is sometimes updated in a week to three weeks that someone could steal my banking credentials through cross site scripting.

Am I right in this assessment?  What am I missing?  For example, perhaps Ubuntu is carefully watching the cve's and only delaying updates when it is safe.

I get that I could just use the candidate channel but I would prefer not to if I can help it.

---

### Post by donald187 on 2023-11-01
I suppose I'm trying to be too granular for the scope of this forum.  Probably it's generally covered in the following quote by Alex Murray.

> 
Vulnerabilities which affect the largest number of Ubuntu installations  and which present the largest risk (by say being remotely exploitable  without any user input, etc.) are prioritised critical or high. Those  which affect only a small number of users and might require user-input  or might only cause smaller effects such as a denial-of-service may be  prioritised as medium, low or negligible. This prioritisation is done on  a case-by-case basis for each vulnerability,....

[URL="https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation"]
[/URL][https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation](https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation)

---

### Post by donald187 on 2023-11-01
Still, even though cross site scripting may be a "smaller effect" from a  technical standpoint if someone gets your banking information that's  real world serious.

---

### Post by donald187 on 2023-12-23
Oh well, I don't really distrust Canonical.  I was just enjoying figuring these things out.  But I guess this is beyond my abilities.  I'm sure Canonical is taking care of me. :)

But then again, what do I know?

---

### Post by Paddy Landau on 2023-12-29
I use Chrome, which is updated rapidly. You have to install it from the official website ([instructions]("https://support.google.com/chrome/answer/95346")), and the installation adds the official PPA.

---

### Post by TheFu on 2023-12-29
I'd never use Chrome. Why would providing a huge advertising company, known for stealing information without clearly asking or compensating each person for this breach be ok?  I'm at a lose to put it any clearer.

Chromium is almost as bad.  There are so many tendrils from that marketing company inside Chromium and when they switched to snap-only distribution, they lost me.  Snaps broke my ability to control security of browsers, so any browser software that is snap packaged, I stopped using.  Basically, Canonical forced me to change to a non-snap desktop so I could have control AND better security.

Browsers are constantly getting security wrong. Constantly.  Don't trust any browser to be bug free. None of them are and when it comes to privacy, google has a poor record of protecting us.

I use different browsers for different purposes almost always running inside a firejail container.  Sometimes that is using a container that prevents touching any local storage, like I do with banking logins.  Sometimes I allow read-write access to a few directories - usually /tmp/ from the browser.  

I seldom worry about cross-site scripting, as I block all 3rd party cookies and use "private" mode from firejail for any locations that I suspect are doing things I wouldn't like.  Additionally, I only access financial institutions using a separate VM with firejail around a browser that isn't allow to save anything.  Where I live, personal banking accounts have limited liability coverage and business banking accounts have zero liability coverage. This means I need to be careful accessing any bank accounts, since that could lead to having all data/funds stolen by nefarious people on the other side of the world.  I used to be a CFO for a small company.  To make payroll, we'd have $100K/month in our checking account.  Imagine if that was stolen and the lives it would impact?  No way will I risk a failure by using the same browser environment that I use for any other purpose for access to payroll checks. No way! It is too important.

Similarly, I'd never use Chrome.  Too risky.

---

### Post by donald187 on 2023-12-29
> **Paddy Landau said:**
> I use Chrome, which is updated rapidly. You have to install it from the official website ([instructions]("https://support.google.com/chrome/answer/95346")), and the installation adds the official PPA.

I had forgotten about Chrome.  That would certainly solve the problem of sometimes slow updates.  I've become somewhat of a purist on Linux trying to stick with only the distribution.  But a respected Debian forum member once said that Chrome would not cause instability so from that perspective it should be ok.  I'll consider it.  Thanks!

---

### Post by donald187 on 2023-12-29
> **TheFu said:**
> I'd never use Chrome. Why would providing a huge advertising company, known for stealing information without clearly asking or compensating each person for this breach be ok?  I'm at a lose to put it any clearer.

Chromium is almost as bad.  There are so many tendrils from that marketing company inside Chromium and when they switched to snap-only distribution, they lost me.  Snaps broke my ability to control security of browsers, so any browser software that is snap packaged, I stopped using.  Basically, Canonical forced me to change to a non-snap desktop so I could have control AND better security.

Browsers are constantly getting security wrong. Constantly.  Don't trust any browser to be bug free. None of them are and when it comes to privacy, google has a poor record of protecting us.

I use different browsers for different purposes almost always running inside a firejail container.  Sometimes that is using a container that prevents touching any local storage, like I do with banking logins.  Sometimes I allow read-write access to a few directories - usually /tmp/ from the browser.  

I seldom worry about cross-site scripting, as I block all 3rd party cookies and use "private" mode from firejail for any locations that I suspect are doing things I wouldn't like.  Additionally, I only access financial institutions using a separate VM with firejail around a browser that isn't allow to save anything.  Where I live, personal banking accounts have limited liability coverage and business banking accounts have zero liability coverage. This means I need to be careful accessing any bank accounts, since that could lead to having all data/funds stolen by nefarious people on the other side of the world.  I used to be a CFO for a small company.  To make payroll, we'd have $100K/month in our checking account.  Imagine if that was stolen and the lives it would impact?  No way will I risk a failure by using the same browser environment that I use for any other purpose for access to payroll checks. No way! It is too important.

Similarly, I'd never use Chrome.  Too risky.

So to recap, browsers are insecure, Google steals information, and use Firejail.  To be honest I'm not too worried about Google.  And snaps have a built in sandbox.  I haven't been ambitious enough to use the Firefox PPA (so that I could use Firejail).  As I mentioned in the previous post I've become a bit of a purist wanting to use just the distribution.  But there's no rhyme or reason about it.  Something to think about.  Thanks!

---

### Post by Paddy Landau on 2023-12-30
> **TheFu said:**
> I'd never use Chrome. Why would providing a huge advertising company, known for stealing information without clearly asking or compensating each person for this breach be ok?
Gosh, @TheFu, that seems like quite a rant against Google, ha ha!

Google and I have a deal. Google provides a great deal of free services to me and the charities that I support (free of charge), and in return Google advertises to me based on my preferences. I don't think that that's a bad deal. I don't believe that it *steals* my information; everything is clear, unless you fail to read the T&C or the news.
> **TheFu said:**
> Snaps broke my ability to control security of browsers…
This is the single thing where snap fails badly: It doesn't allow you tailor the sandbox. That's why I can't use snap Gedit, because it restricts access to a very select few folders. For example, I can't use it to edit, say, /etc/fstab, or even files in my own ~/bin. Flatpak is better in that regard.

---

### Post by TheFu on 2023-12-30
Google has been caught lying far too many times for it to be accidental. It all started when they removed the "Don't be evil" moto.  Seems their moto is now, "see what we can get away doing".

Just yesterday, [https://apnews.com/article/google-incognito-mode-tracking-lawsuit-settlement-8b30c9397f678bc4c546ab84191f7a9d](https://apnews.com/article/google-incognito-mode-tracking-lawsuit-settlement-8b30c9397f678bc4c546ab84191f7a9d)
> Google settles $5 billion privacy lawsuit over tracking people using &#8216;incognito mode&#8217;
The class-action lawsuit filed in 2020 said Google misled users into believing that it wouldn&#8217;t track their internet activities while using incognito mode.

Is that a company that should be trusted?

I want nothing from Google, but there's no way I can opt out of their tracking without providing them even more information.  That's wrong.  People who wish to be tracked should have to opt-in.

---

### Post by Paddy Landau on 2023-12-30
> **TheFu said:**
> It all started when they removed the "Don't be evil" moto.  Seems their moto is now, "see what we can get away doing".
Actually, you are right there.
> **TheFu said:**
> Just yesterday…
True, that. I withdraw my comments.
> **TheFu said:**
> Is that a company that should be trusted?
No, but please name a giant company that can be trusted! At least it's not as godawful as Amazon, the way it treats its workers.

---

### Post by donald187 on 2024-01-03
So apparently cross site scripting has various levels of severity.

> 
XSS can cause a variety of problems for the end user that range in severity from an annoyance to complete account compromise.

[https://owasp.org/www-community/attacks/xss/](https://owasp.org/www-community/attacks/xss/)

and 

> 
The impact of XSS is moderate for reflected and DOM XSS, and severe for  stored XSS, with remote code execution on the victim&#8217;s browser, such as  stealing credentials, sessions, or delivering malware to the victim.

[https://owasp.org/www-project-top-ten/2017/A7_2017-Cross-Site_Scripting_(XSS)](https://owasp.org/www-project-top-ten/2017/A7_2017-Cross-Site_Scripting_(XSS))

So I'm sure this factors into [Ubuntu's CVE Priorities]("https://people.canonical.com/~ubuntu-security/priority.html").

And apparently cross site scripting is not strictly medium.  I found a couple of cross site scripting CVEs on the Ubuntu CVE tracker which were rated high.  And over 300 rated low.

[https://ubuntu.com/security/cves?q=XSS&package=&priority=high&version=&status=](https://ubuntu.com/security/cves?q=XSS&package=&priority=high&version=&status=)

But then ian-weisser did say that the CVE Priorities were merely guidelines.

[https://ubuntuforums.org/showthread.php?t=2481959&p=14123529#post14123529](https://ubuntuforums.org/showthread.php?t=2481959&p=14123529#post14123529)

Still, the vast majority of cross site scripting cves do seem to be medium so I'm not sure that these observations help answer my questions.

---

### Post by TheFu on 2024-01-03
Just turn off all XSS everywhere and be done with it.  Any website that doesn't work without XSS off is one that home users don't need to visit.

If it is required for a work-related webapp, then you shouldn't be using any of your own equipment and the company is responsible for everything. If they allow it for any reason, including ignorance, it is their fault, not yours.

XSS has been a known attack vector for about 15 yrs. We have choice.  We don't need to accept defaults if we disagree with them. We don't have to use webapps that are security and/or privacy risks. We don't have to use programs that don't meet our security requirements. Sometimes I use lynx for browsing. Sometimes I will use a web-site cloning tool to grab a specific page I want from a website - outside using any browser.  We don't have to use javascript either.

These things are all our choices to make.  Nobody else can make them for us, at least at home. It is fine to disagree with others. We each have different needs.

---

### Post by Paddy Landau on 2024-01-04
> **TheFu said:**
> Any website that doesn't work without XSS off is one that home users don't need to visit.
I think that you meant "with", not "without"?
> **TheFu said:**
> Just turn off all XSS everywhere and be done with it.
Agreed. My websites explicitly forbid XSS altogether.
> **TheFu said:**
> We don't have to use javascript either.
That one is really hard! I use a CMS (content management system), specifically WordPress, to generate my websites, and that's impossible without JavaScript, unfortunately.

---

### Post by TheFu on 2024-01-04
> **Paddy Landau said:**
> That one is really hard! I use a CMS (content management system), specifically WordPress, to generate my websites, and that's impossible without JavaScript, unfortunately.

[https://www.schneier.com/blog/archives/2024/01/new-iphone-exploit-uses-four-zero-days.html](https://www.schneier.com/blog/archives/2024/01/new-iphone-exploit-uses-four-zero-days.html)  It uses Javascript to get root.  JavaScript is very complicated.  The barrier to entry for programming it is extremely low.  Just because something works, that doesn't mean it is secure.  Sure, that was an Apple/iOS (not Cisco) issue, but javascript is problematic for many security reasons.  I'd rather not allow random people in the world to run their code on my systems.

My default browser setup denies javascript and it generally works to consume content.  I don't use a browser for videos or audio mainly for security reasons, so there's little need for javascript to be allowed from random websites.  Heck, even on these forums, I disallow a number of unnecessary sites from running javascript.  Sometimes there is a small change and things break.  Nobody said security was free.

On my blog, there is some javascript used - mainly for analytics and for posting. If you don't allow javascript, that's 100% fine with me.  99.999% of the content will still be shown. Analytics help me to make decisions. I don't outsource it. That would be breaking the trust, considering people are visiting my home, literally, when they come to my blog.  I demand very few things of visitors, but proper behavior is enforced, sometimes.  There are some really nasty people in the world.  This morning, I was reviewing anomalous log lines and saw a new attack. It was getting farther than I expected, but since I have multiple layers of security, it was blocked.  The subnet their traffic originated from is now blocked. Sorry for everyone else caught in that same subnet.  It was only a /20, so not overly huge.  It was from a reputable VPS company, so their account will be terminated soon, if it hasn't already been by the VPS guys.  The VPS doesn't want to be notified, it seems since their "abuse" email address doesn't work.   I don't use them, but did consider them in my final 2 choices. It really came down to a flip of the coin for which VPS I'd use.  OTOH, moving to a new VPS isn't a big deal to me. The actual "work" would be about 10 minutes, with the DNS updates forcing the longest delays.

---

### Post by Paddy Landau on 2024-01-04
> **TheFu said:**
> My default browser setup denies javascript and it generally works to consume content.
Intrigued, I decided to test this on my own website. It mostly works without Javascript, although the website doesn't look quite as "pretty". The contact form (presumably because of the anti-spam measures) and some of the buttons such as the "phone" button, don't work.

*(Edited to correct "Javascript")*

---

### Post by TheFu on 2024-01-04
Details matter.

Java and JavaScript are two COMPLETELY DIFFERENT languages.  

Java-based websites/webapps need a JRE on the client-side to work at all. I haven't installed any JRE over a decade.  

Around 1994, I was working in a govt lab writing cross-platform C++ and some guys from SunMicrosytems came for a visit and exchange.  It was dev to dev stuff - which had everyone on my team installing a JRE and running  little java applications, copying the binaries to every platform we had (about 15 different platforms) and running the java programs. They were slow and bloated. The Sun devs said that would be addressed with tighter code and better performance. 29 yrs later and I'm still waiting.

JavaScript was Mozilla's attempt to leverage Java's good press (at the time) for being secure. They look a little like each other, but are vastly different.

Do you really have a phone button on your website?  Is it a $15/minute number?  I've thought about setting one of those up as my main phone number to give out. I really hate phones since I was on-call 24/7/365 for 5 yrs - not allowed to leave the city.  Text is even worse.

---

### Post by Paddy Landau on 2024-01-04
> **TheFu said:**
> Details matter.

Java and JavaScript are two COMPLETELY DIFFERENT languages.
Aargh! I meant to write "Javascript". I have no idea why I wrote "Java" and then failed to pick it up when proofreading.

It was Javascript, not Java, that I disabled.
> **TheFu said:**
> Do you really have a phone button on your website?
Uh, yes, lots of websites do. It used to work from Chrome on the desktop or laptop: Press the button, and (after asking for confirmation) your Android mobile phone would dial it. (That assumes that you have logged into Google on both devices.) Chrome since removed that functionality, who knows why, but it still works if you press the button on the phone's browser itself. I believe that it works on both Android and iOS.

You've been missing out by disabling Javascript!
> **TheFu said:**
> Is it a $15/minute number?
No, ha ha! That sort of thing is very uncommon here in the UK, and tightly regulated. Mine is just a normal landline. It saves the person from having to type the number on their phone: Just press a button and it dials.
> **TheFu said:**
> I really hate phones since I was on-call 24/7/365 for 5 yrs - not allowed to leave the city.
Oof, that sounds dire. I've been on 24-hour call at times in my life, but always for a restricted number of days. Once, I was extremely tired, and late that night, I woke up to realise that I was on the phone (this was in the days before mobile phones had been invented). The person who had called me was saying in a concerned voice, "Paddy, are you awake?" I wasn't awake up until that moment!
  > **TheFu said:**
> Text is even worse.
How do you cope in today's world?!

---

### Post by TheFu on 2024-01-04
> **Paddy Landau said:**
> Aargh! I meant to write "Javascript". I have no idea why I wrote "Java" and then failed to pick it up when proofreading.

It was Javascript, not Java, that I disabled.

I've made similar mistakes thousands of times here. I drop words or end ideas in the middle of a post all the time.

> **Paddy Landau said:**
> Uh, yes, lots of websites do. It used to work from Chrome on the desktop or laptop: Press the button, and (after asking for confirmation) your Android mobile phone would dial it. (That assumes that you have logged into Google on both devices.) Chrome since removed that functionality, who knows why, but it still works if you press the button on the phone's browser itself. I believe that it works on both Android and iOS.

The "tel:" URL works without javascript.  From what I've seen, javascript is abused about 85% of the time when it isn't necessary, even for websites that appear dynamic with a mouse-over toggle for each menu area using CSS.  It is only Ajax stuff that needs javascrript, IME.

> **Paddy Landau said:**
> You've been missing out by disabling Javascript!

Nope.  I don't have any FOMO here.  

> **Paddy Landau said:**
> 
No, ha ha! That sort of thing is very uncommon here in the UK, and tightly regulated. Mine is just a normal landline. It saves the person from having to type the number on their phone: Just press a button and it dials.

There's a URL - "tel:"  ...  just like the "mailto:"  URL.  These have been around since HTML2, I think. If someone needs to communicate with me and they aren't 1 of about 15 close family/friends, they can leave a message on the home phone or email or send a letter.  There's no other method.  I don't get texts. They are blocked.   It has caused issues for some contractors wanting to work with me.  They'd assume I had a cell phone number, which I don't.  I have a cell phone, but it is used as a small tablet, wifi controller, SIP phone and GPS.  It is not connected to a network very often, unless I'm traveling to somewhere I've never been before. Then I'll get a 7 day, $10, data-only, plan in the location.

> **Paddy Landau said:**
> 
Oof, that sounds dire. I've been on 24-hour call at times in my life, but always for a restricted number of days. Once, I was extremely tired, and late that night, I woke up to realise that I was on the phone (this was in the days before mobile phones had been invented). The person who had called me was saying in a concerned voice, "Paddy, are you awake?" I wasn't awake up until that moment!
  

I will never be on-call in that way again.  I had no replacement for those years, actually, until I forced it by leaving.  Nobody in my team had the same access levels I had for secure networks.  We all worked for different companies.  Lives were on the line.

> **Paddy Landau said:**
> 
How do you cope in today's world?!

I don't understand the question.  Cellphones and texting aren't a requirement for anything that I know about.

---

### Post by Paddy Landau on 2024-01-04
> **TheFu said:**
> The "tel:" URL works without javascript.
Ugh, of course, you are absolutely correct. I just didn't see it properly without the Javascript.

The system that I use is designed for people like me who need something to do the work on my behalf. The days of me programming websites is about 3 decades ago, and anyway I don't have the time. I think that that's why it uses Javascript. The site also uses Javascript to hide the email address from bots; without Javascript, the user has to go to the Contact page to find my telephone number, as the email address is hidden, and the contact form isn't displayed.
> **TheFu said:**
> I don't understand the question.  Cellphones and texting aren't a requirement for anything that I know about.
Ha ha, that's a lovely reply. I was thinking just the other day about how complex our lives have become, and how it would help people — and the planet — to revert to a simpler lifestyle. It sounds as though you've managed to do that pretty well!

---

### Post by TheFu on 2024-01-04
> **Paddy Landau said:**
>  Ha ha, that's a lovely reply. I was thinking just the other day about how complex our lives have become, and how it would help people — and the planet — to revert to a simpler lifestyle. It sounds as though you've managed to do that pretty well!
 
We certainly have lots of modern trappings, it is just that cell connectivity isn't one.

---

### Post by donald187 on 2024-01-05
> **TheFu said:**
> Just turn off all XSS everywhere and be done with it.  Any website that doesn't work without XSS off is one that home users don't need to visit.

If it is required for a work-related webapp, then you shouldn't be using any of your own equipment and the company is responsible for everything. If they allow it for any reason, including ignorance, it is their fault, not yours.

XSS has been a known attack vector for about 15 yrs. We have choice.  We don't need to accept defaults if we disagree with them. We don't have to use webapps that are security and/or privacy risks. We don't have to use programs that don't meet our security requirements. Sometimes I use lynx for browsing. Sometimes I will use a web-site cloning tool to grab a specific page I want from a website - outside using any browser.  We don't have to use javascript either.

These things are all our choices to make.  Nobody else can make them for us, at least at home. It is fine to disagree with others. We each have different needs.

So I decided to try out the Firefox add-on NoScript.  The ads didn't work on one site I frequent and I got a blank page on another site.  I realize I could make adjustments to get these to work like I would like.

Aside from that this is really more than I care to get into.  In the future if I install Ubuntu again I'm more likely to just install Chrome as it has the rapid updates.  Chromium was again three weeks out of date until just a couple of days ago.

But thanks!

---

### Post by TheFu on 2024-01-05
For sites you deem "good", enable javascript and allow it for the sub-pages you feel need it.  The settings will be remembered and you'll be fine for a few years.  Trustworthy websites running javascript is a much different thing than allowing random websites to run javascript.  

It is basically an "allow" when needed switch. If that is too difficult, fine.  My 80+ yr old mother was able to handle it.

Plus, nobody says you only need 1 browser for everything and that it 100% must be secure against every possible attacks.  I only use firefox for generally safe browsing of known websites.  For any unknown websites, I'll use a different browser that is running in a protected space, not allowed to touch the system it is running on.

BTW, Canonical has decided to handle some of this by forcing snap-package versions onto end-users.  I reject that.  Actually, I switched my desktop to a non-Ubuntu system primarily due to their forcing the use of snap packages with constraints I have no control over.  For me, those constraints are wrong and not sufficient to my needs. Sometimes I need less contraints and sometimes I need much more - "don't touch anything on the system" constraints. Snaps don't allow that.

For banking, I do much more security and NEVER use my daily use browser + configuration for banking or other financial websites.  I just don't.

---

### Post by donald187 on 2024-01-05
It's not too difficult.  I just don't care to do it.  But thanks.

---

### Post by Paddy Landau on 2024-01-06
> **TheFu said:**
> Snaps don't allow that.
That's the one big objection that I have with snap. Fortunately, flatpak does allow that.

---

### Post by donald187 on 2024-01-09
So I found something which although simplistic makes me feel better.  I was looking for something in the cve priorities which would match up with Alex Murray's statement in the second post about medium, low, and negligible cves having smaller effects (or other conditions).  In the cve priority definitions XSS is generally a medium cve.  But if one XSS matched the "real problem" and "exploitable in the default configuration" criteria it would be prioritized as high.  And there have been a couple of high XSS.  So if you have a medium XSS which can be exploited in the default configuration then it must not be a "real problem".  And so you have Alex Murray's smaller effect.

Good enough. :)

> 
[TABLE="class: table table-bordered table-hover key"]
[TR="class: medium"]
[TD="class: needed"]Medium[/TD]
[TD]   Open vulnerability that is a real problem and is exploitable for many users   of the affected software. Examples include network daemon denial of service,   cross-site scripting and gaining user privileges.[/TD]
[/TR]
[TR="class: high"]
[TD="class: needed"]High[/TD]
[TD]Open vulnerability that is a real problem and is exploitable for many users   in the default configuration of the affected software. Examples include   serious remote denial of service of the system, local root privilege   escalations or local data theft.[/TD]
[/TR]
[/TABLE]


[https://people.canonical.com/~ubuntu-security/priority.html](https://people.canonical.com/~ubuntu-security/priority.html)

---


---
title: "How many people here use NoScript Addon?"
date: 2012-05-24
forum: Security
---

### Post by listerdl on 2012-05-24
I did but I found it very annoying.

I mean it you literally cant visit any html page and when you do try and allow the page you have to keep allowing more and more code to be rendered....

Seems like a waste or am I missing the point?

---

### Post by Ms. Daisy on 2012-05-24
Kinda missing the point IMO.  When you're surfing new, untrusted sites you can temporarily allow scripts.

I presume you followed this:
[https://wiki.ubuntu.com/BasicSecurity/NoScript](https://wiki.ubuntu.com/BasicSecurity/NoScript)

There's a discussion on how to use NoScripts here:
[http://ubuntuforums.org/showthread.php?t=1905730](http://ubuntuforums.org/showthread.php?t=1905730)

---

### Post by wilee-nilee on 2012-05-24
> **listerdl said:**
> I did but I found it very annoying.

I mean it you literally cant visit any html page and when you do try and allow the page you have to keep allowing more and more code to be rendered....

Seems like a waste or am I missing the point?

The extra buttons needed to have per-session okay&#8217;s and back to block are in the right click on the browser panel customize.

You can set it to not pop-up so it will just show on the icon.

Excellent tool really.

Yes you are missing the point, lol. :)

---

### Post by OpSecShellshock on 2012-05-25
I use it and advocate its use. I know it's frustrating, especially at first. You can establish a fairly permanent whitelist of your most frequently visited and trusted sites and leave everything else default-blocked. It takes some work up front, but eventually becomes mostly invisible for most things.

For sites not frequently visited or just unknown, it's good to block scripts. A lot of sites are compromised and have scripts placed in their source that are invisible to people browsing the site. A lot of sites are just inelegant. There's no reason for them to be "designed" in such a complicated manner. And you know, there are many sites out there where you can get what you went to the page for without allowing their scripts to run at all. It might be kind of ugly though.

But we are more and more getting into situations where it's better to think of sites as hosting web applications, rather than just websites. In those cases, yes scripts need to be run. In my opinion there are too many places where an application is used but a page would do just fine. They unknowingly expose themselves and their users to unnecessary risks.

---

### Post by matt_symes on 2012-05-25
Hi

> I use it and advocate its use. I know it's frustrating, especially at first. You can establish a fairly permanent whitelist of your most frequently visited and trusted sites and leave everything else default-blocked. It takes some work up front, but eventually becomes mostly invisible for most things.

For sites not frequently visited or just unknown, it's good to block scripts. A lot of sites are compromised and have scripts placed in their source that are invisible to people browsing the site. A lot of sites are just inelegant. There's no reason for them to be "designed" in such a complicated manner. And you know, there are many sites out there where you can get what you went to the page for without allowing their scripts to run at all. It might be kind of ugly though.

But we are more and more getting into situations where it's better to think of sites as hosting web applications, rather than just websites. In those cases, yes scripts need to be run. In my opinion there are too many places where an application is used but a page would do just fine. They unknowingly expose themselves and their users to unnecessary risks.

^^^ This. A great post.

I use notscript in Chromium extensively and thinks it's an invaluable tool. 

I also disable cookies on almost every site i go to part from ones i know are safe. If the site needs cookies for me to access and is not a trusted site (because i have been not there before), then if i access the site, i will delete the cookie for that site after.

For web e-mail access (Yahoo and Gmail only), i use a dedicated Midori browser and they are they only two sites i visit with that browser.

Kind regards

---

### Post by kevdog on 2012-05-25
I use NoScript everyday with FF for several years.  Its a pain at first and takes awhile to customize it -- meaning you can selectively allow certain sites to run scripts.  Once you spend a month or too customizing what you want to allow I think its great.

---

### Post by CharlesA on 2012-05-25
I use NoScript all the time, allowing sites on a temporary basis is handy.

It was a pain in the butt at first, but now I know which sites get picky about what script to allow in order to view all the content.

---

### Post by Hungry Man on 2012-05-25
Never liked it. I used it back when I was on Firefox because it's basically the best way to be secure on that browser... but it was a pain and I'm glad I don't need it anymore.

edit: I see NotScripts mentioned. It's worth noting that NotScripts hasn't been updated in months (over a year I think) and doesn't use modern Chrome APIs. It's easily bypassed and doesn't have even close to as many features as NoScript. I suggest that you remove it and use ScriptNo instead. It's still not up to par with NoScript but at least it uses the WebRequest() API.

---

### Post by matt_symes on 2012-05-25
Hi

> edit: I see NotScripts mentioned. It's worth noting that NotScripts hasn't been updated in months (over a year I think) and doesn't use modern Chrome APIs. It's easily bypassed and doesn't have even close to as many features as NoScript. I suggest that you remove it and use ScriptNo instead. It's still not up to par with NoScript but at least it uses the WebRequest() API.

Thanks. Getting it now :D

Kind regards

---

### Post by hakermania on 2012-05-25
Well, I used to, but I found it a little too excessive.
Adblock does the trick to block whatever annoys me and I don't feel that NoScript protects me essentially.

---

### Post by zombifier25 on 2012-05-26
NoScript with "Allow scripts on all pages" still provides a great deal of protection against clickjacking, etc. So if you're not comfortable with enabling sites one by one, then go ahead with allowing all sites, but you'll still be safer without NoScript.

---

### Post by Soul-Sing on 2012-05-26
Not anymore. From no-script to Request Policy.(and quick java)

---

### Post by listerdl on 2012-05-26
I just find it annoying and I think I am missing the point....

I mean, I like the idea but its such a pain when you are for example filling in a web form that needs javascript and you have to re-do the whole thing...

*** I have a solution!!! ***

Set up a virtual box and if you are doing any sort of suspect or paranoid search or research or whatever that "worries" you about things like XSS Scripting ect then you should be cool...

my 2 cents....

---

### Post by sammiev on 2012-05-26
I use it all the time and Post#2 says it all. :)

---

### Post by Ms. Daisy on 2012-05-26
> **listerdl said:**
> I just find it annoying and I think I am missing the point....

I mean, I like the idea but its such a pain when you are for example filling in a web form that needs javascript and you have to re-do the whole thing...

*** I have a solution!!! ***

Set up a virtual box and if you are doing any sort of suspect or paranoid search or research or whatever that "worries" you about things like XSS Scripting ect then you should be cool...

my 2 cents....
No.  It would be really cool if it were that simple but it's not.  A virtual machine can experience the same script exploits as a host install.

---

### Post by CharlesA on 2012-05-27
> **Ms. Daisy said:**
> No.  It would be really cool if it were that simple but it's not.  A virtual machine can experience the same script exploits as a host install.
True. Snapshots can help, but you still would run into XSS and whatnot even on a VM.

---

### Post by dd76 on 2012-05-27
I have been using it for about a year and a half on windows and Ubuntu  and love it.  This was recommended by Blizzard when my WoW account was  hacked due to a keylogger program that was hiding on a wow armory  lookalike site.  The program takes some getting used to but once you  know what to allow it is very useful.  Also, it loves to block  advertising on some websites so when you play a video instead of a 30  sec  advertisement in between videos it just jumps to the next video.   This doesn't work on all sites.  For windows this program has become  almost indispensable spyware and adware have been greatly reduced.  For  some odd reason though it works more efficiently on Ubuntu than windows.

---

### Post by listerdl on 2012-05-27
> **CharlesA said:**
> True. Snapshots can help, but you still would run into XSS and whatnot even on a VM.

Right but at least you can delete the virtual machine if it did infect it?

I just need to get my head around NoScript....

---

### Post by Ms. Daisy on 2012-05-27
> **listerdl said:**
> Right but at least you can delete the virtual machine if it did infect it?

I just need to get my head around NoScript.... Yeah, if the script exploit installed something malicious.  

The thing about browser exploits is that some happen entirely inside the browser. So you could get your credentials stolen and someone would have your username & password to a login page.  Deleting the virtual machine does not change the fact that someone already got your credentials.  Hence a virtual machine is not a fail-safe.

---

### Post by Hungry Man on 2012-05-27
A virtual machine isn't really a security program. It is in that they're great for malware analysis but... none of it really improves security except for the fact that it's a separate system from your own. That's it. 

It's like a sandbox except it also virtualizes a new file system and kernel and performs CPU emulation. Huge resource hog and in the end it's just a big blob of complicated attack surface.

Being able to move back to a save state is great but I'd rather just use a something like Apparmor, which provides the same basic type of security without the massive resource usage.

---

### Post by chocklet on 2012-05-28
There's plenty of credible testimony and evidence that javascript is a serious problem at this time.

"JavaScript-based malware attacks have increased in recent years and currently represent a signicant threat to the use of desktop computers, smartphones, and tablets."
[http://research.microsoft.com/apps/pubs/default.aspx?id=162710](http://research.microsoft.com/apps/pubs/default.aspx?id=162710)

Multiple pieces of malware now exist in the wild that are taking advantage of Java vulnerabilities to install themselves as "drive-by downloads" with no user interaction required.
[http://www.reedcorner.net/guides/macvirus/](http://www.reedcorner.net/guides/macvirus/)

most sites are involved in risky behavior by leveraging third-party JavaScript
[http://www.devx.com/security/Article/45236/1954](http://www.devx.com/security/Article/45236/1954)

Noscript may not be only partially effective, but it is what we have.

I've been using it for years.  The small additional hassle is not a factor for me.

---

### Post by zombifier25 on 2012-05-29
> **chocklet said:**
> There's plenty of credible testimony and evidence that javascript is a serious problem at this time.

"JavaScript-based malware attacks have increased in recent years and currently represent a signicant threat to the use of desktop computers, smartphones, and tablets."
[http://research.microsoft.com/apps/pubs/default.aspx?id=162710](http://research.microsoft.com/apps/pubs/default.aspx?id=162710)

Multiple pieces of malware now exist in the wild that are taking advantage of Java vulnerabilities to install themselves as "drive-by downloads" with no user interaction required.
[http://www.reedcorner.net/guides/macvirus/](http://www.reedcorner.net/guides/macvirus/)

most sites are involved in risky behavior by leveraging third-party JavaScript
[http://www.devx.com/security/Article/45236/1954](http://www.devx.com/security/Article/45236/1954)

Noscript may not be only partially effective, but it is what we have.

I've been using it for years.  The small additional hassle is not a factor for me.

And let's not forget the recent JavaScript malware that infected over half a million Macs.

---

### Post by alelinuxbsd on 2012-05-29
I have made an attempt to use it on the past, but the customization is quite longer, so generally i use Adblock plus.

When i want more security i use the browser [xxxterm]("https://opensource.conformal.com/wiki/xxxterm") with a whitelist. 
The configuration is very easy is sufficient add a domain for the activity that you like as:
js
plugin
cookie
Even if isn't possible a fine regulation but only activate all things on a domain or nothing.

Anyway perhaps on future i will make another attempt on NoScript.

---

### Post by Hungry Man on 2012-05-29
> **zombifier25 said:**
> And let's not forget the recent JavaScript malware that infected over half a million Macs.

That was Java, not Javascript.

---


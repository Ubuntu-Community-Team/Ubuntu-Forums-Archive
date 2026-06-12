---
title: "Can webpages access files in Home directory?"
date: 2011-10-19
forum: Security
---

### Post by kliq on 2011-10-19
Hello

Is it possible, for instance, for a Javascript programme of a webpage that's being viewed in Firefox to access any files {or all of them even} in the same Home directory?
If so, then how would you grade the technical feasability?

---

### Post by dfarrell07 on 2011-10-24
I don't think so, but honestly I don't know much about this. Just browsing around, it seems like Firefox would have access to

> ~/.mozilla/firefox/1nnfru5g.default/Cache/*

And maybe some part of /tmp?

---

### Post by Lars Noodén on 2011-10-25
Take a look at the Apache module, [mod_userdir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html#userdir).  That will allow you to specify web-accessible directories within users' home directories.

---

### Post by daviest11 on 2011-10-25
Not sure if this is the type of thing you were thinking, but I use this...

[http://www.3open.org/d/pfn/pfn](http://www.3open.org/d/pfn/pfn)

It's a file browser implemented in PHP. It's a little clunky to use, but totally functional.

Tom

---

### Post by satanselbow on 2011-10-25
From which end or you asking the question? Concerned user or wannabe hacker?

Creating a file upload form (for example) is trivial - retaining a list of files in a folder and associating it to an IP address equally so ;)

---

### Post by bodhi.zazen on 2011-10-25
> **kliq said:**
> Hello

Is it possible, for instance, for a Javascript programme of a webpage that's being viewed in Firefox to access any files {or all of them even} in the same Home directory?
If so, then how would you grade the technical feasability?

It is possible for firefox to access any files the user you are running firefox has access to.

I found example of reading files with a simple google search.

This is why I use NoScript and Apparmor.

People often think of apparmor to restrict access to system files, which is valid, but user files, including things in .ssh and .gpg and elsewhere are equally important.

I use apparmor to restrict firefox to just a few directories in $HOME - .mozilla, Downloads, and Documents for example (not an exhaustive list).

---

### Post by SparTacux on 2011-10-26
I once had my bash history posted on a web forum :-)    I did a search of my computer name and log on name and found a tutorial using my bash history commands as an example - some nice guy taught me a lesson in internet security ;-)  Since then all documents go in a separate user desktop account with my email with no internet access allowed ( using a browser ) from that user account.  Default directory permissions of Ubuntu allow reading of ANY user home directory from another user account. Big Security issue imo and I change the default home directory permissions so that no-one else can read it. I'm presuming Firefox cannot now get to my documents even if apparmor is not being used.

---

### Post by Decaffienated46 on 2011-10-27
Your explanation re: 'Since then all documents go in a separate user desktop account with my email with no internet access allowed...' has me cornfused. Would you please elucidate for a NuB, please?
TIA

---

### Post by SparTacux on 2011-10-27
Simple - create a desktop user called internet which you use just for browsing the internet using firefox or whatever.(  Preferably a Chinese designed browser ;-) )  Store no personal documents in the home folder of user internet. 

Then create another desktop user called ( say johnDoe ) and use that for storing your personal documents. The Only internet access allowed from this account would be to access your email using Thunderbird or Evolution. Encrypt the home folder of this account and/or set directory permissions so that no other user can access this home directory. This would limit possible attack and exploits to just your email program.  Don't run any other internet based program from this account such as Rythmbox, etc as they could lead to exploits leaving your personal data compromised. 

When using Firefox from user 'internet' it should not be able to read the directory of user JohnDoe or get at his documents because the home directory is is encrypted and the default directory permissions have been changed so that no-one else can access it. 

That's the Theory
Still - better use NOSCRIPT and APPARMOR just to be sure ( some guys can't write secure software no matter how hard they try :-) )

---

### Post by SparTacux on 2011-10-27
Still - the best security is not to go on the internet at all.

I have a least two stand alone computers with no internet connections whatsoever. I use these for storing the most confidential and personal documents such as my Taliban contacts, my porn collection and my 10 most wanted list who I plan to assassinate ;-)

Come take me Spartans :-)

---

### Post by Ex-windows on 2011-10-27
> **bodhi.zazen said:**
> It is possible for firefox to access any files the user you are running firefox has access to.

I found example of reading files with a simple google search.

This is why I use NoScript and Apparmor.

I use apparmor to restrict firefox to just a few directories in $HOME - .mozilla, Downloads, and Documents for example (not an exhaustive list).  How can I access/ use Apparmor? I see it is already installed

---

### Post by Thewhistlingwind on 2011-10-27
> **bodhi.zazen said:**
> It is possible for firefox to access any files the user you are running firefox has access to.


It's a good thing I put down my beverage prior to reading that, or else I might have spit it all over the monitor.

Two things:

1. Users can read ANY other user's (besides root) home directory by default. Coupled with this you have a ridiculous vulnerability. 

2. For me, separate Internet account. Right. Now.

---

### Post by bodhi.zazen on 2011-10-28
> **Ex-windows said:**
> How can I access/ use Apparmor? I see it is already installed

see the apparmor sticky at the top of these forums

---

### Post by Dangertux on 2011-10-28
What is this...I don't ...even...know...

Yeah +1 to Apparmor , and to what TheWhistlingwind said about users and home directories.

The caveat is the encrypted home folder. Obviously if that user is not logged in the data will be encrypted.

Definitely implement Apparmor, and home folder encryption plus NoScript or NotScripts depending on your browser if you're concerned about this type of activity.

Hope this helps.

---

### Post by Ex-windows on 2011-10-28
> **bodhi.zazen said:**
> see the apparmor sticky at the top of these forums
 Oh, Duh lol,  I glanced at those and never noticed the fourth one...Thanx I am trying read it now, But I have heard that people have gotten lost in that "Terminal" But I shall be brave and venture forth. But if noone heaers from me in 3 days please send Coffee, food, and medical supplies lol lol :D :KS

---

### Post by bodhi.zazen on 2011-10-28
> **Ex-windows said:**
> Oh, Duh lol,  I glanced at those and never noticed the fourth one...Thanx I am trying read it now, But I have heard that people have gotten lost in that "Terminal" But I shall be brave and venture forth. But if noone heaers from me in 3 days please send Coffee, food, and medical supplies lol lol :D :KS

Opensuse has a graphical interface for apparmor, too bad it has never been ported to Ubuntu.

Fedora has a graphical interface for selinux.

There is a bit of a learning curve for apparmor, but, it is not too bad. 2-3 hours.

---

### Post by Lars Noodén on 2011-10-28
> **bodhi.zazen said:**
> There is a bit of a learning curve for apparmor, but, it is not too bad. 2-3 hours.

I found that systrace is much easier to use than AppArmor.  It's cross-platform, too.

---

### Post by SavageWolf on 2011-10-28
I really doubt that browser based JS has access to your files willy-nilly... That would be a critical security flaw... If you try to click a link like file:///etc/passwd, at least in Firefox and Chrome, the browser will refuse to follow it, so it's kinda hypocritical if they let JavaScript do it...

Yay! Paranoia!

---

### Post by Dangertux on 2011-10-28
> **SavageWolf said:**
> I really doubt that browser based JS has access to your files willy-nilly... That would be a critical security flaw... If you try to click a link like file:///etc/passwd, at least in Firefox and Chrome, the browser will refuse to follow it, so it's kinda hypocritical if they let JavaScript do it...

Yay! Paranoia!

The reason that it refuses to allow it is because of the same origin policy. 

If you notice you can open a new tab and type file:///etc/passwd and it will work just fine. That being said, if a web application can be XSS'ed and violate same origin policy the file can be read just fine by a javascript.

Hope that clarifies that a little bit better.

---

### Post by bodhi.zazen on 2011-10-28
> **SavageWolf said:**
> I really doubt that browser based JS has access to your files willy-nilly... That would be a critical security flaw... If you try to click a link like file:///etc/passwd, at least in Firefox and Chrome, the browser will refuse to follow it, so it's kinda hypocritical if they let JavaScript do it...

Yay! Paranoia!

Just to follow up on what Dangertux gave you,

If things are working normally, then there is no problem.

But every program has bugs, and some bugs can be leveraged as a vulnerability to do unexpected behavior.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

[http://www.ubuntu.com/usn/usn-1210-1/](http://www.ubuntu.com/usn/usn-1210-1/)

> An attacker could use these to possibly execute arbitrary code with the privileges of the user invoking Firefox.

What do you think "execute arbitrary code" means ? pwnage

You really need to match your level of security to the value of your data. Do not label the security concerns of another as "Paranoia" unless you first understand the value of the data and severity of threat.

From your posting style I assume you do not value your data, which is fine, but your approach to security would not apply to a more valuable target.

---

### Post by SavageWolf on 2011-10-28
Yes, there are security problems, but there is no need to create a snadboxed user account, and if there was, it'd be a better idea to use SetUID and setGID. That's actually a good idea... Hmm... But blocking all javascript access is a bit much. Also, bugs are fixed quickly, and AppArmour sets up a good system.

Saying that, how many of you have unblocked scripts and what not on sites like this and google? They are as big a target as any, due to adverts. Also, how many of you wear bullet and knife proof vests when going outside, or do you not value your life? And also, if security issues are so rampant, why isn't everyone using IE like dead or something?

---

### Post by OpSecShellshock on 2011-10-28
> **SavageWolf said:**
> Yes, there are security problems, but there is no need to create a snadboxed user account, and if there was, it'd be a better idea to use SetUID and setGID. That's actually a good idea... Hmm... But blocking all javascript access is a bit much. Also, bugs are fixed quickly, and AppArmour sets up a good system.

Saying that, how many of you have unblocked scripts and what not on sites like this and google? They are as big a target as any, due to adverts. Also, how many of you wear bullet and knife proof vests when going outside, or do you not value your life? And also, if security issues are so rampant, why isn't everyone using IE like dead or something?

Blocking javascript by default on all sites and then allowing where necessary has served me quite well (and made my browsing speedy!). Blocking ads is also a good idea. Sometimes I actually block all requests for third-party content entirely, even when it's just the content delivery network for a site I'm on. Makes a lot of pages look funny and a lot of images fail to show up. But I get what I'm after, so no big deal. Main thing is, this is my machine and I prefer to decide what runs on it and what doesn't. Different people have different thresholds. But it's good to be aware of what the browser is capable of.

---

### Post by bodhi.zazen on 2011-10-28
> **SavageWolf said:**
> And also, if security issues are so rampant, why isn't everyone using IE like dead or something?

The average half life of an unpatched default windows machine with an active internet connection is what - 78 minutes or less ?

[http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/](http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/)

I do not have better stats then that.

Update : [http://www.dshield.org/survivaltime.html](http://www.dshield.org/survivaltime.html)

The survival time for Unix is much better then windows.

---

### Post by Dangertux on 2011-10-28
> **SavageWolf said:**
> Yes, there are security problems, but there is no need to create a snadboxed user account, and if there was, it'd be a better idea to use SetUID and setGID. That's actually a good idea... Hmm... But blocking all javascript access is a bit much. Also, bugs are fixed quickly, and AppArmour sets up a good system.

Saying that, how many of you have unblocked scripts and what not on sites like this and google? They are as big a target as any, due to adverts. Also, how many of you wear bullet and knife proof vests when going outside, or do you not value your life? And also, if security issues are so rampant, why isn't everyone using IE like dead or something?

setuid and setgid + MAC is a recipe for a rooted box...Just letting you know ahead of time.

---

### Post by bodhi.zazen on 2011-10-28
This read may be of interest :

[http://www.redhat.com/f/pdf/security/RHEL4_RiskReport_6yr_wp_5732067_0311_ma_web.pdf](http://www.redhat.com/f/pdf/security/RHEL4_RiskReport_6yr_wp_5732067_0311_ma_web.pdf)

It is a 6 year security summary from RHEL, easy reading, but it shows the types of vulnerabilities seen over the 6 years.

Packages with the most exploits ?

#1 - Firefox
#2 - Seamonkey (also a mozilla package)
#3 - Thunderbird

#4 was the kernel.

---

### Post by Thewhistlingwind on 2011-10-28
> **Dangertux said:**
> setuid and setgid + MAC is a recipe for a rooted box...Just letting you know ahead of time.

I don't think he cares. :wink:

> **SavageWolf said:**
> Yes, there are security problems, but there is no need to create a snadboxed user account, and if there was, it'd be a better idea to use SetUID and setGID.

**I can't comment.**

 That's actually a good idea... Hmm... But blocking all javascript access is a bit much. Also, bugs are fixed quickly, and AppArmour sets up a good system.

**A MAC is always a good idea. That still doesn't mean you should just let your browser be swiss cheese. **

Saying that, how many of you have unblocked scripts and what not on sites like this and google?

**I have.**

 They are as big a target as any, due to adverts.

**I'm fairly sure theres a named logical fallacy for this. It goes something like "If you can't fix 100% of the problem, you should make no attempt at all."** **The truth of the matter is that scripts aren't desirable for me unless I want them. If that makes certain web pages ugly, so be it.**

 Also, how many of you wear bullet and knife proof vests when going outside, or do you not value your life? 

**At my current net worth, I can't afford an investment like that. Otherwise I would.**

And also, if security issues are so rampant, why isn't everyone using IE like dead or something?

**They usually are, if you look at the statistics for rooted desktops on the net, it's a little frightening.**



My response in bold.

---

### Post by bodhi.zazen on 2011-10-29
> **Thewhistlingwind said:**
> I don't think he cares. :wink:

Well, to be honest ...

The simple truth of the matter is that the majority of Ubuntu desktop users do not have a problem with intrusions. So the security that is in place is sufficient for most people.

Some people are not going to care until either have a high value asset they need to protect, or worse until they are cracked.

The analogy of a bullet proof vest is a good one. I would not wear it shopping, but it part of standard equipment in a military zone.

Once again, you have to match the security with the threat level.

This section is for people interested in learning security, don't wast your effort with those who are not interested.

---

### Post by Dangertux on 2011-10-29
> **bodhi.zazen said:**
> Well, to be honest ...

The simple truth of the matter is that the majority of Ubuntu desktop users do not have a problem with intrusions. So the security that is in place is sufficient for most people.

Some people are not going to care until either have a high value asset they need to protect, or worse until they are cracked.

The analogy of a bullet proof vest is a good one. I would not wear it shopping, but it part of standard equipment in a military zone.

Once again, you have to match the security with the threat level.

This section is for people interested in learning security, don't wast your effort with those who are not interested.

I agree with this with one caveat.

That those who have a decent tolerance for risk, and thus relatively low security but also exhibit high risk tendencies in their usage behaviors understand the risks.

What bothers me is those who want a decent modicum of security, but discount any real threats under some blanket marketing statement like "Linux is Secure".

That is where I have issues. If you want to cowboy it up and go crazy, hey it's your system your data be my guest. However, do not deceive people and say that it's all good. If people are asking due to a concern, they should be answered honestly with factual, actionable information not an opinion on the supposed security of a system.

Just my thought on the subject.

---

### Post by bodhi.zazen on 2011-10-29
> **Dangertux said:**
> However, do not deceive people and say that it's all good. If people are asking due to a concern, they should be answered honestly with factual, actionable information not an opinion on the supposed security of a system.

I never see anyone who I respect as knowing a thing or two about security advising an install it and forget it approach. The people I know and whose security advice I trust all advocate a more active stance.

But, security can easily feel overwhelming, so much so that people are inclined to give up.

I try to encourage them to get a start, somewhere ...

---

### Post by Thewhistlingwind on 2011-10-29
> **bodhi.zazen said:**
> 
This section is for people interested in learning security, don't wast your effort with those who are not interested.

I don't want anyone to take away rubbish like "Blocking flash, javascript, and company will not help in the slightest." from a security thread.

---

### Post by bodhi.zazen on 2011-10-29
> **Thewhistlingwind said:**
> I don't want anyone to take away rubbish like "Blocking flash, javascript, and company will not help in the slightest." from a security thread.

+1 , thank you for your diligence on that.

---

### Post by OpSecShellshock on 2011-10-29
Honestly, I don't know why we're stopping at home directory files.  Server-side code can access low level hardware functions through the  browser. Allowing the browser to make use of accelerated graphics does  it. So does allowing code on the web or a browser plugin to make use of  the camera (with or without turning the light on, no big deal). There  are scripts for getting network hardware information, disabling mouse  functions, disabling keyboard shortcuts, it goes on. Attached external  storage information? Oh, you bet.

Sometimes that stuff is fine, and is in fact exactly what users are  wanting. But I'm not sure people want just any site to be able to do it,  all the time. But how would they know when it's happening vs. when it's  not?

Yes, default-blocking matters.

---

### Post by Dangertux on 2011-10-29
> **OpSecShellshock said:**
> Honestly, I don't know why we're stopping at home directory files.  Server-side code can access low level hardware functions through the  browser. Allowing the browser to make use of accelerated graphics does  it. So does allowing code on the web or a browser plugin to make use of  the camera (with or without turning the light on, no big deal). There  are scripts for getting network hardware information, disabling mouse  functions, disabling keyboard shortcuts, it goes on. Attached external  storage information? Oh, you bet.

Sometimes that stuff is fine, and is in fact exactly what users are  wanting. But I'm not sure people want just any site to be able to do it,  all the time. But how would they know when it's happening vs. when it's  not?

Yes, default-blocking matters.

Exactly this. I couldn't agree more.

---

### Post by bodhi.zazen on 2011-10-29
> **OpSecShellshock said:**
> Honestly, I don't know why we're stopping at home directory files.

Well said. To answer that question I sort of see a 'Privacy' crowd. They value their personal data >> system data and often take a 'don't care' attitude to all the system files.

I answer that maintaining the integrity of system files is critical to maintaining privacy. I am sure you (and Dangertux and many others) understand this, but some of the privacy crowd does not 'get it'.

The other part is that sometimes tools such as selinux and apparmor are great at protecting system files, but do not protect $HOME. Personally I find the default firefox profile to be too lax in this regard, same could be said for selinux.

---

### Post by Dangertux on 2011-10-29
> **bodhi.zazen said:**
> Well said. To answer that question I sort of see a 'Privacy' crowd. They value their personal data >> system data and often take a 'don't care' attitude to all the system files.

I answer that maintaining the integrity of system files is critical to maintaining privacy. I am sure you (and Dangertux and many others) understand this, but some of the privacy crowd does not 'get it'.

The other part is that sometimes tools such as selinux and apparmor are great at protecting system files, but do not protect $HOME. Personally I find the default firefox profile to be too lax in this regard, same could be said for selinux.

Thankfully MAC like Apparmor or SELinux can pretty much be as flexible as the need (there are limitations), though I think you'd be hard pressed to find a situation where MAC could not at least give you some added security OR privacy.

---

### Post by kliq on 2011-10-29
Thank you everyone. I very much appreciate your interest in my post.

The reason why I asked it is because while I was waiting for a slow website to load, I was watching the URLs go by, down in the bottom left of the screen. 
Then in the middle of it all appeared one for a web page for the UK Met Office.
 At first I thought:  Hey - that's amazing. That's one of my favourites too .......... I wonder why it's theirs? - {Which was not a weather related site}.
 Then that slowly turned into: ............ erm, ........ is it? ............... could they have got that from my browser? ................ 

Well, You say: yes they could have. Although I'm still not sure about the degree of knowledge necessarily required to do so.
 So, if a web page can get to my Bookmarks then what about the file where my Logins and Passwords are stored,
 [from my replying Yes to whenever Firefox has asked me if I wanted it to save my Login details?] 
If the website copied that, then the snooper would be able to decode that information at their leisure; and I would have been unaware that anything had been taken.
 {I have now asked my bank to cancel my internet access, - permanently - and confirm it in writing - and they have.}

SparTacux. I like your idea about having an  account for Internet access only and turning off JavaScript;
 but surely that needs to be one for sites that do not require a Login and then a separate one for each site that does require a Login, all with their own copy of Firefox,
 since who's site can I trust? 
Maybe Banks - perhaps - but that's a mute point now.
 Not the government's {that I have a Login for} because they can do what they like anyway and always want to know everything anyway too.
 and arguably, not any other organisation either. 
Oh - and what about when I click on a link in an email {which will also be in its own account}?

However, if I do all that then do I still need Apparmor? What system files does a separate copy of Firefox in its own account need to have access to, to be able to run? 
Dangertux wrote: > setuid and setgid + MAC is a recipe for a rooted box...Just letting you know ahead of time.What is MAC? and what is a Rooted box?  


And what about Granny? She doesn't ever visit sites like this, and I'm quite sure that she does Internet banking; - Poor Granny.

---

### Post by Dangertux on 2011-10-29
MAC is Mandatory Access Controls , which is what Apparmor provides you. What I was referring to with the specific statement you quoted is under some conditions if you use SELinux or Apparmor to confine a setuid/setgid application successful exploitation of the application can actually leverage the presence of mandatory access controls to allow the attacker to obtain root privileges (hence a rooted box).

---

### Post by Thewhistlingwind on 2011-10-29
> **kliq said:**
> [SIZE=2]

However, if I do all that then do I still need Apparmor?

**Yes.**

 What system files does a separate copy of Firefox in its own account need to have access to, to be able to run?

**Your .mozilla is in your home directory. You can use separate profiles (Look these up) but for your purposes I'd say you'd need a separate user account for each of these, or a custom SELinux or Apparmor profile. (I haven't gotten into MAC's yet, but you can install a default profile, I don't think it will work for your approach however)**
 [/SIZE][SIZE=2]
Dangertux wrote: What is MAC? 

**A MAC (Mandatory Access Control) is a system that protects directories and files from unauthorized access, it's more flexible and powerful than POSIX permissions. It is a system independent of the root user, usually a kernel module. (Wikipedia: [http://en.wikipedia.org/wiki/Mandatory_access_control](http://en.wikipedia.org/wiki/Mandatory_access_control))**

[/SIZE][SIZE=2]and what is a Rooted box?  

**A "rooted" box is a computer where an intruder has gained the highest user permission level possible. This may or may not include control of the MAC.**
[/SIZE][SIZE=2]

And what about Granny? She doesn't ever visit sites like this, and I'm quite sure that she does Internet banking; - Poor Granny.

**9 times out of 10 granny has bigger problems.**

[/SIZE]

My responses in bold.

---

### Post by SparTacux on 2011-10-30
> **kliq said:**
> [SIZE=2]
SparTacux. I like your idea about having an  account for Internet access only and turning off JavaScript;[/SIZE] [SIZE=2]
 but surely that needs to be one for sites that do not require a Login and then a separate one for each site that does require a Login, all with their own copy of Firefox,
 since who's site can I trust? 
Maybe Banks - perhaps - but that's a mute point now.
 Not the government's {that I have a Login for} because they can do what they like anyway and always want to know everything anyway too.
 and arguably, not any other organisation either. 
Oh - and what about when I click on a link in an email {which will also be in its own account}?
[/SIZE][SIZE=2]
And what about Granny? She doesn't ever visit sites like this, and I'm quite sure that she does Internet banking; - Poor Granny.[/SIZE]

I use a separate internet account for browsing and a separate personal account for documents and email.  
I don't let firefox remember passwords and always enter them everytime I need them.

NOSCRIPT allows you to run or not run scripts on a site by site basis.
You could always have a second internet account just for banking/shopping use where money is involved. ( my wife's PC has this set-up to save her playing around with NOSCRIPT)

Oh and I never click on an email link from my main user account otherwise my browser would run which would defeat the purpose of having a separate internet user.


There are some pro hackers out there with access to major network infrastructure such as content providers, ISPs, telecoms companies, Governments, big internet companies, etc. It really depends on who you are up against. One 'rogue' employee at any of these institutions really could wreak havoc and I wouldn't fancy your chances if you get targeted even if using Linux.


Yup - Poor Granny is probably using Windows too - the mind boggles ;-)

---

### Post by kliq on 2011-10-30
OH NO !

Just I as I was looking forward to being safe to go back into the water, I find the following about AppArmor from [[COLOR=Red]here[/COLOR]]("http://en.wikipedia.org/wiki/Mandatory_access_control").

> SUSE Linux ... and Ubuntu 7.10 have added a MAC implementation called AppArmor. AppArmor utilizes a ... feature called LSM (Linux Security Modules interface).
 ......
Despite LSM being developed as a security API, LSM provides hooks that could be used by rootkits.Though it's better than nothing, of course.

---

### Post by Dangertux on 2011-10-30
> **kliq said:**
> OH NO !

Just I as I was looking forward to being safe to go back into the water, I find the following about AppArmor from [[COLOR=Red]here[/COLOR]]("http://en.wikipedia.org/wiki/Mandatory_access_control").

Though it's better than nothing, of course.


This is something similar to what I was eluding to earlier.

That being said, there is no catch all application. As much as Novell would love Apparmor to be it isn't either. 

The truth of the matter is Apparmor is not an excuse for bad security practices, however proper application of MAC can greatly add to the overall strength of a system's security.

---

### Post by jramshu on 2011-10-30
OP, referring to post #36, as far as sites knowing your favs.

Delete all cookies, browser history, cache, etc. What you are talking about sounds like tracking cookies, pretty common. Use the other methods mentioned, NoScript etc. and use the private browsing mode. Using pbm will help keep sites from storing cookies. The cookies banks and such usually use are session cookies and expire after logout. Some banks, such as mine, keep cookies on your machine to recognize the machine. When I delete my cookies the bank website makes me go through the whole "prove it's you" methods. Which through a good amount of recon some crackers could probably figure out. I just make up stuff for the security questions so they can't just go to any social network site and find.

The main thing is just smart browsing, look for mistakes on websites that 99.9% of legit sites won't make. Stay away from questionable sites, don't download stuff unless it's trusted, and so forth. 

There are so many ways to root a box it would take days to type it all out. Keep your box updated and keep your software updated. 

Then again, I may just be full of it. lol

---

### Post by c.cobb on 2011-11-01
> **jramshu said:**
> OP, referring to post #36, as far as sites knowing your favs.

Delete all cookies, browser history, cache, etc. What you are talking about sounds like tracking cookies, pretty common. Use the other methods mentioned, NoScript etc. and use the private browsing mode. Using pbm will help keep sites from storing cookies. 

Was the site one that uses Google's advert stuff? Another good add-on for FF is Better Privacy, as it deletes the LSO / Flash / Super cookies that sites can use to rebuild deleted HTTP cookies. Google stores two LSOs in your flash cache.

---


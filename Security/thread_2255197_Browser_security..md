---
title: "Browser security."
date: 2014-12-02
forum: Security
---

### Post by seabird22 on 2014-12-02
Here are some settings I have set  in my browser for increasing browser security. What would you add if anything? I am using chromium.


Content settings 
disable java 
disable ALL cookies
send &#8220;do not track&#8221; requests with your browsing data
enable phishing and malware protection


Extentions 
scrip safe addon  (defaults set)
ad block addon
history eraser app
https anywhere

---

### Post by Bucky Ball on 2014-12-02
I use NoScript, AdBlockPlus and duckduckgo.com as a search engine (it doesn't track you in the first place). Never had an issue. You must have some very good reasons for loading up with all that security stuff on a Linux box (Windows I can understand).

---

### Post by seabird22 on 2014-12-03
> **Bucky Ball said:**
> I use NoScript, AdBlockPlus and duckduckgo.com as a search engine (it doesn't track you in the first place). Never had an issue. You must have some very good reasons for loading up with all that security stuff on a Linux box (Windows I can understand).

for content settings, (e.g. java, cookies) I have whitelisted trusted sites, like ubuntuforums and others. My reason is just to be as secure as possible and to learn as much about security as I can. I Forgot, duckduckgo is my default search engine as well.

Why do people use apparmor, hids, snort, and other security measures in linux as outlined in the stickies?

---

### Post by open2reason on 2014-12-03
martin,
You might consider the addition of the Mozilla Firefox addon RequestPolicy, as it shows requests for access to other sites. Works in the same general fashion as NowScript in so far as a bit of a pain at first but once you have constructed your whitelists the you are left free to examine the (should be ) few few exceptions.

---

### Post by pfeiffep on 2014-12-03
I was a Chromium user until I discovered a security issue involving certificate revocation on both Chrome and Chromium. My [post]("http://ubuntuforums.org/showthread.php?t=2254159") explains it.

---

### Post by sammiev on 2014-12-03
Get rid of this "send &#8220;do not track&#8221; requests with your browsing data" when send it back they now know your computer is there.

---

### Post by pfeiffep on 2014-12-03
> **sammiev said:**
> Get rid of this "send “do not track” requests with your browsing data" when send it back they now know your computer is there.
My understanding of how a browser communicates requires the server knows that your computer exists and it's IP address. 
> [Do Not Track is a technology and policy proposal that enables users to  opt out of tracking by websites they do not visit, including analytics  services, advertising networks, and social platforms.]("http://donottrack.us/")
[Cookies]("https://www.eff.org/deeplinks/2009/09/new-cookie-technologies-harder-see-and-remove-wide") are also an integral part of web browsing. The cookies link explains the details. A more consice explanation can be found [here.]("http://www.allaboutcookies.org/cookies/cookies-the-same.html")

---

### Post by PondPuppy on 2014-12-03
For Firefox there are some settings in about:config which can be changed -- geo-location, HTML5 local storage (aka DOM storage), phone-home reports. Fingerprinting is interesting... using Chrome with no privacy safeguards on a Windows computer, the Panopticlick website reports

> [COLOR=#000000][FONT=lucida grande]Your browser fingerprint **appears to be unique** among the 4,754,171 tested so far.[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]Currently, we estimate that your browser has a fingerprint that conveys **at least 22.18 bits of identifying information.**

[FONT=Verdana]Using Firefox with Ghostery and NoScript on the same computer, Panopticlick reports

[/FONT][/FONT][/COLOR]> Within our dataset of several million visitors, only **one in 68,901 browsers have the same fingerprint as yours.**
Currently, we estimate that your browser has a fingerprint that conveys **16.07 bits of identifying information.**

All that said, concern for privacy in this realm is somewhat controversial.  Is it really important to hide as much information as possible?

---

### Post by seabird22 on 2014-12-03
> **PondPuppy said:**
> 

All that said, concern for privacy in this realm is somewhat controversial.  Is it really important to hide as much information as possible?
   
   The Idea of this thread was for me and others to learn about securing our browsers in hopes of adding another layer of security to our online experience. In today's day and age, with I.D. thieves, spammers, marketers, and other adversaries, attempting to probe our computers, I don't think that privacy concerns are controversial. They are real. Whether privacy concerns are warranted or not should be left for another thread frankly. If you can hide personal information from strangers why not? What reason would you have not to? Having said that, I do appreciate everyone who has contributed to this thread.

---

### Post by PondPuppy on 2014-12-03
> [COLOR=#000000]Whether privacy concerns are warranted or not should be left for another thread frankly.[/COLOR]

I agree. Completely. Subject dropped.

Personally, I use one browser configured for privacy and security, and another for specific sites which require the functionality of JavaScript, persistent cookies, and the like. 

Note that enabling phishing and malware protection means releasing data to a server using Google's Safe Browsing API. At least, I believe that's the case.  I opt out of that, preferring to use a sandbox for the secure browser to forestall attacks. And, of course, quite a lot of caution when browsing. 

A VPN would probably give more complete privacy; I believe there are some low-cost or even free ones. Though the latter might be relatively slow. I haven't taken that step myself yet.

---

### Post by open2reason on 2014-12-03
> Personally, I use one browser configured for privacy and security, and  another for specific sites which require the functionality of  JavaScript, persistent cookies, and the like. 
I too have several Firefox browser profiles ranging from shopping, banking sites that will not function without being allowed access to some functions right through to zipped up tight for general browsing. Paranoid? No, just careful.

---

### Post by seabird22 on 2014-12-04
> **PondPuppy said:**
> 

Note that enabling phishing and malware protection means releasing data to a server using Google's Safe Browsing API. At least, I believe that's the case.  I opt out of that, preferring to use a sandbox for the secure browser to forestall attacks. And, of course, quite a lot of caution when browsing. 

You mean confinement like apparmor?

---

### Post by seabird22 on 2014-12-04
> **open2reason said:**
> I too have several Firefox browser profiles ranging from shopping, banking sites that will not function without being allowed access to some functions right through to zipped up tight for general browsing. Paranoid? No, just careful.

With Chromium, there is a people menu with the ability to add another user. So that might work for me. I can probably set up two users with two completely different profiles.

---

### Post by cogset on 2014-12-05
>                               [INDENT]                                                                                                   [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **PondPuppy**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13179913#post13179913")                 

                 
Note that enabling phishing and malware protection means releasing data  to a server using Google's Safe Browsing API. At least, I believe that's  the case.  I opt out of that, preferring to use a sandbox for the  secure browser to forestall attacks.

                      
     
 
[/INDENT]



> **seabird22 said:**
> You mean confinement like apparmor?

I was going to ask the same question, which sandbox are we talking about?  I too thought about apparmor, although strictly speaking it isn't really a sandbox, as far as I can understand  it (which is not much,really).

---

### Post by vasa1 on 2014-12-05
> **seabird22 said:**
> ...
disable java 
...
or javascript?

---

### Post by PondPuppy on 2014-12-05
About sandboxes: I use a simple one called firejail. [http://freecode.com/projects/firejail](http://freecode.com/projects/firejail) 

An alternative is mBox, see this thread on HackerNews: [https://news.ycombinator.com/item?id=7214419](https://news.ycombinator.com/item?id=7214419) I've not tried it.

Probably a more skilled person than I would just set up seccomp themselves. 

I think that firejail does not do as thorough a job of isolating the client application as Sandboxie does for Windows. But it's convenient.

Part of these security measures are, for me, an exercise in pre-emptive measures. I don't think they're really necessary in Linux at this time, unless you're doing something very risky and know it. But I also have a sort of hunch that attacks will be increasing in scope and power over the next years, and I'd rather be well ahead of the curve than behind it.

---

### Post by seabird22 on 2014-12-05
> **PondPuppy said:**
>  But I also have a sort of hunch that attacks will be increasing in scope and power over the next years, and I'd rather be well ahead of the curve than behind it.Bingo!

---


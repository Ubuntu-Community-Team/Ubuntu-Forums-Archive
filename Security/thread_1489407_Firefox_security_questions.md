---
title: "Firefox security questions"
date: 2010-05-21
forum: Security
---

### Post by osomphane on 2010-05-21
So I downloaded a movie from megaupload and a pop up came up with[U] [http://watchinstantmoviesonline.blogspot.com/](http://watchinstantmoviesonline.blogspot.com/)
[/U]that bounced me to
[http://watchinstantmoviesonline.tk/](http://watchinstantmoviesonline.tk/)
but that webpage did not display. Normally, on Windows, I would have an anti-virus that would likely give me some sense of good or bad websites. On Ubuntu, I am not quite sure.

Do I need a malware scanner for the firefox browser? I have the standard package from the 10.04 distro with the latest updates...
[]("http://watchinstantmoviesonline.blogspot.com/")

---

### Post by Rubi1200 on 2010-05-21
Hi,
first of all, relax. There are no known Linux viruses "in the wild" and spyware/malware is also not an issue.
You do not need the kinds of security software that you did in Windows because Ubuntu is secure "out of the box."

What I can recommend, if you are concerned about browser security, is the following:

Install and use the Firefox addons NoScript and WOT (Web of Trust).

NoScript is used to prevent attacks via JavaScript and cross-site scripting (amongst other things) and WOT offers ratings for website safety (e.g. green is ok, red is bad etc).

I also suggest you read the security sticky written by bodhi.zazen for more general, as well as specific, information regarding security in Linux:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Most of all, use your commonsense; if something looks or feels odd, get out of there!

---

### Post by osomphane on 2010-05-21
The thing I am most worried about is a malware attaching itself to firefox and stealing online identities. Would that be possible, as I am not sure how much the windows and linux version share?

I am not worried about phishing attacks and the like.

---

### Post by OpSecShellshock on 2010-05-21
Most of the risk for identity/authentication credential theft by way of the browser involves phishing, password reset manipulation, or server-side breaches. That's true even on Windows, although Windows does have malware available that can perform those functions under the right circumstances.

If you're using Firefox on Ubuntu and you end up browsing to a page that you find suspicious you can usually go to Tools-->Clear Private Data, then when the dialog comes up you select "everything" from the drop-down, expand the arrow next to "details" and make sure all the boxes are checked. Then close the browser. You can set the preferences up so that this will happen every time you close Firefox, and that way all you have to do is close it (with the caveat that if you need to force quit for some reason that won't happen). In the event that doing that doesn't seem to solve the problem, back up your bookmarks and delete your profile.

There are some add-ons I'd recommend that will reduce the need for doing this:

**NoScript** will disable scripting unless you otherwise allow it.
**CSLite** will reject cookies unless you allow them, and you can set exactly how you want to allow them to operate. This will protect you from CSRF.
**BetterPrivacy** will allow you to delete flash cookies, which are traditionally stored in a different place, are persistent, allow sites to see each other's cookies, and allow sites to replace their own cookies if deleted. Those cookies are outside the scope of the browser's built-in cookie deletion (by design, I'd imagine).
**RefControl** allows you to strip referrer headers from your http requests. This is useful because a lot of web-based malicious scripts check to see that you're coming from specific locations (like Google search results pages) prior to running. However, by default this add-on is set to do everything normally, so you have to set it up to remove the referrer. It might break some legitimate uses, but you can allow exceptions.

Another thing to consider is that a lot of malware is multi-stage. Part of it involves a script that's rendered by the browser, but the really harmful stuff like the downloaders, droppers, info-stealers, and bots get brought in at later stages, and are still Windows-only. So even if the initial script successfully runs, the rest of it will fail.

---

### Post by osomphane on 2010-05-21
Good stuff to know, thanks guys :) The reason I was asking was that I heard about some vulnerability where hackers attach a java script to your browser session to get your passwords. From what I heard, I wouldn't be surprised if they used an invisible iframe or something like that...

---

### Post by bodhi.zazen on 2010-05-21
Indeed, browsers are one of the larger potential security holes on any OS. Things such as flash and javascript and xss are thus "cross platform".

There are potential security holes in firefox which allow one to run arbitrary code.

[http://www.ubuntu.com/usn/USN-921-1](http://www.ubuntu.com/usn/USN-921-1)

These kinds of security advisories are fairly common for firefox and I am personally looking into chromium as an alternate.

Search this page : [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

for firefox or xulrunner

I personally confine browsers w/ apparmor.

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

See also :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

---


---
title: "How Secure is Ubuntu/Firefox"
date: 2010-06-14
forum: Security
---

### Post by BobbyDing on 2010-06-14
Newbie here,
I'm thinking of moving mostly to linux to get away from the security holes in Windows. And I have some questions...
 
How secure is Firefox for doing online banking?
 
Sometimes I have run into a situation where the bank doesn't support anything but Windows explorer when accessing my accounts. Can this be gotten around safely in Linux?
 
If so, How?
 
Thanks!!
 
Bobby

---

### Post by aysiu on 2010-06-14
In theory, online banking is totally safe if you're using an updated web browser, logging into the actual bank's website (and not a phishing imitation), and your bank's server administrators are keeping it secure.

It really shouldn't matter whether you're using Windows or Ubuntu, or whether you're using Firefox or some other web browser.

If you're still paranoid about it, don't use online banking at all. Just do your banking in person.

By the way, if your bank doesn't support anything but Windows and Internet Explorer, how are you using it with Firefox and Ubuntu? User Agent Switcher?

---

### Post by Perkins on 2010-06-14
There are generally more security holes found in Firefox than in IE.  Obviously.  Firefox is open source, and anybody can scan the code looking for vulnerabilities.  Of course, said holes are (at least in the time I've been paying attention to such things) always patched before anyone malicious has enough time to make any significant use of them.  As opposed to Internet Explorer which has, on occasion, had known exploits go unpatched for many months.  (And, at least once that I know of, over a year.)

Pretty much the same thing can be said of open source operating systems as well.  There are practically no virii or worms for Linux.  One or two do, occasionally crop up.  They tend not to survive long in the wild.  Spyware is more possible, but it generally requires the user to be dumb enough to install it himself.  So as long as you don't execute code from untrusted sources, you should be good.  As always, beware of phishing scams.  (Make sure you're actually talking to your bank before entering any important information.)

So, basically, Windows or Linux can be equally safe for online banking as long as your machine hasn't been compromised by outside forces.  However, it is generally more difficult to compromise a default Linux installation than a default Windows installation, so you'll be marginally safer with the former.

What you need to do to access the "IE only" sections of your bank's website depends on why they're "IE only."  If it's simply because the bank's programmers are too lazy to test other browsers and don't want to field support calls when they don't work, then it's possible that all you'll have to do is tell Firefox to claim to be IE.  This used to be a nice, handy switch in the preferences dialog...  But it seems to have been removed for some reason.  It can still be done, but I'm afraid I'm not qualified to give instructions.  You'd be best off looking for a tutorial on the Firefox support site.

Unfortunately, Microsoft has never been big on following standards.  So it's also possible that the sections in question are restricted to IE because they make use of some "extensions" that only work in that particular browser.  The simple way to deal with this is to grab PlayOnLinux out of the repository.  It has a quick, clean installer for IE 6 and 7.  (Note:  To legally use this, you must, technically, have a properly licensed copy of Windows installed on the same machine.)  Of course, you are now running a browser that is known for security vulnerabilities inside your linux installation, with no easy way to update it...  Your system as a whole should be fairly safe given that it's running inside of Wine, and most of the code that an attacker could use an exploit to run simply won't work, but, to be safe, I would _only_ use IE to access your banking site.  I would also call up your bank and suggest to them that updating their software to not require a proprietary browser from one particular company is just a Good Idea in the long run.  It would really suck to have IE9 come out and break backward compatibility with the extensions in previous versions and leave their customers incapable of accessing their site...  If they target their site toward any standards-compliant browser, the odds of this happening drop to near zero.

If you want to be super, ultra paranoid, go get a distro like Puppy Linux and run it entirely off the CD without ever saving anything.  (You could use an Ubuntu live CD too, but Puppy is designed for this and will run faster.)  When you turn it off, anything bad that you've picked up goes bye-bye.  Along with any browsing history, saved passwords, or anything else that could be bad-news if your machine is stolen.  Probably overkill for most people, but it is, technically, safer.

---

### Post by bodhi.zazen on 2010-06-14
With internet banking you have 4 issues.

1. Your host (client) OS. Follow security security procedures, much of this is basic to any OS.

2. Your browser, firefox or otherwise. Keep your browser up to date. There are many reports of security holes on Firefox although I do not know of any such security flaw in firefox that has allowed people to obtain banking information.

Secure firefox : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

3. "The web" - there are a number of cross platform techniques such as Phishing

[http://en.wikipedia.org/wiki/Phishing](http://en.wikipedia.org/wiki/Phishing)

Phishing works with any browser.

See also XSS : [http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)

Also in this category is your network. Can somebody monitor your traffic (packet sniffing) ? You should always use https when connecting to your bank.

4. The bank's server. Obviously if your bank's server is compromised so is your account.

All I am saying is "firefox" or your browser is one of several factors and Phishing is more productive then cracking firefox.

In terms of IE compatibility, you can try this extension:

[https://addons.mozilla.org/en-US/firefox/addon/1419/](https://addons.mozilla.org/en-US/firefox/addon/1419/)

It also depends on why the banking site is IE only.

Personally, we have choice of banks and as much as possible I bank with institutions that are linux compatible, they are not *that* difficult to find.

---

### Post by yeleek on 2010-06-14
noscript extension is worth adding, it can be a pain, and i know the temptation of some is to enable all...

However I tend to only allow scripts for the urls i know, banks, online food shopping, etc etc.  The others address as and when.

The other good thing with noscript is it can detect common xss attacks
[http://noscript.net/](http://noscript.net/)
[http://noscript.net/features#xss](http://noscript.net/features#xss)

There are always risks, but if you are sensible, use an extension like noscript and a trusted network (so as to avoid things like sslstrip [http://www.thoughtcrime.org/software/sslstrip/](http://www.thoughtcrime.org/software/sslstrip/)) then there is no reason not to trust Ubuntu/Firefox combo.

---

### Post by anomie on 2010-06-14
[QUOTE=BobbyDing]Sometimes I have run into a situation where the bank doesn't support anything but Windows explorer when accessing my accounts. Can this be gotten around safely in Linux?[/QUOTE]

With respect, complain to your bank and/or start banking with someone who takes security seriously. 

A more drastic approach to secure online banking is dedicating a Linux system as your "financial-only workstation". (A live CD could also be used for this purpose, but it requires some expertise to personalize those.) On your financial-only workstation, no one does anything but log into a couple predefined banking sites. (You could enforce that, BTW.) No one cruises youtube, downloads movies or music, checks their personal webmail, etc.

---

### Post by BobbyDing on 2010-06-15
> **aysiu said:**
> By the way, if your bank doesn't support anything but Windows and Internet Explorer, how are you using it with Firefox and Ubuntu? User Agent Switcher?

I'm a newb to ubuntu, and haven't used ubuntu for accessing banking yet, my experiences were with Firefox running under windows. This was several months ago and at the time I just shrugged my shoulders and jumped back to IE. But now I want to start moving away from my windows dependency. I consider online banking to be my biggest windows dependency. Which is why I inquired here :)

Thanks all for the help!!! Very much appreciated!

Bobby

---

### Post by uRock on 2010-06-16
What bank doesn't allow browsers other than IE, so I can stay away from them? BofA and Wells Fargo allow any browser. Bodhi.zazen has already done a great job showing how to secure Firefox. I use adblock, NoScript, and AppArmor to secure my browser.

---

### Post by needhelppeeps on 2010-06-17
I just loaded NoSCript and set cookies to accept None (using exceptions)  What I am finding out is a lot of sites are requiring more scripting and cookies than what should be required. For example, one forum works just fine without cookies even being enabled and includes all the features like PMs and such.   Some news sites are completely broken unless 5+ sites are allowed to run all manner or scripting.   I am fine with a site using functionality that is needed, but I don't want to trust 5+ sites to watch one Flash news reel. This has been a real eye opener for me. The sites that are full of garbage I just won't use anymore.  I still do not trust 3rd party extensions and greatly wish this type of technology were built into the default firefox package even if it were disabled by default for less savy users.

---

### Post by yeleek on 2010-06-17
Yeah was an interesting eye opener for me too.  To be honest, I tend to look at the source of a site, see what site is hosting the flash movie (whatever) and just allow that site.  

The errors can get annoying, but you can also set them to disappear after a certain amount of time.

---

### Post by needhelppeeps on 2010-06-17
Hmmmm. Im looking at NOSCRIPTS. If you click to allow a site using  NOSCRIPTS, do those scripts have less restrictions than scripts that  would have normally been allowed to run in firefox? In otherwords, when I  whitelist something in NOSCRIPT, does it only have the same abilities  as the same script running in a firefox without NOSCRIPT.

---

### Post by bodhi.zazen on 2010-06-17
> **needhelppeeps said:**
> Hmmmm. Im looking at NOSCRIPTS. If you click to allow a site using  NOSCRIPTS, do those scripts have less restrictions than scripts that  would have normally been allowed to run in firefox? In otherwords, when I  whitelist something in NOSCRIPT, does it only have the same abilities  as the same script running in a firefox without NOSCRIPT.

yes

---

### Post by aysiu on 2010-06-17
> **needhelppeeps said:**
> Hmmmm. Im looking at NOSCRIPTS. If you click to allow a site using  NOSCRIPTS, do those scripts have less restrictions than scripts that  would have normally been allowed to run in firefox? In otherwords, when I  whitelist something in NOSCRIPT, does it only have the same abilities  as the same script running in a firefox without NOSCRIPT.
Yes. Once you whitelist something, that script is free to run as if you didn't have NoScript installed (but *only* that script and other ones you've whitelisted).

---

### Post by spiritofelric on 2010-06-17
Hi Bobby,

Sounds like you've already received allot of help here.  I'd like to add the simplified answer in addition to all this great help.
 
First thing is, all bank connections are done across an [encrypted protocol]("http://en.wikipedia.org/wiki/HTTP_Secure").  The URL should always show HTTPS.  Also, each browser has a graphic (usually a padlock) to show you're accessing across a secure connection.  Regardless of browser or OS, this will ensure the only weak points are between your keyboard and entering the data.  You can also check the strength of the encryption through your browser.
 
"Internet Explorer Only" should be due to the bank only wanting to support one browser.  You should be able to access your bank through other browsers masked as IE.  By no means should a bank use any browser feature not supported by the [WWW Consortium]("http://www.w3.org/").  IE only features such as Active X and Dynamic HTML are large security risks and should be questioned.  Personally, I would change banks if they demanded IE only.
 
In closing, you should be able to use your browser just as safely on Ubuntu as you could on Windows.  Though, keeping a record of your banking transactions is always good policy.
 
Hope that helps.

---


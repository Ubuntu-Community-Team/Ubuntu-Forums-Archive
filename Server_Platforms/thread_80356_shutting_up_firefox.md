---
title: "shutting up firefox"
date: 2005-10-22
forum: Server Platforms
---

### Post by towsonu2003 on 2005-10-22
I am trying to find some way to stop firefox giving out all that information about itself as well as the operating system. I would really prefer to let servers think that I am running windows, not linux. Any ideas how to shut firefox up (changing its headers)?
Currently, here is what it gives out: 


Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Connection: keep-alive
Host: [www.grc.com](www.grc.com)
Referer: [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)
Content-Length: 31
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Secure: [https://www.grc.com](https://www.grc.com)
Nonsecure: [http://www.grc.com](http://www.grc.com)

Thanks
PS. Yes, I am a newbie coming from windows :rolleyes:

---

### Post by BoyOfDestiny on 2005-10-22
Well this is probably overkill:

Privoxy is a web proxy with advanced filtering capabilities for protecting privacy, modifying web page content, managing cookies, controlling access, and removing ads, banners, pop-ups and other obnoxious Internet junk. Privoxy has a very flexible configuration and can be customized to suit individual needs and tastes. Privoxy has application for both stand-alone systems and multi-user networks.

[http://www.privoxy.org/](http://www.privoxy.org/)

I cannot surf the internet without it, whether on windows or linux (it's in the repos) Also it's GPL!

It lets you spoof the user agent (and also the referer tag, by default gives the page you are on, so it doesn't break sites htaccess rules)

If you are interested in web privacy this is it. Works with any browser as far as I know.

EDIT: This explains why firefox and other browsers spit this info out. [http://www.privoxy.org/3.0.3/user-manual/actions-file.html#HIDE-USER-AGENT](http://www.privoxy.org/3.0.3/user-manual/actions-file.html#HIDE-USER-AGENT)
Also, if you change the permissions, you can customize privoxy within the browser...So it makes it very easy!

---

### Post by aysiu on 2005-10-22
I don't know about tricking them into thinking you're on Windows, but you can identify as Internet Explorer with [the User Agent Switcher extension](https://addons.mozilla.org/extensions/moreinfo.php?id=59)

---

### Post by towsonu2003 on 2005-10-22
[QUOTE=BoyOfDestiny]Well this is probably overkill:

Privoxy is a web proxy with advanced filtering capabilities for protecting privacy, modifying web page content, managing cookies, controlling access, and removing ads, banners, pop-ups and other obnoxious Internet junk. Privoxy has a very flexible configuration and can be customized to suit individual needs and tastes. Privoxy has application for both stand-alone systems and multi-user networks.

[http://www.privoxy.org/](http://www.privoxy.org/)

I cannot surf the internet without it, whether on windows or linux (it's in the repos) Also it's GPL!

It lets you spoof the user agent (and also the referer tag, by default gives the page you are on, so it doesn't break sites htaccess rules)

If you are interested in web privacy this is it. Works with any browser as far as I know.

EDIT: This explains why firefox and other browsers spit this info out. [http://www.privoxy.org/3.0.3/user-manual/actions-file.html#HIDE-USER-AGENT](http://www.privoxy.org/3.0.3/user-manual/actions-file.html#HIDE-USER-AGENT)
Also, if you change the permissions, you can customize privoxy within the browser...So it makes it very easy![/QUOTE]

look nice, will give it a try after reading. thanks so much.

---

### Post by towsonu2003 on 2005-10-22
I tried privoxy, but I couldnot figure out to tweak it for the headers.

As for the user agent switcher extension, it works like I wanted. Here is my new headers:

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Connection: keep-alive
Host: [www.grc.com](www.grc.com)
Referer: [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
Content-Length: 31
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Secure: [https://www.grc.com](https://www.grc.com)
Nonsecure: [http://www.grc.com](http://www.grc.com)

thanks all for the help. I really enjoy this community.

---

### Post by ubuntu27 on 2005-10-25
Try Tor + Privoxy.  [http://tor.eff.org/index.html](http://tor.eff.org/index.html)

---

### Post by towsonu2003 on 2005-10-26
[QUOTE=ubuntu27]Try Tor + Privoxy.  [http://tor.eff.org/index.html](http://tor.eff.org/index.html)[/QUOTE]

Now this one looks impresive.

---

### Post by Jonne on 2005-10-26
May I know why you would want to do that?

---

### Post by Ride Jib on 2005-10-26
[QUOTE=Jonne]May I know why you would want to do that?[/QUOTE]

Everyone should want to. Protect yourself, and your privacy.

---

### Post by fannymites on 2005-10-26
I've used tor+privoxy on windows and linux and found it reduced my 2 meg broadband connection to dial-up speed.
So decide which you prefer, speed or privacy.  I chose speed.

---

### Post by Jonne on 2005-10-26
I like my privacy too, but cloaking your user agent doesn't help you a lot. All you do is make it yourself harder when surfing to sites that serve a different page based on the user agent. (yes, I know people that code their sites this way should be shot, but it's a reality).

What would anyone be with knowing you run firefox and ubuntu? The only thing the user agent is used for, is stats.

---

### Post by fannymites on 2005-10-26
I suppose it would help them decide which would be the best way to attack you or simply track which web sites you've visited recently etc.  Even if you use something to fake the browser headers etc, they still have your ip address, unless you use an anonymous proxy (like tor).
This firefox extension may be of interest.  Vbrowseit - [http://www.extensionsmirror.nl/index.php?showtopic=1978](http://www.extensionsmirror.nl/index.php?showtopic=1978)

---

### Post by towsonu2003 on 2005-10-26
[QUOTE=Jonne]May I know why you would want to do that?[/QUOTE]

You can't always browse on web sites that you trust...

"Cloaking" the user agent seems nice to me to avoid a potential attack from a site that specifically focuses on which browser I am using. I know this is not common (or, even, invented), but I like the sound of it. 

This proxying thing seems very impressive to me as I am a newbie to linux and don't really know the inner mechanisms. So it is very hard for me to think of ways that "malicious people" might jeopardize my system (ubuntu) or my privacy. In windows, it was very easy to figure out for me: your privacy is always in jeopardy. However in linux, I just don;t know. So when I enter a site I don;t trust, I want everything I can get for security.

---

### Post by blastus on 2005-10-26
Try this user agent :) 

User-Agent: Shadow Walker DKOM InjectionBot/1.0 (Sobig-F Mydoom.M SQLSlammer MSBlast Zotob.F...)

---

### Post by imagine on 2005-10-27
Just to change the user agent you don't need a proxy or an extension. Just put this in the "user.js" in your Firefox profile directory:
```
// Override the default user-agent string:
user_pref("general.useragent.override", "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)");
```
Or open about:config, create a key called "general.useragent.override" and give it the value you want. Works on the fly.


As a general note: This does not make your computer more secure. Security by obscurity doesn't exist.
It's the same sort of things as changing the default port of the SSH daemon, giving the Windows administrator account some obscure name, stopping the access point from sending out the SSID and countless other things. Just makes life harder but adds few to no additional security. If I think my SSH daemon is a weak spot in my system, then it's either configured wrong (read documentation), has known holes (update the software) or a weak password (change the password). Other than that it's secure. Changing the port to something else than 22 because my SSH daemon has some weaknesses is the wrong way of thinking. It can still be found by a simple portscan and additionally I have to specify the port everytime I want to connect to it.
Same is true for your user agent string. Can your computer be accessed from the internet (on all ports)? If so, is this necessary? Are there any daemons listening (all the time) for connections from outside? Are they needed, are there stong passwords, etc. Those are the questions which should be addressed and not "How do I give other computers the impression that my computer doesn't exist / is another computer".

When you secure a house you lock all the doors and windows or build a wall round it. You do not put a sign in front of it saying "There is no house".

---

### Post by towsonu2003 on 2005-10-27
[QUOTE=imagine]When you secure a house you lock all the doors and windows or build a wall round it. You do not put a sign in front of it saying "There is no house".[/QUOTE]

:D :) :KS 

Well this is very logical. and I keep learning, which is better. I'll definitely keep this in mind.

---

### Post by ubuntu27 on 2005-10-29
And, there is a thread for

[HOWTO: Surf and IM anonymously using tor and privoxy](http://ubuntuforums.org/showthread.php?t=10825)


Even though it is under Warty. I think it can work on Breezy also [I haven't tried it in Breezy yet]

---

### Post by tedrogers on 2007-02-15
I'd have to agree...all of these proxies spoil your speed big time.

I have a 10meg connection and if I use privoxy, tor or i2p (in particular) I may as well be on a 28.8 modem.

There is such a vast amount of info moving around on the net all the time and would probably be interpreted as normal activity...so don't you think that the fact you are concealing yourself might actually draw MORE attention to what you are doing?

---


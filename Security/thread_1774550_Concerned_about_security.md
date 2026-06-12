---
title: "Concerned about security"
date: 2011-06-03
forum: Security
---

### Post by harshisthere on 2011-06-03
I have some questions about security

1> are the flash exploits are of any use to a Linux operating system like Ubuntu etc. ?
2>are the Microsoft office exploits any risk to libreoffice or open-office software suites?
3>are there exploits for Linux , open-office and libreoffice ?

---

### Post by bodhi.zazen on 2011-06-03
There are no know active exploits, your system was patched to the known exploits long ago.

There are always vulnerabilities and if you are interested subscribe to any of the various security sites.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Again you need to understand the difference between a vulnerability and an exploit.

You should also read the security sticky and learn to use apparmor.

As long as your computer is turned on and connected to the internet you are in theory vulnerable, there is no such thing an an invulnerable OS. All you can do is educate yourself, as above, and keep your system up to date.

---

### Post by HermanAB on 2011-06-03
No not really.

Relax and enjoy your ubuntu system.

---

### Post by Lars Noodén on 2011-06-04
> **bodhi.zazen said:**
> 
Again you need to understand the difference between a vulnerability and an exploit.

There is also a time line of events, not in any particular order:  
[list]
[*]black hats discover vulnerability
[*]white hats discover vulnerability
[*]exploits available to black hats
[*]exploits available to white hats
[*]vulnerability made public
[*]vendor informed
[*]vendor acknowledges vulnerability
[*]vendor announces patch
[*]vendor publishes patch
[*]vendor publishes a patch that works
[*]exploits used manually
[*]exploits used by self-replicating tools
[/list]

So far Ubuntu has been doing rather well.

---

### Post by emiller12345 on 2011-06-04
> **Lars Noodén said:**
> 
[LIST]
[*]vendor publishes patch
[*]vendor publishes a patch that works
[/LIST]

That is really funny. Sad but true. 
You should maybe also add a 'vendor republishing patch'

---

### Post by sammiev on 2011-06-04
Linux security is rather very good as most hacks and so on are against the main OS like Windows. The only true 100% security is too keep your computer off the Internet. Been on Linux for sometime now and never had a virus/malware to date. GL :)

---

### Post by Thewhistlingwind on 2011-06-04
I went through this sub-forum up to like the 100th page, three or four people were rooted, by leaving VNC on.

Your fine. If your worried though, noscript.

---

### Post by dFlyer on 2011-06-04
> **harshisthere said:**
> I have some questions about security

1> are the flash exploits are of any use to a Linux operating system like Ubuntu etc. ?
2>are the Microsoft office exploits any risk to libreoffice or open-office software suites?
3>are there exploits for Linux , open-office and libreoffice ?

I've been using linux since the mid 90's and I've never been hacked or had any virus. I don't run antivirus software, my wife does on her ubuntu. She has never had any problem either. Remember to update regularly and you should be ok.

---

### Post by Lars Noodén on 2011-06-05
> **emiller12345 said:**
> That is really funny. Sad but true. 
You should maybe also add a 'vendor republishing patch'

These also aren't very funny:
[list]
[*] vulnerability made public
[*] vendor informed
[*] vendor acknowledges vulnerability
[/list]

That's one of the reasons I moved to Free Software years ago and a big reason everyone else should, too.

---

### Post by kostkon on 2011-06-05
> **harshisthere said:**
> I have some questions about security

1> are the flash exploits are of any use to a Linux operating system like Ubuntu etc. ?
The flash exploits can affect Ubuntu, thus, make sure you are installing all the security updates available in your update manager asap.

---

### Post by Lars Noodén on 2011-06-05
> **kostkon said:**
> The flash exploits can affect Ubuntu, thus, make sure you are installing all the security updates available in your update manager asap.

Or better yet, discourage the use of Flash as a wrapper for video.  The only two things that does are add possible security problems and restrict the number of possible platforms supported to single digits.

---

### Post by Thewhistlingwind on 2011-06-05
> **Lars Noodén said:**
> Or better yet, discourage the use of Flash as a wrapper for video.  The only two things that does are add possible security problems and restrict the number of possible platforms supported to single digits.

Because all website maintainers are afraid of angering their plan9 userbase.;)

Like I said, noscript and move on.

---

### Post by Dry Lips on 2011-06-05
> **kostkon said:**
> The flash exploits can affect Ubuntu, thus, make sure you are installing all the security updates available in your update manager asap.

**Lars Noodén:**
>  			 		 	 	 Or better yet, discourage the use of Flash as a wrapper for video.   The only two things that does are add possible security problems and  restrict the number of possible platforms supported to single digits. 	

Could you guys elaborate a little? In what way is flash a security hazard when running Linux? Are we talking about flash-based malware here?

---

### Post by uRock on 2011-06-05
When it comes to worrying about flash vulnerabilities, I say, "[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") => no worries." Install the [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") add-on in Firefox and don't allow flash to run on pages, unless you trust the page's script.

---

### Post by Dry Lips on 2011-06-05
> **uRock said:**
> When it comes to worrying about flash vulnerabilities, I say, "[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") => no worries." Install the [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") add-on in Firefox and don't allow flash to run on pages, unless you trust the page's script.

I already run NoScript, and I think that we can't refer to this important 
add-on too often. ;)

But theoretically speaking, what harm could a malicious flash script do to a 
linux machine?

---

### Post by uRock on 2011-06-05
> **Dry Lips said:**
> I already run NoScript, and I think that we can't refer to this important 
add-on too often. ;)

But theoretically speaking, what harm could a malicious flash script do to a 
linux machine?

I don't think it can do much unless AppArmor has been unenforced and/or the browser is being run as root.

---


---
title: "Web browser dilemma... Please help!"
date: 2008-01-19
forum: The Cafe
---

### Post by SZF2001 on 2008-01-19
Alright, this is getting to the point of me pulling my hair off my head.

I like Firefox. Really, I do - but the default Firefox 2 build in Ubuntu crashes ALL THE TIME. When it tries to handle Flash, crash. When it tries to handle a few pictures, crash. One time I just went to Google.com and it crashed. Seriously, it's getting ridiculous. I remember the good 'ol Breezy days, that FF version never crashed...

Firefox does one thing I especially love - handle my content. When I want to make a .pls file open with Exaile, you can just tell it, or change your settings later. No hassle, no worry.

I can't stand the crashes. So I try Galeon - it's alright, and I can make it do what I want without crashing all the time... But I just CAN'T customize what the content does! I have the Xine plugin for Mozilla installed because of Real Audio files embedded onto the browser, but anytime I ask the browser to open up a .pls file it just assumes to go with the plugin rather than ask me first!

No problem, I thought - I installed Opera. Damn, this is a nice browser! I can tell it what I want, when I want, however I want, and it will handle all file types according to ME! But get this - embedding Flash makes grey boxes! I can't find the older package of Flash, and I can't seem to find a work around with this. Another ball buster.

I tried compiling Seamonkey. It won't remember my Profile preferences, starting with Default all the time and I HAVE to make a new Profile if I want to continue.

Tried installing IceWeasel. Holy crap.

All I'm looking for is a browser that won't crash (or won't crash too often, because seriously I have to use a Beta of Firefox 3 over a stable version of Firefox 2... SOMETHING ISN'T RIGHT HERE, DUDE), will do as I say with file types and not assume the plugin handles everything, and will actually run the plugins. Is this really that hard? I might even *gulp* go back to Netscape... :mad:

---

### Post by Redache on 2008-01-19
Netscape is dead :)

Try Epiphany. it's in the repo's and is technically Gnome's "default" browser. Might work for you.

---

### Post by init1 on 2008-01-19
Yeah, I'm a Debian Etch user most of the time and Iceweasel has about a 30% chance of crashing at any given page with flash in it. This was not acceptable to me, so I tried to fix it. None of the solutions I found worked, and I couldn't figure out how to get Flash working in Opera. I guess I'll try Epiphany, since I've heard such good things about it.

---

### Post by SunnyRabbiera on 2008-01-19
you can give konqueror a try.
as for you flash issues in opera, they can be fixed if you use opera beta:
[here]("http://www.opera.com/download/linux/?ver=9.50b")

it works well enough

---

### Post by kerry_s on 2008-01-19
have you tried-> [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes)

---

### Post by cb951303 on 2008-01-19
epiphany is really good

---

### Post by SZF2001 on 2008-01-19
> **SunnyRabbiera said:**
> you can give konqueror a try.
as for you flash issues in opera, they can be fixed if you use opera beta:
[here]("http://www.opera.com/download/linux/?ver=9.50b")

it works well enough

Konqueror is alright, except the plugins won't work, even if I direct them to where they are, /usr/lib/mozilla/plugins or wherever... I knew where they were but at the top of my head I can't remember the exact directory.

And that Opera fix seemed to do the trick! Now we just wait for crash results...

One thing, though - in Firefox I use DownloadHelper... is there a widget like this, or vaguely similar, or does the same thing? Sometimes I like to save embedded webpage music or a Youtube video and don't wanna go through the sites source... But if there isn't this still won't stop me from using the Opera beta. >:3 thanks alot for that fix btw.

---

### Post by kodak on 2008-01-19
You could switch to a RPM based distro until Hardy comes out


just a suggestion

---

### Post by SZF2001 on 2008-01-19
How would that help?

I gotta back all my stuff up, switch to something I don't know (as far as yum is concerned), and maybe Hardy won't even fix the problem.

---

### Post by SunnyRabbiera on 2008-01-20
> **SZF2001 said:**
> Konqueror is alright, except the plugins won't work, even if I direct them to where they are, /usr/lib/mozilla/plugins or wherever... I knew where they were but at the top of my head I can't remember the exact directory.

And that Opera fix seemed to do the trick! Now we just wait for crash results...

One thing, though - in Firefox I use DownloadHelper... is there a widget like this, or vaguely similar, or does the same thing? Sometimes I like to save embedded webpage music or a Youtube video and don't wanna go through the sites source... But if there isn't this still won't stop me from using the Opera beta. >:3 thanks alot for that fix btw.

well personally i find the opera beta to be surprisingly stable, I use it often and face little issues.

> **SZF2001 said:**
> How would that help?

I gotta back all my stuff up, switch to something I don't know (as far as yum is concerned), and maybe Hardy won't even fix the problem.


well who said you would have to use yum, mandriva does fine without it :D

---

### Post by init1 on 2008-01-20
> **kodak said:**
> You could switch to a RPM based distro until Hardy comes out


just a suggestion
Agreed, I've had less issues with Firefox crashing in Suse and Blag than in Etch.

---

### Post by SZF2001 on 2008-01-20
I'll consider the RPM structure once I can get my wireless card working on them... But it seems I've found my fix... So...

---

### Post by macogw on 2008-01-20
Have you tried installing firefox-3.0 from the repositories?

---

### Post by SZF2001 on 2008-01-20
Yup.

---

### Post by ice60 on 2008-01-20
the older flash has some security problems, so i'm using the lastest opera 9.5 beta with the lastest flash. i haven't had any problems with this opera beta, it's updated once a week, or so, and you can get it from here -
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

i wrote a thread about making opera better here, i don't know how useful it is to must people though??
[http://www.wilderssecurity.com/showthread.php?t=185624](http://www.wilderssecurity.com/showthread.php?t=185624)

---

### Post by Ebuntor on 2008-01-20
If you'd prefer to still use a Firefox-like browser you could try [Swiftweasel]("http://swiftweasel.tuxfamily.org/").

It's an optimized version of Iceweasel, a bit faster (on my pc) with a lot of bug fixes too. Most of the crashes you described have been fixed and as far as I can tell only the Youtube flash crash remains.

Swiftweasel has a repository or you can directly download debs from the site.

---

### Post by Gigamo on 2008-01-20
I have been really happy with Swiftweasel as well. Especially the trunk release.

---

### Post by ice60 on 2008-01-20
which version of firefox are you all using? i've got the lastest suse build - SUSE/2.0.0.11-3.1 Firefox/2.0.0.11 and it works fine! that's with suse though, not ubuntu.

---

### Post by Ebuntor on 2008-01-20
> **Gigamo said:**
> I have been really happy with Swiftweasel as well. Especially the trunk release.

Glad to hear I'm not the only one who uses Swiftweasel, I thought I was all alone on the boards. ;)

BTW, I love your sig. :)

---

### Post by Acglaphotis on 2008-01-20
Try the firefox alpha. It's really nice, and it almost never crashes for me,

---

### Post by Gigamo on 2008-01-20
> **Ebuntor said:**
> Glad to hear I'm not the only one who uses Swiftweasel, I thought I was all alone on the boards. ;)

BTW, I love your sig. :)

Thanks :D

Yeah its a pity not more people use it. It's really nice imo, makes firefox even better.

---

### Post by koleoptero on 2008-01-20
I guess I am the only one with no problems whatsoever with firefox or flash etc. :confused:

Epiphany is good, you should try it.

---

### Post by fuscia on 2008-01-20
i found youtube to crash firefox a lot less if i used it in only one tab.

---

### Post by billgoldberg on 2008-01-20
I also quit using firefox because of the flash-crashing all the time.

I now use epiphany, i haven't had a crash I can remember of.

However, I had to change my /etc/hosts file with some list ripped from the internet to replace add-block plus and enable the plugins for epiphany, but that's all.

I never touched firefox since.

---


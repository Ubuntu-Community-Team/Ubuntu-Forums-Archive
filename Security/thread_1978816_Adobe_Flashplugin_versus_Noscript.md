---
title: "Adobe Flashplugin versus Noscript"
date: 2012-05-12
forum: Security
---

### Post by v41 on 2012-05-12
I make use of the Noscript option to forbid adobe flash on untrusted sites.
So I was perturbed to find that the flashplugin process,

```
/usr/lib/firefox/plugin-container /usr/lib/adobe-flashplugin/libflashplayer.so -greomni /usr/lib/firefox/omni.ja 1234 true plugin
```and a flash cookie,

```
~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
```appear whenever I apply firefox -> tools -> clear recent history. This occurs even when browsing only a single untrusted website. It has only started happening fairly recently.

I'm wondering why clearing the firefox history spawns a flashplugin process, whether it can be prevented, and whether this is a bug?

---

### Post by v41 on 2012-05-13
Update:    Clearing firefox's history spawns the flash plugin process even when I explicitly disable flash in firefox -> tools -> addons -> plugins.

---

### Post by OpSecShellshock on 2012-05-13
> **v41 said:**
> Update:    Clearing firefox's history spawns the flash plugin process even when I explicitly disable flash in firefox -> tools -> addons -> plugins.

If you have another browser such as Chromium or some other application that uses Flash, it will write its Flash cookies to the same directory that Firefox does. Then when you go to clear out the Firefox history and cookies it will see the cookie or LSO in that directory no matter which other application caused it to be put there.

---

### Post by v41 on 2012-05-13
> **OpSecShellshock said:**
> If you have another browser such as Chromium or some other application that uses Flash, it will write its Flash cookies to the same directory that Firefox does. Then when you go to clear out the Firefox history and cookies it will see the cookie or LSO in that directory no matter which other application caused it to be put there.

The only browser installed is firefox.   Even if I purge the flash-cookie directory, ~/.macromedia, and delete the flashplugin process,  they are both recreated the instant I clear firefox's history.

---

### Post by kleenex on 2012-05-15
Hi, try to install [_BetterPrivacy_]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/") add-on's for Firefox, which *offers various ways to handle Flash-cookies set by Google, YouTube, Ebay and others...*. I use this add-on for a long time and it seems to works very well. BetterPrivacy offers interesting options e.g delete Flash cookies on application start or on Firefox exit etc.

---

### Post by computeratin on 2012-05-15
> **kleenex said:**
> Hi, try to install [_BetterPrivacy_]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/") add-on's for Firefox, which *offers various ways to handle Flash-cookies set by Google, YouTube, Ebay and others...*. I use this add-on for a long time and it seems to works very well. BetterPrivacy offers interesting options e.g delete Flash cookies on application start or on Firefox exit etc.
 
+1 Better Privacy
 
Also look in to [Request Policy]("https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/?src=ss") as a supplement to No Scripts.
 
And I've been reading lately about a new privacy threat called "ever cookies" or "super cookie" that write to a lot of places that cookies don't normally write to.
 
They are supposed to be very hard to block or remove. So far I've only found one tool claiming that it can handle super cookies: [Nevercookie.]("http://www.evercookiekiller.com/")
 
But, every time I try to install it I get error messages.

---

### Post by v41 on 2012-05-16
> **kleenex said:**
> Hi, try to install [_BetterPrivacy_]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/") add-on's for Firefox

Kleenex and computeratin,  thank you for suggesting the BetterPrivacy addon.  I should have mentioned at the outset that I'm using several privacy-related addons, including BetterPrivacy.  They are: AdblockPlus,  BetterPrivacy, FoundStone HTML5 Local Storage Explorer, NoScript, RequestPolicy and Sanitisminau.

It would be interesting to know whether this issue is affecting many people, or just me.  To see whether you are affected, try the following:

(1) While firefox is running, delete the contents of ~/.macromedia
(2) Clear firefox's history ( firefox -> tools -> clear recent history)
(3)  Check whether any files or directories have been created in ~/.macromedia.  If so, then you are affected.

---

### Post by computeratin on 2012-05-16
Congrats on having a clue about browser sec! (/no sarc)
 
Welcome to the latest privacy threat:
 
***_Evercookies:_***

[http://samy.pl/evercookie/](http://samy.pl/evercookie/)
 
[http://www.schneier.com/blog/archives/2010/09/evercookies.html](http://www.schneier.com/blog/archives/2010/09/evercookies.html)
 
[http://en.wikipedia.org/wiki/Evercookie](http://en.wikipedia.org/wiki/Evercookie)
 
[http://forums.pcworld.com/index.php?/topic/100455-how-to-delete-so-called-evercookies/](http://forums.pcworld.com/index.php?/topic/100455-how-to-delete-so-called-evercookies/)
 
[http://blogs.wsj.com/digits/2010/12/01/evercookies-and-fingerprinting-finding-fraudsters-tracking-consumers/](http://blogs.wsj.com/digits/2010/12/01/evercookies-and-fingerprinting-finding-fraudsters-tracking-consumers/)
 
So far I haven't figured out how to keep the bleeeeeeeeeeeeeeeeeeeeeeeeeep things out without breaking 98% of sites on the web.

---

### Post by kleenex on 2012-05-16
**computeratin** thanks for the info about Nevercookie, evercookie and so on, because it seems to be an interesting plug-ins. I will certainly try it.

---

### Post by computeratin on 2012-05-16
This is the first time in a while that I've had a chance to research this. It looks like enough progress has been made that people have figured out how to flush them at least. So that you can't be tracked across sessions. They still can't be blocked without messing up most web sites. (?)
 
Removal methods:
 
1) This one looks a little time consuming, but safe.
[FONT=Calibri][http://www.youtube.com/watch?v=U-WNkB_d8WU&feature=player_embedded](http://www.youtube.com/watch?v=U-WNkB_d8WU&feature=player_embedded)[/FONT]

[FONT=Calibri]2) This one is more automated. But I'm at work. I can't check if it's in the repos. And you know all of the warnings about software not in the repos and it may be dangerous.[/FONT]
[FONT=Calibri][http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)[/FONT]

[FONT=Calibri]3) I'm not sure what this does. I'm not sure if it's supposed to delete or block? But I found it in a few places. It may be dangerous:[/FONT]
[FONT=Calibri]javasc#ipt:ec.set('uid', 12345); (in your browser bar)[/FONT]

[FONT=Calibri]NOTE: I AM NOT AN EXPERT, GURU, PROGRAMMER OR CODER AND I AM NOT ADVOCATING THAT YOU INSTALL SOFTWARE FROM OUTSIDE THE REPOS OR PLUG IN CODE YOU DON'T UNDERSTAND. [/FONT]

[FONT=Calibri]THIS INFORMATION IS FOR RESEARCH PURPOSES ONLY!!! IF ANYTHING PRESENTED HERE IS ABOVE YOUR SKILL LEVEL THEN USE AT YOUR OWN RISK.[/FONT]

[FONT=Calibri]IN OTHER WORDS: IT'S NOT MY FAULT IF YOU BLOW UP YOUR INSTALL!!![/FONT]

[FONT=Calibri]Personally I will test all of this in a virtual machine that I use for nothing other than testing stuff like this.[/FONT]

---

### Post by OpSecShellshock on 2012-05-16
Yes, Bleachbit is in the repositories, and yes if you run it after every browser session it can be used to remove everything that was stored, cached, or otherwise placed in a browser's directory, and it can clear things left by Flash, and it can clear out the Java cache (if anyone uses that). Highly recommend it, especially after a Chromium session. Matter of fact it can clean up after any application that it lists. I do not recommend using the option to run it as root (separate launcher!) unless you know exactly what it's clearing out and whether you need it or not.

---

### Post by desertoasis on 2012-06-03
I installed Lucid Lynx, but am an "absolute beginner" to linux.  Got tired of Windows problems.   I've been using it for over a month and like it, BUT --

I installed No Script and I know it's in there, but I can't find it in a panel or any other place.  Occasionally I see it when videos or other websites come up.  So far as I know it's running, but I can't control it.  I used it when I did Windows, so I understand how to use it, but if you don't see the icon, well --- I've done a number of online searches about this problem, but have not found the answer.

Now I do run Firefox and have this plugin --
[Shockwave Flash]("http://www.adobe.com/go/getflashplayer")Shockwave Flash 11.2 r202 					 					11.2.202.0

So, is there a conflict?   Any help would be extremely appreciated. B-)

---


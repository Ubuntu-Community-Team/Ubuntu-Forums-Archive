---
title: "firefox 1.5 is crap!"
date: 2006-01-24
forum: The Cafe
---

### Post by jerome bettis on 2006-01-24
so i'm back to ubuntu here (awesome btw) and i installed firefox 1.5 the other day.  this thing locks up like windows 95, has anyone else been having lots of problems with it?

---

### Post by mstlyevil on 2006-01-24
[QUOTE=jerome bettis]so i'm back to ubuntu here (awesome btw) and i installed firefox 1.5 the other day.  this thing locks up like windows 95, has anyone else been having lots of problems with it?[/QUOTE]

I have been using it since it's release with no problems whatsoever. Pages load faster and my home page now displays properly. It could be a bad install or a conflict with the previous version if you did not uninstall it.

---

### Post by fuscia on 2006-01-24
no problems here. if it gets a little sluggish, i just switch to dillo until i calm down.

---

### Post by gonçalo on 2006-01-24
I feel the same for ff 1.0.7. I'll just wait for 2.0 to see if it's worth it.

---

### Post by majikstreet on 2006-01-24
no problems here.

---

### Post by BSDFreak on 2006-01-24
No problems with 1.5 in XP, FreeBSD or Ubuntu.

But 1.5 isn't in stable so either you're using Dapper which sucks right now or you are using Breezy with it and then it depends on how you installed it.

---

### Post by jerome bettis on 2006-01-24
yeah i'm using breezy, i installed it with that automatix program in the customization forum (again very awesome btw) ... that added all kinds of repositories and stuff, so maybe it got this version from some wacky repo i have no business using (after gentoo, all i want is my stuff to work right consistently)

it seems like opening windows causes the most problems, but it just freezes up at random a la windows 95 quite frequently.  i guess i'll do a dpkg --purge and remove those repositories and apt-get a good version.

---

### Post by Cap'n Refsmmat on 2006-01-24
There are rather nasty problems with Adblock and FF 1.5 right now, so I'd suggest you get Adblock Plus if that's your problem.

---

### Post by cjm5229 on 2006-01-24
I have 1.5 in Breezy and Dapper, the only problem I have is, once in awhile it will shut down when I close a page. but like everyone keeps saying it is still in the experimental stage in both systems, I have Session Saver enabled so when it crashes I just restart it.You could install Opera and use that until April, when the final Dapper is released.

---

### Post by DigitalDuality on 2006-01-24
[QUOTE=BSDFreak]No problems with 1.5 in XP, FreeBSD or Ubuntu.

But 1.5 isn't in stable so either you're using Dapper which sucks big hairy donkey balls right now or you are using Breezy with it and then it depends on how you installed it.[/QUOTE]


That's quite amazing.  1.5 for Macs and *nix seems to work fine from what i've seen, but FF 1.5 on Win (regardless of version) has a huge memory leak in it if you leave numerous tabs open for any considerable length of time.  A whole helluva lot of people have complained about it.

As for the original poster, FF works  fine for me.  The one that came with the install wasn't bad, but not fast enough.. i did a proper upgrade to FF (after doing an improper one btw) and it runs smooth as ever now.

---

### Post by drizek on 2006-01-24
i stopped using firefox several months ago. i use konqueror in kde, epiphany in gnome and opera in windows.

---

### Post by jdong on 2006-01-24
Remember that Dapper is an EXPERIMENTAL release right now, approximately the halfway mark for the release in April.

You should not expect Dapper to just be a Ubuntu with newer packages and cool new features that works 24/7/182.5 just like any other stable release. As a development release, work is always ongoing, not to mention mistakes and conflicts of work are pretty common, too.

If you cannot accept:
   * Some programs being unstable at the time.
   * your Ubuntu being broken to various degrees once every few upgrades, and needing to take time from other work to fix (or even reinstall) Ubuntu
   * Pulling in 100MB of updates on average per 24 hour period
   * Crayon drawn bootup splashes and other terrible attempts at humor ;)


you shouldn't be running a development release. However, if you have some extra space for a dual boot (or an extra PC), trying Dapper is pretty cool. Not only do you get to see what's coming up without waiting another 3 months, but you also can help out the distro by reporting bugs to Launchpad, because if you report it AFTER the release, often times it will not get fixed till the next release!

---

### Post by BSDFreak on 2006-01-25
[quote=DigitalDuality]That's quite amazing.  1.5 for Macs and *nix seems to work fine from what i've seen, but FF 1.5 on Win (regardless of version) has a huge memory leak in it if you leave numerous tabs open for any considerable length of time.  A whole helluva lot of people have complained about it.[/QUOTE]

Christ man, this "memory leak" has existed in ALL versions since it was called phoenix, it's not a memory leak, it's the caching subsystem doing it's job.

---

### Post by BSDFreak on 2006-01-25
[quote=jdong]Remember that Dapper is an EXPERIMENTAL release right now, approximately the halfway mark for the release in April.

You should not expect Dapper to just be a Ubuntu with newer packages and cool new features that works 24/7/182.5 just like any other stable release. As a development release, work is always ongoing, not to mention mistakes and conflicts of work are pretty common, too.

If you cannot accept:
   * Some programs being unstable at the time.
   * your Ubuntu being broken to various degrees once every few upgrades, and needing to take time from other work to fix (or even reinstall) Ubuntu
   * Pulling in 100MB of updates on average per 24 hour period
   * Crayon drawn bootup splashes and other terrible attempts at humor ;)


you shouldn't be running a development release. However, if you have some extra space for a dual boot (or an extra PC), trying Dapper is pretty cool. Not only do you get to see what's coming up without waiting another 3 months, but you also can help out the distro by reporting bugs to Launchpad, because if you report it AFTER the release, often times it will not get fixed till the next release![/quote]

Add "not being able to boot into x and not being able to boot period to that and i'll agree.

Don't run Dapper as your primary install, run the minimalistic install on it and keep it in a testing area and migrate when you find it stable enough, just don't be tempted to keep updating your now upgraded but stable install becaus when it's at it's most stable point the next batch of experimental are released into current and it breaks again.

I wanted to contribute some to Ubuntu but tracking Current in Ubuntu is a full time job so i won't be doing that except the bug reports.

---

### Post by manicka on 2006-01-25
[QUOTE=jerome bettis]so i'm back to ubuntu here (awesome btw) and i installed firefox 1.5 the other day.  this thing locks up like windows 95, has anyone else been having lots of problems with it?[/QUOTE]

Have you disabled ipv6?

---

### Post by drummer on 2006-01-25
I don't have major problems with FF 1.5, but a couple of times it has spontaneously quit, but then that has happened with other programs as well. But what's just annoying is that in FF 1.5 in both Ubuntu and Windows XP, sometimes when I control-click a link to open it in a new tab, the window switches from its maximised state to its unmaximised state. Has anyone else experienced this?? I have also experienced the memory leak I think in XP.. I had about 16 tabs open the other day, a few of which with lots of pictures and flash, and it stopped responding. I didn't see the leak in the task manager, but I will remember to have a look next time FF stops responding.

---

### Post by mohapi on 2006-01-25
Other than the occasional and otherwise expected crap-out, FF1.5 is working fine for me.

---

### Post by Lord Illidan on 2006-01-25
I had a similar problem with Firefox 1.5 and Breezy Badger. It was crashing on me every few minutes, so much that I was contemplating using Opera full time, which I normally hate.
The solution was to ditch scim and use xim... Also, I re-installed firefox as per the wiki, instead of the Automatix version. Now it seems to be rock solid, no problems, and faster than 1.07, thank Linus.

To use xim, install it from the repos, and launch firefox like this:

```
GTK_IM_MODULE=xim /opt/firefox/firefox %u
```

---

### Post by Jucato on 2006-01-25
the Automatix install of Firefox 1.5 works for me. No problems here, nothing abnormal happening. Except I wish that the next release would have better memory/resource management. Opera (which I tried and don't like) almost performs as well as Firefox, but with less strain on resources (comparing purely from KSysGuard). So until that day comes, I'm using Konqueror for a while...

---

### Post by kenweill on 2006-01-25
[QUOTE=mstlyevil]I have been using it since it's release with no problems whatsoever. Pages load faster and my home page now displays properly. It could be a bad install or a conflict with the previous version if you did not uninstall it.[/QUOTE]

"Your home page"
But not all. Try opening [www.2wire.com](www.2wire.com), it wont display properly. And still, there are alot of website that won't display properly with Firefox. But it works well with IE and Konqueror.

---

### Post by phanboy_iv on 2006-01-25
No problems here. 1.5 is much better that 1.0.7.

---

### Post by nandasunu on 2006-01-25
[QUOTE=kenweill]And still, there are alot of website that won't display properly with Firefox. But it works well with IE and Konqueror.[/QUOTE]

These are called badly coded sites. If the website is coded with standards it will display fine in firefox, not necessarily so with IE... 

Firefox 1.5 (Automatix install) is working fine for me... a lot better then 1.0.7

---

### Post by akurashy on 2006-01-25
i had a lot of problems with firefox 1.5 so much that i had to remove it manually and compile it again. and yes firefox 1.5 locks up way to much =/

---

### Post by mstlyevil on 2006-01-25
[QUOTE=kenweill]"Your home page"
But not all. Try opening [www.2wire.com](www.2wire.com), it wont display properly. And still, there are alot of website that won't display properly with Firefox. But it works well with IE and Konqueror.[/QUOTE]

Yes "My home page" which happens to be yahoo. The text did not display properly in FF 1.07. Firefox 1.5 fixed that problem and now the text displays the same as in IE. I just clicked the link you provided and everything displayed just fine for me. The flash worked and all the buttons and links worked. The pictures are displaying just fine also. Everything appeared to be in the order intended by the web master. I agree that there are still pages that will not display properly but that is not the fault of FF. A lot of pages are still coded for IE and are not coded in web standards. Also if you have a bad install or you are having a conflict somewhere, it could lead to instability and web pages not displaying properly. 1.5 in Ubuntu is working the same as 1.5 does in Windows XP on my computer.

---

### Post by ice60 on 2006-01-25
if you have a memory leak you could try changing the browser cache memory capacity. in earlier versions it helped fix leaks but i don't know about now. i made myself use Opera for a week about 6 months ago and it's one of the best things computer wise i've done, i still use it now :D 

i have no idea if this will help, but as far as i know there's no harm in trying because you can just change it back again if it doesn't help. but it's up to you what you do.

how to change "browser cache memory capacity"         
Step 1. Type about:config into Firefox's Address Bar and press Enter.

Step 2. cut and paste **browser.cache.memory.capacity** into the address bar, press enter

Step 3. double-click (or right-click and select Modify)  browser.cache.memory.capacity 

make a note of the default value, mine is 65536, then lower it to **16000** which represents 16 MB of RAM for the cache, or whatever value you want to try.   

Step 4. Click OK to close the dialog box, then close all instances of Firefox and restart it.



i read this this morning too - FirefoxMyths. it does seem like abit of an Opera fan, but if you haven't tried Opera for a while maybe you should if you are having problems with firefox. have you seen the thread where people name their top ten apps? everyone who uses Opera puts it first. i'll keep my mouth shut now.
[http://mywebpages.comcast.net/SupportCD/FirefoxMyths.html](http://mywebpages.comcast.net/SupportCD/FirefoxMyths.html)

---

### Post by Cap'n Refsmmat on 2006-01-25
[QUOTE=ice60]i read this this morning too - FirefoxMyths. it does seem like abit of an Opera fan, but if you haven't tried Opera for a while maybe you should if you are having problems with firefox. have you seen the thread where people name their top ten apps? everyone who uses Opera puts it first. i'll keep my mouth shut now.
[http://mywebpages.comcast.net/SupportCD/FirefoxMyths.html](http://mywebpages.comcast.net/SupportCD/FirefoxMyths.html)[/QUOTE]
Die stupid myths thing DIE!!!
[http://robert.accettura.com/archives/2005/12/19/firefox-myths/](http://robert.accettura.com/archives/2005/12/19/firefox-myths/)

---

### Post by Tichondrius on 2006-01-25
[QUOTE=jerome bettis]yeah i'm using breezy, i installed it with that automatix program in the customization forum (again very awesome btw) ... that added all kinds of repositories and stuff, so maybe it got this version from some wacky repo i have no business using (after gentoo, all i want is my stuff to work right consistently)

it seems like opening windows causes the most problems, but it just freezes up at random a la windows 95 quite frequently.  i guess i'll do a dpkg --purge and remove those repositories and apt-get a good version.[/QUOTE]


It works great for me and it's faster and than 1.0.7.  The best way to install it is to download it from mozilla.com and install under /opt/firefox and just launch it from there (you can add a launcher to your desktop and apps menu). Contrary to what many FF 1.5 installation guides say, it will very gracefully incorporate all your old setting and even prompt you to upgdate any extensions. As for plugins, you can use the same ones that the old firefox did by pointing the new FF plugins directory (/opt/firefox/plugins) to the old FF plugins directory (/usr/lib/mozilla-firefox/plugins). After the installation you will have all your plugins, extensions, bookmarks, and history fully instact.

FF 1.5 does have a few new bugs, such as a problem with reverse scrolling while trying to click a image link. It's minor but quite annoying. Anyone else notice that ?

---

### Post by ice60 on 2006-01-25
[QUOTE=Cap'n Refsmmat]Die stupid myths thing DIE!!!
[http://robert.accettura.com/archives/2005/12/19/firefox-myths/](http://robert.accettura.com/archives/2005/12/19/firefox-myths/)[/QUOTE]
oops, now you mention it i remember it says > and ActiveX arguably makes things more secure. roflmao
which shows the person doesn't know what they're talking about. oh well, i did my best, i did say i wouldn't go on about Opera so i'll leave it at that =; for Opera and maybe this [-o<  too. lol

---

### Post by ace2005 on 2006-01-25
> firefox 1.5 is crap!

I agree, after about 10 tabs it gets far too slow, especially when you have to minimize and maximize to other apps, it takes ages to come back up sometimes (relative to other apps), so i use opera

---

### Post by Jucato on 2006-01-25
I'm trying to use opera as well, but it's quite confusing for me at first because the interface is a bit confusing and quite different from other browsers (Ctrl+T doesn't open a new Tab, the Navigation buttons are below the tab buttons). But I guess like any other good thing, it takes time to learn, and a bit of tweaking. Wish that Opera (and Konqueror) would have a non-obstructive Find tool like Firefox soon. I might stick to Konqueror a bit coz it integrates well with KDE (KIO stuff).

P.S. ice60: i couldn't find browser.cache.memory.capacity, but only browser.cache.memory.enable (which is set to true). and browser.cache.disk.capacity (which i set to 5000). Maybe I have to manually edit some config files?

---

### Post by ace2005 on 2006-01-26
Well i think you sould get Opera 9 Preview 1

[http://snapshot.opera.com/unix/9.0-Preview-1/intel-linux/](http://snapshot.opera.com/unix/9.0-Preview-1/intel-linux/)

Opera has decided to change Ctrl+N for new tabs to Ctrl+T , which you'll like but i don't since i'm used to Ctrl+N for new tabs. In opera press the full stop button "." and a search box will pop up at the bottom left corner of the screen, just continue typing, i find it easier than Ctrl+F, and if i type ".kde" i will find KDE on this page, then press F3 to go to the next place where kde is. However in Opera 9, every "kde" on the page will be highlighted so you can see everything fast.

Oh and set Tools > Preferences > Advanced Tab > Shortcuts > Middle Click Options and set it to start panning

And you can also close tabs with a middle click, makes life easier, so you can get rid of the close boxes, which i find annoying

---

### Post by ice60 on 2006-01-26
[QUOTE=Fenyx]P.S. ice60: i couldn't find browser.cache.memory.capacity, but only browser.cache.memory.enable (which is set to true). and browser.cache.disk.capacity (which i set to 5000). Maybe I have to manually edit some config files?[/QUOTE]
hi, if you don't have browser.cache.memory.capacity you should definately try the tweak then, you can follow these instructions to enable browser.cache.memory.capacity:

Step 1. Type about:config into Firefox's Address Bar and press Enter.

Step 2. Right-click any row, then click New, Integer. Type or paste the following preference name into the dialog box that appears (this is a hidden preference that doesn't exist in the Configuration Console until you create it):

browser.cache.memory.capacity

Step 3. Click OK, then enter the following integer number into the next dialog box, representing 16 MB of RAM for the cache:

16000

Step 4. Click OK to close the dialog box, then close all instances of Firefox and restart it.

i got them from [here](http://wilderssecurity.com/showpost.php?p=411626&postcount=50) you could try the other tweaks too they really worked for me when i used them.

you can use this extension to tweak the network settings, but if you try the tweak in the next post you don't need it.
[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=327](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&id=327)

---

### Post by ice60 on 2006-01-26
to speed up firefox you can try this, go to - *
/home/**username**/.mozilla/firefox/2vxct6k8.default/
**[color=red]NOTE[/color]**  [color=blue]2vxct6k8[/color].default is random. back up user.js if you have it, if not create it and add this to it:

// Enable pipelining
user_pref("network.http.pipelining", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);

// Turn on timer-based reflow management
user_pref("content.notify.ontimer", true);

// Sets the allowed time between reflows in microseconds
user_pref("content.notify.interval", 750000);

user_pref("content.interrupt.parsing", true);
user_pref("content.max.tokenizing.time", 2250000);
user_pref("content.maxtextrun", 8191);
user_pref("content.switch.threshold", 750000);

// Set the number of reflows to do before waiting for the rest of the page to arrive
user_pref("content.notify.backoffcount", 5);

// Turn initial paint delay to
user_pref("nglayout.initialpaint.delay", 500);

// Set Maximum Connections Per Server
user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy",16);
user_pref("network.http.max-persistent-connections-per-server", 8);

save it and close, then restart firefox. if you don't like the changes either delete the user.js file you made or replace with the backup you made if you already had it. 

these setting really helped me when i used them, but it was a while ago now, so you'll just have to see if they help.

let me know if they help, and if the memory tweak helps too because i'll do a howto if they do. :)

* of course it's totally your responsibility, if something goes wrong i'll try and help but i'm not a firefox guru, i don't even use it!

---

### Post by kenweill on 2006-01-29
[QUOTE=mstlyevil]Yes "My home page" which happens to be yahoo. The text did not display properly in FF 1.07. Firefox 1.5 fixed that problem and now the text displays the same as in IE. I just clicked the link you provided and everything displayed just fine for me. The flash worked and all the buttons and links worked. The pictures are displaying just fine also. Everything appeared to be in the order intended by the web master. I agree that there are still pages that will not display properly but that is not the fault of FF. A lot of pages are still coded for IE and are not coded in web standards. Also if you have a bad install or you are having a conflict somewhere, it could lead to instability and web pages not displaying properly. 1.5 in Ubuntu is working the same as 1.5 does in Windows XP on my computer.[/QUOTE]

Still, it doesn't work for me. Im using Firefox 1.5, both on Ubuntu Breezy and Windows XP machines, the link displayed the same. The links located at the right side of the flash overlaps with the 3rd image below.

Well, Firefox should be able to display web pages properly, both standard and non-standard coded web page. Compatibility. But why does Konqueror displayed it properly(except the flash)? Theres no overlaping.

I have tried reporting this problem to Mozilla Firefox since Firefox 1.5RC1 was released. But still the same. I guess it has nothing to do with my machine.

---

### Post by mstlyevil on 2006-01-29
[QUOTE=kenweill]Still, it doesn't work for me. Im using Firefox 1.5, both on Ubuntu Breezy and Windows XP machines, the link displayed the same. The links located at the right side of the flash overlaps with the 3rd image below.

Well, Firefox should be able to display web pages properly, both standard and non-standard coded web page. Compatibility. But why does Konqueror displayed it properly(except the flash)? Theres no overlaping.

I have tried reporting this problem to Mozilla Firefox since Firefox 1.5RC1 was released. But still the same. I guess it has nothing to do with my machine.[/QUOTE]

It could also be a hardware issue on your computer. That is the funny thing about computers. One persons system will work flawlessly while the others has problems with the exact same program. Did you give Opera a try? It might work better for you than FF does.

---

### Post by Jucato on 2006-01-30
ice60: thanks for the tips! I'll try them out as soon as I get firefox and Opera reinstalled (had to reinstall kubuntu). But right now, I'm enjoying using Konqueror both as file manager and web browser at the same time, without switching apps. And I find the split view especially useful. Thanks again!

---

### Post by kenweill on 2006-01-30
[QUOTE=mstlyevil]It could also be a hardware issue on your computer. That is the funny thing about computers. One persons system will work flawlessly while the others has problems with the exact same program. Did you give Opera a try? It might work better for you than FF does.[/QUOTE]

Perhaps.
Heres my screenshot.

---

### Post by jerome bettis on 2006-01-30
damn i forgot about this haha

i turned off ipv6 and it seems to be behaving much better now. :cool:

---

### Post by mstlyevil on 2006-01-30
[QUOTE=kenweill]Perhaps.
Heres my screenshot.[/QUOTE]

I would be upset also if pages did not display properly. Here is a screenshot of my FF 1.5.

[ATTACH]5703[/ATTACH]

As you can see it displays properly for me. I still suggest you try Opera and see if it does not work better for you.

---

### Post by TechSonic on 2006-01-30
I got both Firefox 1.5 and Opera 8.51 installed (Thanks to Automatix) and I haven't seen a problem with either of them.  Well Opera still doesn't translate pages right and I've only actually used it once to see if it installed right.  It's a backup browser, if you will.


My Firefox is ugly >.< but then again, themes suck.

---

### Post by cjm5229 on 2006-01-31
So write your own themes. That's the beauty of Open Source. If you don't like it figure out how to change it.

---


---
title: "Anyone tried Midori (webkit based browser)?"
date: 2008-01-31
forum: The Cafe
---

### Post by orange2k on 2008-01-31
I`ve read some news about changes in the Gnome 2.22, and about the possibility to build Epiphany with Webkit engine instead of Gecko 1.8

I`m looking for a browser to replace FF2 and Epiphany in terms of the browser engine, so Ive found Midori...

As far as I know, Webkit is the browser engine upon which Apple`s browser Safari is running...

I haven`t tried it yet, so my question is about your experience with it...

---

### Post by kadath on 2008-01-31
I'm interested in Midori too. However, it's obviously too early in development to use full time at the moment. Also, I'm too hooked on certain extensions (like AdBlock Plus and NoScript) to leave them behind.

If Midori ever reaches beta, I'll definitely look closer at it.

---

### Post by Darkhack on 2008-01-31
I've used Midori and even offered to contribute patches and I created its entry on Wikipedia.  Right now Christian Dywan (the developer) is working on it solo, but he is doing an awesome job.

---

### Post by siddartha on 2009-02-08
Tried it and it's quite impressive. Glad to see an alternative to the Portable Internet Explorer or how some might call it - firefox.

---

### Post by Tim Sharitt on 2009-02-08
I tried it a while back. It was a bit rough and featureless for me, but looked good for an early version. I think it may show some promise for the future.

---

### Post by PurposeOfReason on 2009-02-08
It still has the problem with cookies, like all linux webkit browsers, but besides that it is simple and light. No addons or anything, but a good /etc/hosts is better than any adblock.

---

### Post by chucky chuckaluck on 2009-02-08
i don't get the fascination with webkit.

---

### Post by jrusso2 on 2009-02-08
Crashed a lot and I don't think it handled cookies either if I recall.

---

### Post by jrusso2 on 2009-02-08
> **orange2k said:**
> I`ve read some news about changes in the Gnome 2.22, and about the possibility to build Epiphany with Webkit engine instead of Gecko 1.8

I`m looking for a browser to replace FF2 and Epiphany in terms of the browser engine, so Ive found Midori...

As far as I know, Webkit is the browser engine upon which Apple`s browser Safari is running...

I haven`t tried it yet, so my question is about your experience with it...

Why not put the effort into making one really good webkit browser for Linux?

---

### Post by hanzomon4 on 2009-02-08
Wha... what? ^^^^

---

### Post by Sunflower1970 on 2009-02-08
Been trying it out on Arch. It's nice, fast, & will be awesome some day. Right now it crashes a bit too often for regular use. :(

---

### Post by DoubleClicker on 2009-02-09
> **PurposeOfReason said:**
> It still has the problem with cookies, like all linux webkit browsers, but besides that it is simple and light. No addons or anything, but a good /etc/hosts is better than any adblock.

if you get the latest build from the webkit-team on launchpag [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

then cookies will work.

for intrepid add: 

```
 deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) intrepid main
```
to your sources.list (or repositories in synaptic)

for hardy add:
```
 deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) hardy main
```

---

### Post by Rokurosv on 2009-02-09
I liked it, flash worked, it needs more time but I think it's usable.

---

### Post by crimesaucer on 2009-02-09
I built the Arch AUR package of "midori-git" with libwebkit-git and it worked pretty good: [http://aur.archlinux.org/packages.php?ID=14349](http://aur.archlinux.org/packages.php?ID=14349) (well, the latest version hasn't worked good for me)


Git version 20090116 was very stable with the flashplugin-64bit, and the only issues I had with it were that it would not keep the cookies for passwords and it didn't work with the 64 bit java jre plugin.


I also didn't like the way it downloads.... you have to either use a script with wget or install a download manager.


Webkit was alright, it passed the web standards test at 100%..... but it still showed some sites weirdly.


As for how fast it was..... I built 3 really fast browsers that week. They were:

Midori-git with libwebkit-git
Epiphany-webkit with libwebkit-git
Firefox 3.1b2-1-PGO (profile-guided optimized with custom C[XX]FLAGS and LDFLAGS)


They were all equally fast, but Epiphany's URL-searchbar would not work, and the jre64-plugin, extensions, and cookies did not work either.... Midori also had no cookies, extensions, or jre64-plugin.... 


Firefox 3.1b2 had everything work including all of my 3.0.5 Add-Ons. It still feels very fast and has been stable for a few weeks. I'm looking forward to the next 3.1b3 build.


(I also recently built the newer 20090204 git version of Midori and the 40654 version of webkitgtk-svn and they both broke and became totally unusable.)

---

### Post by adamlau on 2009-02-09
> **chucky chuckaluck said:**
> i don't get the fascination with webkit.
Both the rendering and scripting engines of WebKit are fast, fast, fast. Like crimesaucer above, I built both Midori and 3.1b2 PGO on Arch. Only I found Midori to render faster than 3.1b2 PGO overall.

---

### Post by billgoldberg on 2009-02-09
> **Sunflower1970 said:**
> Been trying it out on Arch. It's nice, fast, & will be awesome some day. Right now it crashes a bit too often for regular use. :(

I found out the same.

If it becomes stable I could see myself using it more.

---

### Post by Darkhack on 2009-02-09
The crashes primarily lie in the GTK+ port of WebKit.  I've found Midori itself to be a quality browser since 0.1.0 was released.  Sadly, WebKitGtk doesn't receive as much love as the other ports.

---

### Post by suoko on 2009-02-11
i'm now trying it to check media support i found in this page:
[http://webkit.org/blog/140/html5-media-support/](http://webkit.org/blog/140/html5-media-support/)
but it doesn't work

it looks like media support is disabled by default (read here [https://dev.mobileread.com/trac/webkitbrowser/browser/trunk/WebKit-r30377/configure.ac](https://dev.mobileread.com/trac/webkitbrowser/browser/trunk/WebKit-r30377/configure.ac))

html5 will trash flash & silverlight altogether so i guess we must test this browser a lot
it's just a bit unstable but it's very very very good !!!

---

### Post by crimesaucer on 2009-02-17
The Archlinux AUR package of Midori-git (with webkitgtk-svn) is starting to look really good. (still crashes too much for my #1 browser..... plus jre plugin not working correctly and no cookies saved)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-62-1.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-62.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-62.png)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-64-1.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-64.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-64.png)

---

### Post by ghindo on 2009-02-17
Midori is really light and really fast.  It's a bit unstable at the moment, but I can't wait to see where it goes.  Isn't Xfce incorportating Midori into their project?

---

### Post by crimesaucer on 2009-02-17
> **ghindo said:**
> Midori is really light and really fast.  It's a bit unstable at the moment, but I can't wait to see where it goes.

My Firefox 3.1b2-PGO is feeling just as fast..... but I hope midori will keep getting better.

---

### Post by deepclutch on 2009-02-17
why webkitgtk lacks fast development?I am sure epiphany browser can shift to webkit backend if such a fast development can be done with webkit Linux port.

---

### Post by crimesaucer on 2009-02-17
> **deepclutch said:**
> why webkitgtk lacks fast development?I am sure epiphany browser can shift to webkit backend if such a fast development can be done with webkit Linux port.

They have an Epiphany-webkit in Archlinux AUR..... but the Epiphany search feature in the Address Bar would not work when I built that package. Neither would the jre plugin or the extensions/userscripts.


I might try a newer version of it just to see if it's improved yet. I do know that Gnome has been saying that they were going to switch to webkit soon.....

EDIT: just built Epiphany-webkit and the search feature is still not working. It's very fast though.

---

### Post by DPic on 2009-06-15
I love Midori! It definitely beat Epiphany-wekit (and firefox) but i'd love to see a comparison between them. I also have chrome but i prefer to use a more gnome-friendly app so Midori has been my main browser for a while now. Using the version in the PPA is very nice =]

---

### Post by Wiebelhaus on 2009-06-15
> **Tim Sharitt said:**
> I tried it a while back. It was a bit rough and featureless for me, but looked good for an early version. I think it may show some promise for the future.

I agree and [Ubuntu Tweak]("http://ubuntu-tweak.com/") has the ability to add a repository for dev builds as well as crach reports to help with the development.


Also , ***_Stability is still lacking._*** Even Chrome is much more stable.

---

### Post by joey-elijah on 2009-06-15
> **Wiebelhaus said:**
> Also , ***_Stability is still lacking._*** Even Chrome is much more stable.

x again

Midori crashes more than paper airplanes. It's a shame, but it's been knocking around in such an instable form for so long - whilst remaining pretty featureless at the same time. I think the webkit epiphany holds more promise, tbh.

---

### Post by DPic on 2009-06-15
> **joey-elijah said:**
> x again

Midori crashes more than paper airplanes. It's a shame, but it's been knocking around in such an instable form for so long - whilst remaining pretty featureless at the same time. I think the webkit epiphany holds more promise, tbh.

Are you using the webkit and midori PPAs? They're very stable...

---

### Post by Jesus_Valdez on 2009-06-15
I love Midori, dont chrash as often as I read in the thread, the only complain I have  about it is the fact that sometimes takes litle to go back in the history.

---

### Post by andras artois on 2009-06-15
It's definetly going to be a good browser as long as it carrys on heading in the same direction as it is now. It's nice and lightweight, simple layout but it is featureless (firefox has some damn useful addons!). Would maybe be nice to see a few addons wrote for it such as adblock etc and to be REALLY customiseable (lot's of preferance options).

---

### Post by sertse on 2009-06-15
Adblock is already written. It just wasn't released in time for 1.7

---

### Post by cKGunslinger on 2009-06-21
Used it for ~5 minutes (0.1.4).  I tried to go to [www.google.com](www.google.com) 7 times.  It completely crashed (jsut exited) 4 of those 7 times.  2 times it tooks ~90s to even resolve the DNS entry (could be my system/config, but the 4-5 other browsers I experiment with did not have this problem.)

So, 1 time out of 7 it managed to successfully bring up google in less than a minute without crashing. But at least it's fast.  :)

I'll stick with Opera 10 Beta for now, but hopefully Midori comes along a bit faster.

---

### Post by DPic on 2009-06-21
> **cKGunslinger said:**
> Used it for ~5 minutes (0.1.4).  I tried to go to [www.google.com](www.google.com) 7 times.  It completely crashed (jsut exited) 4 of those 7 times.  2 times it tooks ~90s to even resolve the DNS entry (could be my system/config, but the 4-5 other browsers I experiment with did not have this problem.)

So, 1 time out of 7 it managed to successfully bring up google in less than a minute without crashing. But at least it's fast.  :)

I'll stick with Opera 10 Beta for now, but hopefully Midori comes along a bit faster.

Don't complain if you're not using the most updated version using the Midori and WebKit PPAs.

---

### Post by Mark76 on 2009-06-21
Currently using it as my default browser. It crashes occasionally, but at least I haven't lost all my cookies yet (something that happens with alarming regularity whenever I give Kazehakase a go).

---

### Post by ashwinhgtx on 2009-06-26
I'm using Midori 0.1.2 right now. It's very unstable right now but it's improving a lot after every update. I'm looking forward to this browser. Rendering speed is awesome due to WebKit.
Any developers out there with free time please see if you can help Christian Dywan, the only guy working on Midori.

---

### Post by steeleyuk on 2009-06-26
0.1.7 is the latest available from the PPA. Its much more stable than previous versions and its updated every couple of days.

---

### Post by racoq on 2009-06-26
> **steeleyuk said:**
> 0.1.7 is the latest available from the PPA. Its much more stable than previous versions and its updated every couple of days.

I would like to test the latest version, but still i don't understand why the Hardy version of midori is not updated to 0.1.7. 

Is that such a difficult task to acomplish?

---

### Post by sertse on 2009-06-26
Not worth commenting unless you're on something relatively new. It has rapidly changed in the last couple of revisions. 0.1.7 is pretty stable. Anyways if past trends were to go by 0.1.8 will be out by the end of the month?

As for back porting, general rule is that packages don't get upgraded except for crucial security/bug fixes.

---

### Post by nortexoid on 2009-06-28
I've been trying out 1.7 and actually it's been very stable and the feature set is quite good in comparison with Epiphany (gecko). One thing I tried to add were the Ad Block FiltersetP user style and script for ad blocking, but it doesn't appear to work. They show up ticked in the side panel, but ads still appear. And Epiphany, I believe, uses the exact same script as a plug in, but it WORKS. Anybody get it working? I know I could go proxy for ad blocking, but it seems like too much to figure out for my lazy ***.

What's needed: password management; full popular website support (e.g. gmail won't display the labs calendar side panel--help?); better plug in support; performance improvements (it seems slow compared to Epiphany gecko! But maybe that's because ad block isn't working).

Otherwise I like Midori. On my system it actually seems to be MORE stable than epiphany-gecko (which I just can't use anymore).

---

### Post by Mark76 on 2009-06-28
Mine's been rendering this site weird.

As you can see

---

### Post by sertse on 2009-07-20
Bump ;)

New version is out!

[http://www.twotoasts.de/index.php?/archives/19-Menubarless,-extended-and-also-on-Windows.html](http://www.twotoasts.de/index.php?/archives/19-Menubarless,-extended-and-also-on-Windows.html)

Get it on Ubuntu at

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa) , remember to also add the webkit ppa  at [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by DPic on 2009-07-20
> **sertse said:**
> Bump ;)

New version is out!

[http://www.twotoasts.de/index.php?/archives/19-Menubarless,-extended-and-also-on-Windows.html](http://www.twotoasts.de/index.php?/archives/19-Menubarless,-extended-and-also-on-Windows.html)

Get it on Ubuntu at

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa) , remember to also add the webkit ppa  at [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

Awesome!! Midori is now on Windows too! xD

---

### Post by Jesus_Valdez on 2009-07-20
After I put a couple of scripts it started to crash every now and then, I'll remove them and see how goes from there, but overall I'm very happy about it.

I really like how there's a menu with your bookmarks on every new tab.

---

### Post by DarkReaper79 on 2009-07-22
trying it out now. Looks like currently no import bookmarks, or Im I just missing it?

---

### Post by Dullstar on 2009-07-23
I swear I read somewhere that Microsoft wanted to dump Windows after 7 or 8 and create an OS called Midori.  I'd take this information with a grain of salt though, since I haven't seen many details.

---

### Post by Exershio on 2009-07-23
> **Dullstar said:**
> I swear I read somewhere that Microsoft wanted to dump Windows after 7 or 8 and create an OS called Midori.  I'd take this information with a grain of salt though, since I haven't seen many details.

[http://en.wikipedia.org/wiki/Midori_%28operating_system%29](http://en.wikipedia.org/wiki/Midori_%28operating_system%29)

Midori seems to be a pretty popular word.

---

### Post by ghindo on 2009-07-23
> **Exershio said:**
> Midori seems to be a pretty popular word.Japanese for "green"?  You betcha.

---

### Post by ghindo on 2009-08-01
Midori 0.1.9 is out!

[http://www.twotoasts.de/index.php?/archives/20-The-hated-popup,-javascript-issues-and-tab-panel-improvements.html](http://www.twotoasts.de/index.php?/archives/20-The-hated-popup,-javascript-issues-and-tab-panel-improvements.html)

Get it in the Midori PPA:

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

Also remember to add the WebKit PPA:

[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by MasterNetra on 2009-08-01
I thought Midori has been a around for a while? Anywho it works, at a bare minimal. But sense it apparently isn't a finished product I'll hold of on ripping at it.

---

### Post by Jesus_Valdez on 2009-08-01
> **ghindo said:**
> Midori 0.1.9 is out!

[http://www.twotoasts.de/index.php?/archives/20-The-hated-popup,-javascript-issues-and-tab-panel-improvements.html](http://www.twotoasts.de/index.php?/archives/20-The-hated-popup,-javascript-issues-and-tab-panel-improvements.html)

Get it in the Midori PPA:

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

Also remember to add the WebKit PPA:

[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)
I've just update it.

Still no hotmail, and I'm guessing that the bookmarks at  the bar adress on new windows are gone for good.

---

### Post by sertse on 2009-08-04
Umm, anyone use spellcheck with midori? When you try to correct a misspelled word with one of its suggestions, do you find that it simply deletes the word instead of correcting it?

Just wondering if it was just me.

---

### Post by decoherence on 2009-08-04
I've been using Midori on and off.

Also check out Arora, the Qt4-based equivalent.

I like both 'em both. Fast, accurate browsing on low-end computers.

---

### Post by sertse on 2009-09-11
New Version is out!

Annoucment/Tarballs at [http://www.twotoasts.de](http://www.twotoasts.de)

Key feature: IT SUPPORTS EASYLIST now!!! Easylist is the filter list of Adblock Plus. However that requires the latest webkit, which even in the PPA only karmic has.
 
Try it by adding these PPAs. Instructions to do soare in the links.

Webkit: [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

Midori: [https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

Note: At time of posting the ppa hasn't caught up yet. In fact you probably don't want to use it right now (last development version removed cookie support, it was fixed for final). The PPA will probably update itself to final in a day or two though =)

---

### Post by dragos240 on 2009-09-11
I am using midori with awesome wm right now.

---

### Post by NormanFLinux on 2009-09-11
There is Arora,which is also a browser built on the Webkit engine. Light and fast.

---

### Post by RabbitWho on 2009-09-11
used it on spri,tis fine. :)

---

### Post by Jesus_Valdez on 2009-09-11
Oh my cookies are back.

Happy times!

I was starting to annoy me the lack of cookies for the forum.

---

### Post by Mark76 on 2009-09-12
There's no way to edit bookmarks :shock:

---

### Post by sertse on 2009-09-12
> **sertse said:**
> 
(last development version removed cookie support, it was fixed for final). The PPA will probably update itself to final in a day or two though =)

This the PPA has now fixed this. Enjoy! 

Bookmarks is still quite basic yea, you can manually edit it in the config text file. Hopefully they'll focus on that in the next version. Midori overall has come a long  way though.

---

### Post by sertse on 2009-10-16
MIdori 0.20 is out! Weeeee

Adblock works properly now, for everyone - See my screenshot with Easylist (The list used in Adblock in Firefox) set up. New Features include DNS Prefetching (Try it, might make your pages load faster...I think Chromium has it by default, it's a firefox tweak)  and Form Filling.

Get it using the Webkit and Midori PPAs and follow the instructions

[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

Midori by default is set to use it's own user agent, which in a perfect world where standards are always followed, would be fine. For best results, select Safari as your user agent in your preferences - See screenshot.

My screenshots only look scary because I hide everything btw :P

---

### Post by Mark76 on 2009-10-16
Can anyone duplicate this screenshot?

---

### Post by FootySr on 2009-11-02
I'm using 0.1.9 from the Software Center and I'm interested enough to want to give the newest version a go. That said... can anyone give me some intallation infomation for 0.2.0?

Thanks!  :)

---

### Post by sertse on 2009-11-02
When I thought people would would at least look at the replies immediately above them ;)

Look two posts up. 2nd last post in the previous page.

---

### Post by FootySr on 2009-11-03
> **sertse said:**
> When I thought people would would at least look at the replies immediately above them ;)

Look two posts up. 2nd last post in the previous page.

Yeah so? I saw that but I'm not Batman! I need someone to hold my hand. ;)

I don't have enough Ubuntu under my belt and the process is just a little cryptic for me.

I'll ponder at those 2 links a bit though and look into it. 

It's not just the install but the un-install if I need to, in the future, drop in the next release. I'll need to research that a bit too.

Thank You. :D

---

### Post by Praxicoide on 2009-11-03
If you are on Karmic, then in a terminal type:

sudo add-apt-repository ppa:midori

and

sudo add-apt-repository ppa:webkit-team

Followed by 

sudo apt-get update
sudo apt-get upgrade

---

### Post by FootySr on 2009-11-03
> **Praxicoide said:**
> If you are on Karmic, then in a terminal type:

sudo add-apt-repository ppa:midori

and

sudo add-apt-repository ppa:webkit-team

Followed by 

sudo apt-get update
sudo apt-get upgrade

Thank you! I assume I should un-install the one I got from the Software Center first? 

How would I un-install this 0.2.0 version if needed?

---

### Post by nortexoid on 2009-11-03
You don't need to uninstall anything as the "sudo apt-get upgrade" command will update your old version to the newest one.

---

### Post by Praxicoide on 2009-11-03
> **FootySr said:**
> 

How would I un-install this 0.2.0 version if needed?

You would need to comment out the two ppas, update your sources, and then reinstall midori (and maybe webkit, I don't know).

---

### Post by MikeCyber on 2012-08-02
Very fast, but it doesn't save passwords? Any help with that? I know of a solution using gnome keyring which I don't want to use.

---

### Post by Elfy on 2012-08-02
Try a support question.

As it is, this really old and tired thread is now asleep again.

---


---
title: "Shiretoko Still? WTF!?"
date: 2009-08-27
forum: The Cafe
---

### Post by moore.bryan on 2009-08-27
[FONT=Courier New]|-----------------------------------------|
| WARNING: This may be considered a rant. |
|-----------------------------------------|

[FONT=Tahoma]Many threads have discussed this topic, but I need a better answer than what has been given thus far.

Firefox 3.5.* was/is codenamed *Shiretoko*; I have no problem with that. When Firefox 3.5 was *not* the stable release from Mozilla, using the codename branding made sense. However, *now* 3.5.2 *is* the stable release, but Ubuntu's repos still have it titled/branded as *Shiretoko. Shouldn't *it take-over the place of Firefox (3.0.13)? 
[/FONT][/FONT]

---

### Post by kpkeerthi on 2009-08-27
> Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available. 

... from [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by moore.bryan on 2009-08-27
Thanks, kpkeerthi; that's actually the best attempt at an answer I've read, but I don't know if it applies to Firefox. I have *many* programs installed which were one version in Jaunty when it was a released and the most current now... And I'm not just talking about small, security fixes.

---

### Post by kpkeerthi on 2009-08-27
You might have installed the updated versions from unofficial sources (PPAs, getdeb etc.), may be? :)

---

### Post by moore.bryan on 2009-08-27
Nope and *that's* why I'm so confused/frustrated.

---

### Post by Giant Speck on 2009-08-27
The default version of Firefox in Ubuntu is the only version given the name Firefox.

The default version of Firefox in Ubuntu is 3.0.x, not 3.5.x.  Firefox 3.5.x will remain Shiretoko until the next release of Ubuntu in October, and only *then* will it become known as Firefox, because *then* it will become the default version of Firefox in Ubuntu.

---

### Post by Tibuda on 2009-08-27
> **moore.bryan said:**
> Shouldn't it take-over the place of Firefox (3.0.13)?
Karmic: Yes, it is already there.
Jaunty: No.

---

### Post by hal10000 on 2009-08-27
You may change /usr/bin/firefox-3.5 to be your default browser. I don' know where to find this setting in Xubuntu, but in KDE it can be found in [COLOR="Red"]System-Settings ---> default applications ---> Web-Browser[/COLOR].

---

### Post by sports fan Matt on 2009-08-27
Why not use the script from ubuntuzilla's official page on sourceforge.net?[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by calrogman on 2009-08-27
Oh no!  How will I live without *branding*?

---

### Post by FuturePilot on 2009-08-27
[Why is my Firefox 3.5 still called Shiretoko?]("http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html")

---

### Post by r-mo on 2009-08-27
The branding doesn't matter too much to me (although I did change the icon).  The only real problem was the user agent string being Shiretoko stopped things like facebook chat from working properly.  So I just went into about:config and changed general.useragent.extra.firefox from Shiretoko/3.5.2 to Firefox/3.5.2 and things are working fine now.

---

### Post by moore.bryan on 2009-08-27
Thanks for all the info, folks. The ubuntuzilla script never worked right for me, so I've dumped it. It's not the branding, it's the getting used to gnome-do-ing *shiretoko* instead of *firefox*. Unnecessary PITA.

---

### Post by Giant Speck on 2009-08-27
> **moore.bryan said:**
> Thanks for all the info, folks. The ubuntuzilla script never worked right for me, so I've dumped it. It's not the branding, it's the getting used to gnome-do-ing *shiretoko* instead of *firefox*. Unnecessary PITA.

Typing *firefox-3.5* works, too, I would imagine, since that's the actual name of the process.

---

### Post by nanotube on 2009-08-27
> **moore.bryan said:**
> Thanks for all the info, folks. The ubuntuzilla script never worked right for me, so I've dumped it. It's not the branding, it's the getting used to gnome-do-ing *shiretoko* instead of *firefox*. Unnecessary PITA.

Anything in particular that didn't work for you when using ubuntuzilla? Any error messages, etc. ?

---

### Post by Tibuda on 2009-08-28
> **moore.bryan said:**
> Thanks for all the info, folks. The ubuntuzilla script never worked right for me, so I've dumped it. It's not the branding, it's the getting used to gnome-do-ing *shiretoko* instead of *firefox*. Unnecessary PITA.

Gnome Do uses the name in your applications menu. You can rename it if you right-click the applications menu and click "edit menu".

---

### Post by Chrus on 2009-08-28
> **r-mo said:**
> The branding doesn't matter too much to me (although I did change the icon).

That did confuse my GF. But even she managed to work around it... she grabbed the macbook and found firefox on there.

---

### Post by t0p on 2009-08-28
I've got the version of firefox-3.5 that you can get from [getfirefox.com]("http://getfirefox.com") - the version that sits in your home directory and runs from a script there. The first time I ran it, Ubuntu asked me if I wanted to make it my default browser - I clicked yes, but if you can do this anytime under **Edit > Preferences > Advanced > General**. I wondered if there would be update issues, seeing as this browser is not installed through apt-get.  But the browser updates itself automatically (you can tell it to ask permission first if you like) so I'm currently running firefox-3.5.2.  I got rid of the old firefox icon on my top panel and replaced it with one that points to /home/t0p/firefox/firefox.  So from my point of view it runs perfectly normally but is the new version.  Plus the user-agent reports itself as "firefox" so there's no issue there either.

As for whether firefox-3.5 should be the "official" version for jaunty - *of course it shouldn't*!!  Ubuntu's long-standing policy is that new versions of software are not adopted as the default until a new version of ubuntu is released.  Why on earth should an exception be made for firefox??  You can make it the default browser for your machine by following the steps I outlined above (there are many other ways too, as mentioned by many other users) but why on earth should *your* desire for firefox-3.5 to be default browser be imposed on everyone else?

---

### Post by Keyper7 on 2009-08-28
> **moore.bryan said:**
> Thanks, kpkeerthi; that's actually the best attempt at an answer I've read, but I don't know if it applies to Firefox. I have *many* programs installed which were one version in Jaunty when it was a released and the most current now... And I'm not just talking about small, security fixes.

[https://wiki.edubuntu.org/StableReleaseUpdates/](https://wiki.edubuntu.org/StableReleaseUpdates/)

---

### Post by moore.bryan on 2009-08-28
> **t0p said:**
> As for whether firefox-3.5 should be the "official" version for jaunty - *of course it shouldn't*!!  Ubuntu's long-standing policy is that new versions of software are not adopted as the default until a new version of ubuntu is released.  Why on earth should an exception be made for firefox??  You can make it the default browser for your machine by following the steps I outlined above (there are many other ways too, as mentioned by many other users) but why on earth should *your* desire for firefox-3.5 to be default browser be imposed on everyone else?
This is where I take a different stance, t0p; I think there *should* be certain programs, of which Firefox is one, that should be the absolute most recent on any Ubuntu version.

---

### Post by Jerriy on 2009-08-29
> **Giant Speck said:**
> Firefox 3.5.x will remain Shiretoko until the next release of Ubuntu in OctoberI think Ubuntu made a blunder. Why mess around with the BROWSER? Hello! Do whatever you want with apps or gnome or nautilus or whatever but hands off the BROWSER! I mean I know this is planet linux (where experimenting is galore, compared with Windows & Mac) but still the ubu-guys should have kept their hands away from messing around with the very name of firefox. 

This shiretoko episoide is one (hopefully not giant) step backwards for the open-source world in terms of user-friendliness (as far as the non-geeky common computer user is concerned).

---

### Post by 23meg on 2009-08-29
[QUOTE=Jerriy]Why mess around with the BROWSER? Hello! Do whatever you want with apps or gnome or nautilus or whatever but hands off the BROWSER![/QUOTE]

Which is exactly why "the BROWSER" is Firefox 3.0, and "Shiretoko" is completely optional and out of the way of anyone who doesn't know about it and explicitly installs it. You're arguing in support of that decision.

[QUOTE=Jerriy]This shiretoko episoide is one (hopefully not giant) step backwards for the open-source world in terms of user-friendliness (as far as the non-geeky common computer user is concerned).[/QUOTE]

The "non-geeky common computer user", if she happens to be using Ubuntu, is using Firefox 3.0, the default browser. She doesn't know/care about "Shiretoko".

---

### Post by bodhi.zazen on 2009-08-29
I agree it is a shame Ubuntu 9.04 still uses Firefox 3.0.x

I find Shiretoko in the back ports is not the same as Firefox 3.5.x, it does not perform the same and not all of the extensions I wish to use work.

The easiest "solution" is as t0p indicated, use the binary from mozilla.

Personally I put it in /usr/local/firefox and change the symlink so /bin/firefox points to /usr/local/firefox-3.5/firefox-bin

I have an apparmor profile for it [here]("http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.local.firefox.firefox")

---

### Post by don_pucci on 2009-08-29
> **Giant Speck said:**
> The default version of Firefox in Ubuntu is the only version given the name Firefox.

The default version of Firefox in Ubuntu is 3.0.x, not 3.5.x.  Firefox 3.5.x will remain Shiretoko until the next release of Ubuntu in October, and only *then* will it become known as Firefox, because *then* it will become the default version of Firefox in Ubuntu.

Why does ubuntu get to name the browser how they see fit?  the latest stable version of FIREFOX is 3.5.2.  it should not be called the code name and it should be available in the main repositories.  things like this make ubuntu so frustrating to work with.  the entire rest of the world uses firefox 3.5.2 and can use all their add-ons but not us ubuntu users...we have to wait on the six month development cycle.

pure stupidness

---

### Post by bodhi.zazen on 2009-08-29
> **don_pucci said:**
> Things like this make ubuntu so frustrating to work with.  the entire rest of the world uses firefox 3.5.2 and can use all their add-ons but not us ubuntu users...we have to wait on the six month development cycle.

pure stupidness

No you do not have to wait, download and install the binary yourself, it is very very easy to do.

---

### Post by Paqman on 2009-08-29
> **don_pucci said:**
> things like this make ubuntu so frustrating to work with.  the entire rest of the world uses firefox 3.5.2 and can use all their add-ons but not us ubuntu users...we have to wait on the six month development cycle.

pure stupidness

That's exactly why we've got PPAs. You can have any bleeding-edge package you want, you don't have to wait for the repos to get updated.

---

### Post by don_pucci on 2009-08-29
> **Paqman said:**
> That's exactly why we've got PPAs. You can have any bleeding-edge package you want, you don't have to wait for the repos to get updated.

its not bleeding edge..its the latest stable release.  and its called firefox.  its hard to turn people onto ubuntu when they make things difficult and confusing.

---

### Post by Ric_NYC on 2009-08-29
You are not alone

[http://ubuntuforums.org/showthread.php?t=1237593](http://ubuntuforums.org/showthread.php?t=1237593)

---

### Post by don_pucci on 2009-08-29
> **Ric_NYC said:**
> You are not alone

[http://ubuntuforums.org/showthread.php?t=1237593](http://ubuntuforums.org/showthread.php?t=1237593)

all i want is for my browser to tell them when it needs to be updated, for my add-ons to work when i do update and for it to work properly on the web...

0 for 3 with shiretoko

---

### Post by bodhi.zazen on 2009-08-29
> **don_pucci said:**
> all i want is for my browser to tell them when it needs to be updated, for my add-ons to work when i do update and for it to work properly on the web...

0 for 3 with shiretoko

It seems as if you are either not listening to what I told you or do not know how to "install" the binary from mozilla. As such it make it difficult for you to install and use firefox 3.5.2

When you are ready to update :

Go here : [http://www.mozilla.com/en-US/firefox/personal.html](http://www.mozilla.com/en-US/firefox/personal.html)

Direct linky : [Linux Version]("http://download.mozilla.org/?product=firefox-3.5.2&os=linux&lang=en-US") 

Extract that file and put it where you wish. /home/you/bin , /home/your/firefox , does not matter.

Then simply make a launcher that points to say /home/home/bin/firfox/firefox-bin

or if you want all users to use it, move it to /usr/local/firefox 

Works flawlessly and it is simple. You could have installed it in the time it took you to post your concerns.

The version "Shiretoko" did not work for me either.

I also disagree with your assessment that the lack of firefox 3.5.x is a deterrent to installing and using Ubuntu, but you are entitled to your opinion.
[ ]("http://www.mozilla.com/products/download.html?product=firefox-3.5.2&os=linux&lang=en-US")

---

### Post by Jerriy on 2009-08-29
OK what about the setup of the browser in "preferred applications" option? The firefox that is there is resumably the old one, i.e. version 3.0.[x]```
firefox -new-tab "%s"
```

Now what on earth do I have to do in order that 3.5/shiretoko is the preferred app. What is the code for a "custom" browser?

---

### Post by bodhi.zazen on 2009-08-29
> **Jerriy said:**
> OK what about the setup of the browser in "preferred applications" option? The firefox that is there is resumably the old one, i.e. version 3.0.[x]```
firefox -new-tab "%s"
```Now what on earth do I have to do in order that 3.5/shiretoko is the preferred app. What is the code for a "custom" browser?

Look .... up ....

---

### Post by Jerriy on 2009-08-29
Never mind - supposedly it is 'firefox-3.5 %u'. 
Besides being a search engine Google has now become Ubuntu's primary manual also - lulz
.

---

### Post by bodhi.zazen on 2009-08-29
Sorry, I think I mis-read your question.

It is either an option on your menu under preferences or from the command line

```
sudo update-alternatives --config x-www-browser
```

google can be a good resource of many things and some people prefer it.

Otherwise please keep in mind we are volunteers here any your request for assistance is several pages deep in this thread. Sometimes it is better to start  a new thread.

---

### Post by Jerriy on 2009-08-29
> sudo update-alternatives --config x-www-browserYea thanks I was looking for that

---

### Post by Paqman on 2009-08-30
> **don_pucci said:**
> its not bleeding edge..its the latest stable release.  and its called firefox.  its hard to turn people onto ubuntu when they make things difficult and confusing.

That's why we have helpful people in the community that will happily walk you through [installing Firefox-3.5]("http://andyduffell.com/techblog/?p=280") on your machine.

If you haven't learned how to add a PPA yet, this is great opportunity to try it out.

---

### Post by hoppipolla on 2009-08-30
I think this is very silly. How can people be expected to wait potentially half a year for something they could very readily get instantaneously on Windows?

---

### Post by Jerriy on 2009-08-30
> **Paqman said:**
> That's why we have helpful people in the community that will happily walk you through [installing Firefox-3.5]("http://andyduffell.com/techblog/?p=280") on your machine.

If you haven't learned how to add a PPA yet, this is great opportunity to try it out.

The issue is broader that merely installig. After installing you have to bother about the fact that, thanks to this mess, websites and apps have difficulty interacting: some of them may not even recognize that you do have the latest version. 

For example after installation I wasn't prompted and had to separately discover the existence of and adjust the "preferred application" option in Ubuntu. But guess what, even after adjusting that I still encounter problems:

[INDENT]Problem #1, If i type 'firefox' in terminal I still openes the old version (3.0.x) despite the new 3.5 version being the 'preferred application'

Problem #2, Regarding sites that fail to recognize that I do have Firefox 3.5 in my system: one such website is (ironically) the very place Firefox itself comes from: mozilla.org (the addons section bans me from adding some extentions cuz allegedly I still don't have Firefox 3.5!!!)[/INDENT]
.

---

### Post by grizzler on 2009-08-30
> **hoppipolla said:**
> I think this is very silly. How can people be expected to wait potentially half a year for something they could very readily get instantaneously on Windows?

Indeed. Ubuntu policy or not, this is not a good idea and it negates any attempt to persuade people to try Ubuntu.

[QUOTE=Jerriy]The issue is broader that merely installig. After installing you have to bother about the fact that, thanks to this mess, websites and apps have difficulty interacting: some of them may not even recognize that you do have the latest version.

For example after installation I wasn't prompted and had to separately discover the existence of and adjust the "preferred application" option in Ubuntu. But guess what, even after adjusting that I still encounter problems:

    Problem #1, If i type 'firefox' in terminal I still openes the old version (3.0.x) despite the new 3.5 version being the 'preferred application'

    Problem #2, Regarding sites that fail to recognize that I do have Firefox 3.5 in my system: one such website is (ironically) the very place Firefox itself comes from: mozilla.org (the addons section bans me from adding some extentions cuz allegedly I still don't have Firefox 3.5!!!)[/QUOTE]

This may not be a perfect solution, but I 'installed' the real Firefox 3.5 several weeks ago (see the suggestions earlier in this thread) and changed the softlink in /usr/bin to point to my manually installed version (which I put in /opt):

**sudo ln -s /opt/firefox/firefox /usr/bin/firefox**

This way calling 'firefox' from anywhere will always start Firefox 3.5.2. When the next version is released, I just unpack the tar.bz2 file in the same location (after making a backup of what's there, of course...). As long as there are no major design changes, that's all I'll have to do (already did that when moving from 3.5.1 to 3.5.2).

I will never just accept things decided upon by 'policy makers' (might as well have stayed with windows...). Quite frankly, although I do like many aspects of Ubuntu, the way I feel about certain decisions made by 'the powers that be' cannot be expressed on a public forum...

---

### Post by Jerriy on 2009-08-30
Hey, laat je niet gek maken kerel :mrgreen:

> I just unpack the tar.bz2 file...Is doing that equivalent to (re)installing Firefox or updating it?

---

### Post by grizzler on 2009-08-30
> **Jerriy said:**
> Hey, laat je niet gek maken kerel :mrgreen:
Hehe... Geen kans op.

> Is doing that equivalent to (re)installing Firefox or updating it?
Updating/upgrading. Unpacking the tar.bz2 file simply puts the (new) application files in place. Strictly speaking it isn't really 'installing', because it doesn't automatically update any links or check dependencies. But if the softlink has already been set, that doesn't matter (it will still point to an executable file called 'firefox' in the /opt/firefox directory) and this 'package' doesn't have any external dependencies.

The user specific data is kept in the ~/.mozilla directory and its subdirectories, so that won't be overwritten.

---

### Post by Ric_NYC on 2009-08-30
> **grizzler said:**
> Indeed. Ubuntu policy or not, this is not a good idea and **it negates any attempt to persuade people to try Ubuntu**.






I agree.

---

### Post by Paqman on 2009-08-30
> **Jerriy said:**
> 
[INDENT]Problem #1, If i type 'firefox' in terminal I still openes the old version (3.0.x) despite the new 3.5 version being the 'preferred application'


Easily fixed, either type "firefox-3.5" or set an [alias]("http://ss64.com/bash/alias.html").

Having said that, we should have had firefox-3.5 backported by now. But the fact is we don't.

---

### Post by DougieFresh4U on 2009-08-30
I find using Firefox code named **'Namoroka 3.6a2pre'** to be quite snappy!!

---

### Post by Jerriy on 2009-08-30
Wow that is wicked! I like that wood-panel look

---

### Post by Tibuda on 2009-08-30
> **hoppipolla said:**
> I think this is very silly. How can people be expected to wait potentially half a year for something they could very readily get instantaneously on Windows?

In Windows you probably have downloaded Firefox yourself. You can do it in Linux too.

---

### Post by NTolerance on 2009-09-11
> **grizzler said:**
> Indeed. Ubuntu policy or not, this is not a good idea and it negates any attempt to persuade people to try Ubuntu.



This may not be a perfect solution, but I 'installed' the real Firefox 3.5 several weeks ago (see the suggestions earlier in this thread) and changed the softlink in /usr/bin to point to my manually installed version (which I put in /opt):

**sudo ln -s /opt/firefox/firefox /usr/bin/firefox**

This way calling 'firefox' from anywhere will always start Firefox 3.5.2. When the next version is released, I just unpack the tar.bz2 file in the same location (after making a backup of what's there, of course...). As long as there are no major design changes, that's all I'll have to do (already did that when moving from 3.5.1 to 3.5.2).

I will never just accept things decided upon by 'policy makers' (might as well have stayed with windows...). Quite frankly, although I do like many aspects of Ubuntu, the way I feel about certain decisions made by 'the powers that be' cannot be expressed on a public forum...

Thanks for posting this.  From a technical standpoint, this is the best solution given the circumstances if one wants a clear upgrade path to Karmic, when the "real" Firefox 3.5 becomes available.  

Shiretoko from the repositories has major issues aside from the branding, such as loss of ubufox/lack of ability to open any files with the downloads window.  

When the Karmic upgrade comes around, just pre-emptively delete the /opt/firefox directory and restore the original symlink in /usr/bin.

---

### Post by NormanFLinux on 2009-09-11
I installed Ubuntuzilla. It updates Firefox when a new version is available.

---

### Post by JDShu on 2009-09-12
Shouldn't this thread be in "recurring discussions"?

---

### Post by Viva on 2009-09-12
> **NTolerance said:**
> Thanks for posting this.  From a technical standpoint, this is the best solution given the circumstances if one wants a clear upgrade path to Karmic, when the "real" Firefox 3.5 becomes available.  

**Shiretoko from the repositories has major issues aside from the branding, such as loss of ubufox/lack of ability to open any files with the downloads window.**  

When the Karmic upgrade comes around, just pre-emptively delete the /opt/firefox directory and restore the original symlink in /usr/bin.

Install [firefox-3.5-gnome-support]("apt:firefox-3.5-gnome-support")

---


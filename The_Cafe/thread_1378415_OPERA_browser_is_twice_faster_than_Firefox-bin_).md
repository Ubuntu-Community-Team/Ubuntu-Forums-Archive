---
title: "OPERA browser is twice faster than Firefox-bin :)"
date: 2010-01-11
forum: The Cafe
---

### Post by frenchn00b on 2010-01-11
OPERA browser was always (better) or by far faster than Firefox-bin / Mozilla:) 

It seems that their new version / release is even better and faster :) It's really fast nowadays opera. 

here add these lines to your /etc/apt/sources.list
replace $$$$$$ by the name of your ubuntu distro in the text below:
```

# The Opera Web Browser Official packages.
# maintained by chrisw at opera dot com
deb http://deb.opera.com/opera/ $$$$$$ non-free
```

then 

```
sudo apt-get -f install opera
opera &
```

Enjoy the turbo internet =D>:biggrin:

---

### Post by pwnst*r on 2010-01-11
Do you have some data to back this up?  Since you said it's twice as fast, I'm assuming you're looking at numbers from somewhere.

---

### Post by NoaHall on 2010-01-11
What do you mean by their "new release"? You mean the version which was updated to 10.10 50-ish days ago, or the 10.50 pre-alpha released about ten days ago?  10.10 isn't that new, and 10.50 isn't really a release. It's a pre-alpha. And the name of the Ubuntu distro is Ubuntu. That's why it's the Ubuntu distro. It's called that.

---

### Post by Xbehave on 2010-01-11
chrome is 10x faster than opera, i can make unfounded claims too :O

In reality though all browsers are so fast it makes very little difference which you use and what matters more is the features you need/use, e.g browsing would be much slower for me if i lost selection based searching than if my browser was 0.01 seconds slower at page rending.

---

### Post by juancarlospaco on 2010-01-11
I run my Firefox from RAM and is faster

---

### Post by Cabs21 on 2010-01-11
click to read about [THE RESULTS!]("http://lifehacker.com/5352195/browser-speed-tests-chrome-40-and-opera-10-take-on-all-challengers")

---

### Post by NoaHall on 2010-01-11
> **juancarlospaco said:**
> I run my Firefox from RAM and is faster

I think you'll find all programs run from RAM.

Cabs: That's Opera 10. The latest stable is 10.10. The pre-alpha, is a lot quicker, and that is 10.50.

---

### Post by koleoptero on 2010-01-11
Unfortunately Opera is the only program that has a qt4 release which looks completely out of place in KDE 4.

Arora for me.

---

### Post by frenchn00b on 2010-01-11
> **Xbehave said:**
> chrome is 10x faster than opera, i can make unfounded claims too :O

In reality though all browsers are so fast it makes very little difference which you use and what matters more is the features you need/use, e.g browsing would be much slower for me if i lost selection based searching than if my browser was 0.01 seconds slower at page rending.

no really ... ? 
there was some tests about it on linux.org boards, better several browsers and opera remained the winner; 

but now since Chrome, that might change the idea of browsing ? 
Browsing at the speed of light :)

---

### Post by Tibuda on 2010-01-11
> **frenchn00b said:**
> here add these lines to your /etc/apt/sources.list
replace $$$$$$ by the name of your ubuntu distro in the text below:
```

# The Opera Web Browser Official packages.
# maintained by chrisw at opera dot com
deb http://deb.opera.com/opera/ $$$$$$ non-free
```

then 

```
sudo apt-get -f install opera
opera &
```
Just download and install the deb package from [http://opera.com](http://opera.com). This is a lot easier and will add the repository for you.

---

### Post by Xbehave on 2010-01-11
> **Cabs21 said:**
> click to read about [THE RESULTS!]("http://lifehacker.com/5352195/browser-speed-tests-chrome-40-and-opera-10-take-on-all-challengers")
Opera loses at almost everything other than cold start

---

### Post by NoaHall on 2010-01-11
> **Xbehave said:**
> Opera loses at almost everything other than cold start

The old Opera 10.

---

### Post by Dark_Stang on 2010-01-11
> **Cabs21 said:**
> click to read about [THE RESULTS!]("http://lifehacker.com/5352195/browser-speed-tests-chrome-40-and-opera-10-take-on-all-challengers")
According to that test it took their machine 11 seconds to load firefox for the first time. It sounds like their machine has some issues. Because of that I don't trust any of their other tests.

Edit: Also. Memory usage, less is better? Wtf? Really? By those standards Windows 3.1 is better than debian. Memory is there to be used, not to be reserved for anti-virus software.

---

### Post by frenchn00b on 2010-01-11
Man !!

**Google chrome is terribly fast. faster than firefox , galeon, and opera.**

Wow: 
here is deb:
```
 md5sum google-chrome-beta_current_i386.deb 
b5d44f74288fa52613e420c741c9f350  google-chrome-beta_current_i386.deb
```

it consumes apparently not much memory and with tabs, it remains fast.

How is it possible that they make better than mozilla / firefox ?

---

### Post by pwnst*r on 2010-01-11
> **frenchn00b said:**
> Man !!

**Google chrome is terribly fast. faster than firefox , galeon, and opera.**

Wow: 
here is deb:
```
 md5sum google-chrome-beta_current_i386.deb 
b5d44f74288fa52613e420c741c9f350  google-chrome-beta_current_i386.deb
```

it consumes apparently not much memory and with tabs, it remains fast.

How is it possible that they make better than mozilla / firefox ?

Wow.

---

### Post by NoaHall on 2010-01-11
> **frenchn00b said:**
> Man !!

**Google chrome is terribly fast. faster than firefox , galeon, and opera.**

Wow: 
here is deb:
```
 md5sum google-chrome-beta_current_i386.deb 
b5d44f74288fa52613e420c741c9f350  google-chrome-beta_current_i386.deb
```

it consumes apparently not much memory and with tabs, it remains fast.

How is it possible that they make better than mozilla / firefox ?

I'm afraid I have to conclude you don't know what you're talking about, and simply advertising every web browser you can name :)

---

### Post by Zoot7 on 2010-01-11
The only time I use Opera is the portable version I carry around with me to use on the XP machines in my college. I find its portable version is streets ahead of Firefox's one.
That aside I use Firefox pretty much exclusively under both Linux and Windows.

---

### Post by AllRadioisDead on 2010-01-11
Can anyone point me to an amd64 deb?

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Can anyone point me to an amd64 deb?

For?

```
sudo add-apt-repository ppa:chromium-daily && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
``` Chromium.

Opera 10.10 - [http://www.opera.com/download/?os=linux-x86-64&ver=10.10&local=y](http://www.opera.com/download/?os=linux-x86-64&ver=10.10&local=y)

Chrome - [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb)

---

### Post by Zoot7 on 2010-01-11
> **ihermit said:**
> Can anyone point me to an amd64 deb?
[http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.10&local=y](http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.10&local=y)

They've packages for a surprising amount of distros there.

EDIT: Assuming you mean Opera. :)

---

### Post by AllRadioisDead on 2010-01-11
> **NoaHall said:**
> For?

```
sudo add-apt-repository ppa:chromium-daily && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
``` Chromium.

Opera 10.10 - [http://www.opera.com/download/?os=linux-x86-64&ver=10.10&local=y](http://www.opera.com/download/?os=linux-x86-64&ver=10.10&local=y)

> **Zoot7 said:**
> [http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.10&local=y](http://www.opera.com/browser/download/?os=linux-x86-64&ver=10.10&local=y)

They've packages for a surprising amount of distros there.
Sorry, I was looking for an opera 10.5 build. Thanks.

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Sorry, I was looking for an opera 10.5 build. Thanks.

Here you go. - [http://snapshot.opera.com/unix/labs-6177/](http://snapshot.opera.com/unix/labs-6177/)
It's not in a deb yet, because it's a pre-alpha(Opera looking out for you). To run, just double click the bin file inside the archive.

---

### Post by AllRadioisDead on 2010-01-11
Thanks, tried it.
The menu's look like garbage.

---

### Post by mmix on 2010-01-11
opera seems slightly faster than firefox, but, it is not opensource.

firefox is opensource, but the code-base is too huge 
and quality is gr8, plugin is fantastic.

dillo is small codebase and cross-platform.
doing compiling dillo with mingw, got some error messages now.

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Thanks, tried it.
The menu's look like garbage.

You can change it :) Check out the cherry theme. Or click the icon, and check "Show Menu Bar"

---

### Post by phrostbyte on 2010-01-11
I did a test on some browsers (it's comprehensive though)

[http://ubuntuforums.org/showthread.php?t=1365791](http://ubuntuforums.org/showthread.php?t=1365791)

Chromium beat Firefox in JS performance, but the good news for Firefox users is Firefox 3.6 raises the bar considerably.

---

### Post by AllRadioisDead on 2010-01-11
> **NoaHall said:**
> You can change it :) Check out the cherry theme. Or click the icon, and check "Show Menu Bar"
Did the show menu thing, the actual menu itself, not the toolbar is what looks bad.

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Did the show menu thing, the actual menu itself, not the toolbar is what looks bad.

Which bit of the menu?
I really recommend the Cherry theme, it makes the menu look really good.

---

### Post by AllRadioisDead on 2010-01-11
Here's what I'm talking about:
Font is wrong, white border around the edges, font color is wrong.

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Here's what I'm talking about:

Oh, I see. A downside of being more compatible with your system's theme, I suppose. Let me see what I can find :)

---

### Post by AllRadioisDead on 2010-01-11
> **NoaHall said:**
> Oh, I see. A downside of being more compatible with your system's theme, I suppose. Let me see what I can find :)
Hmm, thanks.
The browser is lightning fast though.

---

### Post by starcannon on 2010-01-11
> **frenchn00b said:**
> OPERA browser was always (better) or by far faster than Firefox-bin / Mozilla:) 

It seems that their new version / release is even better and faster :) It's really fast nowadays opera. 

here add these lines to your /etc/apt/sources.list
replace $$$$$$ by the name of your ubuntu distro in the text below:
```

# The Opera Web Browser Official packages.
# maintained by chrisw at opera dot com
deb http://deb.opera.com/opera/ $$$$$$ non-free
```then 

```
sudo apt-get -f install opera
opera &
```Enjoy the turbo internet =D>:biggrin:
No AdBlock Plus, I don't care how fast it is; it's useless to me. I could run lynx if I didn't care about features, and just wanted speed.

---

### Post by Frak on 2010-01-11
> **frenchn00b said:**
> Man !!

**Google chrome is terribly fast. faster than firefox , galeon, and opera.**

Wow: 
here is deb:
```
 md5sum google-chrome-beta_current_i386.deb 
b5d44f74288fa52613e420c741c9f350  google-chrome-beta_current_i386.deb
```

it consumes apparently not much memory and with tabs, it remains fast.

How is it possible that they make better than mozilla / firefox ?
```
@this.sense = nil
if @this.save
   redirect_to nonsense_path(@this)
else
   screw_it(@this)
end

```

---

### Post by NoaHall on 2010-01-11
> **ihermit said:**
> Hmm, thanks.
The browser is lightning fast though.

It's a known problem on the UNIX builds - part of the switch over of graphic systems. It should be fixed by the beta, and perhaps by the Alpha. It all depends on how many themes(and the theming applied to Opera) they can get it to work with.

Oh, and as for AdBlock - see this -
[http://ubuntuforums.org/showpost.php?p=8643789&postcount=16](http://ubuntuforums.org/showpost.php?p=8643789&postcount=16)

---

### Post by AllRadioisDead on 2010-01-11
Thanks.

---

### Post by pwnst*r on 2010-01-11
> **Frak said:**
> ```
@this.sense = nil
if @this.save
   redirect_to nonsense_path(@this)
else
   screw_it(@this)
end

```

lol

---

### Post by lovinglinux on 2010-01-11
Opera could load pages faster than Firefox with turbo mode, for obvious reasons, but it isn't twice as fast as Firefox. No way. Besides, activate Turbo mode and say goodbye to your privacy.

Google Chrome indeed beats Firefox, but it doesn't have a fraction of Firefox customization options and extensions.

About loading times, a vanilla Firefox loads pretty much instantaneously. The problem is when the user adds a bunch of extensions that needs to perform some heavy functions during load time or when the database gets filled with left-overs, which could also reduce general responsiveness during normal usage.

I'm running Firefox 3.6rc1 with **43 extensions enabled **and it loads in **5 seconds**. All you have to do is some database maintenance and keep an eye on heavy extensions. Xmarks for example has been cut off from my list.

You can also run Firefox profile from RAM, as already suggested by another poster. Since Firefox doesn't need to constantly read and write to the disc, specially when performing database functions (sqlite), then it runs much faster.

Anyway, to learn how to improve Firefox performance see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

BTW, Opera...no thanks.

---

### Post by frenchn00b on 2010-01-12
> **starcannon said:**
> No AdBlock Plus, I don't care how fast it is; it's useless to me. I could run lynx if I didn't care about features, and just wanted speed.

I use ELINKS quite often , for reading, just to go to the essential. Or on old PC. ELINKS is cool, but lacks PDF viewer

---

### Post by Khakilang on 2010-01-12
To me stability and reasonable speed is good for me. I don't need super speed browser.

---

### Post by meborc on 2010-01-12
on my Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

Shiretoko 3.5.8pre - 1768 points
Opera 10.50        - 3855 points

[http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

---

### Post by mikewhatever on 2010-01-12
> **frenchn00b said:**
> [s]OPERA browser was always (better) or by far faster than Firefox-bin / Mozilla:) 

It seems that their new version / release is even better and faster :) It's really fast nowadays opera. 

here add these lines to your /etc/apt/sources.list
replace $$$$$$ by the name of your ubuntu distro in the text below:

then 


Enjoy the turbo internet =D>:biggrin:[/s]

I like Opera and have to say that what you do spreading false claims is counter productive. Only an idiot will use Opera because of reading your promotion.
Before doing more harm, get stuffed, will you.

---

### Post by A_T on 2010-01-12
Trying the 64it Alpha. Gui and fonts are a bit of a mess. Flash works fine though :biggrin:

---

### Post by lovinglinux on 2010-01-12
> **meborc said:**
> on my Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

Shiretoko 3.5.8pre - 1768 points
Opera 10.50        - 3855 points

[http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

I think would be more appropriate to compare Opera 10.50 to Firefox 3.7, since the 3.5.x branch is the current stable release (comparable to Opera 10.10). At least it should be compared to 3.6, which is at release candidate stage now.

My results (Core2 Duo E5700):

```
Firefox 3.**6rc1** - 1564 points
Opera 10.50 - 2031 points
```

Although Opera is indeed considerably faster (30%), is not even close to 50% faster. Twice as fast would be forcing a little bit. Not to mention the Linux version of Firefox is released without PGO optimization, so I bet if you compile Firefox 3.6  from source, with PGO enabled, it will be pretty much as fast as Opera. In fact, Firefox compiled from source with optimizations exhibit about 30% performance increase on my previous tests, so it would gain exactly the difference showed by Opera 10.50.

Would be interesting if someone could post the results of FF 3.7.

---

### Post by meborc on 2010-01-13
> **lovinglinux said:**
> ...

Would be interesting if someone could post the results of FF 3.7.

ok, did the test on my notebook

ff 3.5.8pre - 1394
ff 3.7a1pre - 2057
opera 10.50 - 2414


yeah... 3.7 is much faster than 3.5 at the moment... but it is still very early

---

### Post by NoaHall on 2010-01-13
I'll post my results, one at a time(I should have clicked details the first time. Oh well, I'm not redoing the ones I missed) - 
(On Windows 7 64 bit)

Opera 10.10 - 2661
{
Rendering - 3099
Social networking - 3198
Complex graphics - 3886
Data - 1202
DOM operations - 4476
Text parsing - 2504
}

Opera 10.50 - **5082**

Chrome 3.0.195.38 - 4828

Chrome 4.0.249.64 - **5680** 
{
Rendering - 5858
Social networking - 4929
Complex graphics - **9960**
Data - 4109
DOM operations - **7314**
Text parsing - **6816**
}

IE 8 64 bit - 1235

IE 8 32 bit(running on 64 bit) - 1230
{
Rendering - 1601
Social networking - 1399
Complex graphics - 0
Data - 1053
DOM operations - 818
Text parsing - 1464

Firefox 3.5.7 - 3068

Firefox 3.6 - **4009**

Minefield 3.7a1pre (otherwise known as Firefox) - 3884
{
Rendering
2520
Social networking
3158
Complex graphics
7565
Data
**8427**
DOM operations
3787
Text parsing
3484
}

---


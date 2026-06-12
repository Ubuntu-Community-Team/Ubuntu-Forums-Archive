---
title: "Chrome's Flash plugin bites."
date: 2012-08-02
forum: The Cafe
---

### Post by Copper Bezel on 2012-08-02
***Moved to recurring.***

I'm having all of the kinds of problems I expected from Flash once Adobe dropped Linux support. However, I'm having them in Chrome with Pepper Flash, while Mozilla's outdated plugin still works for everything. Anyone else feeling this?

First the fullscreen feature broke. It still has yet to be fixed. I have no evidence that Chrome's Flash's fullscreen feature works for anyone, anywhere.

Then I started getting garbled audio in the first second or so of each video. On a couple of occasions, I've had the player get "stuck" and cause garbled audio throughout the video. Once, I had to restart to fix the problem.

Now Comedy Central's Flash player has ceased to work in Chrome. It seems like an extreme performance issue, but it's not just choppy or slow - it's completely unusable. It *still works in Firefox*, which means that this is a Pepper Flash problem, not a change in Comedy Central's player.

I doubt that I'm the only one to have these new problems, but I haven't seen anyone else talking about them. What have you noticed, are there any fixes, and am I missing something? It's very troublesome - I like Chrome, and I know that the outdated player used in other browsers won't last forever, but I'm very disappointed with these problems and worried about, yes, the recurring bit, "the future of Flash in Linux."

But specifically, what's up with Chrome / Pepper Flash, seriously?

---

### Post by vasa1 on 2012-08-02
People are talking, sometimes just not in a technically analytical way ... But you can poke around here: [http://productforums.google.com/forum/#!categories/chrome/linux](http://productforums.google.com/forum/#!categories/chrome/linux) and a couple of Google employees seem to be monitoring things there and suggesting people provide information in a format that will help.
There are complaints here as well: [http://www.blogger.com/comment.g?blogID=8982037438137564684&postID=7230672016702450226&isPopup=true](http://www.blogger.com/comment.g?blogID=8982037438137564684&postID=7230672016702450226&isPopup=true)
example being "simone and others with the flash audio problem, please come to [http://code.google.com/p/chromium/issues/detail?id=139953](http://code.google.com/p/chromium/issues/detail?id=139953) and leave us information on your configuration. We are working hard to resolve the issues as quickly as possible. Thank you!"

I'm in a bit of a hurry and so I may not have understood your post at all!

---

### Post by Copper Bezel on 2012-08-03
No, that's great info! I suppose I needed to Google a bit more before posting. Thanks!

Still worried about this big pile-up of problems all more or less at once.

---

### Post by vasa1 on 2012-08-03
I hate to be one of those WFM types but ...

By way of background ...
I'm running 12.04 with Xfce 4.10 on a Dell Inspiron 1545 n series laptop (Core2 Duo) of 2009 vintage and no mods except that the 2 GB RAM has been increased to 4 GB.
If you want the output of specific hardware, give me the specific commands to run. I suspect that I don't have a special graphics card and that everything's integrated.
I know that I can run "Unity 3D".

These are my Chrome browser details:
```
21.0.1180.57 (Official Build 148591)
OS	Linux
WebKit	537.1 (@123707)
JavaScript	V8 3.11.10.17
Flash	11.3.31.222
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.1 (KHTML, like Gecko) Chrome/21.0.1180.57 Safari/537.1
Command Line	 /usr/bin/google-chrome -start-maximized --flag-switches-begin --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/vasa1/.config/google-chrome/Default

```

I have just the Pepper Flash enabled. I disabled the other one (in about:plugins).

I don't know how important this is but my net speed is way slow, nominally 384 Kbps (?) and effectively about 1/8th that, and so I rarely get to watch a video end to end without several episodes of "buffering" (?) and I use the lowest quality.

Now,
> **Copper Bezel said:**
> ...
I'm having all of the kinds of problems I expected from Flash once Adobe dropped Linux support. However, I'm having them in Chrome with Pepper Flash, while Mozilla's outdated plugin still works for everything. Anyone else feeling this?
As I said, I've disabled the Mozilla plugin.

> **Copper Bezel said:**
> ...
First the fullscreen feature broke. It still has yet to be fixed. I have no evidence that Chrome's Flash's fullscreen feature works for anyone, anywhere.

WFM when I replay a fully loaded video but quality (screen res?) takes a bit of a hit. Not much. I have to look to spot the impairment.

> **Copper Bezel said:**
> ...
Then I started getting garbled audio in the first second or so of each video. On a couple of occasions, I've had the player get "stuck" and cause garbled audio throughout the video. Once, I had to restart to fix the problem.
I can't comment on the first couple of seconds because of my net speed. But when the video does start even for the first time, sound is okay. In general, I do not have garbled sound.

In this video ([http://www.youtube.com/watch?v=Xapsk8QUw-k](http://www.youtube.com/watch?v=Xapsk8QUw-k)) both on initial run and replay, there seems to be a slight "lip sync" issue. Again, I have to look for it.

> **Copper Bezel said:**
> ...
Now Comedy Central's Flash player has ceased to work in Chrome. It seems like an extreme performance issue, but it's not just choppy or slow - it's completely unusable.
I'll try it if you put up a link and if "aliens" are allowed to access it but I guess it will take decades to load for me :(

---

### Post by vasa1 on 2012-08-03
[http://www.comedycentral.com/video-clips/vqaslj/roast-of-roseanne-tweet-jane-lynch-your-roseanne-jokes](http://www.comedycentral.com/video-clips/vqaslj/roast-of-roseanne-tweet-jane-lynch-your-roseanne-jokes)

WFM but it's too heavy, I just got past the "Pepsi" ad to the bit about knowing what someone's twitter something or the other. My CPU was uncomfortably high and my temp was > 60° C and so I gave up &#128542;

I'm not sure that Pepper's to blame for that ...

---

### Post by Copper Bezel on 2012-08-03
Yeah, I did have some unattended updates, and Comedy Central is stuttering and apparently cooking my CPU, but working now. And the fullscreen bug and the garbled audio seem to have been fixed, although the fullscreen feature seems to be doing weird things with aspect ratio, now.

Chrome itself now has a couple of odd new bugs, but beggars and choosers. = )

---

### Post by Lucradia on 2012-08-03
Flash 11 is known to have some serious issues, even without hardware acceleration. Like tearing the flash content when scrolling the page. (YouTube tries to get around this by disabling all keyboard and mouse features if you have clicked the youtube flash content. (Save for moving the mouse)

This is fixed if you downgrade to the latest version 10. Some YouTubers have disabled the use of HTML5 on their content by the way, so please don't tell me to switch to it.

---

### Post by vasa1 on 2012-08-03
Awesome advice.

---

### Post by sffvba[e0rt on 2012-08-03
Not read all of the replies, but I can vouch for Chrome in Linux being so bad for me I switched back to FF when I am in Ubuntu (and use Chrome in Windows / Android etc.)


404

---

### Post by MadmanRB on 2012-08-03
I personally do not have an issue, works fine on my end.

---

### Post by vasa1 on 2012-08-03
> **MadmanRB said:**
> I personally do not have an issue, works fine on my end.
Same here.

---

### Post by mips on 2012-08-03
Chromium seems to work fine here?

---

### Post by vasa1 on 2012-08-03
> **mips said:**
> Chromium seems to work fine here?
AFAIK, Chromium _18_ isn't really the issue here. We're discussing Chrome _21_.
Of course Chromium _20_ is available as part of the [webapps ppa]("http://ubuntuforums.org/showthread.php?t=2035166").

---

### Post by doorknob60 on 2012-08-03
Really? I find the Chrome Pepper Flash works way better than any other version of Flash has ever worked for me. Lower CPU usage, better performance, and finally, no more tearing! It unfortunately means I can't even consider using Firefox or other browsers as my default browser, because Flash just isn't as good on them. Oh well, I like Chrome anyways.

---

### Post by madjr on 2012-08-04
chrome 19 was really good then chrome 20 made me switch to firefox again ;/

---

### Post by Copper Bezel on 2012-08-04
Yeah, the problems for me started with 20, then seem to have been fixed in 21, except for performance and skipping, which are perennial problems that only seem *worse* than previously, which isn't a very objective mark. It's certainly much better than it briefly was, and I was very late to be complaining about it.

Thanks for sounding off with your experiences, all, and thanks especially for the extensive checking, vasa1.

Chrome is still irritating me - in 21, it's grown a new bug under Shell when using the "Use System Title Bar and Borders" option, but that's entirely unrelated.

---

### Post by Giant Speck on 2012-08-04
> **not found said:**
> Not read all of the replies, but I can vouch for Chrome in Linux being so bad for me I switched back to FF when I am in Ubuntu (and use Chrome in Windows / Android etc.)
I have a similar experience, and I originally moved from Firefox to Chrome because of the way the plugin was behaving in Firefox!  Flash in Firefox would crash every two seconds or so, so I moved to Chrome.  The Pepper plugin worked fine for a while, but then I started noticing that the first three seconds or so of any video was fast-forwarding and then when the video returned to normal speed, the audio was out of sync by about a second or two.

It turns out that my original problem with Firefox was caused by me using a bad fix to get rid of its "Smurfvision" bug, and once I retackled that issue, it works great.  I'm back on Firefox for now.

---

### Post by viperdvman on 2012-08-04
Well, I run both Windows and a pair of Linux distros (Ubuntu 12.04 and Bodhi 2.0.1). And I run Chrome on all of them just as much as I run Firefox nowadays. The newest Flash for both browsers works perfectly fine for me in Windows. It also worked for me in Firefox in Ubuntu and Bodhi. However, in Chrome, I had problems running Flash in Ubuntu. I've only noticed it when playing YouTube videos. But my problem was: I run dual monitors in Ubuntu. And whenever I went to fullscreen, it would only show the left half of the video. I had to use the Esc key to back out of it. I had seen somewhere on these forums to roll back to the previous Flash in chrome:plugins. And that fixed that problem. Now I didn't have this problem in Bodhi since I don't run dual monitors on it *(E17 does support dual monitors, but it takes some work to get dual monitor support, and E17's Shelves don't work right on it and displays on one monitor and only one monitor)*

So yeah, I would try putting ```
chrome://plugins/
``` in your URL, click on + Details, and disable the newer Flash plug-in and me sure the older one is active. And then restart Chrome and see if that helps.

---

### Post by vasa1 on 2012-08-04
> **Copper Bezel said:**
> ... - in 21, it's grown a new bug under Shell when using the "Use System Title Bar and Borders" option, but that's entirely unrelated.
Did you file a bug @ crbug.com?

---

### Post by Primefalcon on 2012-08-04
I agree it sucks, the problem I am having though is it puts the voice and action out of sync

---

### Post by Copper Bezel on 2012-08-04
[QUOTE=vasa1]Did you file a bug @ crbug.com?[/QUOTE]

I wasn't the first to encounter it - [here](http://code.google.com/p/chromium/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Pri%20Mstone%20ReleaseBlock%20OS%20Area%20Feature%20Status%20Owner%20Summary&groupby=&sort=&id=137447). I did elaborate on it (post 14.)

---

### Post by vasa1 on 2012-08-04
> **Copper Bezel said:**
> ... - in 21, it's grown a new bug _under Shell_ when using the "Use System Title Bar and Borders" option, but that's entirely unrelated.
Okay, it's affecting users of Gnome Shell and Ubuntu 12.04.

Oops. There's even one report with Fedora 17. And Arch.

---


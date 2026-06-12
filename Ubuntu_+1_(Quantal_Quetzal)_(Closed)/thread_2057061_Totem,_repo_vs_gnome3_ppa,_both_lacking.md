---
title: "Totem, repo vs gnome3 ppa, both lacking"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-12
While in the past haven't used totem much for anything but the browser plugin have in the last month found more interesting with the grilo plugins. 
Atm there is no grilo support in the repo version, whether that changes not sure, on my bug it needs a mir, whatever that is..

The ppa has support for grilo 0.2 but only a couple currently work, overall the ppa version has some real flaws, more so in an ubuntu session.

So general state - as seen here on new install tonight, current image
Totem 3.4.3 (repo
Overall works ok, still has full menus in ubuntu sesssion. 

Due to a flaw in the current .10 bad plugin, totem will fail to show video in a fair amount h.264 videos, seriously affects the 0.1  grilo youtube plugin which otherwise work very well.

The mozilla plugin works ok though starting in 3.4 will fail to play video in .mov & .mp4, similar to the bad plugin issue but not connected.
If enabled the grilo plugins all work in all views except vimeo - screen 1

Totem 3.5.9x (Videos, ppa
For local files works well, though in an ubuntu session has no app menu when using the global menus, a big fail there. If the menus are moved back into totem then the app menu will be avail. in unity panel. - screen 2

The 1.0 bad plugin has been repaired for h264parse so not affected like repo version.
The mozilla plugin is totally broken, atm worthless - screen 3

The 0.2 grilo plugins have been extended but currently only a couple work, youtube not at all, appletrailers & blip.tv work ok, at least in browse view. - screen 4

So if the grilo plugins are made  more functional the ppa 3.5.x would seem better & depending on use case still may be better than the repo version.


Atm here will opt for repo version with grilo 0.1 enabled & a repaired 0.10 bad plugin though again atm the latter 2 are self fixes as Ubuntu has dropped the ball in both cases.

(- the 0.10 bad now requires a debdiff & ffe, apparently the last 6 months wasn't enough time to fix. 
I have a debdiff here but think it may not quite 'qualify' so won't bother, so one else can if inclined.. 

Side note on appletrailers
The grilo 0.1 & 0.2 plugins both work extremely well, due in part to the full vid is quickly buffered & totem plays from the buffer.
There is one little issue, at times only a partial listing is shown, like a-h.

Edit: can't actually pin down why the truncated listing, many times either switching WS's or moving totem before opening browse Seems to help restore a-z, don't know..

---

### Post by jbicha on 2012-09-14
I found your post a bit confusing as it discussed several different issues but it was a bit concise about some of the issues. I haven't fully tested Totem 3.5.90 but I did push it into the GNOME3 PPA and I am interested in learning more about any new problems it creates.

> **mc4man said:**
> While in the past haven't used totem much for anything but the browser plugin have in the last month found more interesting with the grilo plugins. 
Atm there is no grilo support in the repo version, whether that changes not sure, on my bug it needs a mir, whatever that is..


MIR is a [Main Inclusion Reques]("https://wiki.ubuntu.com/MainInclusionProcess")t. Apps in "main"  can't build-depend, depend, or recommend any thing from "universe". Grilo is in universe. At this point in the Quantal release cycle, it would probably need a [Feature Freeze Exception]("https://wiki.ubuntu.com/FreezeExceptionProcess") also.

> **mc4man said:**
> 
Totem 3.5.9x (Videos, ppa
For local files works well, though in an ubuntu session has no app menu when using the global menus, a big fail there. If the menus are moved back into totem then the app menu will be avail. in unity panel. - screen 2

Ok, I can verify that Totem 3.5.90 uses both the new GNOME App Menu and a traditional File Edit View menu but Unity only shows the GNOME App Menu.  I commented on [bug 999827]("http://pad.lv/999827"), which I believe is the tracking bug for this type of problem.

> **mc4man said:**
> 
The mozilla plugin is totally broken, atm worthless - screen 3

Could you please report that to GNOME? /usr/share/totem/mozilla-viewer.ui is installed so I don't think this is just a Ubuntu packaging error.

> **mc4man said:**
> 
(- the 0.10 bad now requires a debdiff & ffe, apparently the last 6 months wasn't enough time to fix. 
I have a debdiff here but think it may not quite 'qualify' so won't bother, so one else can if inclined..

Do you have a bug for whatever your problem is? Clear test case would be great too.

We tried to enable the grilo 0.2 plugin in the GNOME 3 PPA build of Totem (since it seems like Totem 3.5.90 can't be built without grilo, which is probably a bug). When I go to Edit>Plugins, I don't see grilo listed, but I do get this error:
```

(totem:15739): Grilo-WARNING **: [registry] grl-registry.c:330: Failed to initialize plugin: '/usr/lib/x86_64-linux-gnu/grilo-0.2/libgrlflickr.so'

```How did you get the grilo plugin working with 3.5.90?

---

### Post by mc4man on 2012-09-14
Give me a bit to re-install the 3.5.x - meanwhile - 
As far as the 0.10 bad plugin
At some point in 12.04 dev the videoparser plugin became a blocker on displaying some videos that are encoded with h.264  - AVC 1 Baseline - L2.1, Baseline - L1.1 & a few 3.0. These are quite common on youtube & elsewhere online..

So I have a 12.04 bug on where we figured out the cause, got upstream commits to fix & filed with Debian on 0.10.23

The current possible ?? issue is that the commits to fix where only for 1.0 & 0.10.23 while Ubuntu has stuck with 0.10.22 for 12.04 & 12.10
So the patch I made isn't just the upstream commit, which by itself means nothing in 0.10.22. 
Basically it updates h264parse.c /.h to 0.10.23 & then applies the commit.

So I'm thinking that could be an issue for officially fixing 0.10.22 in 12.04/.10, occurred to me while creating the debdiff, new patch for.
(even though at this point likely a couple of hundred people have self built the repaired plugin
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

---

### Post by mc4man on 2012-09-14
> How did you get the grilo plugin working with 3.5.90?
At this point with a .deb package that installs to the proper location just simply installing, previously with self built had to mv
> When I go to Edit>Plugins, I don't see grilo listed,
The terminal output is just a warning on 2 of them, (at certain times previously it would say 'so none of the plugins will be loaded'), no longer.

grilo isn't in the listed plugins, have been moved to the extra plugin package & are auto enabled/loaded once installed

What works - mainly just browse view
appletrailers in browse view
blip.tv in browse & search views
Jamendo in browse, edit - works ok once I got the .93 ugly plugin
Optical media - need to test later, this laptop has issues it's dvd drive 

The search box is displayed wrong, but atm only blip.tv works anyway

*New possible issue - 
It may be that the new .94 gstreamer packages will cause Totem (Videos) some real issue - will explore further, initial error after upgrading gst*
totem: symbol lookup error: /usr/lib/libtotem.so.0: undefined symbol: gst_message_parse_duration

Edit: it would appear the totem will just need a simple rebuild against the new .94 base

---

### Post by mc4man on 2012-09-14
> Ok, I can verify that Totem 3.5.90 uses both the new GNOME App Menu and a traditional File Edit View menu but Unity only shows the GNOME App Menu. I commented on bug 999827, which I believe is the tracking bug for this type of problem.

I see the opposite - by default the 'traditional' are in the unity panel. After returning those menu's to the totem window then the app menu shows in the panel (open; open location; fullscreen; preferences, ect.
In any event totem does need ALL it's menus to be useful

---

### Post by jbicha on 2012-09-15
> **mc4man said:**
> 
grilo isn't in the listed plugins, have been moved to the extra plugin package & are auto enabled/loaded once installed

Ah, confusing. Ok, so I guess grilo works as expected here.

> **mc4man said:**
> 
Edit: it would appear the totem will just need a simple rebuild against the new .94 base
Thanks, I just pushed a rebuild to the PPA.

---

### Post by mc4man on 2012-09-15
> **jbicha said:**
> Ah, confusing. Ok, so I guess grilo works as expected here.
.
To some extent, unless you are getting full function?

I figure the 0.2 release works well somewhere , whatever Juan A. Suarez Romero, Cosimo Cecchi, ect. are using, though  certainly not here.

---

### Post by jbicha on 2012-09-15
By "expected" I meant that I confirm your results. Browse basically works; search isn't working for many providers. Interestingly, there's a Vimeo search provider, but I don't see Vimeo in Browse.

You're welcome to report the grilo bugginess to the Totem devs if you like.

I see now that there has been some fixes for the mozilla plugin posted to Totem's git repository so hopefully that will be working in the next GNOME development release next week.

---

### Post by mc4man on 2012-09-15
I have to thank jbicha for taking the time to try to fix the 0.10.x plugin. (h264parser

Unfortunately due to My idiocy in not completely describing what needed to be done the new package won't  work to fix this.

For that I'm truly sorry, hopefully can be squared away..

---


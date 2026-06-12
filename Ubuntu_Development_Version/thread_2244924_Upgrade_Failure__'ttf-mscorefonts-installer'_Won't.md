---
title: "Upgrade Failure:  'ttf-mscorefonts-installer' Won't Download"
date: 2014-09-19
forum: Ubuntu Development Version
---

### Post by VinDSL on 2014-09-19
Utopic has been working amazing well, the past week, or so.  However...

Anybody else experiencing this popup?!?!?


[[img]http://vindsl.com/images/vindsl-desktop-19-sep-2014-1(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-19-sep-2014-1.png")


Been seeing this for a week or so.  I get it once a day.

Funny things is, I don't even run MS fonts.  I hate them.  It's one of the things I delete during a fresh install.

Hrm...

---

### Post by VinDSL on 2014-09-19
Couldn't find anything in the log files, so did the update from CLI.  Here is the relevant error:

```
<SNIP>

ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe
Fetched 552 B in 11s (47 B/s)                                                  

E: Failed to fetch http://downloads.sourceforge.net/corefonts/andale32.exe  Hash Sum mismatch

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...

<SNIP>

```

Can someone confirm, please, and I'll post a bug?

---

### Post by Elfy on 2014-09-19
yes I've seen it

I also thought I'd marked a bug as affecting me - appears not ...

---

### Post by VinDSL on 2014-09-19
Okie dokie.

I'll start a new one:  [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1371783](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1371783)

Thx!

---

### Post by mc4man on 2014-09-19
Maybe try again, seems ok (here
> Selecting previously unselected package ttf-mscorefonts-installer.
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for fontconfig (2.11.1-0ubuntu3) ...
Processing triggers for update-notifier-common (3.156) ...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 1s (175 kB/s)                                                               
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe) [554 kB]
Fetched 554 kB in 2s (215 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe) [168 kB]
Fetched 168 kB in 0s (241 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe) [246 kB]
Fetched 246 kB in 1s (200 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe) [646 kB]
Fetched 646 kB in 0s (665 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe) [392 kB]
Fetched 392 kB in 0s (507 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe) [173 kB]
Fetched 173 kB in 0s (246 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe) [662 kB]
Fetched 662 kB in 1s (405 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe) [357 kB]
Fetched 357 kB in 0s (494 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe) [352 kB]
Fetched 352 kB in 0s (408 kB/s)                                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe) [185 kB]
Fetched 185 kB in 0s (212 kB/s)                                                              

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
ect....

---

### Post by VinDSL on 2014-09-19
Thx, but still not working here...

---

### Post by cariboo on 2014-09-20
I had the problem on an earlier install, but the last one I did about a week ago seems to have gone the way it should. I haven't been bothered by the message for the last several weeks.

---

### Post by VinDSL on 2014-09-20
I give up.  I'm convinced that there's something wrong with their servers.

Every file was being downloaded from a different mirror, and certain mirrors were working, and others weren't.

To put it another way, it was a crap-shoot/russian-roulette as to how far the upgrade progressed before it puked.

 I cheated -- manually installed the Debian 'ttf-mscorefonts-installer' 3.5 unstable package -- and called it a day. :p

---

### Post by VinDSL on 2014-09-20
BTW, to whom it may concern, here's the package I installed:

[https://packages.debian.org/sid/all/ttf-mscorefonts-installer/download](https://packages.debian.org/sid/all/ttf-mscorefonts-installer/download)

I installed it using GDebi (with Lintian installed) so I could check the output before installation.  ;)

---

### Post by Cavsfan on 2014-09-21
I had that exact same problem in Utopic Mate remix. It got an error in terminal when ttf-mscorefonts-installer was initially installed.
Then an annoying popup just like the one you posted and it didn't ever appear to work when I clicked on "Run this action now".

Then an update came down the pipe and it was fixed. I haven't seen it since.

---

### Post by VinDSL on 2014-09-21
Interesting!

Well, I'll try to install it using the official repos, about once a week, and see if it stops crashing with hash sum mismatches, header errors on the mirrors, and so forth, and so on.

Thx

---

### Post by Cavsfan on 2014-09-23
> **VinDSL said:**
> Interesting!

Well, I'll try to install it using the official repos, about once a week, and see if it stops crashing with hash sum mismatches, header errors on the mirrors, and so forth, and so on.

Thx

You're welcome. I was curious to find that anyone else had this same problem. I haven't seen it in quite a while now and I never seen it on Utopic, just on Utopic Mate Remix.
This Utopic install is the same one used for Trusty, just changed the source names.

---

### Post by HunterZ on 2014-11-02
I'm also affected by this after updating Kubuntu 14.04 to 14.10.

---

### Post by cariboo on 2014-11-03
Thread closed, as we are now discussing Vivid (15.04)

---


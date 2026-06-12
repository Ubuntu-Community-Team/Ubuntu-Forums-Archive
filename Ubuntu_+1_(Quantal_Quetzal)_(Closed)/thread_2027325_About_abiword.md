---
title: "About abiword"
date: 2012-07-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-07-16
In Precise we released a very unstable version of 'abiword':

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

If you bother reading that forum post you'll see I posted a work-around:

[http://ubuntuforums.org/showpost.php?p=12093593&postcount=20](http://ubuntuforums.org/showpost.php?p=12093593&postcount=20)

But, as it says, there is now a PPA to revert to version 2.8.6:

[http://ubuntuforums.org/showpost.php?p=12106840&postcount=25](http://ubuntuforums.org/showpost.php?p=12106840&postcount=25)

BTW more testing of that PPA in Precise is quite welcome :)

But my reason for posting here is that my request to revert the package version for 12.04.1 is very likely to be denied :(

I think it's much more realistic to get 'abiword' working properly in Quantal and then get those updates introduced into Precise.

So I'd appreciate everyone inclined to do so to test 'abiword' and report results to that bug report. Does that make sense :confused:

---

### Post by xebian on 2012-07-16
It got in when they synced with Debian testing?  It's now ver. 2.9.2, and to get to Debian testing with that error is amazing.  BTW I don't see that problem of yours in wheezy.

---

### Post by kansasnoob on 2012-07-16
> **xebian said:**
> It got in when they synced with Debian testing?  It's now ver. 2.9.2, and to get to Debian testing with that error is amazing.  BTW I don't see that problem of yours in wheezy.

It was in Debian unstable I think :confused:

But I don't think how it happened is nearly as important as being sure it's fixed in Quantal :)

Then we can try to get that fix ported to Precise either through proposed updates or backports :D

---

### Post by xebian on 2012-07-16
> **kansasnoob said:**
> It was in Debian unstable I think :confused:

But I don't think how it happened is nearly as important as being sure it's fixed in Quantal :)

Then we can try to get that fix ported to Precise either through proposed updates or backports :D

Not clear to me if it has been fixed in QQ for you, but ver 2.9.2 in wheezy is working ok for me.  QQ looks like have the same version - 2.9.2+svn20120603-1

---

### Post by screaminj3sus on 2012-07-16
Yeah the current abiword in the precise repos is COMPLETELY unusable. scrolling doesn't even work for me and the text rendering is totally fubar among other issues. I ended up uninstalling it immediately and just going back to libreoffice.

---

### Post by mc4man on 2012-07-17
Seeing as this thread is "All Variants"  - in _Ubuntu_ 12.10 abiword seems just fine. 
(abiword  2.9.2+svn20120603-1

---

### Post by kansasnoob on 2012-07-17
> **screaminj3sus said:**
> Yeah the current abiword in the precise repos is COMPLETELY unusable. scrolling doesn't even work for me and the text rendering is totally fubar among other issues. I ended up uninstalling it immediately and just going back to libreoffice.

This is what I get also. Mouse-wheel scrolling only works if I hold the cursor over a "standard" scrollbar, and not at all with 'overlay-scrollbars'.

Not sure if you mean the same as me by "text rendering", but particularly with long, multi-page docs I sometimes just get large gray or black blocks either in between areas of text or sometimes blocking the text altogether.

Same thing in both Precise and Quantal.

Pretty much unusable :(

AFAIK Libreoffice still has no plug-in to read existing docs and I began using Abiword in Win ME so I have a lot of old documents that require Abiword, although they can also be read in Firefox.

---

### Post by kansasnoob on 2012-07-17
> **mc4man said:**
> Seeing as this thread is "All Variants"  - in _Ubuntu_ 12.10 abiword seems just fine. 
(abiword  2.9.2+svn20120603-1

Not good here, try scrolling and viewing multi-page documents.

Abiword dev says:

> Dear Canonical,
It fills me with frustration that you chose to distribute our
development version of abiword-2.92 with your LTS 12.04 release. This
was done without any consultation with the abiword community AT ALL.
Please revert to abiword-2.8.6 ASAP.If this is not possible please
advise me as to how you plan to fix these bugs since you don't upgrade
packages either.

Martin Sevior

And most recently:

> Hi everyone,

abiword-2.8.6 will not break an abiword-2.9.2 configuration.

If you can't roll back to 2.8.6 your should at least upgrade to 2.9.3
which has far fewer bugs.

Cheers

Martin

---

### Post by mc4man on 2012-07-17
"Not good here, try scrolling and viewing multi-page documents."

Absolutely fine, just scrolled up & down thru a 190 pg. docu.
Maybe there there is some difference on hardware, video drivers?, don't know...

---

### Post by kansasnoob on 2012-07-17
> **mc4man said:**
> "Not good here, try scrolling and viewing multi-page documents."

Absolutely fine, just scrolled up & down thru a 190 pg. docu.
Maybe there there is some difference on hardware, video drivers?, don't know...

Jeremy Bicha also mentioned that it may be hardware related so that may very well be the case :confused:

The big thing to me is that abiword dev basically says, "yikes, you didn't ship that did you"! Certainly not their exact words, just paraphrasing ;)

I feel that I personally failed in testing abiword adequately during Precise testing :oops:

---

### Post by mc4man on 2012-07-17
Out of curiosity installed abiword on 12.04, same machine where it works fine, (for the most part),  in 12.10
While there is no issue scrolling it appears a large part of the gui is missing, just whitespace & or grey boxes

---

### Post by kansasnoob on 2012-07-17
> **mc4man said:**
> Out of curiosity installed abiword on 12.04, same machine where it works fine, (for the most part),  in 12.10
While there is no issue scrolling it appears a large part of the gui is missing, just whitespace & or grey boxes

It effects both 12.04 and 12.10 for me, but only gray and black boxes, no whitespace :confused:

What really shaped my opinion is the comments from abiword dev :)

---

### Post by philinux on 2012-07-17
For testing purposes I installed it and opened the british-english dictionary from /usr/share/docs

It did grey out but now displays it. Here's a screen shot. Scrolling and page up down work fine. I had to put it into view normal to get rid of black space on right. 

Acer 1410 aspire.
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
```

---

### Post by kansasnoob on 2012-07-17
> **philinux said:**
> For testing purposes I installed it and opened the british-english dictionary from /usr/share/docs

It did grey out but now displays it. Here's a screen shot. Scrolling and page up down work fine. I had to put it into view normal to get rid of black space on right. 

Acer 1410 aspire.
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
```

Hmmm, this makes me wonder about the source of the page(s) being viewed :confused:

I'm gonna be too busy today to test much more but ASAP I'll compare the behavior between newly created docs and older docs.

Some of my older abiword docs were created clear back in Win ME and Lindows :)

Yes, there was a Lindows:

[http://en.wikipedia.org/wiki/Linspire](http://en.wikipedia.org/wiki/Linspire)

Really:

[http://en.wikipedia.org/wiki/Microsoft_v._Lindows](http://en.wikipedia.org/wiki/Microsoft_v._Lindows)

And Xandros broke a promise:

[http://www.linspire.com/](http://www.linspire.com/)

But that's totally OT, just still gets me riled up :mad:

---

### Post by screaminj3sus on 2012-07-17
> **kansasnoob said:**
> This is what I get also. Mouse-wheel scrolling only works if I hold the cursor over a "standard" scrollbar, and not at all with 'overlay-scrollbars'.

Not sure if you mean the same as me by "text rendering", but particularly with long, multi-page docs I sometimes just get large gray or black blocks either in between areas of text or sometimes blocking the text altogether.

Same thing in both Precise and Quantal.

Pretty much unusable :(

AFAIK Libreoffice still has no plug-in to read existing docs and I began using Abiword in Win ME so I have a lot of old documents that require Abiword, although they can also be read in Firefox.

well yeah, I guess just 'rendering' would be a more appropriate description. I was getting the crazy gray boxes and such that others were getting

---

### Post by jerrylamos on 2012-07-19
Bug #1026867 Abiword crash when pasting in some text copied from web site Firefox browser.  Turned right around and pasted into LibreOffice no problem.

Tried again to paste into Abiword crashed again.

I did such pasting from another web site earlier today O.K. with Abiword.

Jerry

---

### Post by kansasnoob on 2012-08-21
Looking good in Quantal now:

> abiword (2.9.2+svn20120603-2) unstable; urgency=low

  * build verbosity increased with --disable-silent-rules
  * lintian-overrides:
    + 'hardening-no-fortify-functions' (false-positives).
    + 'dev-pkg-without-shlib-symlink' (libabiword-2.9.so is a library,
      not a symlink).
  * new patches:
    + format-hardening.patch to avoid FTBFS on --with-gtk2 build.
    + fix-wheel-scrolling.patch (Closes: #672149).
    + fix-paste.patch (backported) with fix for
      "Crash on unicode character paste" (Closes: #681060).
    + no-dbl-buf.patch to disable double buffering in order to prevent
      crash on 'Paste Unformatted'.

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Fri, 17 Aug 2012 11:08:23 +1000


---

### Post by kansasnoob on 2012-09-01
Getting better all the time:

> abiword (2.9.2+svn20120603-5) unstable; urgency=low

  * xz compression for binary packages.
  * new backported patch to fix gtk3 presentation (Closes: #682613).

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Thu, 30 Aug 2012 13:24:15 +1000

abiword (2.9.2+svn20120603-4) unstable; urgency=low

  * new backported patches:
    + r31490_fix-crash-if-inserting-a-footnote.patch
    + r31566_rearrange-date-and-time-formats.patch
    + r31576_remove-separator-from-insert-dialogs.patch
    + r31748_fix-crash-with-copy-paste.patch
    + r31749_fix-bug-with-copy-paste.patch
    + r31753_fix-crash-on-paste.patch
    + r31755_fix-crash-with-create-and-modify-styles-dialog.patch
    + r31767_fix-possible-crash.patch
    + r31768_correct-horizontal-scroll-limit.patch
    + r31842_fix-crash-13401.patch
    + r31843_prevent-crash.patch
    + r31847_fix-program-hanging-during-paste-unformatted.patch
  * old backported patches are renamed to have revision number in file name.
  * lintian-override for 'no-symbols-control-file' (not useful for CPP).

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Fri, 24 Aug 2012 11:09:56 +1000

abiword (2.9.2+svn20120603-3) unstable; urgency=low

  * Replace no-dbl-buf.patch with backported fix-dbl-buff.patch
    to fix 'Paste Unformatted' and re-enable double buffering.

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Fri, 17 Aug 2012 20:16:51 +1000


I hope I can convince the devs to include these updates in Precise proposed or backports soon :)

---

### Post by stedevil on 2012-09-26
For completion 

> 
abiword (2.9.2+svn20120603-7) unstable; urgency=low


  * new backported patches:
    + r31854_bug-13397-RTF-import-fix-missing-text.patch
      to fix missing numbers in beginning of lines on RTF/DOC import
      (Closes: #688552).
    + r31855_gtk3-bug-13405.patch
    + r31877_start-layout-only-after-document-is-fully-loaded.patch
    - removed unused (duplicate) patch file.

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Mon, 24 Sep 2012 11:10:44 +1000

abiword (2.9.2+svn20120603-6) unstable; urgency=low


  * debian/watch to find all available versions with fallback to latest-dev.
  * new patch to fix collab backend if built --with-gtk2 and to fix FTBFS
    without libgtk-3-dev (finally abiword can be built for GTK2).
  * new backported patches:
    + r31861_fix-FTBFS-with-fake-collab-backend.patch
    + r31901_fix-crash-on-open-doc-with-table-in-header.patch
    + r31909_fix-doc-corruption.patch
    + r31910_fix-memory-leak-in-ABW-exporter.patch
    + r31914_fix-clip-art-window.patch (Closes: #672150)
  * beautified list of Build-Depends.
  * libchamplain-gtk-0.12-dev (optional build-dependency) is added to
    Build-Depends (commented, to conform with freeze policy).

 -- Dmitry Smirnov <onlyjob@member.fsf.org>  Thu, 13 Sep 2012 13:08:48 +1000


---

### Post by kansasnoob on 2012-10-05
Things seem to be looking good in Quantal now :D

But I really need some help getting this version into Precise - probably the Precise proposed repos first, and then moved into Precise updates.

I got slammed pretty hard [here]("https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621/comments/33") about not using the proper etiquette in trying to get Abiword fixed prior to 12.04.1.

I know in the past that I did have to resort to complaining at mailing lists to turn up the heat on certain bugs but I'm getting old. I'm running out of gas and I need to try and get this fixed in 12.04.

I rather think more effort should be focused on actually fixing bugs than focusing on demeaning the efforts of us "common folk" when it comes to our individual abilities :mad:

---

### Post by kansasnoob on 2012-10-08
I've been studying a little bit:

[https://wiki.ubuntu.com/StableReleaseUpdates#When](https://wiki.ubuntu.com/StableReleaseUpdates#When)

> Stable release updates will, in general, only be issued in order to fix high-impact bugs. Examples of such bugs include:

    Bugs which may, under realistic circumstances, directly cause a security vulnerability. These are done by the security team and are documented at SecurityTeam/UpdateProcedures.

    Bugs which represent severe regressions from the previous release of Ubuntu. This includes packages which are totally unusable, like being uninstallable or crashing on startup.

    Bugs which may, under realistic circumstances, directly cause a loss of user data
    **[COLOR="Red"]Bugs which do not fit under above categories, but (1) have an obviously safe patch and (2) affect an application rather than critical infrastructure packages (like X.org or the kernel).[/COLOR]**
    For Long Term Support releases we regularly want to enable new hardware. Such changes are appropriate provided that we can ensure to not affect upgrades on existing hardware. For example, modaliases of newly introduced drivers must not overlap with previously shipped drivers.
    New versions of commercial software in the Canonical partner archive.

    FTBFS(Fails To Build From Source) can also be considered. Please note that in main the release process ensures that there are no binaries which are not built from a current source. Usually those bugs should only be SRUed in conjunction with another bug fix. 

For new upstream versions of packages which provide new features, but don't fix critical bugs, a backport should be requested instead. 

So I would certainly think it would be appropriate to file a new bug report against abiword for Precise and request that we upgrade to either the stable Quantal version or I also found a slightly older version in one of Jeremy Bicha's PPA's:

[https://launchpad.net/~jbicha/+archive/dev/+packages](https://launchpad.net/~jbicha/+archive/dev/+packages)

I'm just trying to figure out the best way to do this, by "best way" I mean whatever will get it done ;)

---


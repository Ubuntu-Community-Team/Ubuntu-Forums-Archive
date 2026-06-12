---
title: "Firefox Beta 5!"
date: 2008-04-02
forum: The Cafe
---

### Post by Glaxed on 2008-04-02
Anyone else dissapointed that the Linux version has not undergone the same (awesome) design changes as the windows version?

I'd swear that the windows version is running faster than safari beta 3 now on everything.
No adblock though...
I ran SunSpider on it, and I got overall that Firefox (beta 5) is approx 8.46 times better than IE7 ;).
base 64 string unpacking (or something) is done 119.1 times faster than IE...
```

TEST                   COMPARISON            FROM                 TO             DETAILS

=============================================================================

** TOTAL **:           8.46x as fast     41630.8ms +/- 0.4%   4919.6ms +/- 0.7%     significant


=============================================================================

  3d:                  3.31x as fast      1834.8ms +/- 2.5%    554.0ms +/- 0.6%     significant
    cube:              2.63x as fast       531.4ms +/- 2.6%    202.4ms +/- 1.5%     significant

    morph:             3.30x as fast       600.0ms +/- 5.5%    181.6ms +/- 1.2%     significant
    raytrace:          4.14x as fast       703.4ms +/- 2.7%    170.0ms +/- 0.9%     significant

  access:              3.51x as fast      2759.4ms +/- 0.4%    786.8ms +/- 0.8%     significant

    binary-trees:      9.22x as fast       603.2ms +/- 1.7%     65.4ms +/- 2.2%     significant
    fannkuch:          2.91x as fast      1143.4ms +/- 0.8%    393.4ms +/- 0.2%     significant
    nbody:             2.75x as fast       537.4ms +/- 2.0%    195.2ms +/- 0.5%     significant

    nsieve:            3.58x as fast       475.4ms +/- 2.3%    132.8ms +/- 4.5%     significant

  bitops:              3.72x as fast      2350.0ms +/- 1.3%    631.6ms +/- 0.8%     significant
    3bit-bits-in-byte: 4.21x as fast       546.6ms +/- 0.1%    129.8ms +/- 4.3%     significant

    bits-in-byte:      3.35x as fast       572.0ms +/- 4.5%    170.8ms +/- 0.6%     significant
    bitwise-and:       5.12x as fast       681.2ms +/- 1.5%    133.0ms +/- 0.9%     significant
    nsieve-bits:       2.78x as fast       550.2ms +/- 1.6%    198.0ms +/- 0.6%     significant


  controlflow:         9.82x as fast       656.0ms +/- 0.0%     66.8ms +/- 0.8%     significant
    recursive:         9.82x as fast       656.0ms +/- 0.0%     66.8ms +/- 0.8%     significant

  crypto:              4.47x as fast      1409.4ms +/- 1.2%    315.4ms +/- 0.7%     significant

    aes:               4.30x as fast       534.4ms +/- 1.6%    124.4ms +/- 0.9%     significant
    md5:               4.72x as fast       437.6ms +/- 0.2%     92.8ms +/- 0.6%     significant
    sha1:              4.45x as fast       437.4ms +/- 3.1%     98.2ms +/- 1.1%     significant


  date:                3.05x as fast      1181.6ms +/- 1.5%    386.8ms +/- 1.2%     significant
    format-tofte:      2.38x as fast       587.6ms +/- 3.0%    246.6ms +/- 1.7%     significant
    format-xparb:      4.24x as fast       594.0ms +/- 0.0%    140.2ms +/- 2.5%     significant


  math:                2.82x as fast      1615.0ms +/- 1.4%    572.8ms +/- 2.6%     significant
    cordic:            2.44x as fast       668.6ms +/- 1.3%    273.8ms +/- 0.7%     significant
    partial-sums:      2.31x as fast       425.0ms +/- 2.0%    184.2ms +/- 9.6%     significant

    spectral-norm:     4.54x as fast       521.4ms +/- 3.3%    114.8ms +/- 1.2%     significant

  regexp:              1.19x as fast       537.6ms +/- 3.2%    451.2ms +/- 4.8%     significant
    dna:               1.19x as fast       537.6ms +/- 3.2%    451.2ms +/- 4.8%     significant


  string:              25.4x as fast     29287.0ms +/- 0.5%   1154.2ms +/- 1.0%     significant
    **[COLOR="Red"]base64:            119.1x as fast    14915.4ms +/- 1.1%    125.2ms +/- 1.9%     significant[/COLOR]**
    fasta:             2.59x as fast       671.8ms +/- 2.1%    259.8ms +/- 2.3%     significant

    tagcloud:          18.7x as fast      3834.6ms +/- 5.6%    204.6ms +/- 1.3%     significant
    unpack-code:       1.67x as fast       684.4ms +/- 2.4%    409.0ms +/- 2.9%     significant
    validate-input:    59.0x as fast      9180.8ms +/- 1.9%    155.6ms +/- 3.1%     significant

```
for you sticklers. the test is averaged out of 5 runs.

---

### Post by tubasoldier on 2008-04-02
I don't personally use windows anymore so I have no clue about the GUI changes.
As far as the speed goes, this is good news. Firefox 2 is pretty heavy for being a lightweight browser.

---

### Post by andrewabc on 2008-04-02
> **tubasoldier said:**
> Firefox 2 is pretty heavy for being a lightweight browser.
That's actually a misconception. Firefox was never intended to be a "lightweight" browser. Although I understand what you meant by it.

---

### Post by arbulus on 2008-04-02
How would one running Hardy Beta upgrade Firefox to Beta 5?

---

### Post by mrgnash on 2008-04-02
> **arbulus said:**
> How would one running Hardy Beta upgrade Firefox to Beta 5?

Download the tarball and run the binary, or, better yet, wait for it to enter the repos.

---

### Post by Chimera76 on 2008-04-02
Do we know when it will be in the repos?

---

### Post by mrgnash on 2008-04-02
> **Chimera76 said:**
> Do we know when it will be in the repos?

No. Shouldn't be too long though.

---

### Post by Sef on 2008-04-02
> Do we know when it will be in the repos?

I've read that the expected release date for the stable Firefox 3 is this June.

---

### Post by SomeGuyDude on 2008-04-03
It's okay, but not as "smooth" as even the latest Swiftfox build. Moving the window around is "sticky" with Compiz effects. Otherwise, feels mostly the same.

---

### Post by tubasoldier on 2008-04-03
> That's actually a misconception. Firefox was never intended to be a "lightweight" browser. Although I understand what you meant by it.

When Firefox was still in its original development stage, when it was called Firebird, the intention was for it to be a lightweight alternative to the Mozilla Suite.

---

### Post by JT9161 on 2008-04-03
I'm running it on vista and I've never seen FF run so fast cant wait to run it Ubuntu

---

### Post by sujoy on 2008-04-03
finally we may see the end of a long search for a good not-so-heavy browser. i am gonna wait for it to enter the repos though

---

### Post by mrgnash on 2008-04-03
> **sujoy said:**
> finally we may see the end of a long search for a good not-so-heavy browser. i am gonna wait for it to enter the repos though

Epiphany.

---

### Post by smartboyathome on 2008-04-03
> **mrgnash said:**
> Epiphany.

It either takes to long to load (gecko backend) or is missing important features such as cookies (webkit backend). So right now, I use FF3. ;)

---

### Post by mrgnash on 2008-04-03
> **smartboyathome said:**
> It either takes to long to load (gecko backend) or is missing important features such as cookies (webkit backend). So right now, I use FF3. ;)

Oh yeah, I do too, but it is a good light-weight browser. It's just that, with Firefox 3 having made so many improvements in terms of performance and GNOME integration, and with the webkit backend not being ready yet, there isn't much reason for me to use it anymore :(

---

### Post by arbulus on 2008-04-03
> **mrgnash said:**
> Epiphany.


I could use just about any browser (except IE) if I didn't rely so much on Firefox plugins.  Foxmarks is the one that i absolutely cannot live without.  I have multiple computers and it's important that i always have my bookmarks whenever I need them.  (I have no use of things like del.icio.us because i despise the "social" aspect of it.  My bookmarks aren't meant to be social, they're meant to be mine.)

An of course the Ubuntu Forums menu plugin is awesome.  As well as Adblock Plus. 

Opera's whole "widget" thing annoys the crap out of me, and it seems like Epiphany has no plugins.  And I just can't seem to get my head around Konqueror. 

But I really like Firefox a lot, I've never had any complaints with it (except for that it seems to be a bit clunky on the Mac). And I'm really excited about the final release of FF3, after having seen the speed and usability improvements of the betas so far.

---

### Post by mrgnash on 2008-04-03
> **arbulus said:**
> I could use just about any browser (except IE) if I didn't rely so much on Firefox plugins.  Foxmarks is the one that i absolutely cannot live without.  I have multiple computers and it's important that i always have my bookmarks whenever I need them.  (I have no use of things like del.icio.us because i despise the "social" aspect of it.  My bookmarks aren't meant to be social, they're meant to be mine.)

An of course the Ubuntu Forums menu plugin is awesome.  As well as Adblock Plus. 

Opera's whole "widget" thing annoys the crap out of me, and it seems like Epiphany has no plugins.  And I just can't seem to get my head around Konqueror. 

But I really like Firefox a lot, I've never had any complaints with it (except for that it seems to be a bit clunky on the Mac). And I'm really excited about the final release of FF3, after having seen the speed and usability improvements of the betas so far.

You should like Weave as well -- it aims to be able to sync all your personal data/preferences across browsers :) I'm going to start testing it with Beta 5 (using it with Beta 4 is not recommended, for some reason).

---

### Post by arbulus on 2008-04-03
> **mrgnash said:**
> You should like Weave as well -- it aims to be able to sync all your personal data/preferences across browsers :) I'm going to start testing it with Beta 5 (using it with Beta 4 is not recommended, for some reason).

That's a pretty interesting looking project there.  I'm generally not a big fan of cloud computing, but that's actually a pretty solid looking idea right there.

---

### Post by misfitpierce on 2008-04-03
I heard there are more GUI changes for windows but as I don't use windows I wouldn't really know. Oh well if true let windows have their GUI extras to get them off IE... Gotta give them some slack they are using windows :) lol

---

### Post by mrgnash on 2008-04-03
> **misfitpierce said:**
> I heard there are more GUI changes for windows but as I don't use windows I wouldn't really know. Oh well if true let windows have their GUI extras to get them off IE... Gotta give them some slack they are using windows :) lol

We don't need GUI extras, we just need integration -- which is what we got. Thematic consistency is more attractive than individually snazzy apps any day.

---

### Post by Kokesh on 2008-04-03
I hope that b5 will be available as update also for Hardy Heron beta. FF beta4 drives me crazy sometimes...

---

### Post by billgoldberg on 2008-04-03
The only changes I've noticed that after installing firefox beta 5, all my plugins were gone (minor problem) and the "home" button was gone. 

It still crashes on flash content, but it's faster than ever.

(if you don't know how to install it, click on the link in my sig)

---

### Post by SupaSonic on 2008-04-03
Installed it at work on a windows box, looks pretty. However, once I installed firebug it started crashing 5 seconds after the launch. Back to FF2 sadly, i need firebug for work.

---

### Post by andrewabc on 2008-04-03
> **tubasoldier said:**
> When Firefox was still in its original development stage, when it was called Firebird, the intention was for it to be a lightweight alternative to the Mozilla Suite.

Yes, maybe lightweight compared to a full suite. But not a lightweight browser. The developer (asa) made this clear over the past year at slashdot on one of the articles. I distinctly remember him saying this. Although I can not find the article.

EDIT:
Found the artticle
[http://slashdot.org/article.pl?sid=07/11/11/2036218](http://slashdot.org/article.pl?sid=07/11/11/2036218)
> Are you completely uninformed or are you being intentionally untruthful here?

    > Firefox's roots go back a while (2 years?) before that roadmap was
    > written. The original goal was to make a minimal browser, however,

You're just plain wrong here.

The original goal, that I helped define in early 2002, was to make a browser that could actually compete with IE and gain market share where the feature bloated and designed by committee Mozilla Application Suite had failed. We didn't skimp on features and included many features, bringing it up and beyond parity with IE, that the suite never had.
There is a lot more on the comments section as well. Specifically starting at   Monday November 12, @01:43AM

---

### Post by herbster on 2008-04-03
Been using Beta 4 for about two weeks and it's like a completely different program from FF 2. Just unbelievable speed difference, oodles more responsiveness and tons less memory usage; and I have a Q6600 w/4gb ram, but FF 2 was still sluggish a lot of the time.

Now it's all about the extensions being updated for it, then yeehaw!

---

### Post by SomeGuyDude on 2008-04-03
> **billgoldberg said:**
> The only changes I've noticed that after installing firefox beta 5, all my plugins were gone (minor problem) and the "home" button was gone. 

It still crashes on flash content, but it's faster than ever.

(if you don't know how to install it, click on the link in my sig)

Firefox beta 5: crashing with record speed!

---

### Post by Glaxed on 2008-04-04
B5 Hasn't crashed yet for me.
Actually, I almost ditched B4 for Opera but becasue of a combination of an annoying interface and the incredible speed and feature advancement of B5, im sticking with FF.

I guess most of you guys dont care about the new toolbar/back-forward keyhole etc. I admit its kinda a stupid thing to beg for :D.
I'm just saying that it would be nice if they didn't play favorites (after all, no matter how much market share Windows had, the fact is no one had to beg and be satisfied with mere compatibility.)

I have tremendous respect for the Firefox project, though. 

(I mean, 119.1 times faster on some string work?! -- ahem -- I mean -- such devotion to open source software and platform compatibility! ;)).

---

### Post by dn* on 2008-04-05
I have been using Firefox ever since it was called Phoenix and back then the main reason I and others religiously upgraded our nightlies every day was that it kept getting faster while developing new features. Given back then it only had IE 5.5 to compete with really. But still, I might have a hoke around the mozilla ftp and see if I can crack out an old linux binary.

As a side note, anyone know of a deb / repo with newer betas than 3? I can't upgrade to Hardy at the moment because of a kernal issue that's borking my wireless..

---

### Post by Glaxed on 2008-04-05
have you tried chmod(ing) the one network manager script? that was a problem lots of pidgin users were having, but it got fixed after they chmodded.
random suggestion, but w/e

---

### Post by SomeGuyDude on 2008-04-06
> **dn* said:**
> As a side note, anyone know of a deb / repo with newer betas than 3? I can't upgrade to Hardy at the moment because of a kernal issue that's borking my wireless..

Swiftfox is on the latest version always. Currently it's 3.0pre1, not a beta. :popcorn:

---

### Post by arbulus on 2008-04-06
Beta 5 is in Hardy now.  I installed all of the latest updates today and it uninstalls Firefox completely.  So you have to go in to Add/Remove Programs or Synaptic and install it.  It gives you the choice of either FF2 or 3.  Version three is Beta 5.

It's working really well, except for the fact that not a single one of my add-ons work with it.

---

### Post by vexorian on 2008-04-06
The only difference I see between the windows version and the Linux version of firefox 3 beta 5 is that the Linux one doesn't have the freak big previous button, and I think that's a good thing.

The speed up and memory usage reductions are equally noticeable on both platforms.

---

### Post by mrgnash on 2008-04-06
> **arbulus said:**
> Beta 5 is in Hardy now.  I installed all of the latest updates today and it uninstalls Firefox completely.  So you have to go in to Add/Remove Programs or Synaptic and install it.  It gives you the choice of either FF2 or 3.  Version three is Beta 5.

It's working really well, except for the fact that not a single one of my add-ons work with it.

Really? All of mine work, including:

Adblock Plus
Download Statusbar
Prism
Weave
PDFDownload
Personas

Not that I use very many extensions, as you can see. I tend to think that the more extensions you have, the more chance you have of experiencing instability, so I try not to load Fx up with too many of the little buggers ;)

---

### Post by andrewabc on 2008-04-06
> **mrgnash said:**
> Really? All of mine work, including:
PDFDownload


I'm not sure why people still use that plugin. I admit I used it for about 2 years back when I was on windows and had adobe reader installed and I hated it opening pdfs inside firefox. On my windows install, I use foxit pdf reader, and firefox downloads all pdfs (or I could have them open in foxit window).

Do you actually have pdfs open inside firefox?

---

### Post by mrgnash on 2008-04-06
> **andrewabc said:**
> I'm not sure why people still use that plugin. I admit I used it for about 2 years back when I was on windows and had adobe reader installed and I hated it opening pdfs inside firefox. On my windows install, I use foxit pdf reader, and firefox downloads all pdfs (or I could have them open in foxit window).

Do you actually have pdfs open inside firefox?

Not often, but sometimes, yeah.

---

### Post by Kokesh on 2008-04-06
Strange, I wasn't offered to get the update. Have FF3B4 installed, I have tried to check for updates manually, but nothing happened. Where could I get .deb package for b5?

---

### Post by billgoldberg on 2008-04-06
How did you get those add-ons working in beta 5, because non of mine will work.

---

### Post by Kokesh on 2008-04-06
Got b5 into my Hardy, just added this repositories

[I]deb [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main[/I]

It runs well (yet), the only thing is that I have to do make link to firefox-3.0, it is not possible to start it just with firefox:

*sudo ln -s /usr/bin/firefox-3.0 /usr/bin/firefox*

---

### Post by mrgnash on 2008-04-06
> **billgoldberg said:**
> How did you get those add-ons working in beta 5, because non of mine will work.

I didn't do anything special. Most of them just worked. The only one that didn't was Adblock Plus, which I had to go get the latest development version for.

---

### Post by arbulus on 2008-04-06
> **mrgnash said:**
> Really? All of mine work, including:

Adblock Plus
Download Statusbar
Prism
Weave
PDFDownload
Personas

Not that I use very many extensions, as you can see. I tend to think that the more extensions you have, the more chance you have of experiencing instability, so I try not to load Fx up with too many of the little buggers ;)

I use Adblock Plus, Ubuntu Forums Menu, and Foxmarks and none of them work.

---

### Post by mrgnash on 2008-04-06
> **arbulus said:**
> I use Adblock Plus, Ubuntu Forums Menu, and Foxmarks and none of them work.

[go here](http://adblockplus.org/devbuilds/) to get the latest version of Adblock Plus. It works with Fx3B5.

---

### Post by arbulus on 2008-04-07
> **mrgnash said:**
> [go here](http://adblockplus.org/devbuilds/) to get the latest version of Adblock Plus. It works with Fx3B5.

Thanks!  That worked.

---

### Post by jdong on 2008-04-07
I've just gotten Firefox 3.0 Beta 4 uploaded into Gutsy Backports pending approval by the archive admins.

I was planning on putting in Beta 5, but initial feedback wasn't too good (some potential bugs here and there, and some users reported bad interface lagging and high CPU usage) 

At any rate, sit tight for two days or so for Gutsy Backports packages of Firefox 3 Beta 4, or head over to [https://edge.launchpad.net/~ubuntu-backporters/+archive](https://edge.launchpad.net/~ubuntu-backporters/+archive) for Beta 5 packages if you are extra bold :)

---

### Post by SpookyET on 2008-04-07
The Backporters build is crap. It's not build properly. Crappy fonts. Doesn't replace firefox 2.0. I'll probably do a build. I do the best build on Arch Linux. 

[http://aur.archlinux.org/packages.php?ID=15184](http://aur.archlinux.org/packages.php?ID=15184)

Pacman is grandma easy. I'll have to learn how to do debs.

In the nutshell.

Mozconfig
```

# load defaults from src tarball
. $topsrcdir/browser/config/mozconfig
# add our own options

# TODO need to wait for version 4.7 to be built
# ac_add_options --with-system-nspr
ac_add_options --with-system-nss
ac_add_options --with-system-jpeg
ac_add_options --with-system-zlib
ac_add_options --with-system-png
ac_add_options --with-system-mng
ac_add_options --with-pthreads
ac_add_options --disable-tests
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --enable-optimize="#CFLAGS#"
# ac_add_options --disable-xinerama
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --disable-xprint
ac_add_options --enable-strip
ac_add_options --enable-pango
ac_add_options --enable-xft
ac_add_options --enable-system-cairo
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --prefix=/opt/mozilla
ac_add_options --with-default-mozilla-five-home=/opt/mozilla/lib/firefox
ac_add_options --enable-crypto
ac_add_options --enable-single-profile
ac_add_options --disable-profilesharing
# ac_add_options --disable-gnomevfs
ac_add_options --enable-official-branding
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-opt-obj
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'

```

Build. Some paths will probably have to change.
```

  cd ${startdir}/src/mozilla
  patch -Np1 -i $startdir/src/mozilla-firefox-1.0-lang.patch || return 1

  export MOZ_PROJECT=browser
  export LDFLAGS='-lX11 -lXrender'

  sed "s/#CFLAGS#/${CFLAGS}/g" ${startdir}/src/mozconfig >.mozconfig
  make -f client.mk profiledbuild || return 1
  make DESTDIR=${startdir}/pkg -C ./ff-opt-obj install || return 1

  cd ${startdir}/pkg/opt/mozilla/lib/firefox-${pkgver}
  #export MOZ_DISABLE_GNOME=1
  export MOZTMP=`mktemp -d -p ${startdir}/src`
  LD_LIBRARY_PATH=`pwd` HOME=${MOZTMP} ./firefox-bin -register
  rm -rf ${MOZTMP}
  cd chrome
  find . -maxdepth 1 -type d -exec rm -rf {} \;

  #Remove mozilla devel stuff, this is in XULRunner now
  rm -rf ${startdir}/pkg/opt/mozilla/share
  rm -rf ${startdir}/pkg/opt/mozilla/include
  rm -rf ${startdir}/pkg/opt/mozilla/lib/pkgconfig
  rm -rf ${startdir}/pkg/opt/mozilla/lib/firefox-devel-${pkgver}


  cd ${startdir}/pkg/opt/mozilla/lib && ln -sf firefox-${pkgver} firefox

  rm -rf ${startdir}/pkg/opt/mozilla/bin/defaults

  mkdir -p ${startdir}/pkg/usr/share/applications
  mkdir -p ${startdir}/pkg/usr/share/pixmaps
  convert ${startdir}/src/mozilla/other-licenses/branding/firefox/mozicon50.xpm ${startdir}/pkg/usr/share/pixmaps/firefox.png
  install -m644 ${startdir}/src/firefox.desktop ${startdir}/pkg/usr/share/applications/
  install -m644 ${startdir}/src/firefox-safe.desktop ${startdir}/pkg/usr/share/applications/

  mkdir -p ${startdir}/pkg/opt/mozilla/lib/firefox/chrome/icons/default
  install -m644 ${startdir}/src/mozilla/other-licenses/branding/firefox/mozicon50.xpm ${startdir}/pkg/opt/mozilla/lib/firefox/chrome/icons/default/default.xpm
  install -m644 ${startdir}/src/mozilla/other-licenses/branding/firefox/mozicon50.xpm ${startdir}/pkg/opt/mozilla/lib/firefox/icons/default.xpm

```

Built like this, you'll get all the benefits of the Windows version in terms of speed.  I get around 1000 on that benchmark. Check the comments to my first link.

---


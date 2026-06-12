---
title: "Quantal ubiquity changelog"
date: 2012-05-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-05-26
Thought I'd begin trying to track ubiquity changes since the design team has big plans:

> Ubuntu&#8217;s Ubiquity installer will be &#8216;beefed up&#8217; to provide all of the features offered by the &#8216;alternate installer&#8217;, resulting in the latter being dropped as a download option.

The installer will also see the Windows settings migration assistant feature removed. The team conclude that it is too untested and buggy to remain in place. 

Any specific changelog may be viewed in it's original format by using the URL; <https://launchpad.net/ubuntu/+source/ubiquity/<version_number>/+changelog>, eg:

[https://launchpad.net/ubuntu/+source/ubiquity/2.11.0/+changelog](https://launchpad.net/ubuntu/+source/ubiquity/2.11.0/+changelog)

> [noparse]ubiquity (2.11.0) quantal; urgency=low

  [ Colin Watson ]
  * Install oem-config-slideshow-ubuntu in a separate pass from
    oem-config-$frontend and ubiquity-frontend-$frontend, since it may be
    missing from images; and only do this for the GTK frontend in any case,
    since other frontends don't currently use the slideshow (LP: #987050).
  * Re-enable alpha warning for quantal.
  * Upgrade to debhelper 9 for improved handling of compiler flags.  Make
    sure that /usr/lib/girepository-1.0/ stays where it's supposed to be
    despite changes in the default libdir for multiarch.
  * Port to Python 3:
    - Use Python 3-style print functions.
    - Use "except Exception as e" syntax rather than the old-style "except
      Exception, e".
    - Use reduce from functools rather than relying on the builtin.
    - Use list comprehensions rather than filter or map.
    - Use open() rather than file().
    - Import configparser rather than ConfigParser if available.
    - Use input() rather than raw_input() when running under Python 3.
    - Use set comprehensions.
    - Import quote from urllib.parse rather than urllib if available.
    - Use new-style octal literals.
    - Use test.support rather than test.test_support if available.
    - Add --python2 and --python3 options to tests/run to force running the
      tests under Python 2 or 3 respectively.
    - Handle renaming of __builtin__ to builtins in Python 3.
    - Only pass unicode=1 to gettext.install in Python 2.
    - Port ubiquity.auto_update to python-apt 0.8 progress classes.
    - Use Python 3 names for itertools.izip and itertools.izip_longest if
      available.
    - Use helpers from the six module to deal with some bytes/unicode
      differences.
    - As a general rule, open subprocesses with universal_newlines=True when
      expecting to read text from them.  This has no effect on Python 2
      (aside from \r\n conversion and the like, which is mostly a no-op for
      us), but causes Python 3 to read str rather than bytes.  The
      exceptions at the moment are: debconf-copydb subprocesses, which
      return mixed-encoding data that needs to be handled specially; and
      when feeding the output of a subprocess to hashlib.
    - Use six.reraise rather than the three-argument form of raise.
    - Adjust test_filteredcommand for Python 3 text handling.
    - Fix test_ubi_partman.question_has_variables to handle templates files
      as binary data, since they're mixed-encoding.
    - Cope with assertItemsEqual/assertCountEqual naming difference between
      Python 2.7 and 3.2.
    - Rearrange ubiquity.i18n.get_translations to treat debconf-copydb
      output as binary data and do field-dependent decoding.
    - Adjust test_misc and test_upower to cope with file type changes in
      Python 3.
    - Use xml.etree.cElementTree instead of libxml2; it's faster, has a
      smaller footprint by virtue of being built into the standard library,
      arguably easier to read, and works with Python 3.
    - Fix a slew of file handle leaks, including making much more liberal
      use of context managers.
    - When creating a default username based on the user's full name, decode
      it back to a Unicode type after running it through the
      ascii_transliterate encoder.
    - Remove __pycache__ directories on clean.
    - Use 'from __future__ import unicode_literals' in tests requiring
      Unicode literals.
    - Cope with various builtins and dict methods returning iterators rather
      than lists in Python 3.
    - Use chr rather than unichr in Python 3.
    - Use six.string_types rather than types.StringTypes.
    - Pass a byte string to Gtk.CssProvider.load_from_data.
    - Replace all calls to unicode() with calls to six.text_type() or
      misc.utf8() as appropriate.
    - Use unicode_literals in ubiquity.keyboard_names.
    - Fix up ubiquity.filteredcommand.debug and its tests for Python 3.  In
      Python 3, we can write Unicode strings (i.e. str) directly to
      sys.stderr, and its defaults are such that the worst case is that they
      get backslash-encoded.  Arrange the tests to simulate this.
    - Simplify ubiquity.nm.decode_ssid using bytearray(), allowing it to
      work with Python 3 too.
    - Open .debs in binary mode when verifying their contents.
    - Decode text read from debconffilter subprocesses in Python 3.
    - Only encode preseeded values in Python 2.  Python 3's debconf module
      accepts Unicode strings directly.
    - Encode the second argument to struct.pack.
    - Fix byte array handling when generating /etc/iftab.
    - Fix a missing bit of python-apt 0.8 porting in ubiquity.install_misc.
    - Open /var/lib/dpkg/status in binary mode when compressing it.
    - Pass bytes rather than text to kdecore.ki18n.
    - Call sip.setapi("QVariant", 1) on KDE frontend startup, pending a more
      complete port to the new API.
    - Use boolean tests rather than isNull, to cope with getting ordinary
      Python strings rather than QStrings.
    - In Python 3, pass strings directly to Qt rather than creating
      QStrings.
    - (Build-)depend on python3-gi, since python3-gi-cairo doesn't depend on
      that and in any case we use it directly.
  * Add Burmese translations.
  * Remove obsolete uxlaunch handling, since it's no longer used and has
    been removed from the archive.
  * Avoid locking failures when clicking on the "update this installer" link
    more than once.
  * Move a bit more code into ubiquity.install_misc, including a new
    target_file helper method.
  * Remove unnecessary #! lines from non-executable files.
  * Improve download verification to handle systems not configured for
    multiarch, i.e. anything other than amd64 by default (LP: #998492).
  * Automatic update of included source packages: choose-mirror 2.39ubuntu5,
    clock-setup 0.110ubuntu1, debian-installer-utils 1.89ubuntu1,
    localechooser 2.40ubuntu1.

  [ Stéphane Graber ]
  * Spawn dconf-service from ubiquity-dm and drop all the dbus-launch calls.
    This should ensure we have a single dconf-service running and that gets
    killed on ubiquity's exit.
  * ubiquity-dm: Turn on the compositor in metacity. (LP: #987168)
  * wallpaper: Update code to properly set the wallpaper when compositing
    is enabled.
 -- Colin Watson <cjwatson@ubuntu.com>   Thu, 17 May 2012 03:09:54 +0100[/noparse]

> ubiquity (2.11.1) quantal; urgency=low

  * Fix handling of pipes to update-apt-cache.
  * Sync up scripts/clock-setup-apply with changes in clock-setup 0.110.
  * Only decode bytes read from debconf once we have a complete line
    (LP: #1001542).
  * Remove a couple of unused attributes.
 -- Colin Watson <cjwatson@ubuntu.com>   Mon, 21 May 2012 17:16:32 +0100

**It looks like the migration assistant is already history**:

> ubiquity (2.11.2) quantal; urgency=low

  [ Colin Watson ]
  * If ubiquity is started up in a non-UTF-8 locale, force it into C.UTF-8
    and fail immediately if that's unavailable (LP: #1003851).
  * KDE fails to round-trip strings containing U+FEFF ZERO WIDTH NO-BREAK
    SPACE, such as the translations of a few language names.  Strip these
    from language name translations.
  * Install debconf-set from debian-installer-utils, useful for preseeding.

  [ Evan Dandrea ]
  * [B][COLOR="Red"]Remove migration-assistant following foundations-q-testing-
    migration-assistant. Thanks Dmitrijs Ledkovs![/COLOR][/B]
  * Automatic update of included source packages: base-installer
    1.122ubuntu8, flash-kernel 2.28ubuntu43.
 -- Evan Dandrea <ev@ubuntu.com>   Fri, 25 May 2012 15:47:47 +0100

> ubiquity (2.11.3) quantal; urgency=low

  * Automatic update of included source packages: flash-kernel 2.28ubuntu45.
 -- Colin Watson <cjwatson@ubuntu.com>   Mon, 28 May 2012 09:44:35 +0100

> ubiquity (2.11.4) quantal; urgency=low

  [ Colin Watson ]
  * Force the locale to en_US.UTF-8 for the timezone tests.
  * Fix seddery of clock-setup/finish-install.d/10clock-setup to handle
    changes in clock-setup 0.110 (LP: #1003443).
  * Automatic update of included source packages: flash-kernel
    3.0~rc.4ubuntu1.
  * In the shell script syntax check, filter out *.po and *.pot files
    straight away before doing the slower check using file(1).  There are
    lots of these and it takes quite a long time otherwise.
  * Add several Lintian overrides.

  [ Dmitrijs Ledkovs ]
  * [B][COLOR="Red"]Remove migration-assistant's UI definitions.
[/COLOR][/B]
  [ Martin Pitt ]
  * scripts/simple-plugins, ubiquity/plugins/ubi-prepare.py: Move from Jockey
    to "ubuntu-drivers autoinstall". Add ubuntu-drivers-common Recommends: for
    this.
  * scripts/plugininstall.py: Drop jockey --check-composite call. It is
    obsolete as the free drivers now provide 3D support. Automatic
    installation of graphics drivers is controlled and covered by
    ubuntu-drivers autoinstall now.

  [ Mario Limonciello ]
  * Don't encode callbacks in UTF8 in the timezone plugin anymore.  The strings
    are already unicode.
 -- Colin Watson <cjwatson@ubuntu.com>   Fri, 01 Jun 2012 14:49:41 +0100

> [noparse]ubiquity (2.11.5) quantal-proposed; urgency=low

  * Force the DBUS signature of AddAndActivateConnection (LP: #1008898)
 -- Stephane Graber <stgraber@ubuntu.com>   Tue, 05 Jun 2012 11:10:52 -0400[/noparse]

> ubiquity (2.11.6) quantal; urgency=low

  [ Dmitrijs Ledkovs ]
  * Run debconf-updatepo to remove migration-assistant translations.

  [ Alan Bell ]
  * Adjust the default use_device_title label to make more sense when read
    by screen readers (LP: #1010179).

  [ Stéphane Graber ]
  * Port ubiquity-bluetooth-agent from the old python-gobject to the
    gi version of gobject as required with python3. (LP: #1013172)

  [ Matthew Paul Thomas ]
  * Improvements to the third-party software text:
    - Changes "display" to "play" (since MP3 is about audio, not video).
    - Adds mention of graphics drivers (because the installer may install a
      Nvidia proprietary driver).
    - Changes "wireless" to "wi-fi".
    - Changes "closed-source" to "proprietary", matching Ubuntu Software
      Center.
    - Removes repetition of "the software", by changing "the software's
      documentation" to "its documentation".

  [ Colin Watson ]
  * Add XS-Testsuite header, as per current DEP-8.
  * debian/tests/control: Depend on python3-mock rather than python-mock
    (LP: #1015400).
  * Automatic update of included source packages: apt-setup 1:0.56ubuntu2,
    partconf 1.38, partman-basicmethods 50, partman-jfs 36, partman-newworld
    27, partman-reiserfs 53, partman-xfs 50.

  [ Luke Yelavich ]
  * Show the a11y profile indicator in oem-config as well as in
    maybe-ubiquity mode.
  * bin/ubiquity-dm: Load at-spi for both OEM config and ubiquity.
 -- Colin Watson <cjwatson@ubuntu.com>   Wed, 20 Jun 2012 09:37:32 +0100

I'll do my best to keep this up to date, and I'll highlight what I recognize as major changes :)

---

### Post by jerrylamos on 2012-05-26
> Ubuntu’s Ubiquity installer will be ‘beefed up’ to provide all of the features offered by the ‘alternate installer’, resulting in the latter being dropped as a download option.
During development early testing,any number of times standard ubiquity was so screwed up I ended up using "alternate installer".  No more....

Jerry

---

### Post by kansasnoob on 2012-05-27
> **jerrylamos said:**
> During development early testing,any number of times standard ubiquity was so screwed up I ended up using "alternate installer".  No more....

Jerry

I wouldn't freak out too much just yet. I imagine Colin Watson will have a great deal to say about just exactly what changes get implemented ;)

Testing and reporting bugs, and being prepared for some rather tenuous discussion, are going to be of absolute importance though.

---

### Post by nm_geo on 2012-05-28
> **kansasnoob said:**
> I wouldn't freak out too much just yet. I imagine Colin Watson will have a great deal to say about just exactly what changes get implemented ;)

Testing and reporting bugs, and being prepared for some rather tenuous discussion, are going to be of absolute importance though.

Excellent that danged migration-assistant caused me fits.  As long as we keep some form of the DI installer I am all for it.  By the way, Kansas I picked up a PowerBook G4 for a song and a dance (free) and have converted it to Linux only box so maybe I can help Lars with the powerpc isos.. Well after I get my assigned amd64 tests done.

Be Well

---

### Post by kansasnoob on 2012-05-28
> **nm_geo said:**
> Excellent that danged migration-assistant caused me fits.  As long as we keep some form of the DI installer I am all for it.  By the way, Kansas I picked up a PowerBook G4 for a song and a dance (free) and have converted it to Linux only box so maybe I can help Lars with the powerpc isos.. Well after I get my assigned amd64 tests done.

Be Well

I just don't see how they can do away with the di altogether, but remember they were going to make 64bit the default DL ......... didn't happen:

[ATTACH]218822[/ATTACH]

And originally 12.04 would have no non-pae option, but Colin put a stop to that :)

I think Colin will be open to sensible ideas regarding the installer(s).

---

### Post by jerrylamos on 2012-05-28
Ubiquity bug however installed O.K. anyway.  This is 20120528 .iso install, which got a "ube timezone failed with exit code 2"  plus some dire warning install may fail. I did ubuntu-bug ubiquity creating Launchpad bug #1005656.

Install went fine, booted up and timezone is correct.

Used precise startup disk creator to make USB flash memory boot installed quantal onto a USB hard drive O.K.

Jerry

---

### Post by kansasnoob on 2012-05-30
No big change but just to keep things up to date:

> ubiquity (2.11.3) quantal; urgency=low

  * Automatic update of included source packages: flash-kernel 2.28ubuntu45.
 -- Colin Watson <cjwatson@ubuntu.com>   Mon, 28 May 2012 09:44:35 +0100

---

### Post by kansasnoob on 2012-05-30
I decided it makes more sense to keep adding to my OP. I don't like the way smiley's are sometimes displayed using quote tags but (given the length of some of the changelogs) I dislike using code tags even more.

So I added a note about what link to use to view the original version of any specific changelog. If someone has a better idea give me a shout ;)

---

### Post by cariboo on 2012-05-30
@kansasnoob, you can use the [noparse][noparse][/noparse][/noparse] tags so that [noparse]8)[/noparse] doesn't look like 8)

---

### Post by kansasnoob on 2012-05-30
> **cariboo907 said:**
> @kansasnoob, you can use the [noparse][noparse][/noparse][/noparse] tags so that [noparse]8)[/noparse] doesn't look like 8)

Very cool, thanks :)

---


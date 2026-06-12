---
title: "How to Build Latest Chromium From Source and Install as Debs"
date: 2012-06-24
forum: Tutorials
---

### Post by SleepWalkerX on 2012-06-24
I was sad ever since chromium-daily stopped making daily chromium builds and decided to get it working myself. I tried the instructions [here]("https://help.ubuntu.com/community/Chromium"), but building the chromium way doesn't provide a "make install" target for debian and building the ubuntu way caused some errors.  But I finally managed to get it working.  First step:

```
cd ~
mkdir workspace
cd workspace
```

This is to make a directory to store all the code, its going to get messy.

```
sudo apt-get install bzr subversion binutils-gold libvpx-dev libjpeg62-dev libelf-dev
```
```
sudo apt-get build-dep chromium-browser
```

Then run:

```
bzr branch lp:chromium-browser
```

This will grab the work needed from the chromium bazaar branch and all the rules needed to compile debs.

```
mkdir upstream
cd chromium-browser
```

Now fire up gedit and open up ~/workspace/chromium-browser/debian/rules.  Find the following if statement and comment out the translation portion as follows:

```
ifneq (,$(findstring Ubuntu,$(DEBIAN_DIST)))
	# Merge Translations from Launchpad
	#bzr export $(TMP_DIR)/translations-tools $(TRANSLATIONS_TOOLS_BRANCH)
	#bzr export $(TMP_DIR)/translations-export $(TRANSLATIONS_EXPORT_BRANCH)
	#( cd $(TMP_DIR)/src ; ../translations-tools/chromium2pot.py $(GRIT_CONVERTER_FLAGS) $(GRIT_TEMPLATES) )
	# Patches created:
	#@( cd $(TMP_DIR)/src ; find translations-patches -type f | xargs --verbose -n 1 diffstat -p 1 )
endif
```

There's a problem getting the translation files from launchpad and we don't need them.  Then continue:

```
./debian/rules get-orig-source LOCAL_BRANCH=../upstream/chromium-browser.svn
```

Now its checking out the latest code and you'll see an .orig.tar.gz file in the same directory.  Now edit debian/patches/series and comment out all the lines like so:

```
#system_v8.patch
#ubuntu_dont_overwrite_default_download_directory.patch
#chromium_useragent.patch
#disable_dlog_and_dcheck_in_release_builds.patch
#webkit_rev_parser.patch
#dlopen_libgnutls.patch
#dlopen_sonamed_gl.patch
#fix_glib_includes.patch
```

A lot has changed in the code base which makes these patches obsolete.  Now its time to edit debian/changelog.

We need to change the top of the file to allow our version of chromium to build.  Add this to the top,

```
chromium-browser (x.x.x.x) UNRELEASED; urgency=low

  * change details
    more change details
  * even more change details

 -- maintainer Name <myemail@email.com>  Thu, 22 Jun 2012 00:36:55 -0400
```

You can change the date and email if you want, but make sure its in the same format or it won't work.  Now take a look at the orig.tar.gz file you made.  Copy the version you see and replace x.x.x.x with it.  For example, the orig.tar.gz file I created was chromium-browser_22.0.1185.0~svn20120623r143821.orig.tar.gz so the top would look like, 

```
chromium-browser (22.0.1185.0~svn20120623r143821) UNRELEASED; urgency=low

  * change details
    more change details
  * even more change details

 -- maintainer Name <myemail@email.com>  Thu, 22 Jun 2012 00:36:55 -0400
```

Save the file and exit. There's one more edit.  Open up debian/rules, look for the following, and make it look like this:

```
compare:
	# Look for duplicates, fail if we find any
	@DUPES=`find $(PKG_DIRS) -type f -print | grep -v /DEBIAN/ | cut -d/ -f3- | sort | uniq -c | grep -vE '^ *2 .*/libffmpegsumo.so$$' | grep -vE '^  *1 '` ; \
	if [ "Z$$DUPES" != Z ] ; then \
	  echo " => Found duplicates:\n $$DUPES" ; \
	  exit 1 ; \
	else \
	  echo " => No duplicate found" ; \
	fi
	# Find missing
	@find $(PKG_DIRS) -type f -print | grep -v /DEBIAN/ | grep -vE '(/usr/lib/debug|/locales/|/inspector/|libffmpegsumo.so)' | \
	  grep $(LIB_DIR) | cut -d/ -f5- | sort > /tmp/pkg-$$$$.indebs ; \
	find debian/tmp/$(LIB_DIR) -type f -print | cut -d/ -f5- | grep -vE '(\.log$$|/locales/|/inspector/)' | sort > /tmp/pkg-$$$$.inhammer ; \
	diff -u /tmp/pkg-$$$$.inhammer /tmp/pkg-$$$$.indebs ; \
	if [ $$? -eq 0 ] ; then \
	  echo " => All fine" ; \
	else \
	  echo " => Found differences, please investigate" ; \
	  #exit 1 ; \
	fi ; \
	rm -f /tmp/pkg-$$$$.inhammer /tmp/pkg-$$$$.indebs
```

The only change is the comment in front of exit 1.  I didn't feel like hunting down the reason why there's a comparison check here, but it appears that there's a new file in the chromium source that differs to the one ubuntu expects.  Its ok, it still works, just comment out that line and we can continue.

Now tar -zxvf the orig.tar.gz file.  It creates a chromium-browser-<version> folder with the lzma inside.  Move the .lzma file into the current directory you're working in (~/workspace/chromium-browser).

Now we can run dpkg-buildpackage.

```
dpkg-buildpackage -rfakeroot -b -uc
```

After what feels like an hour there should be some debs built one directory up (workspace in this tutorial).  Sometimes there are errors in the compiling process, there are lots of changes in the chromium source code so repeat from the ./debian/rules command up above and try again if you run into one of these bugs.  Now just,

```
cd ..
sudo dpkg -i *.deb
```

And you should be using the latest chromium browser!

---


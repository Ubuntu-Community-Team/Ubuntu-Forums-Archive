---
title: "Ubuntu APT Helper: Technology Preview"
date: 2005-02-27
forum: The Cafe
---

### Post by jdong on 2005-02-27
Excuse me for using a Microsoft-like term, but it accurately describes my purpose:

1) To give the community an idea of what's brewing.
2) To determine if there's enough "interest" from the community to make it worthwhile to continue development.


Ubuntu APT Helper is a menu-driven APT sources.list generator. It's designed to make it easy and fast for beginners (and distro junkies) to get a decent sources.list.


Currently, I've got the basic "engine" coded and tested to the point where it runs without bombing out. It's designed at heart to be easily extensible with your own entries as desired.


Currently, the Helper doesn't change anything on your hard drive (DEBUG=True), but rather prints what it WOULD do.

Please test, break, and give feedback. Requires Python. Any version should do. Python is in Hoary, and I'm pretty sure it's on Warty by default.

[http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/tags/apt-helper/0.0pre1/uh_apt_helper.py](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/tags/apt-helper/0.0pre1/uh_apt_helper.py)


P.S., Licensed under the GPL. But since we're a Linux community, don't we assume so anyway? ;)

---

### Post by Quest-Master on 2005-02-27
:o I'm wondering if this does the same thing Speedstart does. (thread on Speedstart: [http://www.ubuntuforums.org/showthread.php?t=17274](http://www.ubuntuforums.org/showthread.php?t=17274))

Oh, it seems your's intent is to customize the sources.list. Speedstart's is a bit different I suppose, though it does do some changing of the sources.list as your's does. :) Good luck.

---

### Post by KLineD on 2005-02-27
I think is great. Just a little note on usability, making the user able to select multiple sources in one line, e.g. typing 1,2,3,4 and all of them would be selected. Oh and also maybe it's just me but at first look it seemed as I could only select one number and not keep selecting until I type 'n' but as I said, maybe its just me.

Just my two cents.

---

### Post by TravisNewman on 2005-02-28
OK we now have this, the WAIH, and SpeedStart... is there any chance of consolidation here, so that ALL of this can be done by the same program? Or at least have one pull from all the others? I understand the point of having JUST a sources.list editor, since it doesn't retrieve any legally sketchy packages, so it would be nice if all these projects could pull from the APT helper, once it gets to be more mature? It would just simplify matters if there weren't multiple apps doing the same things.

So are you not going to add universe/multiverse support in that at all?

---

### Post by jdong on 2005-02-28
Glad you brought up the point of consolidation. APT-Helper is designed to be just one module in my Ubuntu-Helper collection of tools.

The WAIH was what I hoped to replace. Python is a much more robust way to implement such a program, as opposed to Bash scripts with Zenity.

Speedstart is designed to be more of a "kickstart" replacement -- installing and customizing the system automatically according to a script. I did not have such intentions in mind.

BTW, you can turn off "dry run" mode by editing the script: Set DEBUG=False near the top, and it'll actually try to write the new sources.list to /etc/apt. I do not recommend doing this, except inside an expendable chroot environment.


I'll start adding the sources you guys suggested soon, but this week is busy for me...

---

### Post by Quest-Master on 2005-02-28
I think WAIH, APT-Helper, and Speedstart all have goals different in various ways, but extremely similar as well.

Good luck on both WAIH and this.. if you want, contact me and we could talk about cooperating with our projects or something of that sort. :)

---

### Post by poofyhairguy on 2005-02-28
[QUOTE=jdong]Excuse me for using a Microsoft-like term, but it accurately describes my purpose:

1) To give the community an idea of what's brewing.
2) To determine if there's enough "interest" from the community to make it worthwhile to continue development.


Ubuntu APT Helper is a menu-driven APT sources.list generator. It's designed to make it easy and fast for beginners (and distro junkies) to get a decent sources.list.


Currently, I've got the basic "engine" coded and tested to the point where it runs without bombing out. It's designed at heart to be easily extensible with your own entries as desired.


Currently, the Helper doesn't change anything on your hard drive (DEBUG=True), but rather prints what it WOULD do.

Please test, break, and give feedback. Requires Python. Any version should do. Python is in Hoary, and I'm pretty sure it's on Warty by default.

[http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/tags/apt-helper/0.0pre1/uh_apt_helper.py](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/tags/apt-helper/0.0pre1/uh_apt_helper.py)[/QUOTE]


Cool. I'll try it.

---

### Post by TravisNewman on 2005-02-28
So do you plan on a graphical interface for this jdong?
One of the things I love about Linux is that it's much easier to make frontends for command line tools than in Windows programming (from my limited experience at least).
I personally prefer powerful command line tools for things like this, but others would prefer a GUI

---

### Post by Daniel G. Taylor on 2005-03-01
Looks pretty good.

I'd suggest moving the data out into configuration files (even if they are just imported python files) and splitting the actual functionality from the interface (i.e. use one file as a library of functionality, and the other as the terminal input/output interface that uses the library to actually do the work). Also, why not just use the date+time for the backup filenames?

After that is done it would be pretty trivial to make a GNOME druid frontend for it (a druid is like a "wizard" type of thing that goes step by step). In fact, this would be a really kick ass thing to run on new installations.

[Edit] I know I'm probably on crack but we can import httplib and automatically check for updated source lists (I've got space and bandwidth for a few text files).

If you are interested I'd like to help out ;-)

---

### Post by Jad on 2005-03-01
its great Idea, 
How can I help?

---

### Post by jdong on 2005-03-01
GUI: Hmm, wasn't part of my original plan, but I guess I can work that in if necessary. Personally, I find that a Text UI for APT Helper is most appropriate, as you can use it both from command line and X.

Separation of data:

I'll try that later today. :)

---

### Post by jdong on 2005-03-01
Guys who wanna help:

Hack the script to support externally loadable sources.list files. The coolest would be the ability to parse a loadable sources.list, like the following style:

```

#BEGIN APT HELPER SOURCES

#Official Warty, main
deb http://us.archive.ubuntu.com/ubuntu main

#Official Warty, universe
deb http://us.archive.ubuntu.com/ubuntu universe

#Beta Repository, disabled by default
#deb http://beta.breaks.pc/breakage destroyer

#END APT HELPER SOURCES

```.

That way, people can both use the sources directly, or let APT Helper customize it to their liking.

---

### Post by DJ_Max on 2005-03-01
> Hack the script to support externally loadable sources.list files.
Do you mean via HTTP and/or FTP? or locally. Either way it won't be hard, as for a phraser, it would be easier for the sources.file to be made of XML or SGML. Python has a XML & SGML phraser built-in.
It will of course output a normal sources.list file.
Just a suggestion, I have yet to use your script. :)

---

### Post by jdong on 2005-03-01
HTTP is nice. I'm working on it.


I'd rather have the data file be in sources.list syntax natively -- that way, people don't have to use APT Helper to get a kick ass configuration.

---

### Post by Daniel G. Taylor on 2005-03-01
I'm working on the file loading. I'll have something posted in a bit :-)

---

### Post by Daniel G. Taylor on 2005-03-01
Okay, I hope I didn't overstep my bounds here, but I've setup a Python module and written a config loader (with a simple filesystem-based loader for now, we can add ftp/http just as easily later). I've included a log module I wrote for my next release of svg-utils that works quite well.

Files: *removed* See farther down the thread for new version.

You can extract that archive and then run ubuntuhelper/config.py and it will show you how it works on the included test.list (You **must** be in the same directory as test.list for the test driver to work properly). Notice that the logger is currently set to DEBUG by default, this means it is very verbose. We can set it to WARNING or CRITICAL later.

I've not yet integrated this module into the actual script, but you will be able to use it by doing an "import ubuntuhelper".

You might notice I use some funny comments; they are in epydoc style, which will automagically generate full developer documentation of the module when we want, which I like to use in my projects now.

About the FTP/HTTP integration, I'd recommend a tarball of .list files to be stored on-server, which can be grabbed, extracted, and parsed using my filesystem-based functions. That will make everything very easy for us.

Anyway, I was **supposed** to be spending the last hour and a half writing UML and header files for an OOP class that are due tomorrow, so I need to work on that now.

---

### Post by TravisNewman on 2005-03-01
DGT: I can't speak for jdong, but I don't think you overstepped any boundaries. In fact, holy crap!

Now, I know my spare PC wasn't enough for hosting of the backports project, but I KNOW it can do this ;)

Personally, I think it'd be nice to have loadable modules later on, so whenever there's something named module_something.py in the modules directory, it loads that on as a module to download/use an alternate sources.list. So people can go to a website and search/browse for different sources modules. Say for example I have a list of audio sources like DeMuDi, etc that I make a module for, you have a list of mono repositories, someone else has a list of ham radio repositories, etc etc.

---

### Post by Daniel G. Taylor on 2005-03-01
Hmmm, technically speaking we could add another optional comment field to the list files that would make this pretty trivial without having to import other Python files. It could look something like:

# Websource: [http://foo.com/foo.list](http://foo.com/foo.list)

Which we could parse and add to the list of dictionaries. Then, when checking for updates we would just need to grab all the lists from the websource values.

This makes it easier on source list distributers as well, because they don't need to make Python modules, just add a line to their list that points us to their servers.

Of course not everyone will implement this in their source lists, and for those people the users will need to manually update.

How does that sound?

[Edit] I should clarify that our source lists (as in the ones we distribute with ubuntuhelper) should still be in a gzipped archive (on our server) because it will let us add / remove list files as we please. These external list files will generally be a one-file thing (per site) so it will only be necessary to grab the actual file (if it has been updated). Another advantage for us with this scheme is that we can eventually incorporate the external lists into our "database" if they get popular enough.

Also, I need to figure a good way to allow multi-line descriptions so we can wrap at 80 lines.

---

### Post by TravisNewman on 2005-03-01
The reason I suggested modules is so the end user wouldn't have to edit anything manually. Otherwise, I agree. Maybe a URI that the script can hit that pops back a list of possible sources.

---

### Post by Daniel G. Taylor on 2005-03-01
Well, with my scenario the end user doesn't need to edit anything, unless I'm misunderstanding what you mean. Take an example:

User goes to foo.com website, finds nice package repository
User downloads and "installs" foo.list
User runs Ubuntu helper script which now has the new source list available for selection.

Essentially our update pseudo-code would look like this:
Grab latest lists.tar.bz2 from our server we setup and extract
Parse local .list files into the list of dictionaries
For each list file we loaded:
    If there is a Websource address go there and try to update the file
Everything is now up to date

The user doesn't have to manually edit anything, and the file will need to be "installed" (i.e. copied to the proper directory) whether it is a list file or Python module. I hope this makes sense. Any problems with this scheme that you can see?

---

### Post by poofyhairguy on 2005-03-01
[QUOTE=Daniel G. Taylor]Well, with my scenario the end user doesn't need to edit anything, unless I'm misunderstanding what you mean. Take an example:

User goes to foo.com website, finds nice package repository
User downloads and "installs" foo.list
User runs Ubuntu helper script which now has the new source list available for selection.
[/QUOTE]

[QUOTE=panickedthumb]DGT: I can't speak for jdong, but I don't think you overstepped any boundaries. In fact, holy crap![/QUOTE]

I second that. This is some interesting stuff.

---

### Post by Daniel G. Taylor on 2005-03-02
Okay, so I couldn't resist. I've implemented multi-line descriptions* and loading the websource line from the source list files. I'm too tired to implement updating the actual source list files from those websources, so it will have to wait.

As an aside I bumped the default log level up to INFO so it is less verbose now, and added another file to show how the functions work with multiple list files.

Files: [http://programmer-art.org/files/uh/uh_module_0.2.tar.bz2](http://programmer-art.org/files/uh/uh_module_0.2.tar.bz2)

* The description comment now needs to have a blank line following it or other lines will get eaten into the description field. Any suggestions on a better way or should I leave it?

---

### Post by TravisNewman on 2005-03-02
Dang.

...

Yeah that's all. Dang. And holy crap again. Wow, maybe? yeah I'll throw in a wow too.
You're going nuts on this thing all of a sudden ;)

---

### Post by Daniel G. Taylor on 2005-03-02
Okay, another update.

Files: [http://programmer-art.org/files/uh/uh_module_0.3.tar.bz2](http://programmer-art.org/files/uh/uh_module_0.3.tar.bz2)

What works:
- Load sources.list-style files
- Update any of those files that contain a websource link (currently only via http)
- Output a new sources.list-style file (that apt can use)

Things you can test run to see it in action:
ubuntuhelper/config.py (runs the same test as before and displays some data)
./uh_test.py (tries to update all the .list files and outputs sources.new in the current path)

Example of generated documentation output:
[HTML Documentation](http://programmer-art.org/files/uh/doc)
[PDF Documentation](http://programmer-art.org/files/uh/uhdoc.pdf)

As always let me know what you think ;-)

---

### Post by jdong on 2005-03-02
WOW, that is nice. This will be integrated when I get home Sunday.

---

### Post by Daniel G. Taylor on 2005-03-03
What can I say, I just can't help myself. I love hacking Python :-D 

I call this release the "Voodoo Regexp Release"
Files: [http://programmer-art.org/files/uh/uh_module_0.4.tar.bz2](http://programmer-art.org/files/uh/uh_module_0.4.tar.bz2)

As you've probably guessed by the name, the file parser now uses regular expressions (which make life oh so much easier once they are working right). This release also includes a few small bug fixes that I noticed after some more rigorous testing. This release has even successfully loaded my real /etc/apt/sources.list file (although it obviously has no name/description/websource)!

My favorite regular expression in this release:
^(?P<disabled>#*)\s*(?P<type>deb|deb-src)\s*(?P<link>(http|ftp)(.*))\s*(?P<dist>.*)\s*(?P<sect>.*)\s*
For the curious, that will find the actual source lines in sources.list-style files. The ?p<...> parts let me access the groups quickly in Python. :-) 

Any regexp wizards that want to check over what I did please do. I just did a quick online crash course and hacked together something that works (hence the "voodoo"). Sometimes I wonder whether man was meant to ever try to comprehend regular expressions.

Same commands as last time work if you want to test, and I've included a new "craptastic.list" file to show off how powerful the new parser is. The documentation from last release should still be current, so I won't update that.

Now, need sleep.

---

### Post by Daniel G. Taylor on 2005-03-04
Just one more release before I leave for the week. I added in some convenience functions and added a few example scripts to help you see what the different functions do. I also updated the HTML docs (on OSX and don't have Latex to update the PDF docs, so that will have to wait)

Files: [http://programmer-art.org/files/uh/uh_module_0.5.tar.bz2](http://programmer-art.org/files/uh/uh_module_0.5.tar.bz2)
Docs: [http://programmer-art.org/files/uh/doc/](http://programmer-art.org/files/uh/doc/)

I hope this is enough for you to get the terminal version working with the library. We should talk about any other functionality we might need. My next big thing will be to get updating the source lists working from a single bzipped archive (so that we can host a bzipped archive of the most popular source lists and have that automatically updated; Notice this is different than updating via the Websource: links in 3rd party source lists).

Anyway, for the curious, try out the different uh_* scripts in this release that test various functions of the library.

---


---
title: "pd-extended on AMD64"
date: 2009-10-29
forum: Ubuntu Studio
---

### Post by skullmunky on 2009-10-29
Just thought I'd share this :)

Pure Data Extended doesn't have an official installer for AMD64, but pretty much everything will compile.  At the moment Pd, GEM, and Zexy are all in the repositories, but there are a few other core externals that haven't made it in yet - OSCx, for example.  

I'm sure a full amd64 release of pd-extended will be on its way shortly, but in the meantime these instructions are helpful:

[http://puredata.info/docs/developer/BuildingPdExtended64bitUbuntuIntrepid](http://puredata.info/docs/developer/BuildingPdExtended64bitUbuntuIntrepid)

I have a build which I'm happy to share if you don't want to go through 
all the hassle :)

---

### Post by barisurum on 2009-10-29
skullmunky! please provide a link to enlighten ubuntu studio community about your miraculous all-in-one 64bit friendly pd-extended and be the man of the year!

---

### Post by kiilo on 2009-11-06
yes provide the deb please 

im now at stage:
pddplink. wont compile ... how many externals? is there an end?

again if
you have your build
provide it

thks
kiilo

---

### Post by bilderbuchi on 2009-11-07
+1! :)

---

### Post by kiilo on 2009-11-07
Here it is!

download at: [URL="http://kiilo.org/pub/ubuntu"]http://kiilo.org/pub/ubuntu

[/URL]  [http://kiilo.org/pub/ubuntu/Pd-0.42.5-extended-20091107.deb](http://kiilo.org/pub/ubuntu/Pd-0.42.5-extended-20091107.deb)

build out of the trunk Gem PiDip OSCx and the others 
[]("http://kiilo.org/pub/ubuntu/pd-extended_usr_lib_pd_TCL.tar")[INDENT]
greets 
kiilo








[/INDENT]

---

### Post by bilderbuchi on 2009-11-08
thanks!
unfortunately, "Error: Dependency is not satisfiable: libmagick++1" on karmic64. i got libmagick++2 installed from the repos, though. :-(

---

### Post by kiilo on 2009-11-08
sorry i have jaunty here,

i will not upgrade or reinstall to 9.10 yet
because i need every weekend up to december for preparing a workshop

i get pd-extended from trunk 
also pd src and Gem src 
both has to be moved inside of trunk folder 

cp -Rv pd trunk/
cp -Rv Gem trunk/

check you have all libXY-dev (basicly the dependencies of pd, -dev versions!)
when you compile
 
cd trunk/packages/linux_make
make install

you will get a errors ca 10 -30 times ;-) 
check the directory of that external by ./configure - if possible - to see what -dev is missing
(not externals all have a configure)

i add '-fPIC' to line 44 in file externals/miXed/Makefile.common: 
DEFINES = -fPIC -DUNIX
 
when you run into -fPIC errors - you have to delete the *.o header files and make a install run again
the file 
because compiler doesnt recompile if there are header (.o) files allready. 
usually 'make clean' should do this but its running in circle forever 
i did a brutal hacking (in folder trunk):
 find . -name "*.o" -exec rm -rf {} \;
to remove all of them

and after 4 days aof try and error finally its running.

---

### Post by bilderbuchi on 2009-11-08
thanks for the tips. i appreciate the walkthrough!
it already complains on the first line about not finding a linux_make/build directory and that dpkg-shlibdeps  needs at least one executable. i don't have the first clue what to do about that.

i think i'll defer installing until someone builds a 64bit version for karmic, then; i, as you, don't have the time to tinker endlessly :-(

---

### Post by skullmunky on 2009-11-13
Here's the link to my build, but kiilo's may be better ... 

[http://transatlab.net/?p=143](http://transatlab.net/?p=143)

I couldn't get iem_tab to build but everything else seems ok so far.

---

### Post by barisurum on 2009-11-24
> unfortunately, "Error: Dependency is not satisfiable: libmagick++1" on karmic64. i got libmagick++2 installed from the repos, though.

I hacked the deb package with a script I found in ubuntu forums and the installation went smoothly. Here is the script:

> #!/bin/bash

EDITOR=gedit

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
$EDITOR "$CONTROL"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"

Save it as a text to a filename of your choice (dependhack maybe) on the same directory as the deb package and make it an executable with

chmod +x dependhack

run it with:

./dependhack SOME_DEB_FILE_HERE.deb

It will call gedit to your ranks and now you can edit the debian control file inside the deb. Change the entry [COLOR="Red"]libmagick++1[/COLOR] to [COLOR="Lime"]libmagick++2[/COLOR] on the [COLOR="Purple"]depends[/COLOR] line, save it, and fire the modified deb package all the way down the hill.

---

### Post by bilderbuchi on 2009-11-25
great, thanks! will try that asap!
edited: great, it worked! thanks!

---

### Post by marcimat on 2009-12-23
Hi all,

I try recently your solution with the Jaunty .deb on Karmic. I thought it was good, but unfortunaly, Gem doesn't want to work.

So, I take my courage and compile myself pd-extended. It was hard (a lot of -dev package was necessary) and some files needed to be edited for add -fPIC. I use theses help to do that (but first link informations are a little out of date in part «2 Prepare» and in package to install) : 
[LIST]
[*][http://puredata.info/docs/developer/BuildingPdExtended64bitUbuntuIntrepid](http://puredata.info/docs/developer/BuildingPdExtended64bitUbuntuIntrepid)
[*][http://puredata.info/docs/developer/BuildingPdExtended](http://puredata.info/docs/developer/BuildingPdExtended)
[*][http://puredata.info/docs/developer/GettingPdSource](http://puredata.info/docs/developer/GettingPdSource)
[/LIST]

I do for me a little .sh witch is like that :

# update sources !
svn co [https://pure-data.svn.sourceforge.net/svnroot/pure-data/trunk](https://pure-data.svn.sourceforge.net/svnroot/pure-data/trunk) pd-extended
cd pd-extended
rm -rf pd
svn co [https://pure-data.svn.sourceforge.net/svnroot/pure-data/branches/pd-extended/0.42/pd](https://pure-data.svn.sourceforge.net/svnroot/pure-data/branches/pd-extended/0.42/pd)
cd ..

# add Gem
rsync -av --delete rsync://128.238.56.50/distros/pd-extended/Gem Gem/

# creer un package
cd packages/linux_make
sh generate_install_makefile.bash
make install && make package

---------
After that (and lot of -dev package add via synaptic when "make" was gasping) I have a nice .deb package for karmic 64bit with the svn stable branche of pd-extended.

And I put it here if someone is interesting : 
[http://marcimat.magraine.net/ftp/deb/Pd-0.42.5-extended-20091223.deb](http://marcimat.magraine.net/ftp/deb/Pd-0.42.5-extended-20091223.deb)

(This built is make on a MacBookPro 5.5 / Core 2 Duo with Ubuntu Karmic 64bits)

Hope I help someone.

(and sorry for bad english)

Marcimat.

---

### Post by barisurum on 2009-12-23
Well gem didn't work for me too so you're right there and thanks for this deb package, I will give it a try.

> (and sorry for bad english)

Definitely not a problem ;)

---

### Post by emviveros on 2012-10-23
Good news...!!!:P

[https://launchpad.net/~eighthave/+archive/pd-extended](https://launchpad.net/~eighthave/+archive/pd-extended)

This ppa maintained for Hans-Christoph Steiner have the latest version of pd-extended.. 

only:

sudo add-apt-repository ppa:eighthave/pd-extended
[Enter]
sudo apt-get update
sudo apt-get install pd-extended

:guitar:

---


---
title: "Google ChromiumOS build script"
date: 2009-12-31
forum: The Cafe
---

### Post by sandyd on 2009-12-31
Ive created a google chromiumOS build script to automate the build process

can anyone test this? (might take a while to download all the code....)
run this (seperately) before running below code
```

#echo "export PATH=\$PATH:/home/"$(whoami)"/dev/depot_tools" >> ~/.bashrc
#bash --rcfile "~/.bashrc"

```

```

##Google ChromiumOS Automated Build Script
##Made By Carlee / Dolphinaura <dolphinaura@studenthotspot.net>
##Based on instructions from http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions
##Testing Version
echo "This script automates the build process of Google ChromiumOS"
MACHINE_TYPE=`uname -m`
if [ ${MACHINE_TYPE} == 'x86_64' ]; then
echo "--Installing Build Dependencies--"
sudo apt-get install -y subversion pkg-config python perl g++ g++-multilib build-essential \
  bison flex gperf libnss3-dev libgtk2.0-dev libnspr4-0d libasound2-dev \
  libnspr4-dev msttcorefonts libgconf2-dev libcairo2-dev libdbus-1-dev \
  libbz2-dev libjpeg62-dev libpam0g-dev wdiff lighttpd php5-cgi sun-java6-fonts \
  lib32asound2-dev lib32bz2-dev qemu virtualbox-3.0 &> ~/dev/google_chromium_os/output.log
else
echo "--Installing Build Dependencies--"
sudo apt-get install -y subversion pkg-config python perl g++ g++-multilib build-essential \
  bison flex gperf libnss3-dev libgtk2.0-dev libnspr4-0d libasound2-dev \
  libnspr4-dev msttcorefonts libgconf2-dev libcairo2-dev libdbus-1-dev \
  libbz2-dev libjpeg62-dev libpam0g-dev wdiff lighttpd php5-cgi sun-java6-fonts qemu virtualbox-3.0 &> ~/dev/google_chromium_os/output.log
fi
echo "--Retrieving Google Build Tools--"
mkdir ~/dev
mkdir ~/dev/google_chromium_os
cd ~/dev/google_chromium_os
svn co http://src.chromium.org/svn/trunk/tools/depot_tools &> ~/dev/google_chromium_os/output.log
#echo "export PATH=\$PATH:/home/"$(whoami)"/dev/depot_tools" >> ~/.bashrc
#bash --rcfile "~/.bashrc"
echo "--Setting Up Build Environment--"
mkdir ~/dev/google_chromium_os/chromium
cd ~/dev/google_chromium_os/chromium
wget -c http://dl.dropbox.com/u/3593659/chromium_os/chromium_browser_gclient &> ~/dev/google_chromium_os/output.log
mv chromium_browser_gclient .gclient
cd ~/dev/google_chromium_os
wget -c http://dl.dropbox.com/u/3593659/chromium_os/chromiumos_gclient &> ~/dev/google_chromium_os/output.log
mv chromiumos_gclient .gclient
echo "--Retrieving Source Code--"
echo "--This is gonna take a long time, please don't kill/close/abort script--"
cd ~/dev/google_chromium_os
gclient sync &> ~/dev/google_chromium_os/output.log
cd ~/dev/google_chromium_os/chromium
gclient sync  &> ~/dev/google_chromium_os/output.log
echo "--Creating Local Repository--"
cd ~/dev/google_chromium_os/chromiumos/src/scripts
./make_local_repo.sh  &> ~/dev/google_chromium_os/output.log
echo "--Creating Chroot--"
./make_chroot.sh  &> ~/dev/google_chromium_os/output.log
echo "--Building Chrome--"
./build_chrome.sh --chrome_dir ~/dev/google_chromium_os/chromium &> ~/dev/google_chromium_os/output.log
echo "--Entering Chroot--"
./enter_chroot.sh
echo "--Setting up User Account--"
cd ../platform/pam_google && ./enable_localaccount.sh $(whoami) &> ~/dev/google_chromium_os/output.log
echo "--When ChromeOS starts up, you can login with your ubuntu username--"
cd ../../
cd scripts
echo "--Set Sudo Password--"
./set_shared_user_password.sh
echo "--Beginning Build--"
./build_all.sh &> ~/dev/google_chromium_os/output.log
exit
echo "--Building VMware and Virtualbox Images--"
mkdir ~/google_chromeos_images
./image_to_vmware.sh --from=~/chromiumos/src/build/images/SUBDIR \
  --to=~/google_chromeos_images/SUBDIR/vmware.vmdk  &> ~/dev/google_chromium_os/output.log
./image_to_virtualbox.sh --from=~/chromiumos/src/build/images/SUBDIR \
  --to=~/google_chromeos_images/SUBDIR/virtualbox.vdi  &> ~/dev/google_chromium_os/output.log
echo "--Build Finished--"

```theirs now a log in ~/dev/google_chromium_os/build.log
I simply output the entire script just so you could see the code, save it as a *.sh file.
p.s. if you have virtualbox installed from the virtualbox repo, remove "virtualbox-ose" from the build dependencies installation.

---

### Post by LeifAndersen on 2009-12-31
Well, I'll give it a try, but first:

1.  I thought that this was a whole OS (that just contained a browser), so how am I going to get into it?

2.  Why couldn't you try it yourself?

Anyway, it looks interesting, and I didn't see any malicious code in there, so I'll give it a shot if you can answer those questions.  Thank you.

---

### Post by sandyd on 2009-12-31
> **LeifAndersen said:**
> Well, I'll give it a try, but first:

1.  I thought that this was a whole OS (that just contained a browser), so how am I going to get into it?

2.  Why couldn't you try it yourself?

Anyway, it looks interesting, and I didn't see any malicious code in there, so I'll give it a shot if you can answer those questions.  Thank you.
1. If you look at the end of the script, youll see that it creates two virtual machine images. One is for VMware and one is for Virtualbox.
And no, its not only a browser. Its a copy of the chromium browser sitting on top of ubuntu karmic (i **think** its ubuntu karmic. or at least thats what it says on the packages)

2. I only have one machine to test this with, and ive already done all of those steps - manually. except that since i installed a whole lotta stuff and modified a whole lot of stuff, and redid things a lot (trial and error anyone?), the build on my machine is not valid for testing the script anymore.

---

### Post by ticopelp on 2009-12-31
I ran it as-is in a terminal, here is the (failed) output. Hopefully the error messages will prove useful.

```

This script automates the build process of Google ChromiumOS
[: 23: i686: unexpected operator
--Installing Build Dependencies--
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
pkg-config is already the newest version.
python is already the newest version.
perl is already the newest version.
g++ is already the newest version.
g++-multilib is already the newest version.
build-essential is already the newest version.
bison is already the newest version.
flex is already the newest version.
gperf is already the newest version.
libnss3-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libnspr4-0d is already the newest version.
libasound2-dev is already the newest version.
libnspr4-dev is already the newest version.
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
libgconf2-dev is already the newest version.
libcairo2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libbz2-dev is already the newest version.
libjpeg62-dev is already the newest version.
libpam0g-dev is already the newest version.
wdiff is already the newest version.
lighttpd is already the newest version.
php5-cgi is already the newest version.
sun-java6-fonts is already the newest version.
qemu is already the newest version.
virtualbox-ose is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
--Retrieving Google Build Tools--
A    depot_tools/git-cl
A    depot_tools/README.gclient
A    depot_tools/WATCHLISTS
A    depot_tools/presubmit_canned_checks.py
A    depot_tools/git-gs
A    depot_tools/git_cl_hooks.py
A    depot_tools/presubmit_support.py
A    depot_tools/git-try
A    depot_tools/profile.xml
A    depot_tools/cpplint.py
A    depot_tools/drover
A    depot_tools/chrome-update.bat
A    depot_tools/tests
A    depot_tools/tests/README.gclient_test
A    depot_tools/tests/presubmit_unittest.py
A    depot_tools/tests/__init__.py
A    depot_tools/tests/scm_unittest.py
A    depot_tools/tests/super_mox.py
A    depot_tools/tests/trychange_unittest.py
A    depot_tools/tests/gcl_unittest.py
A    depot_tools/tests/gclient_test.py
A    depot_tools/tests/gclient_utils_test.py
A    depot_tools/tests/watchlists_unittest.py
A    depot_tools/tests/pymox
A    depot_tools/tests/pymox/stubout_testee.py
A    depot_tools/tests/pymox/__init__.py
A    depot_tools/tests/pymox/setup.py
A    depot_tools/tests/pymox/COPYING
A    depot_tools/tests/pymox/mox_test_helper.py
A    depot_tools/tests/pymox/mox_test.py
A    depot_tools/tests/pymox/mox.py
A    depot_tools/tests/pymox/MANIFEST.in
A    depot_tools/tests/pymox/stubout_test.py
A    depot_tools/tests/pymox/stubout.py
A    depot_tools/tests/pymox/README
A    depot_tools/tests/gclient_scm_test.py
A    depot_tools/tests/revert_unittest.py
A    depot_tools/chrome-update-create-task.bat
A    depot_tools/gcl
A    depot_tools/drover.bat
A    depot_tools/revert
A    depot_tools/scm.py
A    depot_tools/gcl.bat
A    depot_tools/trychange.py
A    depot_tools/README.git-cl
A    depot_tools/watchlists.py
A    depot_tools/revert.bat
A    depot_tools/bootstrap
A    depot_tools/bootstrap/gclient.bat
A    depot_tools/bootstrap/win
A    depot_tools/bootstrap/win/unzip.js
A    depot_tools/bootstrap/win/win_tools.bat
A    depot_tools/bootstrap/win/svn.new.bat
A    depot_tools/bootstrap/win/README.google
A    depot_tools/bootstrap/win/get_file.js
A    depot_tools/bootstrap/win/python.new
A    depot_tools/bootstrap/win/svnversion.new.bat
A    depot_tools/bootstrap/win/python.new.bat
A    depot_tools/bootstrap/win/svn.new
A    depot_tools/bootstrap/gclient.sh
A    depot_tools/gclient_scm.py
A    depot_tools/LICENSE
A    depot_tools/chrome-update.py
A    depot_tools/gclient
A    depot_tools/drover.py
A    depot_tools/create-chromium-git-src
A    depot_tools/gclient.bat
A    depot_tools/gclient_utils.py
A    depot_tools/gcl.py
A    depot_tools/README
A    depot_tools/revert.py
A    depot_tools/git-cl-upload-hook
A    depot_tools/breakpad.py
A    depot_tools/PRESUBMIT.py
A    depot_tools/.gitignore
A    depot_tools/README.git-cl.codereview
A    depot_tools/hammer
A    depot_tools/upload.py
A    depot_tools/gclient.py
A    depot_tools/cpplint.bat
A    depot_tools/hammer.bat
 U   depot_tools
Checked out revision 35423.
chromium.sh: 31: source: not found
--Setting Up Build Environment--
--2009-12-31 11:54:01--  http://dl.dropbox.com/u/3593659/chromium_os/chromium_browser_gclient
Resolving dl.dropbox.com... 174.129.242.127, 75.101.129.115, 75.101.136.120, ...
Connecting to dl.dropbox.com|174.129.242.127|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1144 (1.1K) [application/octet-stream]
Saving to: `chromium_browser_gclient'

100%[======================================>] 1,144       --.-K/s   in 0s      

2009-12-31 11:54:01 (89.9 MB/s) - `chromium_browser_gclient' saved [1144/1144]

--2009-12-31 11:54:01--  http://dl.dropbox.com/u/3593659/chromium_os/chromiumos_gclient
Resolving dl.dropbox.com... 174.129.212.16, 174.129.242.127, 75.101.129.115, ...
Connecting to dl.dropbox.com|174.129.212.16|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 397 [application/octet-stream]
Saving to: `chromiumos_gclient'

100%[======================================>] 397         --.-K/s   in 0s      

2009-12-31 11:54:02 (32.6 MB/s) - `chromiumos_gclient' saved [397/397]

--Retrieving Source Code--
chromium.sh: 44: gclient: not found
chromium.sh: 46: gclient: not found
--Creating Local Repository--
cd: 49: can't cd to /home/dan/dev/google_chromium_os/chromiumos/src/scripts
chromium.sh: 50: ./make_local_repo.sh: not found
--Creating Chroot--
chromium.sh: 53: ./make_chroot.sh: not found
--Building Chrome--
chromium.sh: 56: ./build_chrome.sh: not found
--Entering Chroot--
chromium.sh: 59: ./enter_chroot.sh: not found
--Setting up User Account--
cd: 62: can't cd to ../platform/pam_google
--When ChromeOS starts up, you can login with your ubuntu username--
cd: 66: can't cd to scripts
--Set Sudo Password--
chromium.sh: 68: ./set_shared_user_password.sh: not found
--Beginning Build--
chromium.sh: 71: ./build_all.sh: not found

```

---

### Post by Leach54 on 2009-12-31
Ive run chrome OS. I gotta say, Ill be dual booting that as soon as I can run it not off a build. I'm sure that I could but i think ill wait. What I've seen is awesome. (of coarse I want to work for Google and have an extreme bias for them)

---

### Post by sandyd on 2009-12-31
hmm.
seems like after adding the paths for the google dev tools, you need to close the terminal and reopen it.

ill see if i can find something to automatically refresh the path.

---

### Post by sandyd on 2009-12-31
and i just figured it out.
for some reason, bash does not reconize "source" as a command.....

script fixed

---

### Post by Leach54 on 2009-12-31
I don't know if i'm wrong but non of the stuff in ether of your messages looks like code. It looks the progress (Notice the progress bar). I have never seen any code that look like [=====================================] 100%

---

### Post by LeifAndersen on 2009-12-31
Well, I've been running it, and I must say that some of those steps really don't need to sleep for 30 seconds...

---

### Post by HappinessNow on 2009-12-31
I'll hug the person who makes a Google Chrome OS-Ubuntu hybrid iso (Chrome Buns?)

---

### Post by LeifAndersen on 2009-12-31
Hmm...I hope I didn't kill it.  I thought it was finished, and typed in ls, I don't think I did a cd though (which is good).  And all of the sudden, it started doing more stuff.

---

### Post by sandyd on 2009-12-31
it freezes during the downloading of the source code. its kinda normal. it unfreezes when the source code is finished downloading

---

### Post by sandyd on 2009-12-31
> **&#20170 said:**
> I'll hug the person who makes a Google Chrome OS-Ubuntu hybrid iso (Chrome Buns?)

it typically already is a hybrid. cause it uses packages from karnuc ;)

---

### Post by phrostbyte on 2009-12-31
You can hide the output of a command with &> /dev/null

eg: sudo apt-get install hello &> /dev/null

The command will still execute but silently. :)

Thus you could get rid of your 30 second sleeps.

---

### Post by sandyd on 2009-12-31
> **phrostbyte said:**
> You can hide the output of a command with &> /dev/null

eg: sudo apt-get install hello &> /dev/null

The command will still execute but silently. :)

Thus you could get rid of your 30 second sleeps.
ah thanks!
you know what....
that actually gave me an idea.
ill use that to generate a build log instead.
but for now, ill leave it like this. cause im not finished debugging :)

---

### Post by HappinessNow on 2009-12-31
> **carlee said:**
> it typically already is a hybrid. cause it uses packages from karnuc ;)
Okay so when ever I see you, I owe you a great big bear hug. :p
:lolflag:

---

### Post by sandyd on 2010-01-01
script updated to remove all the mumble jumble.
all the stuff that happens during build is now logged to file instead.

---

### Post by sgwebb on 2010-01-01
There seems to be an issue with the new script:

 sudo ./googleos.sh
This script automates the build process of Google ChromiumOS
./googleos.sh: 66: Syntax error: end of file unexpected (expecting "fi")

---

### Post by sandyd on 2010-01-01
> **sgwebb said:**
> There seems to be an issue with the new script:

 sudo ./googleos.sh
This script automates the build process of Google ChromiumOS
./googleos.sh: 66: Syntax error: end of file unexpected (expecting "fi")
no sudo +i accidentally deleted a fi from the script while going on my sleep removal rampage
fixed

---

### Post by bruno9779 on 2010-01-01
trying this right now on intel 64 bit (test machine, not the one in my sig).

I will post results

---

### Post by k64 on 2010-01-01
I am currently posting from Chrome OS on my Acer Aspire One AOA110-1545 and have to say it works for me - barely. Besides, it only is based on a bare Ubuntu shell. Chrome that is a part of Chrome OS does include some useful features - pinning tabs, an App Switcher, an App Panel - but that's about it. On the upside, Chrome OS could very well bring Linux to the masses. It may by itself only introduce a niche market, but a whole new wave of Linux distributions forked off it won't be as crippled. The result of this is that Linux will obtain the 92% market share that Windows has now - and we'll all be happy.

---

### Post by sandyd on 2010-01-02
bump note.

---

### Post by sunset_studies on 2010-01-09
I can't wait to try this, though in reality the coolest feature of Chome OS (malware immunity) will only work with the official Google hardware right? [http://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview#TOC-Verified-booty](http://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview#TOC-Verified-booty) ('booty' yes that is the real URL!)

Also curious to know what methods people are using to run the various outputs from this script. I assume a version installed to the hard drive is the fastest, followed by a version installed to a usb key, with the virtual machine instances running the slowest?

Thanks again for this, I was a little put off by the official build instructions page :)

Btw, AFIAK Nvidia/ATI cards are not supported, and will make ChromeOS run dead slow unless you hack in your own drivers.

Edit: I think it would be better if the script incorporated the dropbox downloads as static content rather than downloading them at run time. Dropbox is essentially an untrusted source to everyone but the dropbox owner, and I think it's good to teach users not to download from such sources content that will ultimately be executed.

---

### Post by sandyd on 2010-01-10
> **sunset_studies said:**
> I can't wait to try this, though in reality the coolest feature of Chome OS (malware immunity) will only work with the official Google hardware right? [http://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview#TOC-Verified-booty](http://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview#TOC-Verified-booty) ('booty' yes that is the real URL!)

Also curious to know what methods people are using to run the various outputs from this script. I assume a version installed to the hard drive is the fastest, followed by a version installed to a usb key, with the virtual machine instances running the slowest?

Thanks again for this, I was a little put off by the official build instructions page :)

Btw, AFIAK Nvidia/ATI cards are not supported, and will make ChromeOS run dead slow unless you hack in your own drivers.

Edit: I think it would be better if the script incorporated the dropbox downloads as static content rather than downloading them at run time. Dropbox is essentially an untrusted source to everyone but the dropbox owner, and I think it's good to teach users not to download from such sources content that will ultimately be executed.
they aren't executed.
their config files.

---

### Post by sunset_studies on 2010-01-10
> **carlee said:**
> they aren't executed.
their config files.

Sorry, poor choice of words on my part! They aren't executed themselves, but they do control execution, and could be altered to pull code from an untrusted/malicious source, so it is a vulnerability. If users aren't forcefully introduced to safe software installation methods we'll end up no safer than Windows users. Your script will hardly be any longer if you replace those dropbox wget calls with 

echo "<content of those files>" >> .glient

;)


Thanks!

---

### Post by BFG on 2010-01-25
\Script looks great.  I was following instructions in this link and got stuck:
[http://www.grenadepod.com/2009/12/03/building-and-running-google-chrome-os-on-virtualbox/comment-page-1/#comment-431](http://www.grenadepod.com/2009/12/03/building-and-running-google-chrome-os-on-virtualbox/comment-page-1/#comment-431)

I found this thread when looking for answers.  I suspect in the version I downloaded today, something has changed so that the make_local_repo.sh is deprecated, but I can't find any alternative instructions.

more make_local_repo.sh 
```

#!/bin/bash
# This script is no longer needed. This stub is here to avoid immediate
# buildbot breakage and will be removed soon.
exit 0

```

I'm not knowledgeable enough with compiling to guess. I haven;t tried your script yet, as I suspect it will stop in the same place.

---

### Post by egrep on 2010-02-08
> **carlee said:**
> and i just figured it out.
for some reason, bash does not reconize "source" as a command.....

script fixed

carlee - questions because I hit a snag. I see the error, but not sure which parts [mine/yours] are wrong on my systems:

You wrote:
mkdir ~/dev
mkdir ~/dev/google_chromium_os
cd ~/dev/google_chromium_os
then you make the top level dir:
mkdir ~/dev/google_chromium_os/chromium
grab all the source... good so far... but then:

cd ~/dev/google_chromium_os/chromium
wget -c [snip]
mv chromium_browser_gclient .gclient
cd ~/dev/google_chromium_os
wget -c [snip]
mv chromiumos_gclient .gclient
echo "--Retrieving Source Code--"
[snip]
cd ~/dev/google_chromium_os
gclient sync &> ~/dev/google_chromium_os/output.log
cd ~/dev/google_chromium_os/chromium

All good to here dir is called chromium

gclient sync  &> ~/dev/google_chromium_os/output.log
echo "--Creating Local Repository--"
cd ~/dev/google_chromium_os/chromiumos/src/scripts

When did the directory change to chromiumos from chromium?

./make_local_repo.sh  &> ~/dev/google_chromium_os/output.log
echo "--Creating Chroot--"

Fails because I do not have a chromiumos dir. Also, and this is my biggest problem, even when I grab the tarball, the magic directory called src/scripts never gets downloaded.

Anyone tried without having any directories created first? Let me do some editing and testing...

--egrep

---

### Post by sandyd on 2010-02-08
the script is currently defunt due to google making some changes to how chromium/os is compiled. will look into it this week if i have time

---


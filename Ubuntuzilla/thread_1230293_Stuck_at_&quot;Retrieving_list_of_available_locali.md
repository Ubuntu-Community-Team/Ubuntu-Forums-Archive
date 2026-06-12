---
title: "Stuck at &quot;Retrieving list of available localizations for Firefox ...&quot;"
date: 2009-08-03
forum: Ubuntuzilla
---

### Post by test666 on 2009-08-03
Version 4.7.0

After waiting for a long, long time, without having network activity, I pressed Control-C and got this:

Retrieving list of available localizations for Firefox ...
^CTraceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1254, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 281, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 308, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 699, in install
    self.getLocalizationList()
  File "/usr/local/bin/ubuntuzilla.py", line 381, in getLocalizationList
    self.locList = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 107, in getSystemOutput
    returncode = p.wait()
  File "/usr/lib/python2.6/subprocess.py", line 1123, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

What can I do? :confused:

Info: I don't have a proxy.

---

### Post by nanotube on 2009-08-03
hmm, well first question - did you try it again, and did the behavior repeat?

---

### Post by test666 on 2009-08-03
Thank you for answering my plead.

As for your question, yes, I tried several times running Ubuntuzilla. Sorry, I should have said it in the first post.

I tried in the command line:
ubuntuzilla.py
sudo ubuntuzilla.py
sudo ubuntuzilla.py -g
ubuntuzilla.py -g

Rebooted and repeated the above. Same thing happens all the time. The message after Control-C is always the same.

Prior to installing Ubuntuzilla, I installed:
sudo apt-get install libstdc++5 libnotify-bin

Semi-noob here, but eager to learn. :D

---

### Post by derek.moyes on 2009-08-03
The same thing is happening to me. Here's what I get when I hit CTRL+C:

```
^CTraceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1254, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 281, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 308, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 699, in install
    self.getLocalizationList()
  File "/usr/local/bin/ubuntuzilla.py", line 381, in getLocalizationList
    self.locList = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 107, in getSystemOutput
    returncode = p.wait()
  File "/usr/lib/python2.6/subprocess.py", line 1123, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

```
Tried multiple times.

---

### Post by graaant on 2009-08-03
I get that same error. Documented in the Failed Install.. thread just below this one.

---

### Post by nanotube on 2009-08-04
hi guys

this particular problem seems to be caused by w3m waiting indefinitely to connect to the mozilla releases server. 

what happens when you run manually the following command:
```

w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/

```

I'm going to try one thing - i'll change the mirror list, since the releases.mozilla.org main mirror has been known to give occasional trouble. 

i'm attaching an ubuntuzilla.py with the changed mirror list, give it a try and see if that's any better?

just unzip the file to somewhere, and run ```
python /path/to/ubuntuzilla.py
```

**UPDATE: this bugfix is now incorporated in the latest release of ubuntuzilla. No need to use this file anymore. Get the latest release from ubuntuzilla project site.**

---

### Post by graaant on 2009-08-04
That worked beautifully! :D

---

### Post by nanotube on 2009-08-04
> **graaant said:**
> That worked beautifully! :D

awesome! :)

don't know where the other two posters are from, but it could be that releases.mozilla.org doesn't play nice with non-us locations...

Well, if the other guys confirm the same, i think i'll just have to make a new point release with the new mirror list.

---

### Post by graaant on 2009-08-04
Really keen to hear how they go.
You're doing a great job, thanks for the efforts! :)

---

### Post by test666 on 2009-08-04
@nanotube

Worked on the first try. THANK YOU.

I was running Ubuntuzilla from Portugal. Perhaps this happened because of a faulty/slow local mirror? 

Keep up the good work.
Best wishes.

---

### Post by nanotube on 2009-08-04
great!

i think i'm convinced :)

i'll make a 4.7.1 release with a new mirror list in a bit.

---

### Post by nanotube on 2009-08-05
ok, just made a fresh release on sourceforge
should show up in a few minutes. :)

---

### Post by ubunoobie on 2009-08-05
> **nanotube said:**
> ok, just made a fresh release on sourceforge
should show up in a few minutes. :)

Hi nanotube,
I'm having the same issue... I downloaded the zip file you posted earlier and extracted, but I'm not understanding what to do next. When I run the code you posted, the error message says: can't open file.. ..no such file or directory

---

### Post by nanotube on 2009-08-05
Hi ubunoobie

please ignore the file I posted to this thread. that bugfix has already made it into the latest ubuntuzilla release.

so just go to the ubuntuzilla project site, and download the latest release and follow the instructions. :)

---

### Post by MY0613 on 2009-10-09
I got this problem today with 4.7.4 version.
```
ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.7.4

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
^CTraceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 737, in install
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 897, in getLatestVersion
    self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - http://www.mozilla.com |grep 'product=' -m 1", numlines=1, errormessage="Failed to retrieve the latest version of "+ self.options.package.capitalize())
  File "/usr/local/bin/ubuntuzilla.py", line 107, in getSystemOutput
    returncode = p.wait()
  File "/usr/lib/python2.6/subprocess.py", line 1123, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

```and 
```
/etc$ w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/
Index of ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.2/
linux-i686/

[Upper Directory]
af/. . . . . . . . . Jul 31 00:27
ar/. . . . . . . . . Jul 31 00:27
as/. . . . . . . . . Jul 31 00:27
be/. . . . . . . . . Jul 31 00:27
bg/. . . . . . . . . Jul 31 00:27
bn-BD/ . . . . . . . Jul 31 00:27
bn-IN/ . . . . . . . Jul 31 00:27
ca/. . . . . . . . . Jul 31 00:27
cs/. . . . . . . . . Jul 31 00:27
cy/. . . . . . . . . Jul 31 00:27
da/. . . . . . . . . Jul 31 00:27
de/. . . . . . . . . Jul 31 00:27
el/. . . . . . . . . Jul 31 00:27
en-GB/ . . . . . . . Jul 31 00:27
en-US/ . . . . . . . Jul 31 00:27
eo/. . . . . . . . . Jul 31 00:27
es-AR/ . . . . . . . Jul 31 00:27
es-CL/ . . . . . . . Jul 31 00:27
es-ES/ . . . . . . . Jul 31 00:27
es-MX/ . . . . . . . Jul 31 00:27
et/. . . . . . . . . Jul 31 00:27
eu/. . . . . . . . . Jul 31 00:27
fa/. . . . . . . . . Jul 31 00:27
fi/. . . . . . . . . Jul 31 00:27
fr/. . . . . . . . . Jul 31 00:27
fy-NL/ . . . . . . . Jul 31 00:27
ga-IE/ . . . . . . . Jul 31 00:27
gl/. . . . . . . . . Jul 31 00:27
gu-IN/ . . . . . . . Jul 31 00:27
he/. . . . . . . . . Jul 31 00:27
hi-IN/ . . . . . . . Jul 31 00:27
hr/. . . . . . . . . Jul 31 00:27
hu/. . . . . . . . . Jul 31 00:27
id/. . . . . . . . . Jul 31 00:27
is/. . . . . . . . . Jul 31 00:27
it/. . . . . . . . . Jul 31 00:27
ja/. . . . . . . . . Jul 31 00:27
ka/. . . . . . . . . Jul 31 00:27
kk/. . . . . . . . . Jul 31 00:27
kn/. . . . . . . . . Jul 31 00:27
ko/. . . . . . . . . Jul 31 00:27
ku/. . . . . . . . . Jul 31 00:27
lt/. . . . . . . . . Jul 31 00:27
lv/. . . . . . . . . Jul 31 00:27
mk/. . . . . . . . . Jul 31 00:27
ml/. . . . . . . . . Jul 31 00:27
mn/. . . . . . . . . Jul 31 00:27
mr/. . . . . . . . . Jul 31 00:27
nb-NO/ . . . . . . . Jul 31 00:27
nl/. . . . . . . . . Jul 31 00:27
nn-NO/ . . . . . . . Jul 31 00:27
oc/. . . . . . . . . Jul 31 00:27
or/. . . . . . . . . Jul 31 00:27
pa-IN/ . . . . . . . Jul 31 00:27
pl/. . . . . . . . . Jul 31 00:27
pt-BR/ . . . . . . . Jul 31 00:27
pt-PT/ . . . . . . . Jul 31 00:27
rm/. . . . . . . . . Jul 31 00:27
ro/. . . . . . . . . Jul 31 00:27
ru/. . . . . . . . . Jul 31 00:27
si/. . . . . . . . . Jul 31 00:27
sk/. . . . . . . . . Jul 31 00:27
sl/. . . . . . . . . Jul 31 00:27
sq/. . . . . . . . . Jul 31 00:27
sr/. . . . . . . . . Jul 31 00:27
sv-SE/ . . . . . . . Jul 31 00:27
ta-LK/ . . . . . . . Jul 31 00:27
ta/. . . . . . . . . Jul 31 00:28
te/. . . . . . . . . Jul 31 00:28
th/. . . . . . . . . Jul 31 00:28
tr/. . . . . . . . . Jul 31 00:28
uk/. . . . . . . . . Jul 31 00:28
vi/. . . . . . . . . Jul 31 00:28
xpi/ . . . . . . . . Jul 30 09:29
zh-CN/ . . . . . . . Jul 31 00:28
zh-TW/ . . . . . . . Jul 31 00:28

```how could I fix this? could give me direction?
Thanks for help.

Update:

I used this to make it working...
```
python2.5 /usr/local/bin/ubuntuzilla.py
```
Thanks. :)

---


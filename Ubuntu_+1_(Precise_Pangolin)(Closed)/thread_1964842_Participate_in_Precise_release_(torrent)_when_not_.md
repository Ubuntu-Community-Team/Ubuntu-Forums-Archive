---
title: "Participate in Precise release (torrent) when not at home??"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-04-24
I would love to participate in the Ubuntu online  release activity in my usual way on release day by downloading the torrent and then seeding like crazy.
:-)
My big prob is that on that day I will not be at home, I will be away from mid morning, and the release time is, I guess, likey to be in the afternoon or later. Any one got suggestiuons about how I might be able to arrange a pre set configuration with say, Transmission, or something, to automatically make the torrent active in my absence please?
tia

---

### Post by kostkon on 2012-04-24
I wrote this script for you, I haven't test it but, I guess, it should work
```
#!/usr/bin/env python

import glib
import urllib2
import os.path
import subprocess

RELEASE_NO = "12.04"
TORRENT_URL_i386 = "http://releases.ubuntu.com/%s/" \
              "ubuntu-%s-desktop-i386.iso.torrent" % (RELEASE_NO, RELEASE_NO)
TORRENT_URL_AMD64 = "http://releases.ubuntu.com/%s/" \
              "ubuntu-%s-desktop-amd64.iso.torrent" % (RELEASE_NO, RELEASE_NO)
FREQ = 60 # frequency in minutes. Check for torrent file every x minutes
SOCKET_TIMEOUT = 25
TORRENT_FILE_PATH = os.path.abspath("ubuntu_12.04.torrent")


req = urllib2.Request(TORRENT_URL_i386) # for i386 torrent
#req = urllib2.Request(TORRENT_URL_AMD64) # for amd64 torrent

def check_cb():
	try:
		# check if file exists
		torrent_url = urllib2.urlopen(req, timeout=SOCKET_TIMEOUT)
	except urllib2.URLError:
		# file does not exist yet, keep checking for it
		return True
	else:
		global loop
		# 12.04 torrent file exists
		# get file and save it locally
		torrent_contents = torrent_url.read()
		torrent_file = open(TORRENT_FILE_PATH, "w")
		torrent_file.write(torrent_contents)
		torrent_file.close()
		# add file to transmission
		subprocess.Popen(["transmission", TORRENT_FILE_PATH])
		loop.quit()

glib.timeout_add_seconds(FREQ*60, check_cb)

loop = glib.MainLoop()
loop.run()
```
It checks if the torrent file exists (you can specify how often, by setting the value of FREQ. 60mins is the default) and then it downloads it and adds it to transmission.

If you want to download the 64bit version, then uncomment the line for the amd64 request object and put a comment on the line above, i.e.
```
#req = urllib2.Request(TORRENT_URL_i386) # for i386 torrent
req = urllib2.Request(TORRENT_URL_AMD64) # for amd64 torrent
```

Just run it before you leave home.

Hope that helps.

---

### Post by candtalan on 2012-04-25
> **kostkon said:**
> I wrote this script for you, I haven't test it but, I guess, it should work
```
#!/usr/bin/env python

import glib
import urllib2
import os.path
import subprocess

RELEASE_NO = "12.04"
TORRENT_URL_i386 = "http://releases.ubuntu.com/%s/" \
              "ubuntu-%s-desktop-i386.iso.torrent" % (RELEASE_NO, RELEASE_NO)
TORRENT_URL_AMD64 = "http://releases.ubuntu.com/%s/" \
              "ubuntu-%s-desktop-amd64.iso.torrent" % (RELEASE_NO, RELEASE_NO)
FREQ = 60 # frequency in minutes. Check for torrent file every x minutes
SOCKET_TIMEOUT = 25
TORRENT_FILE_PATH = os.path.abspath("ubuntu_12.04.torrent")


req = urllib2.Request(TORRENT_URL_i386) # for i386 torrent
#req = urllib2.Request(TORRENT_URL_AMD64) # for amd64 torrent

def check_cb():
	try:
		# check if file exists
		torrent_url = urllib2.urlopen(req, timeout=SOCKET_TIMEOUT)
	except urllib2.URLError:
		# file does not exist yet, keep checking for it
		return True
	else:
		global loop
		# 12.04 torrent file exists
		# get file and save it locally
		torrent_contents = torrent_url.read()
		torrent_file = open(TORRENT_FILE_PATH, "w")
		torrent_file.write(torrent_contents)
		torrent_file.close()
		# add file to transmission
		subprocess.Popen(["transmission", TORRENT_FILE_PATH])
		loop.quit()

glib.timeout_add_seconds(FREQ*60, check_cb)

loop = glib.MainLoop()
loop.run()
```
It checks if the torrent file exists (you can specify how often, by setting the value of FREQ. 60mins is the default) and then it downloads it and adds it to transmission.

If you want to download the 64bit version, then uncomment the line for the amd64 request object and put a comment on the line above, i.e.
```
#req = urllib2.Request(TORRENT_URL_i386) # for i386 torrent
req = urllib2.Request(TORRENT_URL_AMD64) # for amd64 torrent
```

Just run it before you leave home.

Hope that helps.

WOW!! Thanks! That really is wonderful.

---

### Post by robgraves on 2012-04-25
Actually I think this is AWESOME, except, I modified it to do ubuntu 11.10 and ran the program and got this error:
```

robgraves@ubuntu:~$ python oneirictorrentcheck.py 
Traceback (most recent call last):
  File "oneirictorrentcheck.py", line 37, in check_cb
    subprocess.Popen(["transmission", TORRENT_FILE_PATH])
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


```
it did however downlaod the torrent file and save it in my home folder, but failed to open it in transmission

---

### Post by candtalan on 2012-04-25
For the record, I have tried the (kostkon) script, edited to aim at 11.10 for testing, and I had a problem or two which is not surprising because I am inexperienced at all this magic. However, after some editing and some simplification for me, to reduce complexity, :-) I came up with this

(modified also for a one minute repeat = testing)
(also for only 32 bit)
(hard coded for the release number)
(also transmission is called as transmission-gtk)
(also transmission preferences had to be first changed to stop the Options window appearing and reguiring a mouse click)

```

#!/usr/bin/env python

import glib
import urllib2
import os.path
import subprocess

# RELEASE_NO = "11.10"
TORRENT_URL_i386 = "http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.iso.torrent"


FREQ = 1 # frequency in minutes. Check for torrent file every x minutes
SOCKET_TIMEOUT = 25
TORRENT_FILE_PATH = os.path.abspath("ubuntu_11.10.torrent")

req = urllib2.Request(TORRENT_URL_i386) # for i386 torrent


def check_cb():
	try:
		# check if file exists
		torrent_url = urllib2.urlopen(req, timeout=SOCKET_TIMEOUT)
		
	except urllib2.URLError:
		# file does not exist yet, keep checking for it
		return True
	else:
		global loop
		# 11.10 torrent file exists
		# get file and save it locally
		torrent_contents = torrent_url.read()
		torrent_file = open(TORRENT_FILE_PATH, "w")
		torrent_file.write(torrent_contents)
		torrent_file.close()
		# add file to transmission
		subprocess.Popen(["transmission-gtk", TORRENT_FILE_PATH])
		loop.quit()

glib.timeout_add_seconds(FREQ*60, check_cb)

loop = glib.MainLoop()
loop.run()


```

which does seem to work
(Yay!)

---

### Post by robgraves on 2012-04-25
awesome, with your amendments it works for me as well

---


---
title: "IDJC canno't add mp3"
date: 2009-11-26
forum: Ubuntu Studio
---

### Post by kojis_ on 2009-11-26
I have troubles to add mp3 to idjc's 0.8.0 playlist.

I had before idjc version 0.7.2a and it worked well but now, when i updatet it to 0.8.0 it does not work anymore. In version 0.7.2a it was possible to add mp3 in to playlist.

I have Ubuntu Studio 8.04 and the error code is this when i started idjc from command line and try to add mp3:
```


  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 1570, in file_response
    for each in gen:
  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 1805, in get_elements_from_chosen
    meta = self.get_media_metadata(each)
  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 506, in get_media_metadata
    rg = float(audio["replaygain_track_gain"][0].rstrip(" dB"))
  File "/usr/lib/python2.5/site-packages/mutagen/easyid3.py", line 94, in __getitem__
    else: raise ValueError("%r is not a valid key" % key)
ValueError: 'replaygain_track_gain' is not a valid key


```

---

### Post by StephenF on 2009-11-26
You'll need this version which should be more compatible with older versions of mutagen. Console output would be appreciated if it isn't.

[http://web.bethere.co.uk/idjc/download/idjc-0.8.1_rc1.tar.gz](http://web.bethere.co.uk/idjc/download/idjc-0.8.1_rc1.tar.gz)

---

### Post by kojis_ on 2009-11-26
Installed 0.8.1_rc1, not working :(

```

kojis@us~$ idjc
Internet DJ Console Version 0.8.1_rc1
Copyright 2005-2009 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_US
shout_initialiser: shout_init called
started 6 encoders, 6 streamers, 2 recorders
threads initialised
jack sample rate is 44100
Restoring previous session
Traceback (most recent call last):
  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 1572, in file_response
    for each in gen:
  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 1807, in get_elements_from_chosen
    meta = self.get_media_metadata(each)
  File "/usr/local/lib/python2.5/site-packages/idjc/IDJCmedia.py", line 506, in get_media_metadata
    rg = float(audio["replaygain_track_gain"][0].rstrip(" dB"))
  File "/usr/lib/python2.5/site-packages/mutagen/easyid3.py", line 94, in __getitem__
    else: raise ValueError("%r is not a valid key" % key)
ValueError: 'replaygain_track_gain' is not a valid key

```

---

### Post by StephenF on 2009-11-26
Author is stupid. :-| Try again.

[http://web.bethere.co.uk/idjc/download/idjc-0.8.1_rc2.tar.gz](http://web.bethere.co.uk/idjc/download/idjc-0.8.1_rc2.tar.gz)

---

### Post by kojis_ on 2009-11-27
0.8.1rc2 works, can add mp3 now. Thanks.

This is really nice tool, thanks to all developers.

btw. i have still one problem, cant use checkinstall in compile process:
```

sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.8.1_rc2" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

```

---

### Post by StephenF on 2009-11-27
> **kojis_ said:**
> ```
*** Warning: The package version "0.8.1_rc2" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

```
The package version can be changed by editing the file configure.in on the fifth line. The problem character is the underscore.

The failsafe way to update ./configure would be to issue a
```

$ autoreconf -ifs

```
then go through the whole build process again.

---


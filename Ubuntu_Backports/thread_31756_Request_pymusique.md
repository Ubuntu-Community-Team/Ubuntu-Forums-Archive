---
title: "Request: pymusique"
date: 2005-05-04
forum: Ubuntu Backports
---

### Post by thully on 2005-05-04
Pymusique is a neat program - it lets you preview, search, and purchase from the iTunes store on Linux.  It seems to work quite well on Ubuntu, and I'm curious if anyone is interested in doing this for hoary-extras.  There may be legal issues (iTunes EULA), so I'm unsure of whether this can actually be packaged...

---

### Post by Technoviking on 2005-05-04
You can  find pymusique debs (made for Hoary) at [http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/) but there is a problem with the libfaad2 and gstreamer0.8-faad packages.

Mike

---

### Post by thully on 2005-05-04
[QUOTE=Mike Basinger]You can  find pymusique debs (made for Hoary) at [http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/) but there is a problem with the libfaad2 and gstreamer0.8-faad packages.

Mike[/QUOTE]
 I know about that (that's where I got my debs from - I just used gstreamer from marillat).
I just think it would be nice if it were available in a repository, and not just as loose .debs.

---

### Post by jdong on 2005-05-04
Alright, built and uploading :)

---

### Post by Technoviking on 2005-05-04
[QUOTE=jdong]Alright, built and uploading :)[/QUOTE]
Works well, I would suggest backporting the recommended package python-vlc.

Mike

---

### Post by thully on 2005-05-04
[QUOTE=Mike Basinger]Works well, I would suggest backporting the recommended package python-vlc.

Mike[/QUOTE]
 The pymusique package has a dependency on python2.4-mcrypt - which is not in Hoary nor
any of the backports/extras/staging repositories.  Could you backport this, along with python2.4-vlc and python2.4-mp4ff (which are all really needed for full operation of pymusique)?

---

### Post by Amaranth on 2005-05-04
[QUOTE=jdong]Alright, built and uploading :)[/QUOTE]
 I would recommend not distributing this. I have a feeling it'll end up being like DeCSS was...

---

### Post by thully on 2005-05-04
[QUOTE=Amaranth]I would recommend not distributing this. I have a feeling it'll end up being like DeCSS was...[/QUOTE]
 That is true and that's the reason I mentioned the legal issues in my post - I was a little unsure of posting this myself. However, I saw they actually had DeCSS and other questionable stuff packaged, so I went ahead and suggested this. IANAL, though.

---

### Post by Amaranth on 2005-05-07
*bump*

[https://fuware.net/pymusique/deb/python2.4-mcrypt_1.1-1_i386.deb](https://fuware.net/pymusique/deb/python2.4-mcrypt_1.1-1_i386.deb)
[https://fuware.net/pymusique/deb/python2.4-vlc_0.1-1_i386.deb](https://fuware.net/pymusique/deb/python2.4-vlc_0.1-1_i386.deb)
[https://fuware.net/pymusique/deb/python2.4-mp4ff_0.1-1_i386.deb](https://fuware.net/pymusique/deb/python2.4-mp4ff_0.1-1_i386.deb)

You'll also want it to depend on python2.4-gnome2-extras and gstreamer-faad. I'd fix our package but I don't have access to the web server. Also, I don't have the source for those packages but I can get Jon to give them to me if needed (don't know if you just upload these or if you rebuild them).

---

### Post by tube013 on 2005-05-11
When I run any version of pymusique (including the debs from the fuware site or backports) I get the following error:


Traceback (most recent call last):
  File "/usr/bin/pymusique", line 916, in ?
    window = GUI()
  File "/usr/bin/pymusique", line 166, in __init__
    column.set_fixed_width(int(cwidths[4]))
IndexError: list index out of range

any thoughts

---

### Post by Amaranth on 2005-05-11
[QUOTE=tube013]When I run any version of pymusique (including the debs from the fuware site or backports) I get the following error:


Traceback (most recent call last):
  File "/usr/bin/pymusique", line 916, in ?
    window = GUI()
  File "/usr/bin/pymusique", line 166, in __init__
    column.set_fixed_width(int(cwidths[4]))
IndexError: list index out of range

any thoughts[/QUOTE]
 It's because you used to use an old version. rm ~/.pymusique/cwidths and it should work again.

---

### Post by simianMiscreant on 2005-05-11
```
pymusique:
  Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed
 Depends: libxml2-python2.3  but it is not installable
 Depends: gstreamer0.8-faad but it is not going to be installed
 Depends: python-mcrypt but it is not going to be installed

```

i get that from synaptic when i try to install pymusique.

---

### Post by Amaranth on 2005-05-11
[QUOTE=simianMiscreant]```
pymusique:
  Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed
 Depends: libxml2-python2.3  but it is not installable
 Depends: gstreamer0.8-faad but it is not going to be installed
 Depends: python-mcrypt but it is not going to be installed

```

i get that from synaptic when i try to install pymusique.[/QUOTE]
 Either someone did something funny with the backport or you've gotten it from another repository.

---

### Post by Bo Rosén on 2005-05-12
[QUOTE=simianMiscreant]```
pymusique:
  Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed
 Depends: libxml2-python2.3  but it is not installable
 Depends: gstreamer0.8-faad but it is not going to be installed
 Depends: python-mcrypt but it is not going to be installed

```
[/QUOTE]

I got that too. You need to disable the marrilat repository (not sure about that really) and add the one for backports-hoary-staging.
```

deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted 

```

---

### Post by Bo Rosén on 2005-05-12
Thanks for doing the backports btw.
I noticed that the pymusique deb doesn't list a few countries that now have itunes stores (Sweden e.g) I tried sharpmusique from source and they are present there. Not a big deal I suppose, but a new build would be nice when you have the time.
Cheers

---

### Post by Bo Rosén on 2005-05-12
[QUOTE=Bo Rosén]stores (Sweden e.g) I tried sharpmusique from source and they are present there. Not a big deal I suppose, but a new build would be nice when you have the time.
Cheers[/QUOTE]

Replying to myself. It seems the country thing may be important as I can't buy anything with pymusique. Anyway, I'm assuming that's the issue, no idea really if it is. I can log in and preview songs, but I get an error that the song isn't currently available when I try to purchase it. I have no problems buying the same song with sharpmusique. Just a FYI.

---

### Post by tube013 on 2005-05-12
First off thinks for the tip on getting pymusique running.

secondly, I posted this in another forum, but it was a bit off topic.  Anyway I'm unable to load flies downloaded with pymusique onto my ipod with gtkpod-aac.

I get the following error:
```

Could not open '/home/byron/Music/Assembly of Dust - The Honest Hour -
Harrower.m4a' for reading, or file is not an mp4 file.
```

I worte the author of gtkpod, and here is his response:

> I've looked at the gtkpod code and am sure gtkpod is not to blame. Your
error description shows that the file is recognized as a MP4 file, but the
MP4Read(mp4FileName, 0); call in mp4_get_file_info() in mp4file.c is
failing. This is a call to the mp4v2 library.


I'm not sure how to procede with this.  Is gtkpod using an older mp4v2 lib or something?  gstreamer-faad is able to read and play the files, and tags.

---

### Post by rwabel on 2005-05-15
[QUOTE=Bo Rosén]I got that too. You need to disable the marrilat repository (not sure about that really) and add the one for backports-hoary-staging.
```

deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted 

```[/QUOTE]
 I get the same error in synaptic. I've all backports enabled and also tested once with disabling  marrilat repo. Indeed the needed files aren't in backport. I've then downloaded  python2.4-mcrypt_1.1-1_i386.deb from the homepage but it didn't want to install. 
```

rwabel@RALPH:~/compiling $ sudo dpkg -i python2.4-mcrypt_1.1-1_i386.deb
Selecting previously deselected package python2.4-mcrypt.
(Reading database ... 313524 files and directories currently installed.)
Unpacking python2.4-mcrypt (from python2.4-mcrypt_1.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of python2.4-mcrypt:
 python2.4-mcrypt depends on libmcrypt4; however:
  Package libmcrypt4 is not installed.
dpkg: error processing python2.4-mcrypt (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-mcrypt

```
Don't know why that error, because I could install libmcrypt4 manually and then python2.4-mcrypt_1.1-1_i386.deb could be installed.

Finally it works :-)

---


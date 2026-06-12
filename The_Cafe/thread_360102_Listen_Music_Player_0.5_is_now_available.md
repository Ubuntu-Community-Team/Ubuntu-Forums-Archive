---
title: "Listen Music Player 0.5 is now available"
date: 2007-02-12
forum: The Cafe
---

### Post by dlbolton on 2007-02-12
I just noticed that version 0.5 of Listen is now available (updated on 2007.02.13) [here]("http://www.listen-project.org").  I have played around with the 0.5b1 version but  couldn't get my ipod shuffle to work with it, so I moved back to 0.4.3.  Version 0.4.3 works pretty well, but 0.5b1 was better with podcasts. 

So far it is only available as source.  I will try to get the new version to work tonight and will report back.

---

### Post by rekahsoft on 2007-02-12
i have built and installed it with ease....it is looking very nice as i am using it right now to download some podcasts...for anybody who want to build and install it from source here is a little how-to (note: this is just a quicky):
First you must have all the dependacies installed (check the listen webbsite and synaptic to install them)
After you have all the dependacies installed download the source, uncompress it and run check.py
If you pass all the requirements then go on to make and install by doing the following:```
make
sudo make install
``` there you have it, a very quick how-to.

---

### Post by marcus2004 on 2007-02-13
I cannot seem to get it to go past the make I get the following error and I am not sure what is causing it to fail. I noticed that it says python.h no such file or directory I am wondering if that has anything to do with it. I have python 2.5 installed. 

```
mmkeyspy.c:3:20: error: Python.h: No such file or directory
In file included from mmkeys.override:6:
/usr/include/pygtk-2.0/pygobject.h:20: error: expected specifier-qualifier-list before &#8216;PyObject&#8217;
/usr/include/pygtk-2.0/pygobject.h:27: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:38: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:48: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:60: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:67: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyTypeObject&#8217;
/usr/include/pygtk-2.0/pygobject.h:68: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/usr/include/pygtk-2.0/pygobject.h:76: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pygtk-2.0/pygobject.h:78: error: expected &#8216;;&#8217; before &#8216;void&#8217;
mmkeys.c:16: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mmkeys.c:21: warning: data definition has no type or storage class
mmkeys.c:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PyTypeObject&#8217;
mmkeys.c:21: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;PyMmKeys_Type&#8217;
mmkeys.c:30: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
mmkeys.c:30: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
mmkeys.c: In function &#8216;_wrap_mmkeys_new&#8217;:
mmkeys.c:34: warning: implicit declaration of function &#8216;PyArg_ParseTupleAndKeywords&#8217;
mmkeys.c:34: error: &#8216;args&#8217; undeclared (first use in this function)
mmkeys.c:34: error: (Each undeclared identifier is reported only once
mmkeys.c:34: error: for each function it appears in.)
mmkeys.c:34: error: &#8216;kwargs&#8217; undeclared (first use in this function)
mmkeys.c:39: error: &#8216;struct _PyGObject_Functions&#8217; has no member named &#8216;pygobject_constructv&#8217;
mmkeys.c:40: error: &#8216;PyGObject&#8217; has no member named &#8216;obj&#8217;
mmkeys.c:41: warning: implicit declaration of function &#8216;PyErr_SetString&#8217;
mmkeys.c:42: error: &#8216;PyExc_RuntimeError&#8217; undeclared (first use in this function)
mmkeys.c: At top level:
mmkeys.c:49: warning: data definition has no type or storage class
mmkeys.c:49: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PyTypeObject&#8217;
mmkeys.c:49: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;PyMmKeys_Type&#8217;
mmkeys.c:98: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;mmkeys_functions&#8217;
mmkeys.c:104: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
error: command 'gcc' failed with exit status 1
make[1]: *** [build] Error 1
make[1]: Leaving directory `/home/marc/Desktop/listen-0.5/mmkeys'
make: *** [mmkeys.so] Error 2

```


Edit : I got it working. I installed the python-dev and reinstalled python-mutagen which seemed to work.

---

### Post by dlbolton on 2007-02-13
I didn't get very far with this.  When I entered the command:

sudo make

I received an error message telling me I needed pyGTK 2.6.  I looked in synaptic package manager and couldn't find a package named "pyGTK".  Is this an abbreviation for something else (like python-gtk or python-gtk2)?

---

### Post by v8YKxgHe on 2007-02-13
> **dlbolton said:**
> I didn't get very far with this.  When I entered the command:

sudo make

I received an error message telling me I needed pyGTK 2.6.  I looked in synaptic package manager and couldn't find a package named "pyGTK".  Is this an abbreviation for something else (like python-gtk or python-gtk2)?

Probably, but look for the -dev package, so if it is python-gtk install that and python-gtk-dev

---

### Post by flowbot on 2007-02-13
Is anyone able to use the **Lyrics** or **Wikipedia** tab without Listen crashing with a segmentation fault? I tried the suggestion on >>[this](http://www.listen-project.org/wiki/Faq)<< page, but it still segfaults :(

---

### Post by AhmadMF on 2007-02-13
I installed listen 0.5 but it won't start... It shows the splash screen and then just disappears.

I tried running it from the terminal and it spewed the following:

```
ahmad@ahmad-desktop:~$ listen
/usr/lib/listen/stock.py:78: DeprecationWarning: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
  import const
/usr/lib/listen/player.py:33: DeprecationWarning: Non-ASCII character '\xc2' in file /usr/lib/listen/song.py on line 716, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
  from song import sType
No musicbrainz support (musicbrainz2 missing)
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 219, in ?
    ListenApp()
  File "/usr/lib/listen/listen.py", line 145, in __init__
    from widget.listen import Listen
  File "/usr/lib/listen/widget/listen.py", line 34, in ?
    from widget.player_ui import PlayerUI
  File "/usr/lib/listen/widget/player_ui.py", line 33, in ?
    from widget.dynamic_playlist import DynamicPlaylist
  File "/usr/lib/listen/widget/dynamic_playlist.py", line 30, in ?
    from lastfm_service import lastfm_info
  File "/usr/lib/listen/lastfm_service.py", line 27, in ?
    from xml.etree.ElementTree import fromstring as XMLFromString
ImportError: No module named etree.ElementTree
ahmad@ahmad-desktop:~$ 

```

Any suggestions?

---

### Post by denisesballs on 2007-02-13
Here's what I did:

```
sudo apt-get build-dep listen
```

That should grab most of the dependencies. Then I tried this:

```
make
```

but got

```
Listen require mutagen >= 1.8.
        (http://www.sacredchao.net/quodlibet/wiki/Development/Mutagen)
make: *** [check] Error 1
```

So I downloaded Mutagen from the web since I had all the Mutagen related packages in the repos, get it here - [http://www.sacredchao.net/~piman/software/mutagen-1.10.1.tar.gz](http://www.sacredchao.net/~piman/software/mutagen-1.10.1.tar.gz)

```
tar xvzf mutagen-1.10.1.tar.gz
```

```
./setup.py build
```

```
sudo ./setup.py install
```

That should get Mutagen installed properly. Then go back to your listen directory and do:

```
make
```

and then

```
sudo checkinstall
```

Then I moved my .listen-test directory and started over with my library just to make sure. However I do get it crashing when I click the Wikipedia or Lyrics tab. 

Anyone know why he removed the Listen repository??? That would've been so nice...

---

### Post by denisesballs on 2007-02-13
EDIT TO ABOVE!

I figured it out, it's on the Listen FAQ: [http://www.listen-project.org/wiki/Faq](http://www.listen-project.org/wiki/Faq)

I had to change my /usr/bin/listen from:

```
python -OO /usr/lib/listen/listen.py "$@"
```

to

```
LD_LIBRARY_PATH=/usr/lib/firefox python -OO /usr/lib/listen/listen.py "$@"
```

**[SIZE="5"][COLOR="Red"]MAKE SURE YOU COMMENT OUT THE ORIGINAL LINE WITH A "#" INSTEAD OF CHANGING IT![/COLOR][/SIZE]**

---

### Post by denisesballs on 2007-02-13
ONE MORE EDIT!

I did put my .listen-test back and the new Listen appears to work fine with it, but it needs to be copied from .listen-test to .listen. Hope this helps!

---

### Post by tychocity on 2007-02-13
another missing package  sudo apt-get install python-elementtree

---

### Post by AhmadMF on 2007-02-14
> **tychocity said:**
> another missing package  sudo apt-get install python-elementtree
Wow! thanks, tychocity! That made it work.

---

### Post by Hells_Dark on 2007-02-14
Mmm... i'm waiting for a pack because with some dependencies.
Because without Internet on my computer... -_-

---

### Post by hanzomon4 on 2007-02-14
I can't get tunepimp 0.5, any ideas how?

---

### Post by FlyingHat on 2007-02-14
For TunePimp, grab the source from here: [http://musicbrainz.org/ftpmirror/pub/musicbrainz/libtunepimp-0.5.3.tar.gz](http://musicbrainz.org/ftpmirror/pub/musicbrainz/libtunepimp-0.5.3.tar.gz) and run the usual:

./configure
make
make install

This will install both Python and Perl libraries for libtunepimp.

However I too have an issue.  I can get Listen 0.5 to build fine, but when executing it it complains that it needs mutagen >= 1.8.  I checked, and mutagen does exist in /usr/lib/python2.4/site-packages as well as the executables in /usr/bin.

Any thoughts?

---

### Post by mojohn on 2007-02-14
I installed Listen v. 0.5 last night. Everything seems to work just fine, except that whenever I click on the wiki or lyrics links in the center task bar, Listen shuts down.

Running Dapper on a Dell Inspiron 1100.

Any ideas?

Thanks, 

mojohn

---

### Post by denisesballs on 2007-02-14
> **mojohn said:**
> I installed Listen v. 0.5 last night. Everything seems to work just fine, except that whenever I click on the wiki or lyrics links in the center task bar, Listen shuts down.

Running Dapper on a Dell Inspiron 1100.

Any ideas?

Thanks, 

mojohn

 Read the whole thread

---

### Post by rko618 on 2007-02-14
> **denisesballs said:**
> EDIT TO ABOVE!

I figured it out, it's on the Listen FAQ: [http://www.listen-project.org/wiki/Faq](http://www.listen-project.org/wiki/Faq)

I had to change my /usr/bin/listen from:

```
python -OO /usr/lib/listen/listen.py "$@"
```

to

```
LD_LIBRARY_PATH=/usr/lib/firefox python -OO /usr/lib/listen/listen.py "$@"
```



denisesballs can you elaborate on how to do this?  Is this a line in a file that we need to change?  If so what file?  I couldn't figure it out.

> 
I did put my .listen-test back and the new Listen appears to work fine with it, but it needs to be copied from .listen-test to .listen. Hope this helps!


once again I have no idea what your talking about.  Where is .listen-test?

---

### Post by denisesballs on 2007-02-14
> **rko618 said:**
> denisesballs can you elaborate on how to do this?  Is this a line in a file that we need to change?  If so what file?  I couldn't figure it out.

Well yes, it says above

> I had to change my /usr/bin/listen

That's the name of the file. So do:

```
sudo gedit /usr/bin/listen
```

and change the line:

```
python -OO /usr/lib/listen/listen.py "$@"
```

to:

```
LD_LIBRARY_PATH=/usr/lib/firefox python -OO /usr/lib/listen/listen.py "$@"
```


> once again I have no idea what your talking about.  Where is .listen-test?

Don't worry about that, like I said later in the thread, it doesn't matter.

---

### Post by rko618 on 2007-02-14
Ah thanks denisesballs.  I thought /usr/bin/listen was a directory like /usr/lib/listen is.

Thanks again.

---

### Post by hanzomon4 on 2007-02-14
I just added the edgy [musicbranz repo]("http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2") to my source list and apt-geted whatever listen complained about. I would add the repo and then do a [sudo apt-get build-dep listen] that should grab all of the dependencies.

OT: I went to the lastFM website to figure out my password for the audioscrobbler in listen and rediscovered the [last-exit]("http://folks.o-hand.com/iain/last-exit/") lastFM-radio player. It's much better then the player from lastFM and it makes for a great radio.....

---

### Post by Patskumaster on 2007-02-15
When I try start Listen 0.5, I get this error. What I should be do? I use Feisty Fawn.

```

~$ listen
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 66, in <module>
    import utils, const, stock, config
  File "/usr/lib/listen/utils.py", line 33, in <module>
    import stock
  File "/usr/lib/listen/stock.py", line 78, in <module>
    import const
  File "/usr/lib/listen/const.py", line 116
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

---

### Post by kellsens on 2007-02-15
I do what [http://www.listen-project.org/wiki/Faq](http://www.listen-project.org/wiki/Faq) says to do, but Listen continues crashing in Wikipedia and Listen.
Any sugestion ?

Kellsens

P.S.: Sorry my english :D

---

### Post by denisesballs on 2007-02-15
> **kellsens said:**
> I do what [http://www.listen-project.org/wiki/Faq](http://www.listen-project.org/wiki/Faq) says to do, but Listen continues crashing in Wikipedia and Listen.
Any sugestion ?

Kellsens

P.S.: Sorry my english :D

Again, READ THE WHOLE THREAD! It's like 2 posts above! ^^

---

### Post by kellsens on 2007-02-15
Hi Denisesballs.

    So, I allready read all the thread and do it exactly like you said to rko618, and Listen continues crashing on wiki / lyricis.
    Any sugestion ? :) 

Kellsens

---

### Post by marcus2004 on 2007-02-15
Kellsens,
I found this problem in another thread. Maybe it might help.

[http://www.ubuntuforums.org/showpost.php?p=1835259&postcount=503]("http://www.ubuntuforums.org/showpost.php?p=1835259&postcount=503")

---

### Post by kellsens on 2007-02-15
Hi Marcus !

  Thank's for the help, but, i tryed some of solutions on the pos you send it to me. And still not working wiki / lyrics. 
   I still have hope. [-o< :D

Kellsens

---

### Post by SorinN on 2007-02-16
Someone must help Listen developer to integrate Listen 05 with Feisty - I got Listen work using different revisions of 0.5 version - but every time I got different little errors. Under Edgy is OK.

This message target on Feisty developers too - don't forget Listen for next stable release guys - now is simply the best choice  on Gnome.

---

### Post by SorinN on 2007-02-16
> **Patskumaster said:**
> When I try start Listen 0.5, I get this error. What I should be do? I use Feisty Fawn.

```

~$ listen
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 66, in <module>
    import utils, const, stock, config
  File "/usr/lib/listen/utils.py", line 33, in <module>
    import stock
  File "/usr/lib/listen/stock.py", line 78, in <module>
    import const
  File "/usr/lib/listen/const.py", line 116
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```
to Patskumaster

sudo gedit /usr/lib/listen/const.py

then remove from consty.py the lines where the letters are non-english letters ( look strange ).
there are 3 or 4 lines at the bottom of document. 

then start again with command : listen -> u will receive the second error on other file ( i dont remember exact ...), at line 716 or some. Do the same thing on this file - is a single  strange letter before a declaration. 

After that U will have some errors regarding dbus invocation procedure. Will not work as user with 'listen'  command but will work with 'sudo listen'. 

I still hope on a stable version on Feisty.

Best Luck

---

### Post by bdb51 on 2007-02-17
> **SorinN said:**
> to Patskumaster

sudo gedit /usr/lib/listen/const.py

then remove from consty.py the lines where the letters are non-english letters ( look strange ).
there are 3 or 4 lines at the bottom of document. 

then start again with command : listen -> u will receive the second error on other file ( i dont remember exact ...), at line 716 or some. Do the same thing on this file - is a single  strange letter before a declaration. 

After that U will have some errors regarding dbus invocation procedure. Will not work as user with 'listen'  command but will work with 'sudo listen'. 

I still hope on a stable version on Feisty.

Best Luck

Could you tell me how the letter on line 716 looks like, because I can't seem to find it.

---

### Post by Patskumaster on 2007-02-18
> **bdb51 said:**
> to Patskumaster

sudo gedit /usr/lib/listen/const.py

then remove from consty.py the lines where the letters are non-english letters ( look strange ).
there are 3 or 4 lines at the bottom of document. 

then start again with command : listen -> u will receive the second error on other file ( i dont remember exact ...), at line 716 or some. Do the same thing on this file - is a single  strange letter before a declaration. 

After that U will have some errors regarding dbus invocation procedure. Will not work as user with 'listen'  command but will work with 'sudo listen'. 

I still hope on a stable version on Feisty.

Best Luck

Thanks to help! I edited const.py and song.py(line 716) files.
Now I get following error:

```

$ listen
No musicbrainz support (musicbrainz2 missing)
No iPod support
No Audio cd support (musicbrainz2 missing)
Error grabbing key 144, 0x848b400
Error grabbing key 153, 0x848b400
Error grabbing key 162, 0x848b400
Error grabbing key 164, 0x848b400
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 219, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 146, in __init__
    self.listen_instance = Listen()
  File "/usr/lib/listen/widget/listen.py", line 121, in __init__
    self.dbus_service = ListenDBus(self,player)
  File "/usr/lib/listen/dbus_manager.py", line 56, in __init__
    dbus.service.Object.__init__(self, bus_name, object_path)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 418, in __init__
    self._connection._register_object_path(object_path, self._message_cb, self._unregister_cb)
RuntimeError: To make asynchronous calls, receive signals or export objects, D-Bus connections must be attached to a main loop by passing mainloop=... to the constructor or calling dbus.set_default_main_loop(...)

```

> **bdb51 said:**
> Could you tell me how the letter on line 716 looks like, because I can't seem to find it.

Song.py line 716 looks like this:

```

#|Â tunepimp.tpThreadLookupPUID | tunepimp.tpThreadLookupFile )

```

Ps. Sorry for my English. I hope you understand my text.

---

### Post by SorinN on 2007-02-19
#|Â tunepimp.tpThreadLookupPUID | tunepimp.tpThreadLookupFile ) 
shoult be:
# tunepimp.tpThreadLookupPUID | tunepimp.tpThreadLookupFile )

after U correct all of these - U can start Listen from terminal using 'sudo listen'. Don't look at console errors - Listen will work.

Good Audition !

---

### Post by Patskumaster on 2007-02-21
> **SorinN said:**
> #|Â tunepimp.tpThreadLookupPUID | tunepimp.tpThreadLookupFile ) 
shoult be:
# tunepimp.tpThreadLookupPUID | tunepimp.tpThreadLookupFile )

after U correct all of these - U can start Listen from terminal using 'sudo listen'. Don't look at console errors - Listen will work.

Good Audition !

Big Thanks! Now Listen works. :-D

---

### Post by Nonno Bassotto on 2007-02-21
Does anybody know if there will be some package/repository like before? Or can anyone contact Theli and ask (I wasn't able to find any email on his site)?

It seems that compiling it is quite complicated, building a package may be even more.

---

### Post by drkduncan on 2007-02-21
I'm having issues installing listen and i have read through the entire post :) , when i run ./check.py i get this back:

Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6 found
Checking for gnome.ui; found
Checking for egg.trayicon: found
Checking for mutagen:
Traceback (most recent call last):
  File "./check.py", line 59, in ?
    if float(mutagen.version_string) < 1.6:
ValueError: invalid literal for float(): 1.10.1

anybody have any idea's?

---

### Post by Kuoi on 2007-02-22
Can't get Mutagen 1.8 installed.

After doing the tar command in my home directory, it is unpacked but then ..
When i type > ./setup.py i get an error 
> bash: ./setup.py: No such file or directory


Can somebody help me out ?

Kuoi

---

### Post by Kuoi on 2007-02-22
I did > wget [http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz](http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz)
tar xvfz mutagen-1.8.tar.gz
cd mutagen*
./setup.py build
sudo ./setup.py install , and now Mutagen 1.10 is installed , but the Listen setup gives many more errors.

I stick with version 4.3 for now.

That's my only negative experience with Linux ( Ubuntu ) ...
UPDATING software is almost impossible or takes hours !!!
I can't believe I'm still trying :confused: 

Kuoi

---

### Post by Corbelius on 2007-02-22
> **drkduncan said:**
> I'm having issues installing listen and i have read through the entire post :) , when i run ./check.py i get this back:

Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6 found
Checking for gnome.ui; found
Checking for egg.trayicon: found
Checking for mutagen:
Traceback (most recent call last):
  File "./check.py", line 59, in ?
    if float(mutagen.version_string) < 1.6:
ValueError: invalid literal for float(): 1.10.1

anybody have any idea's?

Try this if u have edgy eft: [http://janvitus.cabspace.com/ubuntu/pool/edgy-janvitus/main-amd64/python-mutagen_1.9-0ubuntu3~janvitus_all.deb](http://janvitus.cabspace.com/ubuntu/pool/edgy-janvitus/main-amd64/python-mutagen_1.9-0ubuntu3~janvitus_all.deb)

---

### Post by Forlong on 2007-02-23
Does anybody get to work Audio-CDs with this?
I installed python-musicbrainz2-0.4.1 and it doesn't complain about "No Audio cd support" anymore but Listen still doesn't recognize my CDs.

When I put a CD in my drive and start Listen afterwards I get this:
```
W:MusicBrainzAudioCD:No disk id
```

btw: it still complains about
```
No musicbrainz support (tunepimp missing or version < 0.5)
```
does this have anything to do with it?
I tried installing libtunepimp-0.5.3 but it complains about way too many dependencies and since I don't care about musicbrainz, I gave up on that.

---

### Post by hanzomon4 on 2007-02-23
Try adding the musicbrainz repo, I'll look for specifics hold on.....

Got it!
add this line to your /etc/apt/source.lst```
#musicbrainz repo
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu edgy musicbrainz

```

Then apt-get install libtunepimp5

This should grab everything you need

---

### Post by Forlong on 2007-02-23
Thanks a lot, hanzomon4!

I only had to uninstall python2.4-tunepimp before I could install python-tunepimp from the repository.
Now Listen isn't complaining about any missing support anymore but unfortunately it didn't solve the actual problem with the Audio-CDs.

I still get the "W:MusicBrainzAudioCD:No disk id" message and there's just no option for CD-playback :-(

---

### Post by hanzomon4 on 2007-02-23
Did you recompile listen?

---

### Post by Forlong on 2007-02-23
> **hanzomon4 said:**
> Did you recompile listen?
Yes, didn't change anything.

_But_ I checked, what more packages are in the musicbrainz-repository ([http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu/dists/edgy/musicbrainz/binary-i386/](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu/dists/edgy/musicbrainz/binary-i386/)) and basically installed every package that sounded well enough to be of any avail (I know... probably not the best way to achieve something), installed Listen again and now it works. :)

Thank you so much for your help!
Unfortunately I can't tell what packages are the ones that were really necessary, so it's not that much help for other users but at least you know there is a way ;)

Thanks again,
Nick

---

### Post by Cuppa-Chino on 2007-03-01
still cannot compile I did what was said mutagen and all but then I get this:

```

johnny@Superbrummer:~/listen-0.5$ make
Checking for Python... /usr/bin/python
Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6: found
Checking for gnome.ui: found
Checking for egg.trayicon: found
Checking for pygtkmozembed: found
Checking for mutagen: found
Checking for PyGSt >= 0.10: found
Checking for DBUS: found
Checking for python-libgpod: found
Checking for python-musicbrainz2: not found
, but recommanded
Checking for python-tunepimp > 0.5: not found
, but recommanded
Checking for libsexy: not found
Listen recommends python sexy for sexy widget. 
make -C mmkeys
make[1]: Entering directory `/home/johnny/listen-0.5/mmkeys'
pygtk-codegen-2.0 --prefix mmkeys \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gdk-types.defs \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gtk-types.defs \
        --override mmkeys.override \
        mmkeys.defs > gen-tmp
***INFO*** There are no declared global functions.
***INFO*** There are no declared methods.
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
mv gen-tmp mmkeyspy.c
./setup.py build
running build
running build_ext
building 'mmkeys' extension
creating build
creating build/temp.linux-i686-2.4
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeyspy.c -o build/temp.linux-i686-2.4/mmkeyspy.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeys.c -o build/temp.linux-i686-2.4/mmkeys.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeysmodule.c -o build/temp.linux-i686-2.4/mmkeysmodule.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
creating build/lib.linux-i686-2.4
gcc -pthread -shared build/temp.linux-i686-2.4/mmkeyspy.o build/temp.linux-i686-2.4/mmkeys.o build/temp.linux-i686-2.4/mmkeysmodule.o -o build/lib.linux-i686-2.4/mmkeys.so -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0
cp build/lib*/mmkeys.so .
make[1]: Leaving directory `/home/johnny/listen-0.5/mmkeys'
cp mmkeys/mmkeys.so src/mmkeys.so
for lang in ./zh_CN ./be ./ar ./ca ./bn ./br ./da ./de ./cs ./es ./fi ./et ./fr ./gl ./hu ./ja ./it ./ko ./lv ./nb ./nl ./pa ./pl ./pt ./ro ./ru ./sk ./sr ./sv ./tr ./uk ./vi ./en_CA ./en_GB ./en_US ./pt_BR; do msgfmt po/$lang.po -o po/$lang.mo;done
intltool-merge -d po misc/listen.desktop.in misc/listen.desktop
make: intltool-merge: Command not found
make: *** [po-data] Error 127



```

what next ?

thanks

---

### Post by tbroderick on 2007-03-01
Do you have intltool installed?

---

### Post by Wayren on 2007-03-01
After a bit of beating Ubuntu with a stick I finally got Listen compiled and installed successfully. My only problem is that my library has 2 copies of every file for some reason. When I try to right-click and remove, the file remains. Anyone know how to empty out my library completely so I can just start over? I can't figure out which file to delete, where it is or how to do it from inside the application.

---

### Post by Forlong on 2007-03-02
> **Wayren said:**
> Anyone know how to empty out my library completely so I can just start over?
You could just delete the (hidden) **.listen** folder in your home directory - consider making a backup first:
```
 cp -r .listen .listen-bak
```
```
 rm -r .listen
```
Next time you'll start Listen it will create a new .listen-folder and you can start all over.

---

### Post by olskar on 2007-03-02
> askar@barbara:~/listen-0.5$ sudo make 
Checking for Python... /usr/bin/python
Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6: found
Checking for gnome.ui: found
Checking for egg.trayicon: found
Checking for pygtkmozembed: found
Checking for mutagen: found
Checking for PyGSt >= 0.10: found
Checking for DBUS: found
Checking for python-libgpod: not found
Listen recommends python-gpod ([http://www.gtkpod.org](http://www.gtkpod.org))
Checking for python-musicbrainz2: not found
, but recommanded
Checking for python-tunepimp > 0.5: not found
, but recommanded
Checking for libsexy: not found
Listen recommends python sexy for sexy widget. 
make -C mmkeys
make[1]: Entering directory `/home/askar/listen-0.5/mmkeys'
pygtk-codegen-2.0 --prefix mmkeys \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gdk-types.defs \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gtk-types.defs \
        --override mmkeys.override \
        mmkeys.defs > gen-tmp
***INFO*** There are no declared global functions.
***INFO*** There are no declared methods.
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
mv gen-tmp mmkeyspy.c
./setup.py build
running build
running build_ext
building 'mmkeys' extension
creating build
creating build/temp.linux-i686-2.4
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeyspy.c -o build/temp.linux-i686-2.4/mmkeyspy.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
mmkeyspy.c:3:20: error: Python.h: No such file or directory
In file included from mmkeys.override:6:
/usr/include/pygtk-2.0/pygobject.h:20: error: expected specifier-qualifier-list before ‘PyObject’
/usr/include/pygtk-2.0/pygobject.h:27: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/pygtk-2.0/pygobject.h:38: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/pygtk-2.0/pygobject.h:48: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/pygtk-2.0/pygobject.h:60: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/pygtk-2.0/pygobject.h:67: error: expected declaration specifiers or ‘...’ before ‘PyTypeObject’
/usr/include/pygtk-2.0/pygobject.h:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/pygtk-2.0/pygobject.h:76: error: expected ‘)’ before ‘*’ token
/usr/include/pygtk-2.0/pygobject.h:78: error: expected ‘;’ before ‘void’
mmkeys.c:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mmkeys.c:21: warning: data definition has no type or storage class
mmkeys.c:21: warning: type defaults to ‘int’ in declaration of ‘PyTypeObject’
mmkeys.c:21: error: expected ‘,’ or ‘;’ before ‘PyMmKeys_Type’
mmkeys.c:30: error: expected declaration specifiers or ‘...’ before ‘PyObject’
mmkeys.c:30: error: expected declaration specifiers or ‘...’ before ‘PyObject’
mmkeys.c: In function ‘_wrap_mmkeys_new’:
mmkeys.c:34: warning: implicit declaration of function ‘PyArg_ParseTupleAndKeywords’
mmkeys.c:34: error: ‘args’ undeclared (first use in this function)
mmkeys.c:34: error: (Each undeclared identifier is reported only once
mmkeys.c:34: error: for each function it appears in.)
mmkeys.c:34: error: ‘kwargs’ undeclared (first use in this function)
mmkeys.c:39: error: ‘struct _PyGObject_Functions’ has no member named ‘pygobject_constructv’
mmkeys.c:40: error: ‘PyGObject’ has no member named ‘obj’
mmkeys.c:41: warning: implicit declaration of function ‘PyErr_SetString’
mmkeys.c:42: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
mmkeys.c: At top level:
mmkeys.c:49: warning: data definition has no type or storage class
mmkeys.c:49: warning: type defaults to ‘int’ in declaration of ‘PyTypeObject’
mmkeys.c:49: error: expected ‘,’ or ‘;’ before ‘PyMmKeys_Type’
mmkeys.c:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mmkeys_functions’
mmkeys.c:104: error: expected ‘)’ before ‘*’ token
error: command 'gcc' failed with exit status 1
make[1]: *** [build] Error 1
make[1]: Leaving directory `/home/askar/listen-0.5/mmkeys'
make: *** [mmkeys.so] Error 2


What is wrong?

---

### Post by tbroderick on 2007-03-02
> **olskar said:**
> What is wrong?

You got python2.4-dev installed?

---

### Post by Cuppa-Chino on 2007-03-02
> **tbroderick said:**
> Do you have intltool installed?

that helped, lets see if I can get it to work now

---

### Post by sherl0k on 2007-03-02
I'm still getting that segmentation fault even with editing the /usr/bin/listen file. Anyone else having this problem?

---

### Post by Kuoi on 2007-03-03
After reading the treath , I've installed Listen 0.5  , or I think I am.

I didn't had any error , but now Listen won't even start anymore.

Install from tar's etc. on Ubuntu ( or all Linux ) ...yeah yeah ,whatever man !
If you're real lucky , you can get one to work , but I'm beginning to have the feeling that you must have many many luck.

I presume if I do a > sudo apt-get install Listen , I'll get the version  4.3 again ?
It's still better than now , ... now it won't even start.

I like to test and update software , but since I use Ubuntu for about a month ( My first Linux steps ) , I get it many times on my nerves !!

Kuoi

---

### Post by punkass on 2007-03-06
Here is just a quick deb I made at work (so I could have the new Listen here) ;)

---

### Post by Kuoi on 2007-03-07
Hello "Punkass" ,
Thank you very much , this is (for me) the first Listen.deb that works.
I'm now listening my songs with Listen version 0.5 ... YES !!
I like the lyrics future , because I didn't see that on any Windoos software before.
I've also installed Streamtuner and xmms to listen to internet radio stations , and I wasn't aware that it was that simple to listen to them .
Hmm , all this makes Windoos almost useless.
But then again , I need it for my minidisc and for editing my recordings.
After using Ubuntu for  about a month , the above is the only reason I need Windoos . 

Thank you , and all other members here who make it so simple to use Ubuntu the right way .=D> 

Kuoi

---

### Post by Kuoi on 2007-03-07
Before you'll mention it...

I've tried the radiostations future in Listen now (in version 4.3 it wasn't working well here) , and I must say it's as quick as Streamtuner , and has all my radiostations too.

I'm about to uninstall Streamtuner and xmms , but will wait till I've rebooted a couple of times.

Greetings , and thanks again , Kuoi

---

### Post by drworm01 on 2007-03-08
I'm having problems installing Listen 0.5 that aren't mentioned in the thread.
I do
./check.py
make
then I get this:
> make -C mmkeys
make[1]: Entering directory `/home/user/listen-0.5/mmkeys'
cp build/lib*/mmkeys.so .
cp: cannot stat `build/lib*/mmkeys.so': No such file or directory
make[1]: *** [mmkeys.so] Error 1
make[1]: Leaving directory `/home/user/listen-0.5/mmkeys'
make: *** [mmkeys.so] Error 2

I tried using punkass's deb package above, but it says I need libatk1.0-0 installed. So I check, and I have it installed but I look for an updated version. When I try to install that, I'm told I need libc6, which, it turns out, I already have installed. What am I doing wrong?
Thanks.

---

### Post by drworm01 on 2007-03-08
Sorry. Forgot to mention I'm using Dapper.

---

### Post by drworm01 on 2007-03-09
I seem to have gotten it sorted out. I still need to do the lyrics/wiki fix, but Lisen 0.5 is working. I had to install libsexymm. Then it said there was a failure with intltools which it turned out I hadn't properly installed. The only question I have about Listen 0.5 now is where do I find python-libgpod? I've checked the repositories, been to the gpod sourcefoge page, even Googled it. The only thing I've found is references on messages boards asking where the heck python-libgpod is. Anyone know?
Thanks.

---

### Post by Kuoi on 2007-03-09
I have 1 problem now.

Listen doesn't start in the right resolution.

I always have to rightclick on the above tab , and then select "Maximilise" (I use the Dutch Ubuntu , sorry if it's not right ) , or i have to 'grab' Listen , and put it to the left to see the Minimalise , maximilse  and off (X) buttons.

I have selected "full modus" (or what it's called in English ) .

Can I maybe change the starter command to start it "maximilsed" ?

Kuoi

---

### Post by Forlong on 2007-03-09
You could use [devilspie](https://help.ubuntu.com/community/Devilspie) for that.

---

### Post by cor2y on 2007-03-10
Anyone have luck with a fix for the segmentation fault error?
I did look at the wiki before and tried that fix as well as the one listed in the INSTALL file that came with the source code.
No go with any of those solutions.

---

### Post by Kuoi on 2007-03-10
> **Kuoi said:**
> I have 1 problem now.

Listen doesn't start in the right resolution.

I always have to rightclick on the above tab , and then select "Maximilise" (I use the Dutch Ubuntu , sorry if it's not right ) , or i have to 'grab' Listen , and put it to the left to see the Minimalise , maximilse  and off (X) buttons.

I have selected "full modus" (or what it's called in English ) .

Can I maybe change the starter command to start it "maximilsed" ?

Kuoi

I think the solution will be that I edit the config file in my /home/.Listen folder.

Can somebody that uses the "full mode" tell me their settings under "Window"
Mine is :

> [window]
pos_organizer = 183
state = normal
pos_cur_playlist = 500
height = 689
width = 1264
pos_global_pane = 311
y = 49
x = 5
view = 2


I think I must edit these settings , but when I've tried for example changing "width = 1264" in "width = 1024" , it doesn't change anything.

Or is there an other setting that I hae to change ?

Thanks , Kuoi

---

### Post by Kuoi on 2007-03-10
It seems I have to change "state = normal" to "state = maximized" ... but ...

It works only the first time I start up Listen , when I close it , and start Listen again , the setting is changed again to normal !
Help !

Kuoi

---

### Post by Kuoi on 2007-03-10
Edited

---

### Post by Kuoi on 2007-03-13
> **Forlong said:**
> You could use [devilspie](https://help.ubuntu.com/community/Devilspie) for that.

Thank you very much for this tip !

I had a problem with the session manager who didn't let me add any program , and in my threath about that [http://www.ubuntuforums.org/showthread.php?t=382476]("http://www.ubuntuforums.org/showthread.php?t=382476")

I've got the solution for this.

After that I've made a "devilspie.ds" file in the .devilspie folder wich contains the following rule
> (if (and (contains (application_name) "Listen") ) (maximize)) and now Listen starts maximized.

Thank you all for the tips.

Kuoi

---

### Post by boast on 2007-03-13
Seems no player but amarok can play music from my media server. 
I don't want to mount it either, thats silly.

---

### Post by xpan on 2007-03-22
hi,

I am trying to compile Listen 0.5 but I get this:

> 
Checking for DBUS: found
Checking for python-libgpod: not found
Listen recommends python-gpod ([http://www.gtkpod.org](http://www.gtkpod.org))
Checking for python-musicbrainz2: not found
, but recommanded
Checking for python-tunepimp > 0.5: not found
, but recommanded
Checking for libsexy: found
make -C mmkeys
make[1]: Entering directory `/home/xpan/temp/listen-0.5/mmkeys'
cp build/lib*/mmkeys.so .
cp: cannot stat `build/lib*/mmkeys.so': No such file or directory
make[1]: *** [mmkeys.so] Error 1
make[1]: Leaving directory `/home/xpan/temp/listen-0.5/mmkeys'
make: *** [mmkeys.so] Error 2
root@xpan-laptop:/home/xpan/temp/listen-0.5# 


and when I do this: 

root@xpan-laptop:/home/xpan/temp/listen-0.5/mmkeys# ./setup.py build

I get this:

> 
running build
running build_ext
building 'mmkeys' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeyspy.c -o build/temp.linux-i686-2.4/mmkeyspy.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
mmkeyspy.c:3:20: error: Python.h: No such file or directory
In file included from mmkeys.override:6:
/usr/include/pygtk-2.0/pygobject.h:20: error: expected specifier-qualifier-list before &#8216;PyObject&#8217;
/usr/include/pygtk-2.0/pygobject.h:27: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:38: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:48: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:60: error: expected specifier-qualifier-list before &#8216;PyObject_HEAD&#8217;
/usr/include/pygtk-2.0/pygobject.h:67: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyTypeObject&#8217;
/usr/include/pygtk-2.0/pygobject.h:68: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/usr/include/pygtk-2.0/pygobject.h:76: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pygtk-2.0/pygobject.h:78: error: expected &#8216;;&#8217; before &#8216;void&#8217;
mmkeys.c:16: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
mmkeys.c:21: warning: data definition has no type or storage class
mmkeys.c:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PyTypeObject&#8217;
mmkeys.c:21: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;PyMmKeys_Type&#8217;
mmkeys.c:30: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
mmkeys.c:30: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyObject&#8217;
mmkeys.c: In function &#8216;_wrap_mmkeys_new&#8217;:
mmkeys.c:34: warning: implicit declaration of function &#8216;PyArg_ParseTupleAndKeywords&#8217;
mmkeys.c:34: error: &#8216;args&#8217; undeclared (first use in this function)
mmkeys.c:34: error: (Each undeclared identifier is reported only once
mmkeys.c:34: error: for each function it appears in.)
mmkeys.c:34: error: &#8216;kwargs&#8217; undeclared (first use in this function)
mmkeys.c:39: error: &#8216;struct _PyGObject_Functions&#8217; has no member named &#8216;pygobject_constructv&#8217;
mmkeys.c:40: error: &#8216;PyGObject&#8217; has no member named &#8216;obj&#8217;
mmkeys.c:41: warning: implicit declaration of function &#8216;PyErr_SetString&#8217;
mmkeys.c:42: error: &#8216;PyExc_RuntimeError&#8217; undeclared (first use in this function)
mmkeys.c: At top level:
mmkeys.c:49: warning: data definition has no type or storage class
mmkeys.c:49: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PyTypeObject&#8217;
mmkeys.c:49: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;PyMmKeys_Type&#8217;
mmkeys.c:98: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;mmkeys_functions&#8217;
mmkeys.c:104: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
error: command 'gcc' failed with exit status 1
root@xpan-laptop:/home/xpan/temp/listen-0.5/mmkeys# 


---

### Post by cor2y on 2007-03-23
if you are compiling from source you will need those dependencies you were warned about in configuring.
See README and INSTALL (they are text files) in the source folder you extracted from the gz/tar archive Which means compiling each and everyone which has dependencies of their own if you don't have the patience to handle compiling those i think there are links to debs in this thread use those instead.

---

### Post by xpan on 2007-03-23
thanks, but the problem is with mmkeys. I tried to compile this but w/o success. You can see it from the second "quote"...

> 
running build
running build_ext
building 'mmkeys' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeyspy.c -o build/temp.linux-i686-2.4/mmkeyspy.o -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0
mmkeyspy.c:3:20: error: Python.h: No such file or directory
In file included from mmkeys.override:6:


---

### Post by cor2y on 2007-03-24
do you have the correct/latest PyGTK and Python development libraries?

It seems to be looking for the libraries and not finding them.

You might try looking for them via synaptic or compiling from source.

---

### Post by cor2y on 2007-03-24
do you have the correct/latest PyGTK and Python development libraries?

It seems to be looking for the libraries and not finding them.

You might try looking for them via synaptic or compiling from source.

---

### Post by hapablap on 2007-03-28
Does anyone know why listen 0.5 takes up more resources/mem. Everytime it loads i see my cpu activity/temp increase and when i view system monitor i see /usr/lib/listen take up to 50mb. Is this just me because I really like what listen has to offer.

---

### Post by Nonno Bassotto on 2007-03-29
I'm using the 0.5 beta and the average RAM use is around 70MB, so I guess it actually improved.

---

### Post by marcantonio on 2007-03-30
I just got Listen 0.5 compiled and running.  However, when I try to edit metadata on a file I get a popup telling that it can't write metadata for file.

On the console I get:

```
Tracback : 'unicode' object has no attribute '_writeData'
```

Anyone seen this before?

Marc

---

### Post by vificunero on 2007-04-01
Hi everythin is working but I can't import any mp3 files. Only ogg. Is someone else facing the same problem? Thank's.

---

### Post by Forlong on 2007-04-02
> **vificunero said:**
> Hi everythin is working but I can't import any mp3 files. Only ogg. Is someone else facing the same problem? Thank's.
Sounds like you haven't installed the codecs - see here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by vificunero on 2007-04-02
Thank's for your reply. Which is the right package I need? Anyway I can listen to mp3 files with beep-media-player.

---

### Post by Zillion on 2007-04-06
I made an asound.conf under etc

Does any know how I can let Listen play on my 6.1 speaker set?

thanks

---

### Post by finisdiem on 2007-04-14
I was able to install it easily with the dependencies by downloading it from source forge []("http://sourceforge.net/project/showfiles.php?group_id=161415")

---

### Post by vificunero on 2007-04-15
> **vificunero said:**
> Thank's for your reply. Which is the right package I need? Anyway I can listen to mp3 files with beep-media-player.

is gstreamer-plugins-ugly (which is a suggested package for listen dependencies)

---

### Post by Sale on 2007-04-28
I have downloaded [this]("http://ubuntuforums.org/showpost.php?p=2258040&postcount=53") *.deb file and I get an "dependency not satisfiable: libatk1.0-0" error.
What can I do about that? Is there a repository that provides Listen? I'm trying to install it on Dapper.

---

### Post by czmiel on 2007-05-02
I've just packaged the newest "Listen-svn + fixes" for Feisty using checkinstall. Enjoy :}

Dependencies looks horrible but almost everything is installed by default.

```
sudo apt-get install libatk1.0-0 libc6 libcairo2 libfontconfig1 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxrandr2 libxrender1 python-central gstreamer0.10-alsa python-gtk2 python-pyogg  python-pymad python-dbus python-gnome2 python-gnome2-extras gstreamer0.10-plugins-good python-gst0.10  gstreamer0.10-plugins-base python-pysqlite2 python-pyvorbis python-mutagen python-tunepimp libtunepimp5 libtunepimp5-mp3 libsexy2 libsexymm2
```

Package is in attachment.

Regards

---

### Post by DomZ on 2007-05-12
Any chance you can make a new .deb file inicluding this patch to make multimedia keys on laptops work:

[http://www.listen-project.org/ticket/606#comment:4](http://www.listen-project.org/ticket/606#comment:4)

---

### Post by dennus on 2007-07-03
Something I don't understand.

I start a song, for instance NICKELBACK - FAR WAY.
It plays nicely, then I click the LYRICS TAB. It fetches to information from lyrc.com.ar.

I presume it ha found the lyrics, because the FONT is larger now. Except, the only thing I see is NICKELBACK-FAR AWAY -. Nothing more. When I visit lyrc.com.ar the lyrics are right there. So, it finds them but it won't show them in Listen Music Player.  Anyone?

EDIT
Another song, this time Linkin Park, works well. Except the lyrics are crappy. Don't know who made them?!?!?  Guess the Nickelback problem was because the name is not 100% the same as the one on the server?   Is there a way to change servers?  leoslyrics doesn't work, so I guess I'm stuck with lyrc.com.ar???

Another thing, some lyrics look like this.... "No, you don’t know what it’s like,"   I've tried to change the font, but can not really find one that works.

---

### Post by miguelitu on 2007-07-25
yeah, i get just the name of the track with the lyrc.com.ar.

the leoslyric works for me, but still i'll be glad with there's a way to add others servers.

anyone?

thanks o/

---

### Post by martin_prince on 2007-08-08
> **czmiel said:**
> Package is in attachment.

Regards

Thanks so much, that worked for me with no fuss!

---

### Post by denisesballs on 2007-08-08
> **czmiel said:**
> I've just packaged the newest "Listen-svn + fixes" for Feisty using checkinstall. Enjoy :}

Dependencies looks horrible but almost everything is installed by default.

```
sudo apt-get install libatk1.0-0 libc6 libcairo2 libfontconfig1 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxrandr2 libxrender1 python-central gstreamer0.10-alsa python-gtk2 python-pyogg  python-pymad python-dbus python-gnome2 python-gnome2-extras gstreamer0.10-plugins-good python-gst0.10  gstreamer0.10-plugins-base python-pysqlite2 python-pyvorbis python-mutagen python-tunepimp libtunepimp5 libtunepimp5-mp3 libsexy2 libsexymm2
```

Package is in attachment.

Regards

This package did work, however I'm pretty disappointed to see the splash screen still doesn't work, and Listen still cannot read track numbers from .m4a files. I've e-mailed the developer about this months ago and never heard back. I love Listen, but this makes it pretty much unusable for me.

---

### Post by cmlewin on 2007-09-24
mmuuuuuch props and thanks to czmiel for that package... only way i got this awesome music player working on my comp

---

### Post by Neo4 on 2007-11-14
I have installed the last version of listen by the lastfm repos but i'm having a problem...
i've choose where are my music files but when it searches for them it only find some!
and if i try to add file by file the files that werent add on the fst time appear gray and i can't choose them!
but if I only open then it opens good on listen, just don't add them to the library!

all my files are .mp3 i don't understand what is wrong!

---

### Post by Eestlane on 2007-12-01
It finds only ogg or other free types.
I have the same problem, I would like to have mp3 support as I have mp3 support for playing.

---

### Post by Nonno Bassotto on 2009-03-15
Listen 0.6 RC1 is [out]("http://www.listen-project.org/downloads") now!! :D

Any chance someone will package it?

---

### Post by denisesballs on 2009-03-15
> **Nonno Bassotto said:**
> Listen 0.6 RC1 is [out]("http://www.listen-project.org/downloads") now!! :D

Any chance someone will package it?

I just installed installing on Jaunty and am getting a seg fault.

---

### Post by Nonno Bassotto on 2009-03-25
Ok, now there is RC2. Maybe you can try again.

---

### Post by Eestlane on 2009-04-01
Just wasted an hour trying to install it from the source, searching for the dependencies for building etc. I failed.

---


---
title: "jabber client &quot;jabbin&quot; with voice support ..."
date: 2006-08-15
forum: The Cafe
---

### Post by samir85 on 2006-08-15
Hey,

did you guys already heard of the open source jabber client jabbin ([www.jabbin.com](www.jabbin.com)) ?

The new version (2.0 beta) has libjingle included and so you can voice chat with GTalk, OpenWengo and other voice compatible jabber clients.
Now they also released debian packages for the client. Unfortunately, I couldn't try it out so far, because I'm still at work.

Maybe you can post your experience with this client !


regards Samir

---

### Post by sapo on 2006-08-15
I installed the Debian Package here with the --force option, it worked, but i have no sound.. and i get this package as broken, so i ll try to download the  tarball

---

### Post by samir85 on 2006-08-15
I think you need to install the libspeex packages in order to have sound.

---

### Post by reacocard on 2006-08-15
same result with the .deb file here. broken package. downloading the source tarball now.

BTW, tapioca works with gtalk voip. no idea if it's interoperable with wengo/jabber voip though.

EDIT: can't get source to compile. first dependency problems (needed libqt3-mt-dev), then make errors, which i have no idea what's causing.

---

### Post by kendals on 2006-09-20
Jabbin installs, but I get this error all the time, and nobody on gtalk can hear me :(

```
:~$ jabbin
/home/kendal/.psi
/usr/share/jabbin
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Any ideas? (Same goes for PSI)

---

### Post by skymt on 2006-09-20
I love Jabber, I love VoIP... Perfect!

I'll check it out when I get home.

---

### Post by kendals on 2006-09-20
Prepare to be disappointed when you get the error I have :(

---

### Post by henriquemaia on 2006-09-20
> **kendals said:**
> Prepare to be disappointed when you get the error I have :(

Have you compiled it? If yes, how? (I get an error upon making).

---

### Post by kendals on 2006-09-20
What error?

And yes, I compiled it. Make sure you have all the dependencies!

---

### Post by henriquemaia on 2006-09-20
> **kendals said:**
> What error?

And yes, I compiled it. Make sure you have all the dependencies!

Here's the output:

```
rtprandom.cpp: In constructor ‘RTPRandom::RTPRandom()’:
rtprandom.cpp:56: error: cast from ‘RTPRandom*’ to ‘u_int32_t’ loses precision
make[2]: *** [.obj/rtprandom.o] Error 1
make[2]: Leaving directory `/home/henriquemaia/Desktop/jabbin-2.0beta/3party/jrtplib'
make[1]: *** [sub-jrtplib] Error 2
make[1]: Leaving directory `/home/henriquemaia/Desktop/jabbin-2.0beta/3party'
make: *** [sub-3party] Error 2

```

---

### Post by henriquemaia on 2006-09-21
Bump.

---

### Post by kendals on 2006-09-22
Try getting jrtplib from synaptics?

---

### Post by revertex on 2006-12-14
works out of the box for me.

---

### Post by PatrickMay16 on 2006-12-14
> **kendals said:**
> Jabbin installs, but I get this error all the time, and nobody on gtalk can hear me :(

```
:~$ jabbin
/home/kendal/.psi
/usr/share/jabbin
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Any ideas? (Same goes for PSI)
Dunno why nobody can hear you, but you're wondering with you get those X "BadDevice" errors, right? This is because by default in ubuntu, some stuff is put into the Xorg.conf to make wacom tablets work. Seems like you haven't got a wacom tablet, so it's complaining there that it can't find the wacom tablet. (two of them; one for the tablet and another for the stylus.) I know this, because I myself got these error messages, and they went when I removed the relevant parts from my Xorg.conf. Because, I have no wacom tablet.
I know this, because I have no wacom tablet.

---

### Post by vilto on 2007-01-31
> **kendals said:**
> Jabbin installs, but I get this error all the time, and nobody on gtalk can hear me :(

```
:~$ jabbin
/home/kendal/.psi
/usr/share/jabbin
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Any ideas? (Same goes for PSI)

getting exactly the same error any and can hear anything

---

### Post by jbrocker on 2007-02-18
> **kendals said:**
> Jabbin installs, but I get this error all the time, and nobody on gtalk can hear me :(

```
:~$ jabbin
/home/kendal/.psi
/usr/share/jabbin
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Any ideas? (Same goes for PSI)

Even i get the same msg.
i can connect to the gmail server...n chat wid all my contacts.....but during call we cant her each other.
can we change the input device in jabber?

---

### Post by jfif on 2007-03-08
No sound too.

Downloaded and installed [SIZE="3"][jabbin_2.0beta2-1baltix1_i386.deb]("https://sourceforge.net/project/showfiles.php?group_id=166861&package_id=201807&release_id=442045")[/SIZE]

And the default sound files supposed to be at [FONT="Courier New"]/usr/share/jabbin/sound/[/FONT]
are also missing.

______________________________
Ubuntu 6.10

---

### Post by carla on 2007-03-14
I'm using it with no problem. As a matter of fact, it worked when other Jabber clients balked on me.

[http://sourceforge.net/projects/jabbin/](http://sourceforge.net/projects/jabbin/)
> 
[LIST]
[*]                     Programming Language :                                                     [C++]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=165")
[*]                     Translations :                                                     [English]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=275"),                                                     [French]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=276"),                                                     [Spanish]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=277")
[*]                     User Interface :                                                     [Qt]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=479")[/LIST]

It does have an [active bug squashing team]("http://sourceforge.net/tracker/?atid=840642&group_id=166861&func=browse"), with 11 developers, so report all this, I'd suggest.

links:
[download Debian package]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=199405")
[download Ubuntu package]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=201807")
[download "Linux and Sources"]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=189813")
[download "Look and Feel"]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=217875")
[download Language Packs]("http://sourceforge.net/project/showfiles.php?group_id=166861&package_id=192929")

It's actually a derivative of the [Psi client]("http://sourceforge.net/projects/psi/"), if that helps anyone, information-wise.

Found a good site for emoticons: roster, emotions, system -- [http://jisp.netflint.net](http://jisp.netflint.net)

documentation snippets for Jabbin: [http://jabberstudio.org/projects/jabbin/docs](http://jabberstudio.org/projects/jabbin/docs)

Here's a screenshot from adept-manager, showing the prereqs and their versions, and the header of my roster (click for larger, on Flickr):
[[IMG]http://farm1.static.flickr.com/183/421504945_d5e97e1e06_m.jpg[/IMG]]("http://flickr.com/photos/hauntedpalace/421504945/")

Hope all of this helps!

---

### Post by jfif on 2007-03-16
Thanks Carla.  Here I got some clue: as was mentioned in the follow-ups of [this bug report]("http://sourceforge.net/tracker/index.php?func=detail&aid=1586559&group_id=166861&atid=840642"), the sound problem could be due to Jabbin's support of OSS. 

Here are the relavent follow-ups:

> Date: 2007-01-05 21:24
Sender: nobody
Logged In: NO 

I think the problem is that, unlike Psi's Jingle build, this latest build
of Jabbin only supports OSS, not ALSA. OSS is deprecated for good reason -
in the past I've had OSS applications lock up the soundcard for their
exclusive use (so nothing else will play), and sometimes found the
microphone unusable while sound is being output. I've currently had no luck
getting it to build against ALSA, assuming the capability is in there.

Repeat for emphasis - OSS is deprecated, only legacy software has an
excuse to be using it.


> Date: 2007-01-05 21:31
Sender: nobody
Logged In: NO 

Followup to the last message re: OSS/ALSA. It works fine for me when run
under aoss ("aoss jabbin"), which redirects OSS output from an application
to ALSA. aoss is found in the alsa-oss package on Debian and Ubuntu.

---

### Post by jfif on 2007-03-18
Tried **aoss**, but still now way. 

Tested between an Ubuntu(6.10) Desktop and an XP notebook.

Jabbin was launched from command line using [FONT="Courier New"]aoss jabbin &[/FONT].

Jabbin in Ubuntu and Google Talk in XP could chat with each other and receive voice call request from the other side. However, there was no voice at all. The "signal strength" indicator of GT remained blank (no signal), so did its mic and speaker level indicator.

So, let's just wait.

---

### Post by albuquerque on 2007-06-24
I too got the same errors.. Any one got a solution?

My machine is an AMD Turion 64x2. Acer Aspire.

Has anyone compiled or pakaged the jibbin for AMD64 arch??

---

### Post by GV1pJTHl on 2007-07-12
> **PatrickMay16 said:**
> This is because by default in ubuntu, some stuff is put into the Xorg.conf to make wacom tablets work.
Commented out the entries in the /etc/X11/xorg.conf file and solved those errors, now if I could get voice working correctly.

Thanks.

---

### Post by boklm on 2007-09-10
> **albuquerque said:**
> I too got the same errors.. Any one got a solution?

My machine is an AMD Turion 64x2. Acer Aspire.

Has anyone compiled or pakaged the jibbin for AMD64 arch??

Here's a small patch that fix the build:
[http://svn.mandriva.com/cgi-bin/viewvc.cgi/packages/cooker/jabbin/current/SOURCES/jabbin-fix_x86_64_build.patch?revision=84148&view=markup](http://svn.mandriva.com/cgi-bin/viewvc.cgi/packages/cooker/jabbin/current/SOURCES/jabbin-fix_x86_64_build.patch?revision=84148&view=markup)

---

### Post by del_Brujo on 2007-10-07
My only problem with Jabbin is that I can't hear the sounds of the notifications. There is no /usr/share/jabbin/sound/ folder. Do anyone knows any way to fix this?

---

### Post by Flatline-kun on 2008-01-11
> **del_Brujo said:**
> My only problem with Jabbin is that I can't hear the sounds of the notifications. There is no /usr/share/jabbin/sound/ folder. Do anyone knows any way to fix this?

Just download the source ([http://easynews.dl.sourceforge.net/sourceforge/jabbin/jabbin-2.0beta2a.tar.bz2](http://easynews.dl.sourceforge.net/sourceforge/jabbin/jabbin-2.0beta2a.tar.bz2)) and extract the /jabbin-2.0beta2a/sound directory to /usr/share/jabbin/sound.

Flatline-kun

---

### Post by unikuser on 2008-02-13
Try compiled deb from [http://code.google.com/p/jabbin-svn-pack-kubuntu/](http://code.google.com/p/jabbin-svn-pack-kubuntu/) 
I tried and it is working for me. 

> sudo gdebi jabbin_2.0.1-20080208-4_i386.deb

---

### Post by www.rzr.online.fr on 2008-07-26
Is the VOIP's sound clear ?
Tests welcome on snapshot version:

[http://rzr.online.fr/q/jingle](http://rzr.online.fr/q/jingle)

Regards

---


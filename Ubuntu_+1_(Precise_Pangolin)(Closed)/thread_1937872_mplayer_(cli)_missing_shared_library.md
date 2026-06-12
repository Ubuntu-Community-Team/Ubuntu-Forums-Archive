---
title: "mplayer (cli) missing shared library"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xzero1 on 2012-03-08
When I start mplayer I get 

```
"mplayer: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory". It was working, probably an update a day or so ago killed it.
```

Anyone else have this issue?

---

### Post by mc4man on 2012-03-08
Not at all - where did you get your mplayer or mplayer2?

The current 12.04 repo builds use libjpeg.so.8 - 
> $ ldd /usr/bin/mplayer |grep libjpeg
	libjpeg.so.8 => /usr/lib/i386-linux-gnu/libjpeg.so.8 

If using a 12.04 repo package then maybe try purging & re-installing. 
If using some other build try installing the older version - libjpeg62

---

### Post by xzero1 on 2012-03-09
It seems there were 2 copies of mplayer installed. One is in /usr/local/bin and causes the error. I have no idea how it got there. Another was in /usr/bin which runs correctly. Ubuntu Software Center uninstalls the one in /usr/bin. USC or apt-get also removes the good one. How do I make sure I clean up the garbage that should not have been installed?

```
$ dpkg --list | grep mplayer
kdog@kdog-TA790GXB-A2:~$
$ find / -name 'mplayer' 2>/dev/null
/usr/local/bin/mplayer
/etc/bash_completion.d/mplayer
kdog@kdog-TA790GXB-A2:~$
```

---

### Post by cariboo on 2012-03-09
> **xzero1 said:**
> It seems there were 2 copies of mplayer installed. One is in /usr/local/bin and causes the error. I have no idea how it got there. Another was in /usr/bin which runs correctly. Ubuntu Software Center uninstalls the one in /usr/bin. USC or apt-get also removes the good one. How do I make sure I clean up the garbage that should not have been installed?

```
$ dpkg --list | grep mplayer
kdog@kdog-TA790GXB-A2:~$
$ find / -name 'mplayer' 2>/dev/null
/usr/local/bin/mplayer
/etc/bash_completion.d/mplayer
kdog@kdog-TA790GXB-A2:~$
```

You must have manually installed mplayer at some point, seeing as both /usr/bin and /usr/local/bin are in your $PATH, there is a conflict between the two. Simply delete the version in /usr/local/bin, and reinstall mplayer if you haven't already, your problem should be solved.

---

### Post by xzero1 on 2012-03-09
The problem is there is other crap that was installed. Is there a way I can be sure anything connected with that bad install is deleted or would that matter? There are probably other files related to this install that I cannot find so easily as with "find mplayer*". I am sure I can get it to work; this is a more general question.

```
find / -name 'mplayer*' 2>/dev/null
/usr/share/app-install/icons/mplayer.png
/usr/share/app-install/desktop/mplayer-gui:mplayer.desktop
/var/cache/apt/archives/mplayer_2%3a1.0~rc4.dfsg1+svn34540-1_amd64.deb
/var/lib/dpkg/info/mplayer.postrm
/var/lib/dpkg/info/mplayer.list
/etc/mplayer
/etc/mplayer/mplayer.conf
/etc/bash_completion.d/mplayer
```

---

### Post by cariboo on 2012-03-09
What you show listed there are the files created when you use one of the install methods to install mplayer. If you remove the version in /usr/local/bin, the other files installed shouldn't make any difference.

---

### Post by mc4man on 2012-03-09
If you built an mplayer, which seems likely, then only a couple of files are installed.
Take a look in /usr/local/* 
You may or may not have built mencoder, if so it would be in /usr/local/bin

Other than that there would probably be a man file, look in /usr/local/share/man/man1

Is so inclined to build a current source of mplayer you may want to use a method like this - 
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

(there currently is an issue with live555, info  on post(s) 340+

---

### Post by xzero1 on 2012-03-09
I did get mplayer running. I can assure you I did not build mplayer. I only installed 12.04 beta a few days ago. I have only installed a handfull of programs since. Whats strange is that ffmpeg gives me a similar error. I am fairly sure I did not attempt to run this as I would have noticed an error. Could it be possible an update or bug is causing these issues?

```
kdog@kdog-TA790GXB-A2:~$ ffmpeg
ffmpeg: error while loading shared libraries: libfaac.so.0: cannot open shared object file: No such file or directory
```


Update:
Ok, this might make more sense now, I did compile mplayer and ffmpeg on Lucid. Does building them yourself place them in /usr/local/bin? I did copy over some of those files.

---

### Post by mc4man on 2012-03-09
> **xzero1 said:**
> 

Update:
Ok, this might make more sense now, I did compile mplayer and ffmpeg on Lucid. Does building them yourself place them in /usr/local/bin? I did copy over some of those files.
Yes, the default for most sources is to install to /usr/local

If I were you I'd go thru /usr/local/* & remove all that you copied over, **none** of it is any good on 12.04
The ffmpeg source would have installed to several places in /usr/local/, -  bin, include, maybe lib, ect.

---

### Post by xzero1 on 2012-03-09
I copied this because I had scripts I needed without realizing there were other executable files there. Thanks to all for your help.

---

### Post by andrew.46 on 2012-03-10
> **mc4man said:**
> (there currently is an issue with live555, info  on post(s) 340+

I am not running Precise but I have great hopes that the repository *liblivemedia-dev* will keep both vlc-git and the svn MPlayer happy. Running 2011.12.23 for both here atm with no trouble so hopefully the packaged version will be enough....

---

### Post by mc4man on 2012-03-10
> **andrew.46 said:**
> I am not running Precise but I have great hopes that the repository *liblivemedia-dev* will keep both vlc-git and the svn MPlayer happy. Running 2011.12.23 for both here atm with no trouble so hopefully the packaged version will be enough....
I meant to ck. yesterday if vlc was as yet ok with an unpatched live555, forgot. (The repo versions of vlc (2.0.1), mplayer, mplayer2 all build dep on liblivemedia-dev so maybe it's ok now?

---

### Post by andrew.46 on 2012-03-10
> **mc4man said:**
> (The repo versions of vlc (2.0.1), mplayer, mplayer2 all build dep on liblivemedia-dev so maybe it's ok now?

Sounds hopeful :).

---


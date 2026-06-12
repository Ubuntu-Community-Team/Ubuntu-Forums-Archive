---
title: "Firefox 1.5"
date: 2005-11-29
forum: Ubuntu Backports
---

### Post by fordp on 2005-11-29
I would like to be the first  to Request Fire Ferret 1.5.

It is being released as we speak.

I know we will have to wait for it to get into testing first.

Cheers.

---

### Post by atoponce on 2005-11-29
[quote=fordp]I would like to be the first  to Request Fire Ferret 1.5.

It is being released as we speak.

I know we will have to wait for it to get into testing first.

Cheers.[/quote]

Fire Ferret 1.5?  What's that?  Do you mean to say Firefox 1.5 final will be released today?  I am running 1.5 RC3, and I have not yet been notified that there are any updates.  What are you talking about?

---

### Post by jrib on 2005-11-29
read the sticky [http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595) ;o

---

### Post by fordp on 2005-11-29
Fire Feret is its Nick Name at :-

[http://www.theinquirer.net/](http://www.theinquirer.net/)

Yes I read the post in requests.

Shame. I will have it on my work Windoze machine today !

---

### Post by veloct on 2005-11-29
[QUOTE=fordp]Fire Feret is its Nick Name at :-

[http://www.theinquirer.net/](http://www.theinquirer.net/)

Yes I read the post in requests.

Shame. I will have it on my work Windoze machine today ![/QUOTE]

And?  You can have it today for linux too.  Just install it :)

---

### Post by ad noiseam on 2005-11-29
[QUOTE=fordp]Fire Ferret 1.5.[/QUOTE]

Damn, is Mozilla snatching Ubuntu coding procedure? What's next? The Thunder Turtle?

---

### Post by atoponce on 2005-11-29
[QUOTE=ad noiseam]Damn, is Mozilla snatching Ubuntu coding procedure? What's next? The Thunder Turtle?[/QUOTE]

Thunder Turtle!  I like it!  Bwa ha ha ha!!  (Laughing so hard, I'm almost crying!):D

---

### Post by vik4 on 2005-11-29
[QUOTE=atoponce]Fire Ferret 1.5?  What's that?  Do you mean to say Firefox 1.5 final will be released today?  I am running 1.5 RC3, and I have not yet been notified that there are any updates.  What are you talking about?[/QUOTE]

1.5RC3 is the same as 1.5Final. The release candidate was released.

---

### Post by atoponce on 2005-11-30
[quote=vik4]1.5RC3 is the same as 1.5Final. The release candidate was released.[/quote]

Firefox 1.5 RC3 is not the same as 1.5 Final.  RC3 is called "Release Candidate 3", which means it is close to final, but not final.  Release candidates are extensions of beta testing.

---

### Post by Chippendale on 2005-11-30
^^ yup, that's true...what he said! ;)

---

### Post by 23meg on 2005-11-30
[quote=atoponce]Firefox 1.5 RC3 is not the same as 1.5 Final.  RC3 is called "Release Candidate 3", which means it is close to final, but not final.  Release candidates are extensions of beta testing.[/quote]But in the case of Firefox, the final has been identical to the latest RC.

---

### Post by makhand on 2005-11-30
[QUOTE=veloct]And?  You can have it today for linux too.  Just install it :)[/QUOTE]

I did that, and like it. except java wont work

---

### Post by jdong on 2005-11-30
[QUOTE=atoponce]Firefox 1.5 RC3 is not the same as 1.5 Final.  RC3 is called "Release Candidate 3", which means it is close to final, but not final.  Release candidates are extensions of beta testing.[/QUOTE]
1.5 RC3 is indeed identical to 1.5 final, as md5sum, diff -Naur both reveal.

Release Candidates are exactly what they sound like. Release Candidates. That is, a package designated as THE final version, if nothing bad gets discovered. For example, when RC1 was released, if there were no major bugs reported, that would've been rebranded as final.


Remember that under Ubuntu, Firefox is not just a browser. It's a **system library** (Gecko) that provides HTML rendering capabilities for many many other programs. Run **apt-cache rdepends firefox && apt-cache rdepends mozilla-firefox** to get an idea of how many packages rest on Firefox's rendering abilities. Changing firefox versions is a major operation.

---

### Post by fordp on 2005-11-30
I think 23meg was saying that the software was the same and only the number changed.

When you change the version number it will change the md5sum but not the software!

I should know I am a software engineer ;)

---

### Post by ben.s on 2005-11-30
[QUOTE=atoponce]Firefox 1.5 RC3 is not the same as 1.5 Final.  RC3 is called "Release Candidate 3", which means it is close to final, but not final.  Release candidates are extensions of beta testing.[/QUOTE]

The RC3 source is the same as the final source -- no changes were made (except presumably to the versioning strings).  So if you're running RC3, you're effectively running 1.5 final.

---

### Post by The Belgain on 2005-11-30
[QUOTE=fordp]I think 23meg was saying that the software was the same and only the number changed.

When you change the version number it will change the md5sum but not the software!

I should know I am a software engineer ;)[/QUOTE]

Yeah I'd have thought so too, but apparently the version number has always been "1.5" even in the RCs, and so there was no version number to change (hence the identical MD5 hash) when releasing the final.

---

### Post by ossi on 2005-12-01
Does anybody here know how to get the video-plugin work for Firefox 1.5??

---

### Post by pertti on 2005-12-01
Read this howto: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion"). It worked for me :D.

---

### Post by dizzy1234 on 2005-12-01
There's a [ferret plugin](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Humor&numpg=10&id=31) that randomises your browsers name to things like firepanda, just to enliven your browsing experience. Not sure if it works with 1.5 though.

---

### Post by haocheng on 2005-12-02
[QUOTE=jdong]
Remember that under Ubuntu, Firefox is not just a browser. It's a **system library** (Gecko) that provides HTML rendering capabilities for many many other programs. [/QUOTE]

Is this the reason why Firefox is so slow on Ubuntu???
Every time when I try to load a page in Firefox, 
I found that the cpu loading will increase up to 90-100% for a second...

Hope Firefox 1.5 can solve this issue.  :???:

---

### Post by jdong on 2005-12-02
FF 1.0.7, for whatever reason, is heavily patched in Ubuntu. This has been resolved in 1.5.

---

### Post by haocheng on 2005-12-02
[QUOTE=jdong]FF 1.0.7, for whatever reason, is heavily patched in Ubuntu. This has been resolved in 1.5.[/QUOTE]

I'm really happy to hear that.
I started using Ubuntu since 4.10, 
and Firefox was not that slow before.

Hope FF 1.5 can enter backports soon ;)

---

### Post by magomago on 2005-12-03
here here!  I hope so as well.  I normally would just install it via the tar, but I updating all my programs via apt-get and if i can avoid it, i would prefer not to fragment that task

hope it gets done soon!

---


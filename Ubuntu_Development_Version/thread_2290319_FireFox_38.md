---
title: "FireFox 38"
date: 2015-08-11
forum: Ubuntu Development Version
---

### Post by v3.xx on 2015-08-11
Why is my Wily repository still on FF38?  And not 39.0.3?

---

### Post by Cavsfan on 2015-08-11
Same here:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy firefox
firefox:
  Installed: 38.0+build3-0ubuntu2
  Candidate: 38.0+build3-0ubuntu2
  Version table:
 *** 38.0+build3-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by dino99 on 2015-08-11
38 into main
40 into proposed (ubuntu here)

---

### Post by rrnbtter on 2015-08-11
Greetings,
{ firefox:
  Installed: 40.0+build4-0ubuntu1
  Candidate: 40.0+build4-0ubuntu1
  Version table:
 *** 40.0+build4-0ubuntu1 0
        500 [http://mirrors.liquidweb.com/ubuntu/](http://mirrors.liquidweb.com/ubuntu/) wily-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     38.0+build3-0ubuntu2 0
        500 [http://mirrors.liquidweb.com/ubuntu/](http://mirrors.liquidweb.com/ubuntu/) wily/main i386 Packages  }

Version 40 here. This has been discussed elsewhere in this section but you may be using a server that is incomplete.  I use the search function in the sources widget and try to get the best available source for my area. 
 Other than that I have switched to Opera anyway. Seems more sophisticated to me. And less intruding.

---

### Post by syntaxerror74 on 2015-08-12
rrnbtter & dino99 beat me to it -- in a nutshell:
*Must* activate **wily-proposed** repo branch to obtain **v40**. For some (to me incomprehensible) reason, wily-main is still at v38; plus, v39 is nowhere mentioned whatsoever. (Presumably the latter was simply skipped for some reason. (too unstable perhaps??))

---

### Post by v3.xx on 2015-08-12
Ok, got me considering this.

[https://ubuntu-mate.community/t/what-of-wily-proposed/2016](https://ubuntu-mate.community/t/what-of-wily-proposed/2016)

---

### Post by QDR06VV9 on 2015-08-12
I have had the Proposed enabled since Vivid.
With no difficulties at all.
Ah Come on in, the waters are fine!:D
Where is your sense of Adventure, this is testing.(Jokingly)
Regards

---

### Post by syntaxerror74 on 2015-08-12
LOL :D 
Well, I can nothing but recommend the 3.6.1-1 openbox update *(wily-proposed/universe), *as it's running perfectly fine. Wouldn't want to revert back to 3.5.2-8 *(wily/universe)* any more (too many quirks with lxappearance, its obconf plugin et. al.)

---

### Post by VMC on 2015-08-12
From the [*nightly builds*]("http://ftp.mozilla.org/pub/firefox/nightly/"), I installed 40 beta when it first came out and it has been updating itself on a regular basis. Now its a released version. I have now removed 38 completely. 
Then on another forum some suggested [Pale Moon]("http://www.palemoon.org/") as a Firefox alternative. It works very well. Fast. You might enjoy it as well.

Edit: If your interested in FF's developer edition, follow this [how to]("http://askubuntu.com/questions/548003/how-do-i-install-the-firefox-developer-edition")  . The developers edition update them self automatically. You just have to agree to the update.

---

### Post by v3.xx on 2015-08-13
> **runrickus said:**
> I have had the Proposed enabled since Vivid.
With no difficulties at all.
Ah Come on in, the waters are fine!:D
Where is your sense of Adventure, this is testing.(Jokingly)
Regards
Yep, it time to jump in :)

---

### Post by v3.xx on 2015-08-15
On a side note..

I expected this to pull in the 4.2 kernel, but it did not.  Guess that's not the way it works.

---

### Post by flocculant on 2015-08-15
> **v3.xx said:**
> On a side note..

I expected this to pull in the 4.2 kernel, but it did not.  Guess that's not the way it works.

Did you see that kernel in -proposed? 

I don't see it. You can only get what's actually in the repo's ;)

---

### Post by v3.xx on 2015-08-15
> You can only get what's actually in the repo's
Thanks for the laugh :)

---

### Post by launchpad-washuu on 2015-08-18
It seems that all currently supported releases EXCEPT Wily have been bumped to Firefox 40.
[http://www.omgubuntu.co.uk/2015/08/firefox-40-features-better-video-playback-linux](http://www.omgubuntu.co.uk/2015/08/firefox-40-features-better-video-playback-linux) (last paragraph).

---

### Post by PaulW2U on 2015-08-18
> **launchpad-washuu said:**
> It seems that all currently supported releases EXCEPT Wily have been bumped to Firefox 40.
For Wily it seems that Firefox 40 is still in the proposed repository. Presumably the developers have their reasons for not releasing the new version as a security update as per the supported releases. Something that I have seen before with previous Ubuntu releases.

Enable/update/install etc at your own risk of course. :)

---

### Post by launchpad-washuu on 2015-08-19
I enabled proposed a couple weeks ago. So far, no breakage (touch wood).

---


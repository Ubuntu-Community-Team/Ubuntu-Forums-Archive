---
title: "GnuPG impossible to use"
date: 2012-12-25
forum: Security
---

### Post by ka55o5 on 2012-12-25
Hi guys, please try not to jump on my case on this one, tnx. I understand that the topic has been covered countless times, but bear with me if you would pls; also I can't ask for clarification in a old post, because of the wrath of the moderators (making indexing of old threads practically useless and no different than something like the Yahoo! questions, but never mind that ;) :))

Ok, after generating and getting through the initial host of problems including [*Screwed up permissions on .gnupg folder - unable to fix with chown*]("http://ubuntuforums.org/showthread.php?t=1236084") (and many more different scenarios, where other stuff happens), I get:

```
~$ gpg --list-keys
/home/kgbme/.gnupg/pubring.gpg
------------------------------
pub   2048R/886DDD89 2009-09-04 [expires: 2016-08-28]
uid                  deb.torproject.org archive signing key
sub   2048R/219EC810 2009-09-04 [expires: 2014-08-29]

pub   4096R/6DA04611 2012-12-25
uid                  Vladimir Nostromov <kgbme@tormail.org>
sub   4096R/10F3D8C8 2012-12-25
```

Enigmail in Thunderbird says there's nothing and then after exporting my PUB key to file and importing it, it gives a cryptic message about the key 'not changed'. I am still left with nothing:

[[img]http://s7.postimage.org/mphjk8g7r/Screenshot_12252012_08_56_27_PM.jpg[/img]](http://postimage.org/image/mphjk8g7r/)

[[img]http://s14.postimage.org/eeozegjcd/Screenshot_12252012_08_53_06_PM.jpg[/img]](http://postimage.org/image/eeozegjcd/)

Then there is **[gpa]("http://ftp.ca.debian.org/debian/pool/main/g/gpa/?C=M;O=D")**. Installed and when loading with my user, it either crashes and/or displays *a couple* of usually different errors. It can be run as root, but then it will just use the different .gnupg folder.

Also, now there is:

```
~$ whereis gpg
gpg: /usr/bin/gpg /usr/bin/X11/gpg /usr/share/man/man1/gpg.1.gz
kgbme@kgbme-MS-7750:~$ whereis gpg2
gpg2: /usr/bin/gpg2 /usr/bin/X11/gpg2 /usr/share/man/man1/gpg2.1.gz
```

&& for sure I would prefer to use the 2.x version, but that's a whole different issue that's also impossible to manage between the OS and programs.

Just once, I was actually able to get everything to read and then a messenger program Psi+ couldn't manage with the keys, even though Enigmail was working (seems like it happened in a different life, if you get what I mean; wiped the system clean to try again (and again) to make sure whatever errors aren't due to something that had been done before - which I know shouldn't even matter, but anyway).

So for a relative Xubuntu noob like me, the situation is hopeless. I hope you can understand my angle - I am NOT posting for the hell of it - just trying to make *some* sense of the whole deal and learn how to manage this. So far, I'm just wasting days of time - at a time - and now I'm wasting yours. If there's any advice, or whatever you can think of, pls just post it, tnx. Err., that would be: constructive advice.

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
```

PS. I am totally clueless, as to what the procedure would be and what I should be doing to get any kind of GnuPG functionality as you can probably tell. It's not just this particular example posted in my thread, it's the whole deal. I went through *all* of the URLs available online, on the forums and on the Ubuntu site(s) a good number of times. Grasping @ straws here, thanks for reading and pls help unless you think I should just unplug my PC from the wall (which I wouldn't blame you).

**Edit**: If I use Enigmail to generate the keypair, the OS can't see it and vice-versa (Enigmail detects gpg and using gpg-agent for passphrases from options) . I suppose they are kept separate and I should just forget about it and use Enigmail for mail and gpg from terminal for whatever.. but it's just not making (much) sense to me at all. :f

PPS. Never mind, lock it, delete it pls... I'll have to figure this out, tnx.

---

### Post by mike acker on 2012-12-26
you probably have a pointer set wrong in there someplace

check with the [email]enigmail-users@enigmail.net[/email]

---

### Post by wdx on 2013-03-02
> It's not just this particular example posted in my thread, it's the whole deal.
...lot's of problems noted. assume this is standard install of xubuntu, thunderbird, gpg (version 1 and 2), and enigmail. and the problem to fix is enigmail. if you've moved conf

you indicate you've both gpg version 1 and 2 installed; and gpa. gpa (I think) default install is gpg  version 2.

gpg --keys and I assume gpa indicate keys and key rings in the default ~/.gnupg which would indicate your permission problem is fixed. make sure your enigmail is pointing at the desired  key rings.

[LIST]
[*]in thunderbird: openpgp>preferences>advanced check 'additional parameters' includes '--homedir ~/.gnupg/' . if it's blank, possibly your default enigmail path to keys is wrong. 
[/LIST]

enigmail errors like "bad passphrase" may occur if the gpg2 is installed and enigmail is configured for gpg (version 1). fix by pointing enigmail explicitly to version 2 (gpg2). 

[LIST]
[*]in thunderbird: openpgp>preferences>basic>files and directories, check 'override with' and enter /usr/bin/gpg2' or browse to '/usr/bin/' select 'gpg2' 
[/LIST]

---


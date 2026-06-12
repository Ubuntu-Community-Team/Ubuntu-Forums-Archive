---
title: "Need a howto: file a bug?"
date: 2005-07-28
forum: The Cafe
---

### Post by jimcooncat on 2005-07-28
I looked and couldn't find a nice 'HOWTO file a bug' in the forum. I was able to guess from a Google search that bugzilla.ubuntu.com was the place to go, then I had to look up the bad package (drupal) to find out that it was in Universe, and file the [bug](https://launchpad.ubuntu.com/malone/bugs/1599)  in the appropriate place.

It was confusing to me if this was the right place, though, because my problem may have been with the original Debian install. Should I have filed the bug with Ubuntu, Debian, or both? I don't need an answer for my particular bug, but how do you tell?

After filing the bug, I couldn't log back into bugzilla.ubuntu.com, but I was able to view my bug by logging into launchpad.ubuntu.com. Not very intuitive!

Also some writing tips for making an effective bug report would be nice.

What does this mean? Should a newbie touch this?
 > Indicate bug also exists:  +   Upstream    +   In Distro    +   In Distro ReleaseAnyone with the proper knowledge care to write a good howto?

---

### Post by az on 2005-07-28
[https://wiki.ubuntu.com/forum/community/BugReports](https://wiki.ubuntu.com/forum/community/BugReports)

Any user should be able to file a bug.  If you do not know what upstream is, or any other of the terms mean, that should not matter.

This is the way it shoudl work:

1.  You find a bug.
2.  You make sure that the bug is reproduceable and not caused by something like a hardware problem.
3.  Whether or not you find a solution is irrelevant.  If others suffer from this problem, it is time to go bug hunting.
4.  You look up the topic on bugzilla (soon to be Malone - Canonical is in the process of switching.  Breezy bugs will be filed on Malone.  Malone is part of Launchpad.)
5.  You search the developmental mailing list to see if the problem already got solved.  You may also use IRC.
6.  If you come up with nothing, you file your bug.  Make a clear description of the problem. 
7.  You wait for the bug to be assigned and in the event that more information is needed, you will be prompted (it will be tagged NEED INFO) to provide pertinent information.  Often this will help you find the problem.
8.  Once the bug is properly identified it will be addressed.  The bug report will be closed.

If it takes more than three days for the bug to be assigned, look into it.  there may have beed a clerical error or something like that.

---

### Post by jimcooncat on 2005-07-28
Thanks, azz. Your explanation is sufficient for me. Don't know the majority of noobs would get it though without more background, links, and walkthrough. 

Gentoo had (it's been a while since I visited) very slick links between documentation, bug reports, and package listings. I wish Ubuntu had them as nice as they did; though its getting better.

One could argue, of course, that Gentoo **needs** great document and feedback to exist, whereas most Ubuntu users are happy to just point and click in Synaptic.

---

### Post by Xian on 2005-07-30
Filing the bug is easy...determining if it _needs_ to be filed is the trick. :)

After doing your research you'd only need to issue a reportbug command.

It collects relevant data from your system, then you will get some prompts to answer. These are questions which provide additional information and then if you're running the session on the applicable PC with an internet connection it will submit the bug.

```
$ reportbug packagename
```
For example, here is the initial output to file a bug on aspell:
```
$ reportbug aspell
Using 'xxx@xxx.localdomain' as your from address.
Detected character set: UTF-8
Please change your locale if this is incorrect.

Getting status for aspell...
Will send report to Ubuntu (per request).
Looking up dependencies of aspell...

Please briefly describe your problem (you can elaborate in a moment; an empty
response will stop reportbug). This should be a concise summary of what is
wrong with the package, for example, "fails to send email" or "does not start
with -q option specified."
>
```

---

### Post by UbuWu on 2005-07-30
[QUOTE=Xian]
After doing your research you'd only need to issue a reportbug command.
[/QUOTE]

Mmm, I thought reportbug wasn't compatible with bugzilla, but I could be wrong...

---


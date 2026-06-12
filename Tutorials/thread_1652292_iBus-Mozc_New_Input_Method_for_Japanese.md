---
title: "iBus-Mozc: New Input Method for Japanese"
date: 2010-12-24
forum: Tutorials
---

### Post by areteichi on 2010-12-24
**[COLOR="Red"]*THIS PROCEDURE IS NOT STRICTLY NECESSARY ANYMORE, AS MOZC IS NOW PACKAGED IN UBUNTU BY DEFAULT. BUT USING THE REPOSITORIES PROVIDED HERE MAY STILL GIVE YOU THE UPDATED VERSIONS OF MOZC*[/COLOR]**

**BACKGROUND**
Google Japan [recently announced]("http://googlejapan.blogspot.com/2010/12/google.html") on its blog that the [Japanese Input Method]("http://www.google.com/intl/ja/ime/"), which has been in development since last December, is officially out of beta. There is actually an open-source version of this input method called **[Mozc]("http://code.google.com/p/mozc/")**, and I thought I would share with the community the procedure involved in setting it up since I didn't see any posts related to it.

**PROCEDURE**
The installation is essentially the same as ibus-anthy, but you first need to add two PPAs in order to retrieve the necessary packages.

The simplest method would be to add the repositories:
```
ppa:japanese-testers/mozc
ppa:japaneseteam/ppa
```
The first PPA ([Launchpad Link]("https://launchpad.net/~japanese-testers/+archive/mozc")) gives you Mozc packages while the second ([Launchpad Link]("https://launchpad.net/~japaneseteam/+archive/ppa")) gives you the updated packages for the Japanese environment. What you will then need to install are:
```
ibus  ibus-mozc  ibus-gtk
```

Once you restart, you should then see in the applet menu the keyboard icon. Under *Preferences* > *Input Method*, you can add *Japanese* > *Mozc* to enable the Mozc input method.

What's new and useful with Mozc is the auto-complete feature as well as inclusion of more 'web' or 'hip' languages that are not found in the previous input methods. I think this is definitely a great addition to the Japanese environment in Ubuntu.

**LINKS**
[Mozc Project - Google Code]("http://code.google.com/p/mozc/")
[Mozc PPA - Launchpad]("https://launchpad.net/~japanese-testers/+archive/mozc")
[Ubuntu Japanese Team PPA - Launchpad]("https://launchpad.net/~japaneseteam/+archive/ppa")

**OTHER RELEVANT LINKS**
(in Japanese) Google Japan's official announcement of the stable release of their version of the Japanese input method
[http://googlejapan.blogspot.com/2010/12/google.html]("http://googlejapan.blogspot.com/2010/12/google.html")
(in Japanese) Google Japan's Input Method Official Website (intro video available)
[http://www.google.com/intl/ja/ime/]("http://www.google.com/intl/ja/ime/")
There is a blog post about this in English:
[http://asiajin.com/blog/2010/12/22/google-japanese-input-drops-beta-tag-does-even-fortun-telling/](http://asiajin.com/blog/2010/12/22/google-japanese-input-drops-beta-tag-does-even-fortun-telling/)
And a comic in Japanese illustrating how Google Japan came to undertake their project (which again is the source of Mozc project).
[http://www.google.com/intl/ja/ime/comic/](http://www.google.com/intl/ja/ime/comic/)

---

### Post by abeowitz on 2011-02-15
Very cool.  Going to try this out!  :)

---

### Post by xtofu80 on 2012-05-01
Is there any user forum for Mozc?
So far, I have not found any site where one can ask questions about the software apart from the bug ticket system.

---

### Post by areteichi on 2012-05-01
As far as I know, the project page hosted on Google Code is their official website, and unfortunately there is no public forum or the like aside from the bug tracker.
[https://code.google.com/p/mozc/](https://code.google.com/p/mozc/)

You could perhaps consider emailing one of the developers if you're having some serious issues. You can find the email addresses on the website.

---


---
title: "DIaspora's Code Has Been Released!"
date: 2010-09-15
forum: The Cafe
---

### Post by Ubuntiac on 2010-09-15
git clone [http://github.com/diaspora/diaspora.git](http://github.com/diaspora/diaspora.git)

to get the goodness. :D



(Ok, you'll want a server to go with that, but hey...)

---

### Post by Dustin2128 on 2010-09-15
still working on getting it running...
come to think of it, it might be a good usage for those small computers that you stick on the wall... can anyone remember what they're called?

---

### Post by renkinjutsu on 2010-09-15
> **Dustin2128 said:**
> still working on getting it running...
come to think of it, it might be a good usage for those small computers that you stick on the wall... can anyone remember what they're called?

Those All-in-one computers? I think that's what you're saying

---

### Post by Dustin2128 on 2010-09-15
> **renkinjutsu said:**
> Those All-in-one computers? I think that's what you're saying
they're about the size of DC converter boxes... does anyone know what I'm talking about?

---

### Post by cariboo on 2010-09-15
Is nettop the word you're looking for?

---

### Post by ad_267 on 2010-09-15
You're thinking of a plug computer like the SheevaPlug. [http://en.wikipedia.org/wiki/Plug_computer](http://en.wikipedia.org/wiki/Plug_computer)

---

### Post by Dustin2128 on 2010-09-15
> **ad_267 said:**
> You're thinking of a plug computer like the SheevaPlug. [http://en.wikipedia.org/wiki/Plug_computer](http://en.wikipedia.org/wiki/Plug_computer)
that's it, thanks.

---

### Post by deinonychai on 2010-09-16
About that...

I'm trying to run the git command, but I can't seem to get anywhere with it... it seems to want to terminate on:

Initialized empty Git repository in ~/diaspora/diaspora/.git/
Permission denied (publickey).
fatal: The remote end hung up unexpectedly

I've never used git before, so I imagine I'm doing something wrong.  Any suggestions?

EDIT: I may not have been doing anything wrong... it just started to work with persistence.  Maybe the remote end really did hang up... huh.

---

### Post by wounded on 2010-09-16
git clone [http://github.com/diaspora/diaspora.git](http://github.com/diaspora/diaspora.git)

seemed to work for me. Ive only used git a little :3



though when i try and actually start diaspora it says "Could not find rake-0.8.7 in any of the sources" and googling hasnt helped me much.

---

### Post by deinonychai on 2010-09-16
> **wounded said:**
> git clone [http://github.com/diaspora/diaspora.git](http://github.com/diaspora/diaspora.git)

seemed to work for me. Ive only used git a little :3



though when i try and actually start diaspora it says "Could not find rake-0.8.7 in any of the sources" and googling hasnt helped me much.

It should be there, in Lucid, if the Universe repository is enabled.  They forgot to add that little tidbit in the installation instructions, I think.

---

### Post by madmaze on 2010-09-16
I have the same problem, i have rake installed, via apt-get, but i still get "Could not find rake-0.8.7 in any of the sources"

---

### Post by madmaze on 2010-09-16
derrr.. 

```

sudo gem install rake 
sudo gem install abstract
.
.
.
and the others

```

---

### Post by madmaze on 2010-09-16
nvm, in the diaspora root run
```

bundle check
sudo bundle install

```

but now i get the following error:
```
/usr/lib/ruby/gems/1.8/gems/activesupport-3.0.0/lib/active_support/dependencies.rb:239:in `require': no such file to load -- /home/madmaze/.bundler/ruby/1.8/em-http-request-6f66010cda90/lib/http11_client (LoadError)
```

---

### Post by madmaze on 2010-09-16
i fixed it, i played with a bunch of things, but my wining strides were:
```

bundle config
bundle install

```

---

### Post by Randofu on 2010-09-16
> **madmaze said:**
> nvm, in the diaspora root run
```

bundle check
sudo bundle install

```

but now i get the following error:
```
/usr/lib/ruby/gems/1.8/gems/activesupport-3.0.0/lib/active_support/dependencies.rb:239:in `require': no such file to load -- /home/madmaze/.bundler/ruby/1.8/em-http-request-6f66010cda90/lib/http11_client (LoadError)
```

I also had this problem. I think that if you do 

```

sudo bundle install

```

it installs the gems in a different place than where it tries to load them from.  I found that changing the owner of ~/.gem to the current user let me do:

```

bundle install

```

Specifically, it let me install the bundle without root access, and then I didn't have any more problems with the rest of the instructions.

I don't know much about how gems are managed, so I don't know if what I did is the right solution, but it worked for me.

---

### Post by mac.ryan on 2010-09-16
Thank you guys. Had similar problems, this thread solved all issues.

---

### Post by madmaze on 2010-09-16
> **mac.ryan said:**
> Thank you guys. Had similar problems, this thread solved all issues.

No problem, now i gotta figure out why I can create a user and be signed in, but if i log out it wont let me log in.

Also If you select multiple images and one of them is not supported, say ".bmp" it will reject all of them

---

### Post by Paqman on 2010-09-17
Quick caveat for people testing this: looks like [Diaspora's security currently leaves a lot to be desired]("http://www.theregister.co.uk/2010/09/16/diaspora_pre_alpha_landmines/"). Tread carefully!

---

### Post by Dustin2128 on 2010-09-17
so, any screenshots yet?

---

### Post by Ubuntiac on 2010-09-18
[IMG]http://www.joindiaspora.com/images/screenshots/album.png[/IMG]
[IMG]http://www.joindiaspora.com/images/screenshots/stream.png[/IMG]
[IMG]http://www.joindiaspora.com/images/screenshots/albums.png[/IMG]

*From the Diaspora blog

---

### Post by JDShu on 2010-09-19
So it turns out the pre-alpha code is really really bad. Also, it appears that its under an Open Core license, which is quite lame. Let's hope the license changes and that the power of open source can fix it up.

---

### Post by Ubuntiac on 2010-09-21
Erm... an open core license?

It's AGPLv3! You know... one of the most hard-core, FSF preferred, protects-people-even-when-the-software-isn't-being-distributed license there is?!

The files they didn't write are X11/MIT (ie BSD-like), but you can hardly blame them for that. Read it again... anything they create is released under the FSF's own AGPLv3. (Remember that unlike the LGPL, the AGPL is *more* hard-core than the standard GPL, ask the FSF). Better yet, don't believe me... read the COPYRIGHT file from the source code:

> Diaspora is copyright Diaspora Inc., 2010, and files herein are **licensed under the Affero General Public License version 3**, the text of which can be found in **GNU-AGPL-3.0**, unless otherwise noted.  Components of Diaspora, including Rails, JQuery, and Devise, are licensed under the MIT/X11 license.  Blueprint-CSS is licensed under a modified version of the MIT/X11 license.  All unmodified files from these and other sources retain their original copyright and license notices: see the relevant individual files.  Attribution information for Diaspora is contained in the AUTHORS file.

The only real beef is that they have a contributor agreement... just as Canonical do. If you're going to complain about this, then really you're on the wrong distro (especially since Diaspora's is for co-ownership).

You'll also notice that they only promised to open source the code on the 15'th (which they did). The media (spurred on by groups that would very much like this project to die leaving only FaceBook) were largely reporting that the 15'th would be "The Release", making sure that everyone got disappointed before the due date even arrived. The very first Alpha isn't even due until some time in October!

Let's hope they *don't* change to some other license (as there are almost none more free), and that people get up off their butts and *contribute* rather than spreading inaccurate FUD in places it might be mistaken for fact by real potential contributors.

---


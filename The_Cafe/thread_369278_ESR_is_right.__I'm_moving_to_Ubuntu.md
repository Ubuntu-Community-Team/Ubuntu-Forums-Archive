---
title: "ESR is right.  I'm moving to Ubuntu"
date: 2007-02-24
forum: The Cafe
---

### Post by elmerfud on 2007-02-24
I agree with ESR about Fedora.   I've been on the verge of moving away from Fedora for a while now.   Its the little things.  Updates get issued that aren't fully tested.  Sometimes updates are very slow in arriving, even though they are out in the Linux world for other distributions, etc. 

Bottom line: Fedora ISN'T a "just works" distribution.   Fedora is a bleeding edge distribution.   Ubuntu looks much more ready to use, rather than something that needs to be tweaked before it can be used. 

Its time for me to change.

---

### Post by elmerfud on 2007-02-24
Here is an example.  I'm a developer and I use kwrite a lot for editing various things.

Every time I run kwrite in konsole, I get this sort of crap on the command line.  I've complained about this for years.  And when I quit kwrite and type another command on the command line, kwrite spews stuff out while I am typing.  Nobody seems to care. 

$ kwrite
kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-krlux/ksycoca
kio (KTrader): query for KTextEditor/Plugin : returning 5 offers
kio (KDirWatch): Available methods: Stat, Inotify
kwrite: Inserted command:script-indent-c-char
kwrite: Inserted command:script-indent-c-newline
kwrite: Inserted command:jstest
kwrite: Inserted command:sort
kwrite: Inserted command:indent
kwrite: Inserted command:unindent
kwrite: Inserted command:cleanindent
kwrite: Inserted command:comment
kwrite: Inserted command:uncomment
kwrite: Inserted command:goto
kwrite: Inserted command:kill-line
kwrite: Inserted command:set-tab-width
kwrite: Inserted command:set-replace-tabs
kwrite: Inserted command:set-show-tabs
kwrite: Inserted command:set-remove-trailing-space
kwrite: Inserted command:set-indent-spaces
kwrite: Inserted command:set-indent-width
kwrite: Inserted command:set-mixed-indent
kwrite: Inserted command:set-indent-mode
kwrite: Inserted command:set-auto-indent
kwrite: Inserted command:set-line-numbers
kwrite: Inserted command:set-folding-markers
kwrite: Inserted command:set-icon-border
kwrite: Inserted command:set-wrap-cursor
kwrite: Inserted command:set-word-wrap
kwrite: Inserted command:set-word-wrap-column
kwrite: Inserted command:set-replace-tabs-save
kwrite: Inserted command:set-remove-trailing-space-save
kwrite: Inserted command:set-highlight
kwrite: Inserted command:run-myself
kwrite: Inserted command:set-show-indent
kwrite: Inserted command:s
kwrite: Inserted command:%s
kwrite: Inserted command:$s
kwrite: Inserted command:char
kwrite: Inserted command:date
kwrite: Inserted command:find
kwrite: Inserted command:replace
kwrite: Inserted command:ifind
Kate (Document): [int KateFileTypeManager::fileType(KateDocument*)]

---

### Post by shareMenaPeace on 2007-02-24
Hi, 
do you mean this happens with fedora or ubuntu/kde - kubuntu?

Cheers

---

### Post by tgalati4 on 2007-02-24
kwrite > /dev/null &

---

### Post by fuscia on 2007-02-24
wtf is ESR?

---

### Post by mips on 2007-02-24
> **fuscia said:**
> wtf is ESR?

Eric S Raymond
[http://en.wikipedia.org/wiki/Eric_S._Raymond](http://en.wikipedia.org/wiki/Eric_S._Raymond)
[http://www.catb.org/~esr/](http://www.catb.org/~esr/)
[http://www.linux.com/article.pl?sid=07/02/21/1340237](http://www.linux.com/article.pl?sid=07/02/21/1340237)

---

### Post by GeneralZod on 2007-02-24
> **tgalati4 said:**
> kwrite > /dev/null &

Or open up kdebugdialog -> Deselect All -> Apply.  This should remove the debug output from all KDE apps.

---

### Post by elmerfud on 2007-02-24
> Or open up kdebugdialog -> Deselect All -> Apply. This should remove the debug output from all KDE apps.

Bingo !  I never even though of using kdebugdialog !  It worked like a charm.  Finally, after all these years of watching kwrite spew jibberish !

---

### Post by GeneralZod on 2007-02-24
> **elmerfud said:**
> Bingo !  I never even though of using kdebugdialog !  It worked like a charm.  Finally, after all these years of watching kwrite spew jibberish !

There's probably a less sledge-hammer-ish way of doing this, but I don't know which particular components are responsible for the kwrite output :)

---

### Post by rko618 on 2007-02-24
Wow and I thought nothing good would come of that retarded post ESR made (which for some reason became internet news).  Though I do kind of feel bad for the guy.  As much of a media hog as he is, I think he intended only for Fedora devs to read that and not every Slashdot/Digg/reddit user.  Then again he loves attention.

---

### Post by saulgoode on 2007-02-24
> **rko618 said:**
> Wow and I thought nothing good would come of that retarded post ESR made (which for some reason became internet news).  Though I do kind of feel bad for the guy.  As much of a media hog as he is, I think he intended only for Fedora devs to read that and not every Slashdot/Digg/reddit user.  Then again he loves attention.

Your sympathy would probably be better directed toward more worthy targets. ESR (media hog as he is) was the one who publicized his decision.

**[linux.com wrote:]("http://enterprise.linux.com/enterprise/07/02/21/1340237.shtml?tid=23&tid=12")**
> The following letter was received from ESR, who has sent it to a number of Linux-related publications and mailing lists. It is presented verbatim, except for the addition of HTML code.

---

### Post by Bloodfen Razormaw on 2007-02-24
> Though I do kind of feel bad for the guy. As much of a media hog as he is, I think he intended only for Fedora devs to read that and not every Slashdot/Digg/reddit user.
Given his obsession with self promotion and desperate need to destroy the rights and freedoms enjoyed by anyone anywhere, I highly doubt that.  Oh, and also because of this little piece of that email...
> From: esr thyrsus com (Eric S. Raymond)
To: fedora-devel-list redhat com
**Cc: lwn lwn net, editors newsforge com, sjvn vna1 com, editors linuxtoday com**

---

### Post by macogw on 2007-02-24
I just tried Fedora (multiboot), and I'm with you guys. Bleh.  No wireless and yum is the slowest thing ever.  I'm staying on the Debian side of things.  No RH.

---

### Post by FyreBrand on 2007-02-24
> **macogw said:**
> I just tried Fedora (multiboot), and I'm with you guys. Bleh.  No wireless and** yum is the slowest thing ever**.  I'm staying on the Debian side of things.  No RH.Yum, among a few other irritating things, is what drove me to Ubuntu.  It was slow and would crash in the middle of updates.  This was on FC4 so I'm sure it's been improved a lot since then, but I shudder when I think about using it.

I was in a computer lab working on something and yum was being all jiggy.  The lab aid came over and handed me a Breezy CD and told me to give it a try.  He said I might like how apt-get and debs work.  That was an understatement.

---

### Post by mephisto786 on 2007-02-24
Careful, you're flaming a fellow ubuntan now!  :-P

But seriously, Ive gotten alot over the years from his views on OSS and his contributions, tho i tend to stay away from his more personal political views and tactics.  Same goes in many ways for RMS...... tp give a lil credit where credit is due, its often called GNU Linux for a reason.  But I;m not gonna be signng manifestos and weaing tinfoil hats.

And news is news......the recent release of the not too friendly exchangge between Torvalds and the folks at gnome probably wasnt meant initially for tabloid publication, but it ended up there.  

cheers

---

### Post by unbuntu on 2007-02-24
> **FyreBrand said:**
> I was in a computer lab working on something and yum was being all jiggy.  The lab aid came over and handed me a [COLOR="Red"]Breezy [/COLOR]CD and told me to give it a try.  He said I might like how apt-get and debs work.  That was an understatement.

Lol...seems someone over-ordered on shipit several years ago and desperately wanted to get rid some of those :D

---

### Post by elmerfud on 2007-02-28
Well, I've been running Ubuntu edgy for 2 days now.  I really like how everything works !  I've got a server running fc6 and I just did some maintenance on it using a USB thumb drive.  In ubuntu it shows up as a media device.  Not so in fc6 !

I didn't mind yum, it worked OK for me. 

I miss 'yum list' and 'rpm -q'  dpkg or apt-get probably have similar commands, I just haven't learned to use them yet. 

I am really liking ubuntu.  Its a way better finished product.   I can't wait for Feisty Fawn !

---


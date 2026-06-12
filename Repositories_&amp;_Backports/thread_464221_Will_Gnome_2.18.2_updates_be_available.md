---
title: "Will Gnome 2.18.2 updates be available?"
date: 2007-06-04
forum: Repositories &amp; Backports
---

### Post by madscientist on 2007-06-04
I posted this last week in the Installation & Upgrades forum but no response.  Anyone here know anything about Gnome 2.18.2 being made available for Feisty, either officially or through a 3rd party repo?  I really, really need a copy of the new Evolution in 2.18.2...

Is there a better place to ask?

----------

One thing I've been disappointed with Ubuntu in over the last couple of years is that they never seem to provide all of the update releases made by the Gnome project. For example, today Gnome 2.18.2 was released, but if history holds that version will never appear as a valid upgrade for Feisty. Instead, we'll have to wait until October for Gutsy and Gnome 2.20.

I'm forced to use Evolution Exchange and although it has made great strides, this application is still problematic and each update provides a number bug fixes and enhancements that I really need.

What's Ubuntu's position on this? Will we get Gnome updates packaged in a timely fashion for us by the official Ubuntu folks? If not, is there a reliable 3rd party repository that will provide these packages?

---

### Post by qamelian on 2007-06-04
You should see 2.18.2 at some point. As far as I recall, the point releases of Gnome do make it in, but you need to wait until the next Ubuntu release for the upgrade to the next major version (2.20).

---

### Post by madscientist on 2007-06-05
I hate to say it, but I see no evidence that any GNOME point releases ever are packaged officially.

I've looked at the Packages files for Breezy, Dapper, and Edgy and I don't see anything more than the 2.*.1 point releases in any of them.  I certainly don't ever recall getting those updates and I've used all of those releases.  Further, I *know* that there were point releases for each of those versions (2.12, the version in Breezy, for example, went up to 2.12.4).

So, I'm not optimistic and I'm wondering where I should go to find out the official Ubuntu position on this.

Thanks!

---

### Post by qamelian on 2007-06-05
> **madscientist said:**
> I hate to say it, but I see no evidence that any GNOME point releases ever are packaged officially.

I've looked at the Packages files for Breezy, Dapper, and Edgy and I don't see anything more than the 2.*.1 point releases in any of them.  I certainly don't ever recall getting those updates and I've used all of those releases.  Further, I *know* that there were point releases for each of those versions (2.12, the version in Breezy, for example, went up to 2.12.4).

So, I'm not optimistic and I'm wondering where I should go to find out the official Ubuntu position on this.

Thanks!

I gues we live in alternate universes then, because I only use the official repos and my update logs show upgrades to the point releases.

---

### Post by madscientist on 2007-06-05
Where do you find update logs on the system?  I have some but they only go back a short time.  I'd be interested to see that info.

Well, maybe I'm just missing some kind of repository then; that would be great!  But, I've pulled down the current Packages file for ALL the distros back to Breezy and included the backports, proposed, security, and updates as well and I see only new point release of Gnome in any of those.  I'm looking at the version of the gnome-about package since I assume any upgrade to a point release would have to include that package, to upgrade the version of Gnome you see when you look at the about box.

I mean sure, I've seen some Ubuntu updates (that is, 2.18.1-1 to 2.18.1-2 etc.) but those are just minor changes and packaging issues, typically.  I'm talking about Gnome point release updates (from 2.18.1 to 2.18.2)

Just in case someone sees what I'm doing wrong, here is how I checked:

```
# pull down all the latest Packages.bz2 files
$ for d in {breezy,dapper,edgy,feisty}{,-{backports,proposed,security,updates}}; do wget -O - http://archive.ubuntu.com/ubuntu/dists/$d/main/binary-i386/Packages.bz2 | bunzip2 > Packages-$d; done

# look for the gnome-about package and print the version of it
$ perl -n -e 'BEGIN { $found = 0; } if (/^Package: gnome-about/) { $found = 1; print $_; } if ($found && /^Version: /) { $found = 0; print $_; }' * 

# the result:
Package: gnome-about
Version: 2.12.1-0ubuntu1
Package: gnome-about
Version: 2.14.1.1-0ubuntu2
Package: gnome-about
Version: 2.14.3-0ubuntu1
Package: gnome-about
Version: 2.16.1-0ubuntu1
Package: gnome-about
Version: 1:2.18.1-0ubuntu1

```

So there is one distro (Dapper Drake) where a newer point release was packaged (2.14.3), I suppose because Dapper is under LTS, but other than that no new Gnome point release has ever been packaged as far as I can see.  And, I have to say, this is consistent with my recollection of the matter.

---

### Post by qamelian on 2007-06-06
> **madscientist said:**
> Where do you find update logs on the system?  I have some but they only go back a short time.  I'd be interested to see that info.

Well, maybe I'm just missing some kind of repository then; that would be great!  But, I've pulled down the current Packages file for ALL the distros back to Breezy and included the backports, proposed, security, and updates as well and I see only new point release of Gnome in any of those.  I'm looking at the version of the gnome-about package since I assume any upgrade to a point release would have to include that package, to upgrade the version of Gnome you see when you look at the about box.

I mean sure, I've seen some Ubuntu updates (that is, 2.18.1-1 to 2.18.1-2 etc.) but those are just minor changes and packaging issues, typically.  I'm talking about Gnome point release updates (from 2.18.1 to 2.18.2)

Just in case someone sees what I'm doing wrong, here is how I checked:

```
# pull down all the latest Packages.bz2 files
$ for d in {breezy,dapper,edgy,feisty}{,-{backports,proposed,security,updates}}; do wget -O - http://archive.ubuntu.com/ubuntu/dists/$d/main/binary-i386/Packages.bz2 | bunzip2 > Packages-$d; done

# look for the gnome-about package and print the version of it
$ perl -n -e 'BEGIN { $found = 0; } if (/^Package: gnome-about/) { $found = 1; print $_; } if ($found && /^Version: /) { $found = 0; print $_; }' * 

# the result:
Package: gnome-about
Version: 2.12.1-0ubuntu1
Package: gnome-about
Version: 2.14.1.1-0ubuntu2
Package: gnome-about
Version: 2.14.3-0ubuntu1
Package: gnome-about
Version: 2.16.1-0ubuntu1
Package: gnome-about
Version: 1:2.18.1-0ubuntu1

```So there is one distro (Dapper Drake) where a newer point release was packaged (2.14.3), I suppose because Dapper is under LTS, but other than that no new Gnome point release has ever been packaged as far as I can see.  And, I have to say, this is consistent with my recollection of the matter.
I was talking about my personal updates logs that I keep in a notebook at my desk. I log every package that gets installed or updated on my test system so I can track exactly what changes took place in case  start experiencing any problems. It's just a habit I got into working in IT. 

I was also talking about Gnome point releases rather than the fixes that Canonical pushes out. Your results above surprise me, but I won't discount the possibility that my memory is flawed on this situation. Considering I work 12 to 16 hours per day in It at my "day job" sometimes, I'm not always at my most coherent when I sit in front of my PC at home!:)

---

### Post by Kosimo on 2007-06-12
I had exactly the same question.

At the moment it seems to we'll never have Gnome 2.18.2 on feisty :(

---

### Post by madscientist on 2007-06-13
I filed a bug in Launchpad against the gnome-desktop package requesting a new version.  It's been closed with what I must assume is the "official" Ubuntu response.  See:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/120248](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/120248)

FYI!

---

### Post by Kosimo on 2007-06-13
> **madscientist said:**
> I filed a bug in Launchpad against the gnome-desktop package requesting a new version.  It's been closed with what I must assume is the "official" Ubuntu response.  See:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/120248](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/120248)

FYI!

It seems like...
We're not gonna see 2.18.2  on Feisty...
The last answer talks about how difficult is it to port the entire GNOME to another version... Maybe the entire community is busy developing Guisty...   Don't realy know the reason... But  maybe we need more developers!

Because Gnome 2.20 will probably born with lot of bugs... In part fixed by the first revision .1, but then... Stop fixing, and let's go to 2.22... so... we'll never have a very STABLE GUI...

Sorry guys but I'm angry....

---

### Post by Kosimo on 2007-06-13
By the way...
I reported a simple (bug) on gnome 
[http://bugzilla.gnome.org/show_bug.cgi?id=436236](http://bugzilla.gnome.org/show_bug.cgi?id=436236)

[I]Please describe the problem:
When Window List is located in a vertical position, the icon of each window is
not located in the center of the button. The icon appears touching the right
side. 

Steps to reproduce:
1. Setting the window list panel in a vertical position (left or right)
2. Opening some windows



Actual results:
The icon in each window button appears deviated to the right

Expected results:
The icon of each window in the middle of each button

Does this happen every time?
always[/I]

[IMG]http://kosimo.googlepages.com/windowlist.jpg[/IMG]


And I'm still waiting some answer since three months ago...

---

### Post by Kosimo on 2007-06-13
> **Kosimo said:**
> By the way...
I reported a simple (bug) on gnome 
[http://bugzilla.gnome.org/show_bug.cgi?id=436236](http://bugzilla.gnome.org/show_bug.cgi?id=436236)

[I]Please describe the problem:
When Window List is located in a vertical position, the icon of each window is
not located in the center of the button. The icon appears touching the right
side. 

Steps to reproduce:
1. Setting the window list panel in a vertical position (left or right)
2. Opening some windows



Actual results:
The icon in each window button appears deviated to the right

Expected results:
The icon of each window in the middle of each button

Does this happen every time?
always[/I]

[IMG]http://kosimo.googlepages.com/windowlist.jpg[/IMG]


And I'm still waiting some answer since three months ago...


Someone using gonme 2.19 can tell us if that problem is still there?

---


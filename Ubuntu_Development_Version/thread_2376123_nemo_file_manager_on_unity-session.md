---
title: "nemo file manager on unity-session"
date: 2017-10-30
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-30
Taking up a suggestion I contacted Khurshid about nemo on unity-session. So this will be a discussion  on pros and cons of using nemo on unity

> 
Ventrical 

Hi Khurshid,
 One of the members of U+1 team suggested file manager &#8216;nemo&#8217;.  Is  there a way we can fix bugs with nemo? Are you against this? Would it  beak any other work you are doing?
 Regards&#8230;




dev Khurshid

> 
Actually I was thinking using Nemo for 18.10 and  beyond. Nemo wouldn&#8217;t break anything and works fairly well with Unity  (though it has some cinnamon dependencies). Nautilus is deeply  integrated with Unity. With Nemo it is also possible to make it  integrated in similar way, but that means much more work for us. Since  18.04 will be LTS, I think we shouldn&#8217;t make this type drastic changes  for LTS cycle.
 Where has this discussion has started? I would like to see the the reasoning behind Nemo as default file manager in LTS.




Regards..

---

### Post by mc4man on 2017-10-30
Some of the hard work has been done already, there may be adjustments needed for 18.04
[https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)
currently no 17.10 build, no idea if they are going to advance.

So here just rebuilt the zesty source on 17.10 & it works ok though some issues remain

Atm I still see the best use case is using nautilus to handle desktop, nemo as default fm

---

### Post by jbicha on 2017-10-30
> **mc4man said:**
> 

Atm I still see the best use case is using nautilus to handle desktop, nemo as default fm

Why?

Note that nemo will seem like a regression to many users who have gotten used to newer versions of nautilus.

---

### Post by ventrical on 2017-10-31
> **jbicha said:**
> Why?

Note that nemo will seem like a regression to many users who have gotten used to newer versions of nautilus.

 I have a really hard time with this statement. If you compare nautilus from 10.10 -16.04 cycle we can say we have some meat and potatoes, at least on unity desktop. But after last 3 cycles nautilus has become a ghost of it's former self -> so of course to many users  it will seem that they are being socially  engineered to navigate otherwise.

---

### Post by jbicha on 2017-10-31
Could you be more specific?

Newer versions of nautilus have several interesting features. Here's some I remember
-  Batch Renaming (and if tracker is installed it can look up metadata  like artist name for a set of mp3s to use as fields for the rename)
- Integrated full text search (also requires tracker)
- Integration with the gvfs admin backend for folders that are only accessible by admin users
- Integrated file compression and decompression
- Integrated file progress dialogs (instead of being in a separate window)
- Headerbars

I  guess it's caja (the MATE fork of nautilus) in particular that really  feels dated to someone used to Unity or GNOME over the past 5 years.

---

### Post by ventrical on 2017-10-31
> **jbicha said:**
> Could you be more specific?

Newer versions of nautilus have several interesting features. Here's some I remember
-  Batch Renaming (and if tracker is installed it can look up metadata  like artist name for a set of mp3s to use as fields for the rename)
- Integrated full text search (also requires tracker)
- Integration with the gvfs admin backend for folders that are only accessible by admin users
- Integrated file compression and decompression
- Integrated file progress dialogs (instead of being in a separate window)
- Headerbars

I  guess it's caja (the MATE fork of nautilus) in particular that really  feels dated to someone used to Unity or GNOME over the past 5 years.

I have a MATE install that has titelbars with pulldowns. The recent (16.04-unity)has the mouse 'hover' highlighted the pull downs version of nautilus. Pull downs are gone in last three devs. More mouse clicks , less hover = increased chance of RSI. I understand computer concepts all to well. Efficiency /over floss and wish-list items- but nautilus has been a favorite ubuntu default even for gnome for the longest time.   

 During zesty cycle I think there was a discussion about extra mouse clicks on gnome and nautilus - I don't remember the bug but I think it got marked "won't fix".. so I'll ask openly .. are there more mouse clicks to nav through nautilus or less? Also ..as nautilus becomes leaner then it becomes more difficult to understand for potentially new users. 

Regards..

---

### Post by Chanath on 2017-10-31
The "new" Nautilus is the most featureless file manager ever to happen for Linux. I'd be happy to have Nemo taking over the desktop, if not just leave Nautilus to stay out of the way and use Nemo. The new Nautilus is practically useless for those, who are coming from File Explorer, which I think is the best GUI file manager out there. The best file manager for Linux is Dolphin. Nemo, at least reminds me of the "old" Nautilus, which is/was quite useful. Whenever the "new" Nautilus is getting newer, it loses some feature and some look, and one day it'd be just a blank rectangle.;)

---

### Post by mc4man on 2017-10-31
I'll mention, not including any unity specific issues -
No type-ahead find
No file name expansion on mouse hover
Other Locations in general - that just leave all this unused space in sidebar
Too many icons per row which leads to some file names being displayed weirdly, classic example
.
thunderbir
d
Hobbled root file browser (admin://
No empty space right click in list view
Reduced context menu compression options
No dual pane view
No compressed view
No default right click > create New Document
No up button
Options split into 2 separate areas plus some only in dconf
List view info shown in very light color
No advanced file permissions option
(nitpicking -
list view modified time registers in column from right to left - wierd
Bottom bar is more useful than floating bar which can sometimes obscure filename
No per folder icon size changes ( or not easily done.

There are some things nemo has but nautilus doesn't & some nice things nautilus has but nemo doesn't.
At least here if choosing between 3.14 & nemo I'd be somewhat torn.. and likely pick[ this]("https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1") nautilus.

(- ot. what does "Recency" possibly mean in nautilus > list view?

---

### Post by mc4man on 2017-10-31
As far as unity specific there are 2 egregious -
The off, on, off again xdg folder launcher icon quicklist items issue (no apparent solution
No global menus

---

### Post by jbicha on 2017-10-31
> **Chanath said:**
> Whenever the "new" Nautilus is getting newer, it loses some feature and some look, and one day it'd be just a blank rectangle.;)

Could we stop with this meme about GNOME? It's frustrating to those who spend their time making GNOME better.

I mean I provided a list of several features that Nautilus got since Ubuntu 16.04 LTS (except headerbars was already in 16.04).

---

### Post by Chanath on 2017-11-01
> **jbicha said:**
> Could we stop with this meme about GNOME? It's frustrating to those who spend their time making GNOME better.

I mean I provided a list of several features that Nautilus got since Ubuntu 16.04 LTS (except headerbars was already in 16.04).

We are not talking about Gnome, I believe. Nemo is a fork of Nautilus. Nemo is more like the old Nautilus with new features, easy for us to use. It is nice, when all the drop down menus are on the top caption bar, such as File, Edit, View, Bookmarks, Help etc, rather than go looking for them all over the app window. Dolphin is even better.

---


---
title: "Why is the Ubuntu documentation for depreciated versions not viewable?"
date: 2021-12-23
forum: The Cafe
---

### Post by acer342 on 2021-12-23
Seriously?

---

### Post by acer342 on 2021-12-23
Of course I have this: [URL="https://docstore.mik.ua/manuals/ubuntu/8.10/internet/C/index.html"]https://docstore.mik.ua/manuals/ubuntu/8.10/internet/C/index.html 
[/URL]and: [https://docs.huihoo.com/ubuntu/10.04/](https://docs.huihoo.com/ubuntu/10.04/)

---

### Post by guiverc on 2021-12-23
Any example maybe helpful.

Much detail is still there if you look (*often found in github or equivalent source directories (which can vary on the doc you're wanting) since the published versions are the supported releases*)

---

### Post by acer342 on 2021-12-23
Example of what?

Incidents where I couldn't access them?

---

### Post by guiverc on 2021-12-24
Example of some *deprecated* documentation you cannot find.

Your question was poorly worded being a single word "Seriously?"


The reasons vary; from the older documentation is wrong for *supported* releases thus getting rid of it is the best policy as it's misleading; to it being *deprecated* and thus replaced by newer documentation (*thus it was hidden away to prevent easy access & thus only those specifically looking for it will actually find it, not those looking for current documentation*).  Some yes will have been deleted.

For the deleted stuff; the source material used to generate the pages is often still available.

I was only recently tasked with *evaluating & cleanup* of *deprecated* documentation, and was encouraged to delete any that no longer applied.  In my case I removed almost nothing (*the pages I deleted had no useful detail as I saw it*), however for the pages I **moved**those who rely on search engines to find the pages will often end at *dead-ends* because the search engines are using pre-move URLs that are *outdated and thus going the wrong place*. If you search on the site where it is stored (*not relying on startpage, duckduckg*o*, google *etc) you'll find the pages though.

In other cases, in support I've referenced documentation that was written and is no longer accessible on *master/lts/stable* pages, but still exists in non-published form as the source code that generated the published pages.  ie. there is no single place to look.

---

### Post by acer342 on 2021-12-24
So where does your non-removed, back end stuff is stored?

"but still exists in non-published form as the source code that generated the published pages" where?

---

### Post by guiverc on 2021-12-24
Each project/team has their own storage, some of it will thus be on github, some gitlab, some phabricator instances etc., moved stuff can likewise exist in multiple locations...  It'll be on the infrastructure used by that project/team.

I was after an example, this is unlikely what you want but I'll use it anyway given I didn't get any other; as it's one I deal with very often.

Lubuntu's documentation is found at [https://manual.lubuntu.me/](https://manual.lubuntu.me/)   (*with three manuals available there, the latest LTS, the latest stable release & the master; those three choices exist for a number of projects as Lubuntu used the same standard adopted & in-use elsewhere within the Ubuntu family*)

The source code for the manual can be found at [https://github.com/lubuntu-team/manual](https://github.com/lubuntu-team/manual) (ie.* you can access the full history of documentation here in source format*)

Internal & other documentation is stored on their phabricator instance  [https://phab.lubuntu.me/](https://phab.lubuntu.me/)

That is one project/team, of which there are many in the wider Ubuntu family (*I'm in fact involved in a number & using Lubuntu only as example; With Lubuntu everything is public & accessible).*

 My other teams store documentation in different locations; ie. it's project/team specific, be it *flavors* like Lubuntu, to the Canonical connected teams such as Ubuntu Desktop, Ubuntu Server etc (*don't forget that many teams  consist of both Canonical & Ubuntu community members too*).  Some even use discourse (eg. [https://discourse.ubuntu.com/t/ubuntu-documentation/707](https://discourse.ubuntu.com/t/ubuntu-documentation/707)) for many public drafts (*an easy way for general users to read & comment; when published it'll be found at [https://ubuntu.com/tutorials](https://ubuntu.com/tutorials) if it's tutorial etc; Lubuntu & other teams do this too* - ie. there is no single method)

Some of the Lubuntu changes I made I referenced earlier were from [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) & moved elsewhere on [https://wiki.ubuntu.com/;](https://wiki.ubuntu.com/;) ie. only URL/addresses changed (using wiki tools thus wiki indexes are correct), which allows users who use the intended methods of access data find everything correctly; only those using *unofficial* or *stale* links (*including search engines*) went to dead-ends.  This wasn't seen as a problem as it did **not** impact any *supported* release.

---

### Post by poorguy on 2021-12-24
[COLOR=#000000][http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/14.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2014.04%20-%20Second%20edition.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/14.04e2/en_US/screen/Getting%20Started%20with%20Ubuntu%2014.04%20-%20Second%20edition.pdf)

[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf)
[/COLOR]

---

### Post by guiverc on 2021-12-25
:) & thanks PoorGuy

I don't even remember where the [Ubuntu Manual Projec]("https://ubuntu-manual.org/")t store their source; though I know this machine has parts of it (*for 18.04*) actually sitting on my disks (*alas too long ago for my poor non-silicon brain to recall how it worked; but it's all documented on the wikis like everything else*).

The Ubuntu Manual Project  [*stalled* due to lack of volunteers]("https://lists.launchpad.net/ubuntu-manual/") to help updating the manual for Ubuntu Desktop 18.04 & again with 20.04 if I recall correctly, so no copy was actually published on GNOME as sections of the book didn't find editors/authors. No newer copies were ever produced*.*  :(

I actually toyed with using that as my example; but opted for Lubuntu as I could do that purely from memory.

---

### Post by poorguy on 2021-12-25
@guiverc

You are welcome.

I'm a RTFM type person. 
.

---

### Post by acer342 on 2021-12-27
Just answer this: Where is the Ubuntu documentation for say version 8/9/10?

---

### Post by acer342 on 2021-12-27
Thanks. But I can't see how this answer the question.

On a different note, how do you find this?

---

### Post by schragge on 2021-12-27
[https://docstore.mik.ua/manuals/ubuntu](https://docstore.mik.ua/manuals/ubuntu) has copies of some older official ubuntu docs. [s]But why do you need them? Do you have a specific question about an older release of Ubuntu?[/s]

[highlight]Update[/highlight]. @**etimon_64** pointed me to [thread=2470262]your other thread[/thread] which answered my question.
To your last question in that thread
> most latest linux distro it can run and the version?
I'd suggest [antiX]("https://antixlinux.com"). It's a modern Debian-based distro specifically designed to run on ancient hardware. Much better choice than an old, unsupported Ubuntu release.

---


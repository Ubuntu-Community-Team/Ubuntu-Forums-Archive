---
title: "The Ubuntu Wiki needs an overhaul."
date: 2007-11-24
forum: The Cafe
---

### Post by Mazza558 on 2007-11-24
I think many users are intimidated by the methods of getting help for Ubuntu. What would be really nice is to intergrate the forums, the wiki, the main site, and the documentation for Ubuntu, so that it's all linked together. 

1. The first thing Ubuntu needs is an overhaul of the wiki homepage. At the moment, it scares me away, and some of the documentation on these forums is superior to the actual wiki. The wiki homepage has a myriad of sections, with a vague place to start after going through the homepage. By comparison, I've attached an image of the wiki for one of the games I play, showing how it essentially fits on the page with no scrolling. All major sections are organised with every aspect of the game. Users can search for information which isn't on the main page, too.

In case you don't want to view the attachments, here's the links to:

[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

and the Guild Wars wiki:

[http://wiki.guildwars.com/wiki/Main_Page]("http://wiki.guildwars.com/wiki/Main_Page")

2. Secondly, if the forums, the wiki, the main site, and the documentation for Ubuntu were all intergrated, a user could search from any point and it would show results for the wiki as well as from forums, etc. Users connected to the internet could also search through the help and support app built into Ubuntu.

---

### Post by freesitebuilder on 2007-11-24
I use the[ Uboontu search engine]("http://www.uboontu.com") if I want something specific to Ubuntu - this searches the forums, help, documentation pages and lists those results before results from other internet sites.

---

### Post by bonzodog on 2007-11-24
What do you mean by Integrated?

If you mean running on the same software, then that, well, isn't going to work.

You see, the forums run on vBulletin, and there are no alternatives that do the job quite so well.

The wiki runs on Moin Moin, and, I agree that it is ugly , and for me personally, nigh on unusable. This is one of the myriad reasons that the [Ubuntu Document Storage Facility]("http://doc.gwos.org") exists, which I help to Admin.

We run that on Dokuwiki, though it used to run on Mediawiki (which is what the GW wiki runs), but mediawiki can become a monster to maintain and run sometimes --it uses an SQL backend. Dokuwiki, whilst it doesn't scale quite so well (doc limit of about 5,000), it does for the purposes of what we need, and is much easier to maintain.

Yes, I think that they need to talk to each other a bit more - a universal login was proposed at one point, though this currently only runs between the wiki and Launchpad.

But there is no one piece of software that can be a massively scalable, highly versatile forum, and a wiki, and a generic website all in one.

They already all share cross links and forums.ubuntu.com does actually resolve to here.

The main wiki DOES need an overhaul IMO, and I think it needs to seriously think about switching software to something like dokuwiki or Mediawiki.

It then needs all it's existing docs indexing properly - moin moin seems to be terrible at that.

It would take a while to port the docs though, but with the right people behind it, it can be done relatively fast.

As already suggested the only solution is an independent search engine that specifically indexes all the sites.

---

### Post by Polygon on 2007-11-24
Why doesnt ubuntu run mediawiki? its what powers wikipedia and that guild wars wiki site, and i think its MUCH superior to whatever the ubuntu wiki runs on now....not to mention mediawiki looks sooooo much better

---

### Post by 23meg on 2007-11-24
[QUOTE=Mazza558]1. The first thing Ubuntu needs is an overhaul of the wiki homepage.[/QUOTE]

It's been planned for a while. There have been long discussions, and IIRC, the consensus has roughly been moving everything user/help-related to help.ubuntu.com, and everything else to dev.ubuntu.com, which would be reserved for development and team-related things, and doing away with the word "wiki" in the domain name, since it's just a technical word and doesn't explain the purpose of the site.

There were some valid reservations that prevented any action being taken, though. You can do a search in the mailing list archives to find out what exactly they were.

[QUOTE=bonzodog]It then needs all it's existing docs indexing properly - moin moin seems to be terrible at that.[/QUOTE]

What exactly do you mean here? I haven't noticed any problems in this regard.

[QUOTE=Polygon]Why doesnt ubuntu run mediawiki?[/QUOTE]

MoinMoin uses Python, and Python is a favourite of Canonical in general. Also, Canonical are pretty strict regarding the software they'll run on the servers, and it may be that they want to minimize the complexity by keeping as much of the software as possible Python based.

[QUOTE=Polygon]and i think its MUCH superior to whatever the ubuntu wiki runs on now[/QUOTE]

You don't mention in which way you think it's superior, but at the end of the day, even if it's superior in some ways, it's a question of whether we really need those superior features, and whether we'd trade MoinMoin's advantages for them. Remember that Mediawiki was designed for Wikimedia's projects in mind; it primarily aims to fit those projects the best way.

---

### Post by 23meg on 2007-12-19
A few things I should add:

[QUOTE=Mazza558]I think many users are intimidated by the methods of getting help for Ubuntu[/QUOTE]

Community documentation is now supposed to be created in [https://help.ubuntu.com/community](https://help.ubuntu.com/community), rather than the main wiki. If you come across any documentation in the main wiki, you can help improve things by moving it to [https://help.ubuntu.com/community](https://help.ubuntu.com/community). Instructions and a dynamic list of pages that need moving are available at [https://wiki.ubuntu.com/CategoryDocumentation](https://wiki.ubuntu.com/CategoryDocumentation).

[QUOTE=Mazza558]What would be really nice is to intergrate the forums, the wiki, the main site, and the documentation for Ubuntu, so that it's all linked together. [/QUOTE]

[QUOTE=Mazza558]2. Secondly, if the forums, the wiki, the main site, and the documentation for Ubuntu were all intergrated, a user could search from any point and it would show results for the wiki as well as from forums, etc.[/QUOTE]

[URL="http://search.ubuntuwire.com"]
Ubuntuwire's search facility[/URL] lets you search many Ubuntu-related sites (Launchpad, wiki,  forums, etc.) with one interface.

---

### Post by smartboyathome on 2007-12-19
23meg, I am confused now. Is the art team staying put for now on wiki.ubuntu.com, or is it being moved to one of the alternative sites. If it is being moved, which one is it being moved to (I didn't find it on help.ubuntu.com, and dev.ubuntu.com isn't up)?

---

### Post by 23meg on 2007-12-19
help.ubuntu.com is just for documentation. All team pages, and everything else related to development is staying on the main wiki, which may be renemed to dev.ubuntu.com at some point (I'm not sure about the outcome of that discussion).

However, art.ubuntu.com will soon be relaunched, and as far as I know, it's meant to make it easy for people to share and discuss artwork and mockups. Stuff related to the team itself will probably remain on the wiki.

---

### Post by jpkotta on 2007-12-19
I completely agree.  I absolutely hate MoinMoin.  MediaWiki has clearer syntax, is better documented, makes it easier to track changes, and seems to run faster (e.g. previewing, though this is probably more a function of the server's speed).  And now that I think about previewing, I think of that hideous Ubuntu logo underneath my draft version, making it hard to read.  I also like how MediaWIki automatically has a discussion page.  

I still use the wiki because I think wikis are inherently better for documentation than a forum.  I was also initially confused by the fact that there was a wiki.ubuntu.com and a help.ubuntu.com, they look almost identical, and sometimes have similar articles.

I think the fact that MoinMoin is implemented in Python is a poor justification to using it.  It shouldn't matter what the implementation language is; are they hacking it?

---


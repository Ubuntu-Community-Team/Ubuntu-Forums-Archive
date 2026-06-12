---
title: "INTRANET configuration suggestions"
date: 2009-01-29
forum: Server Platforms
---

### Post by R.Bucky on 2009-01-29
I have been given the preliminary go ahead to begin work on an intranet for my office of 18 employees. We are an air monitoring agency with 4 main divisions. I would like to integrate a search engine for our internal network documents, photos, and folders. What open-source apps can the community recommend? Can anyone share their ideas, thoughts, or SCREEENSHOTS of intranet developments?

The intranet will be hosted using a LAMP configuration. I have hosted my own domain for just short of 2 years, so I am not a complete noob. The office does not currently utilize a MySQL framework, but soon... Some features that I would like to include are RSS, a bulletin board, image upload and gallery, and document storage. I am skilled in CSS and HTML with moderate abilities in PHP. 

What are your ideas?

---

### Post by Vegan on 2009-01-29
You don't want much do ya. A standard LAN based server can do the job and configuring the router to not accept outside traffic is simple enough.

If you want to use domains, you will need to use more software so read up on BIND. You could use HOSTS but that has a lot of limitations.

You could also have a more complicated setup depending on the needs. For example the 4 divisions could be carved up with a server using SAMBA to provide server services. I use SAMBA for Windows access to the web site folders. SAMBA can do much more and its also a major undertaking.

As servers are cheap these days, you could also use 4 separate servers and really fill up the rack. Then you could pester your boss for more IT spending.

:guitar:

---

### Post by R.Bucky on 2009-01-30
I am currently using VMWare Server2 with an Ubuntu Desktop LAMP as a development environment until the complete needs of the intranet are realized. We use a FreeBSD server for our pages, so I am confident in the system. I plan on plugging it in to the LAN in some corner where it is out of the way. 

Does anyone have screenshots or successful integrations of off the web apps such as bbpress, wordpress, or other CMS derivatives?

---

### Post by lykwydchykyn on 2009-01-31
I do not have quite what you are asking about, but I've successfully used MediaWiki where I work to create a help website for our users.  A wiki is an easy solution that offers some nice things:
 - searchability
 - revision control
 - Document/photo upload (some CMS engines I've seen restrict uploads or make them difficult -- be careful)
 - Nice formatting tools

Biggest drawback to wikis is getting users to learn the syntax.  Honestly, it's a bit wonky and even our techs bail out sometimes when I ask them to add something because of the syntax.  OpenOffice has an export plugin for media wiki, but I've not tried it yet.

Previously I'd used phpnuke, which I didn't like because it was obviously geared toward a certain type of site and there was too much I couldn't disable.  Joomla was a similar experience.

I tried getting my head around Django, but unless you want to get into a lot of coding and abstract concepts it's not really what you want.

I collaborated with some folks once using a Drupal site; it had a lot of interesting options -- much more flexible than the usual "web portal in a can" software, and much different from a wiki.  But a Drupal site can become and unholy mess if you aren't careful about keeping things organized.

Are you looking for a workflow type application, or more of a site-in-a-can that you can upload and search documents?

---

### Post by R.Bucky on 2009-01-31
I was thinking of utilizing Wordpress and bbpress as they are well supported and have many plugins. The search function would work only if it would index our office file server, in addition to the content encapsulated on the intranet. The search function is fairly important.

Agreed on the Wiki syntax. I tried wikis a while back, and found them a bit cumbersome from the sytax point of view. The idea is to have a platform that would have a WYSIWYG input base and a MySQL data storage engine. My office is looking at migrating from Access to MySQL or a similar derivative, so a WP backend would be nice.

---

### Post by Zillion on 2009-01-31
I work myself with TYPO3, the most powerfull open source CMS framework. But it has a bit high learning curve...

---


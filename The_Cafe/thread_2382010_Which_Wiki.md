---
title: "Which Wiki?"
date: 2018-01-07
forum: The Cafe
---

### Post by pengyou2 on 2018-01-07
This is related to Ubuntu, in as much as the service that I subscribe to for hosting uses Ubuntu.  I want to install a Wiki on my site for my students to use to make small websites about geography for their project.  My choices are doku wiki, media wiki, PM wiki, and Tiki Wiki CMS.  I am trying to find one that will be "student friendly" for my students to use to upload photos, video, graphics and text.  I would like it to be secure, so that each student has their own password and account for his/her page.  I have been reading up on these and they all sound like they are easy to use, secure, etc. My experience from delving into a number of searches is that, in fact, their descriptions are not very accurate.  Does anyone have any experience with these?  or any wisdom in how to proceed?  I wish there was some standard for "user friendly".  A plug-in to WordPress would also be nice because wp has the security I need.

---

### Post by TheFu on 2018-01-08
These questions are all opinion-based.

I don't consider any php web-app to be secure. Wordpress would be on the bottom of my list from a security perspective as soon as any addon is added, though node.js is racing to beat them. [https://www.infosecurity-magazine.com/news/over-one-million-wordpress-sites/](https://www.infosecurity-magazine.com/news/over-one-million-wordpress-sites/) is just 1 article about this. There are hundreds. Being popular **is** an issue.

Passwords don't make a web-app secure. Actually, web-apps that use passwords are inherently non-secure. But for something like a wiki, the security of a password is probably sufficient.

I've used tikiWiki and mediaWiki. I've setup mediaWiki for a few small companies.  Non-technical people tended to find wiki syntax too difficult to bother using. It was a real challenge to get them to edit/add to the wiki at all.  We failed. They ignored it.  
 I provided a hour of training in small groups, but they never bothered using the wiki.   

tikiWiki was slow, at least on the server we used. I didn't set it up or have any access beyond the web interface.  MediaWiki was responsive, but you'd really need to add a visual editor addon.  All addons in webapps reduce the security of the total webapp - at least that has been my experience.  Our mediawiki instance was only available via VPN. We were pretty paranoid about security there.

I don't know anything about the others in the list. Sorry.

For a student use-case, have you considered the all-in-one solutions like moodle?  [https://download.moodle.org/](https://download.moodle.org/) or a competitor to that?  You've probably already looked at those things, but for people in the future who read this, it might help.

---

### Post by Habitual on 2018-01-08
I chose Dokuwiki because it stores text in files, not a db.

---


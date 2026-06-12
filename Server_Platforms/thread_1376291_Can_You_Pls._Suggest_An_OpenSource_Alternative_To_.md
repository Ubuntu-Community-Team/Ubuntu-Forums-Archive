---
title: "Can You Pls. Suggest An OpenSource Alternative To MS Sharepoint?"
date: 2010-01-09
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-01-09
Hi, thanks for reading. The reason I'm asking is because we have an office about 20 workstations and 1 server. I want to build an Intranet website for content, idea, calendar, contact, etc... sharing for everyone. I've tried Sharepoint before, but it's M$, you know, and we've completely switched to Ubuntu and OpenSource. :)

---

### Post by AlexanderDGreat on 2010-01-09
Can anybody help?

---

### Post by AlexanderDGreat on 2010-01-10
Surely, anyone out there knows ANY useful Opensource CMS for an Internal website! Pls. help...

---

### Post by Cheesemill on 2010-01-11
There are hundreds of options, take your pick:
[http://php.opensourcecms.com/scripts/show.php?catid=1&cat=CMS%20/%20Portals]("http://php.opensourcecms.com/scripts/show.php?catid=1&cat=CMS%20/%20Portals")

Personally I use Drupal and Joomla due to the large communities and availability of plugins/themes.

---

### Post by munky99999 on 2010-01-11
[http://etherpad.com/](http://etherpad.com/)
[http://code.google.com/p/etherpad/](http://code.google.com/p/etherpad/)
-very strong but from what i read, the package on googlecode is broken. So will take some fixing

google wave
-if you can get an invite. afaik you have to run it on google's servers.
-eventually they want to open source it.

[http://www.joomla.org/](http://www.joomla.org/)
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)
-this is what I use. Good stuff. It's popularity though has led to much fuzzing, which atm has a good number of vulnerabilities; so be careful.

[http://en.wikipedia.org/wiki/Oracle_Beehive](http://en.wikipedia.org/wiki/Oracle_Beehive)
-well... it's oracle. Proprietary just like sharepoint.

[http://www.dimdim.com/opensource/dimdim_open_source_community_edition.html](http://www.dimdim.com/opensource/dimdim_open_source_community_edition.html)
-slick but doesnt scale well

[http://en.wikipedia.org/wiki/MediaWiki](http://en.wikipedia.org/wiki/MediaWiki)
-the wiki itself.


really depends on what you want done.

I think the future of collaboration isnt quite realized yet. I think they will be moreso inevitably be a framework developed by the desktop environment.

Imagine the ability to remote in using VNC having full control of the desktop and apps; but also having the ability for anyone else to remote in and have the same control and all the other users have a sort of "ghost pointer" for everyone; so you see what everyone else is up to.

similarly have the same power for terminal apps also.

---

### Post by HomoGleek on 2010-01-11
[http://www.osalt.com/search?q=sharepoint](http://www.osalt.com/search?q=sharepoint)

---

### Post by AlexanderDGreat on 2010-01-11
@Chesemill - thanks for those links, but I'm really looking for a program that someone has actually tried that works. I'll look into Drupal and Joomla.

@munky99999 - Thanks, I'll look up all those links.

@DarrenTod - I was thinking of something you actually tried and implemented.

Thanks for all the answers.

---

### Post by Lars Noodén on 2010-01-11
Well that depends on how you frame what "SharePoint" does.  I'm sure you can add hacks to any of the below to make them lose random documents or have difficulty working with certain clients, systems or data formats or corrupt the operating system requiring a re-format/re-install removal of the operating system and any third-party apps.  :P

Rather than asking for $THNEED, please tell us what you plan to use it for and how you plan to benefit from it and which languages you wish to develop in.  

Since you ask for ones that are *used*, I've used these as an external user.  Much has changed since I last installed and played with Lenya and Plone.  Such systems are always under development and so moving targets:

[list]
[*][Drupal](http://drupal.org/)
[*][OpenCMS](http://www.opencms.org/en/)
[*][Plone](http://plone.org/)
[*][Lenya](http://lenya.apache.org/)
[*][Joomla](http://www.joomla.org/)
[*][Nuxeo](http://www.nuxeo.org/)
[*][O3 Space](http://o3spaces.org/)
[*][Lyceum](http://lyceum.ibiblio.org/)
[*][Alfresco](http://www.alfresco.com/)
[/list]

If you need celebrity endorsements, the EU presidency will use OpenCMS:

[http://www.itwire.com/content/view/30304/1141](http://www.itwire.com/content/view/30304/1141)

The US presidency will go back to using FOSS and use Drupal.  

[http://www.theage.com.au/technology/enterprise/white-house-switches-to-open-source-20091026-hfdo.html](http://www.theage.com.au/technology/enterprise/white-house-switches-to-open-source-20091026-hfdo.html)

---

### Post by AlexanderDGreat on 2010-01-12
@Lars Noodén - great news! Thanks for sharing, I think I'll try Drupal.

---

### Post by Lars Noodén on 2010-01-12
@ AlexanderDGreat :  If it's not too nosy, can you say a little about what plans you have for using these tools?  A more specific use-case can job a few memories or elicit more input.

---

### Post by AlexanderDGreat on 2010-01-12
No, of course not, it's perfectly fine. Just like I said in my post, we have an office with 20 workstations and file sharing, pictures, calendar-events, meetings, memo's, ARE SO DISORGANIZED! Whew... It's my job to keep them organized so we'll install a basic Intranet website so everyone who opens up their web browser will get redirected to this Company's Internal Web, I have a dd-wrt router, so everyone in the morning the first thing they do is syncronize what everyone else's job will be. I hope I answered your question. :)

PS By the way, I work at a construction firm.

---

### Post by Lars Noodén on 2010-01-13
Do you already have Samba for file sharing and Apache2 for the web server?

---

### Post by AlexanderDGreat on 2010-01-13
Yeah, I'm using NFS for Unix systems and Samba for Windows XP, I did this sudo apt-get install lamp-server^ and I signed up for a dyndns.org account. I studied a little about php object oriented programming to create a MySQL data-driven website, but figured there are lots of CMS already out there, why re-invent the wheel, right? Why'd you ask?

---

### Post by Lars Noodén on 2010-01-13
> **AlexanderDGreat said:**
> ... but figured there are lots of CMS already out there, why re-invent the wheel, right? Why'd you ask?

Good approach.  

I ask because I used to set up, design (including creating taxonomies), and even develop both larger and smaller systems for managing documents and other online resources for about 10-11 years, primarily focused on document retrieval.  Stopped in 2004.  

Also, a Very Long Time Ago (tm), I managed a large database of Frequently Asked Questions and HowTos for a large university's IT department.  Some of that was standardizing the terminology in the entries (which could be several pages), the most useful part was ensuring the right descriptions, keywords (aka subject descriptors).

FWIW I see that new entrants, Boeing, Arwidson Oy and others make good money doing FOSS development more related to workflow than document retrieval.

---

### Post by Lars Noodén on 2010-01-13
Sooo...

I am surprised to notice that it turns out I am still far more interested in these things that I expected.  And I have been asked by others, outside this forum, almost the same question twice in two days, all together three times.   

Here are questions that you don't need to tell anyone, but would be useful to know yourself to guide your choices and priorities:

[list]
[*] What kind of searching and or browsing are your people looking for?  
[*] In other words what can't they find now, but spend time looking for?

[*] What volume of documents already exist and at what rate is the collection growing?
[*] How long must the documents, or subsets of documents, be kept?
[*] Is there an obligation to delete certain documents after a certain time?
[/list]

The most important is that it is simple for all involved.  
At the low-end lot can be managed via the filesystem, adding ACLs if needed.  One method for small shops that works: 

[indent]
have a write-only "drop box" for "finished" documents and a cronjob that notifies the maintainer(s) of the arrival of new documents.  

maintainer(s) checks and maybe normalizes document metadata: title, author, date, subject, etc. (*)

document is copied to the appropriate folder in the archive and 

the Intranet's indexer/cataloger is updated:
[list]
	[*][http://swish-e.org/](http://swish-e.org/)

	[*][http://hyperestraier.sourceforge.net/](http://hyperestraier.sourceforge.net/)

	[*][http://lucene.apache.org/](http://lucene.apache.org/)

	[*][http://www.namazu.org/index.html.en](http://www.namazu.org/index.html.en)

	[*][http://xapian.org/](http://xapian.org/)
[/list]
[/indent]


(*)  this is about the only way to have highly accurate search / browse results.  It can be skipped if full-text is enough
OpenDocument Format and PDF/A can support use of Dublin Core for this, but skipping this step will cause more 'where is it?' dialogs.  

Normalization of metadata can be done in a minute or two.  What is most valuable is that the same individual does the labeling so that it is **consistent**.  Even if it's not accurate or even correct, as long as it is consistent, the error can be compensated for.  It's ok to have users propose metadata, but it should still be gone over for consistencies sake.  

Going to great lengths to classify documents does not have as much of a return on investment for small, seldom used collections.

---

### Post by SecretCode on 2010-01-14
Thank you for those 3 posts Lars - useful and thought-provoking.

---

### Post by AlexanderDGreat on 2010-01-16
Hi Lars,

>     *  What kind of searching and or browsing are your people looking for?
    * In other words what can't they find now, but spend time looking for?
    * What volume of documents already exist and at what rate is the collection growing?
    * How long must the documents, or subsets of documents, be kept?
    * Is there an obligation to delete certain documents after a certain time?


I will post these on my computer monitor and reflect. Thanks.

---


---
title: "I want ot create a blog."
date: 2019-12-24
forum: The Cafe
---

### Post by wolftrax on 2019-12-24
I want to create a blog where I write about good movies I seen.  can anyone recommend me a free solution for that small project ?

---

### Post by Frogs Hair on 2019-12-24
I had a free wordpress blog and it was good platform to gain followers and find interesting subjects.

---

### Post by wolftrax on 2019-12-24
thanks.

---

### Post by kevdog on 2019-12-27
Who hosted your wordpress blog or was it self hosted?

---

### Post by TheFu on 2019-12-28
There are probably 50+ different blog platforms.  Each has faults and failures.
Wordpress is is the MS-Windows of blogging platforms. It is constantly attacked, 3rd party themes and addons cause security failures.  If you run a stock Wordpress install, it is fairly secure. Change the theme or use any addon created by someone not a php expert, all bets are off.  Be extremely careful with file+directory permissions using any CMS, but especially wordpress.

There are a number of other Content Management Systems - CMS.  Drupal, Joomla, Publify, Typo, lots more.
Alternativeto.net will find lots.

Do you want to self-host?  Do you want paid hosting?  Do you want shared hosting?  How cheap do you need? Beware that most hosting providers will setup a CMS, but won't ever update/patch it.  You'll need to do that yourself unless you pay for premium support.

Have you considered using static files that are published through a batch process?  Lots of bloggers have switched from the interactive, DB-driving blogging platforms to static sites for security reasons.  If you don't need php, ruby, or a DBMS, static hosting can be crazy cheap.  Add those things in an the costs can be 10x more.   I've always wanted to use these guys: [https://www.nearlyfreespeech.net/](https://www.nearlyfreespeech.net/)  It is pre-paid, no hand-holding, $0.50/month for a static, shared hosting, setup. It will automatically scale bandwidth as needed. Basically, we pay for the data transferred out. A small blog will cost next to nothing, but if it becomes popular, scale to handle a slashdot hit with thousands of concurrent hits, before it drops back to just a few hundred per day after a week or so.  Much cheaper than buying a business connection from any ISP or setting up a $5/month VPS.

Moving my blog to static has been a goal for years, but I haven't found a tool that will correctly export it due to some choices I made around 2006. I chose to use textile rather than markdown. I still prefer textile and really want to retain the comments. Have about 2000 articles though only about 200 are useful.  So far, looks like the only solution will to lose all comments and require changing to HTML.

google "static site generator" for some of those tools.  Then you'd probably deploy using rsync.  I've been playing with *Template::Toolkit* to accomplish this for a few years. For static sites that appear dynamic, CSS can work wonders.  There are lots of other static site generators.  If you've done any scripting, writing your own static site filter is usually a pretty easy task.  [https://www.linode.com/docs/websites/static-sites/how-to-choose-static-site-generator/](https://www.linode.com/docs/websites/static-sites/how-to-choose-static-site-generator/)  The choice usually depends on the scripting language you already know.  Go, Ruby, php, Python, Perl ... all have static site generation tools.  Probably best to use a tool that will let you have the content compressed and that will optimize image files as part of the deployment step.  Why have a 250KB image when a 12KB image looks the same on a webpage?  Static sites are great for security.

Of course, if you don't go with a free host that specifically does blogs, then you'll need to buy a domainname and probably commercial DNS to point towards the specific IP(s) used.  Google ranks non-SSL sites lower, so you'll want to get a cert as well.

---

### Post by Frogs Hair on 2019-12-28
> **kevdog said:**
> Who hosted your wordpress blog or was it self hosted?

At that time I did not have to do anything related to hosting though things may have changed now that I look into it. I created a free site using a free theme and posted continent and followed other posters.

---

### Post by wolftrax on 2019-12-29
to begin with I just want a free blog I can write reviews of movies I seen and learn html coding meanwhile.  its not anything but educational value.  I have a free blogspot I am working on now where I want to review linux and otehr operative systems but it takes a lot of time to just writing the content and I am nowhere nearly done with the introduction yet. 

movies are sort of more easy for me to write about since I watched a lot of movies in the past and I would think its more easy for me to write something about the movies I like or dislike as short reviews and I could learn a little by doing this as well. 

if by any chance I get relatively good at it I do have some political points of views I want to share with others and then I would be buy a domaine name and set it up..  its the experience I need to gain so wordpress might as well be a good place to start.

---


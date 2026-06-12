---
title: "Commit WebPage via CVS"
date: 2006-01-03
forum: Server Platforms
---

### Post by brentoboy on 2006-01-03
Does anyone out there know of a way to combine Apache and CVS in such a way that you can manage and update a website using CVS instead of FTP-ing the new html docs.

In other words, can I build a CVS module "httpdocs" and then tell apache to use the current version of all the files in the CVS as the actual httpdocs folder?  So that me and a group of site developers can all work from our own CVS repository, and update the website by simply commiting to CVS?

I dont mind if that means that when I commit, it just posts a fresh copy to the actual folder being hosted by apache, or if somehow apache could actually be smart enough to query the current version of a page from the CVS folder without all the extra back-version stuff from previous commits.

has this sort of thing ever been attempted? it seems like a hand in glove fit, but I cant find any info on how to accomplish this sort of thing.

anyone have any ideas?
thanks
-b

---

### Post by brentoboy on 2006-01-03
Anyone?

Please?

---

### Post by majikstreet on 2006-01-03
hmm... I like the idea, but I dunno how to do it.. 

majikstreet

---

### Post by brentoboy on 2006-01-04
I'm guessing that the answer requires me to write a script that gets run after (or as part of) a commit.

I know I cant just copy the file, becuase it is full of version-junk from previous commits.

I know CVS supports server side scripts, becuase the office I used to work at had some validation scripts on the server, but I dont even know where to start writing a script that posts a file to a web folder....

There's got to be someone out there who has done this (or at least tried, and failed) with some advice...

someone... anyone?

---

### Post by tbrownaw on 2006-01-05
Have the web folder be a CVS checkout, and have scripts that run "cvs update" after a commit or just as a cron job?

Tim

---

### Post by brentoboy on 2006-01-06
That sounds like a good idea.

I'll have to play around with it next time I get a chance.  If I get it working, I will post the thigs I do (along with those that dont work)

---


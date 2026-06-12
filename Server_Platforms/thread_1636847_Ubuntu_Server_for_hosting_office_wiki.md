---
title: "Ubuntu Server for hosting office wiki"
date: 2010-12-03
forum: Server Platforms
---

### Post by smerdyakov on 2010-12-03
Hi All, 

Sorry if this is a bit of a random, cobbled-together question! 

I work for a small non-profit, and we are considering using a wiki to pull together a lot of the random information we have, as well as link to files. Since we are poor, I think an ubuntu server running apache with an install of mediawiki seems like the way to go. The only problem is that i've never set up something like that before. I've seen guides here and there, which I probably could follow, but i'd like to know if such a thing is doable by a beginner. 

The server would host the wiki, and our office files (which range from 20kb word documents to 50GB videos), so we could link the files to individual pages for reference. 

I'm a bit out of my league here, so any help (even if it is telling me that such a thing is WAY out of my league) is much appreciated! 

Thanks, 
Nick

---

### Post by CharlesA on 2010-12-03
It shouldn't be all that hard to get it working. 

See here: [https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

---

### Post by SeijiSensei on 2010-12-04
I've worked a little with a site running MediaWiki, and I'd have to say the syntax of entries is *very* arcane.  I don't think I'd enjoy training staff to enter all those {{entry}} types of tags.

You might do better with a "content management system" like [Drupal]("http://drupal.org/") or [Joomla]("http://www.joomla.org/").  These function like shared websites and are designed to let naive users easily upload content.

Another alternative might be using Google Docs.  You won't be able to upload those 50 GB video files, but you can manage office documents and a calendar there.

---

### Post by smerdyakov on 2010-12-08
> **SeijiSensei said:**
> I've worked a little with a site running MediaWiki, and I'd have to say the syntax of entries is *very* arcane.  I don't think I'd enjoy training staff to enter all those {{entry}} types of tags.

You might do better with a "content management system" like [Drupal]("http://drupal.org/") or [Joomla]("http://www.joomla.org/").  These function like shared websites and are designed to let naive users easily upload content.

Another alternative might be using Google Docs.  You won't be able to upload those 50 GB video files, but you can manage office documents and a calendar there.

You make a good point, ease of use is definitely important for the office. We've tried using Google Docs already. We have a lot of information that needs to be accessed but not necessarily changed (lists of speakers at an event and session tittles, summaries, and outlines). Putting it all in a google doc doesn't help because their needs to be some relational organization between the individual files (documents, audio, video, and factual data). Something like a PB  wiki would probably be best, but we don't have the money to pay the monthly fees related to using a PB wiki's hosting features.

On another Note: I've succesffuly installed a 10.10 LAMP server on my LAN, but I can't access the computer with the hostname (which is"server"). It only works if I type in the full IP. How can I change this? (our router currently assigns the DNS, I believe). 

Thanks!
Nick

---

### Post by CharlesA on 2010-12-08
You'd have to make sure DNS is updated.

---

### Post by confusedstingray on 2010-12-10
you have to some how add the ip of the server to dns (if you can) 
or change the hosts files on each machine
eg;  ubuntu host file 
the host file is located at  /etc/hosts
them you have to edit the file

 sudo vi /etc/hosts

then add your server ip to the file 
something like ;

192.168.1.100     server

change the ip to match your servers ip

---

### Post by garryconn on 2010-12-10
The install process of Ubuntu Server is really simple. Even getting things setup such as LAMP isn't too bad at all. The amount of documentation on this is amazing. So you're pretty much covered up to that part. Once you have the LAMP setup, then you need to decide on which CMS is best to use for your non profit organization. 

Wiki is complicated. I love using free php programs a lot (wordpress, phpbb, joomla, etc..) but mediawiki takes a lot of time to learn and then like SeijiSensei had mentioned, now you'll have to train everyone else how to use it. 

Using Google Docs might be the perfect solution actually. It's totally easy to use plus you don't have to depend on your own server to run it. It's all hosted free by Google. Unless you're in this for learning and for the challenge, I would just keep things simple and go with Google. 

If you do decide to host your own CMS, then I second the opinion to use Joomla. It's widely supported, and their community forums are full of helpful people. Good luck.

---


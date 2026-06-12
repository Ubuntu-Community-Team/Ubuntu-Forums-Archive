---
title: "Chrome -&gt; Suspection of Intrusion"
date: 2016-06-04
forum: Security
---

### Post by coinfuture on 2016-06-04
Greetings, and thank you kindly for viewing my thread. 

I am generally new to development (under 2 years) and new to linux (approx 1 year). 

I am a fan of Google, and thus use the Chrome Browser. 

I was researching web scrapers, as I was trying to compile data that would not be that effective to get through the use of API. 

So, I installed multiple web extensions in chrome, all the top rated web scrapers. One of these web scrapers actually ended up installing a "Chrome Web App", when I only installed it as a Chrome Extension. 

After this had happened, ALL of my Google Accounts became logged out of Chrome. Chrome had me logged out completely, with a blue bar across the top of the header. When logging back in (mistake), I noticed that I was not logged in via the web browser, but rather a "shell" around the web browser, with my Google Accounts now outside of the web browser. 

I immediately started checking all settings, removing the extensions, and even ended up removing Chrome completely out of fear of breach of data. 

Next I started up Chromium Browser. It worked fine at first, then experienced chromium browser freezing, and the same setup is now on chromium. where i am logged out inside of the browser, and there is a new "shell" outside of the browser with my accounts. 

Normally, I search for everything myself as I consider everything on the web a learning experience. However, I could not find an answer to this. Could somebody please offer some insight into what happened? Any thoughts, ideas? I tried looking through dpkg.log but this proved useless, because I could not 100% comprehend all of the information stated. 

*Also for bonus points what are some good linux resources that are not easily found via search? 
*Maybe this whole thing is a blessing in disguise, as being a member of this forum will give me incredible opportunity to learn

Thank you,

---

### Post by TheFu on 2016-06-04
Welcome to the forums.

I don´t use chrome browser for privacy reasons, so cannot comment on all that stuff. I block much of google´s infrastructure in a nearly useless attempt to regain some level of privacy from their insidious tracking.  Facebook, twitter, and others are blocked as well.  An article of mine about this: [http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

You may want to look at web-app testing tools. These tools are specifically designed to exercise all aspects of complex websites.  I´ve only used relatively simple versions - my webapps don´t use much javascript on purpose.  Perl Test::More and Cucumber are the tools I´ve used most.

> *Also for bonus points what are some good linux resources that are not easily found via search? 
Find a local LUG, hang out with other people running Linux full-time and run Linux 90% of the time for your home and work needs, if you can´t go 100%. Pick a book and work through it from start to finish.  Learn the shell. Learn the non-GUI methods to do everything (except things which are only possible through the GUI).  Things like reading email and grabbing web pages ARE NOT GUI ONLY.  By working through a book, you´ll get organized knowledge that builds instead of disconnected information.  I like [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) that book. Free PDF download or you can visit any bookstore and buy a copy.  

Would help to find a mentor too, but you need to find someone experienced in the knowledge you seek AND willing to help. Most developers are too busy to be mentors. That will make it hard to find a willing mentor with current skills. There are also groups for specific types of skills that meet all around the world. Seek those groups out. Join them. Listen for a month to their conversations. Attend their meetings. Engage with the group.  For example, my metro area has groups for almost every programming language, devops, multiple OSes, databases, virtualization, and sometimes for specific tools.  Seek those out.  If you need a way to meet them virtually, but don´t like the big, privacy sucking, video conferencing tools (skype for example), take a look at [http://talky.io](http://talky.io).  Quick, easy, no accounts needed, and the only security is from the unique ¨room¨ name you create and share with the other persons involved.

There is a huge fountain of wildly varying knowledge here too.  Do some homework, ask some questions and this community will try to help. We don´t have all the answers, but we will usually share. Please don´t forget that we are all volunteers. 

BTW, I use the chromium-browser from time to time too. It is the browser I use when very complex websites, full of javascript, need to be accessed - think printing airline boarding passes; there are still parts of the world where e-boarding passes are NOT accepted; security won´t allow you into the airport without paper. ;(  Of course, when I use chromium, it runs inside a secured, locked down, virtual file system, container to prevent it from doing anything too nasty.  
```
$ firejail --private chromium-browser
```
The download location for the PDF boarding pass is only seen inside the container. Outside that container, it isn´t known at all.

---


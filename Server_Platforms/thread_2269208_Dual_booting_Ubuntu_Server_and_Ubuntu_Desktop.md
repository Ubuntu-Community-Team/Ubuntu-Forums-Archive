---
title: "Dual booting Ubuntu Server and Ubuntu Desktop"
date: 2015-03-14
forum: Server Platforms
---

### Post by mandarpowale on 2015-03-14
Can I dual boot Ubuntu Server 14.04.2 and Ubuntu Desktop 14.04.2?

I have the Desktop edition installed on one of my partitions already. I have a 250 GB partition available for use.

ADD: I need Server to learn and practice Linux

ADD: Please reply ASAP, as I am doing a course from edx.org.

Ty in advance.

---

### Post by TheFu on 2015-03-14
You don't really need to dual boot anything.
Just don't use a GUI to do anything. Open a terminal or 5 and start typing.

I hate to say this, but you really want a little more background in Linux before starting that course.
The first 5 links here [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) will provide that.  The Command Line Linux link - just read the first 131 pgs (or so) of that book/PDF ... then you should be ready to start the Edx Linux class.  Reading the first 5 shouldn't take over 3 hrs with the first 4 items taking about 30 min.  

Trust me.

---

### Post by mandarpowale on 2015-03-14
Thanks, I will read them.

---

### Post by mandarpowale on 2015-03-14
How do I surf the net on a dos prompt (ubuntu prompt)? The website you typed in is untrust worthy according to mozilla.

---

### Post by TheFu on 2015-03-14
a) that's my site: blog.jdpfu.com . I think some mozilla plugin is lying. However, some ISPs in Thailand and India have reported issues connecting. I've never had issues anywhere else, but I've only tried from about 25 different countries on 5 continents.
b) you can use **lynx** from a terminal. I do that sometimes.
c) you can disable javascript and cookies - all the info/links should still work. Just comments won't be displayed and you cannot make comments. No big deal.

[https://www.google.com/safebrowsing/diagnostic?site=jdpfu.com](https://www.google.com/safebrowsing/diagnostic?site=jdpfu.com) - google doesn't think it is unsafe. 
I don't allow google to use their analytics, so they don't get a deeper look.

AVG says it is safe too: [http://www.avgthreatlabs.com/us-en/website-safety-reports/domain/jdpfu.com/](http://www.avgthreatlabs.com/us-en/website-safety-reports/domain/jdpfu.com/)
WoT says it is a "good site": [https://www.mywot.com/en/scorecard/jdpfu.com](https://www.mywot.com/en/scorecard/jdpfu.com)

The links from my site to other sites are all safe, unless something changed.

Which plugin are you using that claims my site isn't safe?  I take security very seriously.  Last time any server of mine was hacked was in 2002.

---

### Post by mandarpowale on 2015-03-14
i will check tomorrow, sleepy now,  thanks for your time.

---

### Post by mandarpowale on 2015-03-15
it says that 'Requested URL was not found on the server'. I went to the blogs main page and it said that I have to login.

Very sorry to say that the link is not working. Thanks for you help.

---

### Post by TheFu on 2015-03-15
Looks like your ISP is blocking parts of the internet for no good reason. Complain and use a proxy in the meantime.
My website doesn't even allow logins, so the ISP/government is doing a MiTM attack against your system - for some reason.

Looks like my little blog has been caught up in this 
[http://www.labnol.org/internet/blogging/blogspot-typepad-blogs-banned-in-india/59/](http://www.labnol.org/internet/blogging/blogspot-typepad-blogs-banned-in-india/59/) - long time blocking
[http://techcrunch.com/2014/12/31/indian-government-censorsht/](http://techcrunch.com/2014/12/31/indian-government-censorsht/)
[http://www.bbc.com/news/technology-30656298](http://www.bbc.com/news/technology-30656298)
[http://www.zdnet.com/article/india-blocks-32-websites-including-github-internet-archive-pastebin-vimeo/](http://www.zdnet.com/article/india-blocks-32-websites-including-github-internet-archive-pastebin-vimeo/)
[https://www.techdirt.com/articles/20141231/02075529554/indian-government-orders-32-web-sites-blocked-including-github-archiveorg-pastebin-dailymotion-vimeo.shtml](https://www.techdirt.com/articles/20141231/02075529554/indian-government-orders-32-web-sites-blocked-including-github-archiveorg-pastebin-dailymotion-vimeo.shtml)
[http://timesofindia.indiatimes.com/tech/tech-news/Pastebin-Dailymotion-Github-blocked-after-DoT-order-Report/articleshow/45701713.cms](http://timesofindia.indiatimes.com/tech/tech-news/Pastebin-Dailymotion-Github-blocked-after-DoT-order-Report/articleshow/45701713.cms)
[http://en.wikipedia.org/wiki/Internet_censorship_in_India](http://en.wikipedia.org/wiki/Internet_censorship_in_India)

Which makes no sense to me.  I'm just a F/LOSS blogger.  Did you try using the IP address instead of the DNS name? Whenever I've traveled to more restrictive places in the world that blocked websites, using the IP address often got around name-based blocking. Heck - I provide US Govt links for what to do if there is a zombie attack, so it can't be all bad.

From the blog:
Learning Linux &#8230;.

Save yourself many days, weeks, and months of frustration by reading a few primers &#8230; read in order given:

[LIST=1]
[*]    Linux for Windows Users &#8211; ignore the GUI stuff. Working at the command line means having to learn something once. Using the GUI means having to re-learn it every 3 years or so whenever the GUI changes. Be efficient, use the shell/CLI.
[*]    Minimal Ubuntu System maintenance how-to &#8211; patch and backup with just a few other minimal things. Ubuntu mostly runs itself, but &#8230;
[*]    Learn to think the linux way &#8211; stop thinking that point-n-click is the efficient way. It isn&#8217;t. Script and automate things so the results wait for you, not the other way around.
[*]    Tips for New Installations
[*]    Free PDF book on Linux CLI &#8211; READ the first 131pgs, skim the rest over 2-3 hrs to get a taste of possibilities. The early pgs provide background, set expectations, and help to get-your-mind-right for Linux. This is absolutely critical.
[*]    The Linux Documentation Project
[*]    Debian Administrators Guide
[/LIST]
[http://www.linux.com/learn/tutorials/784060-the-complete-beginners-guide-to-linux](http://www.linux.com/learn/tutorials/784060-the-complete-beginners-guide-to-linux) might be useful too.
I saw in another thread you started that someone provide the same link to the free PDF book I like.  "The Linux Command Line" - it really is a good introduction - first 131 pgs - I checked yesterday.

---

### Post by mandarpowale on 2015-03-15
Thanks for your help again. I will learn CLI usiing the free e-book. (the author is William .E .Shotts, right?)


My screen flickers sometimes and It feel as if someone is watching me (remotely taking screenshots of my screens in Ubuntu). Why could that be happening? I'm using opensource drvers that come with Ubuntu for my ASUS HD7750-1GD5-V2.

---


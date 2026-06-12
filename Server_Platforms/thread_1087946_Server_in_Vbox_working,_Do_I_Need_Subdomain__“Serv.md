---
title: "Server in Vbox working, Do I Need Subdomain  “Server Newb”"
date: 2009-03-05
forum: Server Platforms
---

### Post by jeffsa12 on 2009-03-05
I have Ubuntu Server 8.04, LAMP and SSH, running on a virtual PC via xVM VirtualBox 2.1.4 on my Ubuntu 8.04 desktop. I'm aware the following is not “the right way” to setup a server but I installed ubuntu-desktop, and Webmin 1.45 to get familiar with Webmin, and get the fundamentals on how LAMP works before I ditch the GUI.  I did take the time to remove all the apps I didn't need from the ubuntu-desktop for server. I installed VBox additions. I setup a virtual network card with it's own address on my home network. I have an ADSL modem/router, port forwarded port 80. My ISP doesn't block it. All is good.....

I found a free web page template, edited and installed it it the /var/www file and WOW......I had a “That Was Easy” moment.....

I had a Yahoo web page, and used Yahoo to forward my jeffstory.org URL to my home server.

Now I'm beginning to realize how much I DON”T know about all this. I don't even know the terminology so that I can research what I want to do. 

The more I look, the more confusing...DNS, bind9, nameserver, subdomain ....HTML, CSS, Java, Flash.....MySql, database server, database manager...... Python, PHP........and Security.......Where should I start???

My first question is how do I add  pages(?) to my web page? As in if you go to  jeffstory.org, and I want to direct people to additional pages such as  jeffstory.org/morestuff , or  jeffstory.org/coolstuff, etc?

My template had links to other URL”s , and how that works is straight forward. However, this issue has me confused.

I could also use a good source of all that I need to know, but start at a BASIC level that I can build on.

---

### Post by jeffsa12 on 2009-03-05
Wow....

It sure seeme like someone here would be able to at least point me in the right direction!?!? I see by the other posts there are a lot of sharp network / Apache admin's and others here.

So **how about a recomendation on how to get some help here** then???
Am I doing something wrong in the way I ask for help?? Perhaps it's my Desktop and GUI use?? If I thought I could possibly do this without it, I would have, and I realize the benifits of not having a Gnome desktop installed...

---

### Post by jeffsa12 on 2009-03-06
**_anyone??_**

---

### Post by infallible on 2009-03-07
I'm in the same boat, jeff. I think I'm just goint to start buying books. The best advice you'll get is to read the manual; the official sites for Apache and mySQL have been very helpful, as have the many great tutorials and explanatory posts on the ubuntu forums. I'll admit that it's very comforting to have a personal dialogue to walk you through problems that you encounter, but it is much more satisfying for one to learn and understand for oneself.

ubuntu's apache2 web server will serve the site you place in /var/www/ 
if you put all of the files from your yahoo web page in that folder, it should work.

---

### Post by jeffsa12 on 2009-03-07
Thanks infallible,

Yea, as I said, I already have a functional webpage, jeffstory.org on my virtual server that works fine, so I already figured out what you are saying.



 What my question is and I can't figure out is I want to add "pages" to it so I guess it would be a website then?

**EXAMPLE:**

[http://jeffstory.org](http://jeffstory.org) takes you to my webpage.

I would like to add subdirectories with different content within [http://jeffstory.org](http://jeffstory.org)

Such as [http://jeffstory.org/secondpage.html](http://jeffstory.org/secondpage.html) would take you to a similar looking page with different text, and have the same link buttons to either return to the home page, or go to say thirdpage, etc, etc.


I have active "links" to completly different websites such as ubuntu.com, but I want to add active links to my own, additional pages.

---

### Post by infallible on 2009-03-07
I don't know if i can help, because I don't understand your yahoo situation...

You already have what you call "active links" on the left of the page, in this format:

<li><a href="http://en.wikipedia.org/wiki/Linux">Linux</a></li>

so i'm guessing you understand HOW to link, and that you know index.html in the folder specified in your virtual server config loads by default. I'll assume the path as the default, /var/www/
If you copy your index file, ```
sudo cp /var/www/index.html /var/www/otherpage.html
``` and edit the body to leave the basic format but change the content, you'll have a page that can be linked to using <a href="otherpage.html"> The links work relative to the root folder for the site. images are linked the same way, as in <img src="images/jeffy.jpg>

You seem up to speed with your needs in regards to the LAMP situation. the info at [http://www.w3schools.com]("http://www.w3schools.com") are helping me with the html stuff like this, check it out.

---

### Post by jeffsa12 on 2009-03-07
"I had a Yahoo web page, and used Yahoo to forward my jeffstory.org URL to my home server."

I filled out a free Yahoo web page template at 
[http://smallbusiness.yahoo.com/webhosting/](http://smallbusiness.yahoo.com/webhosting/) 


And bought a domain through Yahoo that has the option of domain forwarding at
[http://smallbusiness.yahoo.com/domains/](http://smallbusiness.yahoo.com/domains/)

After I set up a server at home, I just forwarded the URL to my IP.
I'm not sure if this is causing my problems. I think I have tried what you are saying and many slight variations to it, but want to try again, closely following your directions next time.

Uuum...I really don't have a handle on the whole LAMP server thing yet, I think I just got lucky...HA HA

Thanks again!!

---

### Post by volkswagner on 2009-03-08
Jeff,

I would start simple, while it is nice to have a flashy site, you won't learn much if you skip the basics.

I would complete the following tutor.
[http://www.pagetutor.com/html_tutor/index.html](http://www.pagetutor.com/html_tutor/index.html)

Then download a free template from somewhere like opendesigns.org.

You can download it to your desktop and edit it.  then upload the entire file to /var/www on your server.

Your new index.html file will be overwritten upon upload.

You could also create a subdomain and an addition virtual host for this work as not to upset your current page.

For setting up vhosts look here.

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

### Post by o891 on 2009-03-08
> **jeffsa12 said:**
> "I had a Yahoo web page, and used Yahoo to forward my jeffstory.org URL to my home server."

I filled out a free Yahoo web page template at 
[http://smallbusiness.yahoo.com/webhosting/](http://smallbusiness.yahoo.com/webhosting/) 


And bought a domain through Yahoo that has the option of domain forwarding at
[http://smallbusiness.yahoo.com/domains/](http://smallbusiness.yahoo.com/domains/)

After I set up a server at home, I just forwarded the URL to my IP.
I'm not sure if this is causing my problems. I think I have tried what you are saying and many slight variations to it, but want to try again, closely following your directions next time.

Uuum...I really don't have a handle on the whole LAMP server thing yet, I think I just got lucky...HA HA

Thanks again!!


Hi,

well I am not exactly sure if I understand what you would like to do...

But from what I understand you want to learn the basics of web programming and web hosting. Well I am also just getting into linux hosting as well (Ubuntu Intrepid Server), but from past experience I think that it is really important to initially focus on a few tasks, and once you get those right you get onto the other things.

I suppose that if you are going to be doing some website programming you should know the basics of html and even better some php or some other server-sided scripting language.

Then after you can do that, links, some css, etc I would get into the hosting thing (unless you are going to be doing php you don't even need a server for the time being).

Once you have a good grasp on how websites work it will be much easier for you to understand what a server should do.

Well anyway that just my opinion! If you have any precise questions, I will try to answer them!
Oliver

[EDIT: And I wouldn't ever start with templates...it is much easier to learn when you are writing the stuff yourself, as opposed to editing templates you dont understand or copying/pasting code you dont understand.]

---

### Post by hyper_ch on 2009-03-08
do you have a static IP and how do you connect to the inet?

---

### Post by jeffsa12 on 2009-03-08
I'd like to thank everyone for the help and replies. I got a lot of good ideas from all you. I also was able to solve my issues with the help from all of you.

I have two similar threads started here (my bad). My first thread kinda went down without a reply after the first day... and I got impatient, tried to edit the title, and ended up posting another one...I was  caught up in the moment of seeing my first self served web page working. I wanted to build upon it!!! It was relatively easy to get my virtual server functioning enough to get to that point. It was then, that I realized how much I didn't know.

It's no wonder I couldn't find an answer, before the forum here, because I was off looking for a solution in the configuration of the server!! I didn't know basic HTML!!! Thanks to Infallible's reply and reference to w3school, I figured out what was going on. He along with others, gave locations to some great reference material. 

**I spent a bit of time on [http://www.w3schools.com/](http://www.w3schools.com/) going over, and learning some basic HTML, XHTML and CSS. A great source for any other server, website Newb's reading this.** I see things there that I didn't realize were used for website code and implementation. The pieces of the puzzle are slowly coming together....although very slowly!!!

It's time for me to slow down now and learn LAMP and website development with the new direction my computer interests are going!!! I believe mastering all this would take many years if I stay interested and take it to that level!!!

I became intrigued with Linux, and particularly MySQL once I learned of it from my past girlfriends brother. She told me her rich brother, Larry sold the software. When I met him and we talked about what he sold, I learned he did more than just sell software. To be honest, I really didn't completely understand as he tried to explain it. Dazed and confused would probably better describe it Ha ha. I had never used anything but Windows then, and clearly we had too many beers for me to grasp it. I have to say though, Larry's sis is a compassionate and beautiful woman!! She was the love of my life for three years. 

It was after we split, looking for something to fill the void, that I was compelled to learn to use Linux, which led me to a LAMP server. During this time, I also learned more about her brother, Larry Stefonic (former MySQL VP)!!! Now just a few years later, I would have never thought back then that I'd have a LAMP server on my computer at home with MySQL!!!

---


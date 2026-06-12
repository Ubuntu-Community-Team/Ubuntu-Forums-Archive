---
title: "missing httpd.conf file?"
date: 2013-02-16
forum: Server Platforms
---

### Post by whudson1980 on 2013-02-16
Hi everyone. I'm new to the forum, so please excuse if I'm not posting in the correct spot. BTW, I'm a WIndows Server Admin, with limited Apache/Ubuntu server knowledge. 
 
So, I work in a company that is upgrading an Exchange server. In the event that something goes terribly wrong, I wanted to set up a very simple site to guide users on what needs to be done on their end.
 
I followed directions at: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) and was able to quickly set up an Ubuntu server. Works great! I just modified the /var/www/index.html to display what I want, and done! With a quick entry in the company DNS server, my site SystemStatus now works and everyone sees my page. 
 
The problem is now that other sites (satelitte offices) liked the idea, and wanted to add their info to this intranet site. So I simply created links to [http://(sitename)/site2.html](http://(sitename)/site2.html) and put the site2.html in the /var/www folder. Didn't work. After some research, I found that you have to change the DocumentRoot. But the httpd.conf file is nowhere to be found. I"m at a loss. Every possible location this dumb file is suppsed to be ( according to web site searching ) its not. 
 
The site is up perfectly. I just want to add some links. Is there a way to view the DOcumentROot from the command line? ANy ideas on what needs to be done? HELP!!! :(:confused:

---

### Post by Doug S on 2013-02-16
Hi, and welcome to Ubuntu forums.
 
The file /etc/apache2/httpd.conf is either empty or, if your version of Ubuntu is recent enough, non-existent. It has been many versions ago since it was not used anymore, but still required for legacy reasons. As of 12.10 (I think) it isn't there anymore.
 
What you want to do is now handled in the /etc/apache2 subdirectores.
 
A good reference is the [Ubuntu server guide]("https://help.ubuntu.com/12.10/serverguide/index.html"). (I prefer the [PDF]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") version). (The links are to the 12.10 version, but 12.04 is also available)

---

### Post by whudson1980 on 2013-02-16
Thank you! Very helpful, but my initial problem remains. So, in 12.10, the default DocumentRoot is /var/www, and my INDEX.HTML file pulls up perfectly when using the FQDN. So, my question is, why can't I add a single link within index.html to DIRECTIONS.HTML with the file located in /var/www? THe file is there, but the link does not work. If I try to manually go to [http://(FQDN)/directions.html](http://(FQDN)/directions.html) is doesn't work either, yet the file is present in /var/www. 
 
I didn't think something so simple (creating one page with one link) would be so tedious. :(

---

### Post by Doug S on 2013-02-16
I didn't comment on the other part the OP (Original Post), because I didn't understand your issue. I still don't. From what I think I understand from your description (which must be wrong), what you are trying to do should be trivial. Perhaps another reader can help, as I must be dense on this one. You could help by looking at /var/log/apache2/error.log and maybe posting here what is says. The only other thing I can think of is that you wrote "DIRECTIONS.HTML" and [http://(FQDN)/directions.html](http://(FQDN)/directions.html) which are two different files, as linux is case sensitive.
 
Edit: Oh, I just thought, maybe it is a permissions issue and maybe directions.html doesn't have the right settings. The error log should show the root issue.

---

### Post by whudson1980 on 2013-02-16
My apologies, sorry for not being descriptive enough. Here are the details.
 
I created the ubuntu/apache server as specified in the above link using 12.10. I gave the machine a static IP address, and directed our internet DNS server to resolve the name SystemStatus to this IP address. WIth that being said when users ( internal only, not external ) go to [http://SystemStatus](http://SystemStatus), they get the "IT WORKS!!" default page. I found this html file called index.html and edited it to display what I want. That file was located in /var/www. So now, users who access the [http://SystemStatus](http://SystemStatus) get my page, and it works perfectly. BUT. . . 
 
WIthin the index.html file, I added a hyperlink thats says: "New Jersey = FOr you location, click HERE for directions what needs to be done." So the "HERE" hyperlink points to [http://SystemStatus/NJ.html](http://SystemStatus/NJ.html). So I added a second HTML file within the /var/www folder called NJ.html, and the link doesn't work. When users click on the link, they get page cannot be displayed.

---

### Post by Doug S on 2013-02-16
At this point, I can only suggest what I would be doing next. As mentioned in my previous post, look at the log files in /var/log/apache2 , both error.log and access.log. What I am wondering is if the file is even accessed or attempted to be accessed and/or any other useful information. If there is not even an attempt, then the problem is somewhere else, like maybe in the absolute address lookup for the link.
 
I would also try a relative link, just as a test. I.E.```

... For your location, click <A HREF="http://SystemStatus/NJ.html">here (absolute)</A> or <A HREF="./NJ.html">here (relative)</A><BR>
```

---

### Post by gordintoronto on 2013-02-16
Even better, HREF="NJ.html"

@whudson: Every time I mix upper and lower case in file names, I get it wrong. I suggest sticking to all lower case.

---

### Post by sandyd on 2013-02-16
> **whudson1980 said:**
> My apologies, sorry for not being descriptive enough. Here are the details.
 
I created the ubuntu/apache server as specified in the above link using 12.10. I gave the machine a static IP address, and directed our internet DNS server to resolve the name SystemStatus to this IP address. WIth that being said when users ( internal only, not external ) go to [http://SystemStatus](http://SystemStatus), they get the "IT WORKS!!" default page. I found this html file called index.html and edited it to display what I want. That file was located in /var/www. So now, users who access the [http://SystemStatus](http://SystemStatus) get my page, and it works perfectly. BUT. . . 
 
WIthin the index.html file, I added a hyperlink thats says: "New Jersey = FOr you location, click HERE for directions what needs to be done." So the "HERE" hyperlink points to [http://SystemStatus/NJ.html](http://SystemStatus/NJ.html). So I added a second HTML file within the /var/www folder called NJ.html, and the link doesn't work. When users click on the link, they get page cannot be displayed.

Does NJ.html have the correct permissions for apache to read it? 

Should at least have read permissions for 'others'

drwxr--r--

---


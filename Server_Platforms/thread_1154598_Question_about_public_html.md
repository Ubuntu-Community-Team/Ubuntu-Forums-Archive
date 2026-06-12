---
title: "Question about public_html"
date: 2009-05-09
forum: Server Platforms
---

### Post by Lakeside5 on 2009-05-09
Guess I'm missing one more step to upload my web site 'up there'.  I am using Hardy Heron server 8.04, and Filezilla. I have Joomla intalled in var/www (can see it on localhost, a real website) and can upload files to var/www with filezilla, but I think they are supposed to be uploaded to public_html, but I dont' seem to have that directory.  I briefly had free hosting before, when I uploaded one file (test.html) to the public_html directory that seemed to be there, and that is the web page I currently see when going to my web address. But I can't get rid of that page, or upload Joomla to it- I can't find public_html with my own server. Am I supposed to create that directory somewhere? thanks for any help.

---

### Post by ad_267 on 2009-05-09
No, you shouldn't have to put your files in a public_html directory, that's just how some web hosts have set up their hosting. You can access the website fine at [http://localhost/](http://localhost/) though can't you? So what's the problem?

---

### Post by Lakeside5 on 2009-05-09
Yes I can see my website (Joomla) at localhost. The website files are in var/www so I should see it at my web address if my server is working right shouldn't I? I suspect it isn't then, even though: domain registered at GoDaddy, where I've forwarded my domain, and am using their nameservers, my router has ports forwarded correctly, etc. A strange thing, if I type in 192,168.1.1/index.html, it redirects me to 000webhost.com (where I was temporarily hosted, and uploaded the 'test.html' with, that I see when visiting my web address.

---

### Post by Lakeside5 on 2009-05-10
Well I'm quite new to this and just stumbling through it, I would like to get rid of 000webhost on here all together, and I don't know why I'm getting redirected to it. I thought I had done everything right, sigh

---

### Post by ad_267 on 2009-05-10
I would talk to Godaddy and see if they can help you out, it sounds like an issue with the DNS to me. Also, if you've only just changed the DNS settings these can take a while to take effect.

Do you have a /var/www/index.html file? I would have thought that Joomla used an index.php file. What happens if you go to 192.168.1.1/index.php?

---

### Post by Lakeside5 on 2009-05-10
When I type 192.168.1.1/index.php  get 'Bad request' Error 404 not found'
I  entered the nameservers from GoDaddy (ns51dommaincontrol.com, and  ns52....), and wondering if I can use their nameservers, and I am not paying them for hosting, just for a domain name. Now I don't know what's going on, it's worse than ever, when I type in sasswebs.com, I either get page not found, or I get redirected to my gmail page. hmmmm.

---

### Post by Lakeside5 on 2009-05-13
I took your advice and talked to GoDaddy and they were good about helping me. I'm hoping I have finally understood, because now when I use a site checker and type in my url which is  [www.sasswebs.com](www.sasswebs.com)  it seems to go to my homepage, but maybe only I am still seeing that..
*edit* It seems to be sorking now (knock wood) thanks to the great help from this forum and from GoDaddy.  At least, my friends say they can see it :)

---


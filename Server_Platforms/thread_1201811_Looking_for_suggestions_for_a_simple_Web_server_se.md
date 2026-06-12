---
title: "Looking for suggestions for a simple Web server setup!"
date: 2009-07-01
forum: Server Platforms
---

### Post by rmflagg on 2009-07-01
Hi Everyone,

   This started out as another question about Nginx, but I think that I should be asking a different set of questions.

   Here is what I need to do, and this is *ALL* that I need it to do: I need an HTTP server to serve *one* page. That page will run a Bash script and then display a single JPG image that the script creates. I don't need it to do ANYTHING else. Period.

   Now I must admit that when I start reading about setting up an Apache server, my eyes glaze over with a LOT of stuff that I don't understand and what I do understand, is unnecessary to my goal.  
   I also tried about a dozen different "tutorials" about setting up Nginx with no luck

   I am not a complete noob, but I have *zero* experience in setting up a web server.  What I am looking for is: Suggestions as to what server setup would be best(simple!) and a little help when it comes to setting it up. 

   The server is running 8.04.

   I am looking forward to your suggestions.

Thanks,
RMFLagg

---

### Post by v3xtra on 2009-07-01
What are you asking for?  Do you need help understanding how to set up Apache to even host a page?  Or do you need help with your bash script that will actually display the jpg?

If you just install apache2, it should work out of the box perfectly by going to [http://localhost](http://localhost) .  It should say "It Works!" in the browser, and the main files are in /var/www/ for your website.  There should be an index.html file in /var/www/ that you will be wanting to edit to your specifications.  If you want the outside world to see your page, you will need to forward the ports to your computer through your router ( assuming you have one ), which you should google search how to do for your router.  All you'll need to forward is port 80, as that is the HTTP port.

You also may want to get a domain name or a free domain name, such as DynDNS.org, which allows you to have a generic domain name for your computer, so that the outside world can connect to that instead of an IP address.

As for the script, I haven't a clue and don't really know if basic HTML will even allow you to do that, you may have to go with another language such as PHP or Python, but someone may chime in and give you some insight on that part later.

---

### Post by HermanAB on 2009-07-01
Howdy,

there are extremely simple web servers for use in embedded systems.

However installing Apache is not difficult if you use the Ubuntu wizard that comes with the server version.

---

### Post by juancarlospaco on 2009-07-01
**python -m SimpleHTTPServer**

im just jocking, the people above are right :)

---

### Post by rmflagg on 2009-07-01
[QUOTE=v3xtra;7547261]What are you asking for?  Do you need help understanding how to set up Apache to even host a page?  Or do you need help with your bash script that will actually display the jpg?

   Good question!  Sorry that I didn't explain that better.

   I need help setting up Apache and(after doing further research) enable PHP.  The bash script that is going to be run is done.  I just need the web server to serve, to the world, one page that has a PHP command and then display an image that will be created by the Bash script.

   Everything else, the DynDNS, etc is all take care of.

Thanks,
RMF

---

### Post by Cheesemill on 2009-07-02
Just do a:
```
apt-get install lamp-server^
```

and then replace /var/www/index.html with your web-page.
Job done :)

---

### Post by dbrine on 2009-07-02
Is the index.html file protected (permissions)? I tried to overwrite mine if a new one and I got permission denied?

---

### Post by rmflagg on 2009-07-03
> **Cheesemill said:**
> Just do a:
```
apt-get install lamp-server^
```

and then replace /var/www/index.html with your web-page.
Job done :)

Well, it seems to be working and it should do the job, it just seems like smashing a fly with a sledge! ;)

Thanks,
RMF

---

### Post by Cheesemill on 2009-07-03
> **rmflagg said:**
> Well, it seems to be working and it should do the job, it just seems like smashing a fly with a sledge! ;)

Thanks,
RMF

You did ask for simple to set up!!

---

### Post by cybergalvez on 2009-07-03
> **rmflagg said:**
> Well, it seems to be working and it should do the job, it just seems like smashing a fly with a sledge! ;)

Thanks,
RMF

true, if all you need is simple html, and some php support there are lighter webservers such as nginx or lighttd which will also do what you want use a smaller footprint then apache

---

### Post by tuskenraider on 2009-07-03
on my home server i have a 600k server program running(as a service even)... you double click the program and badabing you have a webserver running. 

its called HFS. 
[http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/)

and its free open source and has a very very active community. 

enjoy

tusken

---

### Post by rmflagg on 2009-07-06
> **tuskenraider said:**
> on my home server i have a 600k server program running(as a service even)... you double click the program and badabing you have a webserver running. 

its called HFS. 
[http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/)

and its free open source and has a very very active community. 

enjoy

tusken

Uhhh...isn't this a Windows-only program? You do know that this is an Ubuntu *Linux* forum, right?

---

### Post by tuskenraider on 2009-07-06
> **rmflagg said:**
> Uhhh...isn't this a Windows-only program? You do know that this is an Ubuntu *Linux* forum, right?

ZOMG what?? Ubuntu isnt a Microsoft product??? OH HOLY CRAP! ive been mislead....

1... yes your right... this is an ubuntu linux forum. 
2... I know it works with ubuntu in wine.
3... There are people in the world...some even on this forum that have a windows box at home...  it happens. sorry.

tusken  

p.s
Just so everyone knows....  the HFS program i suggested in an earlier post, WILL WORK with wine in ubuntu. See also codeweavers...

---

### Post by hendoc on 2009-10-09
I use HFS, which is Http File Server. It is a Windows application that runs perfectly on Wine because it does not install. It runs on the desktop and requires no tweaking of Wine. It could not be easier to use. It supports encryption, virtual files or real files. Just Google HFS.

---


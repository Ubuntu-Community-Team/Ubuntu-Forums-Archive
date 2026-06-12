---
title: "Installed Nginx on an Ubuntu Hardy Slice"
date: 2009-12-14
forum: Server Platforms
---

### Post by ex-para on 2009-12-14
I have installed Nginx on an Ubuntu Hardy Slice using the 'aptitude' package manager so how do I  upload a website to this server.
Any answers please.

---

### Post by BkkBonanza on 2009-12-14
Not sure what you're wanting here. You upload files the same way you would for any other purpose. I prefer to use rsync over ssh. But it depends on what you're familiar with. You could use sftp perhaps.

Nginx is not different this way than using apache. You put your files in some directory, perhaps /var/www/mysite for example and then alter the nginx.conf file for your site's details.

Maybe you can be more specific about what you want to know...

---

### Post by ex-para on 2009-12-14
> **BkkBonaza said:**
> Not sure what you're wanting here. You upload files the same way you would for any other purpose. I prefer to use rsync over ssh. But it depends on what you're familiar with. You could use sftp perhaps.

Nginx is not different this way than using apache. You put your files in some directory, perhaps /var/www/mysite for example and then alter the nginx.conf file for your site's details.

Maybe you can be more specific about what you want to know...

Thanks for the reply, I really know nothing at all about servers or uploading files to a server. I have done it in the past using ftp in windows but I have forgot how I did it as it is some time ago. Any way will do just as long as I can put the sight on the server and some instructions on how to do it.

---

### Post by BkkBonanza on 2009-12-14
So, starting from basics. How do you connect to the server now? 
You probably use ssh or if not then getting that going would be a start.
By "Slice" do you mean a VPS account hosted in some data center?
And are you connecting to it from Ubuntu/Linux or Windows at your end?

---

### Post by ex-para on 2009-12-14
> **BkkBonaza said:**
> So, starting from basics. How do you connect to the server now? 
You probably use ssh or if not then getting that going would be a start.
By "Slice" do you mean a VPS account hosted in some data center?
And are you connecting to it from Ubuntu/Linux or Windows at your end?

I am not connecting to any server so using nothing yet, Ubuntu Hardy Slice is the name of what I    downloaded and the server is called Nginx, can be seen here nginx Web Server Tutorials .
I am using ubuntu 8.04

---

### Post by BkkBonanza on 2009-12-14
I'm very familiar with Nginx. I've used it on my servers for several years now instead of Apache and love it (which is why I tried to help here).

Are you running Nginx on your local machine then? 
And you want to set up a website on it for test purposes? 

If you are sitting at the machine then obviously you don't need to connect. Just open a terminal and type or use the file manager.

---

### Post by ex-para on 2009-12-14
> **BkkBonaza said:**
> I'm very familiar with Nginx. I've used it on my servers for several years now instead of Apache and love it (which is why I tried to help here).

Are you running Nginx on your local machine then? 
And you want to set up a website on it for test purposes? 

If you are sitting at the machine then obviously you don't need to connect. Just open a terminal and type or use the file manager.

I was not but I am now and nginix is on the computer. I thought it was a server to run a website from, not just for tests but I am now at the machine.

---

### Post by BkkBonanza on 2009-12-14
Yes. absolutely can run real web sites using Nginx. Wikipedia uses it, for example. Just that a home machine is often used for testing rather than really serving web sites. Depends on traffic and connection quality.

So, if Nginx is up and running then you should have a test page shown if you browse to "localhost".

---

### Post by ex-para on 2009-12-14
> **BkkBonaza said:**
> Yes. absolutely can run real web sites using Nginx. Wikipedia uses it, for example. Just that a home machine is often used for testing rather than really serving web sites. Depends on traffic and connection quality.

So, if Nginx is up and running then you should have a test page shown if you browse to "localhost".

Yes its says welcome to nginx and 50xhtml in /var/www/

---

### Post by BkkBonanza on 2009-12-14
Good. So to get your site going you should add a directory and put your web files there. Then modify /etc/nginx/nginx.conf to have a new section for your web site.
eg.
put files in /var/www/mysite

and add config like this into nginx.conf 

```
server {
	server_name mysite.com;
	root /var/www/mysite;
	access_log  /var/log/www/mysite.log  main;
    	location ~ \.php$ { fastcgi_pass 127.0.0.1:9000; include fastcgi_params; }
    }
```

Only add the "location" line above if you have php installed and configured. That's another whole subject. The main thing is this section tells nginx to recognize a domain and where to find it's files. You can get more fancy and complicated but this basic chunk of code can be copied/pasted in there for each site you want to serve.

You may also remove the section for the test/demo page as you likely don't want it now.

After editing use this command to test the config,

/usr/local/sbin/nginx -t  

And only if good then this command to reload the config and make it active,

kill -HUP `cat /var/run/nginx.pid`


*Note - any path I give here could be different on your server.

---

### Post by ex-para on 2009-12-15
Again thanks for the reply, I have not done it yet but I am reading the message to make sure I get it right and as soon as I have done it I will let you know of the result.

---

### Post by ex-para on 2009-12-15
server {
        server_name [www.barrieb.co.uk;](www.barrieb.co.uk;)
        root /var/www/mysite;
        access_log  /var/log/www/mysite.log  main;  }
 
    }
I have soon got in to trouble.
I tried to put above in to nginx.conf but I don't have permissions so could not save it.
Are my web files the contents of the website like the source.
The added directory will be in new folder and called /var/www/mysite is that correct, and what else will be in the folder and I take it the folder will be in www?

---

### Post by BkkBonanza on 2009-12-15
The files you put in /var/www/mysite would be index.html and others forming the content of the site. You can name it anything you like that makes sense. I just used mysite as an example but it may make more sense as /var/www/barrieb. The actual name isn't important except that the same name is used in the nginx.conf file.

You will need to use sudo (to get root privilages) to edit nginx.conf. 
eg. sudo nano /etc/nginx/nginx.conf 

I would suggest browsing the examples in the nginx docs and also google nginx for other tutorials that will give you more help on it's config format.

See [wiki.nginx.org//Main]("http://wiki.nginx.org//Main")

---


---
title: "Beginner Questions"
date: 2008-02-08
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-08
I have been using Ubuntu Desktop for a few months and have now tried to use Ubuntu Server in hopes of learning more about servers. So I installed ubuntu server on my computer and am now trying to figure out how to host a web page. I already have a static IP through DynDns.org (Please note I have a free account) and a domain name through GoDaddy.com. I installed LAMP when I installed the server and I have no idea where to go next. The main goal for me is to be able to access a webpage that I'm hosting from outside my own network (which the web page works in the network. Thanks for any help that you can provide.

Holmes89

---

### Post by mikesignguy on 2008-02-08
there are two ( that i know of ) ways to handle this.
i will give you what IMHO is the easiest

1. edit this file

sudo nano /etc/apache2/sites-available/default

there are two lines that have /var/www 
change both to where your website is sitting
2. now restart Apache
 sudo /etc/init.d/apache2 restart

3. goto  http:/localhost
  your website should pop up
if it doesn't it is most likely a permissions thing on the files

4. If you hosting the site locally open the ports in your router
and if the DNS servers are set to your IP you should be all set

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)
caution: just use the last section of this tutorial

---

### Post by Holmes89 on 2008-02-08
Oh, right now I have the temporary website, I want to access that first before I start uploading my own website. I am having an issue connecting to the server in the first place. Does that make a difference

---

### Post by mikesignguy on 2008-02-08
yes

call your hosting company and have them walk you through it... that's what u pay them for
i think the easiest way to upload is filezilla and your hosting company should be familiar with it

---

### Post by Holmes89 on 2008-02-08
Let me try rephrasing my question: I have the default website that comes with Apache, just to have a test until I can connect to it from another network. On the network I can access the website no problem. What do I have to do to my router?

---

### Post by freebeer on 2008-02-08
You should set up the Apache Server with a static IP.  Then forward port 80 in your router to point to the static IP of the Apache Server.

---

### Post by Holmes89 on 2008-02-09
Alright, thanks that worked, I was opening the port in the wrong area. My dumb fault. Hey okay now what do I do? I have a website built and on my thumbdrive, what do I do next to get it off and onto my apache sever? Thanks for all the help, this is a really fun project.

---

### Post by freebeer on 2008-02-09
Sounds like you only need to copy the files over to the appropriate folders.  (/var/www is the default but that can vary depending on what is specified in Apache's config files)

---

### Post by Holmes89 on 2008-02-09
okay now I can only connect once after resetting the router, so what do I do? Also I don't have a GUI so how would I transfer the files without one? (I was told not to install a GUI because it slows things down)

---

### Post by freebeer on 2008-02-10
I'm not too clear on what you mean about connecting only once.  Can you elucidate please?

Without a GUI you'll need to copy them over using the command line:

```

sudo cp /source_directory/files /var/www/

```

(assuming /var/www/ is your base directory for apache2)

---

### Post by Holmes89 on 2008-02-10
Actually never mind I figured that one out. The only issue now is getting the website off of my thumb drive and onto the server. How do I mount my thumbdrive or make it so my server drive can see the files so I can copy them over?

---

### Post by mikesignguy on 2008-02-11
it depends on how u r accessing the server.  You should see about secure shelling into the server from another computer on the network



to answer your question
type 
 mount 

this will tell u where the thumbdrive is located

---


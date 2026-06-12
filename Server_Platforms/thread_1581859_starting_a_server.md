---
title: "starting a server"
date: 2010-09-25
forum: Server Platforms
---

### Post by wallytheaviator on 2010-09-25
This is my first post here, but I have been reading many helpful topics throughout the forums here, I am new to linux and ubuntu. I was out of the country when I decided to try an experiment to see if I could get a server running of my own. Mainly to do VOIP calling oveseas, and to host a few websites at different domain names, I have 4 servers that I got at auction and they now have ubuntu running with gnome interface.
 
I installed apache2 and tried to edit the conf file but i am not sure if it is a router issue a dns or the config.
 
I am trying to figure out how to set the server to hold the domain from a dynamic ip address and also how to create some test page to see if i can acess from the internet.
 
I have purchased some books on the command lines and how ubuntu works, I am understanding it so far, but dont know how to have a directory for the dns request to point to for the site
 
what i want to do with the servers...
 
voip
 
web server for about 4 websites - one is for a volunteer rescue organization, another for a test auction site and 2 portfolio sites
 
remote file access- if possible
 
-----------
 
also on a side note, is it possible to have a message relay from one cell phone or transmit to the server and have it send sms message to cell phones? - this will be used for the rescue group as well.
 
Thanks

---

### Post by lisati on 2010-09-25
For your apache server to be visible from the internet, it is usually necessary for you to set up port forwarding in your router for port 80. The specifics vary depending on the make and model of your router. You might also want to check to see if your router can do the automatic update of your IP address with your choice of DNS provider - doing so can help you avoid the hassle of setting up an update provider.

One way of hosting multiple websites with Apache is through *virtual hosts*

---

### Post by drdos2006 on 2010-09-25
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by wallytheaviator on 2010-10-08
Thanks for the advice and the links, been busy getting things running, but it was very useful.
 
Thanks again

---


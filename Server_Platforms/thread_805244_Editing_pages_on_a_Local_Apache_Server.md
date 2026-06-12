---
title: "Editing pages on a Local Apache Server"
date: 2008-05-23
forum: Server Platforms
---

### Post by Nodestar on 2008-05-23
Hello.
I just installed Apache 2.2.8 on a Hardy Heron Computer. The Server is for local toying with AJAX and PHP. And any other Web Sites I might want to design before taking them to the web. I've spent the last month learning about HTML CSS and Javascript but I'm just starting to learn about PHP, Apache(servers) and Databases.

I'm trying to figure it all out but one thing I can't find any documentation on (probably because it's so simple) is how to edit files inside the root of my Apache Server. What I mean is that I can't change the index.html file inside of the htdocs folder. I can't do this because the folder is located in /usr/local/apache2 which is owned by root. So I can only read files owned by root not modify them.

I don't want to be logged in as root all the time just to work on websites locally. So my question is. How do I change Apache to let me modify their files. Or how do I make a user account with the privileges to modify Apache files but not have all the power of root.

Thanks.

---

### Post by windependence on 2008-05-23
You should have a www user and the files sould be owned by that user and not root. Apache normally sets it up this way unless it has changed since 1.3. 

-Tim

---

### Post by Nodestar on 2008-05-23
Hmmm.. I followed a guide and built from source. Perhaps for my purposes that was a mistake. I'll probably just uninstall and reinstall from the repositories and try again. 
Is the www just a folder or is it an actuall Ubuntu User?

---

### Post by ArrantSquid on 2008-05-24
If you install from the repos you'll be editing files within "/var/www/". Basically if you only want the one site, you're fine, but if not, you'll need to setup Virtual Servers (which is fairly simple using a2ensite and a2dissite). Just remember to do a little menial tasking such as turning off ServerSignature and set the ServerTokens to Prod not Full. You'll have to look into editing your httpd.conf (although you can use the 000-default that ubuntu provides in /etc/apache2/sites-enabled/ it is easier to lock down what you want in httpd.conf). HTH.

Also, when you edit the files in /var/www/ to setup a basic index.html file until you actually have a full site up I would just sudo touch /var/www/index.html  and add in a little test message.

You may want to check out the howtoforge site for the "perfect setup" guide. It's fairly comprehensive and is great to begin with. The newest one is [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) . If you want to use 7.10 then just find that one. They all work about the same. Again. HTH

---

### Post by Nodestar on 2008-05-24
Thanks for the info. I'm reading that guide now. Hopefully I can get this figured out.

---

### Post by Nodestar on 2008-05-24
Small problem. I can't uninstall Apache 2. 
This command line sudo apt-get remove apache2
gives me 
Package apache2 is not installed, so not removed

I checked the Synaptic Package Manager and it says I don't have Apache2 installed. (there are no check marks next to the apache2 packages) 
I downloaded the .tar from the main Apache Site and built it from source. When I navigate to [http://localhost/](http://localhost/) I get the "It Works" page that comes with Apache.
And the files are all there. 

Any other way of uninstalling?

---

### Post by ArrantSquid on 2008-05-24
run
```

make uninstall

```
in the directory you compiled it from. that should work

---


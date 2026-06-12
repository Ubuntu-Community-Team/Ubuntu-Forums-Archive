---
title: "Man, I love it !!!!"
date: 2006-04-24
forum: The Cafe
---

### Post by exkalibur on 2006-04-24
Just finished installing Wordpress on my home server. Set up PHP, MySQL and tweaked Webmin. Then found a template for the Blog, modified it to suit my needs ( had to take a quick crash course on PHP). Started to upload pictures and Gimped them to fit. All this in a couple of evenings.......Without having to run back to my window computer (well, had to read the PHP manual from it while working on the Linux box).

Now, That doesn't sound very extraordinary but....I'm a greenhorn in the linux world and I have to say that I found it very stimulating and fairly easy.....I love this stuff !!

I'm glad Ubuntu and Linux found me. :D

---

### Post by nalmeth on 2006-04-24
No, it is extraordinary!
Great job
Nice to see such instant success and gratification (the warm positive kind!)

---

### Post by Kvark on 2006-04-24
You could get all that installed by typing a single command:
```
sudo apt-get install wordpress webmin webmin-apache apache2 libapache2-mod-php5 php5-common php5-mysql mysql-server
```
After that command is done everything is up and running but you may want to change some settings and restart the servers with your new settings. The only settings I needed to change was which directories apache looked for websites in and the users/passwords in mysql, which took less then 5 minutes.

The only thing left to do after that is to find and modify that template for the blog and gimp+upload the pictures.

But you probably didn't know which packages you needed. So instead of typing that command you would have to open Synaptic Package Manager and search for the keywords "wordpress", "webmin", "apache", "php" and "mysql" one at a time, then mark the checkboxes next to the search results you wanted to install and click apply. I guess this method would take 15mins.

---

### Post by exkalibur on 2006-04-24
Hello Kvark. 
I could have used the quick way (apt-get) but I wanted to have the latest version of wordpress. I also wanted to have the opportunity to do a "manual" install, for learning purposes. Modifying the wordpress template was the more time consumming task. The rest of the install was relatively quick.......

Regards

---


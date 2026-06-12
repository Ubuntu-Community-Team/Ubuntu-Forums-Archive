---
title: "Cannot access new webserver"
date: 2006-11-17
forum: Server Platforms
---

### Post by meyrd on 2006-11-17
I just setup a new webserver using an ubuntu desktop on a fresh lamp install (6.06). I put an index.html in the var/www directory. I use a dyndns account and forward port 80 in my router to my server. When I type in the url I get a window that says "Authentication Required". I type in my username and password for the webserver but it just repeats the "Authentication Required" window over and does not actually connect. It does tell me that I am trying to view the index.html on my ip address, which is the correct ip.

I'm a newbie and I'm confused. ](*,)

---

### Post by DRicher33 on 2006-11-17
Hi there,

Sounds like you have the .htaccess file on..check its contents in /var/www

---

### Post by meyrd on 2006-11-17
Nope the file is not in the /var/www directory

---

### Post by meyrd on 2006-11-17
I also have webmin installed. Should I go to that and config the htaccess file?

---

### Post by meyrd on 2006-11-17
I may have figured it out. I went into webadmin and created an htaccess file and used allow all requests as the config.
I have to go to the town hall to see if I can access from the outside world. I'll post if it fixed it. 
If anyone thinks this is wrong or I should add something to the htaccess file please post.

thanks,

---

### Post by DRicher33 on 2006-11-17
Well htaccess is only used if apache is setup to authorize that way.  What authorization did you setup in apache.  it might be wise to post your conf file from webmin...make sure you take out any info that someone could use to hack you.

---

### Post by meyrd on 2006-11-17
Well that'a why I'm still a noob. Can you give me an idea where I can find, how to set that up. I mostly took the defaults setting up the server and I'm learning as I go. Probably not the best way to do it but I want to learn this and I thoought the best thing I could do was jump in....

---

### Post by meyrd on 2006-11-17
](*,)  too frustrated..... starting over and following the perfect install instructions this time....did not know about them before ](*,) 

New install is done now.........

I think I will just ssh in for now and make changes that way instead of trying to install a gui and other stuff.

maybe by tomorrow I will be able to see my site on the server from outside the lan.:D

---

### Post by meyrd on 2006-11-17
Thank-you for your help!

---


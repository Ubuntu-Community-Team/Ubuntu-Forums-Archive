---
title: "Ubuntu Web Server"
date: 2005-09-16
forum: Server Platforms
---

### Post by sampbar on 2005-09-16
Hi
Im guessing this quesion has been asked millions of times so please dont shout at me for asking it again! I have designed my website in NVU but cant be bothered to pay web hosting fees. Ive got an old computer lieing about which i have installed ubuntu on ( not the server install just normal install). I am completly new to linux and web servers so could some give me any helpful advice.

p.s i have a 512 broadband connection

Thankyou

Sampbar

---

### Post by KingBahamut on 2005-09-16
Phew...ok this is a big one. 

Depends on what you want to do. 

Are you developing your pages primarily in HTML or some close variant? PHP? other? 

Do you want to use and understand databases in your web apps? 

Do you want to use and understand Java and java based developments in your apps? 

Or

Are you just designing cool html based pages with NVU and need a place to drop them so that others online can see them?

---

### Post by philpot on 2005-09-16
For a single website, it's pretty straightforward, although you really need to have a static IP address on your ubuntu server. If you are sure that you have this, simply install Apache (web server software), Webmin + Apache plugin (web server admin software), and you should also have Firestarter installed. All these can be installed via Synaptic.

Webmin needs a little tweaking to get it to work with Apache2, and Firestarter will need to be configured. Both of which an be done very easily.

You should also make sure that your domain name is pointed at your servers IP address.

---

### Post by sampbar on 2005-09-16
[QUOTE=KingBahamut]Phew...ok this is a big one. 

Depends on what you want to do. 

Are you developing your pages primarily in HTML or some close variant? PHP? other? 

Do you want to use and understand databases in your web apps? 

Do you want to use and understand Java and java based developments in your apps? 

Or

Are you just designing cool html based pages with NVU and need a place to drop them so that others online can see them?[/QUOTE]
 My web pages are a bit of everything php html etc. etc. i need a place to drop them but would also like to learn about the other things you mentioned

thanks sampbar

p.s i would also like to use phpbb as my forum

---

### Post by sampbar on 2005-09-16
I would also like to make a password protect membes area but dont know how to any help on that would be appreciated

---

### Post by KingBahamut on 2005-09-16
phpbb , great stuff. 

then apt-get all the nessecary files. 

Crack your fingers, get some coffee and start reading 

[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)
[http://www.php.net/manual/en/](http://www.php.net/manual/en/)

Any other specific questions, let us know. 


phpbb is really easy to setup, run, and maintain once you get apache and php installed. Ive even got one or two custom theme plates if youd like em.

---

### Post by sampbar on 2005-09-16
[QUOTE=KingBahamut]phpbb , great stuff. 

then apt-get all the nessecary files. 

Crack your fingers, get some coffee and start reading 

[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)
[http://www.php.net/manual/en/](http://www.php.net/manual/en/)

Any other specific questions, let us know. 


phpbb is really easy to setup, run, and maintain once you get apache and php installed. Ive even got one or two custom theme plates if youd like em.[/QUOTE]
 i hope you dont mind but ive added you to my icq list please accept me if you dont want to i will understand. anyway do you know of any good ways of making a passowd protected members area?

---

### Post by TheDanMan on 2005-09-16
Personally I recommend you just find a cheap webhost and use them.  There are some that are as little as 3 dollars a month!  And some of those will even give you a free domain name.  I run a webhost however I choose not to disseminate that infomation on forums.  That and I wouldn't be cheap enough for you ;-D

Having a good webhost that does the job of keeping the server secure and making it easy for you to manage databases and upload your files is really worth it.  Look for one with a good control panel.  Most have one, pretty much all are good.  The only one I recommend you stay away from is Helm.

As far as the rest of the information you'd need, I say post when you have more specific questions, trying to cover all information you'd need would require us to write you a book.  Which brings up a good idea.  Go to the library and look for a good book on webdesign.  That should cover most questions you might have.  As you need more specific information you should look for books that cover that area.  And if you just need a little tidbit, post on forums :-D


All that said, GOOD LUCK AND HAVE FUN WITH YOUR SITE!

---


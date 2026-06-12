---
title: "[SOLVED] Website hosting on pc"
date: 2008-04-24
forum: Server Platforms
---

### Post by Zeotronic on 2008-04-24
First off, I have to state that I'm not sure if this is the right category... it sounds like the right one, so *oh well!*

I want to know about hosting web pages and such on my PC (Xubuntu, though I doubt that matters)... first and foremost, how do I do it? I made an attempt once, but things didn't go the way I expected them to (aka I was unsuccessful). Secondly, I know that the option in the network settings for a domain name... is quite literally a domain name! (like google.com) As I understand it there are various things involving the law related to domain names... (that statement probably highlighted my present lack of knowledge related to web hosting) does anyone know of anything I should keep in mind when it comes to domain names? Do I need to worry about a big corporation crashing my party *and* suing me for everything I don't have? (admittedly, I was going to go with something way out of the way, like Arron Bishop did when he named 'Secret Of Ultimate Legendary Fantasy UNLEASHED')

So obviously, I know nothing of web hosting, and I want to know *enough*... could anyone answer my questions or direct me to something for people like myself?

---

### Post by pytheas22 on 2008-04-24
Most ISPs make it hard to host websites from residential connections, if that's what you are trying to do, so the first thing to do would be to check with them to see what the restrictions are.  Unless your PC is directly on the Internet (i.e., not behind a router or firewall), which is not the case in most residential situations, you will also need to deal with that.

As far as domain names go, the name won't work until you register it--until DNS servers around the world learn the domain name and the IP address that it's attached to, no one will be able to resolve it to visit your site.  A domain name is just a way to represent an IP address with words so that it's easier to remember.  google.com stands for the IP address 64.233.187.99, and putting either in your browser's address bar will bring you to Google's site.

Once you've dealt with the things above, it's just a matter of installing a web server and putting web pages in it.  If you use an Apache server, which is probably what you'd do, you just put your web pages in the /var/www directory of your machine.

---

### Post by secondstage on 2008-04-24
(I hoped to get here before pytheas22, or anyone else, did, but here is some more details on how to install apache and other programs)

I just asked the same questions only 2 weeks ago, and I hope that I am of assistance. 

       To start off you need to have your own special IP address, you can check your by going to [this website]("http://whatsmyip.com") It will say BOLDLY what your IP address is, for you will need this later on. Now to install some programs that will allow you to host a folder on your computer. 
Type the following in Terminal

```
sudo apt-get install apache2 php5 php5-cgi php5-cli php5-common php5-mysql
```

       Now to test that everything installed OK, go to firefox and in the address bar, type [http://localhost/](http://localhost/). You should get a page of some sort showing what files are in /var/www/. /var/www is where all of the files that you want to be available to others should be(you will need root when accessing and putting files into this directory). 

       If you are going to use PHP in your web pages here is how to test it to make sure that it works. Just go to Terminal, and type the following
1. ```
sudo gedit /var/www/testphp.php
```
2. Insert the following line
             <?php phpinfo(); echo 'Hello World' ?>

3. Save and exit
4. test it in firefox: [http://localhost/testphp.php](http://localhost/testphp.php)

       Hoping that you have some knowledge of html, you can write a homepage and save in /var/www/ , make sure that you save it as index.html, because that is the file that browsers look for when opening a folder(in this case /var/www/). Go back to firefox and test it by going back to [http://localhost/](http://localhost/) and  seeing if it works. 

       Now here is the fun part, getting your page out into the web so that other people can access it. Remember you IP address, well here is where it comes into play. Go to dyndns.com and sign-up. Then click on services in the top toolbar, next click Dynamic DNS. Go through the process of registering a domain for your ip and allow it a couple of minutes to update. I really don't know how long it takes for them to refresh their database, so FILL ME IN HERE anyone who knows. Once it has entered your domain name, you can phone a friend and get then to go to the domain you chose during the registration. It ought to work. If not then ask your questions here. 



A really hope that this helped. :popcorn:

---


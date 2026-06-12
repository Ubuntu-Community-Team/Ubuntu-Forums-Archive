---
title: "HELP!! New to Ubuntu server 7.04"
date: 2007-11-04
forum: Server Platforms
---

### Post by tbuzz2 on 2007-11-04
Hello reader,
   Well i am a total noob to ubuntu, but i have LAMP set up and running, I have my website/blog set up with  wordpress. I can get to the site from the machine that i used for the ip address, but when i try to get on it from another machine on my network all i get is a page that says INDEX OF/ and when i click on the word blog, i get a page that says firefox cannot establish a connection to the server at localhost. I have been trying to fix for a week and cant figure out were i am going wrong:confused::. Is there any good  sites to help set up servers for the NOOBS? or has anyone had this problem?  Thanks  for any help you can give.
                 tbuzz2

---

### Post by HermanAB on 2007-11-04
Hmm, the best way is to install Mandriva and run the web server wizard:  [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

However, if you are hell bent on doing things the hard way :), then you have to approach the problem in a systematic fashion.  First get your internet connection to work, then worry about Apache.

So confirm that your machine has an IP address, that it resolves in DNS, that you have a default route, that you can do nslookup of a public server like [www.yahoo.com](www.yahoo.com), that your firewall allows port 80 and blocks most everything else, that you can send and receive email, so that your administrator can receive warnings.  Once all of that is working, restart Apache and it will most likely be fine.

Cheers,

H.

---

### Post by tbuzz2 on 2007-11-04
HermanAB,
         Thanks for the reply, sorry if i sound like such a NOOB, but anyways when i click on the [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)  it takes you to an index page, thats exactly what iget when i type in the web page i am trying to get to. I dont know if i did it right but the nslookup said the correct ip address for the machine im using for the web server.

---

### Post by HermanAB on 2007-11-05
Mandriva is distributed in the form of CDs or DVDs.  Updates are distributed online just like Ubuntu, but they try to accommodate people with slow net connections.

Pick a torrent (2008: x86, x64, CD or DVD) and save the little file on that index page on your machine, then join the torrent using ktorrent or azureus. Eventually you'll end up with one or more ISO files.  Burn those to a stack of CDs or a DVD and install.

---

### Post by tbuzz2 on 2007-11-05
Hey thanks, igotta get up for work in a few hours, i'll post what i get tomorrow
PEACE

---

### Post by dantrevino on 2007-11-05
er... mandriva, while a nice distro, is not the answer.

If the web server is working from one host, its working from all, its just your configuration that is the problem.

What do you have in your wordpress configuration for "WordPress address (URL)" and "Blog address (URL)"?

dan

---

### Post by tbuzz2 on 2007-11-05
Well i am hell bent on doing it the hard way [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:, i am trying to teach my self, from about 2 yr. ago being able to get on the internet- NOW i am hooked on learning everything i can about ubuntu!!!
My wordpress URL is [http://ubuserver2.gotdns.com/blog/wordpress](http://ubuserver2.gotdns.com/blog/wordpress)
My blogURL is [http://ubuserver2.gotdns.com](http://ubuserver2.gotdns.com)

Basically i would like to set up a blog/website to try to help noobs like me who would like to accomplish things with ubuntu.
The other thing is i would like to pull up my music and videos wherever i am. I can think of a few more things but i figure this is a good start:)

I have 4 working towers, if someone felt like teaching a noob i would gladly  start from scratch to make a woking web and file server and what ever else you think i should learn
BASICALLY UBUNTU IS MY NEW ADDICTION!!!!!!!!!!     :lolflag:

---

### Post by HermanAB on 2007-11-06
"new addiction"

Be careful, since there is no known cure...

---

### Post by doanut on 2007-11-06
If you can't get to your site from another machine it looks to be a router/firewall issue.

I have done a portscan and ping on your domain and it fails. Check to make sure you have the ports open and that Apache is listening on the correct port. 

Also make sure that your ISP doesn't block port 80 and if it does configure apache to listen on another port ie. 8080

Restart apache and try again.

---

### Post by tbuzz2 on 2007-11-06
> **HermanAB said:**
> "new addiction"

Be careful, since there is no known cure...

Do you mean there are know UA (Ubuntu Anonymous) meetings?
My wife is going to be mad :)

---

### Post by tbuzz2 on 2007-11-06
> **doanut said:**
> If you can't get to your site from another machine it looks to be a router/firewall issue.

I have done a portscan and ping on your domain and it fails. Check to make sure you have the ports open and that Apache is listening on the correct port. 

Also make sure that your ISP doesn't block port 80 and if it does configure apache to listen on another port ie. 8080

Restart apache and try again.

doanut,
 Thanks I will talk to isp today from work and look into apache a little deeper concerning open ports. Now here is a strange thing when i click on the my word press URL that i wrote in an earlier post w/ my windows machine it gives me a cannot find local host page, now i have a laptop(running vista :( ) that ijust hooked up to my wireless router yesterday and when i pull up Ubuntu forum and find my post with the wordpress URL and click on it it sends me to my website :confused:

---


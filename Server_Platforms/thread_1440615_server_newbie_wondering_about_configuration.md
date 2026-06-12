---
title: "server newbie wondering about configuration"
date: 2010-03-27
forum: Server Platforms
---

### Post by adgators89 on 2010-03-27
Ok, some of you may have seen my recent posts on inquiries about servers, well I have a new idea as my brain is always spinning...well I'm not sure this is possible, but could I run 1 server that can work as a LAMP, mail server, and a LTSP?

if not, i am also very open to suggestions

---

### Post by new_tolinux on 2010-03-27
It should not be impossible, because LTSP, mail and web shouldn't bite each other.

But it depends also on the amount of "use".
200.000 emails per day + 1.000.000 pagehits per day + a bunch of simultatious users = a bad idea for a single machine.

---

### Post by dudumomo on 2010-03-27
Yes you can do all these on the same machine.
But as told new_tolinux, it depends on your need. (What are they ?)

---

### Post by Iker Etxebarria on 2010-03-27
Yes that's possible. But it's always very interesting to have another machine to backup your entire system. How much time could you affort to be without a mail server? You have to be ready for a hardware crash or any other situation.

---

### Post by adgators89 on 2010-03-27
Well, It would be a setup for a school, so the mail server would most likely be more active and the web server as well, maybe a server for those and then a seperate one for  LTSP if that is recommended.  Next I would have to look into how to set them up as well - since I am server illiterate at this point (trying to learn everything possible with everyone's help on here)  I have  adomain name, so that is a start, I was looking to start hosting our school website in house and also the school email accounts with all of the staff.  Is this possible or is it simply easier to just go with google gmail? and a hosting site like bluehost

---

### Post by koenn on 2010-03-28
> **adgators89 said:**
> staff.  Is this possible or is it simply easier to just go with google gmail? and a hosting site like bluehost
of course it's easier to use gmail : you don't need to set up anything.

---

### Post by new_tolinux on 2010-03-28
> **adgators89 said:**
> Well, It would be a setup for a school, so the mail server would most likely be more active and the web server as well, maybe a server for those and then a seperate one for  LTSP if that is recommended.  Next I would have to look into how to set them up as well - since I am server illiterate at this point (trying to learn everything possible with everyone's help on here)  I have  adomain name, so that is a start, I was looking to start hosting our school website in house and also the school email accounts with all of the staff.
If not for home/test-purposes I would never recommend LTSP together with mail/web on a single machine.
If there's not to many mail (let's say max. 500 accounts/20 mails per day per account) and you're happy with the speed that your webserver serves the pages: do it together on one machine. If you find it's to slow to meet the requirements: split up mail & web to 2 machines also.
> **adgators89 said:**
> Is this possible or is it simply easier to just go with google gmail? and a hosting site like bluehost
Like koenn said. Let someone else do the "job" (maintain servers) is always the more easy way.

For LTSP: don't use it myself, so can't be of any help there.
For mail: long time since I did it on Windows, so can't be of any help there
For webserver: I use apache, php and mysql, so maybe I can answer some questions there. A good start would be installing it from the repositories. There are lots of tutorials around how to get certain things done, some good, some worse, but always worth a google-query.

---

### Post by adgators89 on 2010-03-28
right now I am using Ubuntu 9.10 desktop, so I was looking to use 10.04 server when it came out for the web server and/or mail server.  I can possibly run three servers, if they can be run by 2.8ghz 2gb machines.  I would have to learn a ton about each and how to set them up, but think it might be worth the time investing and if nothing else I will gain some more knowledge about the server world :)

I guess first would be the web server.  My school owns the domain name and I know the ip in which our school is assigned and the internal ip network as well.  so I guess starting with a web server would be the best option.  Once I set up the server (which of course I would need help doing) I would like to setup accounts where the teachers could log in via FTP and edit their web pages only (so I guess restrict their access to only tha tfolder (is this possible?

---

### Post by drdos2006 on 2010-03-28
Check this HOW-TO out. Very thorough.

Latest versions are available at homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by expatCM on 2010-03-29
Thank you drdos2006 for posting the link to woodel.com.  I just clicked and found that there is a 579 page pdf explaining in great detail how to set up a server.

I think I have been trying to find a guide like this for a LONG time.

Thanks again for making the post.

---

### Post by HermanAB on 2010-03-29
Howdy,

Your biggest problem will be the spam load of the mail server.  If you use spamcop and spamhaus black lists and an efficient mail server system such as Citadel, then it should be OK.

---

### Post by adgators89 on 2010-03-29
are those spam and citadel programs open-source as well?  I told you I was a newbie :)

---


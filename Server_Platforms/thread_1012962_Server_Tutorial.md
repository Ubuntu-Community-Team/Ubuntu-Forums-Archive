---
title: "Server Tutorial"
date: 2008-12-16
forum: Server Platforms
---

### Post by andrew_g on 2008-12-16
Hi, is there a beginners users guide for the ubuntu server? - Thanks

---

### Post by jdpearson on 2008-12-16
I too am looking for recommendations on a good, **physical**, book to walk me through Ubuntu Server.  I'm not new to computers, just Linux.  I would need something that would also discuss how to integrate Linux w/ my Win. clients/servers.

Thanks.

---

### Post by fjgaude on 2008-12-16
This link should get you started:

[http://www.unix-tutorials.com/go.php?id=3886](http://www.unix-tutorials.com/go.php?id=3886)

And for other situations, this link is a god-send:

[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)

Have fun!

---

### Post by CrucifiedEgo on 2008-12-16
second link bookmarked.  Thanks!

---

### Post by jdpearson on 2008-12-16
I agree.  Thanks. Now, what about something in more detail about Ubuntu server management, although Webmin seems like the way to go for several reasons.

---

### Post by tjasko12 on 2008-12-16
> **jdpearson said:**
> I agree.  Thanks. Now, what about something in more detail about Ubuntu server management, although Webmin seems like the way to go for several reasons.

I love Webmin and I highly recommend that anyone would use it... ;)

---

### Post by bluesy321 on 2008-12-16
I'm fairly new to Linux and Server/CLI-only as well.  I definitely recommend Webmin like others have.  Webmin is not as nice as a GUI that virtually walks you through everything, but it definitely makes some mundane tasks a lot easier.  Be prepared to know some basic CLI commands as well if you don't know them already though.  :p

Oh, and one little tip for other noobs out there as I had trouble figuring this out for awhile.  If you're struggling to find an easy to use text editor for a Server/CLI-only setup, use "nano"!  I struggled with vi for awhile before realizing nano was installed already and gave me a much easier to use interface.

Good Luck!

---

### Post by Iowan on 2008-12-16
I have the Apress book _Beginning Ubuntu LTS Server Administration_. It's subtitled "From novice to professional".  Though it introduces a lot of topics, I can't say it ever gets to the "professional" state.  I liked the suggestions for partitioning.  It introduces regular expressions, and VPN, but quit short of really explaining how to use them. All in all, I was hoping it'd get me a little closer to professional than novice - I'm not sure it did.
I'll throw in a few links: [serverguide]("https://help.ubuntu.com/8.04/serverguide/C/index.html"), [Webmin]("https://help.ubuntu.com/community/WebMin")

---

### Post by deadlydes on 2008-12-17
> **fjgaude said:**
> This link should get you started:

[http://www.unix-tutorials.com/go.php?id=3886](http://www.unix-tutorials.com/go.php?id=3886)

And for other situations, this link is a god-send:

[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)

Have fun!

those links dont seem to work :confused:
are they right?

---

### Post by jdpearson on 2008-12-17
The worked the other day.  Must be the site is down.  Too bad they were good!

---

### Post by andrew_g on 2008-12-18
Hi, I attempted the webmin install tutorial, but have not managed to get it running. 

I think there is enough interest here to create a step-by-step guide for noob's so let's start at the begining by learning to crawl, walk then run.

So we've chosen webmin as our interface, what we need to know is :

1, How to install it (and on which machine?)
2, how to start it up, and to see if the install worked!
3, if the install failed, why,what are the potential issues, and how to resolve them
4, are firewalls an issue, if so what to do
5, ok so we are finally up and running, lets configure a service (samba, web server, mysql)

Thats just for starters - thanks

---

### Post by baudday on 2008-12-18
The link in my sig may help. It's basically a log of what I did when I set up my server, and includes every link that helped me. Maybe it'll help you.

---

### Post by andrew_g on 2008-12-19
Hi, had a go at the above, but still no luck

Here's where I am currently ...
I have ubuntu **server edition** installed as standard. thats as far as I,ve got so far.

I tried 
 apt-get install webmin webmin-core
but got
 E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission   denied)
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you  root? 

Also  Do I **need** to install a desktop on the server?

---

### Post by linux_tech on 2008-12-19
try 
```
sudo apt-get install webmin webmin-core
```
You need to put sudo before the command since you are not logged in as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by baudday on 2008-12-19
You don't NEED a desktop, but when I first started, I was totally new to unix, and didn't feel comfortable with strictly using commands. There are still some, although very few, tasks that I prefer just doing with a GUI. But the answer is no, if you feel comfortable with just the command line, or if you think that's the only way you'll learn, then don't install a GUI.

---

### Post by rcrcomputing on 2008-12-20
wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.441_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.441_all.deb)
dpkg -i webmin_1.441_all.deb
apt-get -f install

BTW, I never sit in front of a server I'm working on. I access it thru ssh (or putty if your on a windows desktop. That way you can copy and paste etc.. and sit at your own comfortable desktop.

apt-get install ssh
and consider protecting ssh as it's insecure in it's very design.
apt-get install Fail2ban

Soo ..
1st - use nano or "apt-get install vim"
2nd - install ssh and use it.
3rd - install fail2ban or denyhosts to protect ssh
4th - install webmin

---

### Post by rcrcomputing on 2008-12-20
Oh, and don't forget the Ubuntu server guide.
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by koenn on 2008-12-20
> **rcrcomputing said:**
> 
and consider protecting ssh as it's insecure in it's very design.
apt-get install Fail2ban


this caught my eye as I was scanning this thread.

care to explain what's insecure about the design of "secure shell" and what you're hoping to remedy with fail2ban ?

---

### Post by linux_tech on 2008-12-20
Here are a few resources to help get a Ubuntu server going

[http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation](http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation)
[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://wiki.ubuntu.com/ServerTeam/](https://wiki.ubuntu.com/ServerTeam/)
[https://wiki.ubuntu.com/UbuntuServerTasks](https://wiki.ubuntu.com/UbuntuServerTasks)
[https://wiki.ubuntu.com/UbuntuEasyFilePrintServer](https://wiki.ubuntu.com/UbuntuEasyFilePrintServer)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by rcrcomputing on 2008-12-21
> **koenn said:**
> this caught my eye as I was scanning this thread.

care to explain what's insecure about the design of "secure shell" and what you're hoping to remedy with fail2ban ?

Google "brute force ssh" 

You'll notice other programs giving major access to the system limit access attempts by default. And example is webmin.

---

### Post by windependence on 2008-12-21
> **rcrcomputing said:**
> Google "brute force ssh" 

You'll notice other programs giving major access to the system limit access attempts by default. And example is webmin.

If you have your ssh set up correctly, you will NEVER have this problem. I do this professionally for a living and I do not have either one of these installed nor do I plan on it. Use of good secure passwords (read that phrases and not dictionary words) goes a long way in security. Even better yet is setting up passwordless login using public and private keys. Not allowing root login via ssh is another must have. 

It's fine to express your doubts but if you do not have knowledge of an application it's best to refrain from making broad generalizations such as you did. ssh is extremely secure without the use of any other tool if set up and used correctly. Koen is right in asking you why you would say something like this. 

-Tim

---

### Post by koenn on 2008-12-21
> **windependence said:**
> If you have your ssh set up correctly, you will NEVER have this problem. I do this professionally for a living and I do not have either one of these installed nor do I plan on it. Use of good secure passwords (read that phrases and not dictionary words) goes a long way in security. Even better yet is setting up passwordless login using public and private keys. Not allowing root login via ssh is another must have. 

It's fine to express your doubts but if you do not have knowledge of an application it's best to refrain from making broad generalizations such as you did. ssh is extremely secure without the use of any other tool if set up and used correctly. Koen is right in asking you why you would say something like this. 

-Tim
Thanks, my point exactly.

---

### Post by andrew_g on 2008-12-21
Hi, have installed webmin using the following tutorial
[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

NOTE : this is webmin 1.340 but READ ALL the follow up notes at the bottom before proceeding for the updated version

After the install, I could not locate/login to webmin using the suggested url, in my case [https://ubuntuServer:10000/](https://ubuntuServer:10000/) so I typed the ip address in of that machine eg [https://192.168.1.2:10000/](https://192.168.1.2:10000/) (answered a few security questions from my browser) then got the log in screen.

OK so now I have INSTALLED the sever and a gui control panel (webmin), now I will move on to webserver,mysql etc - speak soon perhaps!

I will follow up all other links - thanks alot

Thanks for the help in the meantime - A

---

### Post by rcrcomputing on 2008-12-21
I was aware his question was a "sandbagger" question and was aware I was about to have this conversation. :)
> If you have your ssh set up correctly, you will NEVER have this problem. 
Hmm, you just said, set up "secure shell" and then "secure" it. Shouldn't it have minimal security embedded?
Ok, lets tell the new guy setting his server up, he got compromised in the first 24 hours and it is "his" fault for not setting ssh up correctly. Wonder why other programs are "set up correctly" out of the box. Even windows, when passworded limits attempts.

> I do this professionally for a living and I do not have either one of these installed nor do I plan on it. Use of good secure passwords (read that phrases and not dictionary words) goes a long way in security.
No offense, but I would not hire you. 
With unlimited attempts ANY password can potentially be brute forced. Oh and make sure all your users have these unguessable wonder passwords. And why would you want the brute force attempts in your logs and the loss of bandwidth due to the attempts?

> Even better yet is setting up passwordless login using public and private keys. 
As you must be well aware, this is not always possible for travelers. And use of key's have their own issues.

> Not allowing root login via ssh is another must have. 
And now your machine is just compromised as a user. It now runs brute force attacks on others. Hopefully it's not in a "trusted" part of your domain and has key's set up for other servers.

> It's fine to express your doubts but if you do not have knowledge of an application it's best to refrain from making broad generalizations such as you did. 
If you would like to continue the discussion elsewhere, I'd be happy to test my knowledge against yours. Obviously, you've missed the fact that multiple layers of security should be used. 

> ssh is extremely secure without the use of any other tool if set up and used correctly. 
You have missed the point entirely. That is your choice to do so. 

To those that have not tired of this thread, please take away from this conversation that you must secure ssh. Do not believe the previous post that a good password will do it etc.. By it's design, it allows multiple attempts unlimited. You should use multiple layers of defense including:

Use a firewall and allow only those domains you are likely to connect from.
Install fail2ban as a secondary. These two methods are your first defense.

Others include,
strong passwords
disable password sign on (this can be a pain)
disable root sign-on (secondary method, you don't want them in on any account)

---

### Post by windependence on 2008-12-21
> **rcrcomputing said:**
> I was aware his question was a "sandbagger" question and was aware I was about to have this conversation. :)
 
Hmm, you just said, set up "secure shell" and then "secure" it. Shouldn't it have minimal security embedded?
Ok, lets tell the new guy setting his server up, he got compromised in the first 24 hours and it is "his" fault for not setting ssh up correctly. Wonder why other programs are "set up correctly" out of the box. Even windows, when passworded limits attempts.

This doesn't even warrant an answer. You are supposed to be an ADMIN. I am fond of saying that this is the SERVER forum. Most of the time that implies you have SOME experience with the OS. It IS his fault if he didn't do some planning and research before putting a production server on the web.


> **rcrcomputing said:**
> No offense, but I would not hire you. 
With unlimited attempts ANY password can potentially be brute forced. Oh and make sure all your users have these unguessable wonder passwords. And why would you want the brute force attempts in your logs and the loss of bandwidth due to the attempts?

Well since unwanted packets are discarded at my BSD gateway, I'm not losing any bandwidth. Just FYI, been doing this for over 10 years and never been hacked nor have any of my customers. Of course I have multiple layers of security in place. the point here was that using a dictionary word for a password will get you compromised in less than 5 minutes. With a good strong password it could take days or even weeks, and that is with a constant connection which a good admin would surely have noticed. Care to try to break in to one of my OpenBSD servers?

 
> **rcrcomputing said:**
> As you must be well aware, this is not always possible for travelers. And use of key's have their own issues. 

Why would it be an issue if your traveler has his own laptop? The keys stay with him all the time. A passphrase could also be used.

 
> **rcrcomputing said:**
> And now your machine is just compromised as a user. It now runs brute force attacks on others. Hopefully it's not in a "trusted" part of your domain and has key's set up for other servers. 

You would be assuming that the user accounts are also easily compromised. You're also assuming that the compromised account goes undetected. Ever heard of intrusion detection software?

 
> **rcrcomputing said:**
> If you would like to continue the discussion elsewhere, I'd be happy to test my knowledge against yours. Obviously, you've missed the fact that multiple layers of security should be used. 

Obviously you posted this as flamebait, and I don't have time to get into a pi**ing contest with you. I only wish I had time to set up a server for you to break into.

 
> **rcrcomputing said:**
> You have missed the point entirely. That is your choice to do so. 

To those that have not tired of this thread, please take away from this conversation that you must secure ssh. Do not believe the previous post that a good password will do it etc.. By it's design, it allows multiple attempts unlimited. You should use multiple layers of defense including:

Use a firewall and allow only those domains you are likely to connect from.
Install fail2ban as a secondary. These two methods are your first defense.

Others include,
strong passwords
disable password sign on (this can be a pain)
disable root sign-on (secondary method, you don't want them in on any account)

Well we agree on one thing, you should secure ssh just like you should secure any other application on any OS. I still have no plans to install fail2ban or any of that other junk as I don't need yet another layer of complexity for the little benefit I will gain.

-Tim

---

### Post by koenn on 2008-12-21
> **rcrcomputing said:**
> I was aware his question was a "sandbagger" question and was aware I was about to have this conversation. :)
If you'd just explained that you don't like it that ssh doesn't put a limit on login attempts, and that fail2ban is your way of dealing with that, ...

Calling the program "**flawed in its very design"** because of that, and which is only an issue for password authentication, not for the other authentication methods ssh supports, is a just not right, and gives the wrong impression to the beginner you're trying to help. That's all. 


Other than that, windependence covered most of it. Yes, security is layered, and should be seen as a system, where one measure complements or enhances another. And if you're going to run public servers and/or setup remote administration, you better know what you're doing.

---

### Post by rcrcomputing on 2008-12-21
> You are supposed to be an ADMIN. I am fond of saying that this is the SERVER forum. Most of the time that implies you have SOME experience with the OS. It IS his fault if he didn't do some planning and research before putting a production server on the web.
ok, he's learning to admin, yet he's supposed to be an admin? Have you missed the fact that this thread is named "Server Tutorial"? 

> Well since unwanted packets are discarded at my BSD gateway, I'm not losing any bandwidth. Just FYI, been doing this for over 10 years and never been hacked nor have any of my customers. Of course I have multiple layers of security in place. the point here was that using a dictionary word for a password will get you compromised in less than 5 minutes. With a good strong password it could take days or even weeks, and that is with a constant connection which a good admin would surely have noticed. 

We are not talking about your servers or your experience in years (which is less than mine). We are talking about the choice in ssh design. It does not matter how you secure your server. That you excuse it because YOUR server is arranged to get around or lesson exposure makes no difference to the discussion. 

> Care to try to break in to one of my OpenBSD servers?

Why would I care to break into anyones server?  

> Why would it be an issue if your traveler has his own laptop? The keys stay with him all the time. A passphrase could also be used.

The reasons of not having your own laptop to access are many. Now we are back to passwords.

 
> You would be assuming that the user accounts are also easily compromised. You're also assuming that the compromised account goes undetected. Ever heard of intrusion detection software?

Oh yeah, people learning to set up the server are already supposed to know and be familiar with snort?   


> Obviously you posted this as flamebait, and I don't have time to get into a pi**ing contest with you. I only wish I had time to set up a server for you to break into.

Nonsense. I simply stated my opinion of a design flaw in ssh. You started the pi**ing match. And YOU keep it going. You came on and said you were the big admin and I shouldn't talk about things I do not know about. You keep going off on tangents not related to the subject. Mine was a simple statement to alert users of a design flaw in ssh. 


> Well we agree on one thing, you should secure ssh just like you should secure any other application on any OS. 

ssh is not "just another application".

---

### Post by rcrcomputing on 2008-12-21
> **koenn said:**
> If you'd just explained that you don't like it that ssh doesn't put a limit on login attempts, and that fail2ban is your way of dealing with that, ...

Calling the program "**flawed in its very design"** because of that, and which is only an issue for password authentication, 

Your kidding right? So how would you design such a program that you were going to call "secure shell"?

> 
not for the other authentication methods ssh supports, is a just not right, and gives the wrong impression to the beginner you're trying to help.  
While there was no intent to imply anything other than "password verification design flaw", I stand by my statement.

> 
And if you're going to run public servers and/or setup remote administration, you better know what you're doing.


Hmm, right after reading the tutorial..  haha  That's funny.  You guys keep telling them "you better know what you are doing" when they are asking how to do it...

In any regard, if either of you would like to start another thread to further this discussion, please do so and invite me. You and I have completely managed to trash the intent of this "ubuntu tutorial" thread. Any other posts in this thread by me shall be limited to the subject at hand.

---

### Post by windependence on 2008-12-22
OK if ssh is so flawed in your opinion, then use something else. This argument is pointless.

-Tim

---

### Post by koenn on 2008-12-22
> **rcrcomputing said:**
> Your kidding right? So how would you design such a program that you were going to call "secure shell"?


The ssh faq explains in detail what the 'secure' in secure shell stands for.
[http://www.openssh.com/faq.html#1.1](http://www.openssh.com/faq.html#1.1)
[http://www.openssh.com/faq.html#1.2](http://www.openssh.com/faq.html#1.2)
It's worth a read, if you're interested in facts rather than assumptions.

> **rcrcomputing said:**
> 
While there was no intent to imply anything other than "password verification design flaw", I stand by my statement.

Fine; I'll just conclude that "flawed in its very design" to you is just a synonym for "I assumed it limits the number of login attempts but it doesn't, and I wish it would". I'll keep your tendency to exaggerate and generalize in mind for the next time I see you post an opinion. 


> **rcrcomputing said:**
> 
Hmm, right after reading the tutorial..  haha  That's funny.  You guys keep telling them "you better know what you are doing" when they are asking how to do it...

I merely reacted to your unsubstantiated opinion on ssh, so in this particular thread, this remark of yours is meaningless. Glad you found it funny. I find it funny that you advise to install fail2ban, without explaining what it is, what it does, or how to use it. 


> **rcrcomputing said:**
> 
In any regard, if either of you would like to start another thread to further this discussion, please do so and invite me.
yYou and I have completely managed to trash the intent of this "ubuntu tutorial" thread. Any other posts in this thread by me shall be limited to the subject at hand.
That's the 2nd time you propose to take this outside. Sorry, not interested. I've said what I had to say, and as a result, this thread now contains some background on ssh and some general pointers about what sort of things to pay attention to when setting up a server. That's near-topic enough if you ask me. If in your opinion it's trash, ah, well, ... :)

---

### Post by gg234 on 2008-12-23
Try here for more ubuntu server tutorials

[http://www.ubuntugeek.com/category/server](http://www.ubuntugeek.com/category/server)

---

### Post by cjacobsen on 2009-01-21
I write about Ubuntu security on my blog. The topics covered are for securing your server(s). Primary written for Ubuntu 8.04 LTS, but most of the stuff applies to 8.10 as well.

Contains information on setting up ssh server, and adding addition security to the ssh service. (Part II)

---

### Post by Zanthir on 2010-09-27
> **linux_tech said:**
> Here are a few resources to help get a Ubuntu server going
 
[http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation](http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation)
[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://wiki.ubuntu.com/ServerTeam/](https://wiki.ubuntu.com/ServerTeam/)
[https://wiki.ubuntu.com/UbuntuServerTasks](https://wiki.ubuntu.com/UbuntuServerTasks)
[https://wiki.ubuntu.com/UbuntuEasyFilePrintServer](https://wiki.ubuntu.com/UbuntuEasyFilePrintServer)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
 
Thank you! All of you. This is the best thread I've found for getting my server up and running. Especially this rich set of links, linux_tech. 
 
I think I'll have the tools I need to get my basic server services up and running now. I'm just going through those, "what? No desktop?" growing pains right now. Every little bit of aid helps.

---

### Post by Zanthir on 2010-09-27
I've ordered The Official Ubuntu Server Edition Book, Second Edition, as I've heard it is good, but it has yet to arrive.
 
The Official Ubuntu Book was a great and easy read, and I'm hoping the server book is similar, and give me a sense of familiarity with the OS, why it is the way it is/the philosophy behind it, and how to use it as well as where to find help (here obviously).
 
Anyone else have it/recommend it?

---

### Post by lisati on 2010-09-27
Guides for recent releases of Ubuntu Server can be downloaded here: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

(Closed: this is a really old thread with a large period of inactivity)

---


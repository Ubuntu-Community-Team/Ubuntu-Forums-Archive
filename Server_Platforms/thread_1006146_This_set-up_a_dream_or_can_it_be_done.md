---
title: "This set-up a dream or can it be done"
date: 2008-12-09
forum: Server Platforms
---

### Post by Gregz on 2008-12-09
I have Ubuntu 8.10 and working good since nvidia is working... Now for the important things. What I would like is to use virtualbox to run office small business and accounting pro. and be able to access it from anywhere with laptop. Also to have it do all back-ups on pc's.


Guess basically it be the main frame and hold all the files. Hence something happens to laptop it's all at home on server. It's going to host website ect.... 


Question is can it be done AND will I live through it    lol

---

### Post by bluefrog on 2008-12-09
yes

---

### Post by Gregz on 2008-12-09
ok I have looked through forums and found many differnt things. My question is what is the and easiest (for a noobie) to set-up and maintain. 


2) I have been looking at joomla for website building,but this seems to have issues(hard to set-up), is there a better one?

3) Is there any good reading on a set up like this??

---

### Post by bluefrog on 2008-12-11
if joomla is hard to set up for you I am afraid you'd better hire someone to set up what you want to do which is by the way kind of unclear in your 2 messages.

file server?
need one windows to hold specific windows program? (apparently yes)
web server? do you have a good adsl line?
...

---

### Post by Gregz on 2008-12-11
bluefrog,

I wanna host my own site, plus be able to run my business off this server. 

so yes file server and web server, internet is not problem I have cable and very good speeds.

but It has to be where I can access it from anywhere with laptop. If problems pop up I can fix on fly and also look at customer accounts and inventory ect and also for back-up of laptop. The other pc's not to worried about. I want to get joomla set-up then I will worry about  virtual box set-up...



***as for hiring somebody no trying to cut costs THATS  one of the main reasons I want away from win-doze***.

---

### Post by koenn on 2008-12-11
> **Gregz said:**
> What I would like is to use virtualbox to run office small business and accounting pro. and be able to access it from anywhere with laptop. Also to have it do all back-ups on pc's.

Guess basically it be the main frame and hold all the files. Hence something happens to laptop it's all at home on server. It's going to host website ect.... 

> **Gregz said:**
> 
so yes file server and web server, internet is not problem I have cable and very good speeds.

but It has to be where I can access it from anywhere with laptop. If problems pop up I can fix on fly and also look at customer accounts and inventory ect and also for back-up of laptop. The other pc's not to worried about. I want to get joomla set-up then I will worry about  virtual box set-up...

***as for hiring somebody no trying to cut costs THATS  one of the main reasons I want away from win-doze***.

Yes, it can be done. But don't do it. 

Assuming you're counting on virtualbox to run windows applications : you'll still need a windows license. So much for cheap-skating away from "win-doze". 


Having your business files and apps on pulically accessible web server is a bad idea. Wrapping them in a virtual machine might add a tiny bit of security, depending on how you do it, but still.

Seeing that you want to access your business data "from anywhere", you're going to need tight security unless you want anybody and everybody to access your business data from anywhere

"internet with very good speeds" ? You sure about that ? your server is going to need good **upload** speeds / volume / ... because its _upload_ will be the limit of the _download_ for those connecting to it. 

Using Linux or ditching Windows (if that's what you mean with win-doze) because Linus is cheap, is a mistake. Choose a system that provides the best solution for your business needs. If you choose wrong, you'll pay later in loss of time, loss of data, loss of business.

Same goes for not hiring someone who knows what he's doing because doing it yourself, all wrong, is cheaper.  

Oh, and mainframes have nothing to do with any of this.


You're not up to this, and although counting on recipes and walk-throughs in this thread might get you a working solution, it still sounds like quite a risk to have your business depend on it.
Hire someone to help you with this. Any freshman student in a computer-related field and an interest in Linux can do this in half the time you'll need to post questions and try to figure out what the replies mean.

---

### Post by Gregz on 2008-12-11
OK  you bring up some good points.

1) windows bought and paid for long time ago. Just done sinking money in microsoft. I don't like the way vista ask to ok everything you do. and then won't let you do what you want either. (permission denied). or waiting for a tech for 4 hrs and still have the same problem. NO I could go on for hours about them.

2) internet is business class ***not*** residential. much better speeds. up/down     :guitar:

3) security is where you got me though. I'm going to look into this.. 


4) As far as doing it myself   been doing that for years nothin new there.  :lolflag:

---

### Post by bluefrog on 2008-12-12
Before people starts bitching about security and "you should not do like this but like that", the following is to put you on tracks if you want to do it on your own (not a good idea depending on your IT level)
There are some (lot) things that I omit because it will take me deeper and deeper into explanation for things that take a few sec to put in place or explain when speaking but hours to explain in written (I exaggerate maybe but not that much).

backup of your laptop can be tricky (not as in hard, just tricky) depending of your operating system and what you want to install on your file server.
**backup of laptop and server**
use of partimage can be a good thing (clonezilla, OSCAR also)
generally systemrescuecd is a must have cd to have handy

**synchronization**
_laptop linux - server linux_
  use conduit, unison whatever is easy for you
_laptop windows - server linux_
  need to install and configure samba (again can be tricky)
  need to tweak your windows (especially if windows xp pro)

**access your server when not at home**
   familiar with command line: use ssh
   not familiar with command line, use vnc over ssh
either in putty (windows) or straight from command line in unix/linux
      ssh -L 5901:localhost:5900 your-user@your-server-IP
that needs:
  openssh-server installed on your server
  being sure that connection to port 22 is forwarded to your server
  your-user is logged onto the server (yes security.... blah blah blah - you can also install a vnc server but I am not going into that now)
  remote-desktop is enabled in your-user session (beware of "ask for confirmation" that will prevent you from connecting...
  then connect via your vnc viewer to localhost:5901

**joomla is nothing to install**
1) install LAMP onto your computer (sudo tasksel    select LAMP)
2) create a database and give control to that database only to a user
  mysql -u root -p
  create database joomla;
  grant all on joomla.* to joomlauser@localhost identified by 'joomlauser-password';
  quit;
3) download and install joomla virtuemart (if you want online shop)
  [https://dev.virtuemart.net/cb/displayDocument/VirtueMart_1.1.2_eCommerce_Bundle_Joomla_1.5.8.tar.gz?doc_id=2743](https://dev.virtuemart.net/cb/displayDocument/VirtueMart_1.1.2_eCommerce_Bundle_Joomla_1.5.8.tar.gz?doc_id=2743)
  sudo mkdir /var/www/joomla
  tar xzf VirtueMart_1.1.2_eCommerce_Bundle_Joomla_1.5.8.tar.gz -C /var/www/joomla
  sudo chown -R www-data /var/www/joomla

4) for the following you need a fixed IP (or at least dynamic IP services - not very sensible if you are running an online shop, who would like to buy to a company which cannot even hire itself a fixed IP or a dedicated server on the net? personnally I rent a dedicated server on the net so it is hardware hassle free for me)

  **configure a virtual host for apache**
  sudo vi /etc/apache2/sites-available/joomla
      <VirtualHost *:80>
	ServerAdmin [email]webmaster@your-site.com[/email]
	ServerName your-site.com
	ServerAlias *.your-site.com ## this need a A entry in your registrar dns server such as: * A your-fixed-IP
	DocumentRoot /var/www/joomla

	<Directory /var/www/joomla/>
## prevent people from downloading/viewing /var/www/joomla/configuration.php
## you will need to include the files limit in your default site as well and in your ssl virtual host if you enable it (both in default and joomla)
		<Files configuration.php>
	          AuthType Basic
	          AuthName Restricted
	          AuthUserFile /etc/apache2/sites-available/security/htpasswd  ## you need to create such a folder and issue a command: sudo mkdir sudo /etc/apache2/sites-available/security && htpasswd -c /etc/apache2/sites-available/security/htpasswd whatever-name
	          <Limit GET>
	             Require valid-user
	          </Limit>
                </Files>

		RedirectMatch ^/administrator [https://your-site.com/administrator](https://your-site.com/administrator)   ## to force administration login of joomla thru https, this needs you to enable https, if no ssl, do not enable that line
	 </Directory>

      </VirtualHost>

sudo a2ensite joomla  (declare your virtualhost to apache)
sudo invoke-rc.d apache2 restart

connect to [http://your-site.com](http://your-site.com)  (if hosted on the net)
or         [http://localhost/joomla](http://localhost/joomla)  (you could have [http://joomla.local](http://joomla.local) but you need more virtual host and tweaking of your /etc/hosts)
and let joomla drives you thru the install process.

That should get you started. Remember though that depending on your business and how much time you have that it is generally best to focus on your core business and leave the rest to specialized people (specialized doesn't mean huge companies taking an arm and a leg, but most often small contractors can do what you want at a better price and they are listening to your needs as their business depends on people/companies like you.

yes I will be such a contractor in France starting beginning of next year but small contractors are certainly closer to your home and it is sometimes nice to meet at least once such people...

James Dupin

---

### Post by koenn on 2008-12-12
> **Gregz said:**
> 
4) As far as doing it myself   been doing that for years nothin new there.
Hm. I guess your OP of "is this possible and will I live through it ?" threw me off ...

---

### Post by perspectoff on 2008-12-12
I like Drupal instead of Joomla, but both are good. Neither is that hard to set up.

I have a business wiki, groupware, file servers, and security on a distributed network.

The components I use are on

[http://ubuntuguide.org](http://ubuntuguide.org) (ubuntuGuide)

and

[http://kubuntuguide.org](http://kubuntuguide.org) (Kubuntuguide)

There are very simple ways to install most of the components, and there are very difficult ways.

Many of the long-time users of Linux only know the difficult command-line ways becasue they don't realize that the newer packages streamline installation. So be careful of overly complex instructions -- much of the time they are overkill.

Read the Guides. If the Guides don't help, then ask the forums.

---

### Post by Gregz on 2008-12-12
Thanks bluefrog and everyone else, very informative bluefrog and gave me alot to think about. I have good support from my ip provider and they help out quite abit from there end on security. as far as ip my store will have it own. 

I may just go with hosting website for now, and leave the business stuff on windows, maybe a duel boot again, don,t really like that with vista. Vista has no mbr to fix if something goes wrong. I know I spent 4 hours with microsoft trying to fix one time and lost everything for the day.....oh the pain...... :cry: Had to reload vista and go from back-ups.....oh the pain..... I now have to change cables to go to windows... it's on another hard drive. as of now they are never hooked up at the same time.

---


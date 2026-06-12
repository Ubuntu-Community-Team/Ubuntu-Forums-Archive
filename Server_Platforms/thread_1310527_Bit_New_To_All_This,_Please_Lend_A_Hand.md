---
title: "Bit New To All This, Please Lend A Hand"
date: 2009-11-01
forum: Server Platforms
---

### Post by Geek9 on 2009-11-01
So I'm fairly well versed in Windows, but am pretty much new to Linux, other then using it for ***** and giggles and booting up puppy linux, I know nothing, but in order to become more well rounded and versed I decided to make my own home server, but sadly am already encountering problems. So I come to you hoping you will provide me with some much needed guidance. BTW I'm using the latest 32-bit build of Ubuntu 9.10
Here are my overall goals
-1 Make a working home server that's connected to my HP Photosmart 4200 printer (that way I can use it as a network printer.
-2 Attach a portable HDD and use it over my home network
-3 Possibly  set it up to access it anywhere in the world
Here are my problems right now
-1 when I first boot up it takes me to the login (all fine and dandy I have the info) unfortunately it doesn't seem to want to let me in, it will let me type my username, but unfortunately once it hits the password line becomes unresponsive, unless I hit enter at which point I will type my password, but alas login incorrect pops up.
-2 I really haven't even had any luck with my printer on Linux, but considering I can't even get it up, that doesn't seem to be my biggest problem ATM.
So lend me a hand alright thanks for your help.

---

### Post by BQAggie2006 on 2009-11-01
Are you using the Ubuntu Server edition that brings you into a command line login prompt?

---

### Post by Geek9 on 2009-11-01
> **BQAggie2006 said:**
> Are you using the Ubuntu Server edition that brings you into a command line login prompt?
yup and yup

---

### Post by BQAggie2006 on 2009-11-01
And I assume when you mean the password prompt is unresponsive, that nothing shows up while you're typing?

---

### Post by Geek9 on 2009-11-01
> **BQAggie2006 said:**
> And I assume when you mean the password prompt is unresponsive, that nothing shows up while you're typing?
spot on, nothing shows up, unless I hit enter which brings it down a line and then typing shows

---

### Post by BQAggie2006 on 2009-11-01
This is normal behavior for command line Linux, it doesn't show anything when you type your password, though it is still receiving the characters you are typing.

---

### Post by Geek9 on 2009-11-01
> **BQAggie2006 said:**
> This is normal behavior for command line Linux, it doesn't show anything when you type your password, though it is still receiving the characters you are typing.
lol well I feel quite ******* stupid thanks for the help will try out, but I still require assistance on the other things, so thanks man

---

### Post by BQAggie2006 on 2009-11-01
Don't worry about it, I think I made the same mistake when I switched to Linux. Good luck and let us know if you have any more questions!

---

### Post by Geek9 on 2009-11-02
okay so here's the deal, I'm at command line, but I'm itching for a gui, any advice?

---

### Post by BQAggie2006 on 2009-11-02
You can either install the Ubuntu Desktop edition from CD or run the following command:

```
sudo apt-get install ubuntu-desktop
```

_sudo_: super user do - this is how you get administrator privileges on the machine to run something
_apt-get_: Ubuntu command line tool for handling packages
_install_: obvious
_ubuntu-desktop_: the ubuntu-desktop package which will install the entire Ubuntu Desktop environment for you

---

### Post by ExTruckie on 2009-11-02
I to am using the desktop version for my server. 
I used this to guide me though the setup: [http://www.knightwise.com/content/view/300/9/](http://www.knightwise.com/content/view/300/9/) don't worry about the version on Ubuntu used any of the newer versions are ok 
I didn't bother with Filezilla as I don't wish to run a ftpserver. 
I haven't bothered to setup a print server yet, but it is in the future. Here is the place to be if you have questions. Someone here will be able to come up with an answer eventually.

---

### Post by Geek9 on 2009-11-02
> **BQAggie2006 said:**
> You can either install the Ubuntu Desktop edition from CD or run the following command:

```
sudo apt-get install ubuntu-desktop
```_sudo_: super user do - this is how you get administrator privileges on the machine to run something
_apt-get_: Ubuntu command line tool for handling packages
_install_: obvious
_ubuntu-desktop_: the ubuntu-desktop package which will install the entire Ubuntu Desktop environment for you
big ups to you my man, been searching around and that was what I was getting the just that I had to do, its just such a pain to find a guide, and then o relearn all the **** you thought you knew

---

### Post by BQAggie2006 on 2009-11-02
The Ubuntu Pocket guide is a really good place to start for the basic stuff and can be downloaded for free: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also, along the lines of servers is the Ubuntu Server Guide, which also can be downloaded in PDF form: [https://help.ubuntu.com/9.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/9.04/serverguide/C/serverguide.pdf)

I also use the Ubuntu Community Documentation for Servers a lot: [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

There is a lot of useful information in general at [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by Geek9 on 2009-11-02
thanks to the both of you, this should get me started, I'll let you know how this ends.

---

### Post by Barriehie on 2009-11-02
> **Geek9 said:**
> thanks to the both of you, this should get me started, I'll let you know how this ends.

Ends?????  :)  I've been messing around with my install for the last year and a half and I -think- I'm just gettng started!!!

Barrie

---

### Post by cariboo on 2009-11-03
There is always more to learn, once you get more familiar with the server version, you'll find that you don't need a gui any more. There are limitations to using a gui, especially if you want to stuff the server away in a corner without a monitor and keyboard connected to it. 

There is also the fact that a gui uses resources that could be used elsewhere, as well as being a security problem if you have the server connected to the and accessible from the internet.

---

### Post by mudcow007 on 2009-11-03
sorry guys quick hijack!

i have tried running 

sudo apt-get ubuntu-desktop it takes about 1 1/2 hours (and im on a 20mb connection)

the desktop install fails here is one of them many messages that show on the cli

```
The HTTP server sent an invalid reply header [IP: 194.169.254.10:80] Err http://gb.archive.ubuntu.com Karmic/main xserver-xorg-video-v4 1:0.2.0-3ubuntu1
```

---

### Post by Barriehie on 2009-11-03
> **mudcow007 said:**
> sorry guys quick hijack!

i have tried running 

sudo apt-get ***install*** ubuntu-desktop it takes about 1 1/2 hours (and im on a 20mb connection)

the desktop install fails here is one of them many messages that show on the cli

```
The HTTP server sent an invalid reply header [IP: 194.169.254.10:80] Err http://gb.archive.ubuntu.com Karmic/main xserver-xorg-video-v4 1:0.2.0-3ubuntu1
```

See the man page for apt-get, I think you need to have **install** in your command line.

```

...muted...

       [b]Unless the -h, or --help option is given, one of the commands below
       must be present.[/b]


...muted...
```

Barrie

---

### Post by Geek9 on 2009-11-03
> **cariboo907 said:**
> There is always more to learn, once you get more familiar with the server version, you'll find that you don't need a gui any more. There are limitations to using a gui, especially if you want to stuff the server away in a corner without a monitor and keyboard connected to it. 

There is also the fact that a gui uses resources that could be used elsewhere, as well as being a security problem if you have the server connected to the and accessible from the internet.
yeah, I just need to GUI to get it set up, but unfortunately I really don't feel like doing this from command line

---

### Post by ExTruckie on 2009-11-03
> **Barriehie said:**
> Ends?????  :)  I've been messing around with my install for the last year and a half and I -think- I'm just gettng started!!!

Barrie


I've only been at this for about 3 weeks.
I still have ALOT to learn:popcorn:

---

### Post by Geek9 on 2009-11-03
alright so hit a bit of a wall here, I tried that knightwise guide, but it just doesn't work for me so here's the deal, I installed a gui for the server (gnome) my original goals stand any advice/guides?

---

### Post by Barriehie on 2009-11-03
I don't know what the differences are between the server editions and the desktop but I'm running the desktop version of 8.04 LTS and using it via dyndns to serve up pages.  Mostly I've got one I use for my work but it was painless to install LAMP, Linux, Apache, MySQL, and PHP.  Most ISP's block port 80, which is the default port for http so mine is using 45826, which is handled on the dyndns end and currently not assigned any protocol.  Here's some pics of my HVAC repairs, i.e. it works.  [Click here](http://ubuntubox.hobby-site.org:45826/theacguy).  Later on I installed squid and use it to block thousands of adware, data-logging, none of your business sites.  This one auto-updates once a week.  Makes browsing faster.

So, where are you stuck? How far did you get?

Barrie

Edit:  I'll try to find the LAMP install document I used.  It was really painless and worked out of the box so to speak.

k, here's the community docs on what you've got and are trying to do.  I would suggest browsing through to get a heads up...  **[help.ubuntu.com](https://help.ubuntu.com/9.10/serverguide/C/index.html)**

Looked a bit through the docs on help.ubuntu.com and you can probably not install the DNS - [http://ubuntuforums.org/showthread.php?t=1174726&highlight=bind](http://ubuntuforums.org/showthread.php?t=1174726&highlight=bind)

I've tried installing a mailserver for a week, it still doesn't work...

Tomcat appears to have issues with environment variables.  Lots of google on that one.

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> alright so hit a bit of a wall here, I tried that knightwise guide, but it just doesn't work for me so here's the deal, I installed a gui for the server (gnome) my original goals stand any advice/guides?

I would use metacity for the WM, window manager.  It's like cheerios compared to fruit loops but is less resource requiring than compiz.  Enter a terminal and type:
```

metacity --replace

```
I suggest this only for the speed diff.'s I've aquired on my machine with it.  Not knowing your hardware it's only a suggestion!

Barrie

---

### Post by Geek9 on 2009-11-03
thanks for the  tips, I'ma work on getting LAMP going, the primary problems I'm having now, is I'm not sure what to install to access it/start broadcasting, here's what I want essentially, to be able to access it from any comp with net access, but to have it locked via pass/username (and of course its sharing that portable HDD + files on internal)

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> thanks for the  tips, I'ma work on getting LAMP going, the primary problems I'm having now, is I'm not sure what to install to access it/start broadcasting, here's what I want essentially, to be able to access it from any comp with net access, but to have it locked via pass/username (and of course its sharing that portable HDD + files on internal)

Once apache and mysql and php are installed you'll be online.  Since, as stated before, most ISP's block port 80 you should check out [http://www.dyndns.com/](http://www.dyndns.com/) in regards to port forwarding.  There are many providers of this service, I've used them error free for sneaking up on a year so I know they are reliable.  You can pick a network name, mine is ubuntubox.hobby-site.org, and a port to forward the request to.  They'll map you in as a subnet of their network and the outside world can get to your machine.

In regards to password access are you wanting one username/password pair to allow acces or will you be issuing many?  A small number of username/password pairs can be hardcoded via PHP but many would best be implemented via an SQL database.  PHP is best for this since the code is run on the server, i.e. not visible to the person requesting the page!

An example of a single login is my page [ here](http://ubuntubox.hobby-site.org:45826/pa/).  Enter 'bch0445' and click submit and you'll get to the next page.  I've disabled the add to database button and if selected will yield a custome 404 error page, browser back button will return to previous screen.

'Nuff for now!  Don't want you to overload! :)

Barrie

Edit: A command you'll likely be needing, I did!, is how to restart apache after any config file changes.
```

sudo apache2ctl restart

```

sudo = allows administrative/root user rights to the system.

When you think you've got it you can point your browser to:
[http://localhost/](http://localhost/)  or   [http://127.0.0.1](http://127.0.0.1)  and you'll get the default apache 'It Works' page.

A list of valid port numbers can be found [here](http://www.iana.org/assignments/port-numbers).

---

### Post by Geek9 on 2009-11-03
thanks man you're really gettin me going here

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> thanks man you're really gettin me going here

As did others for me! :)  Feel free to ask ?'s!  Can PM if you like.

Barrie

---

### Post by Geek9 on 2009-11-03
ok so while I'm installing this, here's what I need to know, this will allow me on my home network and around the net to access my server, and then after the passphrase access the files I put up to share correct?

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> ok so while I'm installing this, here's what I need to know, this will allow me on my home network and around the net to access my server, and then after the passphrase access the files I put up to share correct?

I think so! You might have to mess around with your router settings.  First step would be to get the default Apache 'It Works' page going in your browser.  You can go to [http://www.grc.com/](http://www.grc.com/) and under services select shields up and it will tell you what ports are open.  Any experience with PHP for generating a password page?

Barrie

---

### Post by Geek9 on 2009-11-03
> **Barriehie said:**
> I think so! You might have to mess around with your router settings.  First step would be to get the default Apache 'It Works' page going in your browser.  You can go to [http://www.grc.com/](http://www.grc.com/) and under services select shields up and it will tell you what ports are open.  Any experience with PHP for generating a password page?

Barrie
nope, but I've hit a bit of a wall here, at the IP part how do I know which IP I should put it, I keep getting this socket error

---

### Post by Barriehie on 2009-11-03
You must be getting closer.  My browser is waiting for your machine to send the page. The connection timed out...

Barrie

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> nope, but I've hit a bit of a wall here, at the IP part how do I know which IP I should put it, I keep getting this socket error

What IP part???  Are you editing a .conf file???  What's the socket error?

Barrie

---

### Post by Geek9 on 2009-11-03
> **Barriehie said:**
> You must be getting closer.  My browser is waiting for your machine to send the page. The connection timed out...

Barrie
still getting a damn sock failure GAHH

---

### Post by Barriehie on 2009-11-03
What is the error you're getting???  See if you have **/var/log/apache2/error.log** and post it.

Barrie

Edit: So, except maybe for version #'s your setup shouldn't be to much different from mine.  I'll go through my .conf files and see what to post to be relevant.

---

### Post by Geek9 on 2009-11-03
god damn I gotta go, but I will be on this ASAP tomorrow, but essential around the last 3 steps of that guide I get an error at msql -u root, so I'ma try a clean install of mysql tomorrow, but if someone could give me the commands for that that'd be great, also which IP should I be putting, my host IP or the actual IP of my comp?

---

### Post by Barriehie on 2009-11-03
> **Geek9 said:**
> god damn I gotta go, but I will be on this ASAP tomorrow, but essential around the last 3 steps of that guide I get an error at msql -u root, so I'ma try a clean install of mysql tomorrow, but if someone could give me the commands for that that'd be great, also which IP should I be putting, my host IP or the actual IP of my comp?

Actual IP of your comp.  MySQL will be connecting to databases on YOUR machine.

Barrie

Edit: Your IP is probably dynamically assigned, if so use 127.0.0.1.  That is the IP for 'localhost'.  If your IP is static then you can enter in whatever is assigned to you via your ISP.

---

### Post by Barriehie on 2009-11-03
When you're at the term. and entering:
```

>mysql -u root

```
and getting the error you've already setup the root user and password???

You getting this error?
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
Try this if so:
```

>mysql -u root -p

```
You will then be prompted for the root password.

Barrie

P.S.  It's been awhile since I set mine up...

---

### Post by Barriehie on 2009-11-04
Found this in regards to MySQL. [https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20bind%20address](https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20bind%20address).  The complete article is [here](https://help.ubuntu.com/community/ApacheMySQLPHP).

Barrie

---

### Post by MrQuan on 2009-11-04
> **Geek9 said:**
> okay so here's the deal, I'm at command line, but I'm itching for a gui, any advice?
I'm in very much the same situation as you, and also have next to no indepth linux experience... [http://ubuntuforums.org/showthread.php?t=1307534](http://ubuntuforums.org/showthread.php?t=1307534)

I've opted to keep my server GUI free to keep it simple and minimise bloat.  I did find a good comprimise in Webmin and I suggest to give it a chance before installing the gnome desktop.  I was very intimidated by the command line, and Webmin has been excellent.

Webmin is a remote management tool, so I'm assuming you have another PC at home to access it from ;)

Edit: Ok, I just read the rest of the thread and saw that you've gone with gnome, nm :)

---

### Post by Barriehie on 2009-11-04
> **MrQuan said:**
> ...Muted...

Webmin is a remote management tool, so I'm assuming you have another PC at home to access it from ;)

Edit: Ok, I just read the rest of the thread and saw that you've gone with gnome, nm :)

FWIW: I at one time had webmin installed on my machine and you can run it on the machine it's installed on.

Barrie

---

### Post by MrQuan on 2009-11-04
> **Barriehie said:**
> FWIW: I at one time had webmin installed on my machine and you can run it on the machine it's installed on.

Barrie
I assume you already had a GUI then? Or is there some way to run a web browser in a CLI only server??

---

### Post by Barriehie on 2009-11-04
> **MrQuan said:**
> I assume you already had a GUI then? Or is there some way to run a web browser in a CLI only server??

Always been running the desktop version.  For the server req. on here it works just fine!  The only text browser I'm aware of is/was lynx.  I was messing around with it at the dawn of the internet; back when ALL of it was CLI driven.

Barrie

---

### Post by Geek9 on 2009-11-04
ok guys given me a lot to think about, unfortunately I'm out of town for 4 days, so I'ma be inactive, but I'll let you know my results/probs ASAP thanks.

---

### Post by Barriehie on 2009-11-04
> **Geek9 said:**
> ok guys given me a lot to think about, unfortunately I'm out of town for 4 days, so I'ma be inactive, but I'll let you know my results/probs ASAP thanks.

And when you get all of this sorted out you can dive into the world of html, php, sql, javascript, blah blah blah...  :)

I'll work on a passphrase login for you; i.e. edit one I've already got if you like.

Barrie

---

### Post by Geek9 on 2009-11-05
alright so I just need clarification here, I'm away from the server so I can't work on it, but I install webmin on the server correct, then when I view the server from my web browser in windows I should be fine, right? Also does anyone know of a way I can find the IP that the above guide wants me to bind the server to? When I tried entering the one I got it didn't work out well

---

### Post by Barriehie on 2009-11-05
> **Geek9 said:**
> alright so I just need clarification here, I'm away from the server so I can't work on it, but I install webmin on the server correct, then when I view the server from my web browser in windows I should be fine, right? Also does anyone know of a way I can find the IP that the above guide wants me to bind the server to? When I tried entering the one I got it didn't work out well

Webmin is a management tool.  You can set server parameters with it.  To see what your server looks like from the real world you'll type [http://localhost/](http://localhost/) in your browsers address bar, or [http://127.0.0.1/](http://127.0.0.1/)  localhost = 127.0.0.1   The default directory for serving up pages is /var/www/.  If you don't have anything in there it should look like [this](http://ubuntubox.hobby-site.org:45826/).  My machine is a subnet from dyndns so that's why I've got a qualified domain name for the link.  Once again, since ISP's block port 80 I'm using port 45826.

Use localhost for the bind address.

Barrie

---

### Post by Geek9 on 2009-11-06
> **Barriehie said:**
> Webmin is a management tool.  You can set server parameters with it.  To see what your server looks like from the real world you'll type [http://localhost/](http://localhost/) in your browsers address bar, or [http://127.0.0.1/](http://127.0.0.1/)  localhost = 127.0.0.1   The default directory for serving up pages is /var/www/.  If you don't have anything in there it should look like [this]("http://ubuntubox.hobby-site.org:45826/").  My machine is a subnet from dyndns so that's why I've got a qualified domain name for the link.  Once again, since ISP's block port 80 I'm using port 45826.

Use localhost for the bind address.

Barrie
gotcha, just out of curiosity if I ever get this thing up and running when I got the portable HDD connected I should be able to view it in my browser

---

### Post by Barriehie on 2009-11-06
> **Geek9 said:**
> gotcha, just out of curiosity if I ever get this thing up and running when I got the portable HDD connected I should be able to view it in my browser

Well, as long as the permissions are correct and I think you'll have to make a link to it in the /var/www dir.  While on the subject of directories; :)  I've made a ~/www folder and put all my web apps in there and then create a link (man ln) to them in the /var/www folder.  Seems to be more web input on that being the proper way.  Of course I'm the sole user of this machine so it's probably mute point but yet a good practice.

Barrie

---

### Post by Geek9 on 2009-11-06
> **Barriehie said:**
> Well, as long as the permissions are correct and I think you'll have to make a link to it in the /var/www dir.  While on the subject of directories; :)  I've made a ~/www folder and put all my web apps in there and then create a link (man ln) to them in the /var/www folder.  Seems to be more web input on that being the proper way.  Of course I'm the sole user of this machine so it's probably mute point but yet a good practice.

Barrie
the more I do this the more I feel like I may just scrap using ubuntu server edition, I don't want to, but the problem is I feel like a simplistic straight forward guide is missing (probably just me, but that's life) probably just use the desktop version. However I'll let you know after I get home and try try again

---

### Post by Barriehie on 2009-11-06
> **Geek9 said:**
> the more I do this the more I feel like I may just scrap using ubuntu server edition, I don't want to, but the problem is I feel like a simplistic straight forward guide is missing (probably just me, but that's life) probably just use the desktop version. However I'll let you know after I get home and try try again

For what your initial purposes were outlined as I'm sure the desktop version will work just fine.  I ran a site getting 58,000 hits a month off of mine and I never noticed unless I looked at the stats.  Can't remember what version your using but if you install 8.04 LTS it'll be easier, on my end, :) to help you...

Barrie

Addendum:  I've edited some of my login files and have a simple 5 file plain jane, i.e. black on white, passphrase scenario for you/your users.

---

### Post by windependence on 2009-11-07
You all need to do a little more reading and training esp. on networking before giving up.

The idea behind webmin is NOT to view it on the server. In fact, with servers, you don't want to be working on the physical machine. You should admin the machine from a remote machine (yes even your Windoze desktop) by typing the address of your server in your browser on the remote box e.g. [http://192.168.0.2:10000](http://192.168.0.2:10000). You never physically touch the server. the BEST way to admin it though is to ssh into the box in a terminl window, and no, it's not archaic, it's more efficient and makes sense for real server applications.

-Tim

---

### Post by Geek9 on 2009-11-08
> **windependence said:**
> You all need to do a little more reading and training esp. on networking before giving up.

The idea behind webmin is NOT to view it on the server. In fact, with servers, you don't want to be working on the physical machine. You should admin the machine from a remote machine (yes even your Windoze desktop) by typing the address of your server in your browser on the remote box e.g. [http://192.168.0.2:10000](http://192.168.0.2:10000). You never physically touch the server. the BEST way to admin it though is to ssh into the box in a terminl window, and no, it's not archaic, it's more efficient and makes sense for real server applications.

-Tim
figured as much, but I'm trying to learn more and to do more with the server I'll keep it up and see what happens

---

### Post by Geek9 on 2009-11-09
well folks 2 steps forward 10 back, I've scraped my install and am doing a fresh one, still have no clue what the hell I'm doing

---

### Post by Barriehie on 2009-11-09
> **Geek9 said:**
> well folks 2 steps forward 10 back, I've scraped my installed and am doing a fresh one, still have no clue what the hell I'm doing

Still going with the server?

Barrie

Edit: Take a look [here](http://www.howtoforge.com/ubuntu_debian_lamp_server) for a tutorial in installing LAMP.

---

### Post by Geek9 on 2009-11-09
> **Barriehie said:**
> Still going with the server?

Barrie

Edit: Take a look [here]("http://www.howtoforge.com/ubuntu_debian_lamp_server") for a tutorial in installing LAMP.
well got my first victory, managed to connect from my windows comp to my server using putty am now trying to get webmin working, but my browser does not seem to wanna connect to the server any suggestions?

---

### Post by Barriehie on 2009-11-09
> **Geek9 said:**
> well got my first victory, managed to connect from my windows comp to my server using putty am now trying to get webmin working, but my browser does not seem to wanna connect to the server any suggestions?

Well, I would first just install the essentials to LAMP and then worry about all the other stuff! What port are you using and are you putting in the browser url???  Browser url would be something like [http://mydomain : port#/](http://mydomain : port#/) 

Since somthing can connect to it you know you've got apache2 up and running.  Take a look at the logs before DOING anything!!!  /var/log/apache2

Barrie

---

### Post by Geek9 on 2009-11-09
> **Barriehie said:**
> Well, I would first just install the essentials to LAMP and then worry about all the other stuff! What port are you using and are you putting in the browser url???  Browser url would be something like [http://mydomain : port#/]("http://mydomain%20:%20port#/") 

Since somthing can connect to it you know you've got apache2 up and running.  Take a look at the logs before DOING anything!!!  /var/log/apache2

Barrie
well I'm using putty to do this, so I type in my local IP and it says port 22, also the only thing installed ATM is openBSD secure shell

---

### Post by Barriehie on 2009-11-09
So have you got a Windows Home Server going on somewhere???

Barrie

---

### Post by Geek9 on 2009-11-09
> **Barriehie said:**
> So have you got a Windows Home Server going on somewhere???

Barrie
nope reinstalled ubuntu server on my server, then used putty to connect

---

### Post by Barriehie on 2009-11-09
> **Geek9 said:**
> well I'm using putty to do this, so I type in my local IP and it says port 22, also the only thing installed ATM is openBSD secure shell

No clue about Putty!  Don't do windows anymore! :)

Barrie

---

### Post by Geek9 on 2009-11-09
> **Barriehie said:**
> No clue about Putty!  Don't do windows anymore! :)

Barrie
lol ok any advice for webmin?

---

### Post by wojox on 2009-11-09
To connect to webmin you need you local ip for the server entered into the web browser not putty. Log into your router to get the ip if you don't know it.

---

### Post by Geek9 on 2009-11-09
> **wojox said:**
> To connect to webmin you need you local ip for the server entered into the web browser not putty. Log into your router to get the ip if you don't know it.
tried that no response from server
also ATM have gnome installing, will be AFK for a bit

---

### Post by Geek9 on 2009-11-09
what I'm still having a bit o trouble with is should webmin be installed on the server or on the machine accessing the server?

---

### Post by cariboo on 2009-11-10
Webmin is a server administration suite, you would install it on the server. Then you access the interface using your web browser on your desktop computer:

```
http://server_ip_address:10000
```

---

### Post by Geek9 on 2009-11-10
> **cariboo907 said:**
> Webmin is a server administration suite, you would install it on the server. Then you access the interface using your web browser on your desktop computer:

```
http://server_ip_address:10000
```
ok that makes sense, as for the 1000 part I believe that refers to the port correct? but the problem seems to be I'm connecting through port 22 using putty (that way I can access an ssh set up on windows) so a fix?

---

### Post by Geek9 on 2009-11-11
really at a lost here, its seems these guides don't know where to tell you to change the port

---

### Post by Barriehie on 2009-11-11
> **Geek9 said:**
> really at a lost here, its seems these guides don't know where to tell you to change the port

Port 22 is the defined port for SSH between network devices.  The ports on the server and the client can be changed via tunneling and port forwarding sections in the putty user manual.

Barrie

---

### Post by Geek9 on 2009-11-11
> **Barriehie said:**
> Port 22 is the defined port for SSH between network devices.  The ports on the server and the client can be changed via tunneling and port forwarding sections in the putty user manual.

Barrie

can you give me some specifics, also I had to reinstall, and I installed gdm, but no I can't disable its automatic startup, any advice
EDIT: Fixed the GDM problem, and the server appears to be broadcasting, but no luck on webmin

---

### Post by Barriehie on 2009-11-11
> **Geek9 said:**
> can you give me some specifics, also I had to reinstall, and I installed gdm, but no I can't disable its automatic startup, any advice
EDIT: Fixed the GDM problem, and the server appears to be broadcasting, but no luck on webmin

Specifics no, I uninstalled webmin over a year ago!  I found the putty manual [here](http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/).

Barrie

---

### Post by yknivag on 2009-11-11
You don't need putty for webmin.  Just point the web-browser on your client machine at [https://ip.of.your.server:10000/](https://ip.of.your.server:10000/) and if it is correctly installed you will get a login screeen.  Note the port is ten-thousand, not one-thousand.

---

### Post by Geek9 on 2009-11-11
Well girls and guys, guys and girls I did, I accessed the server using the local ip through the browser and have webmin successfully installed, I gotta troubleshoot it now, but overall its working, but what I really need to know is how to get the ip of the server outside the network so I can access it over the net rather then on my home network

---

### Post by Geek9 on 2009-11-11
seems I've jumped out of the frying pan and into the fire couldn't mount the spare drive due to privelgies, so I tried to make myself root using this 
And modify it accordingly if it doesn't.

Further, run      Code:
     sudo visudo 
 and ensure the sudoers file has the following:
     Code:
     %admin LOCAL=(ALL) ALL 
 then ensure you are in the **admin** group

If you have made additions to the sudoers file, ensure the changes aren't the cause.
needless to say it didn't turn out so well, now it doesn't seem to recognize my one and only user as the root, and I can't execute sudo commands, fixes?
EDIT: says I'm not allowed to run sudo on my server and incident will be reported

---

### Post by Barriehie on 2009-11-11
> **Geek9 said:**
> Well girls and guys, guys and girls I did, I accessed the server using the local ip through the browser and have webmin successfully installed, I gotta troubleshoot it now, but overall its working, but what I really need to know is how to get the ip of the server outside the network so I can access it over the net rather then on my home network

Several thread on that topic.  [http://ubuntuforums.org/showthread.php?t=1316174](http://ubuntuforums.org/showthread.php?t=1316174)

Barrie

---

### Post by Barriehie on 2009-11-11
Found this in my ~/bin dir.  Most of it's commented out so it only runs once rather than looping and reporting every 5 minutes.

```

#!/bin/bash
#  Script to get my IP from dyndns
#

#  PID to jobs folder
#echo > /home/barrie/Desktop/temp/jobs/GetMyIP-$$

#looper=1

#while [ looper ]
#  do
  MYIP=`wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'`
  export MYIP
  echo $MYIP
#  sleep 300
#  done

```

Barrie

---

### Post by Barriehie on 2009-11-15
> **Geek9 said:**
> seems I've jumped out of the frying pan and into the fire couldn't mount the spare drive due to privelgies, so I tried to make myself root using this 
And modify it accordingly if it doesn't.

Further, run      Code:
     sudo visudo 
 and ensure the sudoers file has the following:
     Code:
     %admin LOCAL=(ALL) ALL 
 then ensure you are in the **admin** group

If you have made additions to the sudoers file, ensure the changes aren't the cause.
needless to say it didn't turn out so well, now it doesn't seem to recognize my one and only user as the root, and I can't execute sudo commands, fixes?
EDIT: says I'm not allowed to run sudo on my server and incident will be reported

So what is the line in your /etc/fstab file for the spare drive???

Barrie

---

### Post by Geek9 on 2009-11-15
I scraped that install and just did a fresh one, I got webmin working just need to mount that internal to be shared and do likewise with the external any help with that (you've been amazing so far, just a few more to go)

---

### Post by windependence on 2009-11-15
To access webmin from the outside, you'll need to forward port  10,000 back to your server. Here is a good start for that:

[http://portforward.com/](http://portforward.com/)

If you have problems mounting drives using sudo, the problem is something else, NOT that you aren't root. No need to to use visudo or become root. Next time you try to mount it and have problems ask here and post the exact error you get when trying to mount the drive.

Keep your ssh and putty session and use it for mounting drives and doing other things from the command line that are generally easier.

-Tim

---

### Post by Barriehie on 2009-11-15
[nevermind] ...deleted...[/nevermind]

Barrie

---

### Post by Geek9 on 2009-11-17
sorry been busy for awhile, kinda lost track I'll report back as soon as I jump back into the project

---

### Post by Barriehie on 2009-11-17
> **Geek9 said:**
> sorry been busy for awhile, kinda lost track I'll report back as soon as I jump back into the project

You'll have a HOWTO right?, or at least a bottle of excedrin!  :) :) :)

Barrie

---

### Post by whitethorn on 2009-11-18
Are you behind a router?  If you are you should set a fixed IP for your server.  Then log into your router and open the specific ports you need and point them at your server.  If you don't have a static IP then you also need to use something like [www.dyndns.org](www.dyndns.org) to forward to your dynamic IP, this requires a little more work because you need to update your different IP (after a disconnect) at dyndns.org.  There are a couple ways of doing that.  Sometimes routers have a builtin function for dyndns, and there are programs which will also do it.  Then you should be able to connect to your box from outside your home network.

---

### Post by Geek9 on 2010-01-26
lol well I'm sorry it took me so long, but I'm back and boy have I learned from my mistakes, it feels so painful looking at how obvious my problems are. But I'm back and I learned, so first off I just wanna say thanks to all these patients souls, and finally I need just a touch of help getting my weak system to recognize the second internal drive.

---


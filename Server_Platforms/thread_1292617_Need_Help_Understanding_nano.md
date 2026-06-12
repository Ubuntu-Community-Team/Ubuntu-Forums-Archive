---
title: "Need Help Understanding nano"
date: 2009-10-16
forum: Server Platforms
---

### Post by husskii on 2009-10-16
Other then the basics of changing passwrds and reboot, Im new to linux and really need some help pls. Im trying to setup a server on my own for the first time.

Im trying to Set Up A Ubuntu/Debian LAMP Server
and have installed Apache + PHP, MySQL Database Server & PhpMyAdmin with seb by step instructions.

But wen I get to the nano sections, to create a test.php in my /var/www folder with phpinfo() function. I really have no clue what Im doing there. I type the info needed but dnt know how to save it or what to do next. and the instruction doesnt tell you how.

Ive been on it for hrs & could really use some help here pls..

---

### Post by Vermind on 2009-10-16
Hi,
Here are [Nano keyboard commands]("http://staffwww.fullcoll.edu/sedwards/Nano/NanoKeyboardCommands.html").
In short: ctr+X, then y, then enter exits and saves your file with the name it was opened.

Nano, vim or emacs are useful in the long run, though awkward to get used to at first. You could also use rsync or scp to copy the file from another box to the server, if you have ssh access to it. Also, if you install a basic graphical text editor, such as gedit, with ```
sudo apt-get install gedit
```, with ssh access you can then start it remotely like so:
```
me@mydesktop $ ssh -X myserver
me@myserver $ gedit /var/www/myfile.txt
```
This gedit will then open on the remote server, using the X protocol through the ssh session. You will interact with the remote filesystem using your local computer.

---

### Post by Adina on 2009-10-16
You need to be sudo to edit files with nano. If you don't your changes wil not be saved.

If you need to edit your network configuration:

```
sudo nano /etc/network/interfaces
``` 

When you have made your changes just hit ctrl+x and the hit enter to confirm the filename to save.

To make phpinfo.php file you can just type:

```
sudo nano phpinfo.php
```

and then ctrl+x and enter

or alternatively you could also type 

```
touch phpinfo.php
```

---

### Post by husskii on 2009-10-16
Hi m8, thanks heaps I managed to get the test phpinfo() saved and now can access phpinfo on the web thru my browser...
I tried to install gedit but it said it was already installed. Im using ubuntu server 9.04 and also imstalled xinit and x-windows-=system-core-gnome, to get gui on the server. also I should add that I use the server locally atm but I will eventually be wanting to access the server remotlty but for now especially whilst I setup, I will be installing and setting up locally.

Im now upto phpmyadmin & have also installed it onto my server with "apt-get install phpmyadmin" command.
I want to use it to manage my database aned am upto 

""The phpmyadmin configuration file is located at: /etc/phpmyadmin folder.

To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf:

Include /etc/phpmyadmin/apache.conf """

Im guessing I add 'Include /etc/phpmyadmin/apache.conf' to nano but am not sure if I use thet same test command as before to enter nano, which was ""nano /var/www/test.php"" or if there is another command I should be using, or even on the right track :)

do u know where I should add "Include /etc/phpmyadmin/apache.conf"

thanks

---

### Post by openfly on 2009-10-16
nano is just the name of the executable for the nano editor.

You need to add that line to your apahce2 conf file.

So you use nano on that conf file to make changes.

Viola.

---

### Post by husskii on 2009-10-16
thats the thing how do i get into iot to add the line
Include /etc/phpmyadmin/apache.con

at the moment its all just test and once i understand it a litle better I will hopefully be linking my server to whmcs, thats my goal. and I guess use google apps too..

I had a friend set it up for me b4, were my server was linked to whmcs and also did something with google apps so that wen users registered, they would recieve a confirmation email etc. he isnt around and I dnt wanna keep relying on ppl to do it for me, so im trying to do it all on my own, but have gone in with no talent wat so ever.. :)

---

### Post by drumbug1 on 2009-10-16
Hi husskii - not sure if you're stuck on *finding* the apache config or on how to open/edit the file.

If you can't find it - try the "locate" command like this:

```
 locate apache2.conf 
```

That should give you something like:

```

husskii@ubuntu-computer:~$ locate apache2.conf
/etc/apache2/apache2.conf
/usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz
husskii@ubuntu-computer:~$ 

```

OK!  So now that you've found the apache config file... you need to edit it (using nano!).  Do that like this:

```
 sudo nano /etc/apache2/apache2.conf 
```

Then you can add the text you need.  When you are done press CTRL-O to save.

Hope that helps! - I apologize if I misunderstood where you're stuck.

---

### Post by husskii on 2009-10-18
hi drumbug1 thank you mate that helped alot as i think I will need to use that q little later wen I need to configure apache to link it to my whmcs site, but being my first time attempting this, Im not too sure:)
wat I need to know now is how to get to **/etc/apache2/apache2.conf:** 
because After installing phpmyadmin
the instructions are;
" The phpmyadmin configuration file is located at: /etc/phpmyadmin folder.

To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf:
*Include /etc/phpmyadmin/apache.conf* "

do u know how I would get to **/etc/apache2/apache2.conf:
I believe thats were I should add the **Include /etc/phpmyadmin/apache.conf 

once its setup I would like to point it to my whmcs and I guess thats wen the hard stuff starts :)

---

### Post by drumbug1 on 2009-10-18
> **husskii said:**
> 
wat I need to know now is how to get to **/etc/apache2/apache2.conf:** 


From the terminal type:
```

sudo nano /etc/apache2/apache2.conf

```


Am I missing where you are confused by this direction?  If you can help me understand what is unclear - maybe I can be more specific.

---

### Post by husskii on 2009-10-18
sure, once i get into nano Im not sure were to add

" Include /etc/phpmyadmin/apache.conf "

unlike nano /var/www/test.php were it was blankand simple were to add the text, the /etc/apache2/apache2.conf: is full of text and warnings and Im not sure were to add the following text.
" Include /etc/phpmyadmin/apache.conf "

Thanks heaps for all your help, its much needed :)

---

### Post by husskii on 2009-10-20
hi guys im still stuck at configuring apache.
Once I enter sudo nano /etc/apache2/apache2.conf
Im not sure were to enter the following texts..

" Include /etc/phpmyadmin/apache.conf "

could really use the help..
thanks

---

### Post by drumbug1 on 2009-10-21
> **husskii said:**
> sure, once i get into nano Im not sure were to add

" Include /etc/phpmyadmin/apache.conf "



Ok... sorry I misunderstood.

For the most part it doesn't really matter.  It's safe to add that as a new line at the very end of the file (use the down arrow on your keyboard to scroll to the bottom or use CTRL-V to jump pages).

---

### Post by husskii on 2009-10-21
hi m8 thanks heaps I have now added it to the bottom of the page & it worked like a charm, I think lol...

also I created a welcome page which ppl can view whilst my website is under construction, but wen I try to move that file to the www folder or apache conf folder, I get access denied. I checked the permissions in properties and it says root can access edit etc, but my user isnt the owner and i guess i need to be root.

I installed and setup ubuntu, so I dnt understand why I wouldnt be the owner. 

I need to be able to either edit the options or login as root to save this document to the folder, but wen I try login as root with the passwd I use for sudo, it wont authenticate.

Im not sure wat im doing wrong..

atm if u go to my url it only says "it works!" in bold letters
but i can only access that from the actuall server, I cant access the page from a dif pc..

---

### Post by drumbug1 on 2009-10-21
> **husskii said:**
> hi m8 thanks heaps I have now added it to the bottom of the page & it worked like a charm, I think lol...

also I created a welcome page which ppl can view whilst my website is under construction, but wen I try to move that file to the www folder or apache conf folder, I get access denied. I checked the permissions in properties and it says root can access edit etc, but my user isnt the owner and i guess i need to be root.

Are you logging into a graphical user interface and then trying to move the file(s)?  This is probably not the easiest way to do this (unless you want to change the owner of /var/www/ to your "normal" user).  You can move files from the terminal using the "mv" command like this:

```
sudo mv /path/to/my/file.html /var/www/file.html
```

> 

I installed and setup ubuntu, so I dnt understand why I wouldnt be the owner. 



Unlike Windows, Ubuntu does *NOT* make you an admin that has read/write access to all files on the system... _this is a good thing._

> 

I need to be able to either edit the options or login as root to save this document to the folder, but wen I try login as root with the passwd I use for sudo, it wont authenticate.



By design you cannot log into a graphical user interface as root.  Again: _this is a good thing._  Like I said above you need to either use the command-line to admin your Apache webserver or you need to change the owner of /var/www/ to your "normal" user (assuming you want to use the GUI to move files around).

If you really want to do this, run:

```
sudo chown -R username:username /var/www/
```

> 

Im not sure wat im doing wrong..



Think of it this way, you're *learning* what you're doing!

> 

atm if u go to my url it only says "it works!" in bold letters
but i can only access that from the actuall server, I cant access the page from a dif pc..

How are you trying to access the server?  Are you going to the IP address on the different PC's web browser?  This problem could be caused by a lot of things and _ you need to provide more info for us to help you!!! _

< rant >Also please - refrain as much as possible from the "internet abbreviations" (m8, pls, ppl, dif, dnt, atm) -  it makes reading your message very frustrating (The shift and apostrophe keys are also your friends!). < / rant >   ...sorry/no offense - just had to say it.

;-)

---

### Post by husskii on 2009-10-21
ha ha very funny...
Im so sorry I will refrain my self from "internet abbreviations" 
to tell the truth, Im just getting the hang of them my self...


ok I just tried to access the page from my 2nd pc, but this time I used the actuall IP of the server and not the main IP (router ip) I had tried to use before.. when I use my server IP from my notebook which is on my network, I can access a page that has in bold text " **IT WORKS!** " but If I try the same thing but using my domain name. 
on the server I get the same page " **IT WORKS!** " but from my notebook, I get "internet explorer cannot display this page"
so I can only access the page using the IP.

also I had a friend try access the page from his pc, which is in another location and not on my network. he also gets 
"internet explorer cannot display this page"
and it doesnt matter which IP or domain name he tries, he still gets the same error.

with moving my file I think the best option would be to just use terminal to move my files. I think it will be much safer then changing the permissions...

Ill attempt to do that now and see how I go...
thanks

---

### Post by drumbug1 on 2009-10-22
> **husskii said:**
> ha ha very funny...
ok I just tried to access the page from my 2nd pc, but this time I used the actuall IP of the server and not the main IP (router ip) I had tried to use before.. when I use my server IP from my notebook which is on my network, I can access a page that has in bold text " **IT WORKS!** " but If I try the same thing but using my domain name. 
on the server I get the same page " **IT WORKS!** " but from my notebook, I get "internet explorer cannot display this page"
so I can only access the page using the IP.


Is your router forwarding port 80 to the server?  (sounds like it's not - that would be your problem)

Do you have proper DNS setup for your domain name?

---

### Post by husskii on 2009-10-22
ok my router is definatly configured to allow my ip's thru port 80 (http) I havent done anything about dns server, I dnt think its installed to tell the truth.
wen I installed ubuntu server I dnt think I chose dns server in the server options.

I think I just installed mail, lamp, openssh, mysql & one for virtualizing (which I believe virtulizing didnt work, because kvm fails on boot)

should I install dns server, and would the command be 
```
sudo apt-get install dns server
```

thanks

---

### Post by drumbug1 on 2009-10-22
> **husskii said:**
> ok my router is definatly configured to allow my ip's thru port 80 (http) I havent done anything about dns server, I dnt think its installed to tell the truth.
wen I installed ubuntu server I dnt think I chose dns server in the server options.

I think I just installed mail, lamp, openssh, mysql & one for virtualizing (which I believe virtulizing didnt work, because kvm fails on boot)

should I install dns server, and would the command be 
```
sudo apt-get install dns server
```

thanks

Before you worry about DNS, I'd worry about being able to access the site from your public IP address (your router's "outside" ip address).  Unless you get that working installing BIND (the standard DNS server) won't do you any good!

Please provide more info about your setup:

- What is your server's IP address?
- What is your router's (internal) IP address?
- Can you please post the contents of your /etc/network/interfaces file?

---

### Post by husskii on 2009-10-22
Hi mate my server ip is 10.1.1.7
router IP 58.106.219.50
and the content in my /etc/network/interfaces file? is

```
GNU nano 2.0.9  file:/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by drumbug1 on 2009-10-22
Generally using DHCP for a server is not recommended.  Is there a reason you are doing this?  It's very likely that at some point when your DHCP lease expires the IP address will change (thus breaking your port forwarding from your router).

Can you also describe what you did to forward the port 80 to your server?  You'd have to configure the router and actually enter in '10.1.1.7' somewhere.  Did you do this, or simply unblock port 80?  (maybe it would help if I knew what kind of router you were using....)

---

### Post by husskii on 2009-10-23
HI mate Im using a netgear DG834GSP router.
I forwarded my actual ip 10.1.1.7 thru the firewall on ports 80 for http and 443 for https. 

with DHCP Im not sure why I have it, I guess it was just that way wen I had setup the router. If I dnt need it then yea I can change it I guess, but If it doesnt do much harm then I guess it can stay.

at the moment I have to start all over again, I was mssing around with windows server and wen I installed it on a 2nd hdd, it wiped out all of ubuntu, but thats ok I can get to were I was, it should take about 2 or 3 hrs.

---

### Post by husskii on 2009-10-23
hi I just reinstalled ubuntu server this time i installed dns server, so now i have lamp, dns, mysql, mail & openssh aslo followed the [Build Your Own Debian/Ubuntu LAMP Server - Quick & Easy Do it Yourself Installation] & now im back to were we left off.

---

### Post by windependence on 2009-10-24
Just a few tips. ctl + o (that's control o as in onyx) saves your work in nano. Then, you can just ctl+X to quit.

You don't need to, and probably won't want to run your own DNS server after you see how difficult it can be to set it up. Just use your registrar's dns (the people where you registered your domain) to point the IP address at your server.

Always willing to help someone learn the command line.

-Tim

---

### Post by drumbug1 on 2009-10-24
If you're still having trouble accessing through your router, you may want to look here (found this by searching "dg834gsp port forward" on google):

[http://forum.portforward.com/YaBB.cgi?num=1217680091](http://forum.portforward.com/YaBB.cgi?num=1217680091)

---

### Post by husskii on 2009-10-24
thats the same way I forward my ports, but I have just forwarded ports 80 & 443..
I noticed that they were also forwarding http file server, is that something I woulud need..

ok now wen they connect to [http://58.106.219.59/](http://58.106.219.59/) & [http://58.106.219.59/SEED.php](http://58.106.219.59/SEED.php) they can connect but if they try connect using the domain name insead of IP, they get an error ""Internet Explorer Cant Display Webpage""

hi windependence I havent registered a domain name yet. Im still learning how to set it all up and not sure wat name I'll actually use...

---

### Post by windependence on 2009-10-26
Exactly why you can't reach your site by the hostname. How would your browser know that your domain name points to your IP address - in fact it doesn't until you tell your registrar where to point it. 

Also, you will not be able to access your domain from inside your local network unless you modify your hosts file to point to the LOCAL address of your server. Most home routers do not do NAT reflection, so they will not route your traffic locally unless you either run local DNS or put an entry in your hosts file which is most likely the easiest option for you. On most Linux, your hosts file is at /etc/hosts. In Windows, C:\windows\systems32\drivers\etc.

-Tim

---

### Post by husskii on 2009-10-26
i just edited my host file and changed the ip's from 127.0.0.1 local host & 127.0.0.1 seed-machine. I changed the local host to 10.1.1.7 and seed-machine to 58.106.219.59...
they didnt work, so I tried to change them back. Now I can access phpinfo again but for seed-machine, it doesnt matter wether I use my IP or the hostname, on both I get the following error & cant access it from my host machine..
""Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at seed-machine Port 80""

before I tried this action, I was able to access them from my host machine.

---

### Post by husskii on 2009-10-26
hi tim im not sure what u tried to tech me but it stuffed up on me.
I changed the hosts file, they were both 127.0.0.1 for localhost & seed-machine, so I changed the localhost to my local ip and seed-machine to my routers ip, and since then I have had the following error..
""Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at seed-machine Port 80""

and now no matter what I try I cant access                       [http://seed-machine/.index.html](http://seed-machine/.index.html) or [http://58.106.219.63](http://58.106.219.63)

can someone pls help me fix wat ever went wrong, because I really dnt want to have to go thru a reinstall again....

thanks

---

### Post by drumbug1 on 2009-10-26
> **husskii said:**
> hi tim im not sure what u tried to tech me but it stuffed up on me.
I changed the hosts file, they were both 127.0.0.1 for localhost & seed-machine, so I changed the localhost to my local ip and seed-machine to my routers ip, and since then I have had the following error..
""Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch Server at seed-machine Port 80""

and now no matter what I try I cant access                       [http://seed-machine/.index.html](http://seed-machine/.index.html) or [http://58.106.219.63](http://58.106.219.63)

can someone pls help me fix wat ever went wrong, because I really dnt want to have to go thru a reinstall again....

thanks

1st, put your hosts file back how it was (and don't change the localhost ip again!)

2nd, add your ip and host/domain name on _a separate line_!

---

### Post by husskii on 2009-10-27
Hi drumbug1, 

wen u say "2nd, add your ip and host/domain name on a separate line!"

should I add them at the bottom of the page, and also which ip should I use, my local or remote IP...

thanks mate much appreciated...

---

### Post by windependence on 2009-10-27
Like this:

```
127.0.0.1    localhost
255.255.255.255    broadcasthost
::1             localhost 
fe80::1%lo0    localhost
192.168.2.40    dominicanstotheusa.com
```

Note the last line. This has the address of a web site I run. It is the LOCAL address that you need to use in this case. Don't mess with the other stuff that's already there. Yours may not look like mine either.

-Tim

---

### Post by husskii on 2009-10-27
hi m8 this is wat my hosts file looks like.

127.0.0.1       localhost
127.0.1.1       seed-machine

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

""eg. 10.1.1.7 seed-machine.org ""

should I just add my local ip and domain name at the bottom, like Ive done in the example..

thanks

---

### Post by windependence on 2009-10-27
Yep, it should look like this:

```
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.1.1.7 seed-machine.org
```

-Tim

---


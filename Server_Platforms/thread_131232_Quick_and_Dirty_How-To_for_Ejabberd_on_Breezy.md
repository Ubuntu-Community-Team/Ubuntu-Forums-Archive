---
title: "Quick and Dirty How-To for Ejabberd on Breezy"
date: 2006-02-16
forum: Server Platforms
---

### Post by Glarbl_Blarbl on 2006-02-16
I originally posted this in response to a question in the general section, but it totally belongs here.

Ejabberd has more recommendations that I can find than any other open source IM server, as it will do encryption and web-based administration. I installed it a couple of days ago after trying jabberd briefly.
[FONT=Courier New]
sudo apt-get install ejabberd[/FONT] 

It works with only a couple of hacks, you need to edit the /etc/ejabberd/ejabberd.cfg and put your hostname in where it tells you in the comments, like this:
[FONT=Courier New]
% Host(s) name: (replace for your hostname(s))
% Old {host, "localhost"}. option is equivalent to {hosts, ["localhost"]}.
{hosts, ["gps"]}.[/FONT]


My server is called gps. You'll also want to sudo and use "ejabberdctl register" to make yourself an account which you'll add into the same file for admin access.

[FONT=Courier New]sudo ejabberdctl register *screen-name* *password*[/FONT]

and then:

[FONT=Courier New] % Users that have admin access. Add line like one of the following after you
% will be successfully registered on server to get admin access:
{acl, admin, {user, "g"}}.[/FONT]


Gotta love the one-character login, I use it whenever I can.

Once this is done issue the command:

[FONT=Courier New]sudo /etc/init.d/ejabberd restart

[/FONT] and to double-check it's running:

[FONT=Courier New]sudo ejabberdctl status[/FONT]

Then fire up your favorite web browser and point it to
[FONT=Courier New] [http://192.168.0.2:5280/admin/](http://192.168.0.2:5280/admin/)[/FONT]
replacing 192.168.0.2 with the IP or hostname of your new ejabberd server. For username, enter "user@server" where user is the account you made earlier with ejabberdctl and server is the hostname you inserted into the ejabberdctl.cfg file. Hopefully you still remember the password you set from earlier.

In the web admin panel you can set access controls and add users, it doesn't look like you can add or configure modules from here though. There's also a nodes page which is probably part of the fault-tolerance/rollover mechanism. I don't have another server to test this aspect yet, maybe I will investigate and write further later.

The biggest bugaboo I encountered, though, was getting GAIM 1.5.0 to connect ... After a bunch of tries, I found that the only way to make it work was an account set up like this:

change **protocol **to Jabber
** screen name** is user from before
** server** is the hostname from ejabberdctl.cfg
**resource **can be anything you want, if you use different resources you can log in more than once with the same screen name!
** password** from before
** alias** is probably the name that shows up when you type a message
(open "**show more options**")
** check BOTH TLS and SSL**
** port** 5223
** Connect Server** is IP or FQDN of your ejabberd server
** No Proxy**, unless you know that you need it.

Of course, now that you have the right settings you can actually just register a user from GAIM (unless you changed the acl to prevent this already)... It's nice to know how to do it from the command line though.

To add a buddy, make sure to do the full "user@server" formula, mine is g@gps ..

---

### Post by viniosity on 2006-04-03
This was very helpful! Thanks!

---

### Post by KittyChunk on 2006-05-11
Thanks for the instructions, very useful indeed :-)

Note that the new GAIM beta 3 doesn't seem to want to connect to the ejabberd server *at all*, no matter what combinations of SSL, TLS, and port numbers I try. The Psi client works fine though, so at least I know it's all behaving itself on the server side...

[EDIT] My bad. Windows needed a reboot :-P. Also GAIM b3 needs all the TLS options unchecked, only "force old SSL" on port 5223.

---

### Post by Socratez on 2006-05-13
What are the benfits to running your own IM Server? I have got my own mail, web, ftp, etc etc but would I need this for personal uses?


Thanks in advance .. 


Soc

---

### Post by HS-L on 2006-05-28
Hmmmm... i get this:

sudo ejabberdctl restart
Can't restart node ejabberd@ctu: nodedown

seems there is no way to start ejabberd with the ejabberdctl command,
anyone has any clue?

---

### Post by KittyChunk on 2006-06-01
I'm now getting a similar problem - I can start/restart the server fine, and asking for status tells me it's running fine, but I can't connect to the server in any way. 

Trying to access the web admin interface on port 5280 gives a "connection refused" error in the web browser, and users trying to connect to the server over the local network simply get "couldn't connect to server" or "SSL authentication error".

Zounds :-(

---

### Post by Randomskk on 2006-06-04
Hrm, for some reason I can't seem to retrieve my vCard. Any ideas?

---

### Post by porque on 2006-06-05
[QUOTE=KittyChunk]Trying to access the web admin interface on port 5280 gives a "connection refused" error in the web browser, and users trying to connect to the server over the local network simply get "couldn't connect to server" or "SSL authentication error".[/QUOTE]
Did you entered [http://example.org:5280/admin](http://example.org:5280/admin) ?
And did you read this FAQ entry?:
[http://ejabberd.jabber.ru/node/559](http://ejabberd.jabber.ru/node/559)

You also need to create a user and give it admin rights:
[http://www.process-one.net/en/projects/ejabberd/docs/guide_en.html#htoc26](http://www.process-one.net/en/projects/ejabberd/docs/guide_en.html#htoc26)

---

### Post by airtonix on 2006-07-20
i solved this

"not allowed"
your host name in the config file isnt the same  as the one your using to acces the admin.

"not found"
your port forwarding needsto be setup to forward 5222 and 5269

"stream error"
your using 5222 to access the server, this should work. i dont know why for sure, but i think it has something to do with ssl certificates being required, but why its not a ssl port? mmmmm

plus if your doing all this from behind a dyndns domain name, you may have problems doing subdomains unless you pay for it. no sure though.

---

### Post by airtonix on 2006-07-20
Randomskk: doooood, postage and handling are free....show us your config :)

[SIZE=3] **Update**[/SIZE]
[SIZE=1]Friday, July 28 2006

[/SIZE]Randomskk : you must have figured it out....
Others : i have a sussefullyconnected to a jabber server with this setup using clients that talk to port 5222. To do it,  I used gaim to register a new account with the server. after which it seems to use 5222.

I will report back and update more. oh and the jabber admin interface provided through the localhost:5280 seems to have more features since this articale was originally authored. 

[SIZE=3] **Update**[/SIZE]
[SIZE=1]Tuesday, 01 August 2006[/SIZE]

all : need to work out how to allow the admin to use their account from a machine other than the server...or (as i am  slowly realising) is this a security issue? proly yes now that i think of it....cause it breaks the ideal of only using the least-priveldged-access from outside or anywhere type attitude.

My next goal is to work out how to get file transfer working between jabber machines. if anyone has done this already and can verify the setup using either gaim, gajim or kopete then i would love to hear of your method....

---

### Post by 11hjpphty76lkjj on 2007-03-06
when i go to:

[http://loaclhost:5280/admin](http://loaclhost:5280/admin) I get the login prompt and then I get a blank page.  what am i doing wrong?

thanks!

A

---

### Post by 11hjpphty76lkjj on 2007-03-06
nevermind.  

helps if I have the permissions setup correctly :)

A

---


---
title: "Windows Home Server feature equivalent"
date: 2009-02-05
forum: Server Platforms
---

### Post by Kronos2785 on 2009-02-05
Hi, I've recently been experimenting with Windows Home Server and have come to like one particular feature it has. The ability to, via a web browser, to access shared directories. 

Completely through a web interface. 

You are able to upload, download files, browse the directory structure, and are forbidden from accessing shares for which the logged in user is normally unable to access on the internal network.

This is a very nifty feature, and for my Dad it allows him to easily and without any fuss access his files from work, and send files home from work that he needs to work on.

However, We have only been using the evaluation copy, and he is reluctant to pay for a copy. Hence my question, is there a way to get this functionality on a linux server?

regards,
Kronos2785

---

### Post by spiderbatdad on 2009-02-05
Absolutely. Apache webserver is good for this. also web browsers are capable of resolving sftp and ftp with ssh server installed or vsftp, etc.
Apache2 & PHP is probably the simplest to get running. It may seem difficult if you have never worked with linux before, but the community provides good documentation.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

My own simple tutorial for beginners using home servers:
[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

And finally, after installing php-5 from your package manger, there is a cool file called filethingie you can add to /var/www ( or whatever file you host your website from) that makes uploading very easy.
[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

It's a lot to tackle if you're totally new to linux, but do-able. And after you've done it a couple of times, it's a piece of cake.

HMMMM. re-read your post. openssh is also ideal for what you are talking about, and on second thought, is even easier to configure:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Kronos2785 on 2009-02-05
Whilst I'm not a complete Linux noob, I have used Ubuntu Desktop full time for the last 2 years, and have messed with ubuntu server for just a bit less than that.

My issue with what you've suggested to me, is that it isn't a browser based solution.

Here is a link to a screen shot of the interface which might give an idea of what I would like to do. [http://farm1.static.flickr.com/139/400974243_e6c76f90da_o.png]("http://farm1.static.flickr.com/139/400974243_e6c76f90da_o.png")

the whole album
[http://www.flickr.com/photos/65213971@N00/sets/72157594554051272/detail/]("http://www.flickr.com/photos/65213971@N00/sets/72157594554051272/detail/")

These are not my pictures

Hopefully that gives you an idea of what I would like to set up. If there isn't a linux alternative available I will have to convince Dad he needs to buy WHS for the feature he wants. Since it is beyond my ability to program such a thing.

regards,
Kronos

---

### Post by jrusso2 on 2009-02-05
There actually was a Linux Home Server project but last I heard it died.

---

### Post by spiderbatdad on 2009-02-05
How are these suggestions not browser based?
Apache and ssh can both work with browsers. Apache can index files just as ssh can. Screenshots of my server. First apache then ssh

You might be interested in proftp

---

### Post by Kronos2785 on 2009-02-05
I know of those solutions, However what I need is an entire browser solution for the uploading, downloading and navigation of files like the screen shots I posted.

I'm guessing there is currently nothing that fullfils that role in the Linux world?

---

### Post by quietas on 2009-02-05
A quick google for php file manager came back with a bunch. [http://www.blueshoes.org/en/applications/filemanager/](http://www.blueshoes.org/en/applications/filemanager/) looks good though

---

### Post by Kronos2785 on 2009-02-06
Thanks Quietas, that's along the lines of what I am looking for, however looking at their site the File Manager application is only able to be purchased, there is not free or developer access to it.

regards,
Kronos

---

### Post by volkswagner on 2009-02-06
> **spiderbatdad said:**
> ........
HMMMM. re-read your post. openssh is also ideal for what you are talking about, and on second thought, is even easier to configure:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)


As spiderbatdat suggested openssh would be the simplest to setup.  Although it is not browser based it is easy to connect and can be secured by quality passwords, hosts allow and deny, and failtoban.

If you were strictly after a browser base you could install [Webmin]("http://www.webmin.com/cgi-bin/search_third.cgi?modules=1").  It would allow total control of the server remotely.  There is a java plugin file manager.  It would even let you edit files without downloading locally.

Depending on your Dads work scenario, I can understand why you may want browser based, especially if he is not allowed to install programs to run the ssh client.

---

### Post by Kronos2785 on 2009-02-06
Yeah, if he had the ability to install such programs on his workstation, it wouldn't be as much of a problem, but his workstation tends to be different each month as he moves around the office filling in different positions

Unfortunately, there doesn't seem to be a linux equivalent to the feature in WHS that offers such an integrated and seemless experience. One login on the server set up which grants the ability to access shares anywhere in the world.

It would also be a bonus to get this running, as I'd then be able to be more effecient with my own collaborations in my neighbourhood, with the ability to provide my local club a file server they can all access for club business.

Normally I don't condone Linux copying something directly that's in windows or macOS except when the feature is well implemented and benifical like this feature is in Windows Home Server.

regards,
Kronos

I'll keep searching

---

### Post by Skyride on 2009-02-06
but WHY browser based is the bit i REALLY dont get. Webmin is fantastic.

Best thing to do would be setup a VPN and samba or FTP and get your dad Filezilla client on a pen drive (see: [http://portableapps.com/](http://portableapps.com/) )

---

### Post by quietas on 2009-02-06
> **Skyride said:**
> but WHY browser based is the bit i REALLY dont get. Webmin is fantastic.

Best thing to do would be setup a VPN and samba or FTP and get your dad Filezilla client on a pen drive (see: [http://portableapps.com/](http://portableapps.com/) )

Because Webmin is not easy. Filezilla again is not easy. I have used the WHS interface, it is easy. Hell, it even has a dynamic DNS client, internet aware web front end, and remote access off the local network. It just works.

Honestly if WHS works for you I'd recommend it. 95 bucks from Newegg (plus s/h) is relatively cheap.

---

### Post by Kronos2785 on 2009-02-06
Unfortunately, I don't live in America, but Australia, and it seems that I can't find a store that sells it. Only sells pre-built servers with it installed. That's why the search for a linux equivalent. 

I can put up without the easy to use backup features of WHS (windows computers registered on the server have backups automatically pulled from them). Even the ease of setting up a 2nd website on a WHS is easy, but I could forgo that. It is the Web FIle interface which is what makes it so appealing.

I'll keep searching for a linux equivalent.

I might have found one in [PHP File Navigator]("http://pfn.sourceforge.net/index.php") but i'm not sure how easy that will be to set up.

regards,
Kronos

p.s. skyride, My Dad works for the government and the computer workstations have had ALL usb ports either removed, or filled with super glue!

---


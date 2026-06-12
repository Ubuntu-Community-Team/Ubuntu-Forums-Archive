---
title: "Home Server Website Possibility?"
date: 2012-12-02
forum: Server Platforms
---

### Post by BStrizzy on 2012-12-02
Hey guys,
I am just wondering if it is possible to create a simple webite for my home server. I currently store school files, music, movies, ect.. on it and I am the solo user (for now). I am average at html/css and know what I am doing when it comes to the visual part, but I am not sure how I would incorporate files from my server with it. for instance if I got another computer inmy house how can I go to that website and stream/download/upload to the server? I know this is possible and would like the experience in bother webdesign/networking, just need solid direction. 

Thanks!

---

### Post by lisati on 2012-12-02
*Thread moved to **Server Platforms**.*

Ubuntu server edition would be ideal for such a project: the link in my sig "What on earth is a Lisati?" is hosted with the server edition.

On the software side, [Apache2]("https://help.ubuntu.com/10.04/serverguide/httpd.html") is good for hosting web pages. There are other options, which others might mention if needed.

For connectivity with the outside world, you are likely to need to organize a domain name: services such as [no-ip]("http://no-ip.com") have "free" options that can sometimes be useful when starting out. You will also need to organize port forwarding on your router for the relevant services to your server.

---

### Post by Cheesemill on 2012-12-02
Instead of coding the whole thing yourself you could take a look at some of the projects that already exist such as [AjaXplorer]("http://ajaxplorer.info/") and [ownCloud]("http://owncloud.org/").

---

### Post by itpro007ca on 2012-12-02
@BStrizzy: 

As pointed out: all you need is: Apache2,or the LAMP[(L)inux,(A)pache,(M)ySQL,(P)HP] Stack,if you really want to dive in,and from looking at the website for Ajaxplorer(PHP5 required) and ownCloud,they might be good addons,too.

Thanks,Cheesemill and Lisati,I've been looking into this also.

I had the LAMP Stack installed awhile back,but went away from Ubuntu Server to try another Linux briefly,then had to have a bad Power Supply replaced(could've done it myself,but wasn't sure if it was the Power Supply,or the Motherboard,and don't have the test resources,so sent it out),so I'm back up now,planning to get back to playing around with LAMP shortly!

Cheers,
Richard

---

### Post by darkod on 2012-12-02
If you only need the stream/upload/download you mentioned, you don't even need a webpage or webserver.

The upload/download is write/read to a network storage location. Just use simple Samba for that and both windows and ubuntu can access the shares and use the files.

The stream part also depends how are you accessing it. For example, if you use a media player to open a media file, reading the file from the share is enough.
On the other hand, if some device in your home expect to find a working media server (like a TV ttrying to play a movie) you can install something like MiniDLNA or Twonky.

In any case, a webpage is not necessary in the above scenarios and only makes things more complicated.

---

### Post by BStrizzy on 2012-12-02
> **lisati said:**
> *Thread moved to **Server Platforms**.*

Ubuntu server edition would be ideal for such a project: the link in my sig "What on earth is a Lisati?" is hosted with the server edition.

On the software side, [Apache2]("https://help.ubuntu.com/10.04/serverguide/httpd.html") is good for hosting web pages. There are other options, which others might mention if needed.

For connectivity with the outside world, you are likely to need to organize a domain name: services such as [no-ip]("http://no-ip.com") have "free" options that can sometimes be useful when starting out. You will also need to organize port forwarding on your router for the relevant services to your server.

Awesome I will look into this, but I will just be using this home server website to be a local thing. I do not want it out on the air.

---

### Post by BStrizzy on 2012-12-02
> **Cheesemill said:**
> Instead of coding the whole thing yourself you could take a look at some of the projects that already exist such as [AjaXplorer]("http://ajaxplorer.info/") and [ownCloud]("http://owncloud.org/").

hey yeah I will take a look at this, I will probably use that and just modify it, assuming it is open source. Do i need lamp or apachee for any of this stuff? and can you give me a run down of what and why I need them for my own server?  i figured I would only use it to make my site availible to anyone in the world. maybe i need it for local websites too to access the files?(im assuming?)

---

### Post by BStrizzy on 2012-12-02
> **itpro007ca said:**
> @BStrizzy: 

As pointed out: all you need is: Apache2,or the LAMP[(L)inux,(A)pache,(M)ySQL,(P)HP] Stack,if you really want to dive in,and from looking at the website for Ajaxplorer(PHP5 required) and ownCloud,they might be good addons,too.

Thanks,Cheesemill and Lisati,I've been looking into this also.

I had the LAMP Stack installed awhile back,but went away from Ubuntu Server to try another Linux briefly,then had to have a bad Power Supply replaced(could've done it myself,but wasn't sure if it was the Power Supply,or the Motherboard,and don't have the test resources,so sent it out),so I'm back up now,planning to get back to playing around with LAMP shortly!

Cheers,
Richard


ok can you just give me a run down on why i need lamp and apachee again

---

### Post by Cheesemill on 2012-12-02
To run any sort of website you need a web server, Apache has been mentioned several times because it is the most popular web server available (most of the worlds websites run on Apache).

For anything more than static HTML pages the most popular approach is to use the PHP scripting language and the MySQL database program along with Apache to allow for dynamic sites. This is where the LAMP acronym comes in (**L**inux, **A**pache, **M**ySQL, **P**HP).

Once you have LAMP set up there are a large number of open source website frameworks available for you to install on your server to save you doing all the coding yourself; these range from content management systems ([Wordpress]("http://wordpress.org/"), [Joomla]("http://www.joomla.org/") and [Drupal]("http://drupal.org/")) to webmail systems ([Squirrelmail]("http://squirrelmail.org/about/"), [Roundcube]("http://roundcube.net/")) as well as photo galleries ([ZenPhoto]("http://www.zenphoto.org/")) and file management websites ([AjaXplorer]("http://ajaxplorer.info/"), [OwnCloud]("http://owncloud.org/")) to name just a few.

Why would you want to use these? That's down to your own imagination :)


If all you want to do is have a file server to share files throughout your home you don't actually need any of this, you can just set up [Samba]("https://help.ubuntu.com/community/Samba") on your server and it will appear as a network drive on your other computers. However, your initial post was asking about setting up a website on your home server so this is why everyone has been mentioning Apache.

---

### Post by darkod on 2012-12-02
In case you missed my post #5 just to remind you to read it.

I also think you don't need any of this and that your first question was asked wrongly.

Webservers are not used for sharing files (although you can do that with FTP protocol), network shares are used for sharing files in a private home network.

---

### Post by Habitual on 2012-12-02
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
surely will be needed sooner or later.  :)

---

### Post by BStrizzy on 2012-12-02
> **Habitual said:**
> [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
surely will be needed sooner or later.  :)

booked marked immediately, liked the first paragraph and already knew it would be useful. Thanks :)

---

### Post by george897 on 2012-12-03
To run any of website you need a server & web hosting for this you can take a service of any web hosting service provider or maintain your own server from home.

---

### Post by BStrizzy on 2012-12-03
> **darkod said:**
> If you only need the stream/upload/download you mentioned, you don't even need a webpage or webserver.

The upload/download is write/read to a network storage location. Just use simple Samba for that and both windows and ubuntu can access the shares and use the files.

The stream part also depends how are you accessing it. For example, if you use a media player to open a media file, reading the file from the share is enough.
On the other hand, if some device in your home expect to find a working media server (like a TV ttrying to play a movie) you can install something like MiniDLNA or Twonky.

In any case, a webpage is not necessary in the above scenarios and only makes things more complicated.

yeah your right, i would just like to have one for personal use/experience. i just want to "create" something

---

### Post by BStrizzy on 2012-12-03
> **Cheesemill said:**
> Instead of coding the whole thing yourself you could take a look at some of the projects that already exist such as [AjaXplorer]("http://ajaxplorer.info/") and [ownCloud]("http://owncloud.org/").

i tried owncloud but it is kinda limited. I was hoping to get like full access to everything on my server. Like my own website for my self with a cool way to access my files and down load them, lets say from drop down bars, or my own search engine.. is there anything of that you know? cause that will be a long project for me

---

### Post by itpro007ca on 2012-12-06
> **BStrizzy said:**
> i tried owncloud but it is kinda limited. I was hoping to get like full access to everything on my server. Like my own website for my self with a cool way to access my files and down load them, lets say from drop down bars, or my own search engine.. is there anything of that you know? cause that will be a long project for me

Depending on what you want to do?:

*Do want to share files over a Windows Network -SAMBA
*Linux Network -NFS
*Do to want to play videos on your TV from your 'Server'?
*If you have a Playstation 3(I do) - 'PS3 Media Server.'
*If you want to have local (or online website -check your ISP's Term Agreement ,FIRST!) -LAMP

There are several good how to sites for Ubuntu,or Linux Home Server...ie: search :"Linux Home Server."

---

### Post by Habitual on 2012-12-07
> **BStrizzy said:**
> Awesome I will look into this, but I will just be using this home server website to be a local thing. I do not want it out on the air.

And there is the mandatory Security concerns that go along with self-hosting.
Same a a Dedicated Server, All Yours, Captain!

Installing a Intraweb webserver would be safe as long as there is a router in front of your network connection.

DNS would be an issue - 
You would have to access the site internally via ipa.ddr.ess or resolve the domain(.com) with BIND, or /etc/hosts edit(s).

So, if [http://127.0.0.1](http://127.0.0.1) is acceptable, then install away and have fun learning.

---


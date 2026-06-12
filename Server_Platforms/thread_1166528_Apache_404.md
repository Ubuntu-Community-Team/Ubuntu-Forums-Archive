---
title: "Apache 404"
date: 2009-05-21
forum: Server Platforms
---

### Post by Mosaab on 2009-05-21
Hello, I am new to linux in general .. and new to apache.
when I start apache in webmin it gives me this error:
Failed to start apache :

 * Starting web server apache2
apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
   ...fail!

when I go to /etc/apache2/apache2.conf and comment the line (include /etc/apache2/sites-enabled/) apache starts .. but when I try [http://localhost](http://localhost) its gives me a 404 message.

help please :)

---

### Post by Mosaab on 2009-05-21
I removed the symbolic link 000-default from /etc/apache2/sites-enabled/ and now its giving my another error about too many sybolic link level or something like that.

---

### Post by Mosaab on 2009-05-21
I am not sure exactly what I did but it worked...

the problem is that how can I make another virtual directory ?

for example is I want this url (localhost/other) to open another website is some other location?

---

### Post by apel_2804 on 2009-05-22
This will help you:

[http://www.tbaumi.de/blog/?p=72](http://www.tbaumi.de/blog/?p=72)

---

### Post by Mosaab on 2009-05-22
indeed it did help me ... it works now. thank you.

but when I try to access this website from another computer in the lan .. the browser goes to the internet and looks for the website in the net! why that happens.
in my computer (the server) I used this [http://localhost/opengoo](http://localhost/opengoo) and it worked.
in the other computer I used [http://192.168.1.102/opengoo](http://192.168.1.102/opengoo) but it didnt work.

---

### Post by apel_2804 on 2009-05-22
What client (OS and Browser) do you use to connect to [http://192.168.1.102/opengoo](http://192.168.1.102/opengoo) ?

Fiefox will redirect you if he didn't found the requested address. Are you shure that 192.168.1.102 is the ip of your server? Is there an DHCP server (router eg) running? If not and you are using static ip's you can "register" your server ip in your clients /etc/hosts (linux) or \Windows\system32\drivers\etc\hosts (windows) file.

---

### Post by Mosaab on 2009-05-22
thanks for replying..

My router provides the DHCP service, and yes I am sure its the servers ip address cause I ifconfig and used the ip provided by this command.

and does it matter what is the browser or the OS of the client ? its HTTP anyway!!

---

### Post by cariboo on 2009-05-23
You are making thngs hard for yourself by using dhcp. I would suggest setting a static ip address for your server.

This isn't the best way to do it, but I uninstall the dhcp client:

```
sudo apt-get purge dhcp3-client
```

then edit /etc/network/interfaces to set the static ip address so that it looks similar to this:

```
# The primary network interface
auto eth0
iface eth0 inet static
address		192.168.1.250
netmask		255.255.255.0
broadcast	192.168.1.154
gateway		192.168.1.1
```

Then edit /etc/hosts to point a name to the ip address of the server, this is my hosts file:

```
27.0.0.1	localhost
127.0.1.1	alexis-karmic
192.168.1.250	willy
192.168.1.202	minibuntu
192.168.1.1	router
```

in the above example willy and minibuntu are servers. To access a web page on willy, I enter [http://willy/](http://willy/) in firefox.

---

### Post by Mosaab on 2009-05-23
I dont think this is the problem.. cause I went to the otehr windows machine and I got the IP and went back to linux machine and pinged ... it actually pings another computer in the internet.!!

---

### Post by Mosaab on 2009-05-23
I have noticed somethign weird ... when I ping any name which is not is my lan ... it pings this : 208.43.232.224-static.reverse.softlayer.com  ALL THE TIME !!!!

even when I try this command:

ping adsljfhacbnljhsjlfhbvskljfhbvklfhbvlkj

I dont think there is a computer over the net called adsljfhacbnljhsjlfhbvskljfhbvklfhbvlkj

---

### Post by Mosaab on 2009-05-23
actually I have edited the hosts file as you said .. it worked .. but this is was not the case ... actually i played around alot with webmin and it seems I missed up something .. can you figure out what did I do from the story ?

---

### Post by Mosaab on 2009-05-25
ok .. this may clarify something, when I use [http://192.168.1.102](http://192.168.1.102) from the other computer to access the website. the URL will be resolved to [http://localhost/.....(and](http://localhost/.....(and) the rest of the url.

Why ?

---

### Post by Henrike Corinna on 2009-05-25
Hi,

        
**[SIZE=2][B]404.php Installation:**[/SIZE][/B]


Upload zip/tar.gz file to the /wp-content/plugins/ directory and unzip.
Activate the plugin through the ‘Plugins’ menu in WordPress.
Go to your Options Panel and open the “AA Google 404&#8243; submenu. /wp-admin/options-general.php?page=askapache-google-404.php
Enter in your Google Search API Key and hit the “Update Key” Button. 
Add the code to your 404.php template page by including <?php if(function_exists('aa_google_404'))aa_google_404();?> in your main content area.

---

### Post by Mosaab on 2009-05-25
I Am so sorry but I dont know what is this .. its maybe alittle bigger than me..lol

---

### Post by Mosaab on 2009-05-25
actually the host names problem was solved ... adding "wins" at the end of the host line in file /etc/nsswitch.conf  solved the problem.

but it didnt solve accessing the website in apache by another computer other than the local host.

the exact problem is when I write the following in the browser of the client computer:

[http://192.168.1.102](http://192.168.1.102) (Which is the address of apache server machine)

it will be resolved as [http://localhost/opengoo](http://localhost/opengoo)

which will obviously makes the browser of the client report a broken link or a 404 page.

why does the browser resolve the ip to LOCALHOST ? i want the url at least to stay the same !! while it actually supposed to be resolved to the server name.!!

---

### Post by Mosaab on 2009-05-27
any one experienced this before I cant find a solution for it online !

---

### Post by dwayne.hale on 2009-07-02
okay from what I gather you have a router dishing out DHCP scope to the client machines?
When you type in your web browser any address (even like ubuntu.com) it auto defaults to http:// because it is asking for hyper text transfer protocol and not Remote Desktop Protocol or some other protocol. 
So it will always show up as [http://(server](http://(server) IP) unless your on the local box. Now your problem sounds like something may be airy in the way apache sees the web. 
A really awesome guide is here: [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
Basically it sounds like apache has a static IP set in the httpd.conf file which is in the /etc/apache2 directory. There is a line in there that you may have to comment out or add to in order to get it viewable from other PC's on the same lan.
LocalHost always works on the linux box because your basically telling it to only look on that box. Try the IP address of the ubuntu box from the Ubuntu box. You may also have to modify the apache2.conf file so that it no longer tells apache just to listen to port 80 with no ip.
Follow the guide and you'll be fine.

---

### Post by killboymota on 2010-11-30
im using vbulletin and i cannot see any forum or specific thread but i cant access to the admin panel or use the search box.

any static page is not showing...

---


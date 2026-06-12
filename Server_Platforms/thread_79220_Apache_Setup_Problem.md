---
title: "Apache Setup Problem"
date: 2005-10-19
forum: Server Platforms
---

### Post by steveman on 2005-10-19
Hi all,

I'm currently using a Ubuntu/Apache server to handle our company website.   All is working fairly smoothly but....

I'd like people to be able to access stuff from subdirectories directly.  ie if someone types [http://www.xxx.com/somedir](http://www.xxx.com/somedir) into their browser, I'd like them to get what's in somedir.  At the moment when they do, it always brings up the root page (ie just what's at [http://www.xxx.com)](http://www.xxx.com)).  If I provide a link to somedir from the main page, that works fine.  Additionally, I can get to somedir directly from within our network if I just use the ip address of the server instead of the domain name.

I'm using everything pretty much straight out of the box in terms of apache setup (single virtual host, all under /var/www).  Any thoughts?

Cheers,
Steve

---

### Post by cvmostert on 2005-10-30
I have a little problem installing apache aswell.. when i start apache it says that i have a bad group name... in the how-to's it said to chance the user and group names to MY user and group names... how do i know what my group name is?

sorry that i can not help with your problem, all the best.

---

### Post by LordHunter317 on 2005-10-30
[QUOTE=steveman]I'm using everything pretty much straight out of the box in terms of apache setup (single virtual host, all under /var/www).  Any thoughts?[/quote]Post your directory structure: ls -lR

[quote=cvmostert]I have a little problem installing apache aswell.. when i start apache it says that i have a bad group name... in the how-to's it said to chance the user and group names to MY user and group names... how do i know what my group name is?[/quote]Whatever howto told you to do this was wrong.  Apache should always run as www-data:www-data on Ubuntu.  

Now, you should change permissions on /var/www, but that's different.

---

### Post by cvmostert on 2005-10-30
thank you! i changed it back and i seem to be able to go on with the setup..

---

### Post by steveman on 2005-10-30
[QUOTE=LordHunter317]Post your directory structure: ls -lR
[/QUOTE]

Thanks for looking....

```


root@aragorn:/var/www # ls -lR
.:
total 20
drwxrwxr-x  4 root root 4096 Oct 19 09:20 Oxfam05
drwxr-xr-x  2 root root 4096 Oct 19 15:51 apache2-default
drwxr-xr-x  2 root root 4096 Jul 11 16:49 images
-rw-r--r--  1 root root  385 Jul 11 16:46 index.html
-rw-r--r--  1 root root  873 Oct 20 09:54 regal.html

./Oxfam05:
total 76
-rwxrw-r--  1 root root  345 Oct 18 17:35 caption.html
drwxrwxr-x  2 root root 4096 Oct 19 08:26 images
-rwxrw-r--  1 root root  392 Oct 18 17:35 imageset.html
-rwxrw-r--  1 root root  386 Oct 18 17:35 index.html
-rwxrw-r--  1 root root 1874 Aug 23 05:05 logo.gif
-rwxrw-r--  1 root root 1119 Jun  1 08:36 style.css
-rwxrw-r--  1 root root  569 Oct 18 17:35 target0.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target1.html
-rwxrw-r--  1 root root  568 Oct 18 17:35 target10.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target2.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target3.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target4.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target5.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target6.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target7.html
-rwxrw-r--  1 root root  623 Oct 18 17:35 target8.html
-rwxrw-r--  1 root root  624 Oct 18 17:35 target9.html
drwxrwxr-x  2 root root 4096 Oct 19 08:26 thumbnails
-rwxrw-r--  1 root root 2259 Oct 18 17:35 thumbnails.html

./Oxfam05/images:
total 872
-rwxrw-r--  1 root root     94 Oct 18 17:35 Picasa.ini
-rwxrw-r--  1 root root  73617 Oct 18 17:35 img_0082.jpg
-rwxrw-r--  1 root root  81862 Oct 18 17:35 img_0083.jpg
-rwxrw-r--  1 root root  88240 Oct 18 17:35 img_0084.jpg
-rwxrw-r--  1 root root 150452 Oct 18 17:35 img_0086.jpg
-rwxrw-r--  1 root root  75599 Oct 18 17:35 img_0088.jpg
-rwxrw-r--  1 root root  57358 Oct 18 17:35 img_0090.jpg
-rwxrw-r--  1 root root  77299 Oct 18 17:35 img_0091.jpg
-rwxrw-r--  1 root root  78427 Oct 18 17:35 img_0092.jpg
-rwxrw-r--  1 root root  57907 Oct 18 17:35 img_0093.jpg
-rwxrw-r--  1 root root  41604 Oct 18 17:35 img_0095.jpg
-rwxrw-r--  1 root root  48948 Oct 18 17:35 img_0097.jpg

./Oxfam05/thumbnails:
total 128
-rwxrw-r--  1 root root    94 Oct 18 17:35 Picasa.ini
-rwxrw-r--  1 root root  9417 Oct 18 17:35 img_0082.jpg
-rwxrw-r--  1 root root 11923 Oct 18 17:35 img_0083.jpg
-rwxrw-r--  1 root root  9272 Oct 18 17:35 img_0084.jpg
-rwxrw-r--  1 root root 12220 Oct 18 17:35 img_0086.jpg
-rwxrw-r--  1 root root  9393 Oct 18 17:35 img_0088.jpg
-rwxrw-r--  1 root root  8785 Oct 18 17:35 img_0090.jpg
-rwxrw-r--  1 root root  7863 Oct 18 17:35 img_0091.jpg
-rwxrw-r--  1 root root  9642 Oct 18 17:35 img_0092.jpg
-rwxrw-r--  1 root root  9063 Oct 18 17:35 img_0093.jpg
-rwxrw-r--  1 root root  6835 Oct 18 17:35 img_0095.jpg
-rwxrw-r--  1 root root  8259 Oct 18 17:35 img_0097.jpg

./apache2-default:
total 148
-rw-r--r--  1 root root 2326 Nov 22  2004 apache_pb.gif
-rw-r--r--  1 root root 1385 Nov 22  2004 apache_pb.png
-rw-r--r--  1 root root 2414 Nov 22  2004 apache_pb2.gif
-rw-r--r--  1 root root 1463 Nov 22  2004 apache_pb2.png
-rw-r--r--  1 root root 2160 Nov 22  2004 apache_pb2_ani.gif
-rw-r--r--  1 root root 1664 Sep  6 00:13 index.html.ca
-rw-r--r--  1 root root 1584 Sep  6 00:13 index.html.cz.iso8859-2
-rw-r--r--  1 root root 2203 Sep  6 00:13 index.html.de
-rw-r--r--  1 root root 1509 Sep  6 00:13 index.html.dk
-rw-r--r--  1 root root 1829 Sep  6 00:13 index.html.ee
-rw-r--r--  1 root root 1619 Sep  6 00:13 index.html.el
-rw-r--r--  1 root root 1457 Sep  6 00:13 index.html.en
-rw-r--r--  1 root root 1736 Sep  6 00:13 index.html.es
-rw-r--r--  1 root root 1868 Sep  6 00:13 index.html.et
-rw-r--r--  1 root root 1506 Sep  6 00:13 index.html.fr
-rw-r--r--  1 root root 3705 Sep  6 00:13 index.html.he.iso8859-8
-rw-r--r--  1 root root 1605 Sep  6 00:13 index.html.hr.iso8859-2
-rw-r--r--  1 root root 1789 Sep  6 00:13 index.html.it
-rw-r--r--  1 root root 1631 Sep  6 00:13 index.html.ja.iso2022-jp
-rw-r--r--  1 root root 1544 Sep  6 00:13 index.html.ko.euc-kr
-rw-r--r--  1 root root 1838 Sep  6 00:13 index.html.lb.utf8
-rw-r--r--  1 root root 1969 Sep  6 00:13 index.html.nl
-rw-r--r--  1 root root 1535 Sep  6 00:13 index.html.nn
-rw-r--r--  1 root root 1468 Sep  6 00:13 index.html.no
-rw-r--r--  1 root root 1439 Sep  6 00:13 index.html.po.iso8859-2
-rw-r--r--  1 root root 1774 Sep  6 00:13 index.html.pt
-rw-r--r--  1 root root 2047 Sep  6 00:13 index.html.pt-br
-rw-r--r--  1 root root 1523 Sep  6 00:13 index.html.ru.cp-1251
-rw-r--r--  1 root root 1516 Sep  6 00:13 index.html.ru.cp866
-rw-r--r--  1 root root 1521 Sep  6 00:13 index.html.ru.iso-ru
-rw-r--r--  1 root root 1517 Sep  6 00:13 index.html.ru.koi8-r
-rw-r--r--  1 root root 2250 Sep  6 00:13 index.html.ru.utf8
-rw-r--r--  1 root root 1632 Sep  6 00:13 index.html.sv
-rw-r--r--  1 root root 2401 Nov 22  2004 index.html.var
-rw-r--r--  1 root root 1016 Sep  6 00:13 index.html.zh-cn.gb2312
-rw-r--r--  1 root root 1033 Sep  6 00:13 index.html.zh-tw.big5
-rw-r--r--  1 root root   26 Sep  6 00:22 robots.txt

./images:
total 8
-rw-r--r--  1 root root 7538 Jul 11 16:48 regalfm_logo.gif



```

---

### Post by cvmostert on 2005-10-31
LordHunter... i have setup the Apache2 server and i can view the pages in the ../www directory, now i want to view them from other computers... I will read more about it, but if there is a quick answer, it would be greatly appreciated.
Thanx

---

### Post by dbee on 2005-10-31
>  i can view the pages in the ../www directory, now i want to view them from other computers... 

What other computers ???
Other computers on your LAN or other computers worldwide ???

---

### Post by cvmostert on 2005-11-01
Both LAN and worldwide, how do i give access to browse this directory.
Or am i making a mistake? I thought that the /www directory will be the root dir of the "server"?

Damn! I dont like it not knowing anything about servers... hopefully after this ill be able to say a few words on it :-)

---

### Post by dbee on 2005-11-01
the server serves documents from 

/var/www/

you should be able to access it by default from pretty much anywhere you can access your computer on port 80 from. 
If you can't reach the computer or you can't reach port 80 on your computer then you're out of luck.

Point your browser to your server computer 
If it doesn't work then try to telnet your server
If that doesn't work then try to ping it
If that doesn't work, then try plugging it in :razz: (only joking)

Do you have a firewall installed on your ubuntu server ?

Try 
```

iptables -L

```

---

### Post by cvmostert on 2005-11-03
```
root@ubuntu:/home/chris # iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```



i can see my pc from my browser, but it is the same pc! when i try to see the page from my other pc, it does not want to show... the ping was sucsessfull though.

Did i mention that i have a router? Is it important? I also have a dinamic ip. 

how do i view my page through a router? probably not just the ip given by the router?

ok, i am new at this but i want to solve the problem.

thanx in advance!

---

### Post by dbee on 2005-11-03
Ok, so let me get this clear. 

You can see your webpage on localhost (your server computer), but you can't see it from any other computer.  But you can ping the server.

What kind of router are you using ? one of the home ones ?
Did you set the router firmware yourself or is it out of the box ?

try to enter this on the command line of your remote computer (where xxx is the ip address of your server)
```

telnet xxx.xxx.xxx.xxx 80

```

then if you get through, type in this

```

GET / HTTP/1.0

```

apache should give you the index.html sheet in your www/ directory

... if you can't do the first bit then I'd imagine that your router is blocking port 80.
If you can't do the second part then I'd imagine that it's an apache/browser issue.

---

### Post by cvmostert on 2005-11-10
dbee, it was the router that had to be activated on port 80, i looked around at the settings and activated a web server with port 80. works fine now. 

have a dinamic ip and also sorted that with a free service to update the ip and point it to the adress when needed.

thanx for your help anyway.

---


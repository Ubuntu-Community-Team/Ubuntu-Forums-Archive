---
title: "Error on APache restart"
date: 2011-09-23
forum: Server Platforms
---

### Post by Atsuisofu on 2011-09-23
SO I am kind of a n00b with virtual hosts and I was trying to setup a domain on my server for a friend using virtual hosts. I have gotten the domain to point to my ip address than used apcahe2's virtual hosts and user folder mod to create a user and have the domain point to the right folder. My only issue is that it only works for fliponcomputers.com and when I type in [www.fliponcomputers.com](www.fliponcomputers.com) it goes to the main directory of the server not the user virtual host defined one. I added a bit of code to the httpd.conf
```

NameVirtualHost fliponcomputers.com:80

<VirtualHost fliponcomputesr.com:80>
ServerName www.fliponcomputers.com
ServerAlias fliponcomputers.com *.fliponcomputers.com
DocumentRoot /home/xionide/public_html/
</VirtualHost>

```
 Now that I added that the site works with and without the www prefix the only issue is now that i get an error from apache everytime I restart it. The error is below I know I must be doing something wrong either in my httpd.conf or in my sites-enabled but I cant tell I'm sure someone on here can just know what I am doing wrong I cant for the life of me figure this out.
```

atsuisofu@atsuisofu-ProLiant-DL385-G1:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Fri Sep 23 12:02:06 2011] [warn] NameVirtualHost fliponcomputers.com:80 has no VirtualHosts
 ... waiting [Fri Sep 23 12:02:07 2011] [warn] NameVirtualHost fliponcomputers.com:80 has no VirtualHosts

```

Thanks for reading
Regards,

Ethan

---

### Post by Atsuisofu on 2011-09-23
Now it isnt even working with making [www.fliponcomputers.com]("http://www.fliponcomputers.com") and fliponcomputers.com go to the proper folder only the www. So I must have something really messed up

EDITTT

sorry didnt know I could edit 1st post.

So i have figured out why I was getting that error I was putting the [www.fliponcomputers.com]("http://www.fliponcomputers.com") as the virtual host name when it was infact something else. I still cannot seem to get both [www.fliponcomputers]("http://www.fliponcomputers") and flipon computers to point to the proper directory.

2nd Edit

So now I have found that if in httpd.conf I change
NameVirtualHost fliponcomputers.com:80  <VirtualHost fliponcomputesr.com:80> 
TO

NameVirtualHost *:80  <VirtualHost *:80>

I get it the site to function on both [www.fliponcomputers.com](www.fliponcomputers.com) and fliponcomputers.com

But than I get an error from apache2 when I restart
```

atsuisofu@atsuisofu-ProLiant-DL385-G1:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Fri Sep 23 12:26:03 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Fri Sep 23 12:26:05 2011] [warn] NameVirtualHost *:80 has no VirtualHosts

```

---

### Post by silexh on 2011-09-23
I'm quite a noob myself, but this is what I would try:

/etc/apache2/httpd.conf
```

NameVirtualHost *:80

```

/etc/apache2/sites-available/fliponcomputers
```

<VirtualHost *:80>
ServerName www.fliponcomputers.com
ServerAlias fliponcomputers.com *.fliponcomputers.com
DocumentRoot /home/xionide/public_html/
</VirtualHost>

```

Enable it with:
```
sudo a2ensite fliponcomputers
```

That's about how I have it configured.

EDIT: Just looked again, and I commented the 'NameVirtualHost' bit, it gave me errors. Still works like a charm though...
EDIT2: You also misspelled <VirtualHost fliponcomputesr.com:80> ;)

---

### Post by Atsuisofu on 2011-09-23
Awesome it worked! I commented out that line you said and no more error and it still works. Thanks a bunch yeah i realized I typed those wrong as well I am a horrible typist I cant feel my fingers do to nerve damage so it makes it interesting lol. 

Thanks again!

---

### Post by silexh on 2011-09-23
Glad it worked!:D

---


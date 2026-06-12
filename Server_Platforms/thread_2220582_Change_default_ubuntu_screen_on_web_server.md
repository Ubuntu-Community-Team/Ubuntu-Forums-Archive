---
title: "Change default ubuntu screen on web server"
date: 2014-04-28
forum: Server Platforms
---

### Post by Jordan_Hickin on 2014-04-28
Hi guys

How do i change the default ubunter web server screen on my web server.

I want it to show my web page. I have ftp but i don't know where to upload the file to.

Also i have a second account for a second website. But for some reason I can't get it up. 

The web server is LAN IP is 192.168.0.7

This bring up the default screen which i want to change.

192.168.0.7/webuser1 just bring up 404 not found

Hope you can help :)

---

### Post by Jordan_Hickin on 2014-04-28
Hi guys.

Two problems... i have just setup a web server and can access the default ubuntu page at 192.168.0.7. I have setup ftp on the server. How do i change the default page to my personal page?

Also, i set up an additional user Webuser1. However when i try to get to 192.168.0.7/webuser1 it just says 404 Not Found.

I was following this: [http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm](http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm)

Can you help?

---

### Post by Iowan on 2014-04-28
Please don't create multiple threads on the same topic - it dilutes community effort.
Threads merged.

---

### Post by Jordan_Hickin on 2014-04-28
> **Iowan said:**
> Please don't create multiple threads on the same topic - it dilutes community effort.
Threads merged.

Was going to remove the one from general help as i found the server forum :) But thanks anyway

---

### Post by thufirhawat2 on 2014-04-28
Hey man, I think we could use a little more info about your setup. First of all, which version of Ubuntu server did you install? If you installed any version below 14.04, your web page directory will be different than for server 14.04 or above. 

In either case, you have to locate your apache2 host directory on your server. That tutorial does not seem to clarify the fact that apache is the package that is hosting your webpage, but that is what we are dealing with here. So if you installed Trusty Tahr (14.04) then the directory in question is /var/www/html. If you did Precise Pangolin (12.04) then the directory will be /var/www. Inside that directory you will find a document called index.html. That is what apache is serving up on port 80. I personally just moved that document out of the directory and renamed the site I made index.html and moved it into the directory. I have a feeling that there is probably a better way to do that, and I am sure someone on here will point it out, but I am a bit lazy, and I am only an amateur when it comes to building websites. When you move your document in the place of the existing index.html, it should server your page up.

As far as ftp goes, I used to use vsftpd, but I have never tried proftp. I personally just use SSH on my Linux machines, and FileZilla client on my windows machines to upload/download files from the server via SSH. It is more secure than standard FTP, and there is no extra setup to deal with. However, if you are trying to FTP to a server with a particular local username, you typically would not go to [http://server/user](http://server/user), you would normally do [ftp://server](ftp://server). Once the page loads, it should prompt you for the username and password, here is where you would type webuser1 and the password you created for that user.

Hope this helps, let me know if anything was unclear.

---

### Post by Jordan_Hickin on 2014-04-28
Hi...

More information.. well I have setup ftp using proftp.

I am using 14.04 i believe.

I keep getting this:

```

ftp> put /home/jordan/Desktop/index.html /var/www/html/index.html
local: /home/jordan/Desktop/index.html remote: /var/www/html/index.html
200 PORT command successful
550 /var/www/html/index.html: Permission denied

```

Maybe i am doing it wrong. I am new to this.

And how do i get access to the webuser1 site?

---

### Post by Jordan_Hickin on 2014-04-28
I have just got access to the Ubuntu Default Webpage html code by doing

```

root@webserver1:/home/adminjah# vi /var/www/html/index.html


```

So i can change the ubuntu page... how do i completely replace it via ftp?

---

### Post by thufirhawat2 on 2014-04-28
> **Jordan_Hickin said:**
> I have just got access to the Ubuntu Default Webpage html code by doing

```

root@webserver1:/home/adminjah# vi /var/www/html/index.html


```

So i can change the ubuntu page... how do i completely replace it via ftp?

So with FTP you cannot normally load things directly to the /var/www/html directoy unless you have some screwy permissions changes made, which I do not advise. So if you can upload you page into your home directory, you can then move it using a command on the server, something like this:
```
sudo mv /var/www/html/index.html /var/www
```

This will move the default webpage out of the host directory.

```
sudo mv /home/user/index.html /var/www/html
```

This will move the page you uploaded into your home directory to the webserver's host directory. Change user in the command above to the username you are using.

---

### Post by Jordan_Hickin on 2014-04-28
> **thufirhawat2 said:**
> So with FTP you cannot normally load things directly to the /var/www/html directoy unless you have some screwy permissions changes made, which I do not advise. So if you can upload you page into your home directory, you can then move it using a command on the server, something like this:
```
sudo mv /var/www/html/index.html /var/www
```

This will move the default webpage out of the host directory.

```
sudo mv /home/user/index.html /var/www/html
```

This will move the page you uploaded into your home directory to the webserver's host directory. Change user in the command above to the username you are using.

im getting:

mv: cannot stat ‘/home/jordan/Documents/index.html’: No such file or directory

But it is defo there :/

---

### Post by Jordan_Hickin on 2014-04-28
> **Jordan_Hickin said:**
> im getting:

mv: cannot stat &#8216;/home/jordan/Documents/index.html&#8217;: No such file or directory

But it is defo there :/

Sorted it :D Thankyou.. Now i have done that.. how do i get access to the second users site? he is under var/www/webuser1.... 

Thankyou

And by get access i mean show it on my browser.. I am unsure what to enter after 192.168.0.7...

```

adminjah@webserver1:~$ ls /var/www
html  index.html  webuser1
adminjah@webserver1:~$ ls /var/www/webuser1
index.html
adminjah@webserver1:~$ 


```

It is defo saved on the server...

---


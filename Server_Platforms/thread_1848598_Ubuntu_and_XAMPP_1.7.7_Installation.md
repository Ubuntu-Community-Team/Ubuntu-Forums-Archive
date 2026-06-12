---
title: "Ubuntu and XAMPP 1.7.7 Installation"
date: 2011-09-22
forum: Server Platforms
---

### Post by DMackMarshall on 2011-09-22
Hello everyone, my name is Doug and I am new to Ubuntu and Linux.
I apologize if this has been answered but I must be honest, I got tired of looking after 6 or 7 pages.
I have managed to get "Server 11.04" installed and updated, I figured the next set was to get some of my stuff installed.  i downloaded the open source code but I can't figure out how to get it installed.  Their readme file indicated the following:
su
enter password
[FONT=Verdana]tar xvfz xampp-linux-1.7.7.tar.gz -C /opt[/FONT]
When I do the above I get an error message indicating neither the file or folder could be found.

Is there a source for learning this code or instruction set? The file is in my downloads folder, how do I tell it where to find the file or move the fine where it is looking?

Thanks in advance for your time and consideration.

---

### Post by mgif0000 on 2011-09-22
Hi
My english is bad, but i will try to explain something, please follow these steps:
1 download xampp from [here]("http://www.apachefriends.org/en/xampp-linux.html") even there are steps to install
2 Open the terminal and try this
"sudo su" enter
type your password
"tar xvfz /file path/[FONT=Verdana]xampp-linux-1.7.7.tar.gz -C /opt" enter
3 please verify the follow path where it was installed /opt/lampp
4 this commands starts xampp "/opt/lampp/lampp start", if you have an error with a library try this "apt-get install ia32-libs" enter
5 after the install the library try to start xampp [/FONT][FONT=Verdana]"/opt/lampp/lampp start"
6 if it is good you can verify in you  explorer just type "localhost" in your address bar, you have to see "XAMPP", blablaa
7 for permits "chmod -R 777 /opt/lamppl/htdocs"
8 try this for security /opt/lampp/lampp security" you can type your passwords.

Once again, sorry by my english i hope this can help you..

Regards
Noe Maldonado
[/FONT][FONT=Verdana]

[/FONT]

---

### Post by mörgæs on 2011-09-23
If you want a LAMP stack, this is how to do:


```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

Don't download stuff from the web and install. It is a bad habit from Windows.

---

### Post by DMackMarshall on 2011-09-23
I attempted to use the following:
sudo apt-get install tasksel sudo tasksel install lamp-serverand I get a status bar indicting "Configuring" however, the progress bar indicates 0%.
When I go to the browser and enter "http:localhost" it indicates it is working, however, it also state "No content has been installed".

I've attempted the download of "xampp-linux-1.7.7.tar.gz but I cannot figure out the "File Path".  As I indicated I am a virgin to Linux.
I figured out the path and got it installed.  However at the end of the install the system indicated the following:
Starting XAMPP 1.7.7...
XAMPP: Another web server daemon is already running.
XAMPP: Another MYSQL daemon is already running.
XAMPP: Starting ProFPTD
XAMPP for Linux started.

When I open the browser "FireFox" and go to localhost, I get the following:
It Works!
This is the default browser for this server.
The web server software is running but no content has been added.
?? Why am I not getting the Apache splash screen?

Thanks for your patience and consideration):P

---

### Post by mörgæs on 2011-09-23
> **DMackMarshall said:**
> 
When I open the browser "FireFox" and go to localhost, I get the following:
It Works!
This is the default browser for this server.
The web server software is running but no content has been added.

Why am I not getting the Apache splash screen?


You *are* getting the Apache splash screen.

---

### Post by Hack.The.Pow. on 2011-09-23
Yes that is the apache splash screen haha.

Now you should begin adding your web pages to /var/www and you should be well on your way!

---


---
title: "Lamp setup, apache 2 drama."
date: 2009-04-19
forum: Server Platforms
---

### Post by Schtoo on 2009-04-19
Hi all, my first post here so be gentle please. Also a Ubuntu (8.04LTS) virgin so please excuse my clumsiness.

I am trying to get the Lamp server stuff set up, and I am having serious troubles getting it all to work properly. 

Right now I am going through the steps mentioned at[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop") and have hit a snag when configuring the apache2 to work properly. 

When I try to restart apache2, I am getting "Syntax error on line 3 of /etc/apache2/sites-enabled/apache2.conf:" which even I know isn't a good sign, but it's better than it was. FWIW, I am using a simple 'example.com' to work with, and I must be missing something obvious.

That's about all I got and the whole thing is driving me nuts. I got XAMPP working on the other XP box within an hour, and trying to get the same kinda thing working on this new laptop (bought especially for this purpose) has now taken over 4 days and I can't make it work. Yes, I have searched, my firefox history is filled with searches about this and still no go.

Thanks, I hope...

---

### Post by jowilkin on 2009-04-19
Apache2 should work "out of the box" on ubuntu.  I believe apt-get should install apache2.conf to /etc/apache2/apache2.conf, not the location indicated by your error message.

What steps did you take exactly?  It seems something strange has happened to your installation.

If you have already spent 4 days working on it, I would recommend reinstalling ubuntu and using apt-get or aptitude to install a default apache2.  I've done this several times with no issues at all.

I would try to get apache working before anything else.  Just install ubuntu and then in a terminal type "sudo aptitude install apache2".  This should give you a fully working install of apache.  The root of the web server will be in /var/www.  If you have a web page such as "index.html" that you want displayed, simply put it in /var/www.

Another option (possibly much easier) is to install ubuntu server edition.  One of the options during install time is "LAMP server" which seems to be exactly what you want.  Only issue is that Ubuntu server does not install a graphical interface by defauly (command line only).  You can add the GUI by typing "sudo aptitude install ubuntu-desktop" at the command line.

---

### Post by Schtoo on 2009-04-19
I used the Synaptic manager to install all the parts, and have since purged and reinstalled apache2 to try and return it to some kind of normality and it hasn't worked yet. I did get 'It Works!' when going to localhost, and I was trying to get 'example' to use as a base instead of localhost as well as put some files into a place where I could work on them.

In that tutorial I linked to, I was trying to add a virtual host to the server and tried it both ways. No luck at all and this is where things started to fall apart.

I am reluctant to re-install ubuntu because if I have to do that, I won't bother with it any more for a while. I have installed ubuntu 3 times in those 4 days trying to just get this simple little thing working, nothing else. 

(Yes, I am being very restrained here in how I feel about this...)

Thanks, and I'll try and dig out all the apache stuff and reinstall it and see what happens.

---

### Post by dmm1983 on 2009-04-19
When i do a clean install of ubuntu i use the guides on [http://howtoforge.com]("http://howtoforge.com") search for your distro version.

next install dont choice the LAMP option just the openssh server or whatever you are using. but the howtoforge site is really good for what your trying to do i use it a lot.

---

### Post by Schtoo on 2009-04-19
Hi again.

I just reinstalled Ubuntu and all should be clean, lets see if I can't make it work this time.

Now at 5 days to get this &%%$#$% thing going...

---

### Post by Iowan on 2009-04-19
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is another help page that may be useful...

---

### Post by jowilkin on 2009-04-19
Don't get too frustrated, it can be done :P

And Don't spend another 4 days trying to fix it yourself.  

Let us know what errors you get, what you did, and what exactly you were trying accomplish, and we can probably get you running in no time.

---

### Post by daboroe on 2009-04-19
Like the users have said apache and all of that should work out of box. The installation messed up or you edited your .conf file and have a misspelling to cause that error. 

Do you have a copy of your apache.conf file that you can post or what not? That might help us find where the issue is for you.

Thanks

M. Brown

---

### Post by Schtoo on 2009-04-21
Hi all, I did get it all working in a way, but still not what I know I need as opposed to think I need.

I can fire up a browser and work on the things I need to that are on this machine, but it all comes to a screaming halt once I pull the network (attached to an ADSL modem) plug.

I'd like to be able to keep on working 'unplugged' as I don't have wireless (yet) and I don't always end up having the chance to do something where I can also connect to the internet/network.

Still trying to search for what I want to do and how I want to do it, but I am having some trouble coming up with search terms...

Anyway, off to google again. 

Thanks, 

Stu.

---

### Post by jowilkin on 2009-04-21
What program are you using to connect to the server?  That's getting out of my area of expertise, but I'm sure someone on here can give you a hand.

---

### Post by Schtoo on 2009-04-22
Umm, I can't tell you what it's using because I am not 100% sure what it is. Not computer illiterate, just the simple fact that I plug it in, if it works I don't prod and poke.

But I just did prod and poke with the system>network settings and decided to try adding the local host ip addy and guess what, it now works unplugged.


Which is all I wanted in the first place. :)

Colour me happy right now. I was worried Ubuntu was going to be an unending headache for me, and it just keeps impressing me instead.

(Yes, I think I am hooked.)

Thanks folks.

Stu.

(Edit. Now it's not working again. Maybe what I was looking at was stuck in the cache or something. Dag nab it...)

(Edit the edit. Now it is working again. I had to tell Firefox to connect without a real connection. Finally worked out the correct terms for a search of what I wanted to know which helped too.)

---


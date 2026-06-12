---
title: "Home webserver"
date: 2006-02-10
forum: Server Platforms
---

### Post by Pugi! on 2006-02-10
I have an old pentium 450MHz, 384 MB RAM and 40 GB hard disc and I would like to use it as a webserver for home use. I study webprogramming and -design.
I would like to have a webserver (apache 2.x), mysql (4,x or 5,x), PHP5, probably also ftp-server, maybe mail-server to experiment. I would like to work on this server remotely (laptop with Ubuntu Breezy or recent desktop with WinXP and FC4), so I guess I need ssh and/or telnet and samba and firewall.
I would like to be able to just start this webserver by pressing the power on button and shut it down remotely (shutdown -h now) if that's possible. I don't have spare screen, keyboard or mouse, nor do I have the place for it.
I don't need DHCP (I guess) because I have wireless network at home with wireless adsl modem/router/dhcp server.
I was thinking of installing fedora core 4, probably command line only (and I am still bit of newbie), but now I saw there is an Ubuntu server and I know that this computer had not problems with running Ubuntu hoary. Is Ubuntu server something for me ? Where do u download it or is it on the Breezy cdrom ? There is quite a lot of documentation on FC4 as server, is that also the case for Ubuntu server ? What do I need ? Where do I find it ? Where do I start ?

thanx,

Pugi!

---

### Post by skirkpatrick on 2006-02-10
I believe when you use the Breezy install, you type **server** instead of just hitting enter at the very first prompt.

I'm getting ready to change my home server from RedHat 8 to Breezy as soon as I take the time to move the stuff I want to save over to a bigger harddrive.  This machine doesn't do email but it has Apache, MySQL, PHP, and Samba but that's just to let the Windows machines in the house have access to the files.  Because I have Samba, I don't use FTP to access files on it.  This machine has no keyboard, mouse, or monitor and has been running this way for about 4 or 5 years.  I telnet into it for simple things but also use VNC to access it graphically.  I never shut it down and in fact it's on a UPS but there's no reason you can't shut it down remotely.

---

### Post by nagilum on 2006-02-12
Since you want an easy to set up webserver with MySQL and PHP support you might also be interested in [XAMPP](http://www.apachefriends.org/en/xampp.html). Might be easier to install than all the single packages from Ubuntu.

---

### Post by Peter76 on 2006-02-12
The server option on the standard breezy cd gives you a really basic clean system where you add eveything by hand you need; very good if you know what you're looking for. I haven't looked at the server cd myself; but I understand it comes with all the packages you need.
DON'T use telnet; very insecure.... Use ssh; it does exactly what you want in a very secure way ( I can shut down my mates computer which is 100k away:-) Use putty as a ssh client fo windows... Good luck

---

### Post by squirrelyosis on 2006-02-12
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

Here's the guide for setting up most of what you need on Ubuntu.  Its pretty easy, I've had this setup for a while and it works great.  I do a lot of messing around with databases and different PHP scripts.  You can setup Proftpd so that you can FTP your files right into your /var/www directory for your webpages.

---


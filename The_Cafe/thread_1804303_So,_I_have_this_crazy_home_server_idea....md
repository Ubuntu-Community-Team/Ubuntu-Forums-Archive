---
title: "So, I have this crazy home server idea..."
date: 2011-07-14
forum: The Cafe
---

### Post by ninjaaron on 2011-07-14
... is it possible, and how would I start?


First of all, I want to have network attached storage that backs itself up regularly on a separate drive. I think this is no big deal, but I still don't know how to do it.

Next, I want to set up a web server (need Apache or something, right?) that will give me access to my network storage via Internet; my own private cloud, if you will.  I realise this may not be the most secure setup in the world, but as a private individual, I don't have much to hide in the first place.  I guess this is also possible, but again, I don't really know how to do it.

Finally, I want my desktop computer to be the hub for an entertainment center that connects to the TV and several stereos around the house.  This isn't difficult for me.  It's a matter of electronics and wiring and all that, and I can manage that kind of thing. Just need to break out the soldering iron.  Now, the tricky part is, I want to be able to control that sound system with any computer in the house over the network, as well as with smart phones and any other kinds of device.  I know AnyRemote is out there, but I want a more comprehensive solution... perhaps some sort of "website" set up on the server machine that can display information from the media player, as well as send commands back to it.

So, I don't need a full explanation of how to do all of this, but I am looking for a starting point about how to achieve each item.

P.S.  I got a new tattoo today.

---

### Post by CharlesA on 2011-07-14
The server part is fairly easy to set up - build the box, and use rsync to backup the files.

For the web-based file access portion, check out [AjaXploer]("http://www.ajaxplorer.info/wordpress/").

---

### Post by Dustin2128 on 2011-07-14
> **ninjaaron said:**
> ... is it possible, and how would I start?


First of all, I want to have network attached storage that backs itself up regularly on a separate drive. I think this is no big deal, but I still don't know how to do it.

Next, I want to set up a web server (need Apache or something, right?) that will give me access to my network storage via Internet; my own private cloud, if you will.  I realise this may not be the most secure setup in the world, but as a private individual, I don't have much to hide in the first place.  I guess this is also possible, but again, I don't really know how to do it.

Finally, I want my desktop computer to be the hub for an entertainment center that connects to the TV and several stereos around the house.  This isn't difficult for me.  It's a matter of electronics and wiring and all that, and I can manage that kind of thing. Just need to break out the soldering iron.  Now, the tricky part is, I want to be able to control that sound system with any computer in the house over the network, as well as with smart phones and any other kinds of device.  I know AnyRemote is out there, but I want a more comprehensive solution... perhaps some sort of "website" set up on the server machine that can display information from the media player, as well as send commands back to it.

So, I don't need a full explanation of how to do all of this, but I am looking for a starting point about how to achieve each item.

P.S.  I got a new tattoo today.
Easy, actually. Look up instructions on how to do a RAID 1 for backups- that's my recommendation. 

Get ubuntu server edition, of course. I run a web server off of it and I find it an excellent server operating system. Just check the boxes "LAMP Server", and "Open SSH Server" during install, then afterwards, open up your favorite text editor, browse over to /var/www/index.html and write a simple portal page- hyperlinks to all the subdirectories would do. I could even write a template if you like, but html is pretty easy. After that's done, run the command ```
ifconfig | grep inet
``` and that will give you the machine's ip address. If the address starts with 192.168, it's local and will be inaccessible outside your network. In that case, go to your router's web interface and setup a port forwarding system (there are tutorials for this all over the internet, not terribly hard) or DMZ zone it- isolate from the rest of your network and have it connected straight to the internet (this is what I do since my server box does a lot more than web hosting, ssh and SFTP). 

Anyway, once you run ifconfig and get an address not on the local block, you can probably access it anywhere by just typing in the ip address. Not the most elegant solution, but there's a simpler one that's also fairly secure. Just go to /etc/hosts on whatever device you want to use the cloud on, and enter the ip address of the server along with the domain name you'd like to use it with. Alternately, you could just go to co.cc and get a free domain, accessible on any device. As for uploads, grab [FireFTP]("https://addons.mozilla.org/en-US/firefox/addon/fireftp/") and you're set.

That's how I do network storage, but I hear samba is a much more elegant solution, so you might want to check that out.

As for the final one, it might be a bit trickier- I don't know how to do it. What I'd do is get a bunch of cheap arm boards for front ends wherever you want them, have them access the network drive and stream the content you want- should be fairly easy to control with a remote or wireless keyboard.

---

### Post by ssam on 2011-07-14
these projects are fun :-)

mpd is good music player that can be controlled remotely by anynumber of clients.

if you want something that is always on i recomend finding something lower power, mini-itx boards are usually good. or you could look at beagleboard/pandaboard.

---

### Post by Bandit on 2011-07-14
> **ninjaaron said:**
> ... is it possible, and how would I start?


First of all, I want to have network attached storage that backs itself up regularly on a separate drive. I think this is no big deal, but I still don't know how to do it.Easy use of BASH scripting and Cron. Google these as its super easy and you can even have your PC use MD5SUM if you have your backup sent to another location or on a separate drive medium as well as send you email with the confirmation.

> 
Next, I want to set up a web server (need Apache or something, right?) that will give me access to my network storage via Internet; my own private cloud, if you will.  I realise this may not be the most secure setup in the world, but as a private individual, I don't have much to hide in the first place.  I guess this is also possible, but again, I don't really know how to do it. FTP over SSH.

> 
Finally, I want my desktop computer to be the hub for an entertainment center that connects to the TV and several stereos around the house.  This isn't difficult for me.  It's a matter of electronics and wiring and all that, and I can manage that kind of thing. Just need to break out the soldering iron.  Now, the tricky part is, I want to be able to control that sound system with any computer in the house over the network, as well as with smart phones and any other kinds of device.  I know AnyRemote is out there, but I want a more comprehensive solution... perhaps some sort of "website" set up on the server machine that can display information from the media player, as well as send commands back to it.
Simple network and look into MythTV

> 
So, I don't need a full explanation of how to do all of this, but I am looking for a starting point about how to achieve each item.

I hope the links provided will help get you started. There are many minor details you will have to work out on your own that we would know or have the time to work each issue. Plus telling someone what to do doesnt teach them and can take longer then just pointing you in the right direction and you learning on your own. Best of luck and hope to hear how it turns out. If you have a few technical issues tho that arise you cant figure out, please do ask here then we will be happy to help. :)

---

### Post by Bandit on 2011-07-14
> **Dustin2128 said:**
> Easy, actually. Look up instructions on how to do a RAID 1 for backups- that's my recommendation. 

Get ubuntu server edition, of course. I run a web server off of it and I find it an excellent server operating system. Just check the boxes "LAMP Server", and "Open SSH Server" during install, then afterwards, open up your favorite text editor, browse over to /var/www/index.html and write a simple portal page- hyperlinks to all the subdirectories would do. I could even write a template if you like, but html is pretty easy. After that's done, run the command ```
ifconfig | grep inet
``` and that will give you the machine's ip address. If the address starts with 192.168, it's local and will be inaccessible outside your network. In that case, go to your router's web interface and setup a port forwarding system (there are tutorials for this all over the internet, not terribly hard) or DMZ zone it- isolate from the rest of your network and have it connected straight to the internet (this is what I do since my server box does a lot more than web hosting, ssh and SFTP). 

Anyway, once you run ifconfig and get an address not on the local block, you can probably access it anywhere by just typing in the ip address. Not the most elegant solution, but there's a simpler one that's also fairly secure. Just go to /etc/hosts on whatever device you want to use the cloud on, and enter the ip address of the server along with the domain name you'd like to use it with. Alternately, you could just go to co.cc and get a free domain, accessible on any device. As for uploads, grab [FireFTP]("https://addons.mozilla.org/en-US/firefox/addon/fireftp/") and you're set.

That's how I do network storage, but I hear samba is a much more elegant solution, so you might want to check that out.

As for the final one, it might be a bit trickier- I don't know how to do it. What I'd do is get a bunch of cheap arm boards for front ends wherever you want them, have them access the network drive and stream the content you want- should be fairly easy to control with a remote or wireless keyboard.

Good info as well. Ubuntu server is highly recommended and makes setting up LAMP, Java, FTP and SSH services a snap. All at once. 

Dustin mentioned RAID. RAID 1 is simplest as it mirrors 2 disc and can be the cheapest. Draw backs is lack of speed and if you have 2x 1TB drives then your only going to have 1TB of drive space to use. RAID 5 is much like RAID1, but requires a minimum of 3 disc and offers better speed and more space. RAID10 is quickly becoming the most popular as it offers more speed and better redundancy.
I use RAID0, which technically isnt a real RAID as there is no redundancy, but it offers huge speed amounts. Essentially every disc you add increases your speed. If you have a HDD that transfers at 100MB sec, every time you add another one of those you add another 100MB/sec faster speed. I run 4x WD Blue Caviar drives in my system and I top out over 380MB/s reads and 370 writes, average is about 280MB/s using Ext4 FS. With 1.2TBs of space this was a great $160 dollar investment. But the downside is that if ANY of the drives go out.. BYE BYE DATA.. Back ups are goooood...   [ Read this link to determine what is best for you..]("http://en.wikipedia.org/wiki/RAID")

---

### Post by ninjaaron on 2011-07-15
Thanks for all the great ideas guys!  Everyone else, keep 'em coming.

---

### Post by Dustin2128 on 2011-07-15
Almost forgot- the data storage directories need to be under /var/www, and it'd be useful to reassign permissions to your normal user.

---

### Post by aquarius18 on 2011-07-15
> **ninjaaron said:**
> ... is it possible, and how would I start?


First of all, I want to have network attached storage that backs itself up regularly on a separate drive. I think this is no big deal, but I still don't know how to do it.

Next, I want to set up a web server (need Apache or something, right?) that will give me access to my network storage via Internet; my own private cloud, if you will.  I realise this may not be the most secure setup in the world, but as a private individual, I don't have much to hide in the first place.  I guess this is also possible, but again, I don't really know how to do it.

Finally, I want my desktop computer to be the hub for an entertainment center that connects to the TV and several stereos around the house.  This isn't difficult for me.  It's a matter of electronics and wiring and all that, and I can manage that kind of thing. Just need to break out the soldering iron.  Now, the tricky part is, I want to be able to control that sound system with any computer in the house over the network, as well as with smart phones and any other kinds of device.  I know AnyRemote is out there, but I want a more comprehensive solution... perhaps some sort of "website" set up on the server machine that can display information from the media player, as well as send commands back to it.

So, I don't need a full explanation of how to do all of this, but I am looking for a starting point about how to achieve each item.

P.S.  I got a new tattoo today.

Take a look at **[Zentyal]("http://www.zentyal.org/")** - it's built on the latest Ubuntu Server LTS (10.04) release.

---

### Post by BrokenKingpin on 2011-07-15
You could look at OwnCloud for the remote file access website. It is in the ubuntu repos and really easy to configure and setup.

---

### Post by LowSky on 2011-07-15
Just check with your ISP, most do not allow customers to run internet accessible servers, and If they do some only allow Port 80 access.

---

### Post by Porcini M. on 2011-07-26
> **ninjaaron said:**
> .Now, the tricky part is, I want to be able to control that sound system with any computer in the house over the network, as well as with smart phones and any other kinds of device.  I know AnyRemote is out there, but I want a more comprehensive solution... perhaps some sort of "website" set up on the server machine that can display information from the media player, as well as send commands back to it.

Look into the Subsonic music server - [http://www.subsonic.org/pages/index.jsp](http://www.subsonic.org/pages/index.jsp).

You can set it in "jukebox mode", which will send the music to a stereo attached to the server. There are mobile apps for connecting to it.

---


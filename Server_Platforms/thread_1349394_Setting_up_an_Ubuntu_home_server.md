---
title: "Setting up an Ubuntu home server"
date: 2009-12-08
forum: Server Platforms
---

### Post by humphreybc on 2009-12-08
Hi there,

So I was thinking for next year I might try setting up a server in our flat, and connecting it to our local wireless, plus - if possible, the internet so I can access files remotely.

Let me tell you a bit of background, I currently have one 500GB External HDD with my stuff on it, and another 250GB as a backup with important stuff on it. I have my laptop, but no other computer hardware - I'd have to buy the hardware. My new flat has a wireless router, not sure what kind. I've had no experience with servers, and not a lot of networking experience before - although I am a software engineering student.

So - how hard would it be to set up such a system? What sort of hardware should I look at, without breaking the bank? My flatmates (and most of my friends) use Windows/Mac - can I set it up so everyone, regardless of OS can access files locally and on the internet? (Perhaps the latter with password etc)

So requirements would be:

Works with Mac, Linux and Windows
Doesn't require any software to be installed client side
Provides reasonably fast transfer rates
Has a feature to upload new files to the server and organize directory structure, without having to physically visit the server
.. and lastly, although not as important - be available to be accessed on the internet, anywhere in the world, from any computer (with authentication obviously)


Thankyou so much for your replies in advance!

Benjamin

---

### Post by munky99999 on 2009-12-08
[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

[https://help.ubuntu.com/9.10/serverguide/C/file-servers.html](https://help.ubuntu.com/9.10/serverguide/C/file-servers.html)

FTP will be supported by any OS.

Samba or NFS should work fine in all the os also; with a little work.

---

### Post by Meatshield on 2009-12-08
FTP or SFTP would work for what you need file wise, and then a password protected website that lists all the files(.htpasswd and .htaccess method). I can give you some links on how to set all that up if you wanted to go that route.

SFTP runs as SSH for files and uses the local Linux account credentials. I find it a lot easier to manage personally.

That plus Samba would make it no-install since Samba mimics a Windows share, which Mac should be able to see as well (I don't have a Mac so I'm speculating here).

As for the difficulty of it all, I've done it a dozen times on various machines and there are a lot of tutorials on this forums and elsewhere that can walk you through exactly how to do it all. If you have an old computer lying around, use that. Else, you could use anything from a netbook to a full desktop and they will all work just fine. But since you mentioned wireless vs. wired a netbook would probably be the cheapest solution if you have to buy a new machine.

---

### Post by holastickboy on 2009-12-08
what sort of computer do you have for the server?

---

### Post by humphreybc on 2009-12-09
Hey guys, cheers for the replies.

@Meatshield: Okay some links would be good. So using samba, would users be able to drag and drop files if they're connected locally - what about over the internet? Or would I just have an entirely browser based system where users can download files, and then upload stuff too?

@holastickboy: I don't have a computer for a server at the moment. I'm looking at buying just an old computer off the internet and buying a new hard drive to stick in it, probably a 1TB SATA. What would be the minimum processor requirements for a file server?

---

### Post by Andrew Buchinger on 2009-12-09
While you can get away with VERY light processor power for a file server, (I mean I know people who run them off of old windows 95 boxes) I would say anything AMD 1900 or pentium 4 era and later would perform VERY well as just a file server. If you were willing to use something else as a base OS, like FREENAS, then you could go even older on that one.

 A friend of mine picked up a free computer off of Craigslist that he runs his freenas off of and I paid $20 for mine. His is a Pentium 3 and min is a pentium 4 with 512 MB of ram. The only problem you will find with OLD computers is finding IDE hard drives.


It's fairly simple to setup. You can allow anyone or just people who you have created a username and password for to access it, and you will be able to connect those USB externals to it and share them out also.I just used my main PC's monitor and keyboard for setup, but you may have to borrow from a friend since you have a laptop.


 Once it is setup it is 100% remote managed via your web browser of choice, and if you install a samba share people from every OS will be able to recognize the share and partake.

---

### Post by Andrew Buchinger on 2009-12-09
Oh yeah the other REALLY great thing about freenas is if you torrent at all, it has a torrent client installed on the OS, so you can have it start a torrent and download it to your file share, which means you can turn your computer off at night and continue getting your torrent. (I suggest a P4 or higher for this feature and 256mb+ of ram)

---

### Post by humphreybc on 2009-12-09
Thanks for the replies. So it's quite easy to get running through a web browser and have remote upload/download ability, and also compatibility with Mac and Windows?

What about the commands, because Server Edition will be entirely command line based - did you use a guide to set it up?

---

### Post by Meatshield on 2009-12-09
"@Meatshield: Okay some links would be good. So using samba, would users be able to drag and drop files if they're connected locally - what about over the internet? Or would I just have an entirely browser based system where users can download files, and then upload stuff too?"

I'm actually messing around with a browser-based VPN server right no so I'll get back to you on how that worked. I haven't gotten OpenVPN quite where I want it yet, but a VPN could make it so that when you leave your LAN, you can still see the computers and shares as if they were locally connected to you.

Samba will handle the local folders just fine so that it'll look like a Windows share to Mac and Linux clients.

I'll post some links in a bit. I have to run to class first :p

---

### Post by humphreybc on 2009-12-09
Cool, thanks. No rush - I won't be starting this project till January. Thought I'd find out a bit about it first to see if it was indeed feasible! (Monetary wise and skill wise :P )

---

### Post by noway2 on 2009-12-10
One aspect to this that you queried about, but wasn't mentioned is that you will need to configure your router.  You will need to set up your router with either port forwarding to direct incoming traffic to your server (via IP address) or place your server in a DMZ.  Normally, your router, wireless or otherwise, will block incoming traffic for security purposes. Typically this is fairly easy to do and can be figured out by browsing the router's internal configuration page.

The ports you will need to open / forward will depend on what kind of services you want to provide.  For example, if you want to allow web browser traffic you will need to open port 80 and if you want SSH you may want port 22.

Before you do this, I HIGHLY recommend reading through the posts, especially the sticky ones, in the security forum for hints and tips on doing this safely.

---

### Post by Cheesemill on 2009-12-10
For web access to my fileserver I use [AjaXplorer]("http://www.ajaxplorer.info/wordpress/").

As well as file upload/download it has loads of other features such as streaming mp3's, thumbnailing of image files, editing txt files and more.

Check out the [demo]("http://www.ajaxplorer.info/wordpress/demo/").

---

### Post by humphreybc on 2009-12-10
@noway2 - yeah I know a bit about port forwarding. I haven't actually asked the other flatmates if they'd be okay with a server setup running 24/7 yet haha.

@Cheesemill - That looks perfect! Is it easy to set up on Ubuntu? Do you use the command line based Server Edition, or regular Ubuntu?

---

### Post by Cheesemill on 2009-12-11
> **humphreybc said:**
> @Cheesemill - That looks perfect! Is it easy to set up on Ubuntu? Do you use the command line based Server Edition, or regular Ubuntu?

It's very easy to set up, it only took me a few seconds. I have it running on a command line server (actually a VM running JeOS) but it will work just as well on the normal Server or Desktop versions.

---

### Post by Cheesemill on 2009-12-11
To get a head start before you get your hardware, and also because it's your first time setting up a server (and you will make mistakes) I'd recommend practising first with a virtual machine.

Just install VirtualBox on your computer then you can have a play about with a server install, just make sure you set up the machine with bridged networking so it gets its own IP address.

I think the best advice I can give you is to document everything you do, it's all to easy to forget what configuration changes you've made. This way when you get your hardware you'll already know what your doing.

---

### Post by humphreybc on 2009-12-12
> **Cheesemill said:**
> To get a head start before you get your hardware, and also because it's your first time setting up a server (and you will make mistakes) I'd recommend practising first with a virtual machine.

Just install VirtualBox on your computer then you can have a play about with a server install, just make sure you set up the machine with bridged networking so it gets its own IP address.

I think the best advice I can give you is to document everything you do, it's all to easy to forget what configuration changes you've made. This way when you get your hardware you'll already know what your doing.

That's actually a really good idea. I'll download the server edition tomorrow and have a play in VBox. Cheers!

---

### Post by humphreybc on 2009-12-12
One other question, 8.04 or 9.10?

Obviously in April I'll upgrade to 10.04 - but until then, which one?

---

### Post by John Rivera on 2009-12-13
> **humphreybc said:**
> One other question, 8.04 or 9.10?

Obviously in April I'll upgrade to 10.04 - but until then, which one?

I would go with 9.10

Anyhow. I have been working for while with same subject (ubuntu linux server in home)
And since it looks like I am not only one up for idea, maybe it should be shaped into coordinated project ?

---

### Post by humphreybc on 2009-12-13
What do you mean, work together?

---

### Post by humphreybc on 2009-12-19
What do you think of this?

[http://www.trademe.co.nz/Computers/Desktops/No-monitor/auction-260894564.htm](http://www.trademe.co.nz/Computers/Desktops/No-monitor/auction-260894564.htm)

---

### Post by humphreybc on 2009-12-20
Right I have downloaded and installed the 32 bit 9.10 server edition in a virtualbox... I wasn't *entirely* sure what extra options to choose, so I just made some educated guesses.

Now - how do I:

a) Get the Ajaxplorer.zip file from the host (my computer into my virtualbox guest server

b) Install it on the server

c) Get it up and running so I can access it from my browser on the host computer, and across our network? Networking is already working with NAT on the guest.

---

### Post by CharlesA on 2009-12-20
> **humphreybc said:**
> What do you think of this?

[http://www.trademe.co.nz/Computers/Desktops/No-monitor/auction-260894564.htm](http://www.trademe.co.nz/Computers/Desktops/No-monitor/auction-260894564.htm)

Not bad for 30 bucks. I don't do auctions for electronics tho.

> **humphreybc said:**
> Right I have downloaded and installed the 32 bit 9.10 server edition in a virtualbox... I wasn't *entirely* sure what extra options to choose, so I just made some educated guesses.

Now - how do I:

a) Get the Ajaxplorer.zip file from the host (my computer into my virtualbox guest server

b) Install it on the server

c) Get it up and running so I can access it from my browser on the host computer, and across our network? Networking is already working with NAT on the guest.

What OS is the host running? I believe you would need to run the NIC as "bridged" so that it'll be see as on your network. For transfering files betweet the host and guest, I usually create an iso with the files and mount it in the guest OS and go from there. I haven't found a better way to do it with a clean install. :(

EDIT: The "better way" that I use only works if you have ssh installed - as it uses sftp.

---

### Post by humphreybc on 2009-12-20
Okay I'm using Ubuntu 9.10 Karmic as the host.

Of course! Forgot about making an ISO, so I've done that, then I have to mount it, copy the zip somewhere, then unzip it all from the command line... and then what? Could you run through that briefly?

---

### Post by CharlesA on 2009-12-20
> **humphreybc said:**
> Okay I'm using Ubuntu 9.10 Karmic as the host.

Of course! Forgot about making an ISO, so I've done that, then I have to mount it, copy the zip somewhere, then unzip it all from the command line... and then what? Could you run through that briefly?

I'm not sure how to install it tbh, since I've never used it, but a quick google turned this up: [http://www.linux.com/archive/feature/128854](http://www.linux.com/archive/feature/128854)

---

### Post by Cheesemill on 2009-12-20
If the server VM has internet access just download it straight onto the server, this is assuming you have already got LAMP installed. Also how are you accessing your server? If you haven't yet installed openssh-server then I suggest you do that, you can then just copy and paste the following instead of having to type it all out.

```
cd /var/www
sudo wget http://downloads.sourceforge.net/project/ajaxplorer/ajaxplorer/2.5.4.def/ajaxplorer-core-2.5.4.zip
sudo unzip ajaxplorer-core-2.5.4.zip
sudo chown -R www-data:www-data *
```Then just point a browser to "http://serverIP/AjaXplorer-2.5.4/". Done.
You can see what I mean about it taking seconds to install in my earlier post :)

Just post back if you have any problems or want me to explain what any of these commands do.

---

### Post by humphreybc on 2009-12-20
Okay so I've managed to download ajaxplorer, unzipped it and changed the permissions. I'm setting the network to bridged now which seems to work.

Hey I just got it working! Wicked!

So on my test machine I have it set with a 10.7GB hard drive, partitioned in three ways...

5GB for OS - mounted at / with no label
5GB for data - mounted at /home with the label "data"
0.7GB for SWAP

In my actual server, I'll probably leave it at 5GB for my OS, and have the data partition formatted to something like 480GB or whatever is left on my hard drive. I'll give SWAP 1GB.

For the mount points, would /home be the best place to mount.. or not so much? 

And, how do I add the "data" partition to AjaXplorer? Can you set different permissions for different users?

(As an example, I have a heap of music, movies and TV Shows that I want to share with everyone in my flat, so when I set up their accounts they will have read/write access to these places. But I will have my confidential documents backed up on my server too in a different folder, which I only want ME to be able to read/write - can AjaXplorer do that?)

---

### Post by humphreybc on 2009-12-20
Okay I've managed to get some stuff set up... but when I go to upload a movie I get "The file is too big!"

Don't tell me it can't handle large files.... :S

EDIT: Oh I see, it says there is a 2MB upload limit in place...

---

### Post by Cheesemill on 2009-12-20
By default PHP has a 2MB file upload limit, you can change this by editing the /etc/php5/apache2/php.ini file and changing the following line:
```
upload_max_filesize = 2M
```
Then restart apache and you should be good to go.

---

### Post by Cheesemill on 2009-12-20
> **humphreybc said:**
> 
And, how do I add the "data" partition to AjaXplorer? Can you set different permissions for different users?

(As an example, I have a heap of music, movies and TV Shows that I want to share with everyone in my flat, so when I set up their accounts they will have read/write access to these places. But I will have my confidential documents backed up on my server too in a different folder, which I only want ME to be able to read/write - can AjaXplorer do that?)

You can set up users and different repositories (filestores, not Ubuntu repositories) in AjaXplorer from the interface:
[http://www.ajaxplorer.info/wordpress/documentation/chapter-settings/](http://www.ajaxplorer.info/wordpress/documentation/chapter-settings/)

---

### Post by humphreybc on 2009-12-20
Okay sweet. I'm having a bit of trouble adding files from my host - small files work fine, but when I choose a larger file in the upload browse box, it seems to crash AjaXplorer.

I presume it's something to do with Chrome/Firefox and 64 bit flash... going to try on Windows in a sec.

I have many questions: :P

1) As for partitioning, would you bother separating the OS and data? Because then I'd have to set it up to mount automatically each time it boots... and encrypted home partition for servers or no?

2) What stuff should I check when I install Server Edition on the real server... obviously LAMP, open-ssh, PHP, mySQL etc.. what else?

3) How does openssh work (so I can access the server terminal from my laptop up in my room, when it's downstairs) right?

4) Will it use a static IP by default, or do I have to set this up? Can I have the address as something easier to remember (ie, replacing the IP with "server" or something so the URL would be [http://server/AjaXplorer-2.5.4](http://server/AjaXplorer-2.5.4) )

5) Can I have automatic login on the server, or is this a bad idea? Ajax won't work unless I'm logged in on the server, right?

6) Will running the server 24/7 burn out the hard drives? Roughly how much power will it use?

Thankyou!

---

### Post by Cheesemill on 2009-12-20
> **humphreybc said:**
> 
1) As for partitioning, would you bother separating the OS and data? Because then I'd have to set it up to mount automatically each time it boots... and encrypted home partition for servers or no?
I'd definately separate the partitions. I do this because I have the OS on a small system drive and then my data on a RAID5 array but it's always a good idea.
When you install if you select manual partitioning you can have a small partition as / and then the rest as a partition mounted at /data. The installer will take care of automatically mounting it at boot for you.
As for an encrypted home I'd say no. This can cause problems when trying to SSH onto the machine as the SSH keys are stored in /home and unless you are logged on locally the SSH daemon can't access them.

> 
2) What stuff should I check when I install Server Edition on the real server... obviously LAMP, open-ssh, PHP, mySQL etc.. what else?I never select anything from the tasksel menu you get on installation, I prefer to install the packages and set them up as I go along, this gives me a better understanding of the packages involved.
As for MySQL and PHP these are part of the LAMP metapackage (**L**inux **A**pache **M**ySQL **P**HP), I install all of these by running:
```
sudo apt-get install lamp-server^
```> 
3) How does openssh work (so I can access the server terminal from my laptop up in my room, when it's downstairs) right?You can install OpenSSH by doing:
```
sudo apt-get install openssh-server
```It's then just a simple matter of doing:
```
ssh user@serverIP
```in a terminal from any machine on your LAN to log in. You can also use [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") to log in from a Windows client.

> 
4) Will it use a static IP by default, or do I have to set this up? Can I have the address as something easier to remember (ie, replacing the IP with "server" or something so the URL would be [http://server/AjaXplorer-2.5.4](http://server/AjaXplorer-2.5.4) )You can set up a static IP during install, just hit ESC when asked for the hostname and select 'manual network settings'.
You can use names instead of IP's by setting up a DNS server for your internal LAN, a DNS server is used to map IP addresses to machine names and vice-versa.

> 
5) Can I have automatic login on the server, or is this a bad idea? Ajax won't work unless I'm logged in on the server, right?No need, all the services should automatically be configured to auto-start when the machine boots, I'd say the majority of Linux servers in the world never have any local users logged in.

> 
6) Will running the server 24/7 burn out the hard drives? Roughly how much power will it use?This all depends on your hardware. The most important issue is probably cooling, make sure you have sufficient airflow through your machine and space between the drives. I've had home servers made from desktop parts with uptimes measured in years.

You may want to take a look at some of the Ubuntu server tutorials on the internet, I've successfully used plenty of them when I was learning. Check out the 'Perfect Server' guides on [http://www.howtoforge.com/](http://www.howtoforge.com/) as a starting point.

I'm actually re-doing my home network at the moment with the Alpha of Lucid (10.04) and turning my documentation into a set of tutorials. It's very much at first draft stage at the moment but I'm aiming to have it all ready at the same time that Lucid is released, I'll let you know later when it's a bit more polished if you want to take a look.

---

### Post by humphreybc on 2009-12-20
That's awesome, I pretty much know what I'm doing now! Thanks for all the help.

I'm picking up [this computer]("http://www.trademe.co.nz/Browse/Listing.aspx?id=260894564") today that I bought, and then i've got to find a 500GB IDE Hard Drive.

Oh, one more question - I know it's possible to remotely shut down the server just by logging in from ssh and running sudo shutdown -h now, but what about turning it on? Does it depend if the BIOS supports wake on LAN or something?

---

### Post by Cheesemill on 2009-12-20
Wake on LAN is exactly what you're after, once enabled in the BIOS you can then send a so called 'magic packet' across your network containing the MAC address of the server which will cause it to switch on.

---

### Post by humphreybc on 2009-12-21
Picked up the computer today and a 500GB hard drive... I took it apart, cleaned it all out, installed the hard drive and another disk drive (to basically cover up a gap where there was no front placeholder plate) and then replaced some screws.. looking pretty damn good for $500!

I booted it up and have just started installing Server edition. Everything's going great, I'm amazed at how many options there are in the BIOS - this is perfect for a server, Wake on LAN, timed startup/shutdown, even overclocking facilities... crazy!

Anyway I'll post back here if I have any difficulties, but thanks to the virtualbox run through, I think I should be okay!

---

### Post by humphreybc on 2009-12-21
Hmm well so far so good, except when I set up AjaXplorer with /data as another repository, I get:

"Cannot initialize driver : Cannot create recycle bin folder. Please check repository configuration or that your folder is writeable!"

I presume that my data partition is getting mounted without rw permissions or something... I knew how to fix it in grub, but no idea in grub2...

---

### Post by humphreybc on 2009-12-21
Aha! It had to be owned by www-data for it to work. Success!

---

### Post by humphreybc on 2009-12-21
One more question:

Even though I've changed the PHP file size limit to 10,000MB - it still reports it as 1.76GB - any way to fix this?

And, the NUMBER of files is limited to 16 - i'd like to increase that to 200 or something, just to make stuff easy to upload in bulk.

---

### Post by humphreybc on 2009-12-21
Damn, it won't boot properly without a keyboard plugged in... which I don't want. Is there a way to get it to boot without a keyboard?

EDIT: Never fear, I worked it out! There was an option in the BIOS after all.

---

### Post by humphreybc on 2009-12-21
I'm just trying to set up a static IP address but having a bit of difficulty.

I'm trying to follow this guide:
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

I'm not sure what to put for a couple of the addresses in /interfaces and also no idea what to do with resolv.conf

When I actually take the router to its permanent home (i'm only setting it up at the moment), it will be connected to a different router than it is at the moment - will any addresses change, therefore I should just wait to set this up?

---

### Post by humphreybc on 2009-12-21
I don't suppose you know the solution to this problem?

[http://www.ajaxplorer.info/forum/comments.php?DiscussionID=121](http://www.ajaxplorer.info/forum/comments.php?DiscussionID=121)

I'm getting the I/O error then the HTTP error. I've tried some of their simple solutions but to no avail.

On the whole it pretty much crashes every time I try to upload something larger than 5 or 10mb... which is a bit useless for me.

EDIT: I just ran a few tests, here are the results.

Tested with both my 64 bit Ubuntu laptop in FF 3.5 and Chrome Beta, and a 32 bit Windows XP computer (Chrome) on the same network, both with flash 10.

Any file less than 1000kb works fine.
3.4mb file uploaded fine.
5.3mb file uploaded fine.
13.4mb file gave the two error messages below at exactly 6.56mb through upload
Anything above that failed to upload with the same error messages.

The first error message popped up:

"There has been an IO Error:Error #2038"

... then I click OK and this one pops up:

"There has been an HTTP Error: 412"



The difference between Ubuntu and Windows was that in Ubuntu Ajaxplorer would crash and 99% of the time not display the upload status bar during upload before it failed, whereas Windows did.

It seems a few people have run into this... I hope it can be fixed somehow, I'm loving AjaXplorer at the moment!

I've tried [this solution]("http://www.ajaxplorer.info/forum/comments.php?DiscussionID=418") by creating an ".htaccess" file in my root directory, / , but that didn't do anything.

I've tried some of the php changes here too: [http://www.ajaxplorer.info/forum/comments.php?DiscussionID=121](http://www.ajaxplorer.info/forum/comments.php?DiscussionID=121)

But it still aint working. :S



Oh yeah and sorry for the several post spam, easier to make a new post on a whole new topic for me.

---

### Post by humphreybc on 2009-12-21
This is turning into a nightmare. :S

I had a whole heap of charset errors when trying to change the locale, but I managed to fix that and get back to NZ with no errors.

Then I ran into an XML Parser error with AjaXplorer, every time I tried to log in or do anything it gives me this stupid error.

I tried to reinstall lamp-server^ to see if that would fix it, but it didn't do anything which is crazy. So even if I do manage to fix the XML Parser errors, I'm still left with the 2038 and HTTP errors that don't let me upload anything larger than 10mb.

Are there any alternatives to AjaXplorer??

---

### Post by humphreybc on 2009-12-21
Holy crap I think I just fixed it.

I posted my solution here:
[http://www.ajaxplorer.info/forum/comments.php?DiscussionID=672&page=1#Item_2](http://www.ajaxplorer.info/forum/comments.php?DiscussionID=672&page=1#Item_2)

---

### Post by donniezazen on 2010-10-12
> **Cheesemill said:**
> If the server VM has internet access just download it straight onto the server, this is assuming you have already got LAMP installed. Also how are you accessing your server? If you haven't yet installed openssh-server then I suggest you do that, you can then just copy and paste the following instead of having to type it all out.

```
cd /var/www
sudo wget http://downloads.sourceforge.net/project/ajaxplorer/ajaxplorer/2.5.4.def/ajaxplorer-core-2.5.4.zip
sudo unzip ajaxplorer-core-2.5.4.zip
sudo chown -R www-data:www-data *
```Then just point a browser to "http://serverIP/AjaXplorer-2.5.4/". Done.
You can see what I mean about it taking seconds to install in my earlier post :)

Just post back if you have any problems or want me to explain what any of these commands do.

When i try to open [http://serverIP/ajaxplorer/](http://serverIP/ajaxplorer/) it downloads a file with following text but not my filesystem in the browser.

> <?php
/**
 * Copyright 2007-2009 Charles du Jeu
 * This file is part of AjaXplorer.
 * The latest code can be found at [http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)
 * 
 * This program is published under the LGPL Gnu Lesser General Public License.
 * You should have received a copy of the license along with AjaXplorer.
 * 
 * The main conditions are as follow : 
 * You must conspicuously and appropriately publish on each copy distributed 
 * an appropriate copyright notice and disclaimer of warranty and keep intact 
 * all the notices that refer to this License and to the absence of any warranty; 
 * and give any other recipients of the Program a copy of the GNU Lesser General 
 * Public License along with the Program. 
 * 
 * If you modify your copy or copies of the library or any portion of it, you may 
 * distribute the resulting library provided you do so under the GNU Lesser 
 * General Public License. However, programs that link to the library may be 
 * licensed under terms of your choice, so long as the library itself can be changed. 
 * Any translation of the GNU Lesser General Public License must be accompanied by the 
 * GNU Lesser General Public License.
 * 
 * If you copy or distribute the program, you must accompany it with the complete 
 * corresponding machine-readable source code or with a written offer, valid for at 
 * least three years, to furnish the complete corresponding machine-readable source code. 
 * 
 * Any of the above conditions can be waived if you get permission from the copyright holder.
 * AjaXplorer is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; 
 * without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * 
 * Description : main script called at initialisation.
 */
include_once("server/conf/base.conf.php");
require_once("server/classes/class.AJXP_Utils.php");
require_once("server/classes/class.SystemTextEncoding.php");
require_once("server/classes/class.HTMLWriter.php");
require_once("server/classes/class.AJXP_XMLWriter.php");
require_once("server/classes/class.Repository.php");
require_once("server/classes/class.ConfService.php");
require_once("server/classes/class.AuthService.php");
require_once("server/classes/class.AJXP_Logger.php");
require_once("server/classes/class.AJXP_Plugin.php");
require_once("server/classes/class.AJXP_PluginsService.php");
require_once("server/classes/class.AbstractAccessDriver.php");

if(!class_exists("DOMDocument")){
        die("You must have libxml PHP extension enabled on your server.");
}
header("X-UA-Compatible: chrome=1");
HTMLWriter::charsetHeader();
$pServ = AJXP_PluginsService::getInstance();
$pServ->loadPluginsRegistry(INSTALL_PATH."/plugins", INSTALL_PATH."/server/conf");
ConfService::init("server/conf/conf.php");
$confStorageDriver = ConfService::getConfStorageImpl();
include_once($confStorageDriver->getUserClassFileName());
session_name("AjaXplorer");
session_start();

$outputArray = array();
$testedParams = array();
$passed = true;
if(!is_file(TESTS_RESULT_FILE)){
	$passed = AJXP_Utils::runTests($outputArray, $testedParams);
	if(!$passed && !isset($_GET["ignore_tests"])){
		die(AJXP_Utils::testResultsToTable($outputArray, $testedParams));
	}else{
		AJXP_Utils::testResultsToFile($outputArray, $testedParams);
	}
}

$START_PARAMETERS = array("BOOTER_URL"=>"content.php?get_action=get_boot_conf", "MAIN_ELEMENT" => "ajxp_desktop");
if(AuthService::usersEnabled())
{
	AuthService::preLogUser((isSet($_GET["remote_session"])?$_GET["remote_session"]:""));
	AuthService::bootSequence($START_PARAMETERS);
	if(AuthService::getLoggedUser() != null || AuthService::logUser(null, null) == 1)
	{
		if(AuthService::getDefaultRootId() == -1){
			AuthService::disconnect();
		}else{
			$loggedUser = AuthService::getLoggedUser();
			if(!$loggedUser->canRead(ConfService::getCurrentRootDirIndex()) 
					&& AuthService::getDefaultRootId() != ConfService::getCurrentRootDirIndex())
			{
				ConfService::switchRootDir(AuthService::getDefaultRootId());
			}
		}
	}
}

AJXP_Utils::parseApplicationGetParameters($_GET, $START_PARAMETERS, $_SESSION);

$JSON_START_PARAMETERS = json_encode($START_PARAMETERS);
if(ConfService::getConf("JS_DEBUG")){
	$mess = ConfService::getMessages();
	include_once(INSTALL_PATH."/".CLIENT_RESOURCES_FOLDER."/html/gui_debug.html");
}else{
	$content = file_get_contents(INSTALL_PATH."/".CLIENT_RESOURCES_FOLDER."/html/gui.html");	
	$content = AJXP_XMLWriter::replaceAjxpXmlKeywords($content, false);
	if($JSON_START_PARAMETERS){
		$content = str_replace("//AJXP_JSON_START_PARAMETERS", "startParameters = ".$JSON_START_PARAMETERS.";", $content);
	}
	print($content);
}
?>

---

### Post by CharlesA on 2010-10-12
Sounds like you don't have php5 installed.

---

### Post by donniezazen on 2011-04-27
> sudo chown -R www-data:www-data *

This solves file permission issues that i have but also lock files for my username.

> failed to open dir: "fsAccessWrapper::dir_opendir" call failed

This is what i get if i choose to enable create option while setting up repo.

> Cannot create recycle bin folder. Please check repository configuration or that your folder is writeable!

---


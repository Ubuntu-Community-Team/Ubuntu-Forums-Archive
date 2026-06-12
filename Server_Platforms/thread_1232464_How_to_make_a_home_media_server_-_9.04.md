---
title: "How to make a home media server - 9.04"
date: 2009-08-05
forum: Server Platforms
---

### Post by doomsayer97 on 2009-08-05
This is a simple *cough* not really *cough* guide on how to turn a spare laptop or something into a media server. Using the greatest OS on the face of the planet, Linux *cheers*.

I aimed this guide to work best for people who, like me, need someone to tell them exactly what it is that they are doing and why they are doing it. I added things like what commands do, and what certain things meant. If you have ANY questions, feel free to reply to this thread, or send me a PM. I will be sure to respond ASAP. 

I have included all the sources that I gathered this info from.

> 
This is just how to access your home server LOCALLY. I will be putting up another guide telling you how you can access it from anywhere in the world as long as you have an Internet connection.
Let's get started, shall we?

I'm going to first start off by giving you links to all my resources... Here they are:
[Benji Korsak]("http://rubbervir.us/projects/ubuntu_media_server/"). First comprehensive guide that I actually ever found. It worked quite well, actually. I just needed to change some of the codes around so that they would actually WORK. Don't use the last page, it's useless.
[Systm - Dynamic DNS]("http://revision3.com/systm/dyndns"). Systm was one of the greatest shows, of all time. Well, when it comes to tech stuff like this it is. May it rest in peace.
[Tech Support Forum]("http://www.techsupportforum.com/alternative-computing/linux-support/401303-access-media-server-outside-network.html#post2276866"). These people are skilled in just about everything. Anything you throw at them, they can answer. Usually... Don't be afraid to ask questions!
[UbuntuForums.org]("http://ubuntuforums.org/showthread.php?t=1229736"). Just a post that I made on UbuntuForums.org and I had some very friendly people help me out. I love communities :D
[Life Hacker]("http://lifehacker.com/software/web-publishing/geek-to-live-how-to-assign-a-domain-name-to-your-home-web-server-124804.php"). This is the source for my next guide... Know that it's coming :D


OK. Now that you've got those links read and at your disposal, we shall finally get into the awesome fun part that is...


CREATING A HOME MEDIA SERVER!!!! *cue awesome music*

Alright.


First, you'll need these things:
A spare laptop or desktop computer
Said computer device of choice must have enough hard drive space for your files you wish to share
MUST have an internet connection (preferably wired using Ethernet, but a STRONG wireless connection will work too)


I am using an old (OLD) [Dell Inspiron 1150]("http://reviews.cnet.com/laptops/dell-inspiron-1150/4507-3121_7-30836485.html"). It works great as a media server, because the backlight doesn't work, which means that it is useless to me as a laptop.

Alright so there are two ways you can go about doing this next part:
You can install the latest version of Ubuntu over at their [site]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition").
OR
You can get the server edition at their [site]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

I went with the desktop version, because that is all I had at the time and my main computer was out of comission at the time being. So, I went with the desktop (plus, it was a bit easier with a GUI). 
If you use the server edition: At the end of the installer there is an option for the type of server. You will choose the LAMP server. the LAMP server is:
Linux Apache MySQL PHP/Perl/Python
If you decide to use the desktop edition, I will walk you through the process of getting the stuff required for a LAMP server. 
THIS GUIDE WAS WRITTEN USING UBUNTU 9.04 DESKTOP EDITION. 

OK. Now for the REAL instructions:
(I suggest copy-pasting these commands into the terminal, because that way you won't get confused by letters and what have you. To paste into the Terminal on Linux, just tap the third mouse button, or the scroll wheel. If you do not have one, just right click>paste [I think]).

You're going to be installing SSH so that you can access your computer remotely, for whatever reason.
Open a Terminal window (The Applications tab in the top left, and then the first section down. It's sorted in alphabetical order, so Terminal will be near the bottom of the list). Type this command:
```
sudo apt-get install ssh
```Sudo is the command used to get root privileges. All apt-get commands MUST be preceded by sudo. Otherwise, you will get an error 13 message asking if you're root or not. You will be prompted for a password when using sudo (unless you've used sudo before in that session of the Terminal). Apt-get is just the command used to tell the computer to use the package manager. It's used to install software in Linux. Install is very straightforward ;). SSH is the name of the thing you are installing. SSH stands for Secure SHell. It allows you to remotely access your computer from anywhere.

Now, if you wish to use a different computer for the rest of this guide, you can. You'll need to grab a copy of [Putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"), however. Don't worry, it's freeware. 
In the terminal type:
```
ifconfig
```You should see a number (in the long list that appears) that says something like 192.168.15.x, or something similar. This is the INTERNAL IP address of your Linux box. You will type that into the host address of Putty. Leave everything else alone and hit connect. Then you'll need to type in the username and then the password. Then you can do whatever you want within the TERMINAL interface. Not a GUI ;)

No make sure it's up to date...
```
sudo apt-get update
```And install those updates:
```
sudo apt-get upgrade
```Now you should be good to go!

Now you'll need to install Samba. Samba is used to connect your Linux machine to a workgroup. 
```
sudo apt-get install samba smbfs
```Now you need to stop the Samba service so it doesn't interfere with the next commands:
```
sudo /etc/init.d/samba stop
```And now you'll need to move it so that you can easily find it within your server:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.orig
```The mv command just means move.
You'll need to create a file for Samba:
```
sudo touch /etc/samba/smb.conf
```And then edit it:
```
sudo pico /etc/samba/smb.conf
```And now you'll need to paste this stuff into the space that will appear:
```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

```(THERE ARE SEVERAL DIFFERENT TEXT EDITORS. PICO IS INSIDE THE TERMINAL, BUT YOU CAN USE GEDIT IF YOU SO CHOOSE. GEDIT IS LIKE NOTEPAD, BUT IN LINUX. GEDIT WILL ALSO ALLOW YOU TO USE CONTROL + F TO FIND THINGS; ESPECIALLY USEFUL IN THE NEXT SECTION).

```

Replace "YOUR_HOSTNAME" with anything you want, preferably the name of your Linux box
Replace "YOUR_WORKGROUP" with the name of your Windows workgroup
Replace "/media/samba/" with the path of the folder you want to share
Replace "YOUR_USERNAME" with your username

```Now you'll need to save it:
```

Control + X 
Y (The letter y, just tap it ;))
Enter

```Now you'll want to set the permissions so that you won't have any issues with the Samba service. 
REPLACE "/media/samba" WITH THE DIRECTORY THAT YOU SPECIFIED EARLIER (about 8 lines up).
```
sudo chmod 0777 /media/samba
```For example, I used my Music directory. So MY code would look like:
```
sudo chmod 0777 /home/dilyn/Music
```Now you'll need to add a user:
```
sudo smbpasswd -a system_user
``````
sudo pico /etc/samba/smbusers
```And insert the following line into the new file:
```
system_username = "network username"
```And save it:
```

Control + X 
Y (The letter y, just tap it ;))
Enter

```And now you're all done!!! ...With Samba...


Go onto these next steps to setup your awesome amazing new software:

[Jinzora!!!]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fen.jinzora.com%2F&ei=jrN5SsTbC4fIMfjEqKMO&usg=AFQjCNG3Gz46w4h_CCpol_Ii8uekzIx91g&sig2=mkP4mGx_8YG3MZUt9ttPew")

You can read about it if you want... But it's basically just a web based browser thing that allows people to browse through your media in an interesting way.
Just something fun for you! 
My server has been up for:
```
up 1 day, 16:29
```Since 12:32:11 (PM). 
It's working like a charm :ugeek:

So now you'll need to install LAMP and set it up for Jinzora to work properly.

PAY CLOSE ATTENTION.

WHENEVER I USE THE WORD 'pico' IN A COMMAND, FEEL FREE TO SWAP IT OUT WITH 'gedit'. THEY DO THE SAME THING, BUT GEDIT ALLOWS YOU TO SEARCH FOR TEXT USING CONTROL + F, WHICH MAKES THESE NEXT STEPS A LOT EASIER.

Now run the following commands in the terminal:
```
sudo apt-get install apache2
``````
sudo apt-get install php5
``````
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
``````
sudo apt-get install php5-gd
```Now you'll need to configure PHP5 in order for it to meet Jinzora's requirements.

```
sudo pico /etc/php5/apache2/php.ini
```Now change these values:
```

"max_execution_time" to 300
"memory_limit" to 128M
"post_max_size" to 32M
"file_uploads" to On
"upload_max_filesize" to 32M 

```This will allow PHP5 to work correctly with what Jinzora requires it to do. Unless you change these values correctly, you WILL NOT be able to install Jinzora. It just won't let you.

Now you'll need to configure MySQL (pronounced My Sequel). You'll need to make it so that the database can be accessed from the computer.

```
sudo pico /etc/mysql/my.cnf
```And change these values:
```


bind-address = localhost
to
#bind-address = localhost

```Now here is where I ran into some trouble. If you're not looking at the rubbervir.us site that I linked to at the beginning, you don't need to worry. But if you are, don't listen to his commands that he gave you for the MySQL part. They're WRONG in just one little, tiny way.

```
sudo mysql -u root -p
```I don't even know what -p needs to be there for, but it does. If it's not there, it won't work. Now just edit these values:
```

SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

```Change the "PASSWORD('yourpassword')" part with a password of your choosing. LEAVE THE SEMI COLON THERE.
```

GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;

```Change 'yourusername' with a username of your choosing. LEAVE 'localhost' ALONE. Change 'yourpassword' with the password that you added in the previous bit. 
```

/q

```Now you've properly configured MySQL.
DON'T FORGET THAT USERNAME AND PASSWORD. You will need those for setting up Jinzora to work correctly. 

Now here's where all that work comes into play:
Restart Apache.
```
sudo /etc/init.d/apache2 restart
```Apache SHOULD eventually restart itself. 
Now open up your browser and enter your IP address. If you forgot what it is, just type 
```
ifconfig
```into the terminal again. 
You should be greeted by a page either saying "It works!" or listing off a whole bunch of stuff about Apache and things... If not, you'll need to do some port forwarding.

Find your EXTERNAL IP address. Just use
```
ifconfig
```again, and you'll be able to find it. Now enter that IP address into your web browser. Login to your router's configuration page. My router is NOT the same as yours, but you can go [here]("http://portforward.com/") to figure out what you need to do for your router. After you select your router, look in the A's section for Apache and click that. You'll need to forward ports 80 and 443. 

Now you get to do the fun part:
Installing Jinzora!!!

Go and download it... Shouldn't be too hard. If you want to be lazy about it, just enter this code into the Terminal:
```
wget http://en.jinzora.com/downloads/jinzora_releases/28
```If that is not latest stable version, then I suggest you go over to their site and you download it. When you download it, but it on your desktop and use this command:
```
cd /home/'YourUsernameHere'/Desktop
```(Replace 'YourUsernameHere' with your username ;))
And then run these commands:
```
sudo tar xvzf 'name of Jinzora'
``````
sudo mv 'Name of the extracted folder' /var/www/jinzora2
``````
sudo rm 'name of the tar'
``````
sudo chmod -R 777 /var/www/jinzora2
```(Replace the things in little quotes with the actual thing's name).

Now the rest of this can be done in your web browser.

Enter the IP address of the server into your browser.
If you don't see a list of things within the '/' directory, and you just see a window that says "It works!", then enter this code into the terminal:
```
sudo rm /var/www/index.html
```Now you should be good. 
hit the directory that says 'jinzora2/'. Now you just need to proceed through the web based installer.

Click the "Proceed to Requirements>>" button.

Read through all the information on the screen, you should not see any red words under "Requirements" other than the proceed button.

Yes, good? Click the "Proceed to License>>" button.

Agree and continue.

Click the "Proceed to Main Settings>>"button.

Fill out the text boxes, but this time leaving "Default Access Level:" and "Backend Type:" as is and continue.

Once again fill out the text boxes leaving "Database Server:" and "Database Type:" and changing "Create Database:" to true. Continue.

Everything should have been successful. If it says failed created database, double check that on the previous page you used the same user name and password you created when setting up MYSQL. Hit "Proceed to Import Media>>"

Here is where you specify the location of your media, if you did not change it from the previous tutorial it will be in /media/samba/. So navigate to that directory and select analyze. How much media you have will determine how long it will take to import. About 15 songs per second.

Click "Proceed to Save Config>>," "Proceed to Launch Jinzora>>," choose to share anonymous stats or not and finally click "Launch Jinzora"

Login and explore. Now it should say something about it not being secure, so open up ssh again and from the terminal type.
```
sudo rm -r /var/www/jinzora2/install
```Refresh and explore.


If you restart your server, you may have issues connecting to it again. Here's what you'll want to do:

Upon restarting your server, enter these commands into the Terminal:
```
sudo /etc/init.d/apache2 restart
``````
sudo /etc/init.d/mysql restart
```Now it should work just fine.



> 
Again, this is just how to access your home server LOCALLY. I will be putting up another guide telling you how you can access it from anywhere in the world as long as you have an Internet connection.


---

### Post by doomsayer97 on 2009-08-05
This is part 2 of my guide on how to make a media server in Ubuntu 9.04. If you haven't read part 1, I highly suggest doing so, because you'll need a server setup and ready in order to do ANY of this ;)

You can read part 1 [here](http://ubuntuforums.org/showthread.php?t=1232464).

I only had one source for this part. But that doesn't mean that they don't get credit for this!!! 

Here you go, Life Hacker.
I used [this]("http://lifehacker.com/software/web-publishing/geek-to-live-how-to-assign-a-domain-name-to-your-home-web-server-124804.php") guide to figure out how to use this... 
And I suppose I also used Systm's [guide]("http://revision3.com/systm/dyndns") as well. So they both get credit :D


Alright. So you've got your server all setup and whatnot. You can listen to all your music just fine. But ONLY on your network. What about that business trip your were gonna go on. Better bring an MP3 player. And that vacation? You'll be music-less without this guide. 


Alright so what you'll need to do first is head on over to [DynDNS]("http://dyndns.com") and make an account. Don't worry, it doesn't cost any money to create an account or to register your own custom DNS. That's right, you can have up to five different little websites all for free. One condition though. You need to have little appendages like .is-a-geek.com or .kicks-***.org. But as long as you can live with that, you'll be all good :D
Or you can just pay about $30 a year and you can have your own personal DNS. Your choice. 



Either way, after you've created your DynDNS account and logged in, you'll wanna look at one of the three big sections in the middle of the page. 
My Services
Billing
Account Settings
Look at the My Services section. You'll find a subsection labeled My Hosts. Under that, you'll find another subsection labeled Add Host Services. Click that link. 
Now this next part is up to you. 
In the first empty text box, you can pick anything you want. Heck, you could put anything from the number 1 all the way to something totally outrageous like Itsoverninethousandomnomnomnomnom. SOOOO...
After you're done with that...
In the next box you'll see all sorts of different little appendages. You need to pick one that you like. After you find one that you like (I prefer is-a-geek, kicks-***, and homelinux), you'll go down to the section labeled IP Address. Don't mess with any of the radio boxes... You don't need to. Unless you really know what you're doing. But if you do, then I don't understand why you're reading this guide  :shock:.
Hit the hyperlinked words under that text box. It should say something like Use Autodetected IP address xx.xxx.xx.xx. After the box is filled in with that IP address, hit Add to Cart.

Now you just need to proceed through the checkout (it's completely free, no credit card info is asked or anything like that).

After you've done that, the service SHOULD be active. It'll take you to a page that has a list of all your hosts. If it doesn't list the Internal IP address of your server, then you need to figure out what went wrong. 

Now, here's the kicker:
YOU can't test if it works or not, unless you use a proxy or you use a computer not connected to your network. Otherwise it'll just take you to your router login page.  :lol: 
So, give the link to someone you know, and ask them what shows up. If all went well, they should see something that looks similar to [this]("http://mymediaserver.homelinux.com") page. (Yes, that IS my server). If they do, congrats! If they don't, figure out what went wrong and if you can't figure it out, ask me. I'll be more than glad to help.


Hopefully you found my guide helpful :)


Again, you can find my server [here]("http://mymediaserver.homelinux.com"). The login details for an account are:
Username: default
Password: default

If you would like an account on my server, just ask me and give me the details you would like it to have and I'll set it up for you. 

If you would like to add music to my server, ask and I'll tell you what to do.


I'll be making ANOTHER guide. This time on how to add music remotely to your server.

Until next time, enjoy your server!!!



> 
Beware!

If you restart your server, your IP address WILL change. That means that you will need to forward your ports to that new address. If you don't know what that means, you'll need to look at part one of my guide. You can find it [here]("http://techchatforums.com/viewtopic.php?f=53&t=257&start=0"). Just don't restart your server and you should be fine ;)


---

### Post by FerociousTwig on 2009-08-06
Why not just have them configure a static IP and forward ports there?

Very easy to do...

```
 sudo vim /etc/network/interfaces
```

---

### Post by doomsayer97 on 2009-08-06
Well now that works too.

I would love to have a static IP. I'm gonna go and try that. Thanks.

Although you really only need to setup a static IP if you plan on restarting the server very often. Otherwise, it will just keep the same IP address.


EDIT
So what would you edit to make it a static IP?

---

### Post by Bucky Ball on 2009-08-06
local machine sends IP to router, not other way around. Set in System-Admin-Network. You can probably do with the router, depending on the router, but didn't work with mine. This way works a treat.

DHCP server and static IP should be DISabled in the router (as static setting in the router will try to send a static IP and sometimes prevents one coming in even it does not actually have a static IP to send).


Good guides. I found it a bit confusing in the first one which machine I should be doing what on sometimes but sure people will find these helpful. Good work.

---

### Post by doomsayer97 on 2009-08-06
It should also be stated that most routers nowadays have support for services such as DynDNS.


And you can just install the DDClient on Ubuntu so that the IP address will constantly be updated.


EDIT

While purusing around the settings in my router (Dlink VWR 11.4 I believe), I have found a radio box that allows me to 'reserve'. Does that mean it will reserve my IP address for that device? If so, it'd be super simple to make it keep that address.

---

### Post by FerociousTwig on 2009-08-06
Ok few things. DynDNS is for your external IP address. That will allow you to update any web redirects you may have without having to do it manually everytime your ISP gives you a new external IP.

The static IPs we were discussing is for your internal network. The IP that identifies each computer on your network. To create a static IP you need to type

```
sudo vim /etc/network/interfaces
```

which will open a file. Edit that file to make it look something like this...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```


The eth0 section is an example, you need to fill in your own info there. Confusing at first, but if you type
```
sudo ifconfig -a
```
that will give you the information you need to fill in underneath  he line ----- #The primary network interface

---

### Post by Bucky Ball on 2009-08-07
Or you could just do it through the 'Network' GUI as suggested earlier, whichever suits you best. You will also find a tab there called 'DNS' where you will find your DNS server IPs.

---

### Post by haydenSUDOuser on 2009-08-19
i followed these steps and wrote everything as posted and for some reason i can no longer log into my machine!, is there a way i can reset the installation or do a rollback, without having to reinstall the whole machine again

---

### Post by doomsayer97 on 2009-08-19
I believe all you have to do is delete the Jinzora directory in the 'www' folder. That should do it... Then just reinstall Jinzora at that directory and you can redo the Jinzora installation.

_***BUT BEFORE YOU DO THAT:***_

Did you happen to reboot your machine between being able to connect and being unable to connect?
If you did, use this step from the guide:

> 
If you restart your server, you may have issues connecting to it again. Here's what you'll want to do:

Upon restarting your server, enter these commands into the Terminal:
 	Code:
 	sudo /etc/init.d/apache2 restart 
 	Code:
 	sudo /etc/init.d/mysql restart 
Now it should work just fine.


But if that's not the case, still try it ;)

---

### Post by hibliss on 2009-08-19
I guess it all depends on what you are streaming to or serving, but this seems pretty complicated for a simple home media server.

---

### Post by doomsayer97 on 2009-08-19
Well, it's not really all that complicated. 

I mean, it only took me a couple days to setup because I had to ask all kinds of questions about stuff and edit up the orginal codes. This should only take you AT MOST a couple hours to do.

---

### Post by haydenSUDOuser on 2009-08-20
I will try that and let you know. 

thanks

---

### Post by haydenSUDOuser on 2009-08-20
for some reason when i went to redo these instruction i can not set an smb password it says "Failed to modify password entry for user system_user"

---

### Post by doomsayer97 on 2009-08-20
What are you typing in during that part?
[COLOR=#33ccff]```
sudo smbpasswd -a system_user 				
```[/COLOR]

---

### Post by haydenSUDOuser on 2009-08-22
thats exactly what i type in, i dont understand why it doesnt work, could i need to reset my root shell prompt or something because im denied?

---

### Post by doomsayer97 on 2009-08-26
I suggest starting over with the Samba section of the guide. My guess would be that you did something wrong there.

---

### Post by nameproblem on 2009-08-29
I followed the directions completly, all installed, but then got an "Invalid Language" error when i launched Jinzora2. Any one with any ideas? please

---

### Post by cyberaed on 2009-09-03
doomsayer97, This looks like a really good guide. I'm new to Ubuntu and have been trying to install jinzora, but unsuccessfully so far.

Do you know if this works on 9.04 server edition? I installed the server edition and set it up as a LAMP server during install.

Thanks,

---

### Post by doomsayer97 on 2009-09-03
It should work just fine.

I was using the desktop version of Ubuntu 9.04 and it worked just fine. 

I'm gonna get a copy of the server edition and try it out... But it sounds like you've done it right. 

What exactly is it that stops you from installing Jinzora?

---

### Post by cyberaed on 2009-09-04
Basically, I couldn't unzip the tar file from jinzora website.
I was having errors with gzip - I forget what they are now.

Anyway, I decided to install 9.04 desktop instead and now I have Jinzora up and running.

But when I try to stream from the server to my laptop, my laptop downloads the m3u playlist and shows it in iTunes, but it won't play anything.

I don't know where to go from here - any ideas please? :confused:

---

### Post by doomsayer97 on 2009-09-04
I suggest using Windows Media Player. It's much faster.

Or SongBird.


They usually work great. I've tried to do it in iTunes before, but it always seems to take FOREVER to load :\

---

### Post by cyberaed on 2009-09-04
Thanks mate, I'll give Songbird a go.
I've been meaning to install it - now I have another reason to try it lol :D

---

### Post by cyberaed on 2009-09-05
Hi, Just thought I'd let you know I installed Songbird and it's working like a charm.
Thanks mate :)

---

### Post by MrWES on 2009-09-05
If you're looking to just share your music library on a home network; you could install mt-daapd (aka Firefly Media Server). It's in the repositories and the Ubuntu default music player and iTunes for Windows are capable of seeing and using mt-daap shares.

Also, if you so happen to own a PS3, you could run Mediatomb and stream to the PS3, music, video and pictures.

Bill

---

### Post by Jose Catre-Vandis on 2009-09-05
Similarly to MrWes, why not just install [gnump3d]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=2&url=http%3A%2F%2Fwww.ubuntugeek.com%2Fstreaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html&ei=ftGiSs_ZB82h4QaT2pjvCQ&rct=j&q=gnump3d+ubuntu&usg=AFQjCNFXL8Xf00kLGlqYHaU_LTxpPz2aag&sig2=TQ4K5Q2J6cwxcV6IUhOqEg") this will server up mp3 and avis via a web interface. No need for LAMP server stuff, or even a GUI desktop.

Sadly no longer in the repos, but you can get version 3 as a tarball from [here]("http://rapidshare.com/files/276129148/gnump3d-3.0.tar.gz")

---

### Post by kraken613 on 2009-10-26
When I am at the making user part when I enter "sudo smbpasswd -a system_user" It tells me cannot locate UNIX account for 'system_user'!

What am I doing wrong?

---

### Post by doomsayer97 on 2009-10-27
Are you editing the smb.conf file? Be sure to replace the correct stuff...

---

### Post by kraken613 on 2009-10-27
I am pretty sure I did.

For Hostname I put MEDIASERVER. For Workgroup I put WORKGROUP because that is just what I left mine as. For the file I put /home/david/Music/ because that's where I want it. Now for username I put david. Am I supposed to put something else?

Thanks!

---

### Post by Maheriano on 2009-10-27
What benefits does this guide have over a regular Desktop install and Boxee?

---


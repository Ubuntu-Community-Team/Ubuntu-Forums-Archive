---
title: "How does ISPCONFIG work?"
date: 2007-12-22
forum: Server Platforms
---

### Post by icantfindausername on 2007-12-22
First Off, I successfully installed everything.  ispconfig works, but when I create a new site, where is it located and does it have it's own IP address?  I can't afford to buy domain names to test with, so I was going to test it out with ip addresses...if possible.  Then if everything works out, I will get some domain names.

I read this post [http://ubuntuforums.org/showthread.php?t=355474]("http://ubuntuforums.org/showthread.php?t=355474")
 but shouldn't a virtual server have its own address?

thanks

---

### Post by rsw686 on 2007-12-22
> **icantfindausername said:**
> I can't afford to buy domain names to test with, so I was going to test it out with ip addresses...if possible.  Then if everything works out, I will get some domain names.
thanks

It would be better to buy one or two names and set it up. I don't understand how you can't afford to buy the domain names to test, but you're going to buy them if it works. Do you not need the sites?? If it doesn't work will you just not run the sites then?

Whether you host your own site or have it hosted you should purchase the domain name yourself. That way you are in control of it. I ran into issues with the web host changing the contact information when I asked them to unlock my domain. Then I had to wait 60 days to transfer for.

Anyway you only need one IP unless your using HTTPS, which then you need one IP per HTTPS site.

I don't use ISPConfig as I edit the files by hand. What you are asking to do is easy to implement. I'm sure with ISPConfig it is even easier to implement.

---

### Post by now-new on 2007-12-23
why dont you use a free domain I mean like dyndns.com where you can get a domain for free?
the think is I can test my page which ends in "ath.cx" doesnt run when I type it with the www just with the http://
does anyone have any answer to that?

---

### Post by icantfindausername on 2007-12-23
i actually have a domain name.... its asrgraphics.selfip.net using dyndns... it would show my www folder before i installed ispconfig.. 
now it doesn't do anything, unless I boot into windows, then it shows my website running off apache in xp.

how can I set up the asrgraphics.selfip.net?  I'm new to virtual hosting,

once again thanks.

---

### Post by computec on 2007-12-23
I just looked at your address "asrgraphics.selfip.net" It is working ok from what I see. It is showing the index.html page. All you need to do is to ftp to the address [ftp://asrgraphics.selfip.net](ftp://asrgraphics.selfip.net) and login with the username and password that you set up for that site with ISPconfig and upload your new index.html and any other files. ISPconfig creates a new folder for eash new site that you setup in /var/www/
example: /var/www/web5/
example: /var/www/web8/
example: /var/www/web12/

Also under the web5 dir will be you ftp, mail, cgi-bin, log, user, and web folders.
The web folder is where the website files go.
They should go there when you ftp to the site with the correct login and password for that site.

When you create a new site with ISPconfig, they all have the same IP just different hostnames.
So for each domain name just point it to your IP address and then set it up with ISPconfig.
Example: my server address is computec.damnserver.com
I also have computec.homelinux.org
both site were setup using ISPconfig.
I have raven1.bpe.org pointed to the same IP but it is not setup with ISPconfig so it goes to the default ISPconfig site.
The default site is found in: /var/www/sharedip/

I don't have a static IP so I am using dynamic ip updating addresses.
You can setup 5 dynamic domain names for free from no-ip.com
Point them all to the same IP and then setup eash one with ISPconfig.
This would be a great way to test things.

I hope this helps,

Alan
Computec

---

### Post by computec on 2007-12-23
I forgot to say, It would be well worth setting up your server on another PC so you could get rid of windows.
I use windows on most of my desktops and laptops. I do have linux on one desktop besides my server.
My server does not have a graphical interface. It's all done by command line, however to make things easy I do use webmin along with ISPconfig.

Alan
Computec

---

### Post by icantfindausername on 2007-12-24
computec, thanks for the input.   
My brother was on windows playing war of worldcraft and that is why the site worked.  I cannot get it to pull up for some reason on ubuntu since I installed ispconfig. To be honest I don't know what I am doing as far as DNS stuff.  


If I knew what settings to edit.  My computer is setup with a static ip address of 192.168.1.110


here is my hosts file:
------------------------------------------------

127.0.0.1 localhost
192.168.1.110 server1.example.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---------------------------------------------------
and in etc/hostname

server1.example.com




Also in my router do I need to do port forwarding?

---

### Post by icantfindausername on 2007-12-24
Nevermind I finally got it.........
Had to port forward in my router port 80 to my ip address.
Then changed in my site under ispconfig  hostname: asrgraphics
domain: selfip.net

---

### Post by dysolve on 2007-12-31
I have been using ispconfig for about a year now and I host 4 sites with e-mail and it works great.. a few things i have noted since installing it..

1. unable to view sites locally due to router blocking them and theres nothing you can do in the router to fix that (most routers are like that) but the solution was to edit my hosts file under windows and it worked great..

2. make sure all ports required by ISPconfig are forward from your router to the ispconfig box..

3. works fine with dyndns domains once you figure out how to host them ( seems like you found this out)

4. it makes it so much easier then hand editing file on the server..

if you need help PM me and I can help you out , I maybe only new at this hosting thing but ispconfig makes it easy..

---


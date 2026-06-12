---
title: "Best web-based file manager?"
date: 2010-11-15
forum: Server Platforms
---

### Post by X1R1 on 2010-11-15
Hi, I have a file server setup at work running for a while now, all is donde from the command line, but I want a more graphic approach to this to move folders, change persmissions and stuff like that.

What do you recommend for this?

I have checked extplorer and ajaxplorer but cant find them in the ubuntu repos and I dont want to install from source and manually update the package each time a new version comes out.

So, is there any web-based file manager on the ubuntu repos? which one is the best?

thanks in advance

---

### Post by SeijiSensei on 2010-11-15
Try **Midnight Commander**.  (sudo apt-get install mc)

I don't know how you'd run a web-based file manager since the web server (Apache) runs as an unprivileged user.  You could run it as root, but then any file you create would be owned by root, not by you.

---

### Post by Jose Catre-Vandis on 2010-11-15
Try FireFTP, yes its an ftp client for Firefox, but will also work as a file manager of sorts

---

### Post by X1R1 on 2010-11-15
to explain a little further, users are authenticated to the file server using active directory, what I would need to do its create folders and change permissions according to group membership and stuff like that. 

As as im concerned, I think Midnight commander doesnt have a remote connection feature, it only works on where you install it.

right?

---

### Post by arrrghhh on 2010-11-15
[ajaXplorer](http://www.ajaxplorer.info/wordpress/) is the only one I am aware of TBH, and it works well - but I have no clue how it'll act with your AD users...

---

### Post by SeijiSensei on 2010-11-16
> **X1R1 said:**
> to explain a little further, users are authenticated to the file server using active directory, what I would need to do its create folders and change permissions according to group membership and stuff like that. 

Users may be authenticated with their usernames, but the web application itself is going to have the same permissions as the user under which the server software runs.  If you're using Apache as a web server, it runs as the www-data user and won't be able to manipulate other users files or permissions. You could write a web application that runs with root privileges and can manipulate users' files, but that would require a custom application.

> I think Midnight commander doesnt have a remote connection feature, it only works on where you install it.

You can ssh into the server and run it remotely that way.

If your users are on Windows, why not just run Samba on the server and let them mount shared resources that way?  Then you'd avoid any issues about permissions.

---

### Post by Vegan on 2010-11-16
Webmin has a good Java based file manager with a few that is familiar to users of recent GUIs.

Easy to use buttons with edit capacity make fixing config files a breeze.

Webmin can log in as a user with sudo capacity if needed.

Its safe enough to post online to make managing 1000 servers easy.

---

### Post by X1R1 on 2010-11-16
> **SeijiSensei said:**
> 
If your users are on Windows, why not just run Samba on the server and let them mount shared resources that way?  Then you'd avoid any issues about permissions.

Resources are mounted that way, I just want to have a visual look at files to better understand the structure.

I have used webmin in the past, but it was a long time ago, maybe its time to check it out again :D

Will do and come back with results!

EDIT: What is the webmin package name? sudo apt-get install webmin returns this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate


Am I missing something?

EDIT= Yes I was missing something, here is the solution:

> Using the Webmin APT repository
If you like to install and update Webmin via APT, edit the /etc/apt/sources.list file on your system and add the line :
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
You should also fetch and install my GPG key with which the repository is signed, with the commands :
cd /root
wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)
apt-key add jcameron-key.asc
You will now be able to install with the commands :
apt-get update
apt-get install webmin
All dependencies should be resolved automatically.

---

### Post by Vegan on 2010-11-16
I used a slightly graunchy approach.

I downloaded the deb file from the web site.

Then installed it, but apt complained about dependencies

```
sudo apt-get -f install
```

Then the installer came back to life and it works.

So either route gets webmin up.

---

### Post by i.r.id10t on 2010-11-16
Get an X server for your local machine (I think Mac still comes with one, cygwin-x on windows), ssh in and export your display back to your local machine, and then run nautilus.

---

### Post by SeijiSensei on 2010-11-17
If you're the only person who needs to do this, then I think i.r.id10t's suggestion above is the best one.  I've done this from time to time as well.  I've also run Firefox on clients' servers to see the Web the same way they do in case there are differences in DNS, filtering, etc.

Just a bit of caution about Webmin:  I only use it in situations where I have very stringent control over access to port 10000 or whichever port it's assigned to because the server runs with root privileges.  I'll use it over an OpenVPN tunnel or with iptables rules that block anyone but me from the webmin port.  Opening the port to the world is asking for ownage.

---

### Post by volkswagner on 2010-11-17
It seems all options have a trade off on security vs. being able to accomplish what you want to do.

I am not a security expert so I don't know which is the worst of all evils.

Although I don't recommend allowing root logins to a server, if you already have this allowed you can connect via sftp from your Ubuntu desktop by going to <Places><Connect to Server> choose ssh as the protocol and use root as the user.  This will give you a gui window for manipulating the file system... WARNING this is not recommended by is is used by some.


Let the flaming begin... LOL

---

### Post by X1R1 on 2010-11-19
> **i.r.id10t said:**
> Get an X server for your local machine (I think Mac still comes with one, cygwin-x on windows), ssh in and export your display back to your local machine, and then run nautilus.

Any tutorial on how to do this? you mean SSH tunneling with X11 port forwarding right?

EDIT= Webmin its cool and all, but I figured that it would pose a security risk, also it has A LOT of things that probably I would NEVER use.

So, I install nautilus on the server and connect via SSH to it and then export the display to my local machine right?

I read somewhere that you can do this by typing:

ssh -X user@serverIP

then everything regarding to x applications will display on my comp?

is that correct?

---

### Post by arrrghhh on 2010-11-19
> **X1R1 said:**
> Any tutorial on how to do this? you mean SSH tunneling with X11 port forwarding right?

EDIT= Webmin its cool and all, but I figured that it would pose a security risk, also it has A LOT of things that probably I would NEVER use.

So, I install nautilus on the server and connect via SSH to it and then export the display to my local machine right?

I read somewhere that you can do this by typing:

ssh -X user@serverIP

then everything regarding to x applications will display on my comp?

is that correct?

Yes.  Read man ssh if you're confused.  -X forwards any X applications to your local X server.  So if you're not on a Linux box you'll need cygwin or xmming.

---

### Post by X1R1 on 2010-11-19
Running ArchLinux here so no problem, worked like a charm. I was a bit confused, I tought you need to have the app installed on the client and tell the server to use that, but its the other way around, you just forward the output to the client.

All clear now :D Im fact I want to test all possible file managers now that you explained that to me, trying thunar with the X11 forwarding at the moment, no lag at all, gonna try also PCman and nautilus and make a choice, maybe I will write a nice blog post about this :D

That was exactly what I was looking for! a file manager without bloating the server with applications and security risks :D

File managers with dependencies and all take about 100mb total space, not big of a deal, and very low memory since its been forwarded. It really shines!

EDIT= quick question, apache is still installed on my system, I THINK that the only app using it was webmin, how can I check if an application still depends on it?

---

### Post by SeijiSensei on 2010-11-19
> **X1R1 said:**
> EDIT= quick question, apache is still installed on my system, I THINK that the only app using it was webmin, how can I check if an application still depends on it?

AFAIK, Webmin runs its own HTTP server; it doesn't use Apache at all.

---

### Post by arrrghhh on 2010-11-19
> **SeijiSensei said:**
> AFAIK, Webmin runs its own HTTP server; it doesn't use Apache at all.

Wow, I learned something new today, thanks :D

From the [Webmin and Apache doc](http://www.webmin.com/apache.html): > Webmin comes with a very simple webserver called miniserv.pl that is capable of doing all that is necessary for Webmin to run. However, it is not as fast or memory efficient as a well-developed server such as Apache

---

### Post by nymusicman on 2012-06-02
> **X1R1 said:**
> 
EDIT= Webmin its cool and all, but I figured that it would pose a security risk, also it has A LOT of things that probably I would NEVER use.


Webmin is only a risk if you allow outside access to port 10000 through your firewall. 

Also webmin doesn't need all of the "other features" installed to run. Your thinking of Virtualmin. While webmin can do all the other stuff your talking about, it doesn't need those dependencies to be installed or run, at least not on a debian/ubuntu based system.

The only thing missing for me that eXtplorer can do that webmin file manager can't, is other site to my site transfer. For instance if I want to install drupal on my site I never have to leave the browser or download anything to my Downloads folder, I simply copy the url, stick it in eXtplorer and it transfers directly to my server.

---


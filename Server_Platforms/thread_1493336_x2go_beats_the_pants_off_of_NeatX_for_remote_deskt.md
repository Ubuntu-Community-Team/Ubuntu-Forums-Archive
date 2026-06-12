---
title: "x2go beats the pants off of NeatX for remote desktop capabilities"
date: 2010-05-25
forum: Server Platforms
---

### Post by bmullan on 2010-05-25
I feel I'm pretty experienced with NX whether it is NoMachine's server or client or their Web-Portal.

I also used FreeNX server with the NoMachine client for quite a while.

For the past week I've been trying to use NeatX server just so I can have a decent remote desktop to Ubuntu machines running on Amazon's cloud AWS EC2.

First impressions are the NeatX is a pain the butt !

Besides key features that aren't implemented yet, bugs like the old sessions clean up problem are just a real time burner to clean up or work around.

After my fairly successful early use of NoMachine client & server and then client and FreeNX server... my biggest problem was sound/audio.

Then I tried x2go.   It was like a breath of fresh air.

The server side has 3 different flavors ... and I installed the x2go-home on my AWS EC2 Ubuntu Servers.

I've used the debian ppa documented at the [**x2go website**]("http://www.x2go.org/index.php?id=7").

After adding that PPA you run sudo apt-get update then you can go into Synaptic and enter x2go as a search and you will see all of the many possible components you can utilize.

However, at a minimum you just need to select to install the x2go-home server.

After installation on your server go back to your remote machine and install the x2go client for Linux (or Windows if your machine is windows).

Then if on Ubuntu Click on Applications then Internet then x2go Client GTK.

The x2go Client window will pop up.

On the right side will appear boxes identifying any "profiles" you've already made.

There is a small "V" type of icon in the lower right corner and if you put your mouse on it you can choose to Edit Preferences.

Enter the Host IP Address of your Server or its DNS name at a minimim and save.

Click on the profile box you just created/edited and it will move to the left side of the screen.

enter your remote machine ID and password and if all goes well you should have a complete remote X desktop presented within a few seconds.

Surprising is that you will also have Sound/Audio working too.   

x2go also easily supports remote printers and shared directories and its session establishment time is probably 1/2 that of NeatX.

Without significant work NeatX does NOT hold a candle to x2go "at this time".

And... x2go is about to get a major update in a few weeks which will add a Web-Portal access to the Server as well.

With that _*you will only need a java enabled Browser*_ to start your desktop sessions on the *remote* x2go server.

---

### Post by kim0 on 2010-11-06
Awesome, thanks Brian for sharing the info

---

### Post by chrisduke on 2011-01-17
Just wanted to add a bit of info for anyone using x2go on Ubuntu and tearing their hair out because they are getting a black screen after login. 

Since Ubuntu 6.10 the default shell was changed to dash (see [here]("https://wiki.ubuntu.com/DashAsBinSh")) but x2go requires bash to in order to work. You need to do the following to switch your setup from dash to bash:

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

Also, check your /etc/ssh/ssh_config and sshd_config files to make sure X11 forwarding is set to yes (X11Forwarding in the former and ForwardX11 in the latter)

Hope it might help someone get going with x2go.

All the best

Chris

---

### Post by kim0 on 2011-01-17
Well thanks for the info, but I didn't really need to do that to get it running!

---

### Post by chrisduke on 2011-01-30
Err, yeah, it also helps to install gnome desktop before you try connecting to a gnome session. Doh!

---

### Post by paoletto on 2011-04-26
So, today, after updating a server to maverick, i found out that neatx sucks on maverick, due to the new metacity.

i updated the client on windows to the latest nxclient version, that seemingly fixes the window decoration bug, but now its so damn slow..

so i also gave x2go a try, i used the packages from this ppa:
[https://launchpad.net/~siretart/+archive/x2go](https://launchpad.net/~siretart/+archive/x2go)

the maintainer recompiled x2goserver (not the -one version) to use sqlite instead of postgresql, so that it is straightforward to use the full server

i am having copy-paste troubles, at the moment.
i found a message on the forum of a user that solved it by installing a newer client version, but i couldnt find it yet

hope it helps

---

### Post by paoletto on 2011-04-26
so, the "upcomming" version of the client fixes that

however i have a strange bug, that i can log in only with one user, while i cant with the others

---

### Post by kim0 on 2011-05-02
Hi, I blogged about running x2go on ec2 at
[http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html](http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html)
you might find that helpful. Thanks

---


---
title: "Setting up plex on Ubuntu server"
date: 2014-02-28
forum: Server Platforms
---

### Post by grier-devon on 2014-02-28
So I have used Plex on Ubuntu before but that was with a GUI. The only thing running 24/7 is my new Ubuntu Server and I would like to run Plex so people in the house can watch videos at anytime. This is the first guide I found
[http://www.thekunit.com/install-plex-server-ubuntu-server/](http://www.thekunit.com/install-plex-server-ubuntu-server/)

Now in that guide there is a guide to setup NFS
[http://www.thekunit.com/cheatsheets/operating-systems/ubuntu/ubuntu-filesystem/](http://www.thekunit.com/cheatsheets/operating-systems/ubuntu/ubuntu-filesystem/)

What is this for and how does it apply to setting up plex?

My next question is how do I though the command line set plex to pull the videos from a certain directory? I know how to do this on a GUI but I would like to run this from the Ubuntu Server I set up.

Thanks for any input.

---

### Post by ted.drain on 2014-02-28
Here are the links I used to install Plex on 12.04.  I'd say don't bother using apt-get - install it manually.  Use ACL's for permissions - they make things much simpler.

General setup: [https://forums.plex.tv/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/](https://forums.plex.tv/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/)
ACL's: [https://forums.plex.tv/index.php/topic/67962-need-usergroup-to-stick-for-new-files/](https://forums.plex.tv/index.php/topic/67962-need-usergroup-to-stick-for-new-files/)
Firewall ports: [https://forums.plex.tv/index.php/topic/33751-problems-with-pms-and-ufw-on-ubuntu/?p=215319](https://forums.plex.tv/index.php/topic/33751-problems-with-pms-and-ufw-on-ubuntu/?p=215319)

Once you have it running, use a web browser to configure everything.

If you have problems, you're better off asking for help on the plex linux forum.

---

### Post by Kelvin_Kang on 2014-03-25
> **grier-devon said:**
> So I have used Plex on Ubuntu before but that was with a GUI. The only thing running 24/7 is my new Ubuntu Server and I would like to run Plex so people in the house can watch videos at anytime. This is the first guide I found
[http://www.thekunit.com/install-plex-server-ubuntu-server/](http://www.thekunit.com/install-plex-server-ubuntu-server/)

Now in that guide there is a guide to setup NFS
[http://www.thekunit.com/cheatsheets/operating-systems/ubuntu/ubuntu-filesystem/](http://www.thekunit.com/cheatsheets/operating-systems/ubuntu/ubuntu-filesystem/)

What is this for and how does it apply to setting up plex?

My next question is how do I though the command line set plex to pull the videos from a certain directory? I know how to do this on a GUI but I would like to run this from the Ubuntu Server I set up.

Thanks for any input.

Hi there, those are actually my blogs entries. You typically do not need to set up NFS for most installs. My media files are stored on my NAS and rather then to port the files from one server to the next, I just retrieve them via NFS. I'll update the entry so that it makes that delineation.

Your second question is hopefully answered in a previous post. The easiest way to set up Plex after you install it is through the Web UI. You just have to to to http://<machine ip>:32400/manage. From there, you can configure the media type that you're looking for. Hope that helps with your questions.

---

### Post by grier-devon on 2014-05-07
Hello, this is has been a long time but I finally got plex running on my Ubuntu Server. The only issue I am running into now is when I try to go and manage plex through my web browser I requires me to sign in and it won't let me. How on the server side to I link my plex service to my plex account?

---

### Post by kosmokramer314 on 2014-05-07
these are all questions you should be asking on the PLEX forums.  If you are having this much difficulty, it would be best to re-read the documentation and start over.  Head over to google and the plex forums.  It's very straightforward, and if you don't plan on opening the connection to the outside world,  you don't even need authentication for your local network

---


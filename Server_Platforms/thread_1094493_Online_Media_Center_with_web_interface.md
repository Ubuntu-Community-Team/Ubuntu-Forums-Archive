---
title: "Online Media Center with web interface"
date: 2009-03-12
forum: Server Platforms
---

### Post by nbitting on 2009-03-12
Okay, so I recently purchased a T105 Server.  I've installed Ubuntu 8.10 Server Edition.  Now, the main purpose for my server will be for file storage, both locally and remotely.  

I have a lot of movies and music I'm going to migrate onto the server from my laptop.  Most of my family lives out of state and would love to be able to access all of my media.  What I was thinking was to build a website to stream movies and music (including playlists for music) from the server.  

[B]
Here are some general ideas I'd want for requirements:[/B]

I'd want to create usernames and passwords for each of my family members who want access.  It doesn't have to be pretty, just want it to be able to stream using a video player with full screen option for video.  Also would like a music player with ability to create custom playlists from my library.  Ability for approved users to upload music files remotely.

[B]
Now for the ask:[/B]

Is there already software out there designed to accomplish what I'm looking for?  Secondly, I'm new to Ubuntu Server, so I'd need help setting up the web server.

[B]
Here's what I know about setting up a web server from reading ubuntu forums and online tutorials:[/B]

Create static ip address for server, use port forwarding (port 80) options in my wireless router, set up dyndns.com type service for dynamic dns, install apache2, install php/mysql if needed...

Any help or comments would be greatly appreciated.


Thanks!

nb

---

### Post by eatberrys on 2009-03-12
well use apache for web server ->[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

DO you know html/php/sql ?

I am willing to help with what i can but its easyer for me to help over aim so if you would like fell free to send me an IM

---

### Post by cje on 2009-03-12
Maybe it's best to start installing the web server then. This guide should cover your needs:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Good luck!

---

### Post by volkswagner on 2009-03-12
Check out [Jinzora]("http://en.jinzora.com/features").  It is pretty cool.  You can set it up for users require a login/password.

I believe it supports all your requests.

It is fairly easy to setup once you have apache and virtual hosts working.

I have not used it for video but it is supported.

Feel free to check it out.

If you do choose to install it, one item to pay attention to.  If you want required login, don't allow Nobody as a user, it seems difficult to undo.

EDIT: It even allows users to download, or not, you setup permissions.

---

### Post by nbitting on 2009-03-12
Hello everyone...thanks for the replies.  I do know sql and html to a good extent.  I know several programming languages, including object-oriented languages such as C#.  I've already installed php5, apache2, and mysql...FYI.  I already set up the dynDNS.com service and that all works.  I've created test html and php pages and they all work fine.  Now I'm ready to move on to the next step.

Thanks.

nb

---

### Post by nbitting on 2009-03-12
Jinzora seems to be exactly what I'm looking for!  Thanks so much...now for the next question.  How to get jinzora up and running...any good tutorials to install jinzora on the server?

---

### Post by nbitting on 2009-03-13
Okay, so I tried out jinzora and everything was great, except the embedded flvplayer didn't work very well at all.  There were just too many bugs and fullscreen would not work no matter how hard I tried.  I did everything the people on the forums stated, but nothing worked.  Jinzora was actually very similar to what I was looking for, just want to be able to stream my .avi movie files in a flash video player.  HELP!!!

Thanks.

nb

---


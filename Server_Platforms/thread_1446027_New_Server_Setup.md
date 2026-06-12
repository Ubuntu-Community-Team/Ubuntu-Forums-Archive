---
title: "New Server Setup"
date: 2010-04-03
forum: Server Platforms
---

### Post by keljaden on 2010-04-03
I have a Dell at home I want to turn into a small file server
specs
CPU: P4 2.0ghz
RAM: 768MB DDR (idk clock speed sorry)
HDD: ~250 gigs
GPU: ATI Radeon 9700 pro

my goal with this is to be able to access the files from both my Windows and Linux Boxes from wherever I am in a secure method. (hence if I am at my friends place and I want to access my server to pull up images or documents and be able to file transfer)
I have never set up a file server before so I am completely lost on all security protocol and file settings (I am also not a terminal guru), I am used to having a GUI.  The server will be connected via wireless (WPA2 AES) to my Netgear router.

Any help, advice, or links to guides would be extremely welcomed.  I am very new to servers, but I have run Ubuntu/Mint/Fedora for about 2 years now.  I am just starting networking classes in college right now so I know a bit and I am very eager to learn more.

Thanks in advance.

---

### Post by jfmanamtr on 2010-04-03
Awesome. Well, a good start for file sharing is going to be Samba. I use that for all the Windows & Linux boxes that I have in my home. The guide on the Ubuntu home site for setting up different things is pretty good. The section for Samba will be worth your checking out ([link]("https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html")). 

For over the internet, you have a bunch of options. You can use scp over ssh or setup a site & use a PHP file manager. I use the latter & have no issues (though I did run into file permissions issues at first). 

You may want to think about wiring your server into your router. Wireless is inherently slower than wired. I think it will depend on what you are going to use the server for, but it is something to keep in mind. Hope this helps. If you have any more questions feel free to ask.

~John

---

### Post by Datamac on 2010-04-03
I am in  almost the same situation as you except I just got two up and running.  I used Ubuntu 9.04 Server Ed I386.  From the iso file I downloaded through Windows and burned, I was able to do a clean boot, follow the on-screen prompts and have a solid server.  You'll be prompted during the install to include Samba file server as one of the options.  After that, you just need to install a desktop for human life to be easy.

---

### Post by keljaden on 2010-04-03
my up speed (like 150kbps) is not faster than my wifi speed (108mbps) so I am not too worried about having it wired.  What security wise, I need everything to be nice and safe.  I know nothing is 100% perfect, but I would like to get close if possible. and thanks for the replies.  I am getting everything planned out as I am wait for 10.04 to be released before I install as it is the LTS.

---

### Post by KB1JWQ on 2010-04-03
If you're concerned about security first and foremost, I'd advise against having it done via wireless.

Reliability over a wireless medium is a bit challenging in some environments.

---

### Post by HermanAB on 2010-04-04
Over the internet?  Use SSH.  There is no substitute.  Unless you are a masochist and want your machine hacked of course.
;)

---

### Post by guessswh0 on 2010-04-04
sftp will do it fine over internet.

---


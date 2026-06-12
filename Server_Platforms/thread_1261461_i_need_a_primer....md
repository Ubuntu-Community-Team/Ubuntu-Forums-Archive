---
title: "i need a primer..."
date: 2009-09-08
forum: Server Platforms
---

### Post by zander1013 on 2009-09-08
hi,

i am a noob setting up servers. i am using ubuntu 9.04. i seem to be able to set up and install a lamp okay. but then i don't know what to do with it.:confused:

i can login and shut it down but that is about all i can think to do with.

can someone recommend a primer document or suggest a similar small project (with a pointer to instructions) for me to get started with?

perhaps a file server or something like that. or perhaps something that might be useful for my wlan?

you can see what i got at [http://alonzofretwell.com](http://alonzofretwell.com) the system is configured as scenario 4 under Network Setup Options on this page [http://download.excito.net/web/BubbaTwo/UM-ENG/index.html#](http://download.excito.net/web/BubbaTwo/UM-ENG/index.html#) the server will be "COMPUTER 1" in the diagram for scenario 4.

some things i would like to have around include wlan backup server, a test server where i can experiment with cms social media open source prior to actually deploying it on my excito server, a file server, ect...

please advise.

thank you for any help.:neutral:

zander

---

### Post by SoftwareExplorer on 2009-09-08
Well, if your server has a screen, you can install a GUI if that's what you are more comfortable with. 
sudo apt-get install ubuntu-desktop  <--like this

Though, to answer your question:

```
top                                       Monitor system useage of various processes
cd                                        change directory. '..' is what it calls the directory above
nano (filename)                           edit text files (when it lists commands ^ means control)
ls                                        list the files in the current directory
ls -a                                     same as before with hidden files
ls -l                                     same as ls but with permissions
sudo apt-get install (package name)       install a package
sudo apt-get remove  (package name)       remove a package
sudo /etc/init.d/(service name) start     start a service
sudo /etc/init.d/(service name) stop      stop a service
ssh user@computername                     login over the network into a remote computer
file (filename)                           find out what format a file is
```

that should get you started

---

### Post by zander1013 on 2009-09-08
@SoftwareExplorer...

ty that looks like a great start. i was wondering if i should install a gui or not. that is what i am used to but the command line is no problem.

i will follow your suggestion.

-zander

---

### Post by SoftwareExplorer on 2009-09-08
> **zander1013 said:**
> @SoftwareExplorer...

ty that looks like a great start. i was wondering if i should install a gui or not. that is what i am used to but the command line is no problem.

i will follow your suggestion.

-zander
First of all, sorry my table of commands didn't turn out so well, I had then separated by spaces to line everything up nice and clear and I guess html didn't like it.
As far as the GUI, it is up to you. I have heard people argue that it will hold you back in your learning about linux. Others say why make it harder than it really needs? You can always get to a command line to learn the terminal easily enough from the GUI.
Edit: just fixed my previous post.

---


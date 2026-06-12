---
title: "Cannot start gnome gui"
date: 2011-05-13
forum: Server Platforms
---

### Post by rman51 on 2011-05-13
I need help with starting the gnome GUI. 

Environment is Ubuntu 10.04.2 LTS, server edition.

I have installed the ubuntu-desktop package with apt-get, which reported a successful installation. I also installed firefox the same way.

When I run the command "firefox", I get this response: "Error: no display specified". Thinking I might need to run it from the GUI, I tried "startx" (command I found elsewhere on this forum). Response was: "Fatal server error:\nServer is already active for display 0".

Why run GUI and/or Firefox on a server? The second instruction on the Symfony 2.0 install procedure is to "check the configuration" by accessing [http://localhost/Symfony/web/config.php](http://localhost/Symfony/web/config.php). 

I first tried that from my Win-7 workstation, substituting the server's IP address for localhost in the URL above. The response from that is "This script is only accessible from localhost."

SO ... I'm trying to run firefox directly on the server, so that I can access the localhost version of that URL, to follow Symfony's instructions.

Any suggestions how I can get FF (or any other browser) running on the server? Thanks!!

---

### Post by arrrghhh on 2011-05-13
Don't install the ubuntu-desktop package on a server...

Either install the actual Ubuntu Desktop, or at the very least forward X over SSH.  There's no need for a full blown DE on a server, if you feel you need one Ubuntu Desktop includes one ;).

---

### Post by rman51 on 2011-05-13
"Don't install the ubuntu-desktop package on a server ... "

Already done. Is there a procedure to uninstall it?

"Either install the actual Ubuntu Desktop ..."

Choice of OS is not mine. Job is to take what I've been given to work with (server edition 10.04.2), and get apache, mysql, and Symfony 2 running on it, and build a new app using Symfony.

"forward X over SSH."

Sounds like a good plan. Problem is, I have no idea what that means. How would I do that? BTW, I'm accessing this server from a Win-7 workstation using Putty, if that helps.

"There's no need for a full blown DE on a server ..."
I totally agree! I'm just trying to follow the Symfony 2 installation instructions: [http://symfony.com/doc/current/quick_tour/the_big_picture.html](http://symfony.com/doc/current/quick_tour/the_big_picture.html)

I tried to run this from the browser on my Win-7 workstation. All I got back was a notice that the tool will ONLY run on localhost.

SO ... given that I'm stuck with the server edition OS, how can I follow their instruction to run their visual configuration tester in a browser, which MUST be run from localhost?

TIA!!!

---

### Post by arrrghhh on 2011-05-13
Well you can run a cli-only browser, or install a browser and forward it over SSH.

If you're client is Windows-based, you'll need Xmming or something similar to forward the session properly.  There are X forward settings within putty as well.

So you can run Firefox on the server, but forward the X traffic to an X server running locally on your Windows box.  That would be the way I would recommend.  

As for installing ubuntu-desktop... unless you used aptitude, I think you're SOL.  I've seen some guides on how to revert, but it's never pretty...

---


---
title: "Terminal is currently not installed"
date: 2014-08-10
forum: Server Platforms
---

### Post by filipo2 on 2014-08-10
Hi I have just installed 12.04.5 server as I can't get 14.04 to install. (See my post below). The shortcut CTRL+ALT+T did nothing, so I typed terminal at the prompt. I was told terminal was currently not installed and I should try sudo apt-get install rsplib-tools.

The system returned with 'rsplib-tools' has no installation candidate

What can I do now?

---

### Post by Lars Noodén on 2014-08-10
The server edition has no graphical interface but you can do anything (nongraphical) via the console that you could do via the terminal.  You have several consoles to choose from, press ctrl-alt-f1, ctrl-alt-f2, and so on to switch between them.  Or you can install a terminal multiplexer like tmux (or screen) and have multiple sessions within the same console.  

What do you want to do with your server?

---

### Post by filipo2 on 2014-08-10
Thanks for that. I'm going to use it as a development server for php code.

---

### Post by tgalati4 on 2014-08-10
```
apt-cache search terminal
``` 

Just a few to choose from.  Control-Alt-T brings up the default terminal in a graphical environment--something not normally installed in the server version.

---

### Post by filipo2 on 2014-08-10
Thank you. That's all useful

---

### Post by Lars Noodén on 2014-08-10
Do you have a second machine to connect from using SSH?  Or will you need to add a graphical desktop to the server?  You can do the former by installing the package openssh-server.  And you can do the latter by installing ubuntu-desktop, followed by an editor or IDE.  

Regardless, if you are going to do web development with PHP then you need to choose a web server (Apache2 or nginx) and then add php5

---

### Post by filipo2 on 2014-08-10
Yes, I have a second machine and am going to set up SSH. Apache is running and, hopefully PHP also.

---

### Post by Lars Noodén on 2014-08-10
Ok.  If you have a second machine you can do all your work through SSH.  If you want graphical tools, you can use the ones on your local machine and then upload the results or else use [SSHFS](http://manpages.ubuntu.com/manpages/trusty/en/man1/sshfs.1.html) to mount the remote directories and work on the files directly.  SSHFS connects, using SFTP behind the scenes, to allow you to mount a remote account.

If you have an empty folder called 'web' to use as a mount point and the server at 192.168.0.100,

```

sshfs filipo2@192.168.0.100:/var/www/ /home/filipo2/web/

```

Of course, that's after you have /var/www set up on the server.

---

### Post by filipo2 on 2014-08-10
Thanks, Lars, once again that was useful information. I now realise that I was in a terminal window all the time:oops:. But I now understand how to open multiple windows. Two follow up queries. The article I am working through shows a menu at the bottom of the screen - how do I get that? Secondly, I've installed the aptitude documentation - how do I access it?
Many thanks

---

### Post by Lars Noodén on 2014-08-10
Can you post the link to the article?  It helps to see the screenshot.  


The aptitude documentation can be found by pointing your browser at this file:
/usr/share/doc/aptitude/html/en/index.html

Substitute the /en/ for the correct language if you are using another langage.

---

### Post by filipo2 on 2014-08-10
Thanks, Lars, once again that was useful information. I now realise that I was in a terminal window all the time:oops:. But I now understand how to open multiple windows. Two follow up queries. The article I am working through shows a menu at the bottom of the screen - how do I get that? Secondly, I've installed the aptitude documentation - how do I access it?
Many thanks

---

### Post by filipo2 on 2014-08-10
I don't think so. It was an article in Web Designer Issue 208. The screenshot shows a menu along the bottom with options such as Get Help, WriteOut, Read File, Prev Page etc

---

### Post by Lars Noodén on 2014-08-10
Ok.  It is probably not gnome-terminal like Ubuntu is using.  I don't suppose they provide info about which one they are using?  Does it say which terminal or disto is used?

KDE's Konsole used to have a lot of options, I suppose it still does, but I have not used it in a very long time.  It would also pull in a lot of dependencies if you installed it in regular Ubuntu since it uses Qt.

---

### Post by filipo2 on 2014-08-10
Unfortunately not, but looking at the next section where we secure Apache it looks like GNU nano 2.2.6.

---

### Post by bab1 on 2014-08-10
> **filipo2 said:**
> I don't think so. It was an article in Web Designer Issue 208. The screenshot shows a menu along the bottom with options such as Get Help, WriteOut, Read File, Prev Page etc
Yes, that sure  looks like the the user has opened the text editor **nano ** in the terminal.  From an open terminal issue this command to see it```
nano
```

[COLOR="#0000FF"]Edit:  The bottom should look like this[/COLOR]
```
^G Get Help     ^O WriteOut     ^R Read File    ^Y Prev Page    ^K Cut Text     ^C Cur Pos
^X Exit         ^J Justify      ^W Where Is     ^V Next Page    ^U UnCut Text   ^T To Spell
```

---

### Post by tgalati4 on 2014-08-10
If you want multiple text terminals then look into *screen*.  You can have documentation open in one screen and code in another.

---

### Post by filipo2 on 2014-08-10
Thanks everyone. You have all been extremely helpful.

---


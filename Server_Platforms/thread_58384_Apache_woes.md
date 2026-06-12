---
title: "Apache woes"
date: 2005-08-19
forum: Server Platforms
---

### Post by herrpoon on 2005-08-19
Hi there, I've installed LAMP on my ubuntu machine following the ubunutu LAMP guide but am having a few problems.  When i try and start the server, I get the following error message:

"(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs"

I've tried looking around for the answer, but I still can sort the problem out, any help would be very much appreciated, thanks,

Herrpoon

---

### Post by Velox Letum on 2005-08-19
*could not bind to address [::]:80*

It appears its attempting to bind to an empty IP address, probably a virtual host (been so long since I've touched the Apache config files...). Take a look around the apache config, especially the virtual host blocks.

---

### Post by herrpoon on 2005-08-20
right, will do, do you know if it's necessary to froward any ports to get it working?

---

### Post by Velox Letum on 2005-08-20
Port forwarding may be required to access it externally in the future, however it doesn't affect the ability to bind your IP address. If you are on an internal network as I am (IP address: 192.168.0.2) then I'd bind it to that ip address, then in my router (if I wished to enable external access) I'd portforward my external IP address port 80 to 192.168.0.2 port 80.

---

### Post by GrumpySimon on 2005-08-20
[QUOTE=Velox Letum]Port forwarding may be required to access it externally in the future, however it doesn't affect the ability to bind your IP address. If you are on an internal network as I am (IP address: 192.168.0.2) then I'd bind it to that ip address, then in my router (if I wished to enable external access) I'd portforward my external IP address port 80 to 192.168.0.2 port 80.[/QUOTE]
 I think it's more likely that you've already got something running on port 80. Double check that you don't have anything listening. 

Try this command:
```

netstat -l -n | grep :::80

```

If you see something like this:
```

tcp6       0      0 :::80                   :::*                    LISTEN

```

Then you'll need to work out what's sitting on 80.

--Simon

---

### Post by Velox Letum on 2005-08-20
Thats also possible. If nothing comes up with the netstat, then its your Apache config.

---

### Post by herrpoon on 2005-08-21
thanks everybody, I appreciate your input, going to try those things now.

---

### Post by herrpoon on 2005-08-21
Well ive tried those things, and still having the same problems :/  I think I'll reinstall apache, as I don't see what else can be done.

Thanks for all your help.

---

### Post by LordHunter317 on 2005-08-21
Apache is started automatically, why are you trying to start it manually?

---

### Post by herrpoon on 2005-08-21
[QUOTE=LordHunter317]Apache is started automatically, why are you trying to start it manually?[/QUOTE]

I was following this guide:[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29) which seemed to me, after installing apache it needed to be started, i.e

```
$ sudo /usr/sbin/apache2ctl start
```

Since then though, I have restarted/stopped apache many times so it can't be that.

I may not have noticed or it's just started to appear, it says "httpd not running."

I do remember reading somewhere, something about the file httpd.conf but I can't find it anymore so at am a loss  ](*,)

---

### Post by LordHunter317 on 2005-08-21
Well, unless you're sure it's dead, I'm not sure you ever really killed the original apache.

What does 'ps ax | grep apache' say?  If it returns anything but 'grep apache', you haven't done a valid test.  Stop all those processes (using kill if necssary), then try to start apache with:```
sudo /etc/init.d/apache2 start
```  Tell us what happens then.

---

### Post by herrpoon on 2005-08-22
Did what you said, and there were 6 or 7 apache processes running so obviously I hadn't quite killed it!  And when I start it now, it doesn't come up with that error, thanks for your help all!

---

### Post by shutupchuck on 2005-08-29
I followed all of the steps that you generous people are giving but it still says that my httpd isn't running. 

I altered my ports.conf so that it says **listen 8080**

i ran the **ps ax | grep apache** and it showed me 4 services that weren't grep apache so i ran **sudo kill 7635** because that was the number of the first thing on the list then i ran **ps ax | grep apache** again and it said that apache grep was the only thing running.

so I tried to run **apache2ctl restart** and it said **httpd not running, trying to start**

then when i typed **ps ax | grep apache** again it came back with a whole new list of things running.

i dont know what to do, please help.

---


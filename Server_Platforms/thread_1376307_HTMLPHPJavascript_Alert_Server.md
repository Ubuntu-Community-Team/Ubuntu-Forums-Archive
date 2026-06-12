---
title: "HTML/PHP/Javascript Alert Server?"
date: 2010-01-09
forum: Server Platforms
---

### Post by Anatashinu on 2010-01-09
Hi, I have been running a server off of my home computer for about 2 months using LAMP server, and I was wondering if there was a way to alert me when somebody submits a specific form, preferably by a pop-up box on my screen.
 Thanks in advanced! -Anatashinu

---

### Post by BkkBonanza on 2010-01-09
The form can be processed by a php script that could trigger various types of communication to you. It depends what you want to happen.

Php could send an email, send an sms message to your phone, send a skype message etc.

As far as a pop up on your desktop you'd have to have something waiting for or checking for some indicator so it can pop up. It's possible to do this but it kind of depends on how you would want to do it. I mean you could make a simple script that polls your web site for a status value and pops up a message if you like. Either bash or python would be able to do this.

---

### Post by Anatashinu on 2010-01-09
I've tried email multiple ways, I'm sure it's possible, but I would rather not try it any more.  I don't know shell more than some basic commands, but I know python pretty well.  I'm not sure exactly how I would accomplish this, though.  If you conuld explain what I would need to do a bit more inn depth, I would be greatly appreciative.  Thanks for the quick reply, by the way.

---

### Post by BkkBonanza on 2010-01-09
Well there's several ways. The simplest is to have a python script that polls the server. A little nicer would be to have a connection that can receive msgs as they occur but that requires either a port open or using ssh to maintain a tunnel. Either way would work but the tunnel is more secure and easier to configure. If you don't mind the message being up to a minute late then the polling method is easy.

Easy way - polling:
Your python script can either have a timer in it and stay running (daemon), or it can be called by cron every minute and exit after. Your choice. Once every minute it just does a GET on a special page on your server, say something like "chkmsg.php". Your form script just needs to set a value that chkmsg.php returns when called. So the form script can take the form info and put it in a file. Then chkmsg.php simply returns the file contents if it exists and removes the file, or if no file then returns nothing. Your python script gets the data if not empty it pops up the window showing you the content.

Fancy way - ssh tunnel:
You open a tunnel to your server using ssh. Something like,

ssh user@server -L 4040:localhost:4040 -N

(python can do this using an exec call, you can choose whatever port you like, I'm using 4040 as an example)

This tunnel means you have a secure connection open between your local desktop and the server. So your python script needs to open a socket listening on port 4040 and wait for any data coming on it and when it gets something it pops up a window to tell you. You can define your own protocol or just use url encoded form data - whatever suits you. On the server your php script gets the form data and it opens a socket on port 4040 and writes the form data to it using whatever protocol you made up. Could just be urlencoded format for simplicity eg. name=bob&email=blah@blah.com&comment=my+big+comment. If it can't open a socket on 4040 then it appends the data to a file so that later it can try again. 

The nice thing about the tunnel method is the popup is instant and it doesn't have to poll the server so won't show up in the apache logs every minute. The downside is you probably need to learn to use the socket functions - but that's easier then it sounds. Here's a brief intro page I found,

[http://www.amk.ca/python/howto/sockets/](http://www.amk.ca/python/howto/sockets/)

Note that your socket would be listening on "localhost:4040", not on the server because the tunnel handles that transport for you. Same on the php script end, it also opens and writes to "localhost:4040".

If you wanted help writing a python script for the tunnel method I can help out, just because it's interesting.

---

### Post by Anatashinu on 2010-01-09
Hmm... okay, I se what you're saying. but by the way, the server is my desktop so there's no need for SSH.  I'm not exactly sure how the Python script would work though. What I am aiming for though is not a script to check for results, though that would work. I was hoping that there would be a way to alert me on the submitting of the form. For example:
<form name="testform" method="post">
<input type="text" name="testinput" />
<input type="submit" value="submit" />
</form>

So the ways I could imagine doing something like this would be
  A. Use a Javascript onSubmit function when testform is submitted.
OR
  B. Use something like <form name="testform" action=*SOMEPHPCODE* method="post">.

Either way though, I'm still clueless on how I would make an alert box apear.  I was thinking possibly the Javascript alert() function, but I remembered that only appears Client-Side.

Thanks again! -Anatashinu

---

### Post by BkkBonanza on 2010-01-09
Whoa. I didn't know your server is also your desktop. That makes all the difference.
And makes it trivial.
Just make a python script that is submitted to by the form and which throws up a popup message. Done.

Python can be used as a cgi script. Google and read up on that.

---

### Post by Anatashinu on 2010-01-09
Haha wow, I guess I forgot to mention that (>.<) I don't know how I didn't think of that, I'll try it when I get back home.  Oh, now I'm extremely confused, I can't figure out how to use a cgi script. It just says permission denied when I try to run a script in /var/www/cgi-bin O.o This is so confusing!

---

### Post by BkkBonanza on 2010-01-09
The script needs to have read/exec permission for the user that apache runs as.

---

### Post by Anatashinu on 2010-01-09
It does, it has read/exec permissions, and the folder has read permissions, but it says permission denied for the folder and not found for the file (and no, I'm not misspelling it)

---

### Post by BkkBonanza on 2010-01-10
Can you provide exact details, output. 

ls -lsa /var/www/cgi-bin  (or your cgi-bin folder)

ps aux | grep httpd  (show info on apache processes)

Your python script starts with (check correct path to python),
#!/usr/bin/python

---

### Post by BkkBonanza on 2010-01-10
If you haven't got this to work yet here's another way you may want to try. It's a very small bash script I came up with that will do what you want.

Just make a web form page that will store the data you want into a file "msg.dat". Use any language you like, php is very easy on LAMP setups.

This bash script will monitor that file and popup a message for you, and then log the message into the msg.log file. This is just a simple example and you can modify to suit of course.

Create a file "formpop", and chmod +x the file,
```
#!/bin/bash

WINDOWID=""

while [ 1 ]
do
  if [ -f "msg.dat" ]; then
    zenity --info --title "Web Form Message" --text "`cat msg.dat`"
    cat msg.dat >> msg.log
    rm msg.dat
  fi
  sleep 5
done

```

Once you have this script saved and chmod'd you need to run it like this,

formpop & disown

This causes it to run and be detached form the console. If you add it to rc.local for starting on boot then just start it as 

formpop&

The & symbol causes it to background itself and run as a daemon, monitoring this file looking for a message. It checks every 5 seconds.

If you want to kill this process, then run "pkill -9 formpop".

This is pretty much the simplest way I can think to do this.

---

### Post by Anatashinu on 2010-01-11
Ok thanks I'll try that, but I would like to use python rather than bash, mostly because I would like to learn how even if it does nothing better than bash would.  Anyways, here is the output to the things you wanted:  

```
oliver@oliver-desktop:~$ ls -lsa /var/www/cgi-bin
total 12
4 drwxrwxrwx  2 oliver oliver 4096 2010-01-11 18:03 .
4 drwxrwxrwx 17 root   oliver 4096 2010-01-11 17:57 ..
4 -rw-rw-rw-  1 oliver oliver  146 2010-01-11 18:03 pytest.cgi
0 -rw-rw-rw-  1 oliver oliver    0 2010-01-11 18:01 pytest.cgi~

oliver@oliver-desktop:~$ ps aux | grep httpd
oliver    2206  0.0  1.2  24660 12544 ?        S    Jan09   0:49 x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
oliver   26948  0.0  0.0   3036   796 pts/2    R+   18:04   0:00 grep --color=auto httpd
```

And I would do something like this once it works, correct?:  <form action="cgi-bin/pytest.cgi" method="POST" name="form">

Also, here is the apache error log:  
```

oliver@oliver-desktop:~$ tail -f  /var/log/apache2/error.log
[Sun Jan 10 08:02:34 2010] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Jan 11 02:23:23 2010] [error] [client 204.236.172.230] script not found or unable to stat: /usr/lib/cgi-bin/textenv.pl
[Mon Jan 11 03:03:42 2010] [error] [client 174.129.94.221] File does not exist: /var/www/intl
[Mon Jan 11 18:03:14 2010] [error] [client ::1] attempt to invoke directory as script: /usr/lib/cgi-bin/, referer: http://localhost/
[Mon Jan 11 18:03:42 2010] [error] [client ::1] attempt to invoke directory as script: /usr/lib/cgi-bin/, referer: http://localhost/
[Mon Jan 11 18:04:17 2010] [error] [client ::1] script not found or unable to stat: /usr/lib/cgi-bin/pytest.cgi
[Mon Jan 11 18:04:27 2010] [error] [client ::1] script not found or unable to stat: /usr/lib/cgi-bin/pytest.cgi
[Mon Jan 11 18:12:46 2010] [error] [client ::1] attempt to invoke directory as script: /usr/lib/cgi-bin/

```

---

### Post by BkkBonanza on 2010-01-11
Your python script needs to have exec permissions or apache can't run it. Also it looks like from the log it tried but the path is wrong. Apache is trying at /usr/lib/cgi-bin not /var/www/cgi-bin. The cgi-bin path is set in the apache config.

---

### Post by Anatashinu on 2010-01-12
Okay so I realized i had been editing the file in sites-availible (>.<) So i fixed the problem and python scripts work no problem. Now, I just need to figure out how I would get the script to run on my computer rather than theirs.

---

### Post by Anatashinu on 2010-01-18
bump:popcorn:

---


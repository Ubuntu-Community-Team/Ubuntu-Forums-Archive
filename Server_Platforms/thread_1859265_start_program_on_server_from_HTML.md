---
title: "start program on server from HTML"
date: 2011-10-13
forum: Server Platforms
---

### Post by srs008 on 2011-10-13
hi, i'll keep this short, i'd like to Run a Launcher on my "server" computer from a HTML webpage(a button or link? quick script), the idea is for a game server, i can leave my net running and my mates can start the server remotely, I REALLY do not want to trust any of them with actual remote access.

is there anything that can do this?

ubuntu 11.04

thanks for your time.

---

### Post by Jonathan L on 2011-10-13
> **srs008 said:**
> hi, i'll keep this short, i'd like to Run a Launcher on my "server" computer from a HTML webpage(a button or link? quick script), the idea is for a game server, i can leave my net running and my mates can start the server remotely, I REALLY do not want to trust any of them with actual remote access.

is there anything that can do this?

ubuntu 11.04

thanks for your time.

Hi ...

If you're leaving the computer running, why don't you leave the software running too?

But to answer your question, write a shell script to start and stop the software and put it in your cgi-bin directory.  Then a little web page with a form to call the scripts.

Hope that gets you started.

Kind regards
Jonathan

---

### Post by brighty22 on 2011-10-13
If you know basic PHP you could use its [exec()]("http://php.net/manual/en/function.exec.php") function. It would be pretty much trivial to implement with a form on a webpage.

---

### Post by srs008 on 2011-10-16
thanks guys, i'll give it a go in a few hours, the reason it's not running all the time is i plan on running a few game servers, by allowing a remote start, i can put a script/plugin into the game to close off after say 20-30 minutes inactivity. 
thanks again

---

### Post by Jonathan L on 2011-10-16
> **srs008 said:**
> thanks guys, i'll give it a go in a few hours, the reason it's not running all the time is i plan on running a few game servers, by allowing a remote start, i can put a script/plugin into the game to close off after say 20-30 minutes inactivity. 
thanks again

Hi

Good reasons for not leaving it running.  I'd advise separating out the web problem from the game starting and managing.

Here's a trivial web action:
```
<html>
<form method=get action=/cgi-bin/doit.sh>
<input type=submit value=doit>
</form>
</html>
```This is in /usr/lib/cgi-bin/doit.sh
```
#!/bin/sh

echo 'Content-Type: text/plain'
echo ''
date
```You may find you have some permissions issues or the problem with multiple processes running your game.  One way round that is use crontab to start the game, if required, every minute, based on the contents of a request file in /var

Hope those ideas help.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2011-10-17
Remember that the script will be running with the web server's identity and privileges, not root's.  So you need to make sure that starting the server as user "www-data" (in Ubuntu) will successfully launch the application you need.

---


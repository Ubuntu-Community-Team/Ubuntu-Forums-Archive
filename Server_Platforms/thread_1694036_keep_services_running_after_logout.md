---
title: "keep services running after logout"
date: 2011-02-23
forum: Server Platforms
---

### Post by jim001 on 2011-02-23
I am starting apache web server manually due to password,  when I login. 
I need to logout and still keep the service running.

Currently I need to stay logged in in order for web server to keep running.

How can I make this service running even if I log out.

Since I am using server, I don't have GUI option. Also I need to start service manually.

Please advise about the solution.

Thanks

---

### Post by Vegan on 2011-02-23
Apache should be running as a service all the time.

If you have changed it, you will need to start over and install Ubuntu fresh and install LAMP and not mess with it again

if you have questions, ask here as there are lots of competent help

---

### Post by SeijiSensei on 2011-02-24
I think he has a server with an SSL certificate and an encrypted private key.  In that situation you need to enter the pass-phrase to start Apache.

I'd suggest [decrypting the key]("http://www.madboa.com/geek/openssl/#key-removepass") and eliminating the password prompt.

---

### Post by Vegan on 2011-02-24
I found no reason to encrypt keys. The web client cannot get to them so they are safe.

If you use a 32 symbol alpha numeric password to log-on than brute force is useless as the key range exceeds the number of protons in the universe.

---

### Post by hkphooey on 2011-02-25
I'm guessing the fact you have to enter the password is the thing that's stopping you from running the apache server all the time, but in case its not, then get familiar with runlevels. There are two tools which will allow you to pick which services start automatically: chkconfig and sysv-rc-conf. You'll need to make sure that apache is starting on level 3, 4 and 5. 

If that's not the problem then there is another option you might like to consider. Using the program screen you can run commands which will continue to run when you're logged out. eg 
```
sudo apt-get install screen  # if you don't have it already
apache-command
<CTRL> A D -- this disconnects your screen session
exit
```
Then to rejoin the screen session, login and do. 
```
screen -r 
```

Does this help? There's also a "screen on steroids" called byobu which I think ships with Ubuntu, but I don't know much about this.

---


---
title: "I installed the Server 6.10 LTS trying to ssh..."
date: 2007-08-31
forum: Server Platforms
---

### Post by aten on 2007-08-31
I have installed the Server 6.10 LTS 
I was told to run this for SSH and apache:
sudo aptitude install openssh-server apache2'

Now what to i do?

i need to connect via ssh through my laptop (os 10.4) and another desktop (windows XP)
and later over the internet from school.

Help?
I really want to learn NON- GUI i have little GUI Based Ubuntu Knowledge...
Thanks!

---

### Post by HermanAB on 2007-08-31
First test SSH on the server machine itself:
$ ssh username@localhost

then hook up the laptop and server to the same switch and log in from the laptop:
$ ssh [email]username@ip.add.re.ss[/email]

Finally ensure that the server is visible through your firewall/router - forward port 22 to the server on the router and then ssh from the laptop to the public internet address of the router.

Cheers,

H.

---

### Post by bodhi.zazen on 2007-08-31
See if these links help :

 [http://www.suso.org/docs/shell/ssh.sdf](http://www.suso.org/docs/shell/ssh.sdf)

	Ubuntu geek how-to : [http://www.ubuntugeek.com/securely-administer-your-ubuntu-server-remotely.html](http://www.ubuntugeek.com/securely-administer-your-ubuntu-server-remotely.html)

You might also want to secure your connection :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

See also denyhosts

---

### Post by aten on 2007-08-31
x

---

### Post by Brazen on 2007-08-31
Why didn't you just reply to Nothinman in your other thread?

Seriously, go check [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html) .  The documentation there is very noob-friendly.

---

### Post by kumara on 2007-08-31
I tried this and it worked for me

1. Windows machine 
    - Download and install WinSCP

2. Linux machine
   - Download and install SSH
   - Run SSH sudo /etc/init.d/ssh start or restart
   - type ifconfig to get the ipaddress of your linux box

3. On your Windows machine
  - double click and run WinSCP
  - type in your ipaddress, linux machine userid and password.

You should be able to see the Linux machine directory from your Windows box.

I hope this helps.

Kumara

---

### Post by kumara on 2007-08-31
I forgot to mention...I disabled the firewall on my Windows box. Besides I tried these on machines connected on the same router at home.

Kumara

---


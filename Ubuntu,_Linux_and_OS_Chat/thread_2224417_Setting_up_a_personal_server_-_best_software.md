---
title: "Setting up a personal server - best software"
date: 2014-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by dult on 2014-05-16
Hello everyone,

I believe I'm not posting this in the right forum but I'll give it a shot...

For 1 year now I've been using linux (I still use windows at work due to company policies), and I've been really enjoying it. It's really easy to set a lamp server to test a production site.

I've been searching for cpanel alternatives, mainly to set a web-server in order to have some personal websites, that will be acessed mostly by IP - even if dynamic.

I've searched webmin, zpanel, open panel, floxor, etc... but all of them seem either:
A) To big and complex for my needs;
B) Out-date, with no recent updates, abandoned;
C) Undocumented.

I've tried to find tutorials on how to set up all the services I need but it seems to change with each ubuntu version, and ubuntu 14 is too recent.

I gave up managing DNS and server security because I didn't studied network engineering.

So, in a nutshell, I want a personal server where I can:
Have basic security;
Manage FTP accounts;
Manage Mysql.

If I were to learn SSH.. I could install a lamp server, phpmyadmin, ufw and an ftp manager to manage one virtual host (there won't be any private files on the server, only work files and stuff like that).

Can someone give me a suggestion on the best/easiest way to achieve this personal server? I don't want to have a professional hosting, just a personal one, as a hobby. To install a cloud host platform (again as a hobby), some moodle platforms (for tests and experiments), some personal websites (for artistic experimentation).

There are another things that worry myself: I have to point port 80 from my router to the server... that port is used by skype... will it affect my skype calls?

Thanks you...

---

### Post by TheFu on 2014-05-16
Everything you've asked is requesting opinions. I'm happy to provide mine.

The only public service you should put on a public-facing server is ssh. NOT FTP!!!!!  NOT mySQL!!!!!  Just ssh.
After installing the ssh server, install fail2ban and setup keybased authentication, NEVER USE PASSWORDS.

Hobby or not, a public IP is an invitation to be hacked. Block all inbound ports except ssh. Use ssh-tunnels to access whatever you like to run internally, but still access from outside. Pretty much everything you want can to be done over ssh tunnels, securely from anywhere in the world.

Some reading with my opinion - 
* [Stop using FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")
* [Secure SSH]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")
* [Running only LTS releases]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") - 14.04 is the CORRECT answer for you today, IMHO.

Oh - and by doing the ssh-only part, you've just blocked 99.99999999% of the bad people.  You can use sftp from anywhere in the world, securely.  You can setup sftp-only accounts (using keys) for friends.  You will avoid php, which is a major security risk for non-professionals to run on the internet.

Oh ... and ssh is much, much, much easier than FTP to manage and secure.

Lastly, here's my first 5 minutes on a server - the things I do: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) - packages I load, settings I enable, stuff like that.

howtoforge.com is a website you might enjoy, just know that because something works, that doesn't mean it is secure.

---

### Post by dult on 2014-05-17
> **TheFu said:**
> Everything you've asked is requesting opinions. I'm happy to provide mine.

The only public service you should put on a public-facing server is ssh. NOT FTP!!!!!  NOT mySQL!!!!!  Just ssh.
After installing the ssh server, install fail2ban and setup keybased authentication, NEVER USE PASSWORDS.

Hobby or not, a public IP is an invitation to be hacked. Block all inbound ports except ssh. Use ssh-tunnels to access whatever you like to run internally, but still access from outside. Pretty much everything you want can to be done over ssh tunnels, securely from anywhere in the world.

Some reading with my opinion - 
* [Stop using FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")
* [Secure SSH]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")
* [Running only LTS releases]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") - 14.04 is the CORRECT answer for you today, IMHO.

Oh - and by doing the ssh-only part, you've just blocked 99.99999999% of the bad people.  You can use sftp from anywhere in the world, securely.  You can setup sftp-only accounts (using keys) for friends.  You will avoid php, which is a major security risk for non-professionals to run on the internet.

Oh ... and ssh is much, much, much easier than FTP to manage and secure.

Lastly, here's my first 5 minutes on a server - the things I do: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) - packages I load, settings I enable, stuff like that.

howtoforge.com is a website you might enjoy, just know that because something works, that doesn't mean it is secure.

Thanks for the swift reply. I didn't know FTP was so unsecure.

Btw, when I said Ubuntu 14 I meant 14.04, didn't know there would be so much difference.

sFTP and SSH would be fine solutions If it would be only me using the server and only to access files.

Maybe I didn't explain myself well enough... I state the HOBBY projects I intended to make:
[LIST]
[*]Have a public facing LAMP server (this means php and also is the biggest security flaw ever) to power:
[LIST]
[*]Install cloud hosting software that runs over the lamp stack;
[*]A simple webpage that must be accessed via its dynamic ip;
[*]A php script power by cron that gives the server IP to another website with fixed IP so we can find the webpage (don't ask, conceptual artistic stuff).
[/LIST]
[/LIST]

As I said, I didn't study this stuff. I'm self taught and my companies server's are managed and so any technical and security issues are handled by the hosting provider, though I've learned lots!

I'm not going to host private stuff, so i don't care If I have to take the server down and reinstall everything, I don't mind that.

I just don't want someone acessing the pc and installing some malicious software that is going to screw my home router and jeopardize my others pcs.

From what I tested... php can do all these malicious stuff I mentioned... Am I being to platonic with this idea?

Thanks by the way.

---

### Post by TheFu on 2014-05-17
a) your hosting provided probably DOES NOT patch or provide security updates, as you believe they do, unless you are paying them extra specifically for that service. None of the popular providers do it.
b) If you don't want to learn security, then DO NOT PUT a webserver (especially with php on it) on the internet!
c) Get your backups working perfectly. versioned backups are critical for everyone, especially if they do high-risk stuff.

If you don't want someone screwing with your home network, only open the ssh port used and run fail2ban.

You can configure secure ssh-tunnels or a VPN to share ideas with other internet servers. Just don't let the world have access.
No need for the last bulletpoint - just use a dynDNS address.

Sorry, I don't understand the last sentence.  php can be used maliciously by others if you load it and don't know security enough to lock it down. Any language used can be hacked, but php seems to get lots of people who really don't know what they are doing.  To start learning php security techniques, visit the [OWASP PHP security  checklist]("https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet") page. I think your eyes will be opened.  I am not the only person who believes that php shouldn't be used by non-professionals.

---

### Post by dult on 2014-05-17
> **TheFu said:**
> a) your hosting provided probably DOES NOT patch or provide security updates, as you believe they do, unless you are paying them extra specifically for that service. None of the popular providers do it.
b) If you don't want to learn security, then DO NOT PUT a webserver (especially with php on it) on the internet!
c) Get your backups working perfectly. versioned backups are critical for everyone, especially if they do high-risk stuff.

If you don't want someone screwing with your home network, only open the ssh port used and run fail2ban.

You can configure secure ssh-tunnels or a VPN to share ideas with other internet servers. Just don't let the world have access.
No need for the last bulletpoint - just use a dynDNS address.

Sorry, I don't understand the last sentence.  php can be used maliciously by others if you load it and don't know security enough to lock it down. Any language used can be hacked, but php seems to get lots of people who really don't know what they are doing.  To start learning php security techniques, visit the [OWASP PHP security  checklist]("https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet") page. I think your eyes will be opened.  I am not the only person who believes that php shouldn't be used by non-professionals.

Possibly then, ssh is the safest route.

In terms of php... I managed to access another virtual host's moodle config file using simple php readfile. SO, whenever I code php, it's simples stuff (white listed includes via get) and cleansed POST.

Thank you for your time... it was ver enlightening, will do my best to learn ssh.

---


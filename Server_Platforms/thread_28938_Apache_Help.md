---
title: "Apache Help"
date: 2005-04-22
forum: Server Platforms
---

### Post by PeteG on 2005-04-22
Hi,

I installed apache, mysql and php using the ubuntuguide as a reference. I've installed a program called moodle all fine, using all the above. The server is connected to the lan and obviously the internet. When i access the server from the lan IP i have no problems, i can access the moodle program fine. However when trying from the internet IP... it waits for a while then says access denied. I've been trying to get this going all afternoon without any luck. Below are the links to my conf files. Any help would be greatly appreciated.

[http://members.iinet.net.au/~pgri7434/conf_files/hosts](http://members.iinet.net.au/~pgri7434/conf_files/hosts)
[http://members.iinet.net.au/~pgri7434/conf_files/apache2.conf](http://members.iinet.net.au/~pgri7434/conf_files/apache2.conf)
[http://members.iinet.net.au/~pgri7434/conf_files/httpd.conf](http://members.iinet.net.au/~pgri7434/conf_files/httpd.conf)
[http://members.iinet.net.au/~pgri7434/conf_files/ports.conf](http://members.iinet.net.au/~pgri7434/conf_files/ports.conf)
[http://members.iinet.net.au/~pgri7434/conf_files/sites-available/default](http://members.iinet.net.au/~pgri7434/conf_files/sites-available/default)

Pete.

---

### Post by CrustyDOD on 2005-04-22
You're probably behind router if you can't access server from outside of your LAN. If so open port 80 TCP, default port for Apache unless you changed it..

---

### Post by bnutting on 2005-04-22
Here is a silly question, can you ping your local IP from the Internet?

---

### Post by PeteG on 2005-04-22
I can ping both IP's... my lan and my internet IP fine. I don't have a router however would ubuntu block port 80? I'm going to have a look now how to open ports on linux or check which ones are open. If that doesn't work i'm not sure what i could do. I might also show you guys the testphp.php that's on the server as it showed some apache settings in there. Thanks.

Pete.

---

### Post by PeteG on 2005-04-24
Ok i still can't work this out. After actually rebooting the computer i had to change the ports.conf file back to just "Listen 80" or else i couldn't even access the apache server. Also all the information i read over at apache2.org seems to be wrong. The version i installed, is it completely different to it or something? When typing the apachect1 command i get an error saying no such thing. So to start the apache2 server i had to sudo /etc/init.d/apache2 start. Is there a guide somewhere about this debian version of the apache2 server? I can access everything fine from the LAN and from the actual machine itself (localhost), however through the internet just won't work. I loaded up firestart and tried using that however it seemed to just block everything and even trying to get VNC to work through it was a nightmare. I opened all ports for VNC both inbound and out and it still wouldn't work so i turned the firewall off. Any help would be really appreciated.

Pete.

---

### Post by heimo on 2005-04-24
You need to check that the port 80 is open to outside world. If it's not, you need to find what's causing it. When you first posted this thread, I went quickly though your configuration and it looks fine to me.

If you have computer on some other network which can access your server from Internet and you know how to port scan (for example nmap -p 80 serverip), do it. Other way to do it is use this "ShieldsUp!", browse it from your server (hmm... if you have browser there...), select ShieldsUP! (middle of the long page), Proceed, enter 80 in text field and select User Specified Custom Port Probe. Of course the port should be open.
[http://www.grc.com/default.htm](http://www.grc.com/default.htm)

My guess is it's closed or "stealth". If it's open, use another computer to telnet into that port. (telnet serverip 80) and enter 
 ```
HTTP GET / HTTP/1.0 [enter]
[enter]
```

Do you get some html page or any "banner" at all? What is the result code? 200? 404? 500?

Cheers!

---

### Post by PeteG on 2005-04-24
Hi,

Thanks for the help heimo! Turns out that my ISP blocks port 80 and i had to go into the toolbox to unblock it. I used the SheildsUp program and managed to work out that it was the ISP. I'm a little worried now as with my ISP port blocking is either on for all connections, or off. So when disabling port blocking the following ports are opened for all accounts.

# Port 25 (smtp) - Blocked in/outbound on all bliink home and dynamic dial accounts.
# Port 80 (http)
# Port 135 and 139 (netBIOS)
# Port 443 (https)

Now i have 4 computers at home and each of them get a different internet IP address, they all connect through the same modem but get a different IP. 3 machines are windows (on SP2), and they've all got the firewall enabled. The linux box doesn't have a firewall. I might play more with firestarter on the linux box and try get it to cooperate. I'm worried about these ports being unblocked, possibly making the network really vulnerable?

Pete.

---

### Post by heimo on 2005-04-25
[QUOTE=PeteG]
I'm worried about these ports being unblocked, possibly making the network really vulnerable?
Pete.[/QUOTE]

Hmm... I'd consider putting all those computers behind firewall and the Linux box with services to outside world on DMZ. That way you could have better control. Make sure your Windows boxes are not running IIS and that filesharing / printer sharing is blocked to outside world - also on Linux if you're running samba.

Of course the best way to design your network topology varies on many aspects, so don't trust my words blindly.

---


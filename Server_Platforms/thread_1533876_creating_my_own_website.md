---
title: "creating my own website"
date: 2010-07-18
forum: Server Platforms
---

### Post by dustdevels on 2010-07-18
ive gotten as far as being able to install lamp server i have a template i wanna use but when i try to stick it into www folder it will not allow me to im completely new at linux os a friend of mine has helped me get as far as i have and told me ubuntu forums and google were my best friend at learning linux.... ive also been informed that since im on cox it wont let my site show outside my network and as i said im totaly new to this i have no idea what im doing and dont want to mess anything up anybody out there willing to help

---

### Post by Ryan Dwyer on 2010-07-18
Regular users don't have permission to write to /var/www. If this is a test server you might want to consider creating a www folder inside your home folder, then changing your Apache config so the DocumentRoot points to /home/yourname/www instead of /var/www.

---

### Post by richardjh on 2010-07-18
Is this just a test / development box or are you looking to put this server online and use it to host a real website?

In either case, you will need to get up to speed a little bit on permissions. 
Something like [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml) should help.

Badly secured websites are a real problem so do not be tempted to just "chmod 777 " the /var/www/ directory if someone suggests that.

I would change the ownership of /var/www/ to be owned by me, to do this open a terminal window under Applications > Accessories > Terminal

If you aren't familiar with using the terminal, don't panic, this is a one liner that will save you having to use the command line for copying and editing files.

```
$ sudo chown richardjh /var/www/
```Note: This literally means; as the super user, change the ownership of /var/www/ to richardjh. 

You should be able to get someone to verify this wont break your setup and is safe to do, by someone on this forum fairly easily.

Obviously, use your username not "richardjh". Enter your password when prompted.

You can then copy files in and work on them without having to keep using sudo at the command line.

Once you have the code in place, check it runs by visiting [http://localhost](http://localhost) in your web browser.
Check for errors in the file /var/log/apache2/error.log. The other log file you need to know if /var/log/apache2/access.log.

---

### Post by dustdevels on 2010-07-18
well im workin on a pserver for a game i play and i was gonna host it off my server and post it so i dont have to worry about bandwidth and my site closing out on me the server side of the game will only run on linux and i know linux is a good os so im trying my hand at it

---

### Post by dustdevels on 2010-07-19
ok ive gotten a lil further but now having other issues im using no ip i can hit the site from another computer on my network but cant hit it from outside the network ive forwarded a few ports for the spacific machine but still cant get it from outside im using no-ip and their port checker cant hit my site either its a dynex router  any suggestions

---

### Post by richardjh on 2010-07-19
You need to forward port 80 to the local IP of the machine with the site on it on your router.

So assuming your router is on 192.168.1.1 and your server is on 192.168.1.34 you will need to forward port 80 on the router to port 80 on 192.168.1.34.

You can then easily test this bit is working by visiting 

[http://192.168.102.1](http://192.168.102.1) 

in a web browser on any machine on your local network. 
As you are not using name based hosts on apache on your server you should see your website.

If that works, you will need to find out what your external IP address is.
The easiest way to do this is to visit [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and it will tell you what your IP is.

Supposing it is 86.174.32.9.

Then you should visit  [http://86.174.32.9](http://86.174.32.9) in a browser and still be able to see your website. Test this and let us know.

---

### Post by Joe of loath on 2010-07-19
> **richardjh said:**
> You need to forward port 80 to the local IP of the machine with the site on it on your router.

So assuming your router is on 192.168.1.1 and your server is on 192.168.1.34 you will need to forward port 80 on the router to port 80 on 192.168.1.34.

You can then easily test this bit is working by visiting 

[http://192.168.102.1](http://192.168.102.1) 

in a web browser on any machine on your local network. 
As you are not using name based hosts on apache on your server you should see your website.

If that works, you will need to find out what your external IP address is.
The easiest way to do this is to visit [http://www.whatsmyip.org/](http://www.whatsmyip.org/) and it will tell you what your IP is.

Supposing it is 86.174.32.9.

Then you should visit  [http://86.174.32.9](http://86.174.32.9) in a browser and still be able to see your website. Test this and let us know.

Just a note, it I enter my external IP on a box inside my network, I see the login page. What you have to do is use a web proxy, such as hidemyass.com, and enter it there.

---

### Post by richardjh on 2010-07-19
I don't understand your last post. Sorry.

---

### Post by Joe of loath on 2010-07-19
I mean that if I use my dyn-dns hostname or external IP in a web browser inside my network, it shows me the login page for my router, not my website. Because to me, the IP is pointing at my router. It's all very complex, and something to do with NAT.

To see what someone else would see, I have to use a web proxy like hidemyass.com. If I type in my dns or IP there I see what someone would see from outside my network.

---

### Post by dustdevels on 2010-07-19
**i forwarded port 80 ive also forwarded 443 and another port theres a site that no-ip uses to test your ports have opened i type in my ports that ive opened and hit the check button and it comes back connection refused its basicly saying my router is denying the connection i can see my site internally  and everybody outside gets jack and see as i said im completely new to the whole linux apache mysql its all 100% new**
 
**yes i can hit the site with my external ip and internal ips from inside my network but if anybody outside my network trys to view it will now show**

---

### Post by mcarrara on 2010-07-19
your hostname resolves to 72.209.145.18:9000.  That means it is trying to use port 9000.  I tried just using 72.209.145.18 and all I get is page loading message then a blank screen.  I do not use Apache so I can't help you there but I would bet something in the configuration is messed up.  I know it could be a simple as a period or semi colon.  I once worked for a week straight only to find an extra space at the end of a parameter which made things not work.

Mark

---

### Post by richardjh on 2010-07-19
If you find that visiting your external IP takes you to a web interface for the router you will need to set up a different port forward rule.

Convention is to use 8080


Assuming your external IP is 86.174.32.9 and the server is on  192.168.1.33, then:



So your website will be on [http://86.174.32.9:8080](http://86.174.32.9:8080) for example.

Then you set up a rule to forward everything on port 8080 to 192.168.1.33 port 80.

How you sort out the dns for this is another problem. I know there are services out there that do this.

---

### Post by dustdevels on 2010-07-19
using localhost,using router ip and using external ip from with in my network all go strait to the site even using my dns name all takes me to my site but anyone trying from outside my network gets an error i have ports 80 443 and 9000 all forwarded on my router and if my routers not the issue then its the apache system who knows how to change what ever in apache ....

---


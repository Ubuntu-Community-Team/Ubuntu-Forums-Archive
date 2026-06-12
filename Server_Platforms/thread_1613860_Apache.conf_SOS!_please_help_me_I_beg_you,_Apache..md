---
title: "Apache.conf SOS! please help me I beg you, Apache.conf"
date: 2010-11-04
forum: Server Platforms
---

### Post by Axpence on 2010-11-04
[IMG]http://i55.photobucket.com/albums/g153/axpence/Screenshot-3.png[/IMG]


Above is a screenshot of my apache.conf file
I have been reading everywhere I can on the internet for how to edit the apache.conf file in ubuntu.
I purchased a domain name and would like it to be hosted on this machine,
I pointed the domain to my external IP,
I forewarded SSH & HTTP to my linux box
(I think I successuflly installed Joomla)
but still NOTHING is on my website address ([www.leetcs.net](www.leetcs.net))
can anyone please help me?
feel free to email me at [email]alexanderhspencer@gmail.com[/email]
thanks!
-Alex

---

### Post by Barriehie on 2010-11-04
Does your ISP block port 80???  Most do.  If so you'll have to use a diff. port.  What have you got in /etc/apache2/sites-available and /etc/apache2/sites/enabled?

What happens when you connect to [http://localhost](http://localhost), or http:127.0.0.1, what are your error log(s) showing.

---

### Post by wongo888 on 2010-11-05
For your connection refused error, I would ensure that your firewall on your home router is actually forwarding traffic as it should. You might need to verify that Comcast is not blocking port 80 (try a diff port if all else fails). 

If your ISP is not blocking you and your router config is okay, then ensure that the firewall on your server (the machine you're using to run apache) is allowing port 80 traffic:

```
$ sudo ufw status
```

If it is enabled, turn it off:

```
$ sudo ufw disable
```

or allow Apache port traffic:

```
$ sudo ufw allow Apache
```

See: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

You can check your ports using nmap (replace with your IP):

```
$ sudo nmap -sS -O -PI -PT 192.168.0.1
```

Also, you might want to consider using virtualhosts for your site. To enable new virtualhosts, you should use the Debian/Ubuntu specific command to add them (rather than editing the httpd.conf directly as in other UNIXes) and then restart apache:

```
sudo a2ensite mynewsite
sudo /etc/init.d/apache2 restart
```

This is the prefered way to add virtual hosts as noted in the docs:

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by cabaro on 2010-11-05
Try accessing your external ip from a browser to see if you even get through to apache. Something like this:

first check the ip
$ host yourdomain.net

yourdomain.net has address 123.123.123.123

get the ip from that, and then in browser:
[http://123.123.123.123:80](http://123.123.123.123:80)

If it's apache answering, you should get answer something like this:

It Works!


If you get access denied, you are probably being blocked by your router or isp. Or you have blocking rules in your apache.conf like:

<location />
  order deny,allow
  deny from all
</location>


Sorry for syntax errors in the message, but i think you get the idea :)

/cab

---

### Post by volkswagner on 2010-11-05
As others have mentioned check if port 80 is open.  An easy way is to go to [http://canyouseeme.org/](http://canyouseeme.org/) 

Can you view your site locally on your lan from another machine via the local ip address of your web server box?

---

### Post by Axpence on 2010-11-09
First off, let me just say that I am so thankful that all of you took time out of your lives to help me for NOTHING in return, that is charity. Thanks!
Barriehie:
1) I think port 80 may have been blocked. On various port forwarding testers it says that it is blocked, but on the same port forwarding testers it says that port 22 (SSH) is blocked, but I have ssh’ed into this Linux box about a week ago.. hmm.
2) /etc/apache2/sites-available has 2 files “default” and “default-ssl”
 3) and /etc/apache2/sites/enabled has the file “000-default”
4) when I connect to Localhost my firefox gives me an the “Unable to connect” error
5) I will have to look up how to see my error logs!!! Lol (newbie &#61514;)
Wongo888:
1)I did set up port 80 to forward to my linux box on my local router
2) I tried the ufw command, looks like my local machine is now allowing apache traffic 
3) I downloaded and installed nmap, but I could not understand how to use it, I’ll have to try again after reading up a bit about it. THANKS FOR THE HELP!
4) I will try and use virtual hosts, I’ll study the link, That tip is MUCH appreciated.
Cabaro:
1) I tried to access my apache like you said, just a timed out message from firefox/ie
2) No sort of blocking rules in my apache.conf file, (the picture I uploaded I think should clarify that)
Thanks a billion
---Anyway, thanks all for the help, any further help is much appreciated, sorry for the delay!!!
-Alex
[email]alexanderhspencer@gmail.com[/email]

---


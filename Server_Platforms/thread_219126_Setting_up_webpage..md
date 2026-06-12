---
title: "Setting up webpage."
date: 2006-07-19
forum: Server Platforms
---

### Post by sdmike on 2006-07-19
If I want to run my webpage off of one of my computers, what would be the best programs to use?

Also lets say if one of those packages is Apache do I have to make that computers IP static because I'm on a router?

---

### Post by scxtt on 2006-07-19
install apache2 (via synaptic or apt-get or aptitude) and put your files in /var/www then navigate to your static IP address - which is easy to set via network-admin [type **network-admin** in a terminal window, it'll prompt you for your sudo password] ...

---

### Post by sdmike on 2006-07-19
Ok I downloaded Apache2 and it works fine and I made my ip static.
So my next question is how do I configure it so I can access my site from any computer outside my localnetwork like any other website?

---

### Post by scxtt on 2006-07-19
you need to know the IP of your router - and if you're running a firewall (like firestarter), you need to forward port 80 to the IP address of your apache server ...

---

### Post by sdmike on 2006-07-19
My ISP blocks port 80, so I made port 8080 and had that configured in Apache so it listens in on 8080. So when I went on my localnetork to see if it worked by putting in <my real IP:8080> I got server not found.

I have a linksys wireless router to I did something like this

HTTP start-8080 End-8080 Both 192.168.100 enable

---

### Post by scxtt on 2006-07-19
just cause you didn't mention it, did you restart apache [ **sudo /etc/init.d/apache2 restart** ] after making changes to the config file?

---

### Post by Randomskk on 2006-07-19
Accessing your real world IP from a computer on your network usually doesn't work.
Try going to a proxy such as [www.unipeak.com](www.unipeak.com) and trying from there.

---


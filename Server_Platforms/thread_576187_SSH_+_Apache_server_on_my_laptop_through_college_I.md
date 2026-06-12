---
title: "SSH + Apache server on my laptop through college ISP"
date: 2007-10-14
forum: Server Platforms
---

### Post by Zambini on 2007-10-14
Hello UbuntuForums!
I have a slight problem, 

I am trying to do two things
1) Set up SSH so I can log into my computer from anywhere
2) Set up an apache website so I can mess with html & php & all that good stuff

I installed apache via the apt-get stuff, and I signed up my IP address with dyndns.

When I attempt to ssh to *username@myaccount.dyndns.com* from my laptop, it works fine, and when I go to *myaccount.dyndns.com* it works fine also, but when my friend tries to do either of them on his computer, neither works.


I am at college, using the on-campus ISP, so I can't configure the router/switch/whatever it uses, and I am using wireless internet on my Sony Vaio laptop. Ubuntu Dapper Drake 6.06

My guess is its one of two things:
1) I'm using wireless
2) I didn't set something up correctly

How can I set this up?

Thanks :)

---

### Post by MJN on 2007-10-15
As this could be a DNS issue it would be useful to know your URL to enable this to be ruled in/out (not to mention serving as a 3rd party to confirm whether it's your, or your friends, issue).
 
Mathew

---

### Post by Zambini on 2007-10-15
[http://zambini.homeunix.com/](http://zambini.homeunix.com/)

Also, to access wireless internet at our college, you are directed to a login page, where you submit your login/password to connect to the wireless, and when my friend tries to go to my url it redirects him to that page instead of my page in the www/ directory.


Do you think plugging in an ethernet cable vs wireless would make a difference?

---

### Post by MJN on 2007-10-15
Where's your friend? Also at college, or elsewhere?

Perhaps your college doesn't allow port 80 access from outside (so you don't host websites on your PCs using their connection). However, you yourself may not be affected by this on your laptop as you're already on the 'inside'.

It's difficult to say really. I've tried connecting to that URL also but there's no response.

Perhaps you could try changing your Apache port from 80 to something (something high, in the thousands) and seeing if that gets you anywhere.

Mathew

---

### Post by crazyone on 2007-10-15
yea smae here have you tried setting apache to port 8080. that might let you thorugh so you can host the website or if not mabe your school would be nice enought to let you but it on a school computer.

---

### Post by Zambini on 2007-10-16
The website is mostly just for fun, but the SSH is what I want to get working. Can I change the SSH port? or is that tied into the apache config somehow?

---

### Post by D-EJ915 on 2007-10-16
> **Zambini said:**
> The website is mostly just for fun, but the SSH is what I want to get working. Can I change the SSH port? or is that tied into the apache config somehow?
sudo nano /etc/ssh/sshd_config and edit the port there, you should also change a few things if they aren't already done, like permit root login = no.  I think ubuntu comes with some of the recommended things already done.

For apache sudo nano /etc/apache2/ports.conf and just put in whatever you feel like, you can have as many as you want, I have mine listening on 80 (for me) and on another port I have routed to the outside...I don't really need to do that but I did.  Just follow the same way it is already on the next line, etc.

Thing about changing your web server port is that you have to specify the port when you use the url, not a big deal but just tell people that...or  you could use a port 80 redirect service but I don't like those.

---

### Post by Zambini on 2007-10-18
Hmmm.... so I just tried it with :8008 (the port I am using) and it doesnt work on a different laptop on the same network.

 But It works on my laptop....

---

### Post by MJN on 2007-10-18
I'm afraid I'm somewhat lost and confused as to the topology of this network, particular regarding how your friends fits in with it.

Unfortunately I feel understanding this is key to finding the solution so will have to duck out. :(

Mathew

---

### Post by dfreer on 2007-10-19
I'm willing to bet that your college has a campus wide firewall, using NAT to transverse the network. I extremely doubt that you are going to be able to run a website/SSH server from your college, but there might be several ways to check. First, check out [http://whatismyipaddress.com/](http://whatismyipaddress.com/) If the IP address reported there is not the same as your computer's IP, then you are most certainly behind a router, most likely with a firewall. You can then try opening random ports (port 80 and 22 first, but they are almost certainly blocked), and use [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to check if those ports are open. 

Try all of this from your LAN, not wireless.

---

### Post by Zambini on 2007-10-22
Ok, well I asked our IT dept and they said they have basically everything blocked, because you can get both Allowed User (aka: students/teachers/people who are supposed to have access) and Guest access can be granted temporarily also.


They also have Secure Email ports (like to Gmail), most games, Steam, etc etc. blocked


alas*

I guess Ill have to hardwire my lappy if I want to SSH... :( no manipulating my computer via blackberry SSH :( heheh. my inner g33k died a bit)

---


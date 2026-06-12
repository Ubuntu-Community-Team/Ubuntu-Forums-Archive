---
title: "looking to make a career in it working in linux"
date: 2015-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by dbranston4 on 2015-03-09
hi guys and ladies i wonder if i might pick your brains for a few i am looking to work inthe it industry i would love to get involved in working with a linux enviroment,

as a career  path what would you recommend as my ideal first course along side working with tutiorials etc i find on the web. 

i am looking into going sys admin route but then hopefully going into design or possibly security 

your help however small would be appreciated

---

### Post by anthony54 on 2015-03-09
Personally I would recommend a course on cisco networks.  I pursued an IT course a few years back (went a different direction though) and cisco kept popping up under every IT course offered.  Not sure if they set the bar, but I do know that they are used quite often.

---

### Post by Bucky Ball on 2015-03-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by dbranston4 on 2015-03-09
> **anthony54 said:**
> Personally I would recommend a course on cisco networks.  I pursued an IT course a few years back (went a different direction though) and cisco kept popping up under every IT course offered.  Not sure if they set the bar, but I do know that they are used quite often.

thanks Anthony i have seen them pop up quite a bit myself, its more the cost more than anything (as in not working so not much accesible cash)
I found an interesting place called code academy just done my first website tonight that was fun so i think i will keep trying different aspects and see where i lay ie
 which i most enjoy and go from there 

i will look fiurther into cisco though i think they are kind of the standard bearers and trustworthy obviously with there rep in the IT world .

---

### Post by dbranston4 on 2015-03-09
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

apologises bucky will look closer to where things should be posted in future

---

### Post by imotor on 2015-03-13
Learning Cisco networking is excellent advice for a career in IT. But Cisco certs won't help you much for learning Linux.

Here is my advice:

1. Find an old PC that nobody wants anymore (hopefully 64-bit, multicore, 2GB memory at least.)

2. Set it up in a corner and use it only for learning, resist the temptation to use it for important stuff.

3. Install Ubuntu 14.04 Desktop.

4. Get a good book on bash and shell scripting, get a decent understanding of commands, redirection, piping, environment variables, filesystem architecture, and editing config files.

5. Install VirtualBox.

6. Install Ubuntu Server (command line only) as a guest OS and run updates/upgrades.

7. Export guest OS as appliance.

8. Import that appliance.

9. Setup an apache web server on that guest. (plenty of info on the web)

Repeat steps 8 and 9 but with the folloing servers:

DNS/DHCP

NFS/Samba file server

LDAP

Email server (postfix, sendmail, dovcot, etc.)

Database (MySQL, PostGreSQL)

FTP

Puppet or Chef

---

### Post by coldraven on 2015-03-14
> 5. Install VirtualBox.

6. Install Ubuntu Server (command line only) as a guest OS and run updates/upgrades.


Way to go! You can get lots of ready-made VirtualBox server images from here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by coldraven on 2015-03-14
After you get your virtual server running learn how to install SSH on it. Then log into the sever from the host machine using SSH. That way you'll have a full screen terminal and all of the tools and programs of the host available to you.

---

### Post by dbranston4 on 2015-03-20
Thanks guys just so happens i fixed my old pc ( i say old its better than my laptop and im going to be using that as a ubuntu gnome with a partion for a server on it also. 
im up to about 5 or 6 on your list [**[COLOR=#000000]imotor[/COLOR]**]("http://ubuntuforums.org/member.php?u=1337459") but i have made a copy of your full list so i can refer to it when needs be also i joined the linux academy 33 pounds for 3 months of tutorials downloadable content etc ( anyone any experience of these guys ) 
i got hold of putty for the ssh key generator seems ok ( more info appreciated ) [**[COLOR=#000000]coldraven[/COLOR]**]("http://ubuntuforums.org/member.php?u=993657") 
i was working on user controls today adding and removing users tommorrow gonna be working on enviromental variables no clue whats that about except it is something to do with bash 
I really want to have a go at apache but i have a feeling i shoud learn to walk before i can run ( what do you think ) 
With all this new stuff im learning is there a place i can put it to the test ie somewhere that asks you to do scenarios etc

---

### Post by bardo2 on 2015-03-23
Hi, i had my life in the business, done almost any job, low and high, seen many careers, and - depending on your interests/ambitions - i'd put forward:
The fastest growth in knowledge/skills i saw with the fierce and engaged staff in customer support (phone, email,...) Best place to learn the business while earning money. IMHO
You cannot imagine who you would be after 6-12 months on the job, i promise!

---


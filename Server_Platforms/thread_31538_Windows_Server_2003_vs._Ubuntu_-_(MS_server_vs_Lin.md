---
title: "Windows Server 2003 vs. Ubuntu - (MS server vs Linux - the timeless question)"
date: 2005-05-03
forum: Server Platforms
---

### Post by amnesia on 2005-05-03
Hello all -

I am having issues in convincing my supervisor's supervisor to use Ubuntu rather that Windows 2003 Sever to host their websites (about 7-10 all together).

I was turned on to Ubuntu by a user here and have to say that it's a great improvment over what I was used to (Fedora Core 2 - yes, it's been a while)

On this server I plan to use Apache2, php4, MySql, Postfix, SpamAssassin, ClamAV, Firestarter, and Webmin (I think that's it...).  It's a dual xeon 3.2 with 1 gig memory.

The main issue with the 'bobs' is that they are concerened of quality/reliability(security)/cost running Ubuntu rather than Windows Server.  They are concerned because of the low cost of the above listed software that it's not as 'good' (not my choice of words, but...) as a Windows server would be, and since they run all other Microsoft software that it's going to be a pain in the #@# to maintain.  Does anyone here have a similar comparison they can share or any info they could thow out to help steer me to information that would help my Ubuntu case?  

I would really appreciate it.

Kevin

---

### Post by shakin on 2005-05-03
Hey Amnesia, glad you made it here!

Check out this chart from Netcraft:

[IMG]http://news.netcraft.com/archives/2005/05/overallc.gif[/IMG]

(if it doesn't work hit [http://news.netcraft.com/](http://news.netcraft.com/) and look at the middle of the page for the market share analysis).

Basically, Apache holds nearly 70% of the web server market share and it's growing, while MS IIS is shrinking.

Your bosses are in a different world with web servers. This is where Microsoft is not the safe choice... they're the unproven one.

---

### Post by s0c0 on 2005-05-03
[QUOTE=shakin]Hey Amnesia, glad you made it here!

Check out this chart from Netcraft:

[IMG]http://news.netcraft.com/archives/2005/05/overallc.gif[/IMG]

(if it doesn't work hit [http://news.netcraft.com/](http://news.netcraft.com/) and look at the middle of the page for the market share analysis).

Basically, Apache holds nearly 70% of the web server market share and it's growing, while MS IIS is shrinking.

Your bosses are in a different world with web servers. This is where Microsoft is not the safe choice... they're the unproven one.[/QUOTE]

Market share is the best argument to bring up against management types.  The market share that apache holds will help highlight its reliability and security.  

On the otherhand if IIS and MS Server03' is performing good then what reason do you have for converting over?  Is the downtime worth it? 

I have a client I have been working with for a week now and I was unable to convince them to go with Linux, but that's okay since it comes down to what the client, customer, and boss wants.

---

### Post by amnesia on 2005-05-03
There isn't a current web server, this is a brand new server built from ground up and they are wanting to move their websites in-house.

thanks shakin for the chart - it's gonna be put to good use.

---

### Post by Ride Jib on 2005-05-03
[QUOTE=amnesia]Hello all -

I am having issues in convincing my supervisor's supervisor to use Ubuntu rather that Windows 2003 Sever to host their websites (about 7-10 all together).

I was turned on to Ubuntu by a user here and have to say that it's a great improvment over what I was used to (Fedora Core 2 - yes, it's been a while)

On this server I plan to use Apache2, php4, MySql, Postfix, SpamAssassin, ClamAV, Firestarter, and Webmin (I think that's it...).  It's a dual xeon 3.2 with 1 gig memory.

The main issue with the 'bobs' is that they are concerened of quality/reliability(security)/cost running Ubuntu rather than Windows Server.  They are concerned because of the low cost of the above listed software that it's not as 'good' (not my choice of words, but...) as a Windows server would be, and since they run all other Microsoft software that it's going to be a pain in the #@# to maintain.  Does anyone here have a similar comparison they can share or any info they could thow out to help steer me to information that would help my Ubuntu case?  

I would really appreciate it.

Kevin[/QUOTE]
 Unless you are using MySQL already on those windows servers, you may want to do a little research first. MySQL just implemented views/stored procedures/ and triggers, and from my personal experience they are a little shaky (as expected on a first release). 

Apache is definitely the way to go. And since it is a dedicated web server (or so it sounds), you can bump up system efficiency by getting rid of all the extra crap you don't need (unlike MS who gives you some stuff and doesn't let you get rid of it).

Efficiency is key

---

### Post by s0c0 on 2005-05-03
If they are just looking to blow some bucks you could have them go Novell Linux or RHEL.

---

### Post by Myles3 on 2005-05-04
[QUOTE=s0c0]If they are just looking to blow some bucks you could have them go Novell Linux or RHEL.[/QUOTE]

If you want something like Novell Open Server or RHEL then go for CentOS. Thats what we are using at my work.

---


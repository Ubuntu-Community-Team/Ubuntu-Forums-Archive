---
title: "Netatalk question"
date: 2010-09-12
forum: Server Platforms
---

### Post by johan.alfa on 2010-09-12
Hello,

I would like to build a 10.04 ubuntu file server with netatalk.
I was looking for the best strategy but I'm not sure.
Last netatalk version is 2.1.3 and I found this.

[http://plus-alpha-space.cocolog-nifty.com/blog/2010/07/ubuntu-1004neta.html]("http://plus-alpha-space.cocolog-nifty.com/blog/2010/07/ubuntu-1004neta.html")

Is the link above safe or should I trust doing

sudo apt-get install netatalk

Thanks,

---

### Post by Fraaik on 2010-09-12
Hi johan.alfa,

the

sudo apt-get install netatalk

did the job for me some month ago. But the whole network traffic slowed down enormous. I did not solved this problem never. That's why I dicided to disable netatalk again...

---

### Post by johan.alfa on 2010-09-12
> **Fraaik said:**
> Hi johan.alfa,

 But the whole network traffic slowed down enormous. I did not solved this problem never. That's why I dicided to disable netatalk again...

Hello Fraaik

How did you experience the slow down?
Was it all network traffic on all computers or just the server?
Did you measure it?

Regards,

---

### Post by kevinthecomputerguy on 2010-09-13
Are you installing this for Macintosh use?
Because SAMBA will work, from your MAC finder window you can access SAMBA shares like this
 
smb://192.168.1.1
 
Where 192.168.1.1 is the IP address of your SAMBA server.
 
I too experience slowness with netatalk, its all about SAMBA.
 
-Kev

---

### Post by johan.alfa on 2010-09-13
> **kevinthecomputerguy said:**
> Are you installing this for Macintosh use?
I too experience slowness with netatalk, its all about SAMBA.
 
-Kev

Hello,

Yes this would be for Mac OSX users.
Strange you mention also slowness because I read so many comments about afp being so much faster then samba.

Regards,

Johan

---

### Post by Fraaik on 2010-09-13
Hello,

to give you an idea what i mean with "slowing down": to copy a 1MB file from one mac to an other takes about 1 minute! All other net traffic runed at normal speed. After disabling netatalk mac users in our LAN where happy again.

Our samba server can be connected by "servername" in the finders lookup field too (OS X).

---

### Post by 1serveyou on 2010-09-13
I've been using Samba for the past couple months and it has been great. You can have it so that those "shared" folders always stay in the finder as well too which is nice.
 
I will say I never tried netatalk as I have window machines on the network too, and using Samba made it more convenient.

---

### Post by lmicu on 2010-09-17
I am considering using netatalk for the Time Machine purpose. Did any of you guys do this? This would work in combination with Avahi.

Also when you experience slowness, is that an the 2.1.3?

---


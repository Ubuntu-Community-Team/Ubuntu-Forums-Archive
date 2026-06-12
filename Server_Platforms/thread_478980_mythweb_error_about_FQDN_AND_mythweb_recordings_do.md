---
title: "mythweb error about FQDN? AND mythweb recordings do not exist?"
date: 2007-06-19
forum: Server Platforms
---

### Post by dannyboy79 on 2007-06-19
I am getting this when I try to start apache2

 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

this is my hosts file:

127.0.0.1 localhost localhost.localdomain UBUNTU.getmyip.com UBUNTU
#127.0.1.1 UBUNTU.getmyip.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.4 WINXP
192.168.0.5 XUBUNTU-FIESTY
192.168.0.3 UBUNTU

What can I do to resolve this? Yes I do have my FQDN registered with dyndns.com. 

Second issue. WHen I do access mythweb from my browser on the internal network, when I click on a recorded program, this is what I get:
1029_20070619013000.mpg does not exist in the recordings directory.
BUT when I look in that directory, it's there. How would I solve this as well?

---

### Post by dannyboy79 on 2007-06-20
bump...

NOt to mention the few guides that I have tried to follow haven't worked for "securing mythweb". I was really surprised that the User Docs for Ubuntu Mythweb were wrong, shouldn't these be correct? So if anyone can link to a guide for securing mythweb, that actually work in feisty and have the samecorrect file names and locations, than I would be very grateful!

---

### Post by dannyboy79 on 2007-06-21
another polite bump. is this is the wrong section maybe?

---

### Post by Calash on 2007-06-21
I get the same errors as you do, however it does not cause any problems with my mythweb.  There is a post somewhere that says it is not a major issue and can be ignored.  Not sure how to clear the error out, but things work fine with it there.

The second issue is probably due to the links in the /var/www/mythweb/data directory.  Check that the "Recording" link is pointing to where you set MythTV to record the information.


The path may be off....I am not at my computer atm.

---

### Post by dannyboy79 on 2007-06-21
> **Calash said:**
> I get the same errors as you do, however it does not cause any problems with my mythweb.  There is a post somewhere that says it is not a major issue and can be ignored.  Not sure how to clear the error out, but things work fine with it there.

The second issue is probably due to the links in the /var/www/mythweb/data directory.  Check that the "Recording" link is pointing to where you set MythTV to record the information.


The path may be off....I am not at my computer atm.


well my mythweb works internally as well, except for the recordings not being there but I am wondering if mythweb will work frmo outside the lan? the only reason I didn't forward the ports yet in the hardware firewall is because I am not sure if I have secured mythweb yet. Does your mythweb work despite you getting this same about error about determining the FQDN? 

I have checked the /var/www/mythweb/data directory, it does contain a recordings symlink but it points the default mythtv recordings location, which I think was /var/lib/mythtv/recordings. So, yes, you're right, that's wrong. BUT I did try to fix it by doing ln -s recordings /media/400gb/mythtv BUT that didn't work, because the recordings symlink within /var/www/mythweb/data still points to the default mythtv location??? I think I have some kind of nasty loop because there's symlinks within symlinks and I actually found duplicate recordings. Some are in the /media/400gb/mythtv folder and some are in the /var/lib/mythtv/recordings folder (i think this is the default maybe)

 so needless to say I have some symlink issues as well as another issue that I am not even sure how it happened. Why would recordings be within the default location (/var/lib/mythtv/recordings) if that's not even set like that within the backend? Don't know if this is relevant but I am using the mythrename.py, I am using the --link option within roots crontab which runs every 30 minutes so that it merely puts a symlink to a readable filename within the /media/400gb/mythtv/readable-recordings folder. You know, I also tried to set up mythtranscode so that the commercials would be transcoded out but leave it as a .mpg as space isn't an issue for me (I have 2tb's)? I wonder if for some reason the files within /var/lib/mythtv/recordings are the transcoded ones without commercials? I'll have to check that out when I get home.

If you're mythweb works for you outside your lan, can you paste your /etc/hosts file? also inform me if you have anything special in your resolve.conf file (if that matters) as well as can you please paste the output from 
ls -la /var/www/mythtv/data
then if there's a folder within that called mythtv, can you ls -la that folder as well? I just want to see the symlinks and what not. Also, I can understand why mythweb would say files didn't exist if the symlinks were messed up but why am I getting tons of autoexpire errors? The log is saying the same thing, that it isn't going to autoexpire anything because the file doesn't exist? BUT in actuallity it does, it's a duplicate but it does? I just realized that there's duplicates last night and had to go to bed right away due to getting up at 3:45 every morning.

If you could provide anymore help I would greatly appreciate it. I just started using mythtv and I have many questions. Hopefully you'll be able to answer them if you wouldn't mind.

---

### Post by dannyboy79 on 2007-06-26
bump. Anyone, please help.

---

### Post by Wardazo on 2007-06-26
> * Forcing reload of web server (apache2)... apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName



If you edit /etc/apache2/apache2.conf to include:

```
ServerName [servername]
```

The error message should go away. You'll also have to restart apache. Servername can be your hostname or a FQDN.

---

### Post by dannyboy79 on 2007-06-26
thank you, i looked in the file and I don't see that option anywhere, where do suggest I add it. Also, I am to put the FQDN correct?

I was wondering if you could help me with mythweb, no one seems to be able to help me secure my mythweb and get it working. The first issue is even being able to access it once I secure it, then the next issue is the symlinks are all screwed up I am guessing because I am using a NON default recordings folder location. Here's the link if you could please help:
[http://ubuntuforums.org/showthread.php?t=467639&page=2](http://ubuntuforums.org/showthread.php?t=467639&page=2)

---

### Post by Wardazo on 2007-06-26
Just insert the ServerName on a new line at the end of the file. Actually it can go on any line, but itis always a good idea to keep cong edits together. 

> Also, I am to put the FQDN correct?

Yes. Or you can use your hostname. You can use the hostname command to find your host name.

Don't forget to restart apache using

sudo /etc/init.d/apache2 reload

---

### Post by dannyboy79 on 2007-06-26
could you please try to assist me with mythweb security? I would really appreciate that. I have already tried this tutorial with no success: [https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb)
I have a thread already here: could you please assist there?
[http://ubuntuforums.org/showthread.php?t=467639&page=2](http://ubuntuforums.org/showthread.php?t=467639&page=2)

---

### Post by Wardazo on 2007-06-26
> could you please try to assist me with mythweb security?

Sure, I'll do what I can, but I must say I don't know the first thing about Mythweb... but I do about apache and your problem seems to be more apache related than Mythweb related.

So security...

Are you absolutely sure you want to have this app on the web? 

If you don't then forget about securing it. Just make sure that your firewall is blocking port 80 to the outside world.

Ok if it's going on the web then you have to password protect it. Which is what the security tutorial on [https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb) is all about. Where exactly are you having problems with it? What error readings are you getting?

---

### Post by dannyboy79 on 2007-06-26
> **Wardazo said:**
> Sure, I'll do what I can, but I must say I don't know the first thing about Mythweb... but I do about apache and your problem seems to be more apache related than Mythweb related.

So security...

Are you absolutely sure you want to have this app on the web? 

If you don't then forget about securing it. Just make sure that your firewall is blocking port 80 to the outside world.

Ok if it's going on the web then you have to password protect it. Which is what the security tutorial on [https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb) is all about. Where exactly are you having problems with it? What error readings are you getting?

i did mention that I followed that guide without success so thank you for suggesting that but I already tried it. All the details are on the other thread that I linked to, could you post there?

---

### Post by dannyboy79 on 2007-06-27
SOLVED:
add what I put in bold to your /etc/apache2/apache2.conf, I added it immediately after this line with 1 line in between the 2 entries.

ServerRoot "/etc/apache2"

**ServerName [YOUR FQDN OR HOSTNAME HERE]**

Example:
**ServerName mazda01comp**

Your hostname can be found by entering hostname at the command line. If you have a FQDN, you'd know it as you're using dyndns or similar.

---


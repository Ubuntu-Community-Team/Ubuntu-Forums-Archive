---
title: "Postfix/hostname problems"
date: 2008-05-03
forum: Server Platforms
---

### Post by R.Bucky on 2008-05-03
I am having a problem configuring postfix. I recently worked through setting up my hostname file. I ended up with: 
127.0.0.1 mark.buckyspalace.net

I installed postfix using apt-get, go through the configuration, and the install comes back with errors saying:
> Running newaliases
newaliases: warning: valid_hostname: invalid character 32(decimal): 127.0.0.1 mark.buckyspalace.net
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 127.0.0.1 mark.buckyspalace.net
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 75
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

What ideas do you have for a hostname fix, or is there another possible issue?

Mark

---

### Post by RWells on 2008-05-03
Hi, 
Im not really offering an anwser here, as I am a complete neoob.

I have just recently installed ubuntu server 8.04 and when it asked for the hostname it quite clearly stated that the host name is to be a single word?

I dont think you need the ip in the hostname file.
If it were me I would try it with just buckyspalace.net. with no ip.

---

### Post by R.Bucky on 2008-05-03
I too am new to networking. I recently changed my hostname to bucky-desktop. I now have to use the root shell to copy my backup,as I have lost the sudo ability. Second time today.

Would you mind sharing your /etc/hostname to use as a template. I am a cat's hair away from starting all over again!

---

### Post by RWells on 2008-05-03
> **R.Bucky said:**
> I too am new to networking. I recently changed my hostname to bucky-desktop. I now have to use the root shell to copy my backup,as I have lost the sudo ability. Second time today.

Would you mind sharing your /etc/hostname to use as a template. I am a cat's hair away from starting all over again!

rwells.net 

is the only thing in my hostname file

my hosts file

127.0.0.1 rwells.net
127.0.0.1 rwells.info
127.0.0.1 rusty.selfip.info



This is working so far, I have all of my virtual hosts.

---

### Post by R.Bucky on 2008-05-03
Interesting. You do not have the 127.0.0.1 anywhere in your files. I appreciate the help.I am currently downloading, via torrent, Hardy server edition. I installed my server the hard way from the 7.10 desktop edition and then upgraded. The upgrade is what caused all of this mess. 

Ok, i admit. I may have had something to do with it!

---

### Post by RWells on 2008-05-03
> **R.Bucky said:**
> Interesting. You do not have the 127.0.0.1 anywhere in your files. I appreciate the help.I am currently downloading, via torrent, Hardy server edition. I installed my server the hard way from the 7.10 desktop edition and then upgraded. The upgrade is what caused all of this mess. 

Ok, i admit. I may have had something to do with it!


No there is no ip in the hostname file and only one name "rwells.net"

I cant help you with the mail, as I have not set mail up on my server, but I can say that I went down a very simular path as you are, before I figured it out.

I started with 7.10 some time last week and then did a complete install with Hardy 8.04, and I had h### geting my Nvidia card to work.

Rusty

---

### Post by Dr Small on 2008-05-03
The hostname for my Postfix server is in /etc/mailname

---


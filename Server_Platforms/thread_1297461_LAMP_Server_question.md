---
title: "LAMP Server question"
date: 2009-10-21
forum: Server Platforms
---

### Post by stlouis1 on 2009-10-21
I have a quick question, at least I think its a quick question. I tried posting this question on the Arch forums, a week ago, bumped it once or twice, no reply. and the ubuntu community is just so much bigger, and lets be honest, its ubuntu, novice type questions aren't always well received on the arch forums. but I am running Arch, but really, for this question, linux is linux


so here's the scenario,

I setup a lamp server last week. I wanted to try something new. turned out, that wasn't enough, so i registered a DNS, and now its online. then since i'm no web designer, i cheated, with joomla. Then the SQL database crapped out. so I decided I kind of liked having a place to blog my stuff, and put my pictures, and hopefully the phpbb forum i put up will get put to use as an alternative forum for the local MR2 club, since our other forum goes down constantly. This lead me to build a dedicated server, and i did

now my new server is setup in a rather default way, the website is stored in /srv/http, folder permissions are given to an http user, in an http group. very plain. now i need an ftp server, to manage it remotely from my other machine, but what i need is an ftp server that can be put in that http user group, so as not to mess up permission.

suggestions?



oh, and one more quick question, i can't seem to get cookies working properly, i think everything is setup, but my message board won't save my password. could use some input on that one, for what to look for, or what i might be missing. but I mainly need suggestions for an FTP server right now, thats priority

thanks, sorry for the long post, i talk to much ;)

---

### Post by spiderbatdad on 2009-10-21
I would reccomend openssh for remote administration. And yes you can create the same group name.
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
Also consider an easy to use application like fail2ban to limit unwanted attacks by banning intruder ip addresses. There are more advanced ways, but I have found this program to work quite well.
Once you have openssh, you can also connect graphically through the connect to server utility, for simple file transfers.

---

### Post by stlouis1 on 2009-10-21
that seems like a lot of effort for a machine thats right next to me. thats why i was only looking for ftp, i might just use vfs though. trying to figure out my options. its the permissions im worried about, right now everytime i copy a file in there off my flash drive, i have to manually change the owner and group permissions on teh file, thats mainly what im worried about. 

especially if i copy a modified css template for example to server to change the theme in phpbb, then if i want to log into PHPBB's admin panel and tweak one line in that theme, it can't write to it, unless i set the permissions manually. so whatever way i transfer files over, i need that folder tree to retain the http group permissions

---

### Post by stlouis1 on 2009-10-22
just for an update. I ended up using vsftpd. and made a user with the home folder in /srv/ftp and tossed a symlink in there to the /srv/html. i also had to change umask settings for vsftpd so that i could still manage files remotely outside the ftp client through my site control panel.

i can't say i like the way its set 100%, but its almost exactly what i wanted anyway, so maybe a little more tweaking and it will be up to par for me.

---


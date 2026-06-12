---
title: "apache and dokuwiki"
date: 2006-05-30
forum: Server Platforms
---

### Post by stubby on 2006-05-30
Hello, I'm trying to setup a wiki for xubuntu, running it on my own server.

I installed apache (apt-get) and dokuwiki (deb from website) and everything seems to be running ok.

When I goto [http://localhost/dokuwiki/](http://localhost/dokuwiki/) it loads up just fine.

However what I want of course is for it to be accessible over the net. I've already got a domain name so I wondering how do I configure apache to work.

This is the first time i've install apache, so have no idea what I'm doing. I am fairly comfortable with editing files and what not.

---

### Post by nabberuk on 2006-05-30
you will need to change the dns of your domain name to point to the ip address (that your isp gives you)of you server. 

If you have a static isp then use that ip, if you have a dynamic ip, then use a service like no-ip.com

hope this helps
nath

---

### Post by stubby on 2006-05-30
Yup i'm using zonedit atm so that's not a problem. 

it's more the configuration i'm wondering about. it shows up fine on [http://localhost/dokuwiki](http://localhost/dokuwiki), but how do i make it so that it shows up when i type in [http://mydomain/dokuwiki](http://mydomain/dokuwiki) ?
*unresolved*

another thing thing, which might be the underlying problem, is that i created a dummy index.htm file in /var/www and it shows up fine in localhost/index.htm. When I do mydomain/index.htm though, shows up blank. Any suggestions ?
*FIXED* forgot to port forward 80 on my router...

---


---
title: "Issues with Glype and cURL"
date: 2009-02-04
forum: Server Platforms
---

### Post by Skyride on 2009-02-04
Hey guys.

Got an unusual one here. My school currently blocks an obscene amount of websites (im talking about lots of genuinely useful things also, for example google images being blocked is a huge issue for when we are doing product design and display pieces) so I thought I would run an HTTP proxy on my home server (Ubuntu Server 8.10 with X installed).

After a bit of googling and speaking to various people i decided glype would be the best one to use. So I downloaded it, uploaded it to a folder in apache and went to configure it using the admin.php file. There was a notification telling me that cURL was not installed so installed via apt-get and yet it still reports the file does not exist. Does anyone have any clue as to why this might happen?

Thanks, Adam

---

### Post by HermanAB on 2009-02-04
It may want a different library version, or it may want it to be in a different place.  You can investigate the issue using 'ldd'.  Read the man page for details.

BTW, you may find it easier still to use ssh as a socks proxy.

Cheers,

Herman

---

### Post by Skyride on 2009-02-06
I just used the normal package in the ubuntu repo. I can't use SSH as a socks proxy for a couple of reasons.

1. Im talking about doing this from the school computer which are all XP machines where we cannot edit IE's socks info (although i guess Firefox on a pen drive may work).
2. SSH is blocked on the school computers. I tried to do it from my laptop and got the message in terminal "Websense does not allow SSH connections".

Although I found another alternative PHP proxy called "bblocked". Annoyingly though my server has developed an annoying issue where it can't make up its mind which NIC it wants to run Apache on :\ (With all the port forwarding annoyances ensuing). I only have 2 NIC's because I have my XP VM which runs a game server configured to use a certain interface.

---

### Post by R.Bucky on 2009-02-07
have you tried the ```
sudo apt-get upgrade
```i installed a Glype proxy last week on my 9.04 Ubuntu box with a genuine plug-n-play. also, did you install **php5-curl** or just **curl**?

---

### Post by Skyride on 2009-02-07
> **R.Bucky said:**
> have you tried the ```
sudo apt-get upgrade
```i installed a Glype proxy last week on my 9.04 Ubuntu box with a genuine plug-n-play. also, did you install **php5-curl** or just **curl**?

Ah, that'll be the problem. >_<

I only installed curl, not php5-curl

Oh well, Thanks mate

---

### Post by hyper_ch on 2009-02-08
how is it blocking those sites? Maybe it would be sufficient enough to change your dns servers to opendns?

---

### Post by elvinooi on 2010-08-06
well... u need to install **php5, php5-curl **and** curl, **after that restart apache2[B].
[/B]

---


---
title: "Firewall?"
date: 2010-03-29
forum: Security
---

### Post by Nisal on 2010-03-29
what the best firewall available to ubuntu ?and still is there any possibility that RAT can get infected via WINE ?

---

### Post by shebaw on 2010-03-29
I use firestarter, I don't know if it's the best but I've heard that the default settings in Ubuntu are pretty much secure, and regarding your question about running malwares in WINE, check this link out
[http://www.linux.com/archive/feature/42031](http://www.linux.com/archive/feature/42031)

---

### Post by Nisal on 2010-03-29
ok i installed firestarter is there anymore ideas ?

---

### Post by a.walker on 2010-03-29
> **Nisal said:**
> ok i installed firestarter is there anymore ideas ?

Read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") at the top of the Security Discussions forum. If you're not going to run a server, just keep your computer up to date and you should be good. Oh, and don't run VNC (the remote desktop).

---

### Post by CharlesA on 2010-03-29
> **shebaw said:**
> I use firestarter, I don't know if it's the best but I've heard that the default settings in Ubuntu are pretty much secure, and regarding your question about running malwares in WINE, check this link out
[http://www.linux.com/archive/feature/42031](http://www.linux.com/archive/feature/42031)

As far as I know, Firestarter is not longer under development, it would be better to use GUFW (graphical frontend to UFW).

---

### Post by Nisal on 2010-03-29
> **CharlesA said:**
> As far as I know, Firestarter is not longer under development, it would be better to use GUFW (graphical frontend to UFW).

well i found this command while i was googling but it seems it not working 

```
sudo apt-get install gufw
```

---

### Post by uRock on 2010-03-29
GUFW is great. I use it. GUFW is the front end for UFW. I usually just use command line to turn it on and off as needed. ```
sudo ufw enable
``` ```
sudo ufw disable
```

---

### Post by Nisal on 2010-03-29
> **iRock said:**
> GUFW is great. I use it. GUFW is the front end for UFW. I usually just use command line to turn it on and off as needed. ```
sudo ufw enable
``` ```
sudo ufw disable
```

huh that mean it's  pre installed in 9.10 ?

---

### Post by uRock on 2010-03-29
> **Nisal said:**
> huh that mean it's  pre installed in 9.10 ?

Yes, [UFW]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") is already there, just has to be turned on. Check out the [UFW]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") link.

---

### Post by Nisal on 2010-03-29
> **iRock said:**
> Yes, [UFW]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") is already there, just has to be turned on. Check out the [UFW]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") link.

yeah i done it hehe i thought i have to install it okay thanks dude

---

### Post by bodhi.zazen on 2010-03-29
> **Nisal said:**
> what the best firewall available to ubuntu ?and still is there any possibility that RAT can get infected via WINE ?

A better question is , 

What do you want your firewall to do.

By default there are no significant open ports, so there is nothing to firewall.

Also, Firestarter conflicts with ufw, so use one tool or the other. If you want to stay with ufw, purge firestarter.

```
sudo apt-get purge firestarter
```

---

### Post by Nisal on 2010-03-29
> **bodhi.zazen said:**
> A better question is , 

What do you want your firewall to do.

By default there are no significant open ports, so there is nothing to firewall.

Also, Firestarter conflicts with ufw, so use one tool or the other. If you want to stay with ufw, purge firestarter.

```
sudo apt-get purge firestarter
```

so if i get infected with a RAT u mean there are no way to get a effect  ? and after reading some articles i guess ufw will be enough :)

---

### Post by bodhi.zazen on 2010-03-29
What is a RAT ?
How would you be infected by a RAT ?
What makes you think a firewall will help with a RAT ? There are no open ports by default, so you are no more secure with a firewall.

Now if you install a server, such as VNC or ssh, and forward a port that is different.

---

### Post by Nisal on 2010-03-29
> **bodhi.zazen said:**
> What is a RAT ?
How would you be infected by a RAT ?

remote administration tool, and that the question im having with "Wne" is there any possibility to get infected by a RAT ?

Edit:ya i had forward a port so i have open ports

---

### Post by cariboo on 2010-03-29
You already have a remote administration tool installed by default. Make sure it is turned off by going to System->Preferences->Startup Applications, and uncheck Remote Desktop. On the next reboot, it will be disabled.

---

### Post by bodhi.zazen on 2010-03-29
> **Nisal said:**
> remote administration tool, and that the question im having with "Wne" is there any possibility to get infected by a RAT ?

Edit:ya i had forward a port so i have open ports

There are reports of viruses running in wine. So long as you do not run wine as root they can not infect your system files, but they can infect files in .wine.

I would be less concerned that you are infected by "something" in RAT and more concerned in securing RAT. In that case, a firewall is part of security, but you need so secure RAT.

---

### Post by OpSecShellshock on 2010-03-29
Well, there are remote access tools and there are remote access trojans (and in a lot of cases the only difference between the two is in who's running things on the client side). In the trojan context, it's another way of saying backdoor, except you get to turn it into an acronym which sounds more menacing in news articles and sales meetings.

A firewall won't really help you with those, though, since they initiate connections from the inside (end user's PC) to the malicious external device. Don't worry too much about those, since in Linux they aren't really a desktop issue. There's both more value and greater likelihood of success in getting them on a (poorly configured) web server. If you get one because of activity during a Wine session, it should only work while that's running (if at all). With a regular Linux desktop session you won't have sufficient permissions in anything for that to install itself automatically. You'd have to be tricked into installing it yourself, and you'd be asked for your password before it happened.

---

### Post by Nisal on 2010-03-29
> **cariboo907 said:**
> You already have a remote administration tool installed by default. Make sure it is turned off by going to System->Preferences->Startup Applications, and uncheck Remote Desktop. On the next reboot, it will be disabled.

okay il do it hope it won't be much problem

---


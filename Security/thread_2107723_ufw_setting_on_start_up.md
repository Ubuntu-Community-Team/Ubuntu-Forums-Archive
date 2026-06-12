---
title: "ufw setting on start up"
date: 2013-01-22
forum: Security
---

### Post by Grem41 on 2013-01-22
Hope somebody can help regarding ufw.
I just turn on the firewall,nothing special using terminal commands

1) sudo ufw enable tells the firewall is active and enabled on system startup
2) sudo ufw status confirms if the firewall active or inactive.

But when I reboot all those setting are lost and I have an inactive firewall, Can anyone tell me how I would be able to have the firewall active once I reboot ? 

On various forums I gathered might I needed to change start up script but I'm not sure !

---

### Post by chadk5utc on 2013-01-22
Heres a good link for you scroll about half way down look for UFW
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by leclerc65 on 2013-01-22
> **Grem41 said:**
> 
But when I reboot all those setting are lost and I have an inactive firewall, Can anyone tell me how I would be able to have the firewall active once I reboot ? 

It can't be. Click the 'Unlock' button at the bottom right (gufw).

---

### Post by und3rtug4 on 2013-01-25
> **leclerc65 said:**
> It can't be. Click the 'Unlock' button at the bottom right (gufw).

Yep, as mentioned by leclerc65, you can sudo the gufw and take it from there!

Try:

```
sudo apt-get install gufw
```
```
sudo gufw
```

and hit unlock!

From there, it could be easier for you to set up your firewall!
You can also use firestarter, wich is also a nice firewall front-end.

To install it:

```
sudo apt-get install firestarter
```

After that, it should be a launcher available somewhere on Menu -> Internet or Accessories.

To set it up to boot at startup, simply add a new entry to the startup applications(launch command needs gksudo paraphernalia :p).


Hope it helps somehow.
Props!

---

### Post by conquerorodueko on 2013-01-27
I do not recommend fire-starter... i cannot see any visible proof that it is active and functioning... have you adjusted or edited your firewall table [ufw] manually???... misconfiguration of the firewall causes it to turn itself off.

DO:
sudo ufw enable - [enables firewall] - [amended previous typo error]
sudo ufw reload rules - [verifies that all rules are configured valid]
                                              [If some rules are mis-configured ufw will cough up the error]
sudo ufw status verbose - [shows visible proof of all configuration]

*** Thanks for clarifying my typo error ***

---

### Post by cariboo on 2013-01-28
To add to what conquerorodueko said, Firestarter hasn't been fully maintained since 2005, the package maintainer has done a few bug fixes, but that's about it.

---

### Post by deadflowr on 2013-01-28
> **conquerorodueko said:**
> I do not recommend fire-starter... i cannot see any visible proof that it is active and functioning... have you adjusted or edited your firewall table [ufw] manually???... misconfiguration of the firewall causes it to turn itself off.

DO:
sudo enable ufw - [enables firewall]
sudo ufw reload rules - [verifies that all rules are configured valid]
                                              [If some rules are mis-configured ufw will cough up the error]
sudo ufw status verbose - [shows visible proof of all configuration]

Good advice.
However, your command for enabling ufw is backward.

```
sudo ufw enable
```

Running 'sudo enable ufw' will result in a command not found.

---

### Post by bodhi.zazen on 2013-01-29
Alos, UFW conflicts with firestarter, and possibly other firewalls.

So, if you installed firestarter you have to purge it.

```
sudo apt-get purge firestarter
```

If you have already removed it, you have to first re-install it and then purge.

Firestarter is not advised as it is no longer maintained. It was very popular and continues to be advised, but, imo, is just bad advice.

---

### Post by houseworkshy on 2013-01-31
With ufw one also needs to tell it what to do, so "sudo ufw default deny" would be worth doing too.  After that "man ufw" will display the manual page which would help you to fine tune, if you need to.

---


---
title: "Code to start XAMPP at login. Will this work?"
date: 2011-05-09
forum: Server Platforms
---

### Post by relic70 on 2011-05-09
I've got XAMPP installed on Lucid Desktop edition in VirtualBox and all works well.

But, one has to start XAMPP after login with

sudo /opt/lampp/lampp start

I browsed for solutions and found one simple suggestion which entails placing the startup code in the the /etc/init.d/rc.local file after the " #! /bin/sh " line.

The code being " /opt/lampp/lampp start "

Is it safe to place that code in the rc.local file? If so, should it be in any particular line?

Thanks

---

### Post by CharlesA on 2011-05-09
Why not just install the LAMP stack and install Python separately?

How are you installing XAMPP?

---

### Post by relic70 on 2011-05-09
> **CharlesA said:**
> Why not just install the LAMP stack and install Python separately?

How are you installing XAMPP?

I downloaded XAMPP from

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

and installed per their installation directives. Easy to do. And it works.

Just want to be able to start XAMPP when I log in.

---

### Post by relic70 on 2011-05-09
> **CharlesA said:**
> Why not just install the LAMP stack and install Python separately?

How are you installing XAMPP?

P.S. Excuse me, but that doesn't answer my question.

---

### Post by spynappels on 2011-05-10
Have a look at the following wiki page for help on auto starting services:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Can you run the service by using the ```
service lampp start
``` command?

> **relic70 said:**
> P.S. Excuse me, but that doesn't answer my question.

Just FYI, the reason questions like the ones posed by CharlesA are posted are to get background info, so the solution that is suggested is the best possible one. Replying as above can be seen as discourteous and will not get you more or better answers. For the record, I was going to ask the same question but CharlesA beat me to it.

---

### Post by relic70 on 2011-05-10
> **spynappels said:**
> Have a look at the following wiki page for help on auto starting services:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Can you run the service by using the ```
service lampp start
``` command?



I receive the message "unrecognized service". So, the answer is no, I cannot start lampp in that manner from the command line. 

> 
Just FYI, the reason questions like the ones posed by CharlesA are posted are to get background info, so the solution that is suggested is the best possible one. Replying as above can be seen as discourteous and will not get you more or better answers. For the record, I was going to ask the same question but CharlesA beat me to it.

I accept the admonishment.

---

### Post by spynappels on 2011-05-10
You could use the @reboot flag in Cron. You will need to edit the root crontab
```
sudo crontab -e
```
add the following line
```
@reboot /opt/lampp/lampp start
```
and save.
This should run the command after every reboot. I haven't tested this on a recent version, so you may just have to check whether it does actually do what you want it to.

---

### Post by relic70 on 2011-05-10
> **spynappels said:**
> You could use the @reboot flag in Cron. You will need to edit the root crontab
```
sudo crontab -e
```
add the following line
```
@reboot /opt/lampp/lampp start
```
and save.
This should run the command after every reboot. I haven't tested this on a recent version, so you may just have to check whether it does actually do what you want it to.

Thanks spynappels, that method is working. The XAMPP page shows up with [http://localhost/xampp](http://localhost/xampp) in the browser window after a new login.

---

### Post by spynappels on 2011-05-10
> **relic70 said:**
> Thanks spynappels, that method is working. 

Great! You're welcome. If you want to set this up again, it may be easier to use ```
sudo tasksel
``` and select LAMP and then install Python separately from the repositories, as CharlesA suggested. This means that the services are configured to start automatically and makes it easier to add security patches also.

---

### Post by kennad on 2012-12-19
> **spynappels said:**
> You could use the @reboot flag in Cron. You will need to edit the root crontab
```
sudo crontab -e
```add the following line
```
@reboot /opt/lampp/lampp start
```and save.
This should run the command after every reboot. I haven't tested this on a recent version, so you may just have to check whether it does actually do what you want it to.

Worked GREAT. Thanks and have a Merry Christmas!

---

### Post by spynappels on 2012-12-22
You're welcome!

---


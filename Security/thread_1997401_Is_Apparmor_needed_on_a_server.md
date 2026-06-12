---
title: "Is Apparmor needed on a server?"
date: 2012-06-05
forum: Security
---

### Post by kramer65 on 2012-06-05
Hello,

I was building my own server using [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3") from howtoforge. At one point the [guide says]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3") the following:

> **Disable AppArmor**
AppArmor is a security extension (similar to SELinux) that should provide extended security. **_In my opinion you don't need it to configure a secure system_**, and it usually causes more problems than advantages (think of it after you have done a week of trouble-shooting because some service wasn't working as expected, and then you find out that everything was ok, only AppArmor was causing the problem). Therefore I disable it (this is a must if you want to install ISPConfig later on).

We can disable it like this:

```
/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
apt-get remove apparmor apparmor-utils
```

It seems a bit awkward to me though. I am far from an expert, but I would say that apparmor is not made for nothing.

So my question to you; do you think this makes sense? Or are they just saying it because apparently the ISPConfig panel (which is built by the writer of the guide) is not working with Apparmor?

All tips and insights are welcome!

---

### Post by zombifier25 on 2012-06-05
> **Disable AppArmor**
AppArmor is a security extension (similar to SELinux) that should provide extended security. [size=6]In my opinion[/size] you don't need it to configure a secure system, and it usually causes more problems than advantages (think of it after you have done a week of trouble-shooting because some service wasn't working as expected, and then you find out that everything was ok, only AppArmor was causing the problem). Therefore I disable it (this is a must if you want to install ISPConfig later on).

We can disable it like this:

```

/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
apt-get remove apparmor apparmor-utils

```

Yep.

---

### Post by Ms. Daisy on 2012-06-05
No, it's not made for nothing.  The [Apparmor Wiki]("http://wiki.apparmor.net/index.php/Main_Page") says:

> AppArmor is an effective and easy-to-use Linux application security  system. AppArmor proactively protects the operating system and  applications from external or internal threats, even zero-day attacks,  by enforcing good behavior and preventing even unknown application flaws  from being exploited. AppArmor security policies completely define what  system resources individual applications can access, and with what  privileges. A number of default policies are included with AppArmor, and  using a combination of advanced static analysis and learning-based  tools, AppArmor policies for even very complex applications can be  deployed successfully in a matter of hours.  You can also read Bodhi.Zazen's tutorial on [Apparmor]("http://ubuntuforums.org/showthread.php?t=1008906"), too. 

I would recommend it for a web server that faces the internet.  The link you posted doesn't say that Apparmor conflicts with ISPConfig. The way I read it is that the author wasn't able to properly configure Apparmor with ISPConfig.

---

### Post by kramer65 on 2012-06-05
@zombifier25
Do you mean "*yep, it's just his opinion*", or "*yep, it is also my opinion*"?

@Ms. Daisy
Thanks for that, I was already thinking in that direction. So I will need to learn how to use Apparmor in order to create a working profile for ISPConfig. Since ISPConfig is built to control many things in the server, I wonder whether building this profile for ISPConfig isn't veryhard (I guess I need to give it **_a lot_** of permissions?).

I will go through your links and see how far I can come.

If you have any more tips they are more than welcome!

---

### Post by zombifier25 on 2012-06-05
The "Yep" is my response to your question. AppArmor is needed if you want your system to be secure. It may be a PITA to set up as first, but when you're done, it's really safe.

---

### Post by kramer65 on 2012-06-05
> **zombifier25 said:**
> The "Yep" is my response to your question. AppArmor is needed if you want your system to be secure. It may be a PITA to set up as first, but when you're done, it's really safe.

Alright. I'll go readup myself in Apparmor. Once I get to actually building a profile I'll possibly ask the developer of ISPConfig as well to help out. I guess it's to his and everyone's advantage as well.. :-)

Thanks for the info!

---


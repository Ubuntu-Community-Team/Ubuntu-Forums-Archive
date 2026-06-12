---
title: "Can one see what software installed a 'service' ?"
date: 2010-06-29
forum: Server Platforms
---

### Post by grpace on 2010-06-29
Still new to Ubuntu.

32-bit was given to me.  I used it, and decided to go to 64-bit.  I had to start all over again...  But that's OK.

However, it seems that a software package has installed apache2 and mysql as a service that starts every time the the machine starts.

When I went to 64-bit, one of the 1st things I did was install XAMPP.  It worked well and started 'on demand' without complaining.

Then I installed more packages.
Somewhere along the line, one of these packages has set apache2 and mysql as a service.

I thought it was Drupal.  While installing Drupal, it asked me for a password for user 'root' on the database... It was the only install going at the time.

Drupal insists their scripts don't do this.
But I KNOW it asked for it.

Is there a way to see what package installed these 'services' that start upon boot-up ?
Is there a way to get rid of the 'service' upon boot ?

grpace

---

### Post by GreenN00b on 2010-06-29
If you installed drupal from synaptic or using apt-get it installed apache2 too. Mysql server is now marked as recommended dependency so it probably was installed too.
You can remove them using synaptic or apt-get.

---

### Post by GreenN00b on 2010-06-29
To disable service startup you can try using update-rc.d.

---

### Post by arrrghhh on 2010-06-29
You should see all your startup scripts in /etc/init.d

However, they changed the way the startup system works - instead of doing "/etc/init.d/apache2 restart" you simply do "service apache2 restart".

I'm hoping that all the startup scripts are still in the same place and they didn't put them in more than one place... Someone chime in if they did please!

Oh, and to remove or add a script you use the update-rc.d command that GreenN00b spoke of earlier.

---

### Post by cpplinux on 2010-06-29
You can try bum from synaptic.

---


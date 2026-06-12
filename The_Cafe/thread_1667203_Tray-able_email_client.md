---
title: "Tray-able email client?"
date: 2011-01-14
forum: The Cafe
---

### Post by kevin11951 on 2011-01-14
Not sure what happened to my other thread, but Ill try again:

I am sick of dealing with the Evolution/Alltray combo, and am looking for a different email client that is tray-able...  

It would be nice if the tray icon would change when mail has arrived.

kMail looks like an option, but I prefer GTK apps...

---

### Post by juancarlospaco on 2011-01-14
Not sure what happened to your other thread, but again:

Fill the Bug

---

### Post by Primefalcon on 2011-01-14
Try cloudSN I know it's not what you want, but it is really really nice and integrates very nicely.

[http://chuchiperriman.github.com/cloud-services-notifications/](http://chuchiperriman.github.com/cloud-services-notifications/)

---

### Post by Primefalcon on 2011-01-14
triple post due to lag

---

### Post by Primefalcon on 2011-01-14
triple post from forum lag

---

### Post by Viva on 2011-01-14
Thunderbird has a minimize to tray addon.

---

### Post by koleoptero on 2011-01-14
Sylpheed can minimize to the tray too, and check for mail periodically if you want, and notify you of new mail.

---

### Post by forrestcupp on 2011-01-14
> **Viva said:**
> Thunderbird has a minimize to tray addon.

+1  That's what I use.  You just have to install the addon.

Thunderbird with Lightening is just as complete as Evolution.

---

### Post by juancarlospaco on 2011-01-14
triple reply is becoming a trend...

---

### Post by kevin11951 on 2011-01-14
> **Viva said:**
> Thunderbird has a minimize to tray addon.

I am using it now, thanks...

Does it change when new mail arrives?

---

### Post by uRock on 2011-01-14
You can use Alltray in the repos and it will put just about anything in the tray.

---

### Post by kevin11951 on 2011-01-15
I have run into a problem with Thunderbird...

I can't tell when I have new mail, because the icon doesn't change...

---

### Post by Pogeymanz on 2011-01-15
I use claws-mail, which is a fork of sylpheed, and almost identical.

Its icon in the tray changes from three possibilities: You have no new/unread mail, you have unread mail that is not new, you have new mail.

It's a lot lighter than Thunderbird.

---

### Post by the.ciscokid on 2011-05-29
> **kevin11951 said:**
> I have run into a problem with Thunderbird...

I can't tell when I have new mail, because the icon doesn't change...

I found this thread when searching for a solution... apologise to digging up an old thread, but I thought I would post my set up in case it helps any one... (I am running 10.04)

1/ Download and install thunderbird 
2/ Search for the add-on "MinimizeToTray revived" and add it (tools > add-ons).  Reload as instructed.
3/ Now, follow [[COLOR="Red"]this[/COLOR]]("http://ubublogger.wordpress.com/2010/02/02/how-to-install-the-experimental-version-of-libnotify-mozilla/") blog post to build the latest .xpi for the notifier yourself, or go [[COLOR="Red"]here[/COLOR]]("https://launchpad.net/libnotify-mozilla/+download") and download one which was already created (but it might be a little older).
4/ Finally, I had to download "libnotify-bin" from the software centre - or you can use:

```
sudo apt-get install libnotify-bin
```

---

### Post by Fedz on 2011-05-29
I've noticed & it's just as simple to when evolution is open have it in a different workspace & when new email arrives it shows a different icon in the workspace switcher - easy :)

---


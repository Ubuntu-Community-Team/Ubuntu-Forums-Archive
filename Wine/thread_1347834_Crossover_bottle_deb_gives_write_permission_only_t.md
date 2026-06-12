---
title: "Crossover bottle deb gives write permission only to root?"
date: 2009-12-06
forum: Wine
---

### Post by Cenoforums on 2009-12-06
Hi,

In a effort to organize my windows app installs, I tried to export crossover bottles as debs and install them that way. it works, but the bottle files are readonly for my user, hence I need to run the app as root to have write permissions. I changed the permissions manually and it works ok, but it's quite the workaround.
Does anyone know how I can overcome this? I was thinking of editing the deb file directly, as a workaround I could change the permissions in the postint script but I honestly don't know how to do this.

I can up the deb if someone wants to have a look.

---

### Post by beastrace91 on 2009-12-06
Why is manually changing the permissions to your user a big deal? Its one command in terminal: ```
sudo chown -R myuser .
```

Regards,
~Jeff

---

### Post by Cenoforums on 2009-12-06
It's not a big deal, it's just silly that I have to do that to every application on every machine I want to install. I'd rather have the deb install properly and not have to worry about anything. I'm sure editing the deb is really simple for someone who understands how it works, I tried looking into it but damn

---


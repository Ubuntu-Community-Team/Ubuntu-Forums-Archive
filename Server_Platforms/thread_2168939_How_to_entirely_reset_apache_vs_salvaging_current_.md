---
title: "How to entirely reset apache vs salvaging current instance"
date: 2013-08-20
forum: Server Platforms
---

### Post by Roasted on 2013-08-20
I was trying to set up SSL with apache on Ubuntu server 12.04.2. I admittedly am not entirely confident in configuring apache and I've never set up SSL before. I'm afraid that now that I've tinkered with it so much and I'm still getting no where that improper configs in who knows what directory could be playing a key factor. So, question... How do I entirely from ground up reset apache so it's like it was with a fresh install? Or... Is that crazy talk... And maybe I'm closer than I think and possibly over complicating it? Just curious on what the experts think... Thanks!

---

### Post by TheFu on 2013-08-20
I think this should work.

```
sudo dpkg --get-selections | grep apache* > ~/my_apache_pkgs.txt
sudo apt-get purge apache*
sudo dpkg --set-selections < ~/my_apache_pkgs.txt
sudo apt-get install -f
```

Not certain about the last command - might be different, but you'll have all the previously installed apache-whatever packages listed inside the APT system, so getting them reinstalled easy.

I'd also recommend that you get in the habit of making backups or using a code version control system for things like this in the future, if an automatic nightly backup is not enough.

---


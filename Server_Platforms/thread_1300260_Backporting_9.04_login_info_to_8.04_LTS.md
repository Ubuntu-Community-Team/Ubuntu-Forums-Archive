---
title: "Backporting 9.04 login info to 8.04 LTS"
date: 2009-10-24
forum: Server Platforms
---

### Post by mdlueck on 2009-10-24
Greetings-

When I login via SSH to an Ubuntu server 9.04 box, I am presented with some useful stats: CPU / memory / etc load, and also the number of packages needing updating.

Specifically the packages needing updating, which script is that performed by, as I would like to back-port that functionality to 8.04 LTS for my own sanity.

Suggestions / comments anyone?

Thanks,
Michael

---

### Post by scorp123 on 2009-10-25
I think the package you're after is **"update-motd"** ... It was introduced in "intrepid" (8.10). No idea if it would work on "hardy" (8.04 LTS)

---

### Post by mdlueck on 2009-10-25
Thanks scorp123: Indeed the resource utilization does seem to come through via that way. The package update status, however, does not seem to come via that method.

Getting closer! :-)

Any further suggestions on finding where the package update status comes from?

Thanks!

---

### Post by kevin11951 on 2009-10-25
If you want your server to auto update for you, then:

```
sudo crontab -e
```
then type 3, then <enter>.
```
@daily apt-get update; apt-get upgrade --force-yes -y
```
save by typing <ctrl>+"x", then "y", then <enter>

this will check for updates, and then upgrade every night at midnight.

[COLOR="Red"]Keep in mind, i have no idea what kind of havoc this could cause[/COLOR], I just do this so I dont have to worry about upgrading every day.

---

### Post by mdlueck on 2009-10-25
Greetings kevin11951: I am not looking to achieve auto-update, rather just expedite finding out if I need to apply an update.

I find the notification upon logging in to SSH quite helpful, so wish to discover where it comes from, in hopes to implement the same on 8.04 LTS.

Sincerely,

---


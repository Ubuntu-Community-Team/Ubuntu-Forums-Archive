---
title: "Autoinstall security updates"
date: 2006-09-25
forum: Server Platforms
---

### Post by ahlt on 2006-09-25
Is it possible to autoinstall important security updates?

Or if not, how could I solve my "root-problem" for an prospective script for that purpose? The script would need the root password, but I would rather not store that password in a file on the server...

---

### Post by kidders on 2006-09-25
I wonder what you would think of using cron to periodically do an **apt-get update && apt-get upgrade**, say, once a week. Having cron do the job as root would avoid the need to store your password anyplace silly, too.

---

### Post by fifth on 2006-09-25
> **ahlt said:**
> Is it possible to autoinstall important security updates?

Or if not, how could I solve my "root-problem" for an prospective script for that purpose? The script would need the root password, but I would rather not store that password in a file on the server...

Cannot remember if this applies to Dapper and previous tbh, but i'm on edgy ...

Go into Synaptic and select repos menu. Then go to the internet updates tab. There are options there to allow security updates only to be applied without confirmation.

I assume this works with the notification applet to search for updates and they will be applied in the background.

---

### Post by ahlt on 2006-09-25
Thank you very much for your replies.

---

### Post by chrisfay on 2006-09-25
> I wonder what you would think of using cron to periodically do an apt-get update && apt-get upgrade, say, once a week

This is a quick and easy solution. The only problem is the script will have to be allowed to force download any updates without you first accepting them. This is done by using:

```
sudo apt-get update
sudo apt-get -y upgrade
```

If you don't specify the 'y' flag, you won't actually upgrade anything with your script as it requires your approval. The flipside is that any and all upgrades will be automatically installed and you won't have any say in the matter; not really a good practive especially in light of the recent failed updates we've been getting.

---

### Post by kidders on 2006-09-25
Very good point. I guess you'd call it more of a hack than a solution! Emm... where's the un-post button on this thing? Hehe.

---

### Post by kakao on 2008-05-15
I know it's been some time since the initial post ;) but since it came up first in google I'd like to point out your suggestion installs everything there is from all sources you specified by sources.list (including security updates). You said yourself it's a hack :)

Is there a way to tell aptitude to use a specific sources.list, mayby from ```
/etc/apt/sources.list.d
```?

It really would be a great feature to have something in the "software sources" Dialog on the update tab...
Oh, well, sometimes it helps to open ones eyes and actually read -- on my hardy heron it says just there:
> Install security updates whithou confirmation (which will include updating the packages list so you get notified of further upgrades; I guess it triggers some optimized cron job which must include aptitude update in some way).

Now I only need to find out a way to toggle this on machines where you have no GUI or even X not installed. With X installed and sshd running you could ssh to that box and do
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```
or
```
gksu /usr/bin/software-properties-gtk
```

On a sidenote it's safer to condition the upgrade command:
```
sudo aptitude update && sudo aptitude safe-upgrade
```
so it's only been run when there were no erros updating the package list.

Edit: There is more on the topic at [Ubuntu's Security Guide]("https://help.ubuntu.com/community/AutomaticSecurityUpdates").

---


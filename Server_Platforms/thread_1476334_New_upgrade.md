---
title: "New upgrade"
date: 2010-05-07
forum: Server Platforms
---

### Post by josh.pbh on 2010-05-07
Today I upgraded from 9.10 to 10.04 through a do-release-upgrade line. It all went well, took about an hour. When the server restarted though, it took a while and refused to log me (admin) or root in. Apache is running in the background, as is MySQL but Samba isn't able to access Linux users, and hence is refusing connections. I've decided to leave it off for a while (it's been on for months, only restarting once a week!). Does anyone know of this problem and have a solution? Or any suggestions? If it makes any difference, the admin user was running an encrypted LVM.
This is my first post, by the way, so be gentle ):P
Thanks guys (and girls, I guess!),
Joshhy

---

### Post by Vegan on 2010-05-07
When I upgraded I use a CD, but I backed up the server folders first and made sure it was working before I restored the folder and brought it back up.

---

### Post by josh.pbh on 2010-05-08
After hours of trying, I've decided the console is never letting a user log in. root and josh , the users, both time out, but using an incorrect user name or pass flags up as incorrect login. I'm seriously confused...
Thanks

---


---
title: "Updating Script help needed"
date: 2005-06-25
forum: Repositories &amp; Backports
---

### Post by jimcooncat on 2005-06-25
Making a little script to update my (currently) three Ubuntu machines. Could use some feedback on making it better. One thing I'd like it to do is to not "apt-get update" if it's already done so in the last x hours. But any suggestions for improvement are appreciated!


```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
echo switching to plugged-in laptop
ssh jim@laptop "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade"
echo switching to work email server
ssh jim@lan.example.com "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade"
```

---

### Post by intangible on 2005-06-27
Maybe look into "cron-apt", it seems to do what you want already.

---


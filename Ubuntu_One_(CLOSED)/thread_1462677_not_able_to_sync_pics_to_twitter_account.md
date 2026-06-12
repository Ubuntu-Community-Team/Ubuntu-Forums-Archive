---
title: "not able to sync pics to twitter account"
date: 2010-04-26
forum: Ubuntu One (CLOSED)
---

### Post by frankyboy1211 on 2010-04-26
Hello, I saw a funny video, about how you can select a jpeg and sync it with ubuntu, and then copy the url to your twitter account. Only on my system the option copy url is just not there, so maybe I missed some software installment. Can anyone help me?


grtz. Frank

---

### Post by duanedesign on 2010-04-26
I love that video :)

That option is available on newer versions of Ubuntu One. The version in the Beta/PPA and in Lucid has this option. You can run the following to see what version you have installed

```
dpkg -l ubuntuone-client
```

If it is version 1.0.3 or older you wont have this option. You can install the newer version in Karmic with the following:

```
sudo add-apt-repository ppa:ubuntuone/beta && sudo apt-get update && sudo apt-get upgrade
```

keep in mind that the newer versions do not have the applet. It was replaced by the Ubuntu One Preferences. In Karmic that would be accessed by going to System > Preferences > Ubuntu One

---


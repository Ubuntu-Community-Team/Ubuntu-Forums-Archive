---
title: "Ubuntu 7.10 Server, Can I install a Gui?"
date: 2007-12-18
forum: Server Platforms
---

### Post by Brendan Hart on 2007-12-18
If so what is the command?

---

### Post by seshomaru samma on 2007-12-18
I think you need to enable the universe\multiverse repos
```

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
```



then
```
sudo /etc/init.d/gdm start
```

---

### Post by Brendan Hart on 2007-12-18
what is the gdm one.

I like to know what im installing before I do stuff

---

### Post by seshomaru samma on 2007-12-18
gdm will give you a graphic login screen
you don't really need it
you can start the GUI with the command:
```
startx
```

---

### Post by now-new on 2007-12-18
I had a simmilar problem as you my friend because I am still a little dumb working with comand line all the time, so I installed webmin 1.37 which is not really a GUI but can help you picture yourself where things are and how you are going to move them.

and if you want you can use a laptop and configure it from anyplace you want.

I just finished so that's why I am telling ya.
I just need to know how to configure my mail,,, I think I got it configure ok but I dont know how to open an account and start getting emails

if you know anything let me know
any questions let me know....

---

### Post by Brendan Hart on 2007-12-18
I think I will do webmin! because its not like I´ll need interface for anythign else

---


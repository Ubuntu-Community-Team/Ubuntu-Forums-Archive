---
title: "total linux newb stugglin with apache permissions"
date: 2008-06-22
forum: Server Platforms
---

### Post by 03212139 on 2008-06-22
i just installed ubuntu on my machine a few nights ago. i have no linux experience.

i set up apache, php, mysql and they are all working fine. the only problem is that i can't dump any files into the www dir or save files in any of the apache dirs. it tells me i don't have proper permissions. how do i fix this?

i've researched this for a while and i just can't get anywhere. i don't want to waste time screwing around with this stuff i just want to use this machine to develop websites and then upload those files to a different server.

---

### Post by dmond on 2008-06-22
have you tried using chown or chmod?

---

### Post by ad_267 on 2008-06-22
Go to applications - accessories - terminal and run

```
sudo chmod -R a+w /var/www
```

I think you can run into problems if /var/www is not owned by www-data

If you want to edit any of the apache files you can press alt-f2 and run "gksudo gedit" and then open the files you want to edit from there.

---

### Post by 03212139 on 2008-06-22
thank you, everything works great now!

i was wondering how i could fix it so that no one could access my server. its really only supposed to be used for development and i don't want any outsiders accessing it.

also, does anyone have any suggested reading about apache and linux? i don't want to be a newb forever but i can't commit too much time to learning this either.

---

### Post by ginjabunny on 2008-06-22
there is an overview in the server guide doc at [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by ad_267 on 2008-06-22
I have apache, php and mysql set up just for development on my machine but I haven't worried about trying to prevent anyone else from accessing it. You can probably do this using firestarter which is a gui for setting up Ubuntu's built in firewall iptables.

---


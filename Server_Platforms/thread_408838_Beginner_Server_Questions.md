---
title: "Beginner Server Questions"
date: 2007-04-13
forum: Server Platforms
---

### Post by super.rad on 2007-04-13
I have a load of files i need to share with my brother, some of them being quite large. I was wondering what would be the best way to do this, is it possible to set up a small server on my computer (ubuntu edgy desktop) so that he can download the files?
My next question is which type of server would be best?
I was thinking either using ftp or torrents? I want something easy to manage and with a GUI.
Im not at home at the moment so cant install anything yet but wanted to start getting an idea about it, also if anyone has any links to how to setup these kind of things for a beginner it would be great. Thanks

---

### Post by Brazen on 2007-04-13
what is the proximity between you and your brother?  Are you in the same house, sharing on an internal LAN?  Or are you far away, sharing over the internet?

---

### Post by 95aspire on 2007-04-13
what is the other computer? is it xp or is it also ubuntu?

if its xp you can set up samba, whiche i have on dapper but i did everything with help from peeps from here.

---

### Post by jmvidalvia on 2007-04-14
I am also a begginer: some kind people helped me [here]("http://ubuntuforums.org/showthread.php?t=402403").
Good luck, 

jm

---

### Post by super.rad on 2007-04-14
Sorry should have mentioned he lives far away so would be sharing over the internet and he is also running ubuntu. Thanks

---

### Post by Frosty Cold Drink on 2007-04-14
FTP is your best bet. Its meant for this sort of thing. Don't bother with bit torrent since it only helps if you have multiple people downloading the same file at the same time.

---

### Post by super.rad on 2007-04-14
right thanks, could anyone point me in the direction of a good beginners guide to setting up ftp on ubuntu?

---

### Post by nucklebone on 2007-04-14
oops! double posted - see suggestion below. :)

---

### Post by nucklebone on 2007-04-14
I chose Proftp for a FTP server.

You can get started here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Edgy#FTP_Server)

You can find good instructions here:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6)
about mid-way down the page the FTP tutorial begins.

Good luck!

---

### Post by Brazen on 2007-04-14
I would just use ssh if I were you.  you install the server on your computer with ```
sudo aptitude -y install openssh-server
```

Then you brother just used the Connect to Server... wizard in Gnome and use your public IP address.  For added points, set yourself up with a dyndns.org account, so he can use that instead of your ip, which could change on a home account.  Also be sure tcp port 22 is forwarded from your router to your computer.

You will also have to create a user account for him to use.  Just a regular user account created in Gnome will work.  ssh will share the root partition, so restrict down that user's folder permissions if you want to restrict what you share.

---


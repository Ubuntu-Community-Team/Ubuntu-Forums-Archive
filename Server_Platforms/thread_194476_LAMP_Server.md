---
title: "LAMP Server"
date: 2006-06-11
forum: Server Platforms
---

### Post by Nyati on 2006-06-11
Hi, I installed LAMP Server 6.06 LTS but fell short at the use of the console.

I then did:

apt-get install ubuntu-desktop

This obviously installed the ubuntu-desktop distro. Initially, I did this so that I could have the GUI. 

To check that I still have my LAMP modules in place, I typed:

sudo find / -name mysql -print
sudo find / -name php5 -print
sudo find / -name python -print
sudo find / -name perl -print
sudo find / -name apache2 -print

and they're all there! GREAT!

BUT!!! How can I use these, what commands do I use? 

I would like to host my own websites and develop them on my linux machines. I do all this already on my xp machines, but want to transfer to linux machines.

Can anyone help?

I know how to use vim and create and save a file in a directory, but how do you run the module - like apache? A simple but overlooked command - I must be going mad!

---

### Post by oscar on 2006-06-11
If you installed everything correctly then apache and should be running with all of the correct modules.
Open up firefox and go to [http://localhost/](http://localhost/)
You should get the default apache page.
To write your own pages just put them in /var/www/

---

### Post by Nyati on 2006-06-11
Thanks so much, I swear I've lost my mind!:^o

---


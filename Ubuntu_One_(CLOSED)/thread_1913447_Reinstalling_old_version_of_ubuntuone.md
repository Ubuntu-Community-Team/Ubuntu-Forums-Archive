---
title: "Reinstalling old version of ubuntuone"
date: 2012-01-22
forum: Ubuntu One (CLOSED)
---

### Post by JCM_Pico on 2012-01-22
Hi there,

I was recently unpleasant with U1 taking too much time to sync files that were shared with me.... So I attempted to install the most up to date version... --> Big fail
sudo apt-add-repository ppa:ubuntuone/nightlies
The must up to date version does not have a preference menu (GUI) compatible with Ubuntu 10.04... and since I frequently used it I decided to downgrade it....
So with this objective in mind I:

1. Removed the removed the ppa from software sources 
2. Quit the Ubuntu One client
3. sudo rm -rf ~/.share/local/ubuntuone
4. rm -rf ~/.cache/ubuntuone
5. rm -rf ~/.config/ubuntuone
6. Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
7. sudo apt-get purge ubuntuone*
8. sudo apt-get install ubuntuone*

but instaed of a down grade I have it the same way... with out a GUI working... It does not start and I got a lot of libs installed and banshe as well........ =(

Can anybody help me downgrading this or making it work in ubuntu 10.04...

---

### Post by JCM_Pico on 2012-01-23
Bump!!! Bump!!! Bump!!!

Is there anybody out there....

---

### Post by oldos2er on 2012-01-23
Thread moved to Ubuntu One. Please don't bump your post more than once every 24 hours.

---


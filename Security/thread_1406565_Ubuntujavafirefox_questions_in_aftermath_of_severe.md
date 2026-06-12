---
title: "Ubuntu/java/firefox questions in aftermath of severe firefox pwnage"
date: 2010-02-14
forum: Security
---

### Post by distractions on 2010-02-14
Greetings.
I was sent a link to an attacksite, the site spawned loads of java popups, lunched more firefox instances and installed several firefox-plugins. I was using firefox 3.5.7 and Ubuntu 9.1.
[LIST]
[*]How isolated is the java (vm?) from the rest of the system?
[*]How much, if any, access does plugins have to personal data (passwords etc) in firefox?
[*]How do I completly purge my firefox installation with settings and all?
[*]What would you do/check in my situation?
[/LIST]
Thanks good knowledgeable people.

---

### Post by Pjotr123 on 2010-02-14
- close Firefox
- remove the hidden folder .mozilla in your personal folder
- start Firefox: now it has a clean slate
- install a secure Java:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by lovinglinux on 2010-02-14
Additionally, install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722). It should prevent that from happening again.

---

### Post by phillw on 2010-02-14
> **distractions said:**
> Greetings.
I was sent a link to an attacksite, the site spawned loads of java popups, lunched more firefox instances and installed several firefox-plugins. I was using firefox 3.5.7 and Ubuntu 9.1.
[LIST]
[*]How isolated is the java (vm?) from the rest of the system?
[*]How much, if any, access does plugins have to personal data (passwords etc) in firefox?
[*]How do I completly purge my firefox installation with settings and all?
[*]What would you do/check in my situation?
[/LIST]
Thanks good knowledgeable people.

Hi and welcome to the forums - you may also consider putting on NoScript - it's pretty much a 'must-have' these days - It will stop all scripts **except** from sites you say can run, from running. A few of the various things you can do to secure FireFox are covered in an article I wrote on my TechArea recently, you can get to it via my Signature, or directly --> [http://www.vpolink.com/threads/497-Browser-Security](http://www.vpolink.com/threads/497-Browser-Security)

Regards,

Phill.

---

### Post by distractions on 2010-02-14
Thanks for the great advice. But what about the damage done potential. How much of a wall is there between the system and the java-vm and between plugins and passwords in firefox.

---

### Post by lovinglinux on 2010-02-14
> **distractions said:**
> Thanks for the great advice. But what about the damage done potential. How much of a wall is there between the system and the java-vm and between plugins and passwords in firefox.

If you use a strong master password in the Firefox password manager, then you are pretty safe on this area. If not, then I guess it is possible to retrieve your passwords remotely with a script. I'm not sure tho. The thing is that Firefox password manager stores your passwords encrypted on a database named *signons.sqlite*. You can open this database with a sqlite browser without needing a password, but the data itself is encrypted. To actually view the real passwords, you need the encryption key stored into *key3.db*. If you don't use a master password, then all you need is access to this *key3.db* file to read the real passwords from *signons.sqlite* database. Both files are stored in your browser profile folder. So, if an attack site could gain control of your browser functions, like it seems to have accomplished, then I guess it would be possible to upload the *signons.sqlite* and *key3.db* to a remote server. I'm just speculating anyway.

Is better to be safe than sorry. If you have important passwords stored on Firefox, not just forum login info, then I suggest you change them asap.

About the system, I don't think that those scripts would be able to save anything outside your home, because they would need root access. So if there was any damages, they should be contained in your Firefox profile or eventually in your home folder. If you are really paranoid, you could install Ubuntu on Virtual machine, then make a copy the entire home from the virtual machine (this is the control). Then visit the attack site again and let it infect your browser. Then compare the home folder contents with the clean one (the control) using a diff tool like meld. This way you will be able to determine where the attack scripts saved stuff and delete those from your real system.

---

### Post by distractions on 2010-02-14
Thanks lovinglinux, very informative. A bowl of popcorn for you: :popcorn:

---


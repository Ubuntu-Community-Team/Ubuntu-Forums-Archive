---
title: "parental controle ubuntu 16.04"
date: 2016-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by hulk2 on 2016-06-01
I have thus used a third solution which is perfect for my needs and described on [this page]("https://doc.ubuntu-fr.org/tutoriel/comment_mettre_en_place_un_controle_parental#ctparental") (in French). It is based on a simple script which has to be manually installed. The script can be downloaded [here]("https://gitlab.com/marsat/CTparental/tags") . It is documented in French but I think that  it is easy enough to understand to be used by other people (and if  someone not speaking French wants to use it, I volunteer to give him/her  a hand). The script is downloaded and installed from the command line  using:

for ubuntu 16.04
```
sudo apt-get install gdebi-core 
wget -c https://gitlab.com/marsat/CTparental/uploads/c5e23c5cfd52fb860001fd24e7613013/ctparental_ubuntu_16.04_4.23.04-1.0_all.deb
sudo gdebi ctparental_ubuntu_16.04_4.23.04-1.0_all.deb

```

for ubnutu 17.xx or 18.04
```
sudo apt-get install gdebi-core 
wget -c  https://gitlab.com/marsat/CTparental/uploads/53d507262a495d3a20a1e1da622ebf46/ctparental_debian9_ubuntu17.xx_18.04_4.23.04-1.0_all.deb
sudo gdebi ctparental_debian9_ubuntu17.xx_18.04_4.23.04-1.0_all.deb

```

[IMG]https://pix.debian-fr.xyz/upload/img/1462399756.png[/IMG]

The last command line is used to fix the dependency problems which  result from the manual installation of the script. When running it, you  are asked to provide a login and a password for the script administrator  (you). Once the installation completed, open any web browser and enter  the URL [https://admin.ct.local]("http://127.0.0.1/CTadmin/").  The script does two things: the first one is that it restricts the URL  which can be visited by the user (it has a blacklist and a whitelist,  maintained by the university of Toulouse and it can filter out some  extensions and file types, as well as some IPs). A special attention has  to be given to the tab "Groupe privilégié" (which means privileged  user) on which you can choose which users have full access to internet  (in the example "hulk" have full access because they are dad :)):


[IMG]https://pix.debian-fr.xyz/upload/img/1462399805.png[/IMG]

Finally, the tab "Heures de connexion autorisées" ("allowed connexion  time") can be configured. For instance, in the example below, the user  "louisa" is allowed to use her computer maximum 3 hours a day, including  maximum 2 hours of internet connexion. She is not allowed to use it on  Monday, Tuesday and Thursday and is restricted to use it on the  afternoon only on Wednesday and Friday. 

[IMG]https://pix.debian-fr.xyz/upload/img/1462399825.png[/IMG]


[IMG]https://pix.debian-fr.xyz/upload/img/1462399811.png[/IMG]

official site: [https://gitlab.com/marsat/CTparental](https://gitlab.com/marsat/CTparental)

---

### Post by ericbradshaw on 2016-07-07
Is the whitelist editable?

---

### Post by hulk2 on 2016-07-09
yes the whitelist mod is editable.
[IMG]https://pix.debian-fr.xyz/upload/img/1462399766.png[/IMG]

if you ar in blacklist mod the whitelist is rehabilitated domains

---

### Post by hulk2 on 2016-12-30
Update of the links of the new version which corrects many bug ..

---

### Post by hulk2 on 2017-05-09
up version 16.04_4.20.17-1.0

---

### Post by hulk2 on 2017-08-26
up lien ubuntu 16.04 et ubuntu 17.04

---

### Post by hulk2 on 2017-12-24
- added link for ubuntu 14.04 and update link for ubuntu 16.04 ant ubuntu 17.xx 
- new admin interface link = [https://admin.ct.localhost](https://admin.ct.localhost)
- added safesearch qwant
- added safesearch binq in https.
- better support ipv6
- added locale es_ES
[web link to a good explanation on the configuration of ctparental but in French]("https://www.numetopia.fr/installation-de-ctparental-et-configuration/")

---

### Post by monkeybrain20122 on 2017-12-24
Do your kids have smart phones, do they have friends who do? What do you fear that they may see on the internt? I fail to see the point of this.

---

### Post by hulk2 on 2018-01-21
In fact, the children  have access to the internet, not full of the means of our day, and we  can not hope to control them all, and it is good for them that we also  have to talk to them about it. that he has inadvertently seen things he has shocked them.
but  as it is at home, they can have access to the internet without being  polluted by this pornographic matrimage when he wants to watch their  manga, animated cartoon or other research, it does not prevent all but  it is not a reson to not tried to reduce the dose of violence, pornography, stupidity ... that we suffer with them on the net.

---

### Post by hulk2 on 2018-07-10
Microsoft acquiert GitHub! Merci à GitHub , mais je vais sur Gitlab. [https://gitlab.com/marsat/CTparental](https://gitlab.com/marsat/CTparental)

 Microsoft acquires GitHub! Thanks to GitHub, but I'm going on Gitlab. [https://gitlab.com/marsat/CTparental](https://gitlab.com/marsat/CTparental)
 Microsoft adquiere GitHub! Gracias a GitHub, pero voy a Gitlab. [https://gitlab.com/marsat/CTparental](https://gitlab.com/marsat/CTparental)

---


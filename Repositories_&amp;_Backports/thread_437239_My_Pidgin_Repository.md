---
title: "My Pidgin Repository"
date: 2007-05-08
forum: Repositories &amp; Backports
---

### Post by Mightymod on 2007-05-08
Pidgin just made the way into my repo. If you speak german visit [my homepage]("http://ubuntu.schmidtke-hb.de/?q=pidgin-f-r-ubuntu-feisty") for further instructions.

Else you may add [COLOR="Red"]deb [http://apt.schmidtke-hb.de/](http://apt.schmidtke-hb.de/) feisty main[/COLOR] to your sources list and fetch the repo-key from [COLOR="Red"]http://ubuntu.schmidtke-hb.de/aptrepository.asc[/COLOR] to check the sigs.

Have fun with pidgin.

---

### Post by earobinson on 2007-05-08
Sweet, to bad im not german.

---

### Post by Niko_Thien on 2007-05-13
As I am german, I can confirm that the pidgin-deb works perfectly for me :) Only one more thing I would like to see on your repo: A package of the OTR-Plugin :)


greetz Niko

---

### Post by TopasPV on 2007-05-13
nice work! :)


I must admit, I discovered a problem installing pidgin with your repository:

The following NEW packages will be installed:
  pidgin 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7961kB of archives. After unpacking 23.6MB will be used.
Writing extended state information... Done
(Reading database ... 136213 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_2.0.0-schmidtke2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/pidgin_2.0.0-schmidtke2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgnt.so.0.0.0', which is also in package gaim
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin_2.0.0-schmidtke2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Any suggestions? Do I have to remove gaim or some of its packages?

---

### Post by Niko_Thien on 2007-05-13
I removed gaim and after that the installation should work perfectly.

---

### Post by WinterWeaver on 2007-05-13
> Else you may add deb [http://apt.schmidtke-hb.de/](http://apt.schmidtke-hb.de/) feisty main to your sources list and fetch the repo-key from [http://ubuntu.schmidtke-hb.de/aptrepository.asc](http://ubuntu.schmidtke-hb.de/aptrepository.asc) to check the sigs.

How can I get the key ? (newb method pls ^_^ )
I know where to add it, but not where to download it from. nor the command lol?

---

### Post by Niko_Thien on 2007-05-14
WinterWeaver, here we go:

open an terminal than:

```
wget ubuntu.schmidtke-hb.de/aptrepository.asc
```

```
sudo apt-key add aptrepository.asc
```

As the second step, add the repo to the sources list:

```
sudo echo "deb http://apt.schmidtke-hb.de/ feisty main" >> /etc/apt/sources.list
```

```
sudo echo "deb-src http://apt.schmidtke-hb.de/ feisty main" >> /etc/apt/sources.list
```

and finally you can sudo apt-get update your sources.list :)

hf ;)

---

### Post by reinderien on 2007-05-19
The repository is good - but there is something wrong with the deb package.

It seems to install correctly, but Pidgin does NOT load if you have not previously installed libmono 1.0. When you get this from apt then it's okay. So libmono 1.0 (not 2.0) should be brought in as a deb dependency...

---

### Post by Mightymod on 2007-05-19
Hmm, my package depends on libmono0 >= 1.2.3. I will check this later.

BTW: awn and affinity-search are also added to my rep.

See the complete packagelist [here]("http://ubuntu.schmidtke-hb.de/bersicht-des-apt-repositories")

---

### Post by voltagex on 2007-05-19
Replying here to add my thanks. Any chance you could tell me how you made the pidgin deb? I compiled pidgin manually but I've been testing some patches and I'd like to roll it all into a .deb.

---

### Post by mlind on 2007-05-20
> **voltagex said:**
> Replying here to add my thanks. Any chance you could tell me how you made the pidgin deb? I compiled pidgin manually but I've been testing some patches and I'd like to roll it all into a .deb.

get a pidgin source package from the gutsy archive (or debian unstable), apply your patches and rebuild.

---

### Post by reinderien on 2007-05-23
> **Niko_Thien said:**
> Only one more thing I would like to see on your repo: A package of the OTR-Plugin :)

Indeed, that would be very nice!! I can't find this anywhere else. Windows has a pidgin OTR installer, but ubuntu has no apt repo for the deb yet...

Excellent job with the repository nonetheless.

---

### Post by Mightymod on 2007-05-27
pidgin-otr just hit my repository. Feel free to use it now.

---

### Post by Mightymod on 2007-05-28
pidgin-libnotify is also now apt-gettable !

---

### Post by GadgetsGuy on 2007-05-28
any ETA when Pidgin 2.0.1 will make it into the Synaptic package manager for the PPL (such as my GF) who are not comfortable with apt-get and command lines?

---

### Post by dafinga on 2007-06-22
worked great ... thanks again!

---

### Post by macro182 on 2008-04-03
I have some problem with latest update, it tell me that there are unsatisfied dependencies...

I have shmidtke repo in my source list.

Thanks for helping me! ;)

---

### Post by Mightymod on 2008-04-04
Is fixed now

---


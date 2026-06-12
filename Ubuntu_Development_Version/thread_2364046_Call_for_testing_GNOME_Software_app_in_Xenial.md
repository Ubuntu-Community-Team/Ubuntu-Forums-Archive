---
title: "Call for testing: GNOME Software app in Xenial"
date: 2017-06-17
forum: Ubuntu Development Version
---

### Post by jbicha on 2017-06-17
Robert Ancell has just [announced]("https://lists.ubuntu.com/archives/ubuntu-desktop/2017-June/005010.html") that he has prepared a big update for the GNOME Software app in Ubuntu 16.04 LTS. To ensure everything still works, he is asking for help testing.

The GNOME Software app is also known as Ubuntu Software.

Ubuntu 16.04 LTS shipped with version 3.20.1 with a bunch of Ubuntu fixes and customizations. The new version updates that to 3.20.5 and rebases Ubuntu's patches so that if there ever are any future 3.20 updates, it will be much easier to get them into Ubuntu 16.04 LTS.

See the [announcement]("https://lists.ubuntu.com/archives/ubuntu-desktop/2017-June/005010.html") for details on how to try the new version.

---

### Post by P-I H on 2017-06-18
Made some comparisons on a Ryzen 7 1700 computer with 16.04.2 (gnome software 3.20.5), 17.04 (Gnome software 3.22.7) and 17.10 (Gnome software 3.24.3).
16.04.2 old version
Start < 1sec, All <20 sec, look at installed program < 25 sec, search didn't check
16.04.2 new version
Start < 1sec, All <20 sec, look at installed program < 1 sec, search installed program > 1 min, back key > 1 min, use ALL instead of waiting < 1sec
These problems may relate to the Ryzen system.
17.04
Start < 2 sec, All < 1 sec, look at installed program < 1 sec, search installed program < 1 sec, back key < 1 sec, search for none existing app < 1 sec
17.10
Start 1:st time < 10 sec, start next time < 1 sec, look at installed program < 1 sec, search installed program < 1 sec, back key < 1 sec, search for none existing app < 1 sec

---

### Post by jbicha on 2017-06-18
I asked Robert about testing feedback and he said that y'all can _reply directly to the ubuntu-desktop list_.

 	[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=933864") 	[COLOR=#000000]P-I H[/COLOR], I don't know anything about Ryzen. Usually, gnome-software is running in the background. I would think that could make starting the app a bit faster.

---

### Post by ventrical on 2017-06-19
Will not work on ubuntu-mate.

Can you specify with distros please.

regards..

---

### Post by jbicha on 2017-06-19
> **ventrical said:**
> Will not work on ubuntu-mate.


What doesn't work on Ubuntu MATE?

---

### Post by ventrical on 2017-06-19
> **jbicha said:**
> What doesn't work on Ubuntu MATE?

gnome-software

I followed all the steps, installed the ppa .. gnome-software not installed.

just a sec..

```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ killall gnome-software
gnome-software: no process found
ventrical@ventrical-RK574AA-ABA-a1730n:~$ gnome-software
The program 'gnome-software' is currently not installed. You can install it by typing:
sudo apt install gnome-software
ventrical@ventrical-RK574AA-ABA-a1730n:~$ 

```

I thought gnome-sowftware was installed by default on hard installations.

What did I do wrong?


uses ubunt-mate-welcome software only?
Regards..

---

### Post by ventrical on 2017-06-19
Naturally had to install gnome-software first. Momentary laspe of  something on my part :)

Very fast loading from terminal.

Don't like the "Lets go shopping." It makes me think that I have logged on to a commercial web-page. ..but it is very sleek and fast. I like it.

Regards..

---

### Post by jbicha on 2017-06-19
."Let's go shopping" is only shown the first time and it's disabled in Ubuntu and Ubuntu GNOME. Why don't you ask Ubuntu MATE to set gsettings [org.gnome.software]("http://org.gnome.software") first-run=false ? I don't know if they'll bother SRUing that to 16.04 but I think it would be good to have in 17.10.

I think Ubuntu MATE's Software Boutique has a button to install the GNOME Software app.

---

### Post by ventrical on 2017-06-20
> **jbicha said:**
> . Why don't you ask Ubuntu MATE to set gsettings [org.gnome.software]("http://org.gnome.software") first-run=false ? I don't know if they'll bother SRUing that to 16.04 but I think it would be good to have in 17.10.


 I was just declaring an observation using the ppa in Mate 16.04.  I had forgot that they do not use gnome-software from the repo. When it called for testing it didn't specify the specific DE types of ubuntu 16.04 (as I suggested in another post on this thread) so I went ahead and gave it a spin in Mate :)

Regards..

---

### Post by jbicha on 2017-06-20
Ubuntu MATE can still set that option even if Ubuntu MATE does not include the app by default. I encourage you to ask Ubuntu MATE about it. :)

---

### Post by Chanath on 2017-06-21
Gnome software is included in Xubuntu, but it loads very slowly. I keep this app as an oddity, rather than use it. It doesn't show what else (dependencies) is installed together with the app you are installing. It might be installing needed and unneeded dependencies. I use Synaptic, where I can see what would be installed, before clicking okay. Or the terminal.

---


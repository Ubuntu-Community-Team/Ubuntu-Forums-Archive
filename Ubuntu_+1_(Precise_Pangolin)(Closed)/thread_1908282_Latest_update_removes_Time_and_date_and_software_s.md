---
title: "Latest update removes Time and date and software sources"
date: 2012-01-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bfb on 2012-01-13
Since last night's update, which removed parts of libreoffice, I no longer have a time /date indicator, nor can I find software sources in System settings..
I have solved the libre office issue with the workaround in launchpad, but the others remain

---

### Post by dino99 on 2012-01-13
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -a

note: to play with dev release suppose you are able to fix basic things yourself, meaning having some skills.

---

### Post by Harry33 on 2012-01-13
> **bfb said:**
> Since last night's update, which removed parts of libreoffice, I no longer have a time /date indicator, nor can I find software sources in System settings..
I have solved the libre office issue with the workaround in launchpad, but the others remain

Libreoffice has nothing to do with time/date indicator.
Instead, see what have you done with evolution-data-server and its libraries (libecal, libebook ...).

---

### Post by bfb on 2012-01-13
I didn't do anything actively.
After the update there were 3 separate problems, which I realise are unrelated, except that they are all the result of the update (packages removed?)
1) the libre office I have resolved with the advice on launchpad.
2) Software sources are no longer under system settings.
3) time/date was removed but not replaced

Sorry if I am annoying with my level of incompetence
My idea was just to raise this is case others have the same problem

Thanks for the halp so far

---

### Post by jbicha on 2012-01-13
Software Properties was intentionally [removed]("https://launchpad.net/ubuntu/+source/software-properties/0.82.2").

As for time/date, you might have removed something important when doing a dist/full upgrade. Try uninstalling the ubuntu-desktop package then reinstalling it.

---

### Post by lihaitao on 2012-01-13
> **bfb said:**
> 
3) time/date was removed but not replaced


Same here. Solved by reinstalling indicator-datetime and restart.

---

### Post by cariboo on 2012-01-13
To add to jbicha's post, software sources is also still available if you have synaptic installed.

---

### Post by Harry33 on 2012-01-14
> **cariboo907 said:**
> To add to jbicha's post, software sources is also still available if you have synaptic installed.

Synaptic works also well without software-sources package.
Selecting "settings - repositories" looks a bit different, though, but you are able to change the file sources.list this way too (for example selecting or deselecting PPA's).

---

### Post by DougieFresh4U on 2012-01-14
> **bfb said:**
> Since last night's update, which removed parts of libreoffice, I no longer have a time /date indicator, nor can I find software sources in System settings..
I have solved the libre office issue with the workaround in launchpad, but the others remain

Were you offered a 'partial' update?:D

---

### Post by ubiquitin.jf on 2012-01-14
This one snuck onto my machine too.

*sudo apt-get install indicator-datetime*

---


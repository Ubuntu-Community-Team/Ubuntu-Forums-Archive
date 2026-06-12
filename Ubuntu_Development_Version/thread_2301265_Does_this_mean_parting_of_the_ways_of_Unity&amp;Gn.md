---
title: "Does this mean parting of the ways of Unity&amp;Gnome, compiz/Unity&amp;metacity?"
date: 2015-11-01
forum: Ubuntu Development Version
---

### Post by zika on 2015-11-01
1. I like this Halloween cursor gimmick... ;)
2. This has been going for weeks now:```
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... 
The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru
Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED:
  indicator-datetime libcamel-1.2-52 libcheese-gtk23 libcheese7 libebook-contacts-1.2-1 libecal-1.2-18 libedata-cal-1.2-27 libedataserver-1.2-20 libnettle4 ubuntu-desktop unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
The following NEW packages will be installed:
  libcamel-1.2-54 libcheese-gtk25 libcheese8 libebook-contacts-1.2-2 libecal-1.2-19 libedata-cal-1.2-28 libedataserver-1.2-21 libgtop-2.0-10
The following packages have been kept back:
  metacity metacity-common
The following packages will be upgraded:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo cheese cheese-common empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-plugins folks-common gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gnome-contacts gnome-control-center gnome-control-center-data gnome-panel gnome-panel-data gnome-shell gnome-shell-common gnome-shell-extensions libebackend-1.2-10 libebook-1.2-16 libedata-book-1.2-25 libedataserverui-1.2-1 libevolution libfolks-eds25
  libfolks-telepathy25 libfolks25 libgnutls-deb0-28 libgnutls-openssl27 mcp-account-manager-uoa
37 upgraded, 8 newly installed, 14 to remove and 2 not upgraded.
Need to get 29,9 MB of archives.
After this operation, 37,1 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
``````
[FONT=Verdana]:~$ sudo aptitude full-upgrade [/FONT]
The following NEW packages will be installed:
  libcamel-1.2-54{ab} libcheese-gtk25{a} libcheese8{a} libebook-contacts-1.2-2{a} libecal-1.2-19{ab} libedata-cal-1.2-28{a} libedataserver-1.2-21{ab} libgtop-2.0-10{a} libmetacity-private3a{ab} 
The following packages will be REMOVED:
  libebook-contacts-1.2-1{u} libedata-cal-1.2-27{u} 
The following packages will be upgraded:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo cheese cheese-common empathy empathy-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-plugins folks-common gir1.2-ebook-1.2 
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gnome-contacts gnome-control-center gnome-control-center-data gnome-panel gnome-panel-data gnome-shell gnome-shell-common gnome-shell-extensions libebackend-1.2-10 libebook-1.2-16 libedata-book-1.2-25 libedataserverui-1.2-1 libevolution libfolks-eds25 
  libfolks-telepathy25 libfolks25 libgnutls-deb0-28{b} libgnutls-openssl27 mcp-account-manager-uoa metacity metacity-common mtr-tiny{b} unity-control-center 
41 packages upgraded, 9 newly installed, 2 to remove and 0 not upgraded.
Need to get 31,1 MB of archives. After unpacking 48,5 MB will be used.
The following packages have unmet dependencies:
 libcheese7 : Depends: cheese-common (= 3.16.1-1ubuntu2) but 3.18.1-1ubuntu2 is to be installed.
 libgnutls-deb0-28 : Conflicts: libnettle4 but 2.7.1-5 is installed.
 libmetacity-private3a : Breaks: libmetacity-private3 (< 1:3.18) but 1:3.17.2-4ubuntu1 is installed.
 libcamel-1.2-54 : Conflicts: libcamel-1.2-52 but 3.16.5-1ubuntu3 is installed.
 libcheese-gtk23 : Depends: cheese-common (= 3.16.1-1ubuntu2) but 3.18.1-1ubuntu2 is to be installed.
 mtr-tiny : Depends: libncurses5 (>= 6) but 5.9+20150516-2ubuntu1 is installed.
            Depends: libtinfo5 (>= 6) but 5.9+20150516-2ubuntu1 is installed.
 libecal-1.2-19 : Conflicts: libecal-1.2-18 but 3.16.5-1ubuntu3 is installed.
 libmetacity-private3 : Depends: metacity-common (= 1:3.17.2-4ubuntu1) but 1:3.18.1-1ubuntu1 is to be installed.
 libedataserver-1.2-21 : Conflicts: libedataserver-1.2-20 but 3.16.5-1ubuntu3 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                                          
1)      compiz                                                                                
2)      compiz-gnome                                                                          
3)      indicator-datetime                                                                    
4)      libcamel-1.2-52                                                                       
5)      libcheese-gtk23                                                                       
6)      libcheese7                                                                            
7)      libecal-1.2-18                                                                        
8)      libedataserver-1.2-20                                                                 
9)      libmetacity-private3                                                                  
10)     libnettle4                                                                            
11)     mtr-tiny                                                                              
12)     ubuntu-desktop                                                                        
13)     unity                                                                                 
14)     unity-control-center                                                                  
15)     unity-control-center-signon                                                           
16)     unity-tweak-tool                                                                      
17)     webaccounts-extension-common                                                          
18)     xul-ext-webaccounts                                                                   

      Leave the following dependencies unresolved:                                            
19)     indicator-session recommends unity-control-center-signon | gnome-control-center-signon
20)     libaccount-plugin-1.0-0 recommends unity-control-center-signon                        
21)     ubuntu-standard recommends mtr-tiny                                                   
22)     unity-greeter recommends indicator-datetime                                           
23)     indicator-applet-complete recommends indicator-datetime                               
24)     gnome-panel recommends unity-control-center                                           


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```
Does this mean parting of the ways of Unity and Gnome or is it, simply, a stage in development where these few packages are left aside to be dealt once in the futire... ;)?
Update&#8321;: Disregard mtr-tiny as it has been purged accordingly... ;)
Update&#8322;: after making decision and letting dist-upgrade do its job, leaving me without ubuntu-desktop package which I can survive, I'm goint to see how to reconcile metacity and compiz/Unity:```
:~$ sudo apt-get install -s metacity metacity-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmetacity-private3a
The following packages will be REMOVED:
  compiz compiz-gnome libmetacity-private3 unity unity-tweak-tool
The following NEW packages will be installed:
  libmetacity-private3a
The following packages will be upgraded:
  metacity metacity-common
2 upgraded, 1 newly installed, 5 to remove and 0 not upgraded.
Remv unity-tweak-tool [0.0.6ubuntu3]
Remv unity [7.3.2+15.10.20151016-0ubuntu1]
Remv compiz [1:0.9.12.2+15.10.20151015-0ubuntu1]
Remv compiz-gnome [1:0.9.12.2+15.10.20151015-0ubuntu1]
Inst metacity [1:3.17.2-4ubuntu1] (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [amd64]) []
Remv libmetacity-private3 [1:3.17.2-4ubuntu1] []
Inst metacity-common [1:3.17.2-4ubuntu1] (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [all]) []
Inst libmetacity-private3a (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [amd64])
Conf metacity-common (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [all])
Conf libmetacity-private3a (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [amd64])
Conf metacity (1:3.18.1-1ubuntu1 Ubuntu:16.04/xenial-proposed [amd64])
```It looks like we should be turning our heads towards Wayland which I did months ago... ;)
Update: It looks like a joke but it is not:```
:~$ sudo apt-get purge metacity metacity-common -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  compiz* compiz-gnome* gnome-session-flashback* libmetacity-private3* metacity* metacity-common* unity* unity-tweak-tool*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Purg unity-tweak-tool [0.0.6ubuntu3]
Purg unity [7.3.2+15.10.20151016-0ubuntu1]
Purg compiz [1:0.9.12.2+15.10.20151015-0ubuntu1]
Purg compiz-gnome [1:0.9.12.2+15.10.20151015-0ubuntu1]
Purg gnome-session-flashback [1:3.18.1-1ubuntu1]
Purg metacity [1:3.17.2-4ubuntu1]
Purg libmetacity-private3 [1:3.17.2-4ubuntu1]
Purg metacity-common [1:3.17.2-4ubuntu1]
```
Update&#8323;: All is good, peace has been achived between all parties, all packages got theis dependencies, not much removed and it will be reinstalled, I'm marking this thread „solved“... ;)

---

### Post by grahammechanical on 2015-11-01
It is machine logic. The program cannot break out of its set of rules. One day you will run those commands on the development release of a Ubuntu AI machine and you will get the reply: remove the following packages - humans!  :)

Regards

---

### Post by zika on 2015-11-01
> **grahammechanical said:**
> It is machine logic. The program cannot break out of its set of rules. One day you will run those commands on the development release of a Ubuntu AI machine and you will get the reply: remove the following packages - humans!  :)

RegardsNo, that is logic that is OK. Machine should not break it and I do not see any use of it breaking it. I hope that it will not... ;)
Real/true AI is questionable due to some fundamental mathematicall laws but that is another topic... Back to topic... ;)

---

### Post by ventrical on 2015-11-01
Philosophically speaking I think , yes, eventually (if not sooner - then later) there will be  parting of the ways between the two. I  can only offer my opinion as I see .. and that is it has to do with human resources. There is  not enough .. at lease from the Canonical side of things .. to fill in the spaces and unity, unity8, snappy core and snappy_personal are now the focus of this  development cycle.

 However, if the community at large gets involved with testing gnome and wayland and continues to make fixes then  it could look good in the long run. But more and more Canonical is disavowing projects that are not within the infrastructure of their flagship frameworks so I think not.

..just my 2 cents..   it's sort of a holding pattern right now. Snappy is as Snappy does ?

:)

regards..

---

### Post by zika on 2015-11-01
Philosophy, Snappy at al. aside, I was asking for this and only this particular case... ;)
Mea culpa, I did introduce Wayland by mistake... ;)

---

### Post by ventrical on 2015-11-01
> **zika said:**
> It looks like we should be turning our heads towards Wayland which I did months ago... ;)
Update: It looks like a joke but it is not:

Thank you . I rest my philisophical case. :)  umm.. Just on a side note... I was running gnome-shell desktop on wayland in a few instances [s] and when it breaks it breaks really good to the point which is far beyond my experitse to repair. [/s]  So in fairness I'll commit  to DLing the xenial gnome iso and see what happens with wayland. I hope I do not appear to be hijacking this thread. I just find your reports interesting and worth looking into.

Regards..
*edit*
I booted up an install  of gnome3 that I thought was broken and I accidently hit F7 which brought up the gnome-deskktop GUI. Now why this happened I have no clue. btw .. this install has the proposed repos enabled and the wayland option in the greeter before logon. Trying to get up to speed on this.

---

### Post by ronacc on 2015-11-01
for information , I am running xenial-gnome and I am not seeing any of those packages wanting to be removed .

---

### Post by ventrical on 2015-11-01
Ok.. I am on the 'live' xenial gnome-desktop and my philosophical point of view has changed.  The 'Try Ubuntu' option gives way to a speedy desktop with three animated Instructional Development showcases.  Gnome3 is slip-sliding away in a graphical fashion that is far superior to unity-compiz -so- my new point of view is that apparently the gnome-desktop project  has invested is highly accelerated graphical gizzmos that work extremely well.  Even a new gnome loading icon.  I am not sure if it is running wayland but certainly looks so - by default.. so I will next do hard install.

 If there is a pulling away or spitting of gnome and unity it will be to unity's detriment as gnome3 desktop is obviously more highly advanced and effervescent at this stage of the game. My apologies for off topic. umm... seems that wayland has taken mir and X and collided them :)
edit: actually running on X !! No compiz.
Regards..

---

### Post by ronacc on 2015-11-01
on my installed xenial-gnome-desktop there is no trace of unity installed ( only a couple of shared libs ) and no compiz  and it uses mutter as the WM .

---

### Post by grahammechanical on 2015-11-01
There will obviously be a parting of the ways. Gnome.org is going over to a Wayland specified compositor but Ubuntu is not. And Ubuntu Gnome will have to stay true to its mission and also move to the Gnome Wayland compositor. 

There is another parting of the ways between Ubuntu and Ubuntu Personal. The difference is not just Ubuntu using Mir and not Wayland instead of X but Ubuntu being built on snappy Ubuntu core. That is a big fracture point but it does not affect the Ubuntu archives which will continue to be debian packages.

Besides, using Proposed and dist-upgrade does carry a risk that something like ubuntu-desktop will be removed and not reinstalled with a new version. It is a few years since I have had it happen but we never know.

---

### Post by buzzingrobot on 2015-11-03
Gnome's window manager is Mutter and in my experience it's pretty good. Unity moving off Compiz shouldn't affect that. AFAIK, Compiz is anathema to Gnome Shell.

The OP's problem seems to be the expected mish mash of dependency conflicts seen during development.

Some Ubuntu packages are built against a lib or two so they play well with Unity.  They will show up as dependencies if those packages are installed on non-Unity systems.

---

### Post by Cavsfan on 2015-11-03
Xubuntu Xenial 16.04 hasn't ever tried to remove those packages either. Unity has just a small amount of packages but no possibility to use Unity.

```
cavsfan@cavsfan-le-beast:~$ dpkg -l | grep -e "compiz" -e "metacity"
ii  compiz                                      1:0.9.12.2+15.10.20151015-0ubuntu1         all          OpenGL window and compositing manager
ii  compiz-core                                 1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        OpenGL window and compositing manager
ii  compiz-gnome                                1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins:amd64                        1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        OpenGL window and compositing manager - plugins
ii  compiz-plugins-default:amd64                1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        OpenGL window and compositing manager - default plugins
ii  compizconfig-settings-manager               1:0.9.12.2+15.10.20151015-0ubuntu1         all          Compiz configuration settings manager
ii  libcompizconfig0:amd64                      1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        Settings library for plugins - OpenCompositing Project
ii  libmetacity-private3                        1:3.17.2-4ubuntu1                          amd64        library for the Metacity window manager
ii  metacity                                    1:3.17.2-4ubuntu1                          amd64        lightweight GTK+ window manager
ii  metacity-common                             1:3.17.2-4ubuntu1                          all          shared files for the Metacity window manager
ii  metacity-themes                             1.0.11                                     all          Themes for the Gtk2 metacity window manager
ii  python-compizconfig:amd64                   1:0.9.12.2+15.10.20151015-0ubuntu1         amd64        Compizconfig bindings for Python

```

```
cavsfan@cavsfan-le-beast:~$ dpkg -l | grep unity
ii  libunity-protocol-private0:amd64            7.1.4+15.10.20151002-0ubuntu1              amd64        binding to get places into the launcher - private library
ii  libunity-scopes-json-def-desktop            7.1.4+15.10.20151002-0ubuntu1              all          binding to get places into the launcher - desktop def file
ii  libunity9:amd64                             7.1.4+15.10.20151002-0ubuntu1              amd64        binding to get places into the launcher - shared library

```

I really like Xubuntu. :p

---

### Post by zika on 2015-11-03
Due to peace achieved in Update&#8323; in #1 I'm marking this &#8222;solved&#8220;

---

### Post by grahammechanical on 2015-11-04
I have just heard something on UOS about relabelling certain dependencies of certain applications as "recommends" instead of "depends" to avoid the removal of something like Libreoffice also taking out ubuntu-desktop.

---

### Post by rrnbtter on 2015-11-04
I think a bit of patience is in order until Ubuntu completes their conversion to mir and snappy and compliant drivers have been developed for every piece of equipment under the sun which has to be a formidable task. I'm pretty certain that I will be satisfied with the results. What I have now with Xenial and the 4.3 kernel is top notch on five year old equipment. Just switching from 4.2 to 4.3 kernel is a big improvement in speed. My experience with these dev cycles is that some days things are crap and some days things are wonderful and then back to crap again. It is best for me to reserve finial opinion until the cycle ends. But the conversion taking place has been a "multicycle cycle" (my words). So far as the "parting of the ways", well that has been going on for years. When mir, snappy, etc comes online I think the flavors are getting more than a "part", it will be a full blown haircut. I have already lost all my hair from learning linux, so I for one have nothing left to lose. I'm happy!

---


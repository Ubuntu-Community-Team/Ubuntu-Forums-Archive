---
title: "Kdenlive crash on start"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by Questioneer on 2008-07-07
Hello-
When I launch Kdenlive, I get the following message.(In terminal)
> 
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.



I understand this is because I chose the wrong default video format when it was first booted. 

However, which is the right one??? They are all rather confusing. I'm running Hardy Heron with a Radeon X600 and compiz.

Thanks,
Questioneer.

---

### Post by Questioneer on 2008-07-09
Just to add, I do not have any special sound cards... I have a Dell XPS 400.

---

### Post by Statik on 2008-07-13
I too am looking for a solution to this. I have Kdenlive working on one of my desktops, but that was an upgrade from gutsy. This is a fresh install. Getting the following errors:
On initial execute, popup window:
DCOP Communication Error 
There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list.
/home/statik/.DCOPserver_statik-laptop__0
Please check that the "dcopserver" program is running!

Then the program seems to startup before crashing out again and the same popup appears.

In the terminal where I started the program is the following messages:

```
statik@statik-laptop:~$ kdenlive
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdeinit: Aborting. No write access to '/home/statik/.ICEauthority'.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
KCrash: Application 'kdenlive' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
Unable to start Dr. Konqi
statik@statik-laptop:~$ kdeinit: Aborting. No write access to '/home/statik/.ICEauthority'.

```

Any help appreciated

Statik

---

### Post by Creative2 on 2008-07-14
see this
[http://ubuntuforums.org/showthread.php?t=791355](http://ubuntuforums.org/showthread.php?t=791355)

---

### Post by Statik on 2008-07-14
```
1 : sudo apt-get install libxcb-composite0
2: delete configuration files (~/.kde/share/config/kdenliverc)
```

was all that I needed to fix it!

Thanks!

Statik

---

### Post by Statik on 2008-07-14
My fault. I got excited and tried to fix it . . . on my desktop where it already works. It didn't fix it on the laptop. *sigh*

Still looking for a solution.

Statik

---

### Post by Creative2 on 2008-07-15
try with this i ma loaded on my computer right now

sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev


and if your graphid card is an Nvidia you could try this:(**NEVER TESTED BECAUSE I HAVE AN INTEL**)

If you have a NVidia and Ubuntu Hardy Heron, the crash of Kdenlive is due a missconfiguration of the last Nvidia driver in Heron by default.
 
 The solution:
 
 Edit the xorg.conf
 sudo gedit /etc/X11/xorg.conf
 
 Add this line to the Device Section
 Option &#8220;UseCompositeWrapper&#8221; &#8220;True&#8221;
 
 Add this at the end of the file
 Section &#8220;Extensions&#8221;
 Option &#8220;Composite&#8221; &#8220;Enable&#8221;
 EndSection
 
 Reset the X server (Ctrl+Alt+Backspace)


welll if doesn't work i haven't other ideas

---

### Post by Statik on 2008-07-16
The xorg thing isn't related to my problem, I think. Mine seemed to be pointing to KDE. So, I did the following:
1. Installed KDE through synaptic
2. Logout of Gnome and login into KDE by choosing the session option. When asked, choose, only this once.
3. Delete the ~/.kde/share/config/kdenliverc file (I think that's where it is)
4. Start Kdenlive in KDE. Choose the appropriate format.
5. Logout of KDE and back into Gnome
6. Kdenlive runs!

Statik

---

### Post by Creative2 on 2008-07-17
well install kde because kdenlive was not running sound a bit strange...
anyway..

i use kubuntu and kdenlive was crashing before to installe these packages ..

---

### Post by wolfie2x on 2008-07-20
I did this:

1. sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2. rm -rf ~/.kde/share/config/kdenliverc

and I tried the default format, but no luck; still crashes! :(


update: 
worked after turning off compiz!!

3. press Alt+F2 and run "metacity --replace"  (for gnome)

(to enable compiz again do -> "compiz --replace")

---

### Post by w.chris on 2008-09-22
Hi,

there is a solution to fix the problem: downgrade go the gutsy version:

the easy way: 
remove kdenlive and all of its dependencies:
apt-get remove kdenlive kdenlive-data (and libmlt...--I don't remember the exact names)

sed 's/hardy/gutsy/g' -i /etc/apt/sources/list
apt-get update
apt-get install kdenlive
sed 's/gutsy/hardy/g' -i /etc/apt/sources/list
apt-get update

It worked for me just fine. After downgrading kdenlive became very stable and stopped crashing.

---

### Post by dotnix on 2009-01-11
> **wolfie2x said:**
> I did this:

1. sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2. rm -rf ~/.kde/share/config/kdenliverc

and I tried the default format, but no luck; still crashes! :(


update: 
worked after turning off compiz!!

3. press Alt+F2 and run "metacity --replace"  (for gnome)

(to enable compiz again do -> "compiz --replace")


Man, it worked!!!!!!!!!
Thank u sooooooo much!!!!!!!!! u rock! :D

---


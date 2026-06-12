---
title: "ubuntu server... thinking about it"
date: 2010-02-01
forum: Server Platforms
---

### Post by ja660k on 2010-02-01
hey guys,

this may be silly questions... but.
I've been using ubuntu desktop for a while now and im thinking of making a home server...

and the questions are..
does the server come with apt-get? or does things need to be compiled manually.

also i understand there is no gui but X11 window manager like fluxbox so i can throw out the screen and VNC from another computer? (sometimes ssh can get droll)

thanks in advance

---

### Post by terrapin893 on 2010-02-01
I used desktop for a bit then converted to server and its all sorts of fun.   

Yes it comes with apt-get (well, after reviewing my sources, I dont see any particular references to apt-get but I think Ive ran it successfully before) and aptitude and wget so you can get packages.  There also might be some things that you have to manually compile, but Ive found great documentation on setting up the server edition.  It actually taught me how to manually compile stuff.  

As for window managers . . . . I dunno, I always SSH in.

[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

---

### Post by ja660k on 2010-02-01
okay great.
thanks for the link :-)

---

### Post by tornado42 on 2010-02-01
always use ssh... I tried to load a gui on it but the gui eats a lot of the system resources and it takes longer for it to boot.  you can do it though...
 
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)
 
or
 
sudo aptitude install ubuntu-desktop   (Gnome i believe)
sudo aptitude install kubuntu-desktop   (KDE)
sudo aptitude install xubuntu-desktop  (xfce)

---

### Post by BkkBonanza on 2010-02-01
Keep in mind that a lot of the typical server type things you would do - mostly editing config files - can be done easily with Nautilus from your desktop (which uses ssh in the background).

Once you have the server going and ssh working (ideally with a key login) try browsing your server files by entering sftp://user@server/path_to_files in the address bar. You can save it as a bookmark too. You can use your desktop editor tools to work with the files. This covers a large part of server admin. You can create icons/menus to automate other server tasks using ssh with preset commands. eg. restarts. 

Also don't forget http based admin tools like webmin. And, finally, yes, you can use either VNC or X-forwarding for real graphical programs.

---

### Post by tlsarles on 2010-02-01
Yeah, server version is only missing the X11 server. Other than that, it's business as usual. As mentioned, you can do X forwarding to run GUI applications which are running on the server, but displayed on your desktop distro. Quite neat

---

### Post by oupamster on 2010-02-01
fullcircle magazine also has a tutorial on building your own server; issue 9-16 and also on issues 28-29 and issues 31-32

[http://www.fullciclemagazine.org](http://www.fullciclemagazine.org)

---

### Post by jayg1169 on 2010-02-01
In the words of a famous sports brand "Just do it".
You'll learn so much about the CLI when thats the only choice!

The Ubuntu forum and Google are your best friends when learning the CLI!
If you stay with the GUI you will always rely on it!

---

### Post by quietas on 2010-02-02
I started a thread a year back with a bunch of ideas. [http://ubuntuforums.org/showthread.php?t=1075599](http://ubuntuforums.org/showthread.php?t=1075599)

People had all sorts of good setups, I had a few to start and added quite a bit after seeing what else people had though up.

For Apt-get, it's there with any version of Ubuntu, Debian, Mint, ....  Also for desktop I ended up installing it using "sudo apt-get install ubuntu-desltop" you can do similar to install Flux with zubuntu-desktop, KDE, or whatever. I ran mine headless with FreeNX installed rather than VNC, it was simply faster, with near real time screen rendering. I did most work using Putty for SSH command line, but some things like graphically moving files around were quicker with a GUI. It was also easier for my wife to connect in.

---

### Post by dnvikram on 2010-02-02
> **ja660k said:**
> hey guys,

this may be silly questions... but.
I've been using ubuntu desktop for a while now and im thinking of making a home server...

and the questions are..
does the server come with apt-get? or does things need to be compiled manually.

also i understand there is no gui but X11 window manager like fluxbox so i can throw out the screen and VNC from another computer? (sometimes ssh can get droll)

thanks in advance

Running your machine on Ubuntu Server would be a real wise decision.I have been using Ubuntu 8.10/9.04 server versions over an year and its absolutely wonderful.Package mgmt using apt-get is a breeze and makes your life so easy.You can also install UPTRACK(Online Kernel patching) and achieve 100% uptime.My ubuntu servers run like charm with only going down twice in an year's period and that too due to power fluctuation(I havent got an UPS yet :P).Online upgrade to newer releases is effortless and very reliable,unlike other distros where it is still flaky.The best part is it comes without GUI,which reduces the footprint,resource consumption and increases security.

---

### Post by tlsarles on 2010-02-02
Don't listen to the recommendations that say to run a 
apt-get install ubuntu-desktop
or any of the variants. This really defeats the purpose of a server OS. This command should only be thought of as a 'tap-out' when you give up.

---

### Post by quietas on 2010-02-02
> **tlsarles said:**
> Don't listen to the recommendations that say to run a 
apt-get install ubuntu-desktop
or any of the variants. This really defeats the purpose of a server OS. This command should only be thought of as a 'tap-out' when you give up.

Screw that mentality completely. That is exactly what gives people the idea that Linux is for hard core geeks who shun anything main stream.

A GUI has some overhead, modern and even older equipment can take it with ease. Yes, it uses some CPU and RAM, but for example my Ubuntu CLI only server hosts our intranet webpage, document store, GLPI helpdesk, and ZenOSS server. It only has a .10 server load on dual Xeons with 4gb RAM. My mail server running Redhat with a full Gnome GUI, dual Xeons, and 8gb RAM, plus 10x the usage also has .10 load average.

Use what serves your purpose and does what you want the way you want. Don't listen to purists who evangelize the evils of GUI. It all depends on what you are doing and how you access it. Visually seeing things can often be easier and no one says your GUI has to run 24/7.

---

### Post by ja660k on 2010-02-05
thanks for the replies and links posted.
i'm no stranger to CLI. i use solaris at university.

well i installed and working great
thanks alot :)

---


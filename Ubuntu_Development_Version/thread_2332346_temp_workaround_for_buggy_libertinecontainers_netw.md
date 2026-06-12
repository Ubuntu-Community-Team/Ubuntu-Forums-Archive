---
title: "temp workaround for buggy libertine/containers network"
date: 2016-07-30
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-30
Either the nework manager , server or both for the process used to create containers is buggy. The work around is to allow the containers to be built in the background (usually 10 minutes), then exit libertine and open libertine again (no log off needed) . You should then be able to install deb apps like firefox, gedit, nautilus etc... apps like konsole or extremetuxracer will not work but many graphical games work much faster and  more enhanced.. even with only 1GB RAM.

regards..

---

### Post by mc4man on 2016-07-31
The wait 10 min. or so works.

---

### Post by rrnbtter on 2016-08-01
Greetings,
There are some python lxc updates in the stream this morning. I don't have time to check it out so can't give feed back on it.  Regarding the rest of this, I run libertine from the terminal install of the GUI. It lets me get some feed back on what is happening. With Yakkety the problem has been with Matchbox Window Manager installing into the container. This is just with me of course, no one else has my problems.

PS. What temp work-a-round?

---

### Post by mc4man on 2016-08-01
> **rrnbtter said:**
> 

PS. What temp work-a-round?
It's to keep libertine open for 10 min. or so after creating a container, if closed right away the container is 'created' but not usable.  As it stands libertine gives no indication that it is working & needs time to successfully complete.
(- From what i see atm libertine will not be a viable alternative to using apps like (current) Desktop users expect, too restrictive, too 'contained'.

---

### Post by grahammechanical on 2016-08-01
To quote ventrical from another thread

> I got libertine/desktop apps working on xenial installs now after that  update. It's a really tweaky thing you have to do.  When you startup  libertine it will open install screen. You fill out info and name your  container but it will bounce back to install screen. THE CONTAINER is  being created in the background so just watch your modem light and hdd  light until it is done. Then quit libertine or log off /log on or both  and then open libertine again in the same session and you will see  created container. The "+" add icon will work.  Use the top dialog box  for install debian apps. I choose firefox, nautilus, gedit and psensor  which all work. Then you can try other stuff. *note* Installing snap   packages will most likely break your after a time because I tried. so  you might have better luck getting snaps working from terminal.

Most of all .. be patient while container is being created.

Its not a fix but just a temp workaround that works for me.

The modem lights start and stop a couple of times probably due to heavy load. Just be patient. 



At least I assume that is what you are thinking of, ventrical. And appropriate expression would be: "It does me head in."  ;)

Regards

---

### Post by ventrical on 2016-08-01
> **grahammechanical said:**
> To quote ventrical from another thread



At least I assume that is what you are thinking of, ventrical. And appropriate expression would be: "It does me head in."  ;)

Regards

Yeah .. its real snakes and ladders stuff but I like the way containers work. I call it the "poor man's" unity desktop because I can see the potential for it to use minimal resources .. containers and such. The are options to hide apps ertc.. but not yet working. I can pin apps to the unity panel etc.. If is faster and less clutter. Well it is sort of like a phone/slate  etc.. you know .. you're in and you're out  so it doesn't have to be a complex conglamoration of uneccessary gizzmos.

@mac4man  I disagree. I think the sky is the limit if they get all the parts working right. :)

---

### Post by ventrical on 2016-08-01
> **rrnbtter said:**
> Greetings,
There are some python lxc updates in the stream this morning. I don't have time to check it out so can't give feed back on it.  Regarding the rest of this, I run libertine from the terminal install of the GUI. It lets me get some feed back on what is happening. With Yakkety the problem has been with Matchbox Window Manager installing into the container. This is just with me of course, no one else has my problems.

PS. What temp work-a-round?

You have to wait for container to be built in background. The indicator screens are not working correctly so they are all f/ps.

---

### Post by rrnbtter on 2016-08-01
Greetings,
This works for me. 
Terminal:
 libertine-container-manager create -n NameOfContainer -i/UserName (--password password).
The part in () can be added if wanted. Do to the current problems with yakkety using the terminal gives needed feedback.

---

### Post by rrnbtter on 2016-08-01
Greetings,
Currently Unity 8 is plagued with script problems in python, libertine, click, lib's etc. It is easy to tell that they are hard at it. The whole experience is changing daily. Whether visible or not, every update seems to have something for the Unity 8 side. This should be an exciting couple of months. Incidentally, I had to manually install matchbox-window-manager to get a container completion. FYI

---

### Post by ventrical on 2016-08-01
> **rrnbtter said:**
> Greetings,
Currently Unity 8 is plagued with script problems in python, libertine, click, lib's etc. It is easy to tell that they are hard at it. 

Yes.. I have been saying this all along.

Libertine is creating containers here on unity8 across 4 different machines, both xenial and yakketty. it is just the notification windows of libertine are not working correctly.

Remember if you have this:

```

sudo apt-get install phablet-tools phablet-tools-citrain
citrain host-upgrade 031

```

likely your install of libertine will not work.

regards..

---

### Post by rrnbtter on 2016-08-01
Greetings,
@ventrical

I hope you mean "Remember UNLESS you have this:

> **ventrical said:**
> 
Remember if you have this:
```

sudo apt-get install phablet-tools phablet-tools-citrain
citrain host-upgrade 031

```
likely your install of libertine will not work.

---

### Post by ventrical on 2016-08-01
> **rrnbtter said:**
> Greetings,
@ventrical

I hope you mean "Remember UNLESS you have this:

Nope . It's no good now.

Please see : [http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

Having this will most likely break libertine/containers. It is always good to remove:

```


sudo apt-get remove unity8-desktop-session-mir


```

also .

Rather than purge that ppa I have just created fresh installs and only used the one ppa.

Regards..

---

### Post by ventrical on 2016-08-01
Xapps needs to be clicked twice. opened-closed-opened after each time you install a new debian app. The first time it will show blank but the second time will show all apps and containers.

Regards..

---


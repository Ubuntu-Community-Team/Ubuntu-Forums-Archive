---
title: "Flash player in Opera"
date: 2008-06-18
forum: The Cafe
---

### Post by kaldor on 2008-06-18
I know this is the wrong place to post, but for some reason I can't post in the help section ("Not allowed")

Anyway, my problem is this. I don't like firefox that much, but I need it for flash stuff (youtube etc)

How can I make flash plugin work on opera?

---

### Post by hotweiss on 2008-06-18
For me Opera uses the Flash player plugin that Ubuntu has?

---

### Post by LaRoza on 2008-06-18
> **kaldor said:**
> I know this is the wrong place to post, but for some reason I can't post in the help section ("Not allowed")

Anyway, my problem is this. I don't like firefox that much, but I need it for flash stuff (youtube etc)

How can I make flash plugin work on opera?

Are you posting in the Archive? You can't do that.

It should work on Opera. The flash player from the repo works fine.

What version of Opera, Ubuntu and Flash are you using?

---

### Post by cardinals_fan on 2008-06-18
It works fine here.

---

### Post by LaRoza on 2008-06-18
> **cardinals_fan said:**
> It works fine here.

It could be an older version of Opera.

@OP Try using the latest version, 9.5. Go to the Opera site and download the .deb for it and double click it. It should keep all your settings and themes fine.

---

### Post by mthei on 2008-06-18
You realise you need to use the Firefox plugins for Opera, right?
Tools > Preferences > Advanced > Content > Plug-in options > Change Path > Add > Point it to wherever Firefox keeps its plugins in your Home directory.
There's one link to Firefox plugins, but you need the one in the home directory, not the usr directory.

Unless you did that already, in which case, I'll show myself out.

Also, as mentioned above, you need Opera 9.5 for Flash to work. Versions 9.25 to 9.27 were not compatible with Flash. I don't remember who was to blame for that, but it's settled now, I think.

---

### Post by LaRoza on 2008-06-18
> **mthei said:**
> 
Also, as mentioned above, you need Opera 9.5 for Flash to work. Versions 9.25 to 9.27 were not compatible with Flash. I don't remember who was to blame for that, but it's settled now, I think.

It was Adobe's fault. Opera <9.5 where compatible with Flash, but not the newest versions because Adobe changed something. So older versions of Flash worked and the beta of Opera worked (I used the beta as it was good). Now that 9.5 is out, it can be used safely.

Also, it should "just work" if you don't do anything weird installing.

---

### Post by jakupl on 2008-06-18
does not work for me. Neither old or new.

Which is kind of annoying.

Stupid opera says

> You need to install the Macromedia Flash Player plug-in to view all content on this page. Do you want to download this plug-in now?
But i can't find anything usable at the website.

---

### Post by LaRoza on 2008-06-18
> **jakupl said:**
> does not work for me. Neither old or new.

Which is kind of annoying.

Stupid opera says


But i can't find anything usable at the website.

Install it through the repos, or you can do it from the Adobe site.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

(Select the .tar.gz format)

Save it to home, and run:

```

tar -xvvf install_flash_player_9_linux.tar.gz && cd install_flash_player_9_linux && sudo flashplayer-installer 

```

---

### Post by jakupl on 2008-06-18
It installed in the .mozilla folder but opera has no clue. no luck.

btw.your avatar will be assimilated. Resistance is futile

---

### Post by ice60 on 2008-06-18
you can try running this -
tools>preferences>content>plugin options>find new

you can add in paths there too, make sure you've got libflashplayer.so somewhere in one of the paths -
```
locate libflashplayer.so
```

edit, locate libflashpalyer.so might not work if you have only just installed it. this is why i never help, i'm not able to write any kind of support without editting my posts 100 times lol

---

### Post by jakupl on 2008-06-18
thanks a bunch. it works now.

I am surprised that opera can still maintain its speed, when flash is enabled. I have always loved opera, but never made flash work before.

+100000

---

### Post by ice60 on 2008-06-18
i love opera, you can make 1000s of cool changes to it and make it just how you like it.

---

### Post by LaRoza on 2008-06-18
> **jakupl said:**
> It installed in the .mozilla folder but opera has no clue. no luck.

btw.your avatar will be assimilated. Resistance is futile

Are you saying that it isn't working or that you expect it not to work?

I installed Flash through the repos and it works perfectly (and has for a while) with Opera with no configuring.

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]

---


---
title: "Virus"
date: 2006-02-01
forum: Server Platforms
---

### Post by jm2003uk on 2006-02-01
Just installed the Aegis Viris Scanner and thought i'd scan my system. All was going well till i got this up on screen:

[[IMG]http://img207.imageshack.us/img207/2293/screenshotwarning0qj.png[/IMG]](http://imageshack.us)



info on it: [http://vil.nai.com/vil/content/v_99040.htm](http://vil.nai.com/vil/content/v_99040.htm)


Should i be worried? Shall i delete the said file or is the no harm (since it alters .exe's and im in linux)

---

### Post by Breaks on 2006-02-02
Well all it looks like is that your being the "carrier" of a windows virus... it wont affect you i shouldnt think as you said but you could possibly spread it from your machine to Windows users that you come in contact with.. isnt there any features to resolve the virus? like virus vault or remove it?. Ive never used a linux AV before so i dont know what options / features they have, but your post is making me want to now.

---

### Post by nocturn on 2006-02-02
I suggest to use a second AV to confirm the infection (clamav, antivir, ...)

---

### Post by Breaks on 2006-02-02
Wouldnt using more than one make them conflict?

---

### Post by bjweeks on 2006-02-02
[QUOTE=Breaks]Wouldnt using more than one make them conflict?[/QUOTE]
No.

---

### Post by nocturn on 2006-02-02
[QUOTE=Breaks]Wouldnt using more than one make them conflict?[/QUOTE]
 
No, even on windows you can do that.  The only thing that conflict are the on-access scanners, you need to disable those before running a different AV.

---

### Post by ardchoille on 2006-02-02
I'd be worried about where you got /usr/lib/codecs/vp31vfw.dll from. Is this a file that comes with the w32codecs from one of the repos?

---

### Post by ice60 on 2006-02-02
you can upload the file to Jottis malware scanner and scan there.
[http://virusscan.jotti.org/](http://virusscan.jotti.org/)

it sounds like a false positive which they can't be bothered, or aren't able, to correct.
[http://www.ubuntuforums.org/showthread.php?t=85385](http://www.ubuntuforums.org/showthread.php?t=85385)

---

### Post by jm2003uk on 2006-02-02
[QUOTE=ardchoille]I'd be worried about where you got /usr/lib/codecs/vp31vfw.dll from. Is this a file that comes with the w32codecs from one of the repos?[/QUOTE]

The codecs i got using automatix...:-k

The Jottis malware scanner hasn't found anything...

Probably is just a false positive. Cheers for the replys!!

---

### Post by ice60 on 2006-02-02
actually, if it was me i'd give the file to someone to have a look at so you'd know for sure. you can email it to a virus company and ask them. it's normally   submit@ company_name i think.

BTW MM = mass mailer

---

### Post by DoorGunner on 2006-02-02
The magistra.mm virus is located on .exe files not in dll's as picked up by ageis. So not to worry. (According to norton and mccaffee)

According to the agesis site they have trouble with the engine they are using. There will be many false alarms associated with microsoft products.
[http://jodrell.net/projects/aegis](http://jodrell.net/projects/aegis)

I now use F-Prot. It works much better especially with windows mnted products or libraries.

---


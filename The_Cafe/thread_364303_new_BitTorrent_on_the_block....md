---
title: "new BitTorrent on the block..."
date: 2007-02-18
forum: The Cafe
---

### Post by guitarmaniac on 2007-02-18
I just found out about a new BitTorrent program based on Azureus called BitTyrant [http://bittyrant.cs.washington.edu/](http://bittyrant.cs.washington.edu/) that is meant to be up to 70% faster than azureus (though I doubt it).
still it looks interesting.
Does anyone know where I could get a deb of this from???

---

### Post by theslut on 2007-02-18
thanks for the headsup. I don't think you need a deb, just run the jar file.

---

### Post by theslut on 2007-02-18
thanks for the headsup. I don't think you need a deb, just run the jar file.

---

### Post by xopher on 2007-02-18
Dejá vù?

Have to check it out, anything faster than azureus would be nice ;)

---

### Post by guitarmaniac on 2007-02-18
yeah im just not very good at this stuff. tell me if im doing something wrong.
I extracted it to my home folder.
cd /home/luke/azureus
./azureus

it tells me i dont have permission

sudo ./azureus

command not found

im guessing it doesnt know which program to run

sudo sh ./azureus

30: Syntax error: "(" unexpected (expecting "}")

I have come to the conclusion that debs are a good thing :P

---

### Post by koshari on 2007-02-18
iam guessing its a jar file, so you would need a line like ```
java /home/program.jar
```

---

### Post by xmastree on 2007-02-18
Why are you extracting it to /.azureus? Shouldn't it go in its own directory, such as /.bittyrant ?

---

### Post by guitarmaniac on 2007-02-18
@xmastree thats just what the file I unzipped was called, bittyrant is based on azureus so I'm assuming they just didn't bother to change the name.

---

### Post by guitarmaniac on 2007-02-18
still cant figure this damn thing out... maybe I'll just use Tribbler.
I KNOW that has a .deb :P

---

### Post by xmastree on 2007-02-18
yeah, I see that now. I just tried it, but as I was already running azureus instead, it just seemed to open that one. I think.
> 
sudo ./azureus

command not found

im guessing it doesnt know which program to run
Anyway, to run it I had to make the file **azureus** executable.

---

### Post by KaroSHiv0n on 2007-02-18
Will give this a miss. HATE az, its a resource stealing bloated mess, if your looking to alternates to az try klibido or rtorrent :)

---

### Post by guitarmaniac on 2007-02-18
:idea: :idea: :idea: OF COURSE!!!
its always something simple that gets me.
that did the trick, thanks.

---

### Post by Mateo on 2007-02-18
does it load with a splash screen?  i'm not using a bittorrent client that requires a splash screen....

---

### Post by baskus on 2007-04-27
think u need to do a chmod +x azureus for it to run

---

### Post by Jim Link on 2007-04-28
The reason the file is called Azures is that it is a modified version not a totally seperate program.
I have used Bit Tyrant in windows and its is much faster than Azures but I wouldn't say its 70% faste, possibly 50%.  Either way though its still definately worth the change.

---

### Post by MethodOne on 2007-04-30
Just be aware that some private trackers ban this client because it puts leeching at a higher priority than seeding.

---


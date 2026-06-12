---
title: "package request: Lazarus"
date: 2005-05-08
forum: Ubuntu Backports
---

### Post by MadMan2k on 2005-05-08
Lazarus is a Object Pascal RAD IDE - or in other words a Delphi clone.
Everyone, whos has to do Delphi at school will be grateful :)

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

---

### Post by Gandalf on 2005-05-08
[QUOTE=MadMan2k]Lazarus is a Object Pascal RAD IDE - or in other words a Delphi clone.
Everyone, whos has to do Delphi at school will be grateful :)

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)[/QUOTE]
 apparently it's nice, BTW for a C(not C++), PHP and java programmer, is it easy to learn delphi??

---

### Post by linuxn00b on 2005-05-08
[QUOTE=Gandalf]apparently it's nice, BTW for a C(not C++), PHP and java programmer, is it easy to learn delphi??[/QUOTE]

Well, when I started with Delphi I knew a little PHP, and it really wasn't that hard... I however don't know how much it is alike...

In Delphi, you can ie. load a file into a memo (calling this Memo1) like this:
Memo1.Lines.LoadFromFile('somefile.txt');
Very simple :)

And, yeah, I'd really like to see the Lazarus package in the repositorie too :)

---

### Post by Gandalf on 2005-05-08
how to install it from sources? i tried to install fpc so i can run it, but fpc give errors when i run make deb :(

---

### Post by kleeman on 2005-05-08
As mentioned in another thread, if you download the rpms (for lazarus and fpc) and then run them through alien the debs created can be installed using dpkg -i

---

### Post by Gandalf on 2005-05-08
[QUOTE=kleeman]As mentioned in another thread, if you download the rpms (for lazarus and fpc) and then run them through alien the debs created can be installed using dpkg -i[/QUOTE]
 ok thx

---

### Post by MadMan2k on 2005-05-08
[QUOTE=Gandalf]apparently it's nice, BTW for a C(not C++), PHP and java programmer, is it easy to learn delphi??[/QUOTE]
yes - if you dont go mad about the syntax - the semantic is the same;

```

if(foo) {
 //do something
}

vs.

if foo then begin
 {do something}
end;

```

---

### Post by MadMan2k on 2005-05-12
bump

---

### Post by dolson on 2005-05-20
Yeah, um, this would be nice.

Am I totally blind, or is Free Pascal itself not even a part of Ubuntu? I added multiverse and universe and everything, but I still don't see it in there.

Free Pascal is even in Debian Woody!

I run Lazarus at work, and it is amazingly good! I was very shocked at how exact is is, compared to Delphi, at least older versions I used to use during my Windows days. I made a quick Erlang B calculator with it and had no issues whatsoever.

Now I want it at home on my Linux desktop, and my option is to reinstall Debian, or compile from source/do some alien BS/whatever.

My choices aren't looking too good here.

So with that said, I bump this thread again.

---


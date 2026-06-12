---
title: "creating an ISO image from a .bin image"
date: 2005-01-28
forum: The Cafe
---

### Post by indygreen on 2005-01-28
Hi all,

I have a .bin image that I would like to use to create an ISO image.  Is this even possible?

Thanks.

---

### Post by xpt on 2005-01-28
[QUOTE=indygreen]I have a .bin image that I would like to use to create an ISO image.  Is this even possible?[/QUOTE]

Yes, bin2iso can attempt to recreate cue files for single track data cds.

[http://users.andara.com/~doiron/bin2iso/](http://users.andara.com/~doiron/bin2iso/)

---

### Post by piedamaro on 2005-01-28
It can be done with k3b too, IIRC :)

---

### Post by Rule on 2005-01-28
yup k3b can I just burned one  :-D

---

### Post by Randabis on 2005-01-28
There's also a utility called bchunk in the repositories that can do this.

---

### Post by forkart on 2005-03-02
[QUOTE=indygreen]Hi all,

I have a .bin image that I would like to use to create an ISO image.  Is this even possible?

Thanks.[/QUOTE]

Try MagicISO, You can convert bin to iso using it. it is good[ISO creator](http://www.magiciso.com/tutorials/miso-overview.htm) .

---

### Post by tim1 on 2005-03-02
[QUOTE=forkart]Try MagicISO, You can convert bin to iso using it. it is good[ISO creator](http://www.magiciso.com/tutorials/miso-overview.htm) .[/QUOTE]

This is a windows application  :confused: 

greets, tim

---

### Post by crun on 2005-03-02
If you have the .cue file as well you can also do it with Bchunk

```

$ apt-cache search bchunk

```

edit: didn't read carefully enough, Randabis beat me to it

---

### Post by z_diver on 2006-06-26
[quote=Randabis]There's also a utility called bchunk in the repositories that can do this.[/quote] 
Thanks.  Just converted a full CD from bin/cue to iso in 25 seconds.  

The syntax is "bchunk foobar.bin foobar.cue yourname.iso" and in a few seconds you have your iso.

---

### Post by ohman11 on 2006-07-22
> **z_diver said:**
> Thanks.  Just converted a full CD from bin/cue to iso in 25 seconds.  

The syntax is "bchunk foobar.bin foobar.cue yourname.iso" and in a few seconds you have your iso.

  You get 2 iso's when you do this...which do you burn?

---

### Post by Gen2ly on 2007-05-26
I used bin2iso though it's mentioned with audio it did fine on a non-audio .bin for.  Usage is easy:
```
bin2iso name.cue
```

---


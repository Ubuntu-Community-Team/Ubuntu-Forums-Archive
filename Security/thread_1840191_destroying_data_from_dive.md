---
title: "destroying data from dive"
date: 2011-09-07
forum: Security
---

### Post by SlugSlug on 2011-09-07
Does anyone know the best way to wipe a drive clean? 

(would also be interested if anyone has tried to recover data from a wiped drive)

---

### Post by nothingspecial on 2011-09-07
An incinerator, sledge hammer, acid.......

other than that dban or dd

---

### Post by mmsmc on 2011-09-07
hmm, i never knew you could wipe it clean, other that going to out to no mans land, shredding it and burying it

---

### Post by SlugSlug on 2011-09-07
am not sure abut dban - does the free version only allow 1 pass of 0's ?

---

### Post by dcstar on 2011-09-08
> **SlugSlug said:**
> Does anyone know the best way to wipe a drive clean? 


You use the drive's **Secure Erase** facility that the **hdparm** tool gives you access to.

Do a web search for detailed instructions.

---

### Post by fdrake on 2011-09-08
i doubt you can recover something after a :

```

dd if=/dev/zero of=/dev/hda1 

```

if that's not enough then, the only thing left to do is **Blender**! [http://www.youtube.com/watch?v=lAl28d6tbko&feature=related](http://www.youtube.com/watch?v=lAl28d6tbko&feature=related)

---

### Post by HermanAB on 2011-09-08
The best way is with a sledge hammer.  The second best way is with hdparm.  Everything else is third best.

---

### Post by SlugSlug on 2011-09-08
cheers will look into hdparm

---

### Post by tubbygweilo on 2011-09-08
SlugSlug, this [solved]("http://ubuntuforums.org/showthread.php?t=1839877") thread discussed at length the question of removing data from a drive. You may find it of use.

---

### Post by tgm4883 on 2011-09-09
dd ftw

---

### Post by Cheesemill on 2011-09-09
As above, just overwrite with zeros using:

```
dd if=/dev/zero of=/dev/sda
```

Just be sure that you specify the right drive, it may not be /dev/sda in your case.

---

### Post by SlugSlug on 2011-09-09
> **Cheesemill said:**
> As above, just overwrite with zeros using:

```
dd if=/dev/zero of=/dev/sda
```Just be sure that you specify the right drive, it may not be /dev/sda in your case.


so is zero's enough then? can data be recovered form that ? would /dev/urandom offer more security?

---

### Post by tgm4883 on 2011-09-09
> **SlugSlug said:**
> so is zero's enough then? can data be recovered form that ? would /dev/urandom offer more security?

I've never seen proof (despite contests to prove otherwise) that data can be recovered from a drive after writing zeros to it.

---

### Post by fdrake on 2011-09-09
> **SlugSlug said:**
> so is zero's enough then? can data be recovered form that ? would /dev/urandom offer more security?

as i stated in my post if dd /dev/zero is not enough the only thing left to do is to Blend it!!!!!!
[IMG]http://www.gadgetvenue.com/wp-content/uploads/2010/04/Apple-iPad-Will-it-Blend.png[/IMG]

jokes aside: is in not possible to recover an overwritten (with zeros) hdd .
zero is just a value .

---


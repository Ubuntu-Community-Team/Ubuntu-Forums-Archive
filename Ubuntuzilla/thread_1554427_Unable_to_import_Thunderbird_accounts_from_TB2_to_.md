---
title: "Unable to import Thunderbird accounts from TB2 to TB3"
date: 2010-08-16
forum: Ubuntuzilla
---

### Post by nolanpro on 2010-08-16
I searched and searched but I cant find an answer to this. I upgraded TB2 to TB3 in Jaunty using the command "sudo apt-get install thunderbird-mozilla-build"

TB3 Installed correctly but none of my accounts were migrated from TB2. I tried Tools > Import > All Settings but it when it says "... and other settings from:" the box is blank and I can not continue.

My TB2 settings folders is ~/.mozilla-thunderbird and TB3 is ~./thunderbird

Any way to do this? I have around 20 accounts and it would be hell to have to manually add them all.

Thanks!

---

### Post by nanotube on 2010-08-18
Hi
Simple: close thunderbird... then rename your .mozilla-thunderbird directory to simply .thunderbird, and start thunderbird. It will now automagically detect all you settings and mail.

(of course, make backups before doing anything :) )

---

### Post by nolanpro on 2010-08-18
By Golly you're right! Thanks! The folder structure looked so different I didn't think it would work. Thanks!

---

### Post by nanotube on 2010-08-18
> **nolanpro said:**
> By Golly you're right! Thanks! The folder structure looked so different I didn't think it would work. Thanks!

you're welcome, enjoy tb3 :)

---

### Post by Hakunka-Matata on 2010-09-30
>  nanotube      
Re: Unable to import Thunderbird accounts from TB2 to TB3
Hi
Simple: close thunderbird... then rename your .mozilla-thunderbird directory to simply .thunderbird, and start thunderbird. It will now automagically detect all you settings and mail.

(of course, make backups before doing anything ) 

Thanks so MUCH nanotube, since this is SOLVED, does it now get marked as such or am I thinking of some other forum?  Thanks again

---

### Post by nanotube on 2010-10-03
> **Hakunka-Matata said:**
> Thanks so MUCH nanotube, since this is SOLVED, does it now get marked as such or am I thinking of some other forum?  Thanks again

mm well ideally the original poster would mark it as solved... but i guess i can give it a try. :)

---


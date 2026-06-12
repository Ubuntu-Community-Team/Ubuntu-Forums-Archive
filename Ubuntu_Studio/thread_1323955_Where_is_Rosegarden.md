---
title: "Where is Rosegarden?"
date: 2009-11-12
forum: Ubuntu Studio
---

### Post by Triphido on 2009-11-12
I'm using UbuntuStudio 9.04. Documentation says that instalation DVD brings Rosegarden and PiTiVi but I can't find them anywhere. I tryed to use DVD as repository but there are no packages with these names. How can I get Rosegarden and PiTiVI? Why documentation lies? 

I haven't Internet connection, so i can't use *apt-get*. 

Thank you!

---

### Post by BenAshton24 on 2009-11-12
try running:
```
rosegarden
```
in the terminal, if nothing happens then it's probably not installed. you could also check usr/share and see if there is anything there...

---

### Post by Triphido on 2009-11-12
Yeah, I tried to execute rosegarden from command line but it didn't work. I'll try your second solution at home... ¿Any other idea? Thank you BenAshton24.

---

### Post by thorgal on 2009-11-12
sudo apt-get install rosegarden

---

### Post by AutoStatic on 2009-11-12
[It's not on the DVD apparently]("http://ubuntuforums.org/showpost.php?p=8297174&postcount=29") so you have to get it somewhere else unfortunately.

---

### Post by markbuntu on 2009-11-13
If you have internet access from another machine and a usb stick or something you can get the packages only and put them on the usb stick and transfer them to your other machine that way.

---

### Post by Stochastic on 2009-11-14
> **Triphido said:**
> I'm using UbuntuStudio 9.04. Documentation says that instalation DVD brings Rosegarden and PiTiVi but I can't find them anywhere. I tryed to use DVD as repository but there are no packages with these names. How can I get Rosegarden and PiTiVI? Why documentation lies? 

I haven't Internet connection, so i can't use *apt-get*. 

Thank you!

I'd love to know what documentation you're talking about so that it can be fixed.

Rosegarden and PiTiVi were both taken out of the DVD a few releases back.

If you don't have an internet connection, you can get these programs by downloading the .deb file from [http://packages.ubuntu.com](http://packages.ubuntu.com) on a different computer and transferring that file to your Ubuntu Studio computer.  Unfortunately, you'll also need to download all the dependencies as well (many of them are probably installed already, but certainly not all of them).  Once you have the .deb file on your Ubuntu Studio machine you can install it by running ```
sudo dpkg -i rosegarden_file_name.deb
```

---

### Post by RedRat on 2009-11-14
At least for 8.04 it is in the repositories and you can get it via Synaptic. Don't know if it is there for 9.04.

---


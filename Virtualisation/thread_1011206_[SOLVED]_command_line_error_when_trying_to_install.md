---
title: "[SOLVED] command line error when trying to install vmware"
date: 2008-12-14
forum: Virtualisation
---

### Post by mwillams73 on 2008-12-14
I took the time( 24 hours to be exact) to download vmware server 2.0 and used the tutorial to run superuser and install the patches etc, but when i try to extract vmware a window pops up and says: command line error
Whats that all about? All I want to do is run xp in vmware so i can use my zune. I would dual boot like so many others but when i was doing that i always had to tinker with the screen position when i booted xp and vice versa with Intrepid. I tried using virtualbox and everything worked awesomely, the updates installed and the zune software but of course no usb support( and yes i tried all the lil tricks that houndreds of linux users supplied no dice) All i need to do is to get my zune to associate itself with the zune software once that happens I dont need the usb ( wireless is the coolest feature of the zune) I can the boot up xp in vm of some kind and then wirelessly sync the zune, but vmware refuses to install, SOOOOO what do i do?

---

### Post by mwillams73 on 2008-12-14
Sorry i forgot to thank anyone who can help in advance, this is very important to me I love just about everthing about ubuntu and hate that my xp machine messed up and i had to reinstall every month or so. I read that some people were trying to get zune, Ipod, zen etc natively working on linux and Ubuntu, does anyone know if thats going to happen cause I dont want throw my zune away or go back to windows and besides theres no replacing a zune or Ipod when it comes to multimedia players none of the other players have what my zune has.

---

### Post by Dedoimedo on 2008-12-15
Hello,

Do you mind posting the exact error you get.

Some general tips:

To install vmware server successfully, you'll have to do a bit of compiling. For that, you need the build-essential package.

```

sudo apt-get install build-essential

```

Next, do not use the rpm, use the archives to install.

Furthermore, I recommend server 1.0.x and not 2.0, because it's faster, slimmer and uses a much better, more intuitive interface.

Dedoimedo

---

### Post by mwillams73 on 2009-01-09
Sorry i forgot to mark this as solved way back when and to say thanks, I actualy ditched ubuntu in favor of my zune but now that its dead( my zune) I can fully enjoy the intrepid expeirience!

---


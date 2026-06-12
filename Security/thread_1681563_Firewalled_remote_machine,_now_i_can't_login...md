---
title: "Firewalled remote machine, now i can't login.."
date: 2011-02-04
forum: Security
---

### Post by mrhyde03 on 2011-02-04
So, i have a remote ubuntu machine that i normally use NX Client to log into. I decided to turn on the firewall before allowing any ports (yeah yeah..).. now I cannot log in. I turned it on by "ufw enable". I do remember seeing the CUPS server was already allowed which uses port 631.. just wondering if theres any hope for it. remote desktop was the only way for me to access it.

if anybody has any ideas for me to get into it, then awesome.

ubuntu 10.04

---

### Post by CharlesA on 2011-02-04
If the firewall is blocking all connections, the only way to fix it is to either get console access, or reboot it and hope the firewall resets after it boots up.

---

### Post by stlsaint on 2011-02-05
If its thru a providing company than have them get access into it and turn it off or open up port 22 for ssh (if its already installed). Or the same with if you have a friend or someone who can do it for you also at the machine. Either way poses a risk because someone has to get root access to your machine. You should really do more research on this prior to making changes as such. I cant blame you on the mistake though cause i have locking myself out of machines playing with firewalls and such but they were local for me.:guitar:

---

### Post by mrhyde03 on 2011-02-08
Ok. I got it opened back up. It was a VM at my university we are using in our Network Security class. We had to use the console upstairs in the server room.

Thanks!

---


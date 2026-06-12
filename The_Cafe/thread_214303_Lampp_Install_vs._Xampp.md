---
title: "Lampp Install vs. Xampp"
date: 2006-07-12
forum: The Cafe
---

### Post by Johnsie on 2006-07-12
What's the difference between an Ubuntu Lampp install and installing Xampp manually on a desktop install?

---

### Post by lapsey on 2006-07-12
i wasn't aware there was an Ubuntu Lampp install..

XAMPP, the all-in-one LAMP project, used to be called LAMPP. Are you referring to LAMP?

All I know is that XAMPP is great because it takes only a few commands to get a fully integrated LAMP system up and running. Installing the components seperately has typically been quite difficult.

---

### Post by Johnsie on 2006-07-12
Yeah, I use Xampp too sand find it easy to install... I think Lamp is one of the optional install types of some of the alternate intall cd's. I can't remember whether it was an XUbuntu cd or an Ubuntu cd though...


Is it just that it installs things in dereerent folders?

---

### Post by daniel of sarnia on 2006-07-12
It's an option on the server cd when you install.

---

### Post by mech7 on 2006-07-12
Does XAMPP work ok with you? When i run it localhost does not work with me ](*,)

---

### Post by Johnsie on 2006-07-12
Xampp/Lampp works fine for me.... I've had problems doing [http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1) on some non-Ubuntu machines but you can get around that by using a proxy in your browser.

Can you connect to the site from other computers on your network? If not then your server might not be running. You can make the Linux version of Xampp start at boot time by doing the following in terminal:

> cd /etc/rc2.d
The example on the site gives you rc3 as an example but since Ubuntu is a debian based you have to use rc2


> 
sudo ln -s /opt/lampp/lampp S99lampp
sudo ln -s /opt/lampp/lampp K01lampp


---


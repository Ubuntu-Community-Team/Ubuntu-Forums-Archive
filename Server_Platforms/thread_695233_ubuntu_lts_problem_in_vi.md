---
title: "ubuntu lts problem in vi"
date: 2008-02-12
forum: Server Platforms
---

### Post by psychobeauty on 2008-02-12
hello i start setting up the lts serer using this tutorial, [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)


the problem is that on network configuration vi /etc/network/interfaces

i dont know how to make the changes and return to the command menu.


howdoesvi workhow tochange save and escape???



thanx alot

---

### Post by LaRoza on 2008-02-12
```

:w   == save
:q    == quit
:wq == save and quite

```

---

### Post by yabbadabbadont on 2008-02-12
You can use nano instead.  It is quite a bit easier to use for inexperienced users.

---

### Post by psychobeauty on 2008-02-12
hello i start setting up the lts serer using this tutorial, [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)


the problem is that on network configuration vi /etc/network/interfaces

i dont know how to make the changes and return to the command menu.


howdoesvi workhow tochange save and escape???



thanx alot

---

### Post by dcstar on 2008-02-12
> **psychobeauty said:**
> hello i start setting up the lts serer using this tutorial, [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)


the problem is that on network configuration vi /etc/network/interfaces

i dont know how to make the changes and return to the command menu.


howdoesvi workhow tochange save and escape???



thanx alot

vi is a pain to use, do this:

```
sudo nano /etc/network/interfaces
```

---

### Post by psychobeauty on 2008-02-12
thanx for the codes that help me....



nano??explaine please

---

### Post by p_quarles on 2008-02-12
Threads merged. Please do not cross-post.

---


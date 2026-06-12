---
title: "ubuntu core in virtualbox on a mac"
date: 2017-10-24
forum: Virtualisation
---

### Post by macwolter on 2017-10-24
Hi together,

I have the following problem: I want to run ubuntu core in a virtual box on my Mac so that I can install a Nextcloud snap. I was very happy with that on my Ubuntu desktop.


But I can't manage to enter my e-mail address in the terminal at the boot of ubuntu core: there is no @ in the VM! copy and paste do not work either. Can't start ssh and can't get on with the installation.

Who can help me? I despair!

Thank you very much

Matt

---

### Post by slickymaster on 2017-10-24
Thread moved to **Virtualisation** for a better fit

---

### Post by macwolter on 2017-10-24
Thanks, thought I was new and it was up to me

---

### Post by Kirboosy on 2017-10-25
Welcome to the forums!

Why don't you try to run the [Ubuntu Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") instead of core? After installing minimal you can manually install the snap utility with the following command

```
sudo apt install -y snapd
```

Hope that helps!
~Caboose

---

### Post by macwolter on 2017-10-28
Thank you very much, that is what I’m looking for - I’m happy.

P.S. for the @ you need shift - 2, but I cannot login to ubuntu core on a vm on mac, equal minimal is better, thanks a lot

---


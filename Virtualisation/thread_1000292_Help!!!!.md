---
title: "Help!!!!"
date: 2008-12-02
forum: Virtualisation
---

### Post by eival on 2008-12-02
[IMG]http://i36.tinypic.com/212foy0.png[/IMG]

this just started appearing today when i tried to start my windows VM, i hadnt made any changes from my last usage and i dont understand the directory its telling me to run.

please help!

---

### Post by HotShotDJ on 2008-12-02
If this is the version that you get SUN (I think it is based on the screenshot), all you have to do is open a terminal (Applications --> Accessories --> Terminal) and then run the following:```
sudo apt-get install build-essential
sudo /etc/init.d/vboxdrv setup
```

---

### Post by eival on 2008-12-02
> **HotShotDJ said:**
> If this is the version that you get SUN (I think it is based on the screenshot), all you have to do is open a terminal (Applications --> Accessories --> Terminal) and then run the following:```
sudo apt-get install build-essential
sudo /etc/init.d/vboxdrv setup
```

thank god!

i thought everything was lost, do you know what caused this issue?

was it just a kernal update?

---

### Post by HotShotDJ on 2008-12-02
> **eival said:**
> thank god!

i thought everything was lost, do you know what caused this issue?

was it just a kernal update?Yeah... it was just a kernel update.  The SUN version will usually detect and install the proper module when you first install VirtualBox.  But when there is a kernel update, you'll have to rebuild the module.  Fortunately, they give you a pretty easy way to do it, once you know the magic.  (BTW, next time you can leave out the part about installing build-essential now that you've got it on your system .... just remember to install it again if you ever reinstall your system.)

---


---
title: "Remove VirtualBox"
date: 2012-03-17
forum: Virtualisation
---

### Post by carusoswi on 2012-03-17
So, I installed VirtualBox a week or so ago.  Now, I would like to remove it.  I have removed the virtual machines that I created.  How do I remove the program?

I can list my directories in a terminal, but cannot navigate to or remove the one that is listed as VirtualBox VMs.

I get no such file or directory.

I cannot get VB to come up under the software center, either.  Usually, I remove an application by brining it up in the Software Center, then, merely clicking 'remove' or 'uninstall' (can't remember which).

Help would be greatly appreciated.

Thanks.

Caruso

---

### Post by winh8r on 2012-03-17
Try 

```
sudo apt-get remove virtualbox-ose --purge
```

in the terminal

---

### Post by synaptix on 2012-03-17
@OP

Did you install Oracles Virtualbox from their website?

---

### Post by carusoswi on 2012-03-17
Thanks for the replies.  I do not remember how I installed this application, and I tried the terminal commands suggested.  Ubuntu runs the commands, then reports that the application was not installed, so it was not removed.

Yet, I can use Unity to invoke the application, an she pops up plain as day.

I received a message from VB that a newer version was available, and I downloaded but have not installed it.  Would like to make certain I have uninstalled the existing version first.

Thanks again for the replies, but I remain stumped.

Caruso

---

### Post by synaptix on 2012-03-17
> **carusoswi said:**
> ...

Try:

```
sudo apt-get remove virtualbox* --purge
```

---

### Post by winh8r on 2012-03-17
You may need to run this command if you installed from a source other than the Ubuntu repositories:


```
sudo ./VirtualBox.run uninstall
```


Worth a try.

Hope it helps you.

---

### Post by carusoswi on 2012-03-18
Seems to have worked this time.
Thanks for all the replies/suggestions.
Caruso

> **synaptix said:**
> Try:

```
sudo apt-get remove virtualbox* --purge
```

---

### Post by Jesua on 2012-08-01
> **carusoswi said:**
> Seems to have worked this time.
Thanks for all the replies/suggestions.
Caruso

It works... thanks...

---

### Post by apyoung88 on 2013-05-26
> **synaptix said:**
> Try:

```
sudo apt-get remove virtualbox* --purge
```

I had the same issue, this solved it for me, thanks.

---

### Post by sahabcse on 2013-05-31
Try:

Code:

sudo apt-get remove virtualbox* --purge

---

### Post by bdarblay on 2013-07-09
> **sahabcse said:**
> Try:

Code:

sudo apt-get remove virtualbox* --purge

Great! The above didn't work but this did! Many thanks!

---


---
title: "Get System Info"
date: 2007-11-28
forum: The Cafe
---

### Post by Black Mage on 2007-11-28
I'm trying to write a program that can log into a computer on my internal network ex 192.168.1.34, and then get the system information. Would I need to have a client /server set up? And is there a file where the system information is kept?

And as for system information, I mean things such as Ram, Hard Disk Space, Operating System, computer manufactur, model, etc. And once the information is obtained, it is then returned to a database.

---

### Post by DoctorMO on 2007-11-28
You could use lshw for most of the details. you could also use dohickey-project.com and recode it to output what you need.

---

### Post by Black Mage on 2007-11-28
Is there anything in java or php?

And there is no file where the information is stored? Or a function in a language that returns that kind of information?

---

### Post by bobbocanfly on 2007-11-28
> **Black Mage said:**
> Is there anything in java or php?

And there is no file where the information is stored? Or a function in a language that returns that kind of information?

Ssystem information is kept in the /proc directory. If it is writing a PHP page and outputting information fro files in /proc should be pretty trivial.

You can use the uname command to get some info about your system too.

---

### Post by Black Mage on 2007-11-28
/proc the same for windows?

---

### Post by jinx099 on 2007-11-28
Theres an app called phpsysinfo that reads all your info from /proc and displays it on a webpage.  Maybe this would help for your program.

---

### Post by Black Mage on 2007-12-06
Is there a name for getting information on all computers in a network and then monitor it from one computer?

Basically I'm looking for a solution for obtaining information on all computers on a network. And I'm trying to stay open source.

---

### Post by popch on 2007-12-06
> **Black Mage said:**
> Is there a name for getting information on all computers in a network and then monitor it from one computer?

Basically I'm looking for a solution for obtaining information on all computers on a network. And I'm trying to stay open source.

Wouldn't that fall under the heading of a Simple Network Management Protocol (SNMP)? I think that many devices and OSs support that, and that it adresses your need.

---

### Post by Black Mage on 2007-12-06
Simple Network Management Protocol  doesn't quite do it. I'm talking about specs on each machine. Like users, Operating System, etc.

---

### Post by Black Mage on 2007-12-06
Basically, something like this that exist in open source.

[http://manageengine.adventnet.com/products/asset-explorer/track-it-assets.html](http://manageengine.adventnet.com/products/asset-explorer/track-it-assets.html)

---


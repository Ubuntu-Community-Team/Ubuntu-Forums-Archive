---
title: "Few doubts in &quot;apt-get source&quot; usage?"
date: 2010-01-26
forum: Ubuntu Dev Link Forum
---

### Post by kapmsd on 2010-01-26
Hi guys!!
I downloaded the source code of apt using apt-get source apt.
The folder I got has the name apt-0.7.6ubuntu13.
But the version of apt my system has is 0.7.9ubuntu17.2 (found using dpkg -p apt).
Why I dint get the source code of apt currently in my system?

---

### Post by Ibidem on 2010-07-13
If you're still looking for an answer, here's mine.

Look in your configuration file (/etc/apt/sources.list), and see if there is a line like this:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main

If so, you will also want this line: 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main
Not commented out, like
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main


Replace "lucid" with your current release.
In general, apt-get source uses the "deb-src " lines, while apt-get install uses the "deb " lines.
Thus, to download source for every package, every line starting with "deb " must be matched by a "deb-src ".

---

### Post by Ibidem on 2010-07-13
I assume you looked at what I wrote?

One thing I didn't mention: BEFORE you use apt-get source, you should run "sudo apt-get-update" so apt-get knows that the source packages exist.

So: 
sudo gedit /etc/apt/sources.list
#Edit appropriately
sudo apt-get update
sudo apt-get build-dep apt                #If you want to compile it.
apt-get source apt

Ibidem

---


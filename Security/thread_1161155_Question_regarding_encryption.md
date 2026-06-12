---
title: "Question regarding encryption"
date: 2009-05-16
forum: Security
---

### Post by Thunderhit on 2009-05-16
Right now I use Windows on my desktop TC and encrypted the complete HDD with Truecrypt. I'm now getting a Thinkpad R400 which I plan to also encrypt.
It however has only a 180GB 5200rpm HDD, not something to be considered fast. Now if I were to fully encrypt it, I guess it would make a somehow serious impact on performance and probably drain the battery life too much. 

Since every program writes its settings etc. in the home folder, unlike most of the Windows program, a full encryption shouldn't be necessary. Of course /home needs to be encrypted. I only want to protect my personal data and settings for programs (like browser stuff) and do not care if another person finds out I use program xyz. Are there other folders that would need encryption, such as /var/log?
So should I use full encryption or only a partial one?

Another important thing: If I have a problem with the laptop and need the data, am I able to get it by putting the HDD it into my windows machine or by booting from the ubuntu live cd or something of that sort? With Truecrypt that wouldn't be a problem, but I have no idea about this program.

---

### Post by tubbygweilo on 2009-05-16
Thunderhit, you could use the alt-install disk to encrypt only the home directory and then encrypt via truecrypt a few directories containing the minimum of data you wish to protect. This I think will impose a minimum of overhead upon your system and when coupled with strong passwords will I hope keep your data safe from prying eyes.

---

### Post by Thunderhit on 2009-05-16
I also thought about this, but I guess it has a too high performance impact, two encryptions for the home folder.

Or do you mean encrypt with Truecrypt folders like /xyz and not /home/user/xyz? Because the first would mean I still cannot access it outside the laptop...
Or are there ways to access the encrypted partitions from outside the system?
And does anyone know how much effects it the battery drain?

edit: is it enough to only encrypt /home? How about those other directories, such as /var/log ? Would be bad if there is somehow critical information stored there. I'm relatively new to Ubuntu/Linux and have no idea what kind of logs are stored there.

---

### Post by HermanAB on 2009-05-17
Howdy,

Software based encryption slows the machine down by about 3%.  You won't notice anything.  You only need to encrypt /home and /swap.  Read 'man swapon' to learn how to encrypt /swap.

Here is how to do it with LUKS:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---


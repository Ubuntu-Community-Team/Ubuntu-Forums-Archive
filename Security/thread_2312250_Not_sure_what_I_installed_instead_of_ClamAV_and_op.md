---
title: "Not sure what I installed instead of ClamAV and openSSL"
date: 2016-02-03
forum: Security
---

### Post by helm10101 on 2016-02-03
Hi,
I downloaded the clamav-0.99.tar.gz from here: [http://www.clamav.net/downloads](http://www.clamav.net/downloads),
instead of simply typing "apt-get install clamav".
What I did next was to extract it to desktop, and following the INSTALL document instructions, I used these commands on terminal :"./configure", but then it told me that openSSL was not installed, so I did this:
"sudo apt-get install openssl", but it still gave me the warning that openSSL was not installed, so I then followed some instruction I found and wrote "sudo apt-get install libssl-dev", then I went to clamav folder and again typed "./configure" and it worked.
Then I wrote "sudo make install" and it''s been running for a long time now without stopping. 
Attached a file of what is currently running non-stop on my terminal after typing "sudo make install"

[IMG]http://i.imgur.com/HyrUq11.jpg[/IMG]

Was doing "sudo apt-get install openssl" and "sudo apt-get install libssl -dev" safe?
Did I do something wrong?

Thanks!


**Edit: Now when I did apt-get install clamav, after i type "sudo freshclam" or "sudo clamscan" it says there are errors!

---

### Post by deadflowr on 2016-02-03
Moved to the ***Security*** sub-forum.

No idea why openssl would be problematic, as it is a default package...

Aside from that, do you know what those clamav errors are?

---

### Post by helm10101 on 2016-02-04
No idea :), I am new to Ubuntu and just following commands and how-to's I find

---

### Post by monkeybrain20122 on 2016-02-04
Well it is building and it may take a long time. Not sure why you want to build from source rather than install the binary from the Software Centre. The -dev file is completely safe, -dev stands for developmental. To compile something from source that requires libwhatever you need to have the headers for libwhatever, the package libwhatever-dev provides that.

BTW, I think after ./configure and then "make "and finally "sudo make install". And if you build from source I would recommend installing the package checkinstall and do "sudo checkinstall" instead of "sudo make install" because, depending on the software it may scatter files all over your system and removing it will be a pain. Checkinstall creates and installs a .deb so you can just remove it with synaptic or the software centre. 

Yeah if you are a new user instead of copying and pasting sudo apt-get blah blah install synaptic and use it to search for, install and update packages. Either install it from the Software Centre or "sudo apt-get install synaptic". The command is only useful if you know exactly the name of the package you want to install.

---

### Post by oldos2er on 2016-02-04
Did you run "make" between ./configure and sudo make install? Why didn't you install it from the repositories?

---

### Post by helm10101 on 2016-02-05
I just went after instructions I found online since I'm new here :)

---

### Post by oldos2er on 2016-02-06
What instructions? Did clamav install properly yet? My 2nd question in post #5 remains, and in light of your other question [here]("http://ubuntuforums.org/showthread.php?t=2312596") I think it's important, assuming you still want to pursue this.

---

### Post by helm10101 on 2016-02-06
> **oldos2er said:**
> What instructions? Did clamav install properly yet? My 2nd question in post #5 remains, and in light of your other question [here]("http://ubuntuforums.org/showthread.php?t=2312596") I think it's important, assuming you still want to pursue this.

Yep, I remember there was "make" in the instructions I followed. (no idea what that means though :) ), I will be more careful next time.
Btw I've reinstalled Ubuntu since then about 3 times (because of my AMD card issue discussed on my other thread)

---

### Post by oldos2er on 2016-02-07
Ok, thank for the follow-up.

---


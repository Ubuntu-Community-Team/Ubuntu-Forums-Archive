---
title: "Planet76 Repository won't authenicate"
date: 2010-10-03
forum: System76 Support
---

### Post by david12 on 2010-10-03
I did a clean install of Lucid on my Ratel Ultra.  As per the instructions I downloaded the 76 driver and installed it. (The http://planet76.com/repositories/ ./ had not shown up in Software Sources on its own.) 

Upon running the System 76 Driver, a notice appeared to the effect that, for my model, all drivers were maintained by Ubuntu.  I took that to mean that nothing in the System 76 driver is relevant to the Ratel Ultra at this time.

I decided to install the Planet76 repository anyway.  So, in Software Software Sources, Other Software I added: "deb http://planet76.com/repositories/ ./". and it took it. The box was checked.  I closed the dialog which updated the repo information. I then received an error to the effect the a public key was not available or no good or something.

The planet76 repo remains in Other Software, with the box checked. I've restarted the system twice, but the Planet 76 repository remains un-authenicated.

What needs to be done about the authenitication? How does one go about it?

Thanks for your help.

---

### Post by chaanakya_chiraag on 2010-10-03
I'm not exactly sure where you are going to get it (check on the Planet76 website), but you need a gpg key which you then import into Software Sources under the Authentication tab.

---

### Post by david12 on 2010-10-03
Thanks, I checked Planet76 and found a file called "system76_dev.pub". I downloaded it selected it using the 'Import Key File...' button in the Software Sources > Authentication dialog. It appears to have taken. So, I'm good to go, I guess.:)

---

### Post by chaanakya_chiraag on 2010-10-05
Yay!! :)  Please mark this thread as solved by going to Thread Tools -> Mark Thread as Solved.  Thanks! :)

---


---
title: "Can not install RedHat(guest) on ubuntu 14.04(host) trough virtualbox"
date: 2015-08-04
forum: Virtualisation
---

### Post by nir_ben_harush on 2015-08-04
hi everybody!
I had a 10 years old book with an installation disk of red-hat and I really wanted to install red hat as a guest on Ubuntu 14.04 LTS trough virtual box.
No matters what I did I did not succeed. After a while I downloaded a new iso file of redhat from the internet I burned it to a dvd and i got the same results as before.
will please someone explain me how to install red hat on virtual box machine, it is very important to me since I have this book and I want to learn red hat.
any links will do also.
Thank you in advance.
Any replies will be appreciably received.

---

### Post by QIII on 2015-08-04
Hello!

"No matters what I did I did not succeed" does not tell us much.

What happened?  What failed?

---

### Post by nir_ben_harush on 2015-08-04
Thank you for your interest!
I define a virtual machine in virtual box with no problem(allocating RAM, allocating disk space etc.) then I get to the moment when I need to start the virtual machine and it asks me for directions  to to iso. file(path) on my computer or on dvd, I comply to the orders and direct the virtual box to the right place for iso. file(sometimes on my hd and sometimes on my dvd) then it seems that it loads the iso file, but instead giving me options to choose language, zone, time and so on it simply load something on the black screen,  which looks like a menu and no matters which option I choose from the menu it does nothing except that it says "it is safe to reboot the machine now". and soon all the pc simply stop responding.
Thank you if you could help me on that. If you need more details I would promptly supply  more details.

---

### Post by howefield on 2015-08-04
Something more up to date isn't an option ?

---

### Post by TheFu on 2015-08-05
A 10 yr old Redhat book isn't really very useful now. RHEL 7.x changes many things - even logging is vastly changed thanks to systemd. Firewalls, system startup, installation, partitioning have all changed drastically in the last 10 yrs.

If you want to learn currently used RHEL stuff - get a CentOS 6.x ISO and a RHEL book that follows that.  You'll need the 7.x CentOS and a RHEL book for that too.

CentOS and RHEL are binary compatible for the same release number. That is the primary purpose of CentOS - to be 100% like RHEL with only the branding/icons being different. Of course, any connections to the RHN won't work with Cent.

Anyways - definitely get a fresh CentOS download before you waste much time.

I don't use virtualbox anymore, but I have CentOS 6.6 and 7.1 running under KVM + libvirt happily.  I've been following the ACC learning documents to improve my RHEL skills: 
* [http://www.bob-carnaghi-online.net/rhce6/index.html](http://www.bob-carnaghi-online.net/rhce6/index.html)
* [http://www.linuxtopia.org/online_books/rhel6/](http://www.linuxtopia.org/online_books/rhel6/)
and the cert objectives are here: [http://www.certdepot.net/rhcsa-exam-objectives/](http://www.certdepot.net/rhcsa-exam-objectives/)

---

### Post by SeijiSensei on 2015-08-05
I have a CentOS 7 virtual machine running in VirtualBox on Kubuntu 14.04.  It installed without a hitch from the downloaded ISO image.

---

### Post by nir_ben_harush on 2015-08-06
Hi,
you are truly speaking.
I would try the suggestions as soon as possible, it seems logic what you are saying since I opened the book and it indeed very old , compared to the technology today.
please suggest me should I mark the post SOLVED or might I wait for other replies to pop up in the sake of other people with the same problem.
May be by waiting a little bit more I might get other options which may be productive for other members.
Any way ,for me the solutions suggested were quite satisfactory and applicable.
Thank you for your assistance and your time.
Cheers.

---


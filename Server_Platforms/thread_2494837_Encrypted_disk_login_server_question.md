---
title: "Encrypted disk login server question"
date: 2024-01-28
forum: Server Platforms
---

### Post by Heeter on 2024-01-28
Hi Guys

Sorry stupid question coming your way.

I am putting into service and new headless KVM server in the next couple of weeks, to replace my current headless KVM old hardware.

If I was to install Ubuntu server with disk encryption, would I be able to ssh into it when I need it to reboot? Or do I have to be at the physical keyboard/monitor to get past the disk encryption password, like my workstations? 

Never had a disk encrypted server that I needed to remote ssh into.

Of course internet searches leaves me with more confusion to this question.

Regards

---

### Post by MAFoElffen on 2024-01-28
When I set up an Encrypted Server and I intend that it might be headless (or in a server rack somehwere), I generate a keyfile to write to a USB key, then add that key to a keyslot and the crypttab. Then to set a server to do autologin through getty.  That way an operator can insert the USB key into the Server, and it can reboot successfully without interaction... Which would get you into it remotely via ssh.

If you tailor your google query to that, you should find many answers to do that... or I search on my username this forum on LVM encrypted LVM and there are a few posts where I showed people how to do that. Found one: [https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569](https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569)

Then a few answered where people wanted a user autologged in after reboot via getty: [https://ubuntuforums.org/showthread.php?t=2480429&p=14117734#post14117734](https://ubuntuforums.org/showthread.php?t=2480429&p=14117734#post14117734)

---

### Post by Heeter on 2024-01-28
Thank you, Thank you, Thank you

and For the links as well, this will be incredibly helpful for me.

Regards

---


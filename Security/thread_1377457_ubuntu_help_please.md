---
title: "ubuntu help please"
date: 2010-01-10
forum: Security
---

### Post by anas2009 on 2010-01-10
[SIZE=3][B]i have ubuntu 9.10 installed with only root account 
the problem that many people use my room
i have some  questions about ubuntu security and i need and serious answers please

[COLOR=DarkRed][COLOR=Red]first question :[/COLOR]

[/COLOR] i want to know if someone take my hard disk where ubuntu installed and he put it in another computer can he get my files and can he know my passwords like dns config ext...

[COLOR=Red]second question:[/COLOR]

how to secure ubuntu boot loader to protect my pc ; i think if someone use recovery mode he will get into my ubuntu and do what he want....
[COLOR=Red]
final question:
[COLOR=Black]
how can i hide or encrypt a file in ubuntu

and thx.
[/COLOR]

[/COLOR]

[/B][/SIZE]

---

### Post by tubbygweilo on 2010-01-10
Anas, if someone has physical access to your computer then they can do whatever they wish. 

You can encrypt the whole disk as this will stop people examining your data and can de accomplished by using the alt install Ubuntu disk. Other methods exist that will allow you to encrypt your disk but I will let others advise you on this topic.

The third party application [Truecrypt]("http://www.truecrypt.org/docs/?s=tutorial") is often used to both encrypt and hide files within an Ubuntu system.

---

### Post by anas2009 on 2010-01-10
this truecrypt is unde windows i need to encrypt my ubuntu pc please

---

### Post by TwoWordz on 2010-01-10
First of all here is some [documentation ]("http://catb.org/~esr/faqs/smart-questions.html")on how to ask a question online.

Second, the security on ubuntu or any linux is as good as you make it. Using only the root account is insecure and I suggest you make your regular account. 

With your current setup, someone could just take your hard drive and mount it in another linux system or boot a live cd and they will have access to all your files. Also, most of the configuration files on the system are readable from a regular user account. You can prevent this by chmod'ing the files and changing the setting to your liking.

You can setup a password on the bootloader during installation. You can also do it later by editing the grub configuration. I suggest you do a google search for "grub password".

Finally, you can encrypt your entire drive during this installation and require a password to access it. This should help with your privacy worries. 

TW

---


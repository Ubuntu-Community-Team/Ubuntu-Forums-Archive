---
title: "securing the computer physically"
date: 2011-09-15
forum: Security
---

### Post by jsvidyad on 2011-09-15
Hello,

  I use kubuntu 10.04 . I have a question regarding security of the computer. Right now, I have set up a password which has to be entered to change BIOS settings. I'd like to make the computer more secure. Essentially, I want to make it impossible or atleast difficult and time consuming for someone with physical access to the computer to be able to get into the computer as root or any other user.

  How do I go about securing my computer in this way?

Thank you in advance for your help.

---

### Post by mycroft on 2011-09-15
You would have to make it physically impossible to even open the cabinet then - otherwise someone could get to the CMOS battery on the motherboard. This battery powers the components that store and maintain BIOS settings, your BIOS password, if any, among them. Remove it temporarily and the BIOS password is removed.

---

### Post by lykwydchykyn on 2011-09-15
Encrypting the hard drive would be a good start.

You can password-protect GRUB entries too, to prevent people editing the boot entries.

---

### Post by sh4d0w808 on 2011-09-15
Put your computer into a safe/vault and lock it with a Kensington if applicable.

---

### Post by fdrake on 2011-09-15
just leave your computer inside fort-knox. No one will be able to get inside, not even the goverment!!:P
[img]http://www.mostinterestingfacts.com/wp-content/uploads/2010/11/fort-knox.jpg[/img]

security measures depends on how important is your data. is your data worth be erased if someone steals your laptop? 

1. keep your os in a separate partition from your home/user partition. Encrypt the home partition directory.

2. you can write a script that after a total of failed logins (or after you enter a specific password) will wipe out the home partition in the background... Make sure you write a message at the login saying password is :bla-bla. so the person will attempt to login using that specific word.

3. I would not put any password at bios or at grub, since they are very easy to bypass. Also you need the attacker to get to the login session to input that word.

ahh and don't forget to install an auto-explosive device so that you will be sure it will never be recovered!  :D

---

### Post by tubbygweilo on 2011-09-15
Your kit isolated within a secure enviroment is a good place to start but remember some screens also have usb access and someone with a better mind than mine may be able to subvert your measures via this route. Secure containers with alarmed locks that may contact you or record unauthorised access are available it is just how far do you wish to take things?

As stated enctypting data also helps as it adds to the time needed for someone to do the dirty deed and this in itself may act as some form of deterant.

---

### Post by Sc0urgeTR on 2011-09-15
As far as tampering with hardware you can get computer cases with locks to stop them from being opened. 

As stated above hard drive encryption. But also making sure your computer goes to a screen saver that requires log in to re enter is useful whilst the OS is running.

Remotely connecting to your computer via a smart phone with alerts for activity isn't a bad option. It does leave security a little wide in my opinion (if someone was to hack the connectiong (not really likely unless you've pissed off someone that knows their way around password hacking)) to having an Internet gateway to remotely use your device but it's effective and useful.

Ubuntu doesn't allow for root access specifically so you could use that. Make all your users low level operators and never use root so even if anyone does gain access to your account it has limited access.

you could mod your case a bit. drill a couple of large holes and stick a bike chain through it  :D

get some liquid nitrogen and freeze your case to your work station.

Cammoflage your computer case and hide it in amongst some plants.

have a sign on your computer that says if you use this computer it means you are clearly enjoy incest.

nail your mouse to the desk.

glue pubic hair to your mouse. 

have the computer running in command line interface to scare off the windows kiddies.

---

### Post by Sef on 2011-09-15
Where is the computer? 

How many people will have physical access to  it?

You can overdo security too. You need to decide how much security will be needed based on those two questions, in part. 100% is impossible, so you have to decide what is the right amount for you.

---

### Post by foureyesboy on 2011-09-15
1) some notebook computers have BIOS startup password, together with BIOS supervisor password.
2) disable USB booting from BIOS.
3) GRUB password.
4) disable auto login.
5) encrypt the filesystem.
6) and don't use trivial passwords.

---

### Post by jsvidyad on 2011-09-15
Hello,

  I'd like to set up the passwords to further secure the computer. Can someone please tell me what passwords, besides BIOS settings password and ubuntu user accounts passwords, I have to set up in order to decrease the chances of someone with physical access to the computer being able to use the computer?

---

### Post by Dangertux on 2011-09-15
The solution involving glue and a mouse made me laugh...hard

Basic physical security. 

-- lock your computer case (make sure it is made of a strong material)
-- bios password
-- boot password
-- boot loader password
-- disable booting from anything other than the hard drive
-- bolt computer to desk/floor
-- lock your doors and windows
-- have strong doors and windows
-- home security system
-- fence around home
-- big dog inside of fence (optional)
-- don't allow anyone near your computer with a teensy HID

---

### Post by jsvidyad on 2011-09-15
I also have set up the BIOS so that it can boot only from the hard drive and from nothing else. That's why I have a BIOS password so that someone can't change that.

  What I'm looking for is ways to prevent a casual intruder from being able to get into my computer and change stuff or steal data. I realize that a person who has physical access to my computer and has the intention of doing stuff on the computer can always do that.

   I am just asking what reasonable precautions I must take. I am basically asking what passwords I need to set up for this purpose.

---

### Post by jsvidyad on 2011-09-15
> **Dangertux said:**
> The solution involving glue and a mouse made me laugh...hard

Basic physical security. 

-- lock your computer case (make sure it is made of a strong material)
-- bios password
-- boot password
-- boot loader password
-- disable booting from anything other than the hard drive
-- bolt computer to desk/floor
-- lock your doors and windows
-- have strong doors and windows
-- home security system
-- fence around home
-- big dog inside of fence (optional)
-- don't allow anyone near your computer with a teensy HID

Can you tell me how I go about setting up the passwords you mentioned? I use grub2 rather than grub.

---

### Post by Dangertux on 2011-09-15
> **jsvidyad said:**
> Can you tell me how I go about setting up the passwords you mentioned? I use grub2 rather than grub.

For boot and bios passwords consult your motherboard documentation or check your bios settings.

For boot loader passwords with Grub 2 check out this forum thread fairly detailed explanation.

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by sh4d0w808 on 2011-09-16
You have to know that ALL BIOS vendors using master passwords which can open your closed BIOS. This means that if the attacker seriously wants your datas, he will get them. Furthermore, if somebody removes your BIOS battery, all BIOS settings will be reset to default. If the attacker will have physical access to your machine, then you'll be catched.

On the Internet, there are two kinds of machines: already hacked and will be hacked. You can do a lot of steps to slow down attackers but if somebody specifically wants your datas, you will loose. This is the main reason, why a lot of people do security steps.

---

### Post by bodhi.zazen on 2011-09-16
> **jsvidyad said:**
> Hello,

  I use kubuntu 10.04 . I have a question regarding security of the computer. Right now, I have set up a password which has to be entered to change BIOS settings. I'd like to make the computer more secure. Essentially, I want to make it impossible or atleast difficult and time consuming for someone with physical access to the computer to be able to get into the computer as root or any other user.

  How do I go about securing my computer in this way?

Thank you in advance for your help.

Keep your computer in a locked room and encrypt you data.

---

### Post by zkissane on 2011-09-16
Who's your anticpated threat?  
1) Your parents/roommates/siblings/significant other finding your porn stash?  
2)  Somebody stealing your personal financial data?  
3)  Somebody stealing your small business financial data?  
4)  Somebody stealing your large corporation financial data?
5)  Somebody stealing other sensitive information, trade secrets, billing rates, etc.?

For 1-3, a BIOS password and an encrypted hard disk (or home directory) would be sufficient.  If you keep 4 or 5 on your home PC, you're an idiot.  Also, don't forget this:

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

(the alt-text for this on [XKCD's site]("http://xkcd.com/538/") is also particularly relevant)

---

### Post by archolman on 2011-09-16
There is some excellent advise on the CERN Computer Security page:
> 
[http://security.web.cern.ch/security/recommendations/en/index.shtml](http://security.web.cern.ch/security/recommendations/en/index.shtml)

for all levels of user.

---

### Post by westie457 on 2011-09-16
Here is a novel suggestion.

Use the hard drive for data only with encryption and no OS installed, and install the OS to a USB stick.

---

### Post by archolman on 2011-09-16
> **westie457 said:**
> ...

Use the hard drive for data only with encryption and no OS installed, and install the OS to a USB stick.
Further to this idea, use a caddy, & secure your HD in an HD safe when unattended. This is, or was, standard practise with task-critical installations.

---

### Post by jsvidyad on 2011-09-16
How do I set up a password for grub2(not legacy grub)?

---

### Post by lykwydchykyn on 2011-09-16
> **jsvidyad said:**
> How do I set up a password for grub2(not legacy grub)?

See this:

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by Paddy Landau on 2011-09-20
The only solution is to encrypt your data.

Ubuntu comes with a built-in facility to encrypt your home folder. That would suffice. As mentioned already, set your screen saver to lock after (say) 5 minutes of inactivity.

Your password should be at least 10 characters long, with a mix of  lowercase and uppercase letters, digits, and other characters.

Thus, if anyone gets physical access to your computer, your data is safe.

The only way to get past that is to have someone force you to reveal the password (or, if the government really wants your data, to use a supercomputer to crack your password).

Remember to encrypt your backups, too!

---


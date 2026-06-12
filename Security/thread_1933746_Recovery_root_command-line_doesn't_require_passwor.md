---
title: "Recovery root command-line doesn't require password?"
date: 2012-02-29
forum: Security
---

### Post by Dngrsone on 2012-02-29
So I had to boot into Recovery mode today (Ubuntu 10.04 desktop 64), and selected root command-line.

It dropped me right into a command-line with root privileges without asking me for a password.

Is this normal, or did I somehow break the security on my install?

---

### Post by tubbygweilo on 2012-03-01
Dngrsone, normal as anyone with physical access to your kit can do this. Keep your machine safe and away from prying hands and eyes.

---

### Post by winh8r on 2012-03-01
It is normal for the "drop to root shell prompt" to appear in the recovery mode menu, in order to resolve issues with booting that require root privileges.

As tubbygweilo says, this is where the saying "physical access is root access" comes from.

Every computer system is vulnerable when an unauthorized person has physical access to it regardless of whether or not they have a password.

---

### Post by Grenage on 2012-03-01
> **Dngrsone said:**
> So I had to boot into Recovery mode today (Ubuntu 10.04 desktop 64), and selected root command-line.

It dropped me right into a command-line with root privileges without asking me for a password.

Is this normal, or did I somehow break the security on my install?



If you need local file security, you need encryption, or a means of physically securing the machine.

Covering it in cement and placing it in a safe, in a concealed bomb shelter, for example.

---

### Post by arubislander on 2012-03-01
If this behaviour is a cause for concern (as I can imagine it is) it is simple to adjust. After you boot into your normal desktop, open a terminal and type after the prompt:```
$> sudo passwd
```
You will be prompted for your own password to execute the command as root, and then for a password and asked to retype it to confirm. If succesful this will have changed the password for root. From now on when you drop to a root prompt by way of the boot menu you will be asked for the password you just entered.

---

### Post by Dngrsone on 2012-03-01
> **Grenage said:**
> If you need local file security, you need encryption, or a means of physically securing the machine.

Covering it in cement and placing it in a safe, in a concealed bomb shelter, for example.

[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rollin.gif[/IMG]

> **arubislander said:**
> If this behaviour is a cause for concern (as I can imagine it is) it is simple to adjust. After you boot into your normal desktop, open a terminal and type after the prompt:```
$> sudo passwd
```
You will be prompted for your own password to execute the command as root, and then for a password and asked to retype it to confirm. If succesful this will have changed the password for root. From now on when you drop to a root prompt by way of the boot menu you will be asked for the password you just entered.

Thanks for that tidbit, arubislander.

My physical security is pretty good, and I'm the only one in the house who knows Linux anyway (everyone else barely knows how to use a mouse), but having that extra little bit of security might save me from something stupid happening by accident.

---

### Post by cariboo on 2012-03-01
> **Dngrsone said:**
> [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rollin.gif[/IMG]



Thanks for that tidbit, arubislander.

My physical security is pretty good, and I'm the only one in the house who knows Linux anyway (everyone else barely knows how to use a mouse), but having that extra little bit of security might save me from something stupid happening by accident.

You can still do something stupid running as root too.

---

### Post by accessgranted on 2012-03-01
you can remove the recovery option in the grub boot menu but there is still another point of entry even without entering recovery mode.

---

### Post by winh8r on 2012-03-02
Live CD = "root" access

---

### Post by Dngrsone on 2012-03-02
> **cariboo907 said:**
> You can still do something stupid running as root too.

> **accessgranted said:**
> you can remove the recovery option in the grub boot menu but there is still another point of entry even without entering recovery mode.

> **winh8r said:**
> Live CD = "root" access

All very true; been there, and done all of the above.

I know I'd be much safer if I encrypted the drive, but I have this fear of not being able to get back in after some unspecific disaster...

As it is, I crash Ubuntu every other month when I forget to clear out my monthly backups.

Realistically, though. I have few secrets.  The worst that could happen if my laptop were stolen is I'd have to change a couple hundred passwords online and I'll lose some pages from my book.

---


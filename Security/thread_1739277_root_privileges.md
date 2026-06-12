---
title: "root privileges?"
date: 2011-04-25
forum: Security
---

### Post by willchurch on 2011-04-25
I was installing a driver for a printer, when I was asked for the root (administrative) privileges. I typed my password, but the notification says it is wrong. I have no idea what the problem is. Is there any way to determine what the root password is? I assumed it was the same as the password I use for everything else on my computer. How can one determine the root password?

---

### Post by dacoolio on 2011-04-25
On Ubuntu you don't really use root as a user with a password. Instead, you use your own password by prefixing the command with "sudo"

For example, if you want to run "apt-get install python" as root, you actually type:

```
sudo apt-get install python
```

Then you just enter YOUR password, as long as you are a superuser (in the sudoers file) on the computer. Or, if you want to actually log in as root, type this in the terminal and enter YOUR password:

```
sudo su
```

---

### Post by Ryan Dwyer on 2011-04-25
Check your caps lock, check you're pressing the correct keys, then count the number of asterisks in the password box and make sure it's correct.

This is a assuming you're NOT using a terminal with sudo.

---

### Post by CharlesA on 2011-04-25
The root account is disabled by default.

Use sudo instead.

---

### Post by willchurch on 2011-04-25
The prompt for the password is not in terminal, it is in the little step-by-step install thing. I have tried my correct password to no avail. I'm not sure what the deal with it is.

---

### Post by collisionystm on 2011-04-25
I am sure the root account must be enabled for this. I explained how to enable it in a previous post and I received a warning because its against ubuntu policy. Although as stated in their docs, there are times when using root is absolutely necessary. Just think about this....you can set a password with the command
```

passwd username

```
that's all im saying.

---

### Post by zipperback on 2011-04-25
> **collisionystm said:**
> I am sure the root account must be enabled for this. I explained how to enable it in a previous post and I received a warning because its against ubuntu policy. Although as stated in their docs, there are times when using root is absolutely necessary. Just think about this....you can set a password with the command
```

passwd username

```
that's all im saying.


YOU ARE INCORRECT. 

THEY DO NOT NEED TO ENABLE THE ROOT ACCOUNT TO INSTALL SOFTWARE!

You should not encourage users to enable the root account in this manner.

- zipperback

---

### Post by zipperback on 2011-04-25
The original poster has been provided information on how to properly install the software using sudo already.

For example:   sudo apt-get install whatever

In regard to printer configurations however you should try this first: (it may be slightly different depending on your actual installation and version of ubuntu installed).

Click System then Administration then Printing. 

Check to see if the printer is being properly recognized by the system and if so, then you should be able configure the specific printer via this interface.

If this is not working for you , please tell us what the specific manufacturer and model of your printer is.

Thank you.
- zipperback
:popcorn:

---

### Post by collisionystm on 2011-04-25
See this is what I am talking about. People freak out on here at the sheer mention of root like its a voodoo word. And yes zipper, sometimes you need root. It even says it in the ubuntu docs. Did you even read this guys problem? Or did you just freak out as soon as you saw my post? It is completely okay to enable root. Its not okay to use it for everything. Hence the use of sudo. A feature that is just as dangerous.

---

### Post by CharlesA on 2011-04-25
If you need to enable the root account to accomplish something, it's a good idea to disable it again after you are done.

You can use this to 'lock' the root account:

```
sudo passwd -l root
```

In any case the OP hasn't told us anything other then "it prompts for a password"

What are you trying to install, and how are you trying to install it?

---

### Post by bodhi.zazen on 2011-04-25
> **collisionystm said:**
> People freak out on here at the sheer mention of root like its a voodoo word.

Judging from your post, sometimes people freak out at the word "sudo" as well.

Ubuntu uses sudo by default and we prefer if you teach people to use sudo first, teach them linux permissions, etc.


Please enable the root account only if absolutely necessary. The information (how to enable the root account) is easily available with even a cursory Google search, so we do not need to provide poor information on these forums (such as enabling the root account).

Sometimes when all you have is a hammer, everything looks like a nail.

---

### Post by willchurch on 2011-04-25
I was trying to install a lexmark driver from their website. The driver installation prompted me for the root password. I used my password, but it did not work.

---

### Post by CharlesA on 2011-04-25
> **willchurch said:**
> I was trying to install a lexmark driver from their website. The driver installation prompted me for the root password. I used my password, but it did not work.
Which driver specifically?

---

### Post by willchurch on 2011-04-25
The debian version (not the red hat one) of the driver for a Lexmark X5650 printer.

---

### Post by CharlesA on 2011-04-25
> **willchurch said:**
> The debian version (not the red hat one) of the driver for a Lexmark X5650 printer.

Is it this one?

[http://support.lexmark.com/index?page=product&linkSelected=node0&locale=EN&userlocale=EN_US#2](http://support.lexmark.com/index?page=product&linkSelected=node0&locale=EN&userlocale=EN_US#2)

Looks like you need to unzip it and then run it in a terminal (use sudo)

---

### Post by collisionystm on 2011-04-25
Sudo is no better. You can still damage a system. I see absolutely no safety in using it.

---

### Post by willchurch on 2011-04-25
> **CharlesA said:**
> 

Looks like you need to unzip it and then run it in a terminal (use sudo)

How do you run it in terminal with sudo?

---

### Post by CharlesA on 2011-04-25
> **willchurch said:**
> How do you run it in terminal with sudo?
What's the filename?

```
sudo ./filename.deb.sh
```

---

### Post by willchurch on 2011-04-25
I get the same thing.
I'm not sure my problem is understood exactly. The driver opens successfully, I click agree to a bunch of legal malarkey then I get the attached image.
I try my password, then am told it is not the right one.

---

### Post by collisionystm on 2011-04-25
Sudo passwd root

Enter a new passcode

Run your program, use the passcode

Sudo -l root

That's an L in that command

---

### Post by CharlesA on 2011-04-25
Yeah, looks like it's using it's own install program.

Give the above post a shot and see if it works.

---

### Post by willchurch on 2011-04-25
> **collisionystm said:**
> Sudo passwd root

Enter a new passcode

Run your program, use the passcode

Sudo -l root

That's an L in that command

The program ran successfully using the password change, but the "sudo -l root" command got me an error message.

---

### Post by CharlesA on 2011-04-25
It should be:

```
sudo passwd -l root
```

---

### Post by willchurch on 2011-04-25
Ah, I see.
Thank you very much.

---

### Post by collisionystm on 2011-04-25
Sorry, the droid is to blame for the capital letters!

---

### Post by CharlesA on 2011-04-25
> **willchurch said:**
> Ah, I see.
Thank you very much.

You are welcome. :)

> **collisionystm said:**
> Sorry, the droid is to blame for the capital letters!

Darn those smartphones! :lol:

---

### Post by lisati on 2011-04-25
BTW, information about sudo can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


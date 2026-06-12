---
title: "Yubikey Desktop Authentication Software problem on Ubuntu18"
date: 2020-05-03
forum: Security
---

### Post by matrix012 on 2020-05-03
Fellow Forum Members,
It seems my Ubuntu Bionic Beaver 18.04 has a problem with the Yubico Desktop Authentication (YDA) software that supports my new Yubikey 5 Series two factor authentication security key. 

In Windows10 the YDA software works perfectly. I just plug the security key into my USB port and the YDA app promptly shows a blue "ADD" key button once it detects the key is touched. 

In contrast, my Ubuntu does not show the blue "ADD" button. However, it does indicate the security key is inserted but does not go beyond that. The YDA app I'm using was downloaded from the Yubico link below and it is packaged as an AppImage file: 

 [https://www.yubico.com/products/services-software/download/yubico-authenticator/#download_here](https://www.yubico.com/products/services-software/download/yubico-authenticator/#download_here)

Does anyone out there know what software I need to add to my Ubuntu so it correctly supports Yubikey two factor authentication? I ask because the instructions Yubico provides in the link below is not helpful at all:

[https://support.yubico.com/support/solutions/articles/15000006419-using-your-yubikey-with-authenticator-codes#configure](https://support.yubico.com/support/solutions/articles/15000006419-using-your-yubikey-with-authenticator-codes#configure)

Lastly, I also tried in my terminal the code shown below:

 ```
[COLOR=blue]sudo apt-get install libu2f-udev [/COLOR]
```

Which I got from the link below:

[https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID11](https://easylinuxtipsproject.blogspot.com/p/bugs.html#ID11)

And at the end of all of it I got a message in my Terminal that zero code was installed because the code already installed on my Ubuntu was newer than what I was trying to install. So if this is the case why does not the Yubico Desktop Authentication AppImage software work properly and show me the blue "ADD" button like the Windows10 version of the YDA software does?  

Any suggestions will be greatly appreciated. Thank you for your time.

---

### Post by EuclideanCoffee on 2020-05-03
> 
And at the end of all of it I got a message in my Terminal that zero  code was installed because the code already installed on my Ubuntu was  newer than what I was trying to install. So if this is the case why does  not the Yubico Desktop Authentication AppImage software work properly  and show me the blue "ADD" button like the Windows10 version of the YDA  software does?  


I believe you're likely to find issues because Yubi can't determine what your configuration would be. Even if they setup a "standard" application, it won't likely fit everyone's needs. Windows 10 locks users to a specific configuration and makes it challenging to configure it, so it's a little easier to build an application for it and have some return value. When you build a specific Ubuntu application, you're likely to lose value. And companies would rather let the consumer do the configuration themselves.

In this post, you're installing a library.

The guide is very thorough and even describes what you should do if the prompt doesn't work. I would start from there, with the manual installation.

---

### Post by matrix012 on 2020-05-03
Thanks for the post EuclideanCoffee. After spending a bunch on time on this matter I finally figured it out. 

For any 5series Yubikey to work on Ubuntu 18 you need to make sure the pcscd service is installed and running.

After I installed the pcscd service onto my Ubuntu 18 my Yubikey started working as designed. 

Additionally, you also have to modify the 70-u2f-generic.rules file with a bunch of data Yubico provides.

Long story short, I now have a ProtonMail email account setup with 2factor Authentication and what is cool about it is no cell phone is involved in the verification process. 

In my opinion all Linux distributions should support U2F straight out of the box because Linux represents security and privacy. In contrast, Windows10 does not because I hear it has built  in telemetry.

---

### Post by EuclideanCoffee on 2020-05-03
Awesome. I'm glad you got it working.

Linux distributions have many goals. For example, I use System76 that uses telemetry, and it's constantly pinging. Canonical does something similar with apport.

If you want a private Linux distribution, I would check out what the project's ethos and goals are.

Ubuntu is a solid choice, but there are some modifications you'd need to create to make it suit the ideal security and privacy computer. For example TPM2 and secure boot require some additional libraries to have setup properly.

Best wishes on your journey.

Note to future reader. This solves the problem.

> 
[COLOR=blue][FONT=Arial]sudo apt-get install libu2f-udev[/FONT][/COLOR]

[FONT=Arial]Press Enter. Type your password when prompted. [/FONT][I]In Ubuntu this remains entirely invisible, not even dots will show when you type it, that's normal. In Mint this has changed: you'll see asterisks when you type. Press Enter again.

d. Reboot.

e. Launch Google Chrome or Chromium and install the key, for example for your Gmail account.

f. No avail? Then try a manual approach, starting with this terminal command:

[COLOR=blue]sudo touch /etc/udev/rules.d/70-u2f-generic.rules[/COLOR]

Press Enter. Type your password when prompted. [I]In Ubuntu this remains entirely invisible, not even dots will show when you type it, that's normal. In Mint this has changed: you'll see asterisks when you type. Press Enter again.

g. Now open that text file for editing, with this command line ([use copy/paste to transfer it into the terminal]("https://easylinuxtipsproject.blogspot.com/p/copy-paste.html")):

[COLOR=blue]xed admin:///etc/udev/rules.d/70-u2f-generic.rules[/COLOR]

Press Enter.

h. Empty all existing contents (if any) and copy/paste the following blue text into it (don't type it!):

[COLOR=blue]ACTION!="add|change", GOTO="u2f_end"

KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="*", ATTRS{idProduct}=="*", TAG+="uaccess"

LABEL="u2f_end"[/COLOR]

i. Save the modified file and close it.

j. Reboot your computer.

k. Launch Google Chrome or Chromium and install the key, for example for your Gmail account.
[/I][/I]

---


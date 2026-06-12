---
title: "Help!  SMTP is Blocked!"
date: 2006-11-04
forum: Ubuntu Christian Edition
---

### Post by batonac on 2006-11-04
Hi everyone!

I've installed Ubuntu CE on almost every computer in our Christian School.  The distro is really awesome! :KS I only have one problem.  Whenever a teacher tries to send mail with an email client (i've tried evolution and thunderbird)  the connection always times out when trying to contact the smtp server. ](*,)  The only diference I could find from when it did work to now when it doesn't is the presence of squid and dansguardian in ubuntu ce.  Can somebody please help me fix this problem so our teachers can write email again?!?  --thanks

---

### Post by tonhou on 2006-11-05
Yes, you are right!
We are finding more areas that the firewall "firehol" is blocking that we need to free up.

Need to edit the file by typing in as below:

*sudo gedit /etc/firehol/firehol.conf*

and then add:
**server smtp accept**

then restart the firewall

*/etc/init.d/firehol restart*

Hopefully that will resolve it!

--Tony

---

### Post by mips on 2006-11-05
UbuntuCE has it's own forum, [http://www.ubuntuforums.org/forumdisplay.php?f=168](http://www.ubuntuforums.org/forumdisplay.php?f=168)

---

### Post by mhancoc7 on 2006-11-05
> **tonhou said:**
> Yes, you are right!
We are finding more areas that the firewall "firehol" is blocking that we need to free up.

Need to edit the file by typing in as below:

*sudo gedit /etc/firehol/firehol.conf*

and then add:
**server smtp accept**

then restart the firewall

*/etc/init.d/firehol restart*

Hopefully that will resolve it!

--Tony

I am very interested in the solution to this one. I am going to be releasing v1.5 very soon. It would be easy to make some changes to the firehol conf before the release. Please let me know if this works. :)

God Bless, Jereme

---

### Post by Mardon on 2006-11-06
:D I did a complete uninstall of dansguardian it works great. Thanks for your help. God Bless, Mark

---

### Post by Mardon on 2006-11-06
](*,)  I forgot also Firehol

---

### Post by mhancoc7 on 2006-11-06
> **Mardon said:**
> :D I did a complete uninstall of dansguardian it works great. Thanks for your help. God Bless, Mark

Hopefully we can find a solution that does not require you to remove the content filtering. I am glad to hear that you got it going though.
God Bless, Jereme

---

### Post by tonhou on 2006-11-07
> I did a complete uninstall of dansguardian it works great. Thanks for your help.

I don't quite understand - what was your original problem?

--Tony

---

### Post by tonhou on 2006-11-07
> The only diference I could find from when it did work to now when it doesn't is the presence of squid and dansguardian in ubuntu ce

Hopefully you don't have squid installed! It definitely is not included with the standard Ubuntu CE install.

--Tony

---

### Post by Mardon on 2006-11-07
> **tonhou said:**
> I don't quite understand - what was your original problem?

--Tony

The reason was it blocked some sites that I wanted to see, it blocked some pages in Firefox and Opera, I don't want it telling me what I can  or can't do . Being new to Ubuntu I didn't know how or if I could configure it or not?](*,) God Bless, Mark

---


---
title: "Two confusions about security."
date: 2010-07-21
forum: Security
---

### Post by poZiaC on 2010-07-21
Hi, 

I have started using linux only this year and am still becoming accustomed to it. I just have two security questions which I have been long confused about and would like to finally get resolved. 
    First, when using sudo, there is a fifteen minute window where you do not need to type in the password anymore. Is this period of time insecure? Can anyone or anything have root privileges until the fifteen minutes is over?
    Second, I have read that part of the security of linux systems is that if you do get anything nasty on your system, it will only be limited on the account on which it was installed. However, when I install a program, I see that it is installed on all accounts on my system. It seems that a virus or whatever can also install itself to include the scope of the entire system if it wanted to. I know viruses are rare in linux, but I would like to clear up any misunderstandings I have of how the system works.

Thank you.

---

### Post by vandorjw on 2010-07-21
About the "sudo" confusion.
- Yes, if you just used your admin password and walk away without logging out, your system would be at risk for about 15 minutes. 

And yes, if you install something using the admin account, or using the Ubuntu sofware center, (using an admin password) you are able to make whatever you installed available to the entire system.

However, you do not need to install all your programs into the root of the system. If you have the binaries you can usually run the program from anywhere.

A normal user CAN NOT put any files into the root of the system EVER.
Only someone privileged enough to have an admin password can do this.

Generally, if I, a normal user, put a virus on the school linux servers, no one but myself would be bothered by it. However, if our admin does it, we are all in trouble.

Hope that helps. PS, the comic is meant as a joke. Please don't take offense.

Linux cannot protect itself from "cabbages"

[http://www.dilbert.com/strips/comic/2010-05-20/](http://www.dilbert.com/strips/comic/2010-05-20/)

---

### Post by movieman on 2010-07-22
> **cc7gir said:**
> About the "sudo" confusion.
- Yes, if you just used your admin password and walk away without logging out, your system would be at risk for about 15 minutes.

However, note that:

1. Sudo authorisation is tied to a particular terminal window, so they can't run sudo from any other window. It's not perfect since if you close a terminal window and then they open another as you, that's likely to use the same terminal ID and hence still have the same sudo authorisation.

2. You can easily change the timeout to a shorter period or completely remove it by changing the sudo configuration files.

---

### Post by poZiaC on 2010-07-22
Okay, I experimentally verified that the thing about the terminals is true. I guess I still have to play around with installing things from different user accounts. Thank you everybody!

---

### Post by bodhi.zazen on 2010-07-22
for sudo , run sudo -k or change the defaults in sudoers.

[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

See the timeout defaults

---


---
title: "MobileOTP token authentication with PAM module."
date: 2011-10-28
forum: Security
---

### Post by RayVad on 2011-10-28
Since i'm running a server, on which i login from the Internet by SSH, i was looking for a (Mobile) OTP token option.
Did find LinOTP2 [http://www.linotp.org/]("http://www.linotp.org/") and [http://http://motp.sourceforge.net/]("http://http://motp.sourceforge.net/") which worked well together.
But since LinOTP2 need an webservice and a MySQL server, it isn't that what i exactly want. I don't want to run extra services.
So i did found this solution form the [http://http://motp.sourceforge.net/]("http://http://motp.sourceforge.net/") , based on a file. And wrote these instruction to install on Ubuntu:

Download the Pam module:
[http://motp.sourceforge.net/pam_mobile_otp-0.6.1.tgz](http://motp.sourceforge.net/pam_mobile_otp-0.6.1.tgz)
tar zxvf pam_mobile_otp-0.6.1.tgz

sudo apt-get install libpam0g-dev

Edit the Makefile and change ld -x –shared to gcc –shared
execute: make
(*note: You will see some warnings about "Char *". You can ignore these.)
And then execute: sudo make install

sudo cp motp.conf /etc/security/
sudo chmod 600 /etc/security/motp.conf

sudo mkdir /var/cache/motp

Download the MobileOTP jar file from [http://motp.sourceforge.net/](http://motp.sourceforge.net/)
[http://motp.sourceforge.net/MobileOTP.jar](http://motp.sourceforge.net/MobileOTP.jar)
and/or jad:
[http://motp.sourceforge.net/MobileOTP.jad](http://motp.sourceforge.net/MobileOTP.jad)
Install one of them to your Mobile phone.

start MobileOTP on your phone.
Enter the pin 0000 to configure a new init-secret
fill in a random 25 number key and it will return a 16 digit init-sercret.
add the returned Init-secret key to motp.conf:
sudo nano /etc/security/motp.conf

Add to the same line a 4 digit pin code you will use with MobileOTP for your user.

There is a test user(delete this if you are ready configuring) in the motp.conf to show you how to write user, init-secret, pin, GMT offset.

Everytime you will enter the pin in MobileOTP it will generate a code. This code you will need to fill in to access SSH.

Add these lines to /etc/pam.d/sshd:
auth  sufficient /lib/security/pam_mobile_otp.so not_set_pass
password required /lib/security/pam_mobile_otp.so debug
account required /lib/security/pam_mobile_otp.so

And qoute out the line:
#@include common-auth

save /etc/pam.d/sshd 

Keep in mind that when you do the following restart, you can't login anymore if you did something wrong.
So keep one console open just in case!

Restart your ssh server: sudo /etc/init.d/ssh restart

Only the users you added to the motp.conf are able to log in to SSH. 

GMT offset can be set in the motp.conf and in MobileOTP on your phone. On your phone you need to go to options>time zone and enter 1 or 3 for up or down.
If you can't login, you could try to set these setting. Both 0 will do for me.

There is a management tool in the pam_mobile_otp-0.6.1.tgz package as well to manage the motp.conf file.
you can add this motp-manager to /usr/bin/
sudo cp motp-manager /usr/bin/
you need to start it as: sudo motp-manager

Done!




All advices or ideas are welcome.

Ray
(Using Ubuntu 10.04LTS 32 and 64 bit)

---

### Post by mistermic on 2013-02-24
:D Wow, that was easy!!!  Thanks a ton for posting this.  I had to search a bit to find this, but once I google'd "mobile otp ubuntu" this page was at the top.  The only thing I had to do was change the GMT offset back to zero--the iPhone app I got has no option to change offset--no biggie!  Works like a charm, even with NoMachine NX client as the login; very nice!!

Thanks again,  

mistermic 

Ubuntu 12.04 LTS x86_64

---

### Post by kevdog on 2013-02-25
I haven't installed yet but what ports on the firewall do I need to open up to use this?

---


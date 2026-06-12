---
title: "Keyring sign on"
date: 2010-05-12
forum: Ubuntu One (CLOSED)
---

### Post by garydem on 2010-05-12
I am running Ubuntu 10.04 and using Ubuntu One that is auto starting.  When my system starts I soon receive a notice to unlock the Password keyring.  I tried using the method suggested to prevent this using the procedure outlined in the Ubuntu One FAQ.  On my system that does not appear to work.  Are they other methods to have Ubuntu auto log in without a prompt?


Thanks,
Gary

---

### Post by joshuahoover on 2010-05-12
> **garydem said:**
> I am running Ubuntu 10.04 and using Ubuntu One that is auto starting.  When my system starts I soon receive a notice to unlock the Password keyring.  I tried using the method suggested to prevent this using the procedure outlined in the Ubuntu One FAQ.  On my system that does not appear to work.  Are they other methods to have Ubuntu auto log in without a prompt?

Hi Gary,

There is a not very secure way to have it not prompt you but it is not recommended as your passwords in the keyring would be stored in plain text. (This method is to set a blank password for the keyring.) We don't include that in the FAQ as we don't recommend doing this. Our recommendation is to setup a login and make the login password and keyring password match one another. 

Thank you,

Joshua

---

### Post by wcorey on 2010-05-25
Hi Joshua,
   I've been dealing with that same issue since I upgraded to 10.4. Would you elaborate on the solution you DO recommend?

Thanks,

Walt

---

### Post by joshuahoover on 2010-05-27
> **wcorey said:**
> Hi Joshua,
   I've been dealing with that same issue since I upgraded to 10.4.  Would you elaborate on the solution you DO recommend?

Thanks,

Walt

Hi Walt,

Sure! The following FAQ has information on how to fix this problem:  [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20get%20rid%20of%20the%20keyring%20password%20prompt?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20get%20rid%20of%20the%20keyring%20password%20prompt?)

If that isn't helpful let me know where it's not clear and I'll do my best to clear things up. :)

Thanks!

Joshua

---

### Post by Polmac on 2010-06-01
> There are two common scenarios where you will be prompted for your keyring password:

1. You are set to auto-login
2. Your keyring password is different than your login password

For #1, if you want to remove the keyring password prompt, it is recommended you setup a login for Ubuntu and set the keyring password to be the same as your Ubuntu login password.

This means if I don't want to enter my password to access the keyring, I have to enter my password on login?? there's really no way for **not entering any password** at all??

Seriously, this is really annoying. I use Dropbox as well and it doesn't bother me me with this kind of things.

---


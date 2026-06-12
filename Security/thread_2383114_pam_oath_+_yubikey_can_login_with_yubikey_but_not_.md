---
title: "pam_oath + yubikey: can login with yubikey but not unlock lockscreen"
date: 2018-01-21
forum: Security
---

### Post by berndhard on 2018-01-21
Hi,

I'm using pam_oath.so from the libpam_oath package to use my yubikey  to login. Its configured as OATH-HOTP and it's working fine. I can login  with my pin and a press on my yubikey. I dont need to enter my user-pw  when login in to my account.

  But when I lock the screen and try to unlock it I cant use my yubikey  alone. I always have to enter my password. It doesn't even matter if I  enter the correct pin and I also can discard the whole  yubikey-authentication (by just pressing enter) as long as I enter my  correct user password, I can unlock the screen.

  This is config line I use in /etc/pam.d/common-auth:
  ```
auth sufficient pam_oath.so usersfile=/etc/users.oath window=20 digits=8

```  I tried to enter the same line in various config files in pam.d, for example lightdm, lightdm-greeter, unity but nothing changed the behaviour.
  Can anyone explain me where my error is, or what the correct syntax  must be if I want to be able to unlock the screen when using my pin +  yubikey.
  I no it's possible, because if you use freeradius + yubikey and pin,  you are able to unlock your locked screen with pin + yubikey.


  Any hint how to hunt the error is also much appreciated!

---


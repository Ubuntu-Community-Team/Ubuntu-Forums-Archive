---
title: "Give access to external user to server"
date: 2012-08-07
forum: Security
---

### Post by cribeirobt on 2012-08-07
We have a ubuntu 12 server in Amazon AWS
We would like to hire someone to work on our website but I would not like to share the pem key nor provide ssh access

I would like to give access by SFTP to this external user to have permissions to do anything on /var/www where we have several websites

Could you please offer a detailed explanation of the different steps?

add user, give user password, add user to group ?? ....

The client used for SFTP is Transmit

I am in desperate need of help on this issue. Thank you

---

### Post by cintiaarosales on 2012-08-07
¡Hola!

To give SFTP access to an external user to work in /var/www you should try the following:
1. First, add new system group (e.g. TransmitSFTP)
2. Next, add the user (or users you want to allow restricted permissions to the group.
3. Now, add the following to the ssh config file:
   ```
Subsystem sftp internal-sftp

    Match Group TransmitSFTP
        ChrootDirectory %h
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
```
The users added to your new group will be directed to the sftp subsystem you setup in SSH.
¡buena suerte!,
:cool: Cintia

---

### Post by cribeirobt on 2012-08-07
Thank you for your reply

In fact I did that before, however when I try to login with the standard user ubuntu it stops working
It also does not work with an external user created for sftp access using Transmit

I followed the instructions on this page 

[https://library.linode.com/security/sftp-jails](https://library.linode.com/security/sftp-jails)

---


---
title: "cannot acces SWAT as root"
date: 2006-11-20
forum: Server Platforms
---

### Post by kjacks on 2006-11-20
I just started using SWAT and Samba.  I cannot access SWAT as the root user.  I did add a user with this command:

sudo smbpasswd -a james

I log in @ [http://ubuntu:901/shares](http://ubuntu:901/shares)

I can log in under username james fine but it doesn't give me all the functionality that the root would give.  Shouldn't I be able to log in with the Ubuntu's root password?  Here is what my xinetd.d file looks like:

# description: SAMBA SWAT
service swat {
 disable = no
 socket_type = stream
 protocol = tcp
 #should use a more limited user here
 user = root
 wait = no
 server = /usr/sbin/swat
}

I copied this from a lot of SWAT tutorials and I'm sure I just missed some simple step.  Thanks for any help you can give!

---

### Post by peter@kkvs on 2006-11-20
Just had the same problem. change or reset your root passwd
sudo passwd root
new password  "big-secret"
then go to your browser and just enter [http://server:901](http://server:901)
it will prompt for user name and password.
Which needs to be "root" followed by the root password
If this does not work over a network you need to install netkit-inetd
sudo apt-get install netkit-inetd
and all should work fine 
(PS took me nearly a day to find these key bits of info on the web - why are they not written clearly in any of the manuels ?)

---

### Post by kjacks on 2006-11-21
Worked like a charm.  Thanks for the help!

---

